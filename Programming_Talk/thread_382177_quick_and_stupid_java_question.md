---
title: "quick and stupid java question"
date: 2007-03-11
forum: Programming Talk
---

### Post by Tuna-Fish on 2007-03-11
Is there any way to make a reference (pointer?) that points to a specific index in a int[] array?
It is trivial if the contents of that array are objects, but if they are primitives it seems impossible, is it really so?

---

### Post by phossal on 2007-03-11
Like this?

```
package com;

public class Pointer {

	
	public int[] x;
	
	
	public Pointer() {
		x = new int[3];
		x[1] = 2;
	}
	
	public static void main(String[] args) {
		Pointer p = new Pointer();
		
		int p1 = p.x[1];
		System.out.println(p1);
		
		p.x[1] = 45;
		System.out.println(p1);
	}
	
}
```

Your goal is to end up with a var like p1 which reflects any changes in x[1] ?

---

### Post by Tuna-Fish on 2007-03-11
That doesn't work, i tried.
the program prints```
2
2
```
int p1 = p.x[1]; //Assigns the value of p.x[1] to p1, it doesn't make p1 a pointer to p.x[1]

---

### Post by Tuna-Fish on 2007-03-11
Yes, the point is to have a var p1 which directly points to p.x[1].
p1 cannot be an int, just because int only ever stores the value, not a location.

---

### Post by phossal on 2007-03-11
It would work something like this:

```
package com;

public class Pointer {

	
	public int[] x;
	
	
	public Pointer() {
		x = new int[3];
		x[1] = 2;
	}
	
	public static void main(String[] args) {
		Pointer p = new Pointer();
		System.out.println(p.x[1]);
		
		Pointer q = p; //<--- THE POINTER
		System.out.println(q.x[1]);
		
		
		p.x[1] = 45;
		
		System.out.println(q.x[1]);
		
	}
	
}
```

---

### Post by phossal on 2007-03-11
Removed

---

### Post by pmasiar on 2007-03-11
> **Tuna-Fish said:**
> Is there any way to make a reference (pointer?) that points to a specific index in a int[] array?
It is trivial if the contents of that array are objects, but if they are primitives it seems impossible, is it really so?

I am not a Java expert but IIUC values of primitive types are stored in stack frame, and are not available after exit (function's stack frame is out of scope). Java objects are stored in the heap, and they are "alive" (protected from garbage collector) as long as any reference to them is valid. This is difference between int (primitive) and Integer (object).

---

