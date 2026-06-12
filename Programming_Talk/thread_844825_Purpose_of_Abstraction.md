---
title: "Purpose of Abstraction"
date: 2008-06-27
forum: Programming Talk
---

### Post by Miben on 2008-06-27
Can somebody tell me about overloading, overriden and abstraction in PHP5?I am not understand the usage of this..

---

### Post by xlinuks on 2008-06-27
There's a lot of useful info if you google for it, there are several wiki articles about overloading, here's method overloading (you can also find there info about overriding and so on):
[http://en.wikipedia.org/wiki/Method_overloading](http://en.wikipedia.org/wiki/Method_overloading)

PS: To understand "overloading" the language used as an example doesn't really matter

---

### Post by sshuber on 2008-06-27
Quite simply, overloading is where you have functions with the same exact name and type, but different arguments that are passed to them.

For instance:
int newnum(int a, int b, int c)
{
...
}
int newnum(int a, int b, int c, int d)
{
...
}

If I call newnum(1,2,3) it will run the first newnum function since I'm passing three int values..
If I call newnum(1,2,3,4) it will call the second newnum function since I'm passing four int values.

---

### Post by Miben on 2008-06-29
Thanks for help.Can somebody tell me when and why we do overriding and abstraction?Thanks...

---

### Post by Can+~ on 2008-06-29
> **Miben said:**
> Thanks for help.Can somebody tell me when and why we do overriding and abstraction?Thanks...

I can tell you when NOT to do it. Some tasks may be obscured with overloading, for example (pseudocode):

```
x = "hello" + 5
```

Produces "bananas", another programmer who sees this will expect the hello to be concatenated with the 5 or something like that, but gets completely shocked by the results and has to look inside the class (which is not the idea).

Overloading is used when it makes sense, for operators, usually when an object represents a certain data type, for example, a class money that can sum USD with GBP.

---

### Post by Miben on 2008-06-29
I am new in PHP, I'm not understand about abstraction.What is the purpose of abstraction? How to use it? Please help..

---

### Post by myrtle1908 on 2008-06-29
Have you tried searching on google, wikipedia etc?  Abstraction is not something specific to PHP rather it is a notion in computer programming in general.

[http://en.wikipedia.org/wiki/Abstraction_(computer_science](http://en.wikipedia.org/wiki/Abstraction_(computer_science))

[http://www.devshed.com/c/a/PHP/Abstract-Classes-in-PHP-Working-with-PHP-5/](http://www.devshed.com/c/a/PHP/Abstract-Classes-in-PHP-Working-with-PHP-5/)

---

### Post by Can+~ on 2008-06-30
> **myrtle1908 said:**
> Have you tried searching on google, wikipedia etc?  Abstraction is not something specific to PHP rather it is a notion in computer programming in general.

[http://en.wikipedia.org/wiki/Abstraction_(computer_science](http://en.wikipedia.org/wiki/Abstraction_(computer_science))

[http://www.devshed.com/c/a/PHP/Abstract-Classes-in-PHP-Working-with-PHP-5/](http://www.devshed.com/c/a/PHP/Abstract-Classes-in-PHP-Working-with-PHP-5/)

Broken link there
[http://en.wikipedia.org/wiki/Abstraction_(computer_science)](http://en.wikipedia.org/wiki/Abstraction_(computer_science))

---

### Post by Miben on 2008-06-30
Can someone tell me what is the purpose of using abstraction, static and magicMethod in PHP5??Please help me undestand it.Thnks..

---

### Post by escapee on 2008-06-30
Can you give us more insight into what exactly you're confused about for each and what you do understand about them?

In short, abstraction refers to reducing amount of what you need to know into multiple layers so as not to overload you or parts of your code.  (i.e. You don't need to know how a car works to drive it)

Static...well that depends on what context, but for the most part it always follows the definition of "static".  Let us know if you mean static typed, static variables, etc.

magicMethod...where are you seeing this?


Edit:  I just noticed you have two other threads open asking the same question.  In the future, just wait for answers in the one thread.  Amongst other reasons, it keeps the forums a bit cleaner and keeps your answers in one location.

---

### Post by pmasiar on 2008-06-30
Also, read FAQ, "how to ask questions" (also in my sig). Try better title next time.

---

### Post by Zugzwang on 2008-06-30
> **pmasiar said:**
> Also, read FAQ, "how to ask questions" (also in my sig). Try better title next time.

...not to mention avoidance of double-posting: [http://ubuntuforums.org/showthread.php?t=844825]("http://ubuntuforums.org/showthread.php?t=844825")

---

### Post by Can+~ on 2008-06-30
> **Zugzwang said:**
> ...not to mention avoidance of double-posting: [http://ubuntuforums.org/showthread.php?t=844825]("http://ubuntuforums.org/showthread.php?t=844825")

You just linked to the same topic?

Damn you recursion!

---

### Post by LaRoza on 2008-06-30
> **Can+~ said:**
> You just linked to the same topic?

Damn you recursion!

I merged the threads and retitled it.

Links to either thread will lead to this one.

---

### Post by Elsven on 2008-06-30
In C++ overloading is very useful when you want to have one function that can accept and handle more then one variable type.  For example if you have a function called add values and you want it to add integers, longs, shorts, and chars. So you would have an overloaded function to handle each one.  The name can stay the same however the function can handle multiple different types of inputs.  Another place they are commonly used is in initializing variables.   Say you have 3 variables, A, B, and C.  You need a function where you want to be able to initialize all of them with a custom value but this feature may not always be needed.  So you overload the constructor so you can just initialize A and B, C however will just default to a predetermined value.  Then the next time you initialize the class you want to give all variables a value so you can use the overloaded function to set all variables.  This is how things are for C++ I cannot say they are the same for PHP however I am sure the idea of overloading will stay relatively the same.

Regards,


Richard

---

### Post by Miben on 2008-06-30
I really dont understand at all about the abstraction? I cant imagine in what case in programming we use abstration?
For static, i only know about static variable.But, when i think about static, i dont know when i should declare static variable and static method? I hope somebody can give me a good understanding on it..Thnks!!

---

### Post by escapee on 2008-06-30
> **Miben said:**
> I really dont understand at all about the abstraction? I cant imagine in what case in programming we use abstration?
For static, i only know about static variable.But, when i think about static, i dont know when i should declare static variable and static method? I hope somebody can give me a good understanding on it..Thnks!!

Think of it as this - when you're using a class in PHP, you're using it's interface and are not concerned with how it works underneath.  That is abstraction.

You use static variables when you need to track a variable across multiple instances of a class object.  If you want to know how many times an object is instantiated, create a static variable and have it increment upon instantiation.

Try reading documents online, such as Wikipedia or searching Google.  There are lots that are very helpful.

---

### Post by CptPicard on 2008-06-30
> **Miben said:**
> I really dont understand at all about the abstraction? I cant imagine in what case in programming we use abstration?

Abstraction is just simply what you, as the programmer, **do** all the time. You create abstract models of things in your problem domain using the tools given to you by your language. Hopefully, those abstractions are useful in the sense that they make it clearer how your problem "works".

It would sort of suck to code everything in terms ones and zeroes, no? :)

This sounds almost like some extreme low limit of blub -- not understanding *any* level of abstraction (kudos to LaRoza for the idea) ;)

---

### Post by Miben on 2008-06-30
escappe...what u mean is when i declare a static variable, the purpose is to memorize the numbers of times an object is instantiated? Is that any other purpose?

Then, when we should declare a static method?Can you describe more about it?Thnks..

---

### Post by escapee on 2008-07-01
> **Miben said:**
> escappe...what u mean is when i declare a static variable, the purpose is to memorize the numbers of times an object is instantiated? Is that any other purpose?

Then, when we should declare a static method?Can you describe more about it?Thnks..

No, I just gave an example of what you *can* do with static variables.  They are used to act on the type itself and not on a particular instance.  Not to sound condescending, but I'm not sure knowing that's going to benefit you until you understand object-oriented programming more.  

Search Google for "Object-Oriented Programming" to learn more concepts. 

[URL="http://en.wikipedia.org/wiki/Object_oriented"]
http://en.wikipedia.org/wiki/Object_oriented[/URL]
Here is Wikipedia's entry on Object-Oriented Programming to get you started.  

[http://www.phpbuilder.com/manual/en/language.oop5.static.php]("http://www.phpbuilder.com/manual/en/language.oop5.static.php")
And here is an entry from a PHP manual on static variables/functions.

Good luck

---

