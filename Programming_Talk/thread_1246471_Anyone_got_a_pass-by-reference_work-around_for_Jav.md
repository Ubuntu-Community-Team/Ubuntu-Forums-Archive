---
title: "Anyone got a pass-by-reference work-around for Java?"
date: 2009-08-21
forum: Programming Talk
---

### Post by SNYP40A1 on 2009-08-21
I know everything in Java is pass by value.  The problem (probably a frequent problem) is that I have a function where I need to return 3 integers.  In C++, I would just pass the integers by reference as parameters.  In Java, I the function returns an object that holds the 3 integers.  The object is a waste because it's only used as a holder and has no functionality other than getters and setters.  Anyone found a better solution to my issue?

---

### Post by eeperson on 2009-08-21
Actually, (with the exception of primitive types) Java does pass by reference

---

### Post by Habbit on 2009-08-21
No, it passes "handles" to objects by value, which is semantically very similar with a true pass-by-reference, but not fully. For example: ```

// C++
void swap(MyClass& a, MyClass& b) {
    MyClass temp = a;
    a = b;
    b = temp;
}
MyClass x, y;
swap(x, y);


// Java
void swap(MyClass a, MyClass b) {
    MyClass temp = a;
    a = b;
    b = temp;
}
MyClass x = new MyClass(), y = new MyClass();
swap(x, y);

```The C++ code (using true by-reference semantics) successfully exchanges x and y, while the Java code only exchanges the local copies of the handles pointing to x and y, thus leaving the objects themselves unaffected.

---

### Post by eeperson on 2009-08-21
That is an important distinction to make, thanks Habbit.  I was not aware that you could do that with C++ style references, or that Java was did not do true 'call-by-reference'. Good to know.

I guess what I meant is that variables in Java store references(by which I mean [this]("http://en.wikipedia.org/wiki/Reference_(computer_science)") not [this]("http://en.wikipedia.org/wiki/Reference_(C%2B%2B)")) to Objects.  So you can do something like this:
```

public void swap(MyObject object) {
    int a = object.getA();
    int b = object.getB();
    object.setA(b);
    object.setB(a);
}

```

So, to the OP, unless you can do something like the above then there really is no good workaround.

---

### Post by DougB1958 on 2009-08-21
> **SNYP40A1 said:**
> I know everything in Java is pass by value.  The problem (probably a frequent problem) is that I have a function where I need to return 3 integers.  In C++, I would just pass the integers by reference as parameters.  In Java, I the function returns an object that holds the 3 integers.  The object is a waste because it's only used as a holder and has no functionality other than getters and setters.  Anyone found a better solution to my issue?

I suppose my first pass at a solution would be to redesign the overall program so that this function doesn't have 3 results that aren't conceptually members of something larger. But if that's not going to happen (and I suppose there are reasons why it might not), you could cut down your programming overhead by making the integers public members of your result class, and not writing getter and setter methods for them.

For example, instead of

[PHP]class Carrier {
    private int x;
    private int y;
    private int z;
    public void setX( int newX ) { x = newX; }
    public int getX() { return x; }
    ... etc ...
}

// Your function in question...
Carrier myFunction( ... ) {
    Carrier result = new Carrier();
    result.setX( ... calculations for first integer ... );
    ... etc ...
    return result;
}[/PHP]

you could try

[PHP]class Carrier {
    public int x;
    public int y;
    public int z;
}

// Your function in question...
Carrier myFunction( ... ) {
    Carrier result = new Carrier();
    result.x = ... calculations for first integer ...
    ... etc ...
    return result;
}[/PHP]

(Forgive me if the Java syntax isn't perfect, it's been a while since I wrote Java.)

Making the integers public lets you write less code, but breaks conventional style rules about not allowing public data members. But then the problem as a whole breaks conventional style rules about a function only having one result....

---

### Post by shadylookin on 2009-08-22
> **SNYP40A1 said:**
> I know everything in Java is pass by value.  The problem (probably a frequent problem) is that I have a function where I need to return 3 integers.  In C++, I would just pass the integers by reference as parameters.  In Java, I the function returns an object that holds the 3 integers.  The object is a waste because it's only used as a holder and has no functionality other than getters and setters.  Anyone found a better solution to my issue?

in java all primitives have an object type as well. Try using the class Integer instead of the primative int for the variable if you want a pass by reference(yes I know it's not technically pass by reference).

---

### Post by spupy on 2009-08-22
If the 3 integers you want to return belong logically together, put them in the simplest class (even with public fields and no getters/setters). If they don't belong together, why do you return them in the same function? In that case your design is bad.

Using Integers and giving the to-return values as arguments is a bad design. Think in java, not in C/C++.

Other idea is to use an array, Vector or ArrayList (I don't really know what is the difference between the last two).

---

### Post by eeperson on 2009-08-22
> **shadylookin said:**
> in java all primitives have an object type as well. Try using the class Integer instead of the primative int for the variable if you want a pass by reference(yes I know it's not technically pass by reference).

The problem with using the Integer class is that it is immutable.  So, you can't change its value after it has been created.

---

### Post by Reiger on 2009-08-22
If you can be sure that all objects/types are of the same type T, then you can use an array. For instance, this inverts an array of the generic type T[]:

```

public T[] invert(T[] old) {
  int i = old.length;
  T[] result = new T[i];
  for(T obj: old) {
    i--;
    result[i] = obj;
  }
  return result;
}

```

Similar constructs can be used for Iterable<T> 's, because the for (each) loop really only requires that &#8220;old&#8221; be Iterable (and arrays are a special case of that in Java), and the Iterable interface includes index-based access to the underlying data structure IIRC.

Anyways in Java the simple thing to do for basic cases in which you essentially modify a fixed-dimension vector is to represent that as an array of something.

---

### Post by Habbit on 2009-08-22
> **Reiger said:**
> ```

  T[] result = new T[i];

```
This line is illegal, Java does not allow you to create an array from a generic parameter because array types are reified (i.e. present at runtime), while generics type parameters are not. Read a bit on erasure as a method of implementing generics with backwards compatibility.

---

