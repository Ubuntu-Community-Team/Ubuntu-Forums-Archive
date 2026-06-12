---
title: "[SOLVED] [Vala] Interfaces not working?"
date: 2008-09-28
forum: Programming Talk
---

### Post by pikkio on 2008-09-28
Hi! I'm new to **[Vala]("http://www.vala-project.org")** programming, and actually I'm reading the tutorial right now.

I'll go right to the point: I can't get **Interfaces** working. Bear in mind that I'm quite comfortable with the Java programming, so it's not a matter of understanding the OOP principles behind interfaces.

Despite that, I can't get compiled even this example code from the tutorial!

```
using GLib;

public interface ITest {
	public abstract int data_1 { get; set; }
	public abstract void function_1();
}

public class Test1 : ITest {
	public int data_1 { get; set; }
	public void function_1() {
	}
}

public class Test : Object {

	public static void main(string[] args) {
		Test1 t = new Test1();
		t.function_1();

		ITest i = t;
		i.function_1();
	}
}
```

These are the two errors I got:

```
pikkio:vala % valac -o interfaces interfaces.vala
interfaces2.vala:22.13-22.13: error: missing class prerequisite for interface `ITest'
		ITest i = t;
		          ^
interfaces2.vala:22.3-22.7: error: missing class prerequisite for interface `ITest'
		ITest i = t;
		^^^^^
Compilation failed: 2 error(s), 0 warning(s)

```

Thanks in advance for any suggestion.

P.S. On my Hardy installation I've got the 0.3.5 version of Vala libs

---

### Post by Quikee on 2008-09-28
Looks like you have hit [this]("http://bugzilla.gnome.org/show_bug.cgi?id=547362"). Mind that Vala is still not in a stable state.

---

### Post by pikkio on 2008-09-28
@Quikee: Thanks, I'll post a comment on that bug. Anyway, I'm perfectly aware of Vala's beta state, and it's still doing a damn awesome job at version 0.3.5 :-)

Besides of that, I can't figure out why an official example code doesn't even compile :confused:

---

### Post by Quikee on 2008-09-29
> **pikkio said:**
> 
Besides of that, I can't figure out why an official example code doesn't even compile :confused:

Which example? This is possible because examples aren't checked regularly.

---

### Post by pikkio on 2008-09-29
The example I posted before is adapted from the Vala tutorial: [http://live.gnome.org/Vala/Tutorial#head-550883e2f1aeebc10f4d160561df2907ff79255c](http://live.gnome.org/Vala/Tutorial#head-550883e2f1aeebc10f4d160561df2907ff79255c)
I've basically done a copy-n-paste, adding the Test class with the main() entry point.

That tutorial is a draft, of course, but in this case it's just showing the basic interfaces syntax...

---

### Post by pikkio on 2008-09-29
Ok, I got it.
A dev on the gnome Bugzilla said it's necessary to put a class (e.g. GLib.Object) as the prerequisite for every interface definition. So the previous example turns to:

```
using GLib;

public interface ITest : Object {
	public abstract int data_1 { get; set; }
	public abstract void function_1();
}

public class Test1 : Object, ITest {
	public int data_1 { get; set; }
	public void function_1() {
	}
}

public class Test : Object {

	public static void main(string[] args) {
		Test1 t = new Test1();
		t.function_1();

		ITest i = t;
		i.function_1();
	}
}
```

I'll mark this topic as Resolved, and I'll file a bug against Vala tutorial, as this behaviour is not documented at all.

Thanks for your attention, anyway :)

---

### Post by bruce89 on 2008-09-29
By the way, the "using GLib;" statement is depreciated. GLib is always included now.

---

### Post by pikkio on 2008-09-29
> **bruce89 said:**
> By the way, the "using GLib;" statement is depreciated. GLib is always included now.

Really? It has to be a recent thing, since I've heard about this nowhere...:confused:
So, how it is the way now? I simply omit the "using GLib;" and leave everything else the same, or what?

thanks.

---

### Post by pikkio on 2008-09-29
> **bruce89 said:**
> GLib is always included now.

Mh. I suppose the answer to my question is "Yes" :D

---

### Post by bruce89 on 2008-09-29
> **pikkio said:**
> Really? It has to be a recent thing, since I've heard about this nowhere...:confused:

It was in 0.3.4.

> **pikkio said:**
> Mh. I suppose the answer to my question is "Yes" :D

Yes, it is yes.

---

