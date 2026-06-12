---
title: "Java Sub/Superclasses"
date: 2009-11-16
forum: Programming Talk
---

### Post by dwally89 on 2009-11-16
Hi,

So, for university, I have been given a class InputFrame, that basically creates a input box on the screen, into which the user can enter data. The data can be retrieved using methods such as getInt().

I have to create a subclass called SpyFrame which is a subclass of InputFrame. This will have an overiding method getInt(), which will retrieve the data from the SpyFrame, and store it in an integer (just like an InputFrame would do), and then I need to also output this integer using System.out.prinln.

I am trying to do this, but am getting an error, here is my code:

```
package ex8;

public class SpyFrame extends InputFrame{

    public SpyFrame(){        
    }

    public int getInt(){
        int i = super.getInt();
        System.out.println(i);
        return i;
    }
}

```

I am getting a stack overflow error.

What is wrong with my code?

Thanks

---

### Post by dwhitney67 on 2009-11-16
What is InputFrame?  How do I know if it has been properly constructed?

Heck, I do not even know how you are calling SpyFrame's getInt(), much less how you constructed the SpyFrame object.

This thread is probably going to be closed soon, because moderator's tend to do such things when they realize that the thread involves 'homework'.

---

### Post by dwally89 on 2009-11-16
> **dwhitney67 said:**
> What is InputFrame?  How do I know if it has been properly constructed?

Heck, I do not even know how you are calling SpyFrame's getInt(), much less how you constructed the SpyFrame object.

This thread is probably going to be closed soon, because moderator's tend to do such things when they realize that the thread involves 'homework'.

It's not very complicated, it just involves overriding methods...

Help would be appreciated.

---

### Post by Zugzwang on 2009-11-16
It is probably worthwhile noting that when obtaining a stack overflow error, running the whole program in a debugger usually gives the developer a good idea why things are going wrong. I think that this hint isn't against the homework policy. ;-)

---

### Post by dwally89 on 2009-11-16
I tried debugging, and didn't get any help from that

---

### Post by Zugzwang on 2009-11-16
> **dwally89 said:**
> I tried debugging, and didn't get any help from that

How comes? If you get a stack overflow error, the call stack should be full of method calls which tell you precisely where the infinite calling loop (which is very likely to be there) occurs.

---

### Post by akoskm on 2009-11-16
The mighty "recursive" call is in front of you. :popcorn:

---

### Post by dwally89 on 2009-11-16
The problem is, is that getInt is being called infinitely.

The problem is in the line:
```
int i = super.getInt();
```

I want "i" to be the result of when getInt is called. However, both the superclass (InputFrame) and the subclass (SpyFrame) have a method called this.

I want "i" to be the result of when getInt (from the superclass InputFrame) is called.

How do I do this?

Thanks

---

### Post by akoskm on 2009-11-16
Example:

```
package ex8;

public class SpyFrame extends InputFrame{

    private int i;

    public SpyFrame(){
      i = super.getInt();        
    }

    public int getInt(){
        System.out.println(i);
        return i;
    }
}
```

But in this case before calling the method *getInt()* initialize an instance of ht SpyFrame class:
```

...
...a = new SpyFrame();
a.getInt();
...

```

---

### Post by dwally89 on 2009-11-16
I did that already, I get the error with that.

---

### Post by akoskm on 2009-11-16
> **dwally89 said:**
> I did that already, I get the error with that.

What is the error message?

---

### Post by dwally89 on 2009-11-16
> **dwally89 said:**
> Hi,

So, for university, I have been given a class InputFrame, that basically creates a input box on the screen, into which the user can enter data. The data can be retrieved using methods such as getInt().

I have to create a subclass called SpyFrame which is a subclass of InputFrame. This will have an overiding method getInt(), which will retrieve the data from the SpyFrame, and store it in an integer (just like an InputFrame would do), and then I need to also output this integer using System.out.prinln.

I am trying to do this, but am getting an error, here is my code:

```
package ex8;

public class SpyFrame extends InputFrame{

    public SpyFrame(){        
    }

    public int getInt(){
        int i = super.getInt();
        System.out.println(i);
        return i;
    }
}

```

I am getting a stack overflow error.

What is wrong with my code?

Thanks

.

---

### Post by akoskm on 2009-11-16
Stack overflow error?

If you modified the code like I suggested and created the instance first, then the problem is not in the SpyFrame class...

---

### Post by dwally89 on 2009-11-16
Don't think you fully understand the problem...

---

### Post by dwhitney67 on 2009-11-16
@ dwally

You should post your code if you want immediate help.  Instead, you appear to be dancing around a problem, and providing very little facts to support the error you are getting.

Here's the simplest code that emulates what you are trying to do, and surprisingly, it works.  Therefore, you must be doing something wacko in your code to get a stack overflow error.  But until I see your complete code, I will have to get back to my book, "Be a Psychic in 21 Days!".
```

class Base
{
   private int i = 5;

   public Base() {}

   public int getInt() {
      return i;
   }
}

public class Derived extends Base
{
   public Derived() {
      super();
   }

   public int getInt() {
      return super.getInt();
   }

   public static void main(String[] args) {
      Derived d = new Derived();
      System.out.println("d.getInt() = " + d.getInt());
   }
}

```

---

### Post by Zugzwang on 2009-11-16
> **dwally89 said:**
> .

Dear OP, please be a little bit more patient. Wait at least 12 hours before bumping a thread.

