---
title: "C functions and data types"
date: 2008-03-17
forum: Programming Talk
---

### Post by raddmadd on 2008-03-17
I do not understand declaring functions and their data types, and the return statement.

Say for instance, that I declare a function to be of type int.  What does that do?   Does that mean that the functions value is of type int?

Now, say that I have a variable of type float, and I use the return statement to return that as my value... won't that interfere with the data type I declared my function as?

Also, say for instance I declare a function with a parameter that is of type int.  Now, when I call this function, say that I have a variable as this argument.  I do not understand how that works.  Is the variable's value used as the value for the parameter?

---

### Post by slavik on 2008-03-17
> I do not understand declaring functions and their data types, and the return statement.

Say for instance, that I declare a function to be of type int.  What does that do?   Does that mean that the functions value is of type int?
[quote]

the function's type is the type that it returns, a function declared as in returns an int, if it returns a float, the compiler will give an error.

[quote]
Now, say that I have a variable of type float, and I use the return statement to return that as my value... won't that interfere with the data type I declared my function as?

see  above, your code won't even compile in this way

> 
Also, say for instance I declare a function with a parameter that is of type int.  Now, when I call this function, say that I have a variable as this argument.  I do not understand how that works.  Is the variable's value used as the value for the parameter?

when you declare a parameter as an int, it will only take an int, it will not accept a floar. it is possible to cast types from one to another but there is a risk in losing information.

---

### Post by FunkyJack on 2008-03-17
See this
[http://www.cprogramming.com/tutorial/c/lesson4.html](http://www.cprogramming.com/tutorial/c/lesson4.html)

---

### Post by LaRoza on 2008-03-17
> **raddmadd said:**
> I do not understand declaring functions and their data types, and the return statement.

Say for instance, that I declare a function to be of type int.  What does that do?   Does that mean that the functions value is of type int?

Now, say that I have a variable of type float, and I use the return statement to return that as my value... won't that interfere with the data type I declared my function as?

Also, say for instance I declare a function with a parameter that is of type int.  Now, when I call this function, say that I have a variable as this argument.  I do not understand how that works.  Is the variable's value used as the value for the parameter?

To do a short explanation, I am going to use another language (which doesn't require datatypes to be declared)

Take this function:
[php]
function square(x)
{
    return x * x;
}
[/php]

It declared a function, which accepts one argument, and returns x * x (the square of it)

In C (and the language I am using as an example), the value you pass to the function is copied. In other words, the "x" inside the function exists only in the function. The function does return a value. So:

[php]
var x = 10;
var y;

y = square(x); // x still equals 10, but y equals 100
[/php]

The return value can be used by the calling code. Although I use the same names here, x in the function, and x that is declared to be 10, are not the same variable.

Now, in C, you have to declare the datatypes of the variables and functions. 

So:

[php]
int square(x)
{
    return x * x;
}

int x = 10;
int y;

y = square(x); // x still equals 10, but y equals 100
[/php]

If you find C to be too confusing, and you are wrestling with the static typing, you might find you will learn faster with another language. The "scripting languages" thread in the sticky will give you several.

---

### Post by Wybiral on 2008-03-17
And remember, C is a _**weakly-typed**_ language, so you have to know your types really well because the compiler doesn't always complain about things. This will throw a warning, but it will still compile:
```

int test()
{
    return "Hello" + 1;
}

```
Pay attention to those warnings (because it's all C will give you). Compile using the "-Wall" flag to get as many warnings as you can.

---

