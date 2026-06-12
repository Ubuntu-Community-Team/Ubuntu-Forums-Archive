---
title: "Java Constructor Problem"
date: 2010-04-13
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-04-13
Say I have two classes in Java which look like this (ignore the meaning of the classes):


[PHP]public class Number {
	public Number() {
		doSomething();
	}

     void doSomething() { ... }
}

public class Integer extends Number {
	private int integer;
	
	public Two(int integer) {
		this.integer = integer;
		super();
	}

    void doSomething() { ...do something with integer... }
}[/PHP]

with the Integer class, I want to assign a specific integer passed into the constructor.  The above code will not compile because the this.integer = integer; assignment cannot come before super();  The problem arises if doSomething() of the Integer class does something with the integer field which needs to be set before calling super().  How do I get around this issue?

---

### Post by ja660k on 2010-04-13
> **SNYP40A1 said:**
> Say I have two classes in Java which look like this (ignore the meaning of the classes):


```
public class Number {
	public Number() {
		doSomething();
	}

     void doSomething() { ... }
}

public class Integer extends Number {
	private int integer;
	
	[B]public Two(int integer) {
		this.integer = integer;
		super();
	}[/B]

    void doSomething() { ...do something with integer... }
}
```


the constructor "Two" needs to be the same name as your class. 
and if your calling a super class constructor, the first line in your constructor needs to be super();
[PHP]
public Integer(int integer){
    super();
    this.integer = integer;
}[/PHP]

---

### Post by Reiger on 2010-04-13
The problem, really, is that as a consequence of the inheritance tree the call stack looks like this:

[list="1"]
[*]Integer(); -- constructor
[*]Number(); -- through super();
[*]Integer.doSomething(); -- overriden method doSomething();
[/list]

And the question is how to set the integer field of Integer before doSomething() is called.

You can solve this two ways. Both amount to restructuring the code. The first way is to introduce a generic type field in Number like this:
```

public class Number<N extends java.lang.Number> {
  private N number;
  public Number(N number) {
    if(number == null) {
      /* 
       * this is an error. 
       * throw an exception or use a default error state.
       */
    }
    this.number=number;
    doSomething();
  }
  
  public void doSomething() {
    // do something with number
  }
}
public class Integer extends Number<java.lang.Integer> {
  public Integer(java.lang.Integer integer) {
    super(integer);
  }
  
  @Override
  public void doSomething() {
    // do something with number
  }
}

```

Alternatively make it part of the contract of your class that there is an additional initialisation method which must be invoked before the object can be used. And do not invoke this method yourself from a constructor. For example:

```

public class Number {
  public void doSomething() {
    // do something
  }
  
  /**
   * Call this method to initialize the object.
   * You should probably add a bit of state like a boolean to
   * mark whether or not this method has been called.
   */
  public void init() {
    doSomething();
  }

}
public class Integer {
  private int integer;
  public Integer(int integer) {
    this.integer=integer;
  }

  @Override
  public void doSomething() {
    // do something with integer
  }
}

// construct and initialise like this:
Number n= new Number();
n.init();
Integer i=new Integer(22);
i.init();

```

---

### Post by SNYP40A1 on 2010-04-13
> the constructor "Two" needs to be the same name as your class. 


True, my typo.

I guess I'll have to opt for option number two.  The parent constructor is intended to be JPanel where the constructor initiates itself.  Each panel will take an entirely different set of options and having to create an option field for each possible parameter whether the panel uses it or not is a bit messy.  The init idea looks like the better plan.

---

### Post by Reiger on 2010-04-13
Depending on how you intend to use the class; it may be beneficial through the trouble of writing separate getters/setters for each property; and a void constructor.

```

import javax.swing.*;
public class MyPanel extends JPanel {
  /**
   * Void constructor, ensures this class is a so-called Java-bean.
   * This helps tools such as GUI builders, as they are typically
   * capable of recognizing this &#8220;pattern&#8221;.
   */
  public MyPanel() {}

  private int integer;
  
  /** setter method for integer property */
  public void setInteger(int integer) {
    this.integer=integer;
  }
  
  /** alternatively add a getter method for integer property */
  public int getInteger() {
    return this.integer;
  }
}

```

For instance the NetBeans GUI builder (Matisse) can automatically work with this class (once it has been compiled) as a distinct type of &#8220;component&#8221;; including code generation of the setInteger() call.

---

