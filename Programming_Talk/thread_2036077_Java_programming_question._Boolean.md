---
title: "Java programming question. Boolean"
date: 2012-08-01
forum: Programming Talk
---

### Post by Drenriza on 2012-08-01
Hi guys.

So i was told if i wanted to check a boolean, if it is true or false. I could do it as follows

boolean end = false;

```

while(!end)

```
And that this would check if the boolean is false

```

while(end)

```
And this if it is true.

But i was wondering, how is it that you can skip the != and == signs in each loop. Is this just something that Java have implemented? Or is their a higher meaning. And can this only be done with boolean's or can it also be used in other situations? For loops, if then statements and so on.

Kind regards.

---

### Post by muteXe on 2012-08-01
both cases evaluate to a boolean so it's the same thing really.

i tend not to do:

```

while(!end)

```

but do 

```

while(end == false)

```

It's easier for a pleb like me to understand it when i re-read it again six months down the line.

---

### Post by davetv on 2012-08-01
It is the same in c/c++. I don't know about java, but in c you can use the same construct to check an integer value for zero or non-zero where zero=false, any other value =true.

Sometimes you might use the same for a pointer, declare a pointer and set it to NULL and you can test it with the same boolean construct and it will be false, if it has a value it =true.

And yes ... it should work for if for and repeat statements. Any sort of boolean test.


lol @ your next comment muteXe

---

### Post by muteXe on 2012-08-01
> **davetv said:**
> It is the same in c/c++. I don't know about java, but in c you can use the same construct to check an integer value for zero or non-zero where zero=false, any other value =true.


thankfully this type of thing is not allowed in java.

---

### Post by davetv on 2012-08-01
Hi muteXe ... why is that bad? Your "thankfully" comment gives me the vibe. Don't you think that is a versatile use of that construct?

I don't see it as confusing as long as you know the typedef and history of the tested variable.

---

### Post by schauerlich on 2012-08-01
The while loop condition only requires and expression that returns a boolean. There are many ways to have that happen, and not all of them involve an equals/not equals sign. This is a simple case, where just the variable's name gives you a boolean value, which the while loop checks for true/false. You can also do things like negate it, use a boolean and/or on it with other expressions, or return a boolean from a function (eg, while(iter.hasNext()).

The situation in C is slightly different. C has no innate boolean class, so the while loop condition looks for integers. If the integer is 0, the condition evaluates to false. Otherwise, it is true. C implicitly "casts" (reinterprets) a lot of things to int, which lets you put a few more things in the condition expression. Any numeric type checks whether it equals 0, and any other type casts to int and checks if that value is 0. In most cases this means checking if a pointer is null or not. C++ has a similar situation for primitive types because it is (mostly) a superset of C.

---

### Post by trent.josephsen on 2012-08-01
> **schauerlich said:**
> C implicitly "casts" (reinterprets) a lot of things to int

I know I should probably let this go, but casts are always explicit. The word you're looking for is "converts". 

```
int i = (int) 1.0; /* this line contains a cast (explicit conversion) */
int j = 1.0; /* this line relies on implicit conversion and doesn't have a cast */
```

---

### Post by muteXe on 2012-08-01
Just to add an example to extend to what schauerlich quite correctly is saying:

If you have 2 ints, variable1 and variable2, in C or C++ this is perfectly allowable:

```

if(variable1 - variable2)
{
    // do some stuff --- A
}
else
{
    // do some otherstuff   --- B
}

```

so you are 'if'ing on an integer (not a true or false), and if variable1 and 2 were the same then you'd get a if(0) i.e. it would evaluate to false and path B would execute.

This kinda thing wouldn't even compile in java. It expects, in an 'if', a built-in boolean type.

---

### Post by Bachstelze on 2012-08-01
> **schauerlich said:**
> 
C implicitly "casts" (reinterprets) a lot of things to int, which lets you put a few more things in the condition expression. Any numeric type checks whether it equals 0, and any other type casts to int and checks if that value is 0.

No! In C, when you write

```
if (foo)
```

it is interpreted as

```
if (foo != 0)
```

and then the usual rules for comparison apply. In some cases, there will be a *conversion* (not a cast!), but not always. In particular, if [font=monospace]foo[/font] is a pointer, the expression [font=monospace]foo != 0[/font] will have value [font=monospace]0[/font] is [font=monospace]foo[/font] is a null pointer, and [font=monospace]1[/font] otherwise. There is no conversion performed!

