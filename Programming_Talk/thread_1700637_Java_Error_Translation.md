---
title: "Java: Error Translation?"
date: 2011-03-05
forum: Programming Talk
---

### Post by fallenshadow on 2011-03-05
Hi again guys and gals,

I have an error with the following code:

```
className myclass = new className("",0);
                className.getName();
```

I am getting this error message:

> non-static method getName() cannot be referenced from a static context

Can somebody please explain or translate that error into more plain english? (something I can understand)

Any help will be appreciated, as it will help me identify whats wrong with my program.

---

### Post by PaulM1985 on 2011-03-05
In Java there are static methods and non-static methods.  A non-static method is a method which can be executed on an instance of a class (an object).  This means that a non-static method can have access to the member variables of the object it is being executed on.  A static method is executed using the class name and cannot access any of the member variables, since you have executed it on a class name, it does not know which object's member variables it is supposed to use.

In your example, you have called:

```

ClassName.getName(); // <- This is a static method call, because it is being executed on the name of the class rather than on an instance of the class (an object).

```

I am assuming that in the definition of ClassName, you have added a method for getName, but you have not prefixed it with the "static" keyword.  If you have used any member variables in you definition of the getName method, you will not be able to use static (see the description of static / non-static above).  So if you wanted it to be static, it would look something like this:

```

public static String getName()
{
    // implementation
}

```

If this method is supposed to be static, you can just add the "static" keyword, otherwise, you need to execute it on the instance you defined using:

```

myclass.getName();

```

Does this help?

Paul

---

### Post by pbrane on 2011-03-05
Edit: PaulM1985 beat me to it.

You should call the 'getName()' method like this:
```

className myclass = new className("", 0);
**myclass**.getName();

```

Although I'm sure you wanted to actually get the name of something from the className class, so you probably wanted to do something like this.
```

className myclass = new className("", 0);
String name = myclass.getName();

```
assuming the return value is a String.

You could declare the getName method as static and then call it like so:
```

String name = className.getName();

```
without actually instantiating the class itself.

---

### Post by fallenshadow on 2011-03-05
Thanks for the help! :)

I was still stuck on this until I changed the variable to static too! 

> private static String name;

Is this correct? Or should I not be changing variables to static?

That should be the last of my questions. :)

---

### Post by Reiger on 2011-03-05
Well that depends: do you intend getName() to return the same name every time it is called? Or did you intend an object to “have a name”?

In the first case you get something like this:
```

public class MyClass {
  /* 
   * this name is independent of the actual MyClass “instance”
   * if it does not change consider using a public static final 
   * property instead, so you don't need use a static getName()
   * method
   */
  private static String name="name"; 
  public static String getName() { return MyClass.name; }
}

```
In the second case you get something like this:

```

public class MyClass {
  /*
   * This name depends on the particular MyClass instance.
   * E.g. MyClass("bob").getName() returns "bob", 
   * and MyClass("alice").getName() returns "alice".
   */
  private String name;
  public MyClass(String name) { this.name= name; }
  public String getName() { return this.name; }
}

```

---

### Post by fallenshadow on 2011-03-06
I guess I wanted the object to contain a name because every time Myclass.getname() is executed it will ask the user to input a name.

Also I am struggling to get this line to be accepted/compiled:

```
return (Object)getObject(indexIn);
```

Here is what its part of:

```

public int getObject(int indexIn)
    {
        return (Object)getObject(indexIn);
    }

```

This is part of getting an objectlist to work. Its showing this error:

> Incompatible types - found Object but expected int

Obviously it expects something of type int but what I have is an object that contains Strings like name for example. I don't know what to change to make this work. Anyone know a solution?

---

