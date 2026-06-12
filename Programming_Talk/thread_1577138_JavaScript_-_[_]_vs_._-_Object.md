---
title: "JavaScript - [ ] vs . - Object"
date: 2010-09-18
forum: Programming Talk
---

### Post by Pergi on 2010-09-18
Hello Ubuntuers!

I have a question regarding the 'for in' looping statement of JavaScript.

Can you explain why from the 2 'for in' loops of the following code i get different output?

```

// Sourse code of 'test.js'

var myObject;
var myVar;

myObject = {
  a: "a",
  b: "b",
  c: "c"
};

document.writeln("Print the properties of myObject using .");
for (myVar in myObject) {
  document.writeln(myVar + ": " + myObject.myVar);
}

document.writeln("\nPrint the properties of myObject using []");
for (myVar in myObject) {
  document.writeln(myVar + ": " + myObject[myVar]);
}
```

```

// Source code of 'test.html'
<html><body><pre><script src="test.js"></script></pre></body> </html>

```

```

// output
Print the properties of myObject using .
a: undefined
b: undefined
c: undefined

Print the properties of myObject using []
a: a
b: b
c: c

```

I thought that [] and . operators are used interchangeably for retrieving the property of an object and that generally the . notation is preferred. So, why we have different output? :confused:

Thanks in advance,
Pergi

---

### Post by delfick on 2010-09-18
Hello,

The difference is that when you're doing dot notation you're accessing that particular key on the object.

When you're doing array notation in Javascript (well, generally any language that has such syntax), it evaluates what is inside the square brackets before  accessing the result on the object.

So essentially,

```

//Say we have a variable that equals "a"
var someVariable = "a";

//And some object that has a value for the key "a"
//And for the key "b"
var someObject = {
    a : "blah",
    b : "meh"
}

//We now have two ways of accessing the key "a"
//First way, is to access it directly through dot notation
console.log(somObject.a)   // Prints "blah" to the console

//Second way, is to use array notation
console.log(someObject[someVariable]) 
//This evaluates someVariable to "a" and then returns someObject.a

//This is useful because it allows us to specify that we want some value from the object
//And be able to specify what particular item at run time
//For example, if I change the value of someVariable
someVariable = "b"

//Now doing array notation using someVariable as the value, gives a different result
console.log(someObject[someVariable])    //Prints "meh" to the console

//Note that if we use dot notation, i.e.
console.log(someObject.someVariable)
//We're not doing anything with the variable someVariable, we are instead using the string "someVariable" as a key to the object
//This prints out undefined because there is no such key on someObject

```

As for dot notation being preferred.... not really. There is no difference between the two notations. It's just that there are limitations on the dot notation (can't access a key with spaces or some particular special letters) and the square notation allows our code to be a lot more dynamic :)

If you still have questions, fee free to ask :D

---

### Post by dv3500ea on 2010-09-19
Use . notation if you know the name of the key when you are writing the program.

Use [] notation if you don't know the name of the key until runtime.

The for in structure gets the name of every key in an object at *runtime* so you need to use [] notation.

---

### Post by Pergi on 2010-09-19
Thanks for your answers delfick and dv3500ea :)

@delfick
From what you said and what i found from my search, i concluded that the [ ] suffix accepts **only** strings, and like you said, reads the content in order to find the property.

```

var obj = { a: "hello" };

for (i in obj) {
  document.writeln(typeof i); // prints string
  document.writeln(obj[i]); // so it works
  document.writeln(obj.i); // undefined, i is string
}

```

From the other hand, the . notation doesn't accept strings.

```

document.writeln(obj.a); // it works
document.writeln(obj[a]); // error, because a is not string, it is not defined

```

Also, about the preference between [ ] and . notation, Douglas Crockford at his book "JavaScript: The Good Parts" mention the following.
*"The . notation is preferred because it is more compact and it reads better"*

---

