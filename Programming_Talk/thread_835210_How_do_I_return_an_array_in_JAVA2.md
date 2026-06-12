---
title: "How do I return an array in JAVA2??"
date: 2008-06-20
forum: Programming Talk
---

### Post by theodorekon on 2008-06-20
Hi,
I was wondering how can I return a whole array from a class in Java. I mean when I want to return an integer named k I write the command:
```
return k;
```
But this does not apply for arrays, I can't give the command:
```
return k[];
```
Is there a way to do that??

---

### Post by screech on 2008-06-20
return k;

---

### Post by xlinuks on 2008-06-20
screech means that if your array is called k then just write "return k", if it's "myArray" then "return myArray". Pretty straightforward I think, here's an example:
```

private float[] getMatrix() {
	float[] myMatrix = new float[ 2000000 ];
	//do stuff
	return myMatrix;
}

```

---

### Post by theodorekon on 2008-06-20
Sorry for the stupid question, I thought it would be a bit more complicated than that. I was told something about pointers and stuff but the ```
return k;
``` command seems to work just fine.
Thanks

---

### Post by themusicwave on 2008-06-20
> **theodorekon said:**
> Sorry for the stupid question, I thought it would be a bit more complicated than that. I was told something about pointers and stuff but the ```
return k;
``` command seems to work just fine.
Thanks

You can rest assured that there are no pointers in Java.  Under the hood Java is written in C, so it uses pointers, but when you write Java code you do not need pointers.  Actually, Java can't even declare a pointer.  You couldn't use them even if you wanted.

---

### Post by NormR2 on 2008-06-20
There must be pointers in Java.
How would you get a NullPointerException if there weren't?

---

### Post by descendency on 2008-06-20
> **NormR2 said:**
> There must be pointers in Java.
How would you get a NullPointerException if there weren't?

There are pointers in Java. You as a programmer can NOT program with them.

NullPointerException means whatever you are dealing with has not been initialized and is therefore pointing to nothing.

Often it results when you try to use a block of an array before a value is assigned to it, but I think (I don't really program much in java - eww ...) it also happens when you try to return a blank array. 

Arrays are nothing more than a series of pointers pointing to RAM locations where information is stored.

This shouldn't generate the error (I initialize it).
```
public int[] getArray()
{
  int[] testArray = {0,0,0,0,0};
  return testArray;
}

```

---

