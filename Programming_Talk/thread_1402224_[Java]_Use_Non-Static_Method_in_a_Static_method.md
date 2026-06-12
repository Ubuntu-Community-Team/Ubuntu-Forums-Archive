---
title: "[Java] Use Non-Static Method in a Static method"
date: 2010-02-08
forum: Programming Talk
---

### Post by patrickaupperle on 2010-02-08
Why aren't you allowed to call non-static methods from static methods? 

Ex (From Head First Java 2nd Edition)

```

public class duck {
  private int size;

  public static void main (String[] args) {
    System.out.println("Size is " + getSize()); //this line 
  }

  public void setSize(int s) {
    size = s;
  }

  public int getSize() {
    return size;
  }
}

```
I know it is not allowed, but why?

---

### Post by dwhitney67 on 2010-02-08
Non-static methods require that an object be instantiated before the method can be called.  After all, the method is in essence an 'attribute' of the object.  With no object, you have no method!


P.S.  If you want to have some "fun", and at the same time gain some knowledge, implement a singleton class.

---

### Post by patrickaupperle on 2010-02-08
> **dwhitney67 said:**
> Non-static methods require that an object be instantiated before the method can be called.  After all, the method is in essence an 'attribute' of the object.  With no object, you have no method!


P.S.  If you want to have some "fun", and at the same time gain some knowledge, implement a singleton class.

Wow, I think I know what you are saying, correct me if I am wrong.
The instance variables are only created at the creation of the object, therefore, they can not be accessed except for after the object is created. Is this it?

Also, what is a singleton class?

---

### Post by dwhitney67 on 2010-02-08
> **patrickaupperle said:**
> Wow, I think I know what you are saying, correct me if I am wrong.
The instance variables are only created at the creation of the object, therefore, they can not be accessed except for after the object is created. Is this it?

Yes, you are correct.

> **patrickaupperle said:**
> 
Also, what is a singleton class?
I was hoping you would take the initiative to research this... but because I am bored...

```

class Singleton
{
   private static Singleton theInstance = new Singleton();

   // ensure that only one instance of this class can be performed
   // p.s.  if this class has a main(), then it could instantiate more than
   //       one Singleton.
   //
   private Singleton() {}

   public static Singleton instance()
   {
      return theInstance;
   }

   public void someMethod()
   {
      System.out.println("Hello Java!");
   }
}

public class Foo
{
   public static void main(String[] args)
   {
      Singleton.instance().someMethod();

      // not permitted
      //Singleton s = new Singleton();
   }
}

```

A singleton allows for only one instance of the object to be created.  It is a common design pattern.

---

### Post by abhishek.malhotra35 on 2010-02-08
Another example would be:
class Singleton {
	
	private static Singleton singleton;
	
	private Singleton() {}
	
	public Singleton getInstance()
	{
		if (singleton == null)
			singleton = new Singleton();
		return singleton;
	}

}

public class foo {
     
      public static void main(String args[])
      {
           Singleton singleton1 = new Singleton();
           singleton1.getInstance();
           Singleton singleton2 = new Singleton();
           singleton2.getInstance();
      }
}

In this, singleton1 will initialize the Singleton class. When the second singleton object is made, it will check whether the variable has been initialized or not. If the variable has been initialized, then it is returned without creating another instance. 

Singleton pattern is very helpful in case of pooling.

---

### Post by Some Penguin on 2010-02-09
> **patrickaupperle said:**
> Wow, I think I know what you are saying, correct me if I am wrong.
The instance variables are only created at the creation of the object, therefore, they can not be accessed except for after the object is created. Is this it?


More directly, the instance variables are meaningful only in the context of a particular object.  A static method has no reference to any particular instance (other than those explicitly passed in, if any).  It is therefore not possible for it to access an instance variable even if objects have already been created -- because which one would it use?

It's like asking "What color is this car" when I haven't made it remotely clear which particular car I'm asking you about.

---

### Post by patrickaupperle on 2010-02-09
@dwhitney67

That is really interesting. I guess I should have researched it, but I was already posting back for something else anyway. I am sure this has a point, but I don't see it (new to Java, obviously).

@abhishek.malhotra35

How does that work?
in public class foo you put
```
Singleton singleton1 = new Singleton();
```
but the constructor for Singleton is private. 

A quick trip to the compiler and 
```
[patrick@arch Desktop]$ javac foo.java 
foo.java:20: Singleton() has private access in Singleton
Singleton singleton1 = new Singleton();
                       ^
foo.java:22: Singleton() has private access in Singleton
Singleton singleton2 = new Singleton();
                       ^
2 errors

```