And it is not just pedantry, either. The conversion from pointer to int is implementation-defined, so it is possible that a null pointer [font=monospace]foo[/font], when cast to an [font=monospace]int[/font], will give a value of [font=monospace]1[/font]. Even then, though, the expression [font=monospace]foo != 0[/font] will still have value [font=monospace]0[/font], because [font=monospace]foo[/font] is a null pointer.

---

### Post by dagoth_pie on 2012-08-02
> **muteXe said:**
> 

```

while(end == false)

```

It's easier for a pleb like me to understand it when i re-read it again six months down the line.
But 6 months later... "What the hell does end mean!?"

---

### Post by Drenriza on 2012-08-02
> **dagoth_pie said:**
> But 6 months later... "What the hell does end mean!?"
.

---

### Post by muteXe on 2012-08-02
and you think that's worse than
```

while(end)
{
..
}

```

?

---

### Post by trent.josephsen on 2012-08-02
@Drenriza: Is there any possibility of that while loop running more than once? If not then why make it a while loop at all?

I usually read "while (!value)" as "until value" and "if (!value)" as "unless value", which is a little more intuitive to me than "while value is false" or "if value is false". But that's just the Perl speaking.

---

### Post by Drenriza on 2012-08-03
> @Drenriza: Is there any possibility of that while loop running more than once? If not then why make it a while loop at all?

I have the while loop because if i don't and an exception is thrown the program stops from where the exception was thrown.

---

### Post by muteXe on 2012-08-03
take out the while loop and understand why the exception is thrown.

---

### Post by Drenriza on 2012-08-03
> **muteXe said:**
> take out the while loop and understand why the exception is thrown.
 
O snap :)
 
I understand why the exception is thrown. But it is not something that can be helped to prevent it from being thrown, since it's a unknownhostname exception if i remember correctly. And this is thrown on some systems eachtime the program is run due to the system setup nature.
 
So the while loop prevents that this exception stops the program.

---

### Post by spjackson on 2012-08-03
> **Drenriza said:**
> O snap :)
 
I understand while the exception is thrown. But it is not something that can be helped to prevent it from being thrown, since it's a unknownhostname exception if i remember correctly. And this is thrown on some systems eachtime the program is run due to the system setup nature.
 
So the while loop prevents that this exception stops the program.
If you really think that's what a while loop does, you'd better read the relevant sections of your Java tutorial again. It's
```

try {
  ...
}
catch (...) {
  ...
}

```
that prevents the exception from stopping your program. The while loop has nothing whatsoever to do with it.

---

### Post by Drenriza on 2012-08-03
> **spjackson said:**
> If you really think that's what a while loop does, you'd better read the relevant sections of your Java tutorial again. It's

Instead of being a smart *** in your sentence. **if you really think that's what a while loop does**, followed up by a **you'd better read the relevant sections of your Java tutorial again**.

Your not very constructed in your reply, ***_THIS_*** reply is a bit useless.

You give scars if any information, while you let a question stand. If you know ***_EXACTLY_*** what a while loop does and what it can and what it CANT, your welcome to share your knowledge.

But to be perfectly honest, such a reply pisses me of a bit.

Also you assume that i have used a Java tutorial. That is not the case, something i found to a problem on the web where i have the exact described problem. And OMG the while loop sorted that out at that point. Maybe it wasn't the correct solution, i don't really care. Because it was the info and solution i had at that point of time.

---

### Post by trent.josephsen on 2012-08-03
You snipped the important part of spjackson's post. The while loop isn't doing you any favors. Loops affect normal control flow, not exception handling. Present a counter-example and we'll be happy to concede the point.

Or you could just take the while loop out and see that it has the exact same behavior.

---

### Post by spjackson on 2012-08-03
> **Drenriza said:**
> 
<Rant snipped.>

Also you assume that i have used a Java tutorial. That is not the case, something i found to a problem on the web where i have the exact described problem. And OMG the while loop sorted that out at that point. Maybe it wasn't the correct solution, i don't really care. Because it was the info and solution i had at that point of time.
I am very sorry to have provoked such a reaction. I thought you were trying to learn Java; I am sorry for that misunderstanding on my part.

