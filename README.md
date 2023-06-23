# 
<h1 align="center"> Javascript Tricks Tips </h1>


## Table Of Content 
- [Array](#array)
   - [Array and Spread Operator](#array-and-spread-operator)
      <details>
      <summary>
         Trick and Tips
      </summary>
      
      - [Create an Array](#generate-an-array)
      - [Get unique value from array](#get-unique-value-from-array-using-set)
      - [Shuffle Array](#shuffle-array)
      - [Resize an Array](#resize-an-array)
      - [Random item from Array](#random-item-from-array)

      </details>
- [Expression & Operators](#expression-and-operators)
   
    <details>
    <summary>
        Trick and Tips
    </summary>
    
    - [0 is a devil, please stay away from it](#0-is-a-devil-please-stay-away-from-it)

    </details>
- [String](#string)
- [Function](#function)
   - [Arrow Function](#arrow-function)
   - [Concise Declarative Functions with ES6](#concise-declarative-functions-with-es6)
   - [Functional Programming](#functional-programming)
- [Object](#object)
   - [Prevent Object Mutation](#prevent-object-mutation)
- [Class](#class)
- [OOP](#oop---object-oriented-programming-sample-code)
- [Set](#set)
- [Destruction](#destruction)
- [Promises and Asynchronous Programming](#promises-and-asynchronous-programming)
- [Regular expressions](#regular-expressions)
- [Recursion](#recursion)
- [Debugging](#debugging)






<br><br><br>


## Array
#### [Array.concat()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)
The concat() method is used to merge two or more arrays. This method does not change the existing arrays, but instead returns a new array
```javascript
let newArray = [1, 2, 3].concat([4, 5, 6]);
// output - [1, 2, 3, 4, 5, 6].
```
<br>

#### [Array.slice()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)
The slice() method returns a shallow copy of a portion of an array into a new array object selected from start to end (end not included) where start and end represent the index of items in that array. **The original array will not be modified.**
```javascript
// slice()
// slice(start)
// slice(start, end)

let fruits = ['Banana', 'Orange', 'Lemon', 'Apple', 'Mango']
let citrus = fruits.slice(1, 3)
// fruits -  ['Banana', 'Orange', 'Lemon', 'Apple', 'Mango']
// citrus -  ['Orange','Lemon']

// copy array using slice method
let citrusCopied = fruits.slice();
// citrusCopied -  ['Banana', 'Orange', 'Lemon', 'Apple', 'Mango']
```
<br>

#### [Array.splice()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)
The splice() method changes the contents of an array by **removing or replacing** existing elements and/or adding new elements in place. To access part of an array without modifying it, see slice().
```javascript
// splice(start)
// splice(start, deleteCount)
// splice(start, deleteCount, item1)
// splice(start, deleteCount, item1, item2, itemN)

let myFish = ['angel', 'clown', 'mandarin', 'sturgeon']
let removed = myFish.splice(2, 0, 'drum')
// myFish -  ["angel", "clown", "drum", "mandarin", "sturgeon"]
// removed -  [], no elements removed

let myFish = ['angel', 'clown', 'drum', 'mandarin', 'sturgeon']
let removed = myFish.splice(3, 1)
// myFish - ["angel", "clown", "drum", "sturgeon"]
// removed - ["mandarin"]

let myFish = ['angel', 'clown', 'drum', 'sturgeon']
let removed = myFish.splice(2, 1, 'trumpet')
// myFish - ["angel", "clown", "trumpet", "sturgeon"]
// removed - ["drum"]
```
<br>

#### [Array.filter()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)
The filter() method creates a new array with all elements that pass the test implemented by the provided function. Filter Array
```javascript
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];
const result = words.filter(word => word.length > 6);
console.log(result);
// expected output: Array ["exuberant", "destruction", "present"]
//
//
// Arrow function
Array.filter((element) => { ... } )
Array.filter((element, index) => { ... } )
Array.filter((element, index, array) => { ... } )
/* 
element : The current element being processed in the array.
index   : The index of the current element being processed in the array.
array   : The array filter was called upon.
*/
```
<br>

#### [Array.map()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
The map() method creates a new array populated with the results of calling a provided function on every element in the calling array
```javascript
const users = [
  { name: 'John', age: 34 },
  { name: 'Amy', age: 20 },
  { name: 'camperCat', age: 10 }
];
const names = users.map(user => user.name);
console.log(names);
// expected output: [ 'John', 'Amy', 'camperCat' ]

const array1 = [1, 4, 9, 16];
const map1 = array1.map(x => x * 2);
console.log(map1);
// expected output: Array [2, 8, 18, 32]

// Arrow function
map((element) => { ... } )
map((element, index) => { ... } )
map((element, index, array) => { ... } )
```
<br>

#### [Array.reduce()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)
The reduce() method executes a reducer function (that you provide) on each element of the array, resulting in a single output value.
```javascript
// reduce((accumulator, currentValue) => { ... } )
// reduce((accumulator, currentValue, index) => { ... } )
// reduce((accumulator, currentValue, index, array) => { ... } )
// reduce((accumulator, currentValue, index, array) => { ... }, initialValue)
//-----
// if initialValue value not supplied then iteration will start 
// from second index and accumulator will be first element of array
//-----

const array1 = [1, 2, 3, 4];
const sum = array1.reduce((accumulator, currentValue) => accumulator + currentValue);
// sum - 10

const users = [
  { name: 'John', age: 34 },
  { name: 'Amy', age: 20 },
  { name: 'camperCat', age: 10 }
];
const sumOfAges = users.reduce((sum, user) => sum + user.age, 0);
console.log(sumOfAges);  
// output - 64

const users = [
  { name: 'John', age: 34 },
  { name: 'Amy', age: 20 },
  { name: 'camperCat', age: 10 }
];
const sumOfAges = users.reduce((sum, user) => sum + user.age, 0);
console.log(sumOfAges);  
// output - 64

const users = [
  { name: 'John', age: 34 },
  { name: 'Amy', age: 20 },
  { name: 'camperCat', age: 10 }
];
const usersObj = users.reduce((obj, user) => {
  obj[user.name] = user.age;
  return obj;
}, {});
console.log(usersObj);
// output - { John: 34, Amy: 20, camperCat: 10 }.
```
<br>

#### [Array.every()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
The every() method tests whether all elements in the array pass the test implemented by the provided function. It returns a Boolean value.
```javascript
// every((element) => { ... } )
// every((element, index) => { ... } )
// every((element, index, array) => { ... } )

var numbers = [1, 5, 8, 0, 10, 11];
var boolean = numbers.every(function(element) {
  return element < 10;
});
console.log(boolean) // false
```
<br>

#### [Array.some()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
The some() method tests whether at least one element in the array passes the test implemented by the provided function. It returns true if, in the array, it finds an element for which the provided function returns true; otherwise it returns false. It doesn't modify the array.
```javascript
// some((element) => { ... } )
// some((element, index) => { ... } )
// some((element, index, array) => { ... } )

var numbers = [10, 50, 8, 220, 110, 11];
var boolean = numbers.some(function(currentValue) {
  return currentValue < 10;
});
console.log(boolean) // true
```

<br>

#### [Array.sort()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)
The sort() method sorts the elements of an array in place and returns the sorted array
```javascript
// Number Sorting
let numbers = [4, 2, 5, 1, 3];
numbers.sort((a, b) => a - b);
console.log(numbers);
// [1, 2, 3, 4, 5]
//
//
// Number and String Sorting
var items = [
  { name: 'Edward', value: 21 },
  { name: 'Sharpe', value: 37 },
  { name: 'And', value: 45 },
  { name: 'The', value: -12 },
  { name: 'Magnetic', value: 13 },
  { name: 'Zeros', value: 37 }
];
// sort by value
items.sort(function (a, b) {
  return a.value - b.value;
});
// sort by name
items.sort(function(a, b) {
  var nameA = a.name.toUpperCase(); // ignore upper and lowercase
  var nameB = b.name.toUpperCase(); // ignore upper and lowercase
  if (nameA < nameB) {
    return -1;
  }
  if (nameA > nameB) {
    return 1;
  }
  // names must be equal
  return 0;
});
```

<br>

#### [Array.fill()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/fill)
The fill() method changes all elements in an array to a static value, from a start index (default 0) to an end index (default array.length). It returns the modified array.
```javascript
array.fill(value)
array.fill(value, start)
array.fill(value, start, end)


const array1 = [1, 2, 3, 4];

// fill with 0 from position 2 until position 4
console.log(array1.fill(0, 2, 4));
// expected output: [1, 2, 0, 0]

// fill with 5 from position 1
console.log(array1.fill(5, 1));
// expected output: [1, 5, 5, 5]

console.log(array1.fill(6));
// expected output: [6, 6, 6, 6]
```
:warning: : using fill method you can generate static value array. To generate array value as per you need you have to use [**Array.from**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from) method


<br><br><br>


### Array and Spread Operator
```javascript
const arr = [6, 89, 3, 45];
const maximus = Math.max(...arr);
// result -  89

```
<br><br><br>

### Generate an Array
##### Empty array of length **`n`**

  ```js
  var arr = new Array(3);

  // result: arr = [undefined, undefined, undefined]
  ```


<br>

##### Empty array of length **`n`** & fill value **`x`**
  ```js
  var arr = [...Array(3).fill(1)];
  var arr2 = [...Array(5).fill(1, 0, 3)];

  /* 
    result: arr = [1, 1, 1]
            arr2 = [1, 1, 1, undefined, undefined]
  */
  ```
:warning: : using fill method you can generate static value array. To generate array value as per you need you have to use [**Array.from**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from) method

<br>

##### Array containing `0...n`

  ```js
  var arr = [...Array.keys(5)];

  // result: arr = [0, 1, 2, 3, 4]
  ```

<br>

##### [Array containing `1...n`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from)

  ```js
  var arr = [];
  for (let i = 0; arr.push(++i) < 4; );

  var arr2 = Array.from({ length: 4 }, (_, i) => i + 1);
  var arr3 = Array.from({ length: 4 }, (_, i) => i * 2);
  var arr4 = Array.from({ length: 4 }, () => Math.random());

  /* 
    result: arr =  [1, 2, 3, 4]
            arr2 = [1, 2, 3, 4]
            arr3 = [0, 2, 4, 6]
            arr4 = [0.211, 0.5123, 0.612, 0.8921]
  */
  ```

<br><br><br>

### Get unique value from array using Set
```javascript
var arr = [1, 2, 2, 3, 5, 5, 4];
var newArr = [...new Set(arr)];

// result: newArr = [1, 2, 3, 5, 4]
```

<br><br><br>

### Shuffle Array
```javascript
var arr = [1, 2, 3, 4, 5];
var shuffleArr = arr.sort(() => Math.random() - 0.5);

// result: shuffleArr = [3, 1, 2, 4, 5]
```

<br><br><br>

### Resize an Array
```javascript
var arr = [1, 2, 3, 4, 5];
arr.length = 2;

var arr2 = [1, 2, 3, 4, 5];
arr2.length = 0;

var arr3 = [1, 2, 3, 4, 5];
arr3.length = 7;

/*
  result: arr = [1, 2]
          arr2 = []
          arr3 = [1, 2, 3, 4, 5, undefined, undefined]
*/
```

<br><br><br>

### Random item from Array
```javascript
var arr = [2, 4, 5];
var item = arr[Math.floor(Math.random() * arr.length)];

```




<br>

<hr>


<br><br>


## Expression and Operators

###  [0 is a devil, please stay away from it](https://javascript.plainenglish.io/its-2023-please-stop-using-for-conditional-rendering-in-react-b588a09ebb17)
Please Stop Using “&&” for Conditional Rendering in React
```javascript
// React Code
return (
    list.length && (
      <div className="name-list-container">
        {list.map((name) => {
          return <div className="name-list-item">{name}</div>;
        })}
      </div>
    )
  );
```
How && works<br>
More generally, the operator returns the value of the first falsy operand encountered when evaluating from left to right, or the value of the last operand if they are all truthy. <br>
Let’s learn a very easy example, and I think you will understand it very quickly
```javascript
const a = 0
const b = "React"
const c = 1
const d = "Javascript"

console.log(a && b) // 0
console.log(c && d) // Javascript
```
We can try these 3 ways to avoid this problem.
```javascript
// 1. Convert list.length to boolean
!!list.length && <Component list={list} />

// 2. Controlled by specific logic
list.length >= 1 && <Component list={list} />;

// 3. Use ternary expressions and null
list.length ? <Component list={list} /> : null;
```


<br>
<hr>


<br><br>


## String
### Create Strings using Template Literals
Template literals allow you to create multi-line strings and to use string interpolation features to create strings.
```javascript
const person = {
  name: "Zodiac Hasbro",
  age: 56
};

const greeting = `Hello, my name is ${person.name}!
I am ${person.age} years old.`;

console.log(greeting);
```


<br>
<hr>
<br><br><br>

## Function
### Arrow Function
```javascript
const myFunc = () => {
  const myVar = "value";
  return myVar;
}

// without parameter
const myFunc = () => "value";

// If an arrow function has a single parameter,
const doubler = (item) => item * 2;
const doubler = item => item * 2;

// pass more than one parameter 
const multiplier = (item, multi) => item * multi;

// default parameters for functions
const greeting = (name = "Anonymous") => "Hello " + name;
console.log(greeting("John"));
console.log(greeting());

// Use the Rest Parameter with Function Parameters
function howMany(...args) {
  return "You have passed " + args.length + " arguments.";
}
console.log(howMany(0, 1, 2));
console.log(howMany("string", null, [1, 2, 3], { }));

```

<br><br>


### Concise Declarative Functions with ES6
```javascript
//--  ES5 --------
const person = {
  name: "Taylor",
  sayHello: function() {
    return `Hello! My name is ${this.name}.`;
  }
};
//--  ES6 --------
// With ES6, you can remove the function keyword and 
// colon altogether when defining functions in objects
const person = {
  name: "Taylor",
  sayHello() {
    return `Hello! My name is ${this.name}.`;
  }
};

```
<br><br><br>

### Functional Programming
Functional Programming is another popular approach to software development. In Functional Programming, code is organized into smaller, basic functions that can be combined to build complex programs

- Functional programming is a style of programming where solutions are simple, isolated functions, without any side effects outside of the function scope: INPUT -> PROCESS -> OUTPUT
- **Callbacks** are the functions that are slipped or passed into another function to decide the invocation of that function
- Functional programming is a form of declarative programming. You tell the computer what you want done by calling a method or function
- **Avoid Mutations and Side Effects Using Functional Programming** - One of the core principles of functional programming is to not change things. Changes lead to bugs. It's easier to prevent bugs knowing that your functions don't change anything, including the function arguments or any global variable.
- **Pass Arguments to Avoid External Dependence in a Function** - Another principle of functional programming is to always declare your dependencies explicitly. This means if a function depends on a variable or object being present, then pass that variable or object directly into the function as an argument
- Don't alter a variable or object - create new variables and objects and return them if need be from a function. Hint
- Use the map Method to Extract Data from an Array

```javascript
// console.log() - To print output use console.log
var name = "Shailendra";
var surname = "more";
console.log(name, surname)
```

<br>
<hr>

<br><br><br>

## Object
### [Prevent Object Mutation](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/prevent-object-mutation)
JavaScript provides a function Object.freeze to prevent data mutation.
Once the object is frozen, you can no longer add, update, or delete properties from it. Any attempt at changing the object will be rejected without an error.
```javascript
let obj = {
  name:"FreeCodeCamp",
  review:"Awesome"
};

Object.freeze(obj);

obj.review = "bad";
obj.newProp = "Test";
console.log(obj); 
/*
The obj.review and obj.newProp assignments will result 
in errors, and the console will display the value 
{ name: "FreeCodeCamp", review: "Awesome" }.
*/
```




<br>
<hr>

<br><br><br>


## Class
```javascript
//---  js/spaceShuttle.js  ---
class SpaceShuttle {
  constructor(targetPlanet) {
    this.targetPlanet = targetPlanet;
  }
}
// export variable or function to use in another file
export{SpaceShuttle} 

const zeus = new SpaceShuttle('Jupiter');


//---  ./js/math_functions.js  ---
const add = (x, y) => {
  return x + y;
}
const subtract = (x, y) => {
  return x - y;
}
//  You can export multiple things by repeating export 
export{add}
export{subtract}
// or by placing them all in the export statement
export {add, subtract };


// Getters and Setters
//---  js/book.js  ---
// you can only have one value be a 'default export' in 
// each module or file. Additionally, you cannot use 
// export default with var, let, or const
export default class Book {
  constructor(author) {
    this._author = author;
  }
  // getter
  get writer() {
    return this._author;
  }
  // setter
  set writer(updatedAuthor) {
    this._author = updatedAuthor;
  }
}

const novel = new Book('anonymous');
console.log(novel.writer);
novel.writer = 'newAuthor';
console.log(novel.writer);
```
```html
<!-- 
A script that uses type="module" can now use 
the import and export features of ES6
Note: all code execute inside of /js/spaceShuttle.js
Example: Console.log written outside of class
 -->
<script type="module" src="./js/spaceShuttle.js"></script>

<!-- or import in html using script tag and 
initialize inside script tag it -->
<script  type="module" >
   import {SpaceShuttle} from './js/spaceShuttle.js';
   const zeus = new SpaceShuttle('Jupiter');
</script>
```
```javascript
// import
import add from "./math_functions.js";

/* 
Use * to Import Everything from a File.
The above import statement will create an object called 
myMathModule. This is just a variable name, you can name it
anything. The object will contain all of the exports from 
math_functions.js
*/
import * as myMathModule from "./js/math_functions.js";
myMathModule.add(2,3);
myMathModule.subtract(5,3);
```

<br>
<hr>

<br><br>




## OOP - Object Oriented Programming Sample Code
```javascript
window.objLib = window.objLib || {};
(function () {
    var Cactus = function () {
        this.super_initialize();
        this.initialize();
    };
    var p = Cactus.prototype

    var p = Cactus.prototype = new gameLib.BaseElement();
    p.constructor = Cactus;
    p.super_initialize = p.initialize;

    p.initialize = function () {
        var This = this;
    };
    objLib.Cactus = Cactus;
}());
```

```javascript
//----------------------------
// Singleton Object
//----------------------------
window.objLib = window.objLib || {};
(function() {
	var Utils = function() {	
		this.initialize();
	}
	var p = Utils.prototype;
	p.canvas;
	p.initialize = function() {
		var This = this;
	}
	objLib.Utils = new Utils();
}());
```



<br><br><br>



### OOP - Object Oriented Programming In Depth
```javascript
let duck = {
  name: "Aflac",
  numLegs: 2,
  sayName: function() {
    return "The name of this duck is " + this.name + ".";
    }
};
duck.sayName();


// Constructors are functions that create new objects
function Bird(name, color) {
  this.name = name;
  this.color = color;
  this.numLegs = 2;
}
let cardinal = new Bird("Bruce", "red");


// Verify an Object's Constructor with instanceof
let crow = new Bird("Alexis", "black");
crow instanceof Bird;  // true
duck instanceof Bird;  // false


// Use Closure to Protect Properties Within an Object 
// from Being Modified Externally
function Bird() {
  let hatchedEgg = 10;
  this.getHatchedEggCount = function() { 
    return hatchedEgg;
  };
}
let ducky = new Bird();
ducky.getHatchedEggCount();


// ---  hasOwnProperty  ----
// hasOwnProperty() as opposed to inheriting.
// The hasOwnProperty() method returns a boolean indicating whether 
// the object has the specified property as its own property 
// (as opposed to inheriting it).
const object1 = {};
object1.property1 = 42;
console.log(object1.hasOwnProperty('property1'));  //true
console.log(object1.hasOwnProperty('toString'));  // false
console.log(object1.hasOwnProperty('hasOwnProperty'));  // false
// The `in` operator will return true for direct or inherited properties:
'property1' in example;  // true
'toString' in example;  // true
'hasOwnProperty' in example;  // true
let fruits = ['Apple', 'Banana','Watermelon', 'Orange'];
fruits.hasOwnProperty(3);   // true ('Orange')
fruits.hasOwnProperty(4);   // false - not defined


// ---  prototype  ----
// assume lots of instance initialized and you want to some property.
// you can add using prototype
function Bird(name) {
  this.name = name;
}
Bird.prototype.numLegs = 2;
let snoopy = new Bird("Snoopy");
// adding eye prop after initialized
Bird.prototype.eye = 2;
console.log(snoopy.numLegs);
console.log(snoopy.eye);

// Add All properties at once:
function Dog(name) {
  this.name = name;
}
Dog.prototype = {
  numLegs: 2, 
  eat: function() {
    console.log("nom nom nom");
  },
  describe: function() {
    console.log("My name is " + this.name);
  }
};
Dog.prototype.speed = 40;
var dog = new Dog("tommy");
console.log(dog.name);  // tommy
console.log(dog.numLegs);  // 2
dog.eat();  // nom nom nom
dog.describe();  // My name is tommy
console.log(dog.speed);  // 40

// setting the prototype it erases the constructor property and
// constructor now gives false results:
function Dog(name) {
  this.name = name;
}
var dogA = new Dog("ss");
console.log(dogA.constructor === Dog); // true
Dog.prototype.speed = 40;
var dogAA = new Dog("ss");
console.log(dogAA.constructor === Dog); // true
// after setting object prototype it erase constructor
Dog.prototype = {
  leg:4
}
var dogB = new Dog("ss");
console.log(dogB.constructor === Dog);  // false
// reset constructor in prototype
Dog.prototype = {
  constructor:Dog
}
var dogC = new Dog("ss");
console.log(dogC.constructor === Dog);  // true


// ---  Inheritance  ---
function Animal(name) {
  this.location = "mumbai";
 };
Animal.prototype = {
  constructor: Animal, 
  initialise:function(name){
    this.name = name;
    console.log("super initialised - ", name)
  },
  describe: function() {
    console.log("My name is " + this.name);
  }
};

function Bird(name) {
  this.animal_initialise(name);
  this.wing = 2;
};
var p = Bird.prototype = new Animal();
p.constructor = Bird;
p.animal_initialise = p.initialise;

function Dog(name) {
  this.animal_initialise(name);
  this.leg = 4;
};
var p = Dog.prototype = new Animal();
p.constructor = Dog;
p.animal_initialise = p.initialise;
p.initialize = function () {
    var This = this;
};

var bird = new Bird("Bird");  // super initialised -  Bird
var dog = new Dog("Tommy");  // super initialised -  Tommy
bird.describe();  // My name is Bird
dog.describe();  // My name is Tommy
console.log(bird.location, bird.wing);  // mumbai 2
console.log(dog.location, dog.leg);  // mumbai 4

```


<br>
<hr>

<br><br>


## [Set](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set)
The Set object lets you store unique values of any type, whether primitive values or object references.
```javascript
const mySet1 = new Set()

mySet1.add(1)           // Set [ 1 ]
mySet1.add(5)           // Set [ 1, 5 ]
mySet1.add(5)           // Set [ 1, 5 ]
mySet1.add('some text') // Set [ 1, 5, 'some text' ]
const o = {a: 1, b: 2}
mySet1.add(o)
// Set  [1, 5, 'some text', {a: 1, b: 2}]

mySet1.add({a: 1, b: 2})   // o is referencing a different object, so this is okay
// Set  [1, 5, 'some text', {a: 1, b: 2}, , {a: 1, b: 2}]

mySet1.has(1)              // true
mySet1.has(3)              // false, since 3 has not been added to the set
mySet1.has(5)              // true
mySet1.has(Math.sqrt(25))  // true
mySet1.has('Some Text'.toLowerCase()) // true
mySet1.has(o)       // true

mySet1.size         // 5

mySet1.delete(5)    // removes 5 value from the set

mySet1.has(5)       // false, 5 has been removed

mySet1.size         // 4, since we just removed one value

mySet1.add(5)       // Set [1, 'some text', {...}, {...}, 5] - a previously deleted item will be added as a new item, it will not retain its original position before deletion

console.log(mySet1)
// logs Set(5) [ 1, "some text", {…}, {…}, 5 ] in Firefox
// logs Set(5) { 1, "some text", {…}, {…}, 5 } in Chrome
```
<br>

[To Iterating and Loop Set](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set#iterating_sets)

[Union/Join, Intersection, SymmetricDifference, Difference, isSuperset](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set#implementing_basic_set_operations)

<br>
<hr>

<br><br>


## Destruction

#### With Array
```javascript
// Extract Values from Objects
const user = { name: 'John Doe', age: 34 };
const { name, age } = user;

// Extract and give new variable names in the assignment
const user = { name: 'John Doe', age: 34 };
const { name: userName, age: userAge } = user;

// Assign Variables from Nested Objects Passed
const user = {
  johnDoe: { 
    age: 34,
    email: 'johnDoe@freeCodeCamp.com'
  }
};
const { johnDoe: { age, email }} = user;
const { johnDoe: { age: userAge, email: userEmail }} = user;


// Destructuring an array lets us do exactly that:
const [a, b] = [1, 2, 3, 4, 5, 6];
console.log(a, b); // The console will display the values of a and b as 1, 2.

// Destructuring by using commas to reach the desired index
const [a, b,,, c] = [1, 2, 3, 4, 5, 6];
console.log(a, b, c);
// The console will display the values 
// of a, b, and c as 1, 2, 5.

// Destructuring Assignment with 
// the Rest Parameter to Reassign Array
const [a, b, ...arr] = [1, 2, 3, 4, 5, 7];
console.log(a, b);
console.log(arr);
// The console would display the values 1, 2 and [3, 4, 5, 7].

// Copy Array using Destruction
let array = [1, 2, 3, 4, 5, 7];
let copyArray = [...array];

// declare and set default value
var [a, b = 0, c = 0] = [1, 2];
// same: var a = 1, b = 2, c = 0;

// nested array destructuring
var [a, b, [c, d], e] = [1, 2, [3, 4], 5];
// same: var a = 1, b = 2, c = 3, d = 4, e = 5

// Destructuring Assignment to Pass an Object as a Function's Parameters
const update = ({name, age, nationality, location}) => {
    console.log(name, age, nationality, location)
}
update({name:"shailendra", age:43, location:"Mumbai"})

```
<br><br>

#### With Object

```javascript
var person = { name: 'Dyno', age: 18 };

var { name, age } = person;
// same: var name = person.name, age = person.age;

// declare and set default value
var { name = 'Anonymous', age = 1, address = 'HCM city' } = person;
// same: var name = person.name, age = person.age, address: 'HCM city'

// declare and change variable name
var { name: personName, age: personAge } = person;
// same: var personName =  person.name, personAge = person.age

console.log({ name, age });
// same: {name: 'Dyno', age: 18}

var person = { name: 'Dyno', age: 18, infor: { address: 'HCM', phone: '123' } };
var {
	name,
	age,
	infor: { address, phone },
} = person;
// same: name = person.name, age = person.agem, address = person.infor.address, phone = person.infor.phone
// nested object destructuring
```

<br>
<hr>
<br><br>



## Promises and Asynchronous Programming
A promise is a placeholder for the result of an asynchronous operation. Instead of subscribing to an event or passing a callback to a function, the function can return a promise
```javascript
//----------------------

let promise = new Promise(function(resolve, reject) {
	console.log("Promise");
    let isFileReceived = true;
    if(isFileReceived){        
	    resolve("received file");
    }else{        
	    reject("fail to receive file");
    }
});

promise.then(function(msg) {
	console.log("Resolved - ", msg);
    // "Resolved - received file"
}, function(msg) {
	console.log("Reject - ", msg);
    // "Reject - fail to receive file"
});
//  The previous example is equivalent to:
promise.then(function(msg) {
	console.log("Resolved - ", msg);
    // "Resolved - received file"
}).catch(function(msg) {
	console.log("Reject - ", msg);
    // "Reject - fail to receive file"
});


//----------------------


// Executor Errors
// If an error is thrown inside an executor, 
// then the promise’s rejection handler is called. For example: 

let promise = new Promise(function(resolve, reject) {
	throw new Error("Explosion!");
});
promise.catch(function(error) {
	console.log(error.message); 	// "Explosion!"
});
//--- The previous example is equivalent to:
let promise = new Promise(function(resolve, reject) {
	try {
    	throw new Error("Explosion!");
	} catch (ex) {
    	reject(ex);
	}
});
promise.catch(function(error) {
	console.log(error.message); 	// "Explosion!"
});


//----------------------


// Chaining Promises
// Each call to then() or catch() actually creates and 
// returns another promise. This second promise is resolved
// only once the first has been fulfilled or rejected.

let p1 = new Promise(function(resolve, reject) {
	resolve(42);
});

p1.then(function(value) {
	console.log(value);      	// calling sequence - 1
}).then(function() {
	console.log("Finished-1");   // calling sequence - 3
}).then(function() {
	console.log("Finished-2");   // calling sequence - 5
});

p1.then(function(value) {
	console.log(value+" Other");  // calling sequence - 2
}).then(function() {
	console.log("Finished-1 Other");   // calling sequence - 4
})
/*---The code outputs:
42
42 Other
Finished-1
Finished-1 Other
Finished-2
*/


//----------------------


// Catching Errors
// Promise chaining allows you to catch errors that may
// occur in a fulfillment or rejection handler from a 
// previous promise. For example:
let p1 = new Promise(function(resolve, reject) {
	resolve(42);
});

p1.then(function(value) {
	throw new Error("Boom!");
}).catch(function(error) {
	console.log(error.message); 	// "Boom!"
});
 
// The same is true if a rejection handler throws an error:
let p1 = new Promise(function(resolve, reject) {
	throw new Error("Explosion!");
});

p1.catch(function(error) {
	console.log(error.message);   // "Explosion!"
	throw new Error("Boom!");	 // if this line commented then below catch will not call
}).catch(function(error) {
	console.log(error.message);   // "Boom!"
});


//----------------------


// Returning Values in Promise Chains
// Another important aspect of promise chains is the ability to pass
// data from one promise to the next. You’ve already seen that a value
// passed to the resolve() handler inside an executor is passed to the
//  fulfillment handler for that promise. You can continue passing data 
// along a chain by specifying a return value from the fulfillment handler.

let p1 = new Promise(function(resolve, reject) {
	resolve(42);
});

p1.then(function(value) {
	console.log(value);     	// "42"
	return value + 1;
}).then(function(value) {
	console.log(value);     	// "43"
});
 
// You could do the same thing with the rejection handler. When a 
// rejection handler is called, it may return a value. If it does, 
// that value is used to fulfill the next promise in the chain, 
// like this:
let p1 = new Promise(function(resolve, reject) {
	reject(42);
});
 
p1.catch(function(value) {
	console.log(value);     	// "42"
	return value + 1;
}).then(function(value) {
	console.log(value);     	// "43"
});


//----------------------


// Returning Promises in Promise Chains
// Returning primitive values from fulfillment and rejection handlers allows 
// passing of data between promises, but what if you return an object? If the 
// object is a promise, then there’s an extra step that’s taken to determine 
// how to proceed. Consider the following example:

let p1 = new Promise(function(resolve, reject) {
	resolve(42);
});
let p2 = new Promise(function(resolve, reject) {
	resolve(43);
});

p1.then(function(value) {
	// first fulfillment handler
	console.log(value);     // 42
	return p2;
}).then(function(value) {
	// second fulfillment handler
	console.log(value); 	// 43
});

// previous example equivalent to this:
let p1 = new Promise(function(resolve, reject) {
	resolve(42);
});
let p2 = new Promise(function(resolve, reject) {
	resolve(43);
});
let p3 = p1.then(function(value) {
	// first fulfillment handler
	console.log(value); 	// 42
	return p2;
});
p3.then(function(value) {
	// second fulfillment handler
	console.log(value); 	// 43
});
 
// Here, it’s clear that the second fulfillment handler is attached to p3 
// rather than p2. This is a subtle but important distinction, as the second 
// fulfillment handler will not be called if p2 is rejected. For instance:

let p1 = new Promise(function(resolve, reject) {
	resolve(42);
});
let p2 = new Promise(function(resolve, reject) {
	reject(43);
});

p1.then(function(value) {
	// first fulfillment handler
	console.log(value); 	// 42
	return p2;
}).then(function(value) {
	// second fulfillment handler
	console.log(value);	 // never called
}, function(value) {
	// second rejection handler
	console.log(value); 	// 43
});

// In this example, the second fulfillment handler is never called because p2 
// is rejected. You could, however, attach a rejection handler instead:

let p1 = new Promise(function(resolve, reject) {
	resolve(42);
});
let p2 = new Promise(function(resolve, reject) {
	reject(43);
});

p1.then(function(value) {
	// first fulfillment handler
	console.log(value); 	// 42
	return p2;
}).catch(function(value) {
	// rejection handler
	console.log(value); 	// 43
}); 


//----------------------


// Returning thenables simply allows you to define additional responses to the 
// promise results. You defer the execution of fulfillment handlers by 
// creating a new promise within a fulfillment handler. For example:

let p1 = new Promise(function(resolve, reject) {
	resolve(42);
});
p1.then(function(value) {
	console.log(value); 	// 42
	// create a new promise
	let p2 = new Promise(function(resolve, reject) {
    	resolve(43);
	});
	return p2
}).then(function(value) {
	console.log(value); 	// 43
});


//----------------------

 
// Responding to Multiple Promises
// The Promise.all() Method
// The Promise.all() method accepts a single argument, which is an iterable 
// (such as an array) of promises to monitor,

let p1 = new Promise(function(resolve, reject) {
  setTimeout(function(){ resolve(10); }, 1000)
});
let p2 = new Promise(function(resolve, reject) {
  setTimeout(function(){ resolve(0.5); }, 500)
});
let p3 = new Promise(function(resolve, reject) {
  setTimeout(function(){ resolve(20); }, 4000)
});
let p4 = Promise.all([p1, p2, p3]);

p4.then(function(value) {
    // This fulfillment handler will call on all Promises 
    // resolved (after 4 second)
	console.log(Array.isArray(value));  // true
	console.log(value[0]);          	// 10
	console.log(value[1]);          	// 0.5
	console.log(value[2]);          	// 20
});
 
// If any promise passed to Promise.all() is rejected, the returned promise is
// immediately rejected without waiting for the other promises to complete:
let p1 = new Promise(function(resolve, reject) {
  setTimeout(function(){ resolve(10); }, 1000)
});
let p2 = new Promise(function(resolve, reject) {
  setTimeout(function(){ reject(0.5); }, 500)
});
let p3 = new Promise(function(resolve, reject) {
  setTimeout(function(){ resolve(20); }, 4000)
});
let p4 = Promise.all([p1, p2, p3]);

p4.then(function(value) {
    // will not call
	console.log(Array.isArray(value)); 
	console.log(value[0]);          	
	console.log(value[1]);          	
	console.log(value[2]);          	
}).catch(function(value) {
    // The rejection handler for p4 is called immediately without 
    // waiting for p1 or p3 to finish executing (after 0.5 Second)
	console.log(Array.isArray(value))   // false
	console.log(value);             	// 0.5
});
// The rejection handler always receives a single value rather than an array,
// and the value is the rejection value from the promise that was rejected.


//----------------------

 
// The Promise.race() Method
// When resolve first Promise
// As like race who will come first will be winner, like that which Promise 
// handler call first (resolve or reject) will trigger their haldler
// (fulfilment or catch) and other Promise handler will ignore. The returned 
// promise is settled as soon as the first promise is settled. Instead of 
// waiting for all promises to be fulfilled
let p1 = new Promise(function(resolve, reject) {
  setTimeout(function(){ resolve(10); }, 1000)
});
let p2 = new Promise(function(resolve, reject) {
  setTimeout(function(){ resolve(0.5); }, 500)
});
let p3 = new Promise(function(resolve, reject) {
  setTimeout(function(){ resolve(20); }, 4000)
});
let p4 = Promise.race([p1, p2, p3]);

p4.then(function(value) {
    // This p2 fulfillment handler will call only one time 
    // when p2 resolved (after 0.5 second). Other will not call
	console.log(value);          	// 0.5
});
 
 
// When reject first Promise
// The returned promise is settled as soon as the first promise is settled. 
// Instead of waiting for all promises to be fulfilled
let p1 = new Promise(function(resolve, reject) {
  setTimeout(function(){ resolve(10); }, 1000)
});
let p2 = new Promise(function(resolve, reject) {
  setTimeout(function(){ reject(0.5); }, 500)
});
let p3 = new Promise(function(resolve, reject) {
  setTimeout(function(){ resolve(20); }, 4000)
});
let p4 = Promise.race([p1, p2, p3]);

p4.then(function(value) {
    // will not call
	console.log(value);
}, function(value) {
    // This p2 reject handler will call only one time when p2 reject 
    // (after 0.5 second). Other will not call
	console.log(value);          	// 0.5
});


//----------------------

 
// Inheriting from Promises
// Just like other built-in types, you can use a promise as the base for a 
// derived class. The success() method mimics resolve() and failure() mimics 
// the reject() method
class MyPromise extends Promise {
	// create custom then function by name success
	success(resolve, reject) {
    	return this.then(resolve, reject);
	}
	// create custom catch or reject function by name failure
	failure(reject) {
    	return this.catch(reject);
	}
}
let promise = new MyPromise(function(resolve, reject) {
	resolve(42);
});

promise.success(function(value) {
	console.log(value);         	// 42
}).failure(function(value) {
	console.log(value);
});
```



<br>
<hr>


<br><br>



## Regular expressions
```javascript
let result = "Hello, World!".test(/Hello/);
// or 
let myString = "Hello, World!";
let myRegex = /Hello/;
let result = myRegex.test(myString);
console.log(myRegex.test(myString)); // true
```
<br>

#### Match a Literal String with Different Possibilities
```javascript
let petString = "James has a pet cat.";
let petRegex = /dog|cat|bird|fish/;
let result = petRegex.test(petString);
console.log(result) // true
```

#### Ignore Case While Matching
```javascript
// The i flag use to ignore uppercase letters and lowercase. 
// You can use it by appending it to the regex.
let myString = "Hello, World!";
let fccRegex = /hello, world!/i; // Change this line
let result = fccRegex.test(myString);
console.log(result); // true
```
<br>

#### Extract Matches
```javascript
// Extract the actual matches you found with the .match() method.
"Hello, World!".match(/Hello/);  
/* --- output ---
[ 'Hello', 
  index: 0, 
  input: 'Hello, World!', 
  groups: undefined ] */
//
let ourStr = "Regular expressions";
let ourRegex = /expressions/;
ourStr.match(ourRegex);
/* -- output --
[ 'expressions',
  index: 8,
  input: 'Regular expressions',
  groups: undefined ] 
*/
```
<br>

#### Find More Than the First Match
```javascript
// To search or extract a pattern more than once, 
// you can use the g flag.
let twinkleStar = "Twinkle, twinkle, little star";
let result_1 = twinkleStar.match(/Twinkle/g);
let result_2 = twinkleStar.match(/Twinkle/ig);
console.log(result_1);   // [ 'Twinkle' ]
console.log(result_2);   // [ 'Twinkle', 'twinkle' ]
```
<br>

#### Match Anything with Wildcard Period
```javascript
// The wildcard character . (dot) will match any one character.
// You can use the wildcard character just like any other 
// character in the regex. For example, if you wanted to match 
// hug, huh, hut, and hum, you can use the regex /hu./ to match 
// all four words.
/hu./.test("I'll hum a song")  // true
/hu./.test("I'll hu a song")  // true
/hu./.test("I'll humm a song")  // true
/hu. /.test("I'll humm a song")  // false
/ hu./.test("I'll hhu a song")   // false
/.un/.test("Have fun with friends!")  // true
/ .un/.test("Have ffun with friends!")  // false
/ ..un/.test("Have ffun with friends!")  // true
```
<br>

#### Match Single Character with Multiple Possibilities
```javascript
// You want to match bag, big, and bug but not bog. 
// You can create the regex /b[aiu]g/ to do this. 
// The [aiu] is the character class that will only match 
// the characters a, i, or u.
let bigStr = "big";
let bagStr = "bag";
let bugStr = "bug";
let bogStr = "bog";
let bgRegex = /b[aiu]g/;
bigStr.match(bgRegex);  // ["big"]
bagStr.match(bgRegex);  // ["bag"]
bugStr.match(bgRegex);  // ["bug"]
bogStr.match(bgRegex);  // null
```
<br>

#### Match Single Character with Multiple Possibilities
```javascript
// You want to match bag, big, and bug but not bog. 
// You can create the regex /b[aiu]g/ to do this. 
// The [aiu] is the character class that will only match 
// the characters a, i, or u.
let bigStr = "big";
let bagStr = "bag";
let bugStr = "bug";
let bogStr = "bog";
let bgRegex = /b[aiu]g/;
bigStr.match(bgRegex);  // ["big"]
bagStr.match(bgRegex);  // ["bag"]
bugStr.match(bgRegex);  // ["bug"]
bogStr.match(bgRegex);  // null
```
<br>

#### Match Letters of the Alphabet
```javascript
// You want to match bag, big, and bug but not bog. 
// You can create the regex /b[aiu]g/ to do this. 
// The [aiu] is the character class that will only match 
// the characters a, i, or u.
let bigStr = "big";
let bagStr = "bag";
let bugStr = "bug";
let bogStr = "bog";
let bgRegex = /b[aiu]g/;
bigStr.match(bgRegex);  // ["big"]
bagStr.match(bgRegex);  // ["bag"]
bugStr.match(bgRegex);  // ["bug"]
bogStr.match(bgRegex);  // null
```
<br>

#### Match Numbers and Letters of the Alphabet
```javascript
// /[0-5]/ matches any number between 0 and 5, 
// including the 0 and 5 and a to z alphabet.
let jennyStr = "Jenny8675309";
let myRegex = /[a-z0-5]/ig;
jennyStr.match(myRegex);
```
<br>

#### Match Single Characters Not Specified
```javascript
// Create a set of characters that you do not want to match. 
// These types of character sets are called negated character sets.
// in below example we are matching single characters not specified
let quoteSample = "abcdefgHIjk.";
let myRegex = /[^cbefhjk]/ig;
let result = quoteSample.match(myRegex);
console.log(result); // [ 'a', 'd', 'g', 'I', '.' ]
//
let quoteSample = "12345678.";
let myRegex = /[^327]/ig;
let result = quoteSample.match(myRegex);
console.log(result); // [ '1', '4', '5', '6', '8', '.' ]
//
let quoteSample = "3 blind mice.";
let myRegex = /[^0-9aeiou]/ig;
let result = quoteSample.match(myRegex);this line
console.log(result); // [ ' ', 'b', 'l', 'n', 'd', ' ', 'm', 'c', '.' ]
```
<br>

#### Match Characters that Occur One or More Times
```javascript
// To match character which appear one time or 
// has repeat one after another 
let stringA = "aabc";
let stringB = "aabcaaa";
let stringC = "aabcaaa abc";
let reg = /a+/ig
console.log( stringA.match(reg) );  // [ 'aa' ]
console.log( stringB.match(reg) );  // [ 'aa', 'aaa' ]
console.log( stringC.match(reg) );  // [ 'aa', 'aaa', 'a' ]
//
// observe in below example it check repetition of last character from given pattern
let stringA = "abab";
let stringB = "ab abbbab abbbbbbc";
let reg = /ab+/ig
console.log( stringA.match(reg) );  // [ 'ab', 'ab' ]
console.log( stringB.match(reg) );  // [ 'ab', 'abbb', 'ab', 'abbbbbb' ]
```

#### The Asterisk (*)  - Pending
```javascript
// Pending
// https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/regular-expressions/match-characters-that-occur-zero-or-more-times
```

<br>
<hr>


<br><br>



## Recursion
#### [Recursion - Return Sub of Array](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/replace-loops-using-recursion)
```javascript
/*
A recursive function that returns 
the sum of the first n elements of an array arr
*/
function sum(arr, n) {
  if(n <= 0) {
    return 0;
  } else {
    return sum(arr, n - 1) + arr[n - 1];
  }
}
sum([1], 0)           // return 0
sum([2, 3, 4], 1)     // return 2
sum([2, 3, 4, 5], 3)  // return 9
```

<br><br><br>

#### [Recursion - to Create a Countdown](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/use-recursion-to-create-a-range-of-numbers)
```javascript
function countup(n) {
  if (n < 1) {
    return [];
  } else {
    const countArray = countup(n - 1);
    countArray.push(n);
    return countArray;
  }
}
console.log(countup(5));
// The value [1, 2, 3, 4, 5] will be displayed in the console.
```



<br><br><br>


#### [Recursion - to Create a Range of Numbers](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/use-recursion-to-create-a-countdown)
```javascript

/*
rangeOfNumbers(1, 5) should return [1, 2, 3, 4, 5]
rangeOfNumbers(6, 9) should return [6, 7, 8, 9]
rangeOfNumbers(4, 4) should return [4]
*/
// Solution 1
function rangeOfNumbers(startNum, endNum) {
  if (endNum - startNum === 0) {
    return [startNum];
  } else {
    var numbers = rangeOfNumbers(startNum, endNum - 1);
    numbers.push(endNum);
    return numbers;
  }
}

// Solution 2
function rangeOfNumbers(startNum, endNum) {
  return startNum === endNum
    ? [startNum]
    : rangeOfNumbers(startNum, endNum - 1).concat(endNum);
}

// Solution 3
function rangeOfNumbers(startNum, endNum) {
  return startNum === endNum
    ? [startNum]
    : [...rangeOfNumbers(startNum, endNum - 1), endNum ];
}
// The value [1, 2, 3, 4, 5] will be displayed in the console.
```





<br>
<hr>


<br><br>



## Debugging
```javascript
// console.log() - To print output use console.log
var name = "Shailendra";
var surname = "more";
console.log(name, surname)

//-- clear() - To Clear Console use 
console.clear();

// typeof - Use typeof to Check the Type of a Variable
console.log(typeof "");  // string
console.log(typeof 0);   // number
console.log(typeof []);  // object
console.log(typeof {});  // object

// constructor
let duck = new Bird();
let beagle = new Dog();
console.log(duck.constructor === Bird); // true
console.log(beagle.constructor === Dog); // true
console.log(beagle.constructor === Bird); // false

// isPrototypeOf
function Bird(name) {
  this.name = name;
}
let duck = new Bird("Donald");
Bird.prototype.isPrototypeOf(duck); // true

// instanceof - check an Object's Constructor with instanceof
let Bird = function(name, color) {
  this.name = name;
}
let crow = new Bird("Alexis", "black");
crow instanceof Bird;   // true


// hasOwnProperty - 
function Bird(name) {
  this.name = name;  //own property
}
Bird.prototype.numLegs = 2; // prototype property
let duck = new Bird("Donald");
duck.hasOwnProperty("name") // true
duck.hasOwnProperty("numLegs") // false
```


<br>
<hr>

<br><br><br>




----------
<br><br><br><br><br><br>