Second, let me just state that you did something here that is considered to be very inpolite: Apparently you already found the root of your problem with a debugger but still asked "what is the problem" in your first post. Always describe your problem and what you got so far as comprehensible and complete as possible (but leave our unnecessary stuff).

Finally, if you get such an infinite recursion, I would say that the problem lies in the class InputFrame and not in the class Spyframe, which leads to the answer to the original problem: Nothing is wrong with the code that you actually exposed here.

---

### Post by dwally89 on 2009-11-16
> **dwhitney67 said:**
> @ dwally

You should post your code if you want immediate help.  Instead, you appear to be dancing around a problem, and providing very little facts to support the error you are getting.

Here's the simplest code that emulates what you are trying to do, and surprisingly, it works.  Therefore, you must be doing something wacko in your code to get a stack overflow error.  But until I see your complete code, I will have to get back to my book, "Be a Psychic in 21 Days!".
```

class Base
{
   private int i = 5;

   public Base() {}

   public int getInt() {
      return i;
   }
}

public class Derived extends Base
{
   public Derived() {
      super();
   }

   public int getInt() {
      return super.getInt();
   }

   public static void main(String[] args) {
      Derived d = new Derived();
      System.out.println("d.getInt() = " + d.getInt());
   }
}

```

Hmm... your code here does indeed replicate what I am trying to do. Not sure why mine isn't working.

---

### Post by dwally89 on 2009-11-16
> **Zugzwang said:**
> Dear OP, please be a little bit more patient. Wait at least 12 hours before bumping a thread.
I was not bumping my thread, I was merely telling akoskm to refer to my previous thread, in regards to what the error message was.

> **Zugzwang said:**
> Second, let me just state that you did something here that is considered to be very inpolite: Apparently you already found the root of your problem with a debugger but still asked "what is the problem" in your first post. Always describe your problem and what you got so far as comprehensible and complete as possible (but leave our unnecessary stuff).
I did not intend to be impolite, I was merely asking what is the problem, as I wasn't sure how to solve it myself.

> **Zugzwang said:**
> Finally, if you get such an infinite recursion, I would say that the problem lies in the class InputFrame and not in the class Spyframe, which leads to the answer to the original problem: Nothing is wrong with the code that you actually exposed here.
I doubt there is a problem with the class InputFrame as it was written by [Steve Vickers]("http://en.wikipedia.org/wiki/Steve_Vickers_%28academia%29"), the same person who wrote the Sinclair ZX Spectrum ROM firmware.

Thanks

---

### Post by TennTux on 2009-11-16
As has been suggested a couple of times we don't know what is in the classes around SpyFrame. i.e. Who calls SpyFrame's getInt() and InputFrame. Knowing this would help. But if we can't see that then you could add some code to output useful info like the changes below. The first one or two times the "if ((callCount % 10) == 0)" is true should be very helpful.

```

package ex8;

public class SpyFrame extends InputFrame{
**    private static int callCount = 0 ;**

    public SpyFrame(){        
    }

    public int getInt(){
[B]	callCount++ ;
	if ((callCount % 10) == 0)
	{
		System.out.println("Called " + callCount + " times.") ;
		Exception	e	= new Exception("Looping") ;
		e.printStackTrace() ;
	}[/B]
        int i = super.getInt();
        System.out.println(i);
        return i;
    }
}

```

Hope this helps.

---

### Post by akoskm on 2009-11-16
> **dwally89 said:**
> I was not bumping my thread, I was merely telling akoskm to refer to my previous thread, in regards to what the error message was.

```

.....
    public SpyFrame(){
      i = super.getInt();        
    }

    public int getInt(){
        System.out.println(i);
        return i;
    }
------
...
...a = new SpyFrame();
a.getInt();
...

```

```

   public int getInt() {
      return super.getInt();
   }

   public static void main(String[] args) {
      Derived d = new Derived();
      System.out.println("d.getInt() = " + d.getInt());
   }

```

...anyway, the point in both solutions is the same. I thought that you'll understand it without explicit constructor calls and complete code. ):P

---

### Post by dwally89 on 2009-11-16
I can't seem to get it to work.
Attached is all of my files, including the java library in which InputFrame can be found.

Thanks

---

### Post by Can+~ on 2009-11-16
Executed your code, and saw nothing like a recursive call or Stack overflow.

---

### Post by dwally89 on 2009-11-16
What happened when you executed it?

---

### Post by Can+~ on 2009-11-16
> **dwally89 said:**
> What happened when you executed it?

A window popped up, asked for an integer, I wrote "5", then asked me for 5 floats (although I had to look the code to figure that out), and when I reached 5 the input became grey.

I executed it on pair with the debugger, and I didn't see anything weird (aside from spawning a lot of threads just for this).

---

### Post by dwally89 on 2009-11-16
Hmm... weird.

When I execute it I get:
```
Exception in thread "main" java.lang.StackOverflowError
        at ex8.SpyFrame.getInt(SpyFrame.java:23)
```

---

### Post by dwally89 on 2009-11-16
I messed around with it, and it works now :S (not that I'm complaining).

Does anyone know a good program that can visually show the difference between two text files, as I can't quite remember what changes I made?

Thanks

---

### Post by Can+~ on 2009-11-16
> **dwally89 said:**
> I messed around with it, and it works now :S (not that I'm complaining).

Does anyone know a good program that can visually show the difference between two text files, as I can't quite remember what changes I made?

Thanks

diff? If you want a graphical interface for diff, install Meld.

---