Nevertheless, you had stated, and have now repeated that adding a while loop prevented an exception from terminating your program. I contend that this  cannot be the case. Your declaration suggests to me that you have fundamentally misunderstood either while loops, or exceptions or both. You are free to continue in that understanding if you want to.

However, for the sake of those who may refer to this thread in future, [here is an explanation of while]("http://docs.oracle.com/javase/tutorial/java/nutsandbolts/while.html") that is better than I could express, and [here is an explanation of try/catch]("http://docs.oracle.com/javase/tutorial/essential/exceptions/try.html") which is also better than I could express.

My belief that while has nothing to do with exception handling is based on documentation, such as that cited above. However, it can also be demonstrated experimentally, thus.

```

$ cat Test1.java
// Test1.java

import java.net.InetAddress;
import java.net.UnknownHostException;

public class Test1 {

    public static void main(String[] args) throws UnknownHostException {
        boolean end = false;
        while (!end) {
           InetAddress ip = InetAddress.getByName("no-such-address");
           end = true;
        }
        System.out.println("Program ran to completion.");
    }
}
$ javac Test1.java
$ java Test1
Exception in thread "main" java.net.UnknownHostException: no-such-address
        at java.net.Inet6AddressImpl.lookupAllHostAddr(Native Method)
        at java.net.InetAddress$1.lookupAllHostAddr(InetAddress.java:850)
        at java.net.InetAddress.getAddressFromNameService(InetAddress.java:1201)
        at java.net.InetAddress.getAllByName0(InetAddress.java:1154)
        at java.net.InetAddress.getAllByName(InetAddress.java:1084)
        at java.net.InetAddress.getAllByName(InetAddress.java:1020)
        at java.net.InetAddress.getByName(InetAddress.java:970)
        at Test1.main(Test1.java:11)
$ cat Test2.java
// Test2.java

import java.net.InetAddress;
import java.net.UnknownHostException;

public class Test2 {

    public static void main(String[] args) {
        try {
            InetAddress ip = InetAddress.getByName("no-such-address");
        }
        catch (UnknownHostException ex) {
            System.out.println("Magic! Exception successfully handled without any while loop in sight.");
        }
        System.out.println("Program ran to completion.");
    }
}
$ javac Test2.java
$ java Test2
Magic! Exception successfully handled without any while loop in sight.
Program ran to completion.

```

Again, I apologise for the upset caused. It was not my intent.

If you can provide a short complete example that supports your position, by all means do. If you are happy with your present understanding, that's fine by me, but I believe you are mistaken, as I have tried to demonstrate.

---

### Post by dagoth_pie on 2012-08-03
Hey Drenriza,

I'll clarify my statement about "end". I'm on of those people who likes to name variable exactly what they are. So I would name a bool being used like this, something like "bIs<What the while loop is doing>Completed". 

But then I'm one of those crazy guys...

PS. I'd also suggest putting it into a for loop rather than a while loop. As it is, you'd have a possibility of locking this into an infinite loop, of course you're logging it, so you'd see why straight away.

---

### Post by Some Penguin on 2012-08-04
> **spjackson said:**
> I am very sorry to have provoked such a reaction. I thought you were trying to learn Java; I am sorry for that misunderstanding on my part.

Nevertheless, you had stated, and have now repeated that adding a while loop prevented an exception from terminating your program. I contend that this  cannot be the case. Your declaration suggests to me that you have fundamentally misunderstood either while loops, or exceptions or both. You are free to continue in that understanding if you want to.


He's actually in the approximate vicinity of correctness, since the intent of his while() is most likely to **retry** after logging the exceptions.  However, he implemented it incorrectly, since the 'end' flag is set regardless of whether exceptions occurred or not (unless, of course, said exceptions are unchecked).  From a quick glance,

1) the while() loop should probably be replaced with a for() loop allowing a limited number of retries (perhaps with a delay),
2) the 'end' flag should be renamed something like 'success' and set only upon success -- *not* after the fall-through catch blocks,
3) the error logging possibly should be replaced with calls to log4j or similar

Also, code that simply logs exceptions and retries might make one's eyes twitch a bit.  In particular, InterruptedExceptions are a common way of signaling that a server do something in particular like abort a request for taking too long, reread a configuration or initiate an orderly shutdown... so one commonly expects *something* to be done with it -- even if it's only resetting the thread-is-interrupted flag, aborting the current request, and returning to the caller.

---

