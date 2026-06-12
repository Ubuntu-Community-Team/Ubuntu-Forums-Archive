---
title: "java datatype question"
date: 2009-03-13
forum: Programming Talk
---

### Post by badperson on 2009-03-13
Hi,

let's say you have a method to do something mathematical, like return the factorial of a number.


If you want to able to use either int or long, is it best to just have two versions of the method? Or should the long method work it's way down into the range of an int value and then call the int version? 
bp

---

### Post by simeon87 on 2009-03-13
Not tested:

```

public long getFactorial(int i) {
  // code
  return result;
}

public int getFactorial(int i) {
  long result = getFactorial(i);
  if ( result > Integer.MAX_VALUE ) {
    // throw exception or so
  }
  return (int) result;
}

```

---

### Post by shadylookin on 2009-03-13
int factorial(int number){
 //stuff
}

and 

long factorial(long number){
 //stuff
} 

then you can call 

factorial(your_number);

and it will give you an appropriate result based on whether your_number is an int or a long.

---

### Post by mcla0203 on 2009-03-13
Both of these should work, but I think the second example is more "java-style".  At least I've seen this method more in my java experience.  Especially with constructors.

---

### Post by HotCupOfJava on 2009-03-13
Well, unless you were expecting results that are too large for an int, you could just use a method that returns an int. An int would be automatically promoted if you had to use it in an expression with a long. I guess it also depends on whether you are passing the int or long to the method, or returning the int or long!

---

### Post by txcrackers on 2009-03-14
That kind if assumption is **never** a good idea.

This is what the OP is asking about:

[http://www.google.com/search?q=method+overloading+in+java&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=method+overloading+in+java&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by badperson on 2009-03-14
In the examples above, and the way I have my code written now, there are two essentially identical versions of the method, one which takes an int argument, one which takes a long. 

The scenario I was thinking of, say you wanted to get the factorial of a huge number, beyond the range of an int. (the return value would probably have to be something like BigInteger)

Say you have a factorial method that starts as a long...

n * (n-1) * (n-2), etc...

when n gets within int range, my question is, would it be better to then call the int version of the method, or just continue to call long, even though n is within the range of an int.
bp

---

### Post by HotCupOfJava on 2009-03-14
> **txcrackers said:**
> That kind if assumption is **never** a good idea.

This is what the OP is asking about:

[http://www.google.com/search?q=method+overloading+in+java&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=method+overloading+in+java&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Yes, I know about overloading a method. I was unclear on whether the OP was referring to the method parameters, or the return type. It seems the OP is referring to the parameters. You could just use a method that takes a long. If you happened to pass it an int, it would automatically be promoted. In fact, if you're using a long anywhere in a mathematical expression and you stick an int in there, it will be promoted to a long. So even if your method goes like this:

```

public long doStuff(int anInt){
    long aLong = //whatever;
    return aLong * anInt; // anInt automatically becomes a long
}

```

However, I do believe that if you started with numbers large enough to require a long (or even some large ints) it is possible you would find yourself without an appropriate return type, if 

> n * (n-1) * (n-2), etc...

is any indication!

---

