---
title: "Theory questions about Java"
date: 2010-03-23
forum: Programming Talk
---

### Post by s3a on 2010-03-23
I've been reading my text book and I'm studying for an upcoming test and I have some questions. As you might notice my questions are pretty basic but that's because we're only beginning to cover this topic and therefore we won't have anything serious on inheritance on the test but it will be there mildly. Anyways, on to my questions (sorry if they're badly worded):

-------------------------------

1) If a class is not abstract but it has an abstract method, is it true that it still CAN NOT be instantiated? Or do abstract methods only exist inside abstract classes?

2) The purpose of an abstract METHOD is to make sure the subclass overrides the method but what's the purpose of an abstract CLASS? Is the purpose of an abstract CLASS to be able to store the abstract METHODS? (that is IF I am right in saying that abstract methods HAVE TO BE in abstract classes)

3) Imagine I had an array called, and set up as, array[rows][columns]. Doing array.length would give me the length of the rows but is array[].length the way to get the length of the columns?

-------------------------------

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by wmcbrine on 2010-03-23
Could you maybe edit down (or remove entirely) those dashed lines, so your message will fit in my browser window? I doubt I'll be the only one with a problem.

---

### Post by NovaAesa on 2010-03-23
Try compiling:
```

public class Foo
{
    public abstract void bar();
}

```
You will get a compile error.
```

Foo.java:1: Foo is not abstract and does not override abstract method bar() in Foo
public class Foo
       ^
1 error

```

You are correct about your second point.

With number three, array.length would give you the number of rows (i.e. the length of the columns). The number of columns can be calculated by array[0].length (Maybe there's a better way to do this though, I'm not sure).

---

### Post by s3a on 2010-03-24
> **wmcbrine said:**
> Could you maybe edit down (or remove entirely) those dashed lines, so your message will fit in my browser window? I doubt I'll be the only one with a problem.

I edited them down.

---

### Post by s3a on 2010-03-24
Does it have to be array[0] or could it be array[1] for example? And what about the other questions?

> **NovaAesa said:**
> Try compiling:
```

public class Foo
{
    public abstract void bar();
}

```
You will get a compile error.
```

Foo.java:1: Foo is not abstract and does not override abstract method bar() in Foo
public class Foo
       ^
1 error

```

You are correct about your second point.

With number three, array.length would give you the number of rows (i.e. the length of the columns). The number of columns can be calculated by array[0].length (Maybe there's a better way to do this though, I'm not sure).

---

### Post by goseph on 2010-03-24
3) Imagine I had an array called, and set up as, array[rows][columns]. Doing array.length would give me the length of the rows but is array[].length the way to get the length of the columns?

Why not try it out?

---

### Post by lykeion on 2010-03-24
Just an additional tip (because I agree with goseph: try and learn).
If you need a gui editor for java to quickly try out code and don't need to spend additional time to learn an advanced ide, I've heard many java students use BlueJ (just google it and try it out).

---

### Post by DougB1958 on 2010-03-24
> **goseph said:**
> 3) Imagine I had an array called, and set up as, array[rows][columns]. Doing array.length would give me the length of the rows but is array[].length the way to get the length of the columns?

Why not try it out?

"Try and learn" is a definitely a good habit to get into with programming. But this might be a case where a lot of people wouldn't try one of the relevant experiments. I don't actually know what array[].length will do for a 2D array, but I'm pretty sure you'll get some interesting results from the following:

```
int array[][] = { { 1, 2, 3 },
                  { 4, 5 } };
System.out.println( array[0].length );
System.out.println( array[1].length );
```

---

### Post by falconindy on 2010-03-24
array[].length won't compile because it's not referencing a valid object. OP could answer all 3 questions by writing code roughly as long as the initial post.

---

### Post by LKjell on 2010-03-24
It feels like this is an IQ test.

1) If you have an abstract class it means you cannot instantiate the class, but you can have a subclass of it, and pointer. If a method is abstract it means that you need to implement the method in every regular subclass of it.
A normal class with an abstract method does not make sense.

2) If an abstract class has only public abstract method you can just call it an interface. However, abstract class is like a normal class with some exception as you cannot instantiate the class and you can have abstract methods in it. The purpose of abstract class is to create subclasses that derives from the abstract class and to have a unified pointer that can access critical methods you make. You might want to read more about interface before taking the test.

3) If an array is set up as array[row][column] then array.length would give you the number of rows and the variable column will give you the length of columns.

---

