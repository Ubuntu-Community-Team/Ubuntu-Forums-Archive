---
title: "Returning multiple values from Another Class in Java"
date: 2007-03-18
forum: Programming Talk
---

### Post by krypto_wizard on 2007-03-18
I need to retrieve two values from a function on another class, first is a long a value and seconds is a String.

How can I do that ? 

Every help is appreciated.

---

### Post by pmasiar on 2007-03-18
Function in Java can return either a scalar value or reference (also a scalar) to a collection (like a list). 

OTOH Python can return multiple values and unpack them on assigment :-)

---

### Post by Tomosaur on 2007-03-18
I don't think it's possible, but you shouldn't really need to do this anyway. A few ways around it would be:

1) Spit up the method so that you have one returning a long, one returning a string.
2) Create a new class, and return that, so you can use: myClass.getLong() and myClass.getString() to get at the data.
3) Use a Hashtable (probably not worth it for single values.
4) Return an array of Object. Everything in Java is a subclass of java.Object. However, you need to make sure you don't use the native types, but use the Object types, for this to work. For example, don't use:
```

int x = 5;

```

but use:
```

Integer x = new Integer(5);

```
Instead. It's much less economical, but allows you to use the Object array as described above.

I personally would recommend you use 2. You can create a static, nested class, like this:
```

class myClass{
  static class Returner{
    int a;
    int b;
  }

  public myClass(){    
  }

  public static Returner getVals(int x, int y){
    Returner myReturner = new Returner();
    myReturner.a = x + y;
    myReturner.b = x * y;
    return myReturner;
  }
}

```

Notice how the Returner class is nested and static. This allows you to instantiate it from a different class, like this:

```

class tester{
  public static void main(String[] args){
    myClass.Returner ret = myClass.getVals(20, 30);
    System.out.println("Value 1 =" +  ret.a + ", Value 2 = " + ret.b + ".");
  }
}
```

That should work. In short, the answer is that there is no native way to return multiple values. You need to create some kind of structure to store multiple values, and return that, or just split up your code so that you're only returning one value at a time. Java tries to encourage the latter approach - it is designed to force you to make very modular code - where methods do the least number of things possible. In essence, each method should only be doing one thing, returning one value / Object etc. The embedded, static class idea is slightly similar to creating a struct in C/C++.

---

### Post by laxmanb on 2007-03-19
Make a class that contains both the string and the int, return an object of the class... extract the values.... mark the object for GC.

---