Maybe you made a mistake somewhere or I copy and pasted to gedit wrong.

---

### Post by MadCow108 on 2010-02-09
he did that on purpose.
It shows you that you can't create a second singleton. If you try you get a compiler error. Thats the nice thing about Singletons.

The only way to access the Singleton is by using the Instance method, this assures only a single Instance can be created.

edit: read the wrong code :)
abhishek.malhotra35 code is wrong, the getInstance method needs to be static as in dwhitney's example
and the calls to new must be commented for it to compile (intended)
the getInstance method creates an instance but only once!
a second call will return the existing singleton instance.
constructor calls will fails as wished by the singleton pattern.

abisheks variant has the advantage that the singleton is never constructed if it is not needed. This is useful if your singleton is some expensive object which is only needed in case of an unlikely error.

---

### Post by CptPicard on 2010-02-09
The getInstance() doesn't necessarily have to be static, as long as the variable is. I've never seen singleton implemented like that, though. However, there is a potential race-condition bug in the null-checking; it should be inside a synchronization block.

---

### Post by MadCow108 on 2010-02-09
> **CptPicard said:**
> The getInstance() doesn't necessarily have to be static, as long as the variable is. I've never seen singleton implemented like that, though. However, there is a potential race-condition bug in the null-checking; it should be inside a synchronization block.

and its a potential place for a double checking lock :) (beware dangerous in some languages!)

I get an error if its not static:
foo.java:21: non-static method getInstance() cannot be referenced from a static context
    Singleton singleton1 = Singleton.getInstance();

---

### Post by CptPicard on 2010-02-09
Oh yeah, I was reading it carelessly, you're right.

---

### Post by dwhitney67 on 2010-02-09
> **CptPicard said:**
> Oh yeah, I was reading it carelessly, you're right.

Ironic... we've come full circle with this thread.  One cannot access a non-static method without an instance of an object.  :-)

---

### Post by patrickaupperle on 2010-02-09
Ok, I think I understand everything that was said. To make sure, can someone post a corrected version of abhishek.malhotra35s code?

---

### Post by abhishek.malhotra35 on 2010-02-09
My mistake. I apologize for that. Have been out of java coding for quite some time now :). Sorry about my previous post. Will change it.

---

### Post by dwhitney67 on 2010-02-09
> **patrickaupperle said:**
> Ok, I think I understand everything that was said. To make sure, can someone post a corrected version of abhishek.malhotra35s code?
His code should have been very similar to mine; the only difference he was demonstrating was the initialization of the static 'singleton' within the getInstance() method versus directly as I had done when I declared 'theInstance'.

He did everything correct, except for what is inside the main() function.  The main() should appears as:
```

public static void main(String[] args)
{
   Singleton s = Singleton.getInstance();

   // not permitted
   //Singleton oops = new Singleton();
}

```

---

### Post by nvteighen on 2010-02-09
My singleton :)

```

class Singleton(object):
    __SINGLETON__ = None

    def __init__(self):
        if Singleton.__SINGLETON__ == None:
            self.a = 'a'
            self.b = {}
            # Whatever...
            Singleton.__SINGLETON__ = 1
        else:
            # Ok, this is a bit crude... a custom exception would be better
            raise TypeError

def main():
    a = Singleton()
    b = Singleton() # <- Error

if __name__ == "__main__":
    main()

```

---

### Post by CptPicard on 2010-02-09
@nvteighen, in addition to preventing multiple instantiation, a Singleton typically also provides a single global access point to the singly-existing object, so that you don't need to carry it around... a Singleton.getInstance().

---

### Post by nvteighen on 2010-02-09
> **CptPicard said:**
> @nvteighen, in addition to preventing multiple instantiation, a Singleton typically also provides a single global access point to the singly-existing object, so that you don't need to carry it around... a Singleton.getInstance().

oh... I think it would be trivial to do.

EDIT: Here it is :)

```

class Singleton(object):
    __LOCK__ = None
    __SINGLETON__ = None

    def __init__(self):
        if Singleton.__LOCK__ == None:
            self.a = 'a'
            self.b = {}
            # Whatever...

            Singleton.__SINGLETON__ = self
            Singleton.__LOCK__ = 1
        else:
            # Ok, this is a bit crude... a custom exception would be better
            raise TypeError

    @staticmethod
    def get_instance():
        return Singleton.__SINGLETON__

def main():
    a = Singleton()
    print a == Singleton.get_instance() # prints 'True'
    b = Singleton() # <- Error

if __name__ == "__main__":
    main()

```

---

