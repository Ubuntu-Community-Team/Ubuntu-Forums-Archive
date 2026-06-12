---
title: "Used to do this in Java, how to do it in C++?"
date: 2009-02-24
forum: Programming Talk
---

### Post by cl333r on 2009-02-24
Hi folks,
I need to call non static methods of a class from other classes without passing that class as a parameter to all the other classes. Below is a short example how I used to do this in Java, I'd appreciate an example how I can do that in C++:

```

package test;

public class Main {
	private static Main itself;

    public static void main(String[] args) {
		new Main();
    }

	public Main() {
		itself = this;
		new Test1();
		new Test2();
		new Test3();
	}

	public static Main itself() {
		return itself;
	}

	void method1() {
		System.out.println( "called method 1 " );
	}

	void method2() {
		System.out.println( "method 2" );
	}
}

class Test1 {
	public Test1() {
		Main.itself().method1();
	}
}

class Test2 {
	public Test2() {
		Main.itself().method1();
		Main.itself().method2();
	}
}

class Test3 {
	public Test3() {
		Main.itself().method2();
	}
}

```

---

### Post by Sockerdrickan on 2009-02-24
Lol that's a lot of classes...
namespaces?

---

### Post by cl333r on 2009-02-24
The classes at the end (Test1, Test2, Test3) are there to just show how other classes can access random non static methods (method1 & method2) of the main class without having to pass a reference of the main class to them.

---

### Post by CptPicard on 2009-02-24
It looks like you're just using the singleton pattern, although in a dangerous-looking way.

[http://www.google.fi/search?q=c%2B%2B+singleton+pattern](http://www.google.fi/search?q=c%2B%2B+singleton+pattern)

---

### Post by cl333r on 2009-02-24
Yes, that seems to be what I've been looking for, I'll have a look, thanks.

---

### Post by dwhitney67 on 2009-02-24
For a singleton object, there should only be one instantiation of said object; hence the constructor should be defined as private, not public.  This applies to C++ and Java.

In C++:
```

class Singleton
{
  public:
    static Singleton& instance()
    {
      static Singleton theInstance;
      return theInstance;
    }

    // non-static methods...
    void doSomething();

    // destructor
    ~Singleton() {}

  private:
    // constructor
    Singleton() {}

    // non-static data members...
};

```

Example usage:
```

Singleton::instance().doSomething();

```

---

