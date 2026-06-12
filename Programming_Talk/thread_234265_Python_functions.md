---
title: "Python functions"
date: 2006-08-11
forum: Programming Talk
---

### Post by jordilin on 2006-08-11
A very basic question
I have this code:
```

def hello(x):
[INDENT]x=4[/INDENT]

x=6
hello(x)
print x

```
and the result is 6 and not 4.
Why x remains the same, when in python function calls are made by reference? Anyone to explain clearly what's going on behind the scenes?

---

### Post by dabear on 2006-08-11
No, parameter values are evaluated when the function definition is executed. You would have to use a mutable object such as a list or dictionary to get that effect
[quote="ipython console"]
In [8]: def hello(x=[]):
   ...:     x.append('My name is Bond, Mr.Bond')
   ...:
   ...:

In [9]: x=['yo']

In [10]: hello(x)

In [11]: x
Out[11]: ['yo', 'My name is Bond, Mr.Bond']

In [12]:
[/quote]

---

### Post by Note360 on 2006-08-11
or you could also do something like this

```

# defines function hello and assigns the default value of x to 4
def hello(x=4):
    x = 6
    return x

x = 4
x = hello(x)

```
If you do that x will be 6

---

### Post by dabear on 2006-08-11
> **Note360 said:**
> or you could also do something like this

```

# defines function hello and assigns the default value of x to 4
def hello(x=4):
    x = 6
    return x

x = 4
x = hello(x)

```
If you do that x will be 6
Yes, offcourse, but jordilin wanted a way to change a value directly, not by copying and assigning a function return value to a variable. I believe he already knows how to do what you showed here; its pretty basic python

---

### Post by jordilin on 2006-08-11
> **dabear said:**
> Yes, offcourse, but jordilin wanted a way to change a value directly, not by copying and assigning a function return value to a variable. I believe he already knows how to do what you showed here; its pretty basic python

Yes, I already know. I do want to know why it does not change when python passes values by object reference.

---

### Post by DirtDawg on 2006-08-11
I think x is only altered within the function.
```

def hell(x):
    print x
    x=4
    print x

x=6
hell(x)
6
4

print x
6

```

---

### Post by jordilin on 2006-08-11
> **DirtDawg said:**
> I think x is only altered within the function.
```

def hell(x):
    print x
    x=4
    print x

x=6
hell(x)
6
4

print x
6

```
Yes, why?

---

### Post by DirtDawg on 2006-08-11
I believe it was intentionally designes that way. Unless you specifically tell the function to alter the global variable x, it will only alter the local instance of x. 

In other words, when x is placed into the hello() function, it only assignes the value of the global x object to the x namespace created when the function is run. The x inside the function is entirely sperate from the global x. 

I'm not sure I'm clear. 

Imagine hello() like this:
```

def hello(x):
    y=x
    print y
    y=4
    print y

x=6

hello(x)
6
4

print x
6

```
Essentially, this code is exactly the same. You don't expect a reassignment of y to change x because they're two different things.

I hope this addresses the issue and isn't a total symantic mess.

---

### Post by DirtDawg on 2006-08-11
Oops! Double post :D

---

### Post by cwaldbieser on 2006-08-12
> **jordilin said:**
> Yes, I already know. I do want to know why it does not change when python passes values by object reference.

You are correct that python passes parameters by object reference.

In your function, the variable x at module scope is is bound to the number 6.  6 is an immutable object; you cannot change it.  You can bind the name "x" to another object, though.

When you make the call hello(x), the reference to the object 6 that is bound to the name "x" at modual scope is bound to the name "x" at local scope.  The name "x" at local scope is rebound to another object, 4.  However, the name "x" at modual scope is not rebound to any object.

---

### Post by NewWithoutClue on 2006-08-13
This is how i would go about it:

```


def blah():
    global x; x=2

if __name__ == '__main__':
    x=4; blah(); print str(x)


```

Output:
2

Regards,
Paul

---

### Post by DirtDawg on 2006-08-13
> **NewWithoutClue said:**
> This is how i would go about it:

```


def blah():
    global x; x=2

if __name__ == '__main__':
    x=4; blah(); print str(x)


```

Output:
2

Regards,
Paul

Or:
```

def ohell(x):
    import __main__
    __main__.x= 4
    print x

if __name__ == '__main__':
    x=6
    ohell(x); print x

6
4

```
:grin:

---

### Post by Van_Gogh on 2006-08-13
> **DirtDawg said:**
> Or:
```

def ohell(x):
    import __main__
    __main__.x= 4
    print x

if __name__ == '__main__':
    x=6
    ohell(x); print x

6
4

```
:grin:

