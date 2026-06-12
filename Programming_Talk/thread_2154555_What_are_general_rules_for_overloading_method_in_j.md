---
title: "What are general rules for overloading method in java?"
date: 2013-06-15
forum: Programming Talk
---

### Post by pavelexpertov on 2013-06-15
Basically, I am trying to make methods to return a value when they are called from another method or class. I was wondering what conditions and rules I have to follow to make them work. If you want an example of what I meant, just ask me and I will update the post.

Here is an example of what I have done. [COLOR=#000000][FONT=Arial]I have created two classes. In the first class, I have tried to make a method in another class to return a value with a command to output value on the console. But I get an error that says there are incompatible types. Here are two classes that I have created and I wanted to make a calculator out of that: The first class:

[/FONT][/COLOR]```

[COLOR=#00008B]class[/COLOR] calc1
{ [COLOR=#00008B]public[/COLOR] [COLOR=#00008B]static[/COLOR] [COLOR=#00008B]int[/COLOR] num1; [COLOR=gray]//first number variable[/COLOR]    
[COLOR=#00008B]public[/COLOR] [COLOR=#00008B]static[/COLOR] [COLOR=#00008B]int[/COLOR] num2; [COLOR=gray]//Second number variable[/COLOR]    
[COLOR=#00008B]public[/COLOR] [COLOR=#00008B]static[/COLOR] [COLOR=#2B91AF]String[/COLOR] op; [COLOR=gray]//Operatior variable[/COLOR]    
[COLOR=#00008B]public[/COLOR] [COLOR=#00008B]static[/COLOR] [COLOR=#00008B]void[/COLOR] main([COLOR=#2B91AF]String[/COLOR][] args) [COLOR=gray]//[/COLOR]    
{        num1 = [COLOR=#2B91AF]Integer[/COLOR].parseInt(args[[COLOR=#800000]0[/COLOR]]);        
num2 = [COLOR=#2B91AF]Integer[/COLOR].parseInt(args[[COLOR=#800000]2[/COLOR]]);        
op = args[[COLOR=#800000]1[/COLOR]];        
calc3.calculate(op); [COLOR=gray]//Calling method from the second class with an arugement.[/COLOR]    
}
}[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]

Here is the second:

[/FONT][/COLOR]```

[COLOR=#00008B]class[/COLOR] calc3
{    [COLOR=#00008B]public[/COLOR] [COLOR=#00008B]static[/COLOR] [COLOR=#00008B]int[/COLOR] calculate([COLOR=#2B91AF]String[/COLOR] ops)    
{        
[COLOR=#00008B]switch[/COLOR](ops) [COLOR=gray]//I believe that ops stores value from op variable in the first class.[/COLOR]        
{ [COLOR=#00008B]case[/COLOR] [COLOR=#800000]"+"[/COLOR]: { [COLOR=#00008B]int[/COLOR] num = calc1.num1 + calc1.num2;                
[COLOR=#00008B]return[/COLOR] ([COLOR=#2B91AF]System[/COLOR].out.println(num));            
}       
}    
}
}
```[COLOR=#000000][FONT=Arial]

Here is an error message I get after I try to compile it:

[/FONT][/COLOR]```

[COLOR=#2B91AF]Desktop$[/COLOR] javac calc1.java
./calc3.java:[COLOR=#800000]10[/COLOR]: error: incompatible types        [COLOR=#00008B]return[/COLOR] ([COLOR=#2B91AF]System[/COLOR].out.println(num));^                                
required: [COLOR=#00008B]int[/COLOR] 
found:    [COLOR=#00008B]void
[/COLOR][COLOR=#800000]1[/COLOR] error


```
[COLOR=#000000][FONT=Arial]
PS. I believe it is not overriding process, but still I would like to know about calling methods and returning value when they are called.
[/FONT][/COLOR]

---

### Post by r-senior on 2013-06-15
I think we need an example. Be clear whether you mean overload or override. Check on Wikipedia if you aren't sure.

---

### Post by ofnuts on 2013-06-15
> when they are called from another method or class

Caller-dependent behavior? Gross :)

---

### Post by KdotJ on 2013-06-15
As r-senior said, I think with need more information of what you're trying to achieve.

---

### Post by sum1nil on 2013-06-15
If you have a class and want too override say, toString(), you would put the @Override notation before the method like:

public class SmartyPants
.........
@Override
 public String toString() {
return " Not gonna say!";
}

....
In class b, you instantiate a SmartPants object and call the overridden toString().

SmartyPant levis = new SmartyPants();

levis.toString() gives " Not gonna say!"

---

### Post by CptPicard on 2013-06-15
Actually, the @Override annotation is not in any way required. It provides the benefit of making the compiler actually check that you are, indeed, overriding a method from a superclass.

It is sufficient to just implement the same method in a subclass, and you get the overriding behaviour automatically.

---

### Post by sum1nil on 2013-06-15
Thank you, all this time I believed it required.

---

### Post by r-senior on 2013-06-16
> **pavelexpertov said:**
> Here is an error message I get after I try to compile it:

[/FONT][/COLOR]```

[COLOR=#2B91AF]Desktop$[/COLOR] javac calc1.java
./calc3.java:[COLOR=#800000]10[/COLOR]: error: incompatible types        [COLOR=#00008B]return[/COLOR] ([COLOR=#2B91AF]System[/COLOR].out.println(num));^                                
required: [COLOR=#00008B]int[/COLOR] 
found:    [COLOR=#00008B]void
[/COLOR][COLOR=#800000]1[/COLOR] error


```
[COLOR=#000000][FONT=Arial]
PS. I believe it is not overriding process, but still I would like to know about calling methods and returning value when they are called.
[/FONT][/COLOR]
It's usually better to add a new post to the thread rather than go back and edit a previous one with more information. A lot of people will just look at the last post, see there is nothing new and move on.

The compilation problem is that you are trying to return the return value of System.out.println from a method. System.out.println is a void method, so there is no return value. You probably want to return the result of the calculation as an int and print it using System.out.println in the calc1 class.

What's your programming background?

---

### Post by Leuchten on 2013-06-16
> **sum1nil said:**
> Thank you, all this time I believed it required.

It's definitely useful and can help cut down on bugs.

---

### Post by CptPicard on 2013-06-17
> **Leuchten said:**
> It's definitely useful and can help cut down on bugs.

On the other hand, inheritance and overriding is such a core mechanism in Java that it's vitally important to understand that it does *not *depend on an annotation. :)

---

### Post by pavelexpertov on 2013-06-21
> **r-senior said:**
> It's usually better to add a new post to the thread rather than go back and edit a previous one with more information. A lot of people will just look at the last post, see there is nothing new and move on.

The compilation problem is that you are trying to return the return value of System.out.println from a method. System.out.println is a void method, so there is no return value. You probably want to return the result of the calculation as an int and print it using System.out.println in the calc1 class.

What's your programming background?
My programming background is a beginner, but I managed to figure the problem out by reading and researching, so I manage to learn as well as to correct the problems.

---

### Post by jairoh_ on 2013-06-21
> **pavelexpertov said:**
> Basically, I am trying to make methods to return a value when they are called from another method or class. I was wondering what conditions and rules I have to follow to make them work. If you want an example of what I meant, just ask me and I will update the post.

Here is an example of what I have done. [COLOR=#000000][FONT=Arial]I have created two classes. In the first class, I have tried to make a method in another class to return a value with a command to output value on the console. But I get an error that says there are incompatible types. Here are two classes that I have created and I wanted to make a calculator out of that: The first class:

[/FONT][/COLOR]```

[COLOR=#00008B]class[/COLOR] calc1
{ [COLOR=#00008B]public[/COLOR] [COLOR=#00008B]static[/COLOR] [COLOR=#00008B]int[/COLOR] num1; [COLOR=gray]//first number variable[/COLOR]    
[COLOR=#00008B]public[/COLOR] [COLOR=#00008B]static[/COLOR] [COLOR=#00008B]int[/COLOR] num2; [COLOR=gray]//Second number variable[/COLOR]    
[COLOR=#00008B]public[/COLOR] [COLOR=#00008B]static[/COLOR] [COLOR=#2B91AF]String[/COLOR] op; [COLOR=gray]//Operatior variable[/COLOR]    
[COLOR=#00008B]public[/COLOR] [COLOR=#00008B]static[/COLOR] [COLOR=#00008B]void[/COLOR] main([COLOR=#2B91AF]String[/COLOR][] args) [COLOR=gray]//[/COLOR]    
{        num1 = [COLOR=#2B91AF]Integer[/COLOR].parseInt(args[[COLOR=#800000]0[/COLOR]]);        
num2 = [COLOR=#2B91AF]Integer[/COLOR].parseInt(args[[COLOR=#800000]2[/COLOR]]);        
op = args[[COLOR=#800000]1[/COLOR]];        
calc3.calculate(op); [COLOR=gray]//Calling method from the second class with an arugement.[/COLOR]    
}
}[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]

Here is the second:

[/FONT][/COLOR]```

[COLOR=#00008B]class[/COLOR] calc3
{    [COLOR=#00008B]public[/COLOR] [COLOR=#00008B]static[/COLOR] [COLOR=#00008B]int[/COLOR] calculate([COLOR=#2B91AF]String[/COLOR] ops)    
{        
[COLOR=#00008B]switch[/COLOR](ops) [COLOR=gray]//I believe that ops stores value from op variable in the first class.[/COLOR]        
{ [COLOR=#00008B]case[/COLOR] [COLOR=#800000]"+"[/COLOR]: { [COLOR=#00008B]int[/COLOR] num = calc1.num1 + calc1.num2;                
[COLOR=#00008B]return[/COLOR] ([COLOR=#2B91AF]System[/COLOR].out.println(num));            
}       
}    
}
}
```[COLOR=#000000][FONT=Arial]

Here is an error message I get after I try to compile it:

[/FONT][/COLOR]```

[COLOR=#2B91AF]Desktop$[/COLOR] javac calc1.java
./calc3.java:[COLOR=#800000]10[/COLOR]: error: incompatible types        [COLOR=#00008B]return[/COLOR] ([COLOR=#2B91AF]System[/COLOR].out.println(num));^                                
required: [COLOR=#00008B]int[/COLOR] 
found:    [COLOR=#00008B]void
[/COLOR][COLOR=#800000]1[/COLOR] error


```
[COLOR=#000000][FONT=Arial]
PS. I believe it is not overriding process, but still I would like to know about calling methods and returning value when they are called.
[/FONT][/COLOR]

use this instead
```

calc3 cal = new calc3();     
System.out.println( calc.calculate( pass the values here ) ); [COLOR=gray]//Calling method from the second class with an arugement.[/COLOR] 

```

and int calc3 class,
you cannot do this unless it extends calc1 and the variable should be global and public.
```

[COLOR=#00008B]int[/COLOR] num = calc1.num1 + calc1.num2;

```

---

