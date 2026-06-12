---
title: "Another Java question... Enclosed classes."
date: 2008-06-25
forum: Programming Talk
---

### Post by Phristen on 2008-06-25
Ok, I have something like this:

public class A {
...

class B {
...
}

...
}


Question is, how do I get a reference to A from inside of B?
Of course, I could include a method in A which would just return **this**, and call it whenever I need, but... Doesn't that feels kind of .... unprofessional?

---

### Post by mdawg414 on 2008-06-25
I would think the best way to do it would be to pass the reference to A in the constructor of B and then hold that as a field in B. Basically, every instance of B "belongs" to an A but I do not know of a way to determine that from B itself. Try something like this:

public class A {
...

class B {

A parent

public B(A parent) {
this.parent = parent;
}
...
}

...
}

---

### Post by JudgeFudge on 2008-06-25
Do you really need the reference to the enclosing class? You probably know that you can invoke the methods of the encloser directly from the enclosed instance:


public class OuterC {
	String someString = "yo";
	
	class InnerC {
		public void whatever() {
			System.out.println(someString);
		}
	}
	
	public static void main(String args[]) {
		OuterC outerC = new OuterC();
		InnerC innerC = outerC.new InnerC();
		innerC.whatever();
	}

}


otherwise your solution sounds perfectly reasonable.

---

### Post by mdawg414 on 2008-06-25
That is true but what if you want to pass a reference to the outer class to another method. If that was the case *this* would only pass to B. But you are correct fudge, everything that is inside of the outer class can be accessed by the inner class

---

### Post by Phristen on 2008-06-25
Well, it's complicated :)

I need to add listeners to some other class, and the listeners need to have access to all of A's variables.

Normally I would just make class A listen to its own events, but in this case A is very generic and the events will be processed in various ways.

So, I created an inner class, which implements the appropriate listener interface, and then I create anonymous classes from that, at which point you can no longer reference A's methods and properties.

P.S.
Like this:[PHP]
public class A {
	class B implements SomeListener {
		...
	}
}



public class C {
	public A a1;	// this is an example, in reality there will be an unknown # of A's
	public Component c1, c2, ... ;	// ... and unknown # of Components
	...
	c1.addSomeListener (a1.new B () {
			...
			// here A's methods can no longer be accessed
			...
		});
	// Every one of c1, c2, ... will need a listener and all of the listeners will need
	// access to the properties of some instance of A (e.g. a1).
}
[/PHP]

P.P.S. Also, while we're on this topic, another question comes to mind.
How can I call A's method from B, if B already has its own method with the same signature?

---

### Post by jamesstansell on 2008-06-25
As you are smelling a stink, it may be that you're getting into an anti-pattern.  I'm just not sure which pattern to suggest that you try instead.

---

### Post by jamesstansell on 2008-06-25
> **Phristen said:**
> 
P.P.S. Also, while we're on this topic, another question comes to mind.
How can I call A's method from B, if B already has its own method with the same signature?

How about using super?  From the [http://java.sys-con.com/read/48839.htm](http://java.sys-con.com/read/48839.htm) article:

> Q20. How can a subclass call a method or a constructor defined in a superclass?

A. Use the following syntax: super.myMethod(); To call a constructor of the superclass, just write super(); in the first line of the subclass's constructor.

---

### Post by Phristen on 2008-06-25
> Q20. How can a subclass call a method or a constructor defined in a superclass?We are not talking about subclasses, but ENCLOSED classes.

Enclosing class is NOT a superclass of an enclosed class, thus you can't use super.

---

### Post by jamesstansell on 2008-06-26
Oops - I got confused.  Back to the drawing board.

---

### Post by dtmilano on 2008-06-26
Is this what you want ?

> package mytests;

public class A {
	private int i;
	private B b;
	
	A(int i) {
		this.i = i;
		this.b = new B();
	}
	
	class B {
		private C c;
		
		B() {
			A a = A.this;
			this.c = new C(A.this);
			System.out.println("my A.i is " + a.getI());
		}
	}
	
	int getI() {
		return i;
	}
	
	public static void main(String[] args) {
		A a1 = new A(1);
		A a2 = new A(2);
	}
}


> package mytests;

public class C {
	A a;
	
	C(A a) {
		this.a = a;
	}
}


---

### Post by achelis on 2008-06-26
In short:

All enclosed classes have a reference to the enclosing class. Unless they are static I believe.

You get a reference to the enclosing class (as dtmilano correctly shows) by:

```

EnclosingClassName.this

```

I see you try to access it from an anonymous class as well so will provide a simple example:

```

public class EnclosingClassName
{
	private int i = 5;

	public void accesingFromAnonymousClass()
	{
		new JButton().addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e)
			{
				EnclosingClassName.this.i++;
			}
		});
	}
	
	public class EnclosedClass
	{

		public EnclosedClass()
		{
			super();
			EnclosingClassName.this.i = 2;
		}
	}

	public static class StaticEnclosedClass
	{
		public StaticEnclosedClass()
		{
			super();
			// This won't work - enclosed class is static and have no reference.
			// EnclosingClassName.this.i = 2;
		}
	}

}

```

---

### Post by Phristen on 2008-06-26
> this.c = new C(A.this);
> EnclosingClassName.this
Thanks!

---