Nice trick :-)

---

### Post by NewWithoutClue on 2006-08-14
> **Van_Gogh said:**
> Nice trick :-)

Ditto

---

### Post by chonger on 2006-08-15
It is intentionally designed. I think the hangup in on that phrase "pass by reference". 

Better way to think about python functions is this.

```
def function(local_x):
   local_x = 1
```


What if you called?

> function(3)

Should python now change "3" into "2"?

You can think about things this way.

```
def function(local_x):
   local_x = 1
```

When function is called, by default there is a variable called local_x. The default value of local_x will be the value passed in. When you call local_x = 1. You are trying to say, replace the value of local_x with the value '1'. You are not saying, find the object local_x points to, and replace that object's value with 1.

---

### Post by LordHunter317 on 2006-08-15
> **jordilin said:**
> Yes, I already know. I do want to know why it does not change when python passes values by object reference.Clearly, python is passing-by-value in this case, not by reference.

Internally, it is pass-by-reference, but the scoping rules are weird (all of python's scoping rules are weird and inconsistent, big surprise there).

---

### Post by DirtDawg on 2006-08-16
> **NewWithoutClue said:**
> Ditto

Thanks guys, but I certaintly didn't think of that. I read about it in something(?) written by smarter men than myself.

---

### Post by chonger on 2006-08-16
> Clearly, python is passing-by-value in this case, not by reference.

Internally, it is pass-by-reference, but the scoping rules are weird (all of python's scoping rules are weird and inconsistent, big surprise there).

Why is it so weird? Where is it inconsistent? The hang up is that "passing by value" and "passing by reference" are usually used (and have special meanings) to C/C++ programmers. Python and other higher level languages are simply very different beasts.

---

### Post by LordHunter317 on 2006-08-16
> **chonger said:**
> Why is it so weird? Where is it inconsistent?Demonstrated right there.  If integers are really immutable then code of the form:```
def y(x)
  x = 3
```Should be illegal, because the reference is immutable.  That means: we can't change it. But it's not, so clearly python is effectively passing-by-value.

Actually, python is always pass-by-value.  It just happens it's always passing object references (making it effectively pass-by-pointer).

It also just so happens that immutable objects are always copy constructed when entering function scope.  Some people call this pass-by-assignment.

It also just so happens that "immutable" objects are nothing of the sort because again, this would be illegal:```
x = 2 
print x
x = 3 # Error, object is immutable, can't change it's value
print x

```But the code works, so clearly "immutable" objects are nothing of the sort.  What is true is the reference can't be *reseated* (meaning, made to point to another place in memory), but that's true of all languages that actually have references (e.g., C++, Pascal).

> The hang up is that "passing by value" and "passing by reference" are usually used (and have special meanings) to C/C++ programmers.No, they do not.  They have special meaning to python programmers because it has totally broken scoping rules, and no one clearly explains them.

C and C++ are perfectly consistent in their meanings of pass-by-reference and pass-by-value.  Especially seeing as C doesn't have pass-by-reference at all.

> Python and other higher level languages are simply very different beasts.Nope, sorry.  Python is in the same class as PHP and Perl with just plain weird and poor scoping rules.

---

### Post by jordilin on 2006-08-16
> **LordHunter317 said:**
> Python is in the same class as PHP and Perl with just plain weird and poor scoping rules.
I would not say Python has weird and poor scoping rules. Python is widely used and adopted by the software industry. The problem is that this particular question is not very well explained by books, howtos and tutorials, and it's in fact a crucial question to understand what's going on behind the scenes.

---

### Post by LordHunter317 on 2006-08-16
> **jordilin said:**
> I would not say Python has weird and poor scoping rules.But it does.  See the explanation of how it really works above.  That's clearly not consistent with any other language.  If you really want, I'll write the C++ to prove it.  

That's ignoring all the other scoping issues Python has.

> The problem is that this particular question is not very well explained by books,It wouldn't have to be if the rules were more consistent, and Python's use of terminology was consistent with the rest of the world.

---

### Post by jordilin on 2006-08-16
LordHunter317, when you say
```

x = 2 
print x
x = 3 # Error, object is immutable, can't change it's value
print x

```
In theory it should not be an error. Everything in python is an object, so when you do
```
x=3
```
you are creating another object named "3" and x is now pointing to this new object. The value "2" is not being changed, and x is merely a pointer. The variable x can be changed to point to any object you create, being a list, number or anything. 
if you write:
```

x=2
print x
print id(x)
x=3
print x
print id(x)

```
you'll get the idea.
Python clearly states that numbers, strings and tuples are immutable. So, effectively in the example you are not trying to change the value "2" because you can't, instead you are creating a new object "3" and binding it to x.

---

### Post by LordHunter317 on 2006-08-16
> you are creating another object named "3" and x is now pointing to this new object.Which means Python references, just like Java and C#, are really pointers.

> Python clearly states that numbers, strings and tuples are immutable.Yes.  I was partly confused because I didn't understand all the rules.  Now that I understand that Python is doing 'pass-a-pointer-by-value always', just like Java or C#, there is no problem.

---

### Post by neilp85 on 2006-08-16
The order in which python attempts to find a bound variable is clearly defined. First the local namespace isi checked, then the global namespace, and if both those fail it checks the built-in namespace as a last resort. I think this example may be a little bit more clear than previous ones.

```
def hello(x):
    x = 4
    print x
    print locals()['x']
    print globals()['x']

def hello2(x):
    globals()['x'] = 4


>>>x = 6
>>>hello(x)
4
4
6
>>>print x
6
>>>hello2(x)
>>>print x
4
``` 

The locals() and globals() functions return a dictionary where the keys are the names of the variables as strings and the values are the actual values of the those variables for the respective namespace. I find the globals() function to be a clearer way of accessing variables in the global namespace as apposed to importing the __main__ module.

---

### Post by LordHunter317 on 2006-08-16
But they're not.  If it was really as you say, then the 'global' statement wouldn't be needed.  But it is, so clearly things aren't as easy as one wishes.

---

### Post by neilp85 on 2006-08-16
I simply offered my example as another way of approaching how python handles namespace. The parameter list for functions are part of the local namespace and as such any arguments passed to those functions are copied to the local namespace. As a note, the dictionary returned by a call to locals() is read only unlike the one returned by globals() which can be used to modify variables in the global namespace.

---

### Post by jordilin on 2006-08-16
> **LordHunter317 said:**
> Which means Python references, just like Java and C#, are really pointers.
Yes, variables are pointers to objects residing in memory. 

> Yes.  I was partly confused because I didn't understand all the rules.  Now that I understand that Python is doing 'pass-a-pointer-by-value always', just like Java or C#, there is no problem.

LordHunter317, what do you understand by pass-a-pointer-by-value? Pointers are always passed by value, aren't they? I mean, being C, C++ or whatever, you are always passing the value of the pointer, which has the address of the object it points to.

---

### Post by chonger on 2006-08-16
> **LordHunter317 said:**
> 
C and C++ are perfectly consistent in their meanings of pass-by-reference and pass-by-value.  Especially seeing as C doesn't have pass-by-reference at all.

Nope, sorry.  Python is in the same class as PHP and Perl with just plain weird and poor scoping rules.

What I mean is the way Python handles function parameters is consistent within itself. However, it is very different from languages such as C and C++. 

When you say "Nope". Do you mean Python is very similar in design with C and C++ and Python programmers needs to think in terms of C/C++? 

Are the scoping rules for Python, PHP, and Perl really "poor", or just different?

The fact is, the scoping rules for Python, as designed, has their advantages. One of which is that when you pass a object into a function, you do not have to worry about that object being erased into null by the function.

---

### Post by LordHunter317 on 2006-08-16
> **jordilin said:**
> Pointers are always passed by value, aren't they?Not always.  .NET permits pass-by-reference for "reference types" (meaning objects you always have a pointer to).  C# and VB.NET both support this, though it's rarely used.

In C, C++, and Java it is impossible, however.

---

### Post by LordHunter317 on 2006-08-16
> **chonger said:**
> What I mean is the way Python handles function parameters is consistent within itself.But scoping isn't consistent overall.  I can access global variables from function scope, but I can't assign to them.  It should be both or neither.

> When you say "Nope". Do you mean Python is very similar in design with C and C++ and Python programmers needs to think in terms of C/C++? No, I mean the rules are poor.  See above.  That's a terrible rule really.  Too easy to make a mistake.


Frankly, I think explict variable declaration should always be a strict requirement.  But if you don't agree, then the fact that the scoping should be consistent is a requirement.  Python's isn't.

> One of which is that when you pass a object into a function, you do not have to worry about that object being erased into null by the function.But I don't have to worry about that with C (if people wrote const-correct code) or C++, or C#, or Java either.  And they have the benefit of not treating globals in an inconsistent way.

---

### Post by chonger on 2006-08-16
> But I don't have to worry about that with C (if people wrote const-correct code). 


The point is, you don't have to worry about it in Python at all. Perhaps a better way to state it is that, you don't have to worry about people writing correct code to make sure things like that don't happen.

> I can access global variables from function scope, but I can't assign to them.  

You could (if you write correct code).

---

### Post by LordHunter317 on 2006-08-16
> **chonger said:**
> You could (if you write correct code).Great job on completing missing the point.  Try interpreting the statement in context.

I thought we'd all learned from perl that mixed dynamic/lexical scoping was bad.

---

### Post by jordilin on 2006-08-16
> **LordHunter317 said:**
> Not always.  .NET permits pass-by-reference for "reference types" (meaning objects you always have a pointer to).  C# and VB.NET both support this, though it's rarely used.

In C, C++, and Java it is impossible, however.

Yes, but I still don't understand. What's the meaning about passing a pointer by value. Could you explain that, please?

---

### Post by LordHunter317 on 2006-08-16
Here's a quick and dirty C# example:```

public class Example {

	public static void Main()
	{
		// You can only get a pointer to reference types (i.e., class Foo) 
		StringBuilder builder = new StringBuilder();

		// The pointer is passed-by-value here.
	    PassByValue(builder);
        Console.WriteLine(builder == null);

		PassByRef(ref builder);
		Console.WriteLine(builder == null);
	}

	// This method takes a pointer in pass-by-value.  This means that changes
    // to the object it points to (i.e., calling .Append()) will effect the
	// object and be seen by the caller.  However, reseating the pointer
	// (i.e., setting it to null) has no effect on the caller.
	public static void PassByValue(StringBuilder arg)
	{
		arg = null;
	}

	// This method tkaes a pointer in pass-by-reference.  This means that
	// changes to the object that is pointed to and reseating the pointer will
	// have an effect on the caller.
	public static void PassByReference(ref StringBuilder arg)
	{
		arg = null;
	}
}
```If it doesn't compile, my bad.  Anyway, the difference between passing by reference and passing by value should be clear.  If I pass a pointer by reference, I can change what object it is pointed to in the caller's scope.  If I pass it by value, reseating the pointer has no effect outside the called function.

To be clear: Java, Python, C++, and C always pass pointers by-value.  C++ also supports pass-by-reference, but not for pointers.

In fact, of those languages, only C++ supports any mode other than pass-by-value all the time.

C# and other .NET languages support passing pointers both by-value (default) and by reference.

---

### Post by jordilin on 2006-08-16
> **LordHunter317 said:**
> Here's a quick and dirty C# example:```

public class Example {

	public static void Main()
	{
		// You can only get a pointer to reference types (i.e., class Foo) 
		StringBuilder builder = new StringBuilder();

		// The pointer is passed-by-value here.
	    PassByValue(builder);
        Console.WriteLine(builder == null);

		PassByRef(ref builder);
		Console.WriteLine(builder == null);
	}

	// This method takes a pointer in pass-by-value.  This means that changes
    // to the object it points to (i.e., calling .Append()) will effect the
	// object and be seen by the caller.  However, reseating the pointer
	// (i.e., setting it to null) has no effect on the caller.
	public static void PassByValue(StringBuilder arg)
	{
		arg = null;
	}

	// This method tkaes a pointer in pass-by-reference.  This means that
	// changes to the object that is pointed to and reseating the pointer will
	// have an effect on the caller.
	public static void PassByReference(ref StringBuilder arg)
	{
		arg = null;
	}
}
```If it doesn't compile, my bad.  Anyway, the difference between passing by reference and passing by value should be clear.  If I pass a pointer by reference, I can change what object it is pointed to in the caller's scope.  If I pass it by value, reseating the pointer has no effect outside the called function.

To be clear: Java, Python, C++, and C always pass pointers by-value.  C++ also supports pass-by-reference, but not for pointers.

In fact, of those languages, only C++ supports any mode other than pass-by-value all the time.

C# and other .NET languages support passing pointers both by-value (default) and by reference.

thanks LordHunter317, I think I'm getting the point. I'll take a closer look at it. If not, I'll post again.

---

### Post by jordilin on 2006-08-16
LordHunter317, when you say:
> This method takes a pointer in pass-by-value.  This means that changes
    // to the object it points to (i.e., calling .Append()) will effect the
	// object and be seen by the caller.  However, reseating the pointer
	// (i.e., setting it to null) has no effect on the caller.
The pointer, instead of being resetted, if it points to another value (object), the result is the same, isn't it?

---

### Post by jordilin on 2006-08-16
I see. In the passbyvalue function, when arg is set to point to null, the caller does not see that arg points to another object, so builder stays the same. In the second case builder will point to another object (in this case null) and will forget about the object created at the very beginning.

---

### Post by LordHunter317 on 2006-08-16
When you return to the caller's scope, yes.  It's like the pointer was never reseated.

I'll try to summerize the rules:[list=1][*]Pass type by value: The called function can modify the value as it sees fit.  Any changes made are not seen by the calling function.  A simple prototype is:```
void func1(int foo)
```If func1 changes foo in any way, the change is never seen outside of func1.
[*]Pass type by reference: The called function can modify the value as it sees fit.  Any change is seen by the calling function.  A simple C++ prototype is:```
void func2(int& foo)
```If func2 sets the value of foo to 3, the calling function will see that when func2 returns.[*]Pass pointer by value:The called function can modify the *pointed-to* object as it sees fit.  Any changes to the *pointed-to* type are seen by the calling function.  However, any changes to *what the pointer points to* are not seen.  I gave an example above.[*]Pass pointer by reference: The called function can modify both the pointed-to object and the pointer and both changes are seen by the caller.  I gave an example above.[/list]

I should point out that 3 and 4 in that list are no different from 1 and 2, respectively.  It's the property of a pointer that we can dereference it and get another object that enables one to pass a pointer by value and modify something else.

In fact, that's the whole reason to pass a pointer in C.  You pass a pointer to modify *something else, **not** the pointer.*  A passed pointer behaves no differently from a passed int in C. 

In Java, this fact is hidden from you because you deal with pointers all the time, except for the few primative types (i.e., int, char, byte, etc.).

I hope that helps some too.

---

### Post by LordHunter317 on 2006-08-16
> **jordilin said:**
> I see. In the passbyvalue function, when arg is set to point to null, the caller does not see that arg points to another object, so builder stays the same. In the second case builder will point to another object (in this case null) and will forget about the object created at the very beginning.Exactly.  That's the difference between pass-by-reference and pass-by-value.  Changes made to a parameter passed-by-value are never seen outside the called function.  Changes made to a parameter passed-by-reference are.

The confusing part is that in Python, Java, C#, etc., you're dealing with pointers (almost) all of the time, so it's not apparent that in:```
MyObject foo = new MyObject();

// This deferences the foo pointer to call a function on MyObject
foo.bar();
```The pointer dereference is really happening, esp. if you're coming from a C background.

Then again, in Python, Java, C#, etc. you rarely have to worry about it either.

---

### Post by jordilin on 2006-08-16
> **LordHunter317 said:**
> When you return to the caller's scope, yes.  It's like the pointer was never reseated.

I'll try to summerize the rules:[list=1][*]Pass type by value: The called function can modify the value as it sees fit.  Any changes made are not seen by the calling function.  A simple prototype is:```
void func1(int foo)
```If func1 changes foo in any way, the change is never seen outside of func1.
[*]Pass type by reference: The called function can modify the value as it sees fit.  Any change is seen by the calling function.  A simple C++ prototype is:```
void func2(int& foo)
```If func2 sets the value of foo to 3, the calling function will see that when func2 returns.[*]Pass pointer by value:The called function can modify the *pointed-to* object as it sees fit.  Any changes to the *pointed-to* type are seen by the calling function.  However, any changes to *what the pointer points to* are not seen.  I gave an example above.[*]Pass pointer by reference: The called function can modify both the pointed-to object and the pointer and both changes are seen by the caller.  I gave an example above.[/list]

I should point out that 3 and 4 in that list are no different from 1 and 2, respectively.  It's the property of a pointer that we can dereference it and get another object that enables one to pass a pointer by value and modify something else.

In fact, that's the whole reason to pass a pointer in C.  You pass a pointer to modify *something else, **not** the pointer.*  A passed pointer behaves no differently from a passed int in C. 

In Java, this fact is hidden from you because you deal with pointers all the time, except for the few primative types (i.e., int, char, byte, etc.).

I hope that helps some too.
Thanks LordHunter317 for your explanation. Let's see if I finally understand:
So, Python passes pointers by value, so in a function, the pointer can point to anything else and the caller will not see the change. But the object it points to can be changed in the function and the caller will see the change done to the object. It must be clear, that the object must be a mutable object such as a List (array), because a number obviously cannot be changed. Is that right?

---

### Post by LordHunter317 on 2006-08-16
Yes, you've got it. :)  Much like in Java, if you change an immutable object, you really cause the pointer to point to a new object.

---

### Post by jordilin on 2006-08-16
Thanks LordHunter317 by your clear explanations. It seems that all doubts have been cleared!!! :D

---

