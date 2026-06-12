---
title: "Checking Object size in Java"
date: 2009-08-18
forum: Programming Talk
---

### Post by Finalfantasykid on 2009-08-18
Is there any method to check the amount of memory a specific Object takes up?

---

### Post by tinny on 2009-08-18
Why are you wanting to do this?

You should have a look into profiling. The NetBeans IDE has a good one built in. (That's what I use)

[http://www.netbeans.org/features/java/profiler.html](http://www.netbeans.org/features/java/profiler.html)

I don't know of a Java API that gives you this data, but there is some interesting stuff in the Runtime class

[http://java.sun.com/j2se/1.5.0/docs/api/java/lang/Runtime.html](http://java.sun.com/j2se/1.5.0/docs/api/java/lang/Runtime.html)

---

### Post by Finalfantasykid on 2009-08-19
I am working on something which uses a decent amount of memory, and would like to see how much memory some of the larger objects are using(media files).

I have used profiling in the past, but it is not exactly what I want to use.  A method would be prefered so that I can just do a println();

And RunTime was the first class that I checked for this, but as far as I could tell there was nothing of use in there, just methods to check how much memory was left in the heap and stuff like that.

---

### Post by kpkeerthi on 2009-08-19
Here is a crude way:
1. Create a ByteArrayOutpStream
2. Create an ObjectOutputStream that is backed up by the ByteArrayOutputStream
3. Write your object (this object must be serializable) to the ObjectOutputStream
4. Invoke the size() method on the ByteArrayOutputStream to find the size of the object. You could also invoke toByteArray().length instead.

```

import java.io.ByteArrayOutputStream;
import java.io.IOException;
import java.io.ObjectOutputStream;
import java.io.Serializable;


public class ObjectUtil {

	public static int getSize(Serializable object) throws IOException {
		ByteArrayOutputStream byteStream = new ByteArrayOutputStream();
		ObjectOutputStream objectStream = new ObjectOutputStream(byteStream);
		
		objectStream.writeObject(object);
		objectStream.flush();
		objectStream.close();
		
		return byteStream.size();
	}
}

```

---

### Post by jespdj on 2009-08-19
kpkeerthi's method does not work. The size of the data when you serialize an object is not the same as the size of a live object in memory.

---

### Post by tinny on 2009-08-19
> **jespdj said:**
> kpkeerthi's method does not work. The size of the data when you serialize an object is not the same as the size of a live object in memory.

+1 This is right. 

People use profilers for the very type of problem that is being described here.

When I look at my profiler I can see object allocation counts, bytes allocated for each type, percentage of heap used by each type etc...

---

### Post by kpkeerthi on 2009-08-21
> **jespdj said:**
> kpkeerthi's method does not work. The size of the data when you serialize an object is not the same as the size of a live object in memory.

> **tinny said:**
> +1 This is right. 

It will work. But I guess I already mentioned in the post that its a 'crude' solution.

---

### Post by Zugzwang on 2009-08-21
> **kpkeerthi said:**
> It will work. But I guess I already mentioned in the post that its a 'crude' solution.

...which means that it is a very rough approximation of the object size (plus all non-system referenced objects).

---

### Post by jespdj on 2009-08-21
> **kpkeerthi said:**
> It will work. But I guess I already mentioned in the post that its a 'crude' solution.
Your solution will give you some number, but that number has very little to do with how much memory an object will take up when it is in memory.

So if you want to know how much memory an object uses, as Finalfantasykid asks, then your solution is not useful.

Especially if you have added custom writeObject() and readObject() methods to your class, the data that is written to or read from a stream when the object is serialized or deserialized can be totally different from what an object looks like when it is in memory.

Here's an example:
```
	public static void main(String[] args) throws IOException {
		Integer value = 23;

		ObjectOutputStream out = new ObjectOutputStream(new FileOutputStream("output.ser"));
		out.writeObject(value);
		out.flush();
		out.close();
	}

```
On my computer, this writes a file of 81 bytes, which is WAY more than what I'd expect an Integer object takes up in memory.

---

### Post by tinny on 2009-08-21
> **jespdj said:**
> Your solution will give you some number, but that number has very little to do with how much memory an object will take up when it is in memory.

So if you want to know how much memory an object uses, as Finalfantasykid asks, then your solution is not useful.

Especially if you have added custom writeObject() and readObject() methods to your class, the data that is written to or read from a stream when the object is serialized or deserialized can be totally different from what an object looks like when it is in memory.

Here's an example:
```
	public static void main(String[] args) throws IOException {
		Integer value = 23;

		ObjectOutputStream out = new ObjectOutputStream(new FileOutputStream("output.ser"));
		out.writeObject(value);
		out.flush();
		out.close();
	}

```
On my computer, this writes a file of 81 bytes, which is WAY more than what I'd expect an Integer object takes up in memory.

Yeah, one of the problems is that you get type info bla, bla etc..

---

