---
title: "[SOLVED] D: calling a superclass' method"
date: 2007-10-02
forum: Programming Talk
---

### Post by WebDrake on 2007-10-02
I'm trying to teach myself D and have got stuck on the following problem: how do I call a superclass method from the subclass?  (Can I?)

Consider the following code:
```

import std.stdio;

class A {
	this() {
		i = 5;
	}

	void foo() {
		writefln("i = ", i);
	}

	private {
		int i;
	}
}

class B : A {
	this() {
		i = 7;
	}

	void foo() {
		writef("But seriously, ");
		**// and here I want to call A's foo. :-)**
	}
}

void main() {
	A a = new A();
	B b = new B();
	A.foo();
	B.foo();
}

```

How can I achieve what I want?  (i.e. that B's foo() can call A's?)

---

### Post by ynnhoj on 2007-10-02
does d have a keyword such as "parent" or "super"?  maybe you should look it up, or just do some trial and error.  you could try "super.foo();" or something like that and see what happens..

---

### Post by WebDrake on 2007-10-02
> **ynnhoj said:**
> does d have a keyword such as "parent" or "super"?  maybe you should look it up, or just do some trial and error.  you could try "super.foo();" or something like that and see what happens..

Thanks!  In fact I'd tried super.foo(), which is the correct answer, but didn't realise it because of a dumb, stupid error in the code.  If you look at the last lines, they should read,

```

	A a = new A();
	B b = new B();
	a.foo();
	b.foo();

```

Not realising that had me chasing around a wild goose chase for ages.  Anyway, the correct code is,

```

import std.stdio;

class A {
	this() {
		i = 5;
	}

	void foo() {
		writefln("i = ", i);
	}

	private {
		int i;
	}
}

class B : A {
	this() {
		i = 7;
	}

	void foo() {
		writef("But seriously, ");
		super.foo();
	}
}

void main() {
	A a = new A;
	B b = new B;
	a.foo();
	b.foo();
}

```

---

### Post by dwhitney67 on 2007-10-02
In C++ one would use a statement like A::foo().  Maybe it's the same is D.

Ah, just saw your solution.  It appears that D is more Java-like than C++, or maybe it's a combo of the two?

---

### Post by WebDrake on 2007-10-03
> **dwhitney67 said:**
> In C++ one would use a statement like A::foo().  Maybe it's the same is D.

Ah, just saw your solution.  It appears that D is more Java-like than C++, or maybe it's a combo of the two?

Yes, D is more Java-like---it seems to have taken many of the best features from Java and C# (including garbage collection) but works as a fully-compiled language.  It'll be interesting to see whether it gets taken up widely---I have a feeling it might be exciting for games developers.

---

