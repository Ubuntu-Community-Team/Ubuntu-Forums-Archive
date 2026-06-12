---
title: "Java &quot;unchecked conversion &quot; warning -- help"
date: 2008-09-02
forum: Programming Talk
---

### Post by DBQ on 2008-09-02
In java when I compile my program, the following line gives a warning (when compiled with -Xlint):

Vector<String>[] dbTable = new Vector [20];

warning: [unchecked] unchecked conversion

How do I eliminate it?  I do not want to simply suppress it like some sites suggest. Thank you all.

---

### Post by FFfanatic on 2008-09-02
I believe you need to say (if I recall correctly from class): 
```
Vector<String>[] dbTable = new Vector<String>[20];
```
This is to make sure that the vector knows what it's supposed to hold.

---

### Post by tinny on 2008-09-02
> **DBQ said:**
> In java when I compile my program, the following line gives a warning (when compiled with -Xlint):

Vector<String>[] dbTable = new Vector [20];

warning: [unchecked] unchecked conversion

How do I eliminate it?  I do not want to simply suppress it like some sites suggest. Thank you all.

This is the best I can come up with for you

[PHP]Vector<Vector<String>> dbTable = new Vector<Vector<String>>();[/PHP]


A Vector of Vector<String> 

If I where you id just suppress  the warning.

BTW: Why aren't you using ArrayList's?

---

### Post by FFfanatic on 2008-09-02
He might be making a distributed application (that's where I remember this from), Vectors are one of the few DSs that can be picked apart, sent over the web and then reconfigured properly (usually for RMI (Remote Method Invocation)/RPC (Remote Procedure Call)).

---

### Post by tinny on 2008-09-02
> **FFfanatic said:**
> I believe you need to say (if I recall correctly from class): 
```
Vector<String>[] dbTable = new Vector<String>[20];
```
This is to make sure that the vector knows what it's supposed to hold.

Does this code compile? (Doesn't for me)

---

### Post by FFfanatic on 2008-09-02
I was going from memory a couple of months old. I'll quickly whip something together to see if it compiles and how I did it.

Finally found it:
```
Vector<String> v = new Vector<String>();
		v.add("blm");
```
or something similar for other data structures
```
Vector<Integer> v = new Vector<Integer>();
		v.add(32);
```

---

### Post by tinny on 2008-09-03
Does the OP want an array of Vector<String>?

Or just a standard generic collection?

Standard generic collection of String's
```

Vector<String> v = new Vector<String>();
		v.add("blm");

```

Standard generic collection of Integer's
```

Vector<Integer> v = new Vector<Integer>();
		v.add(32);

```

---

### Post by DBQ on 2008-09-03
Thank you all for the responses.  I need an array of Vector<String>.

---

### Post by Reiger on 2008-09-03
Vector<String>[] foo = new VectorString<String>[num_items];

Each item of Vector<String> must be initialised to new Vector<String>() ... and only then can you begin filling your table. Incidentally... Why not use ArrayLists which are essentially 'arrays without bounds', just like 'vectors' are?

---

### Post by jespdj on 2008-09-03
> **FFfanatic said:**
> He might be making a distributed application (that's where I remember this from), Vectors are one of the few DSs that can be picked apart, sent over the web and then reconfigured properly (usually for RMI (Remote Method Invocation)/RPC (Remote Procedure Call)).
That's not a good reason to use Vector. Vector is an old, legacy collection class from Java 1.0 that you really should not use anymore.

ArrayList is also Serializable and will work just fine with RMI.

---

### Post by Zugzwang on 2008-09-03
> **Reiger said:**
> Vector<String>[] foo = new VectorString<String>[num_items];


Try it out. As tinny already pointed out, this doesn't work that way due to Java's backward-compatible type system. For details see [here]("http://forums.sun.com/thread.jspa?threadID=530823&tstart=75") here.

Here's an example how to create an array of vectors of strings anyway. However, it will yield a warning. Dunno how to fix that.
[PHP]
import java.util.*;
import java.lang.reflect.*;

class test {
    public static void main(String[] args) {
        Vector<String>[] bar = (Vector<String>[])Array.newInstance(Vector.class,20);
        bar[14] = new Vector<String>();
        bar[14].add("Hello");
    }
}
[/PHP]

EDIT: Ok, this is technically what the OP had anyway. But the link is of course still of relevance.

---

### Post by mrmorris on 2008-09-03
You should not use Vector or arrays any longer. Do this instead:

List<String> dbTable = new ArrayList<String>(20);

When you DO run into the kind of issue you described (which is hopefully rare) you can suppress it with this line written on top of it:

@SuppressWarnings("unchecked")

/Casper

---

### Post by Zugzwang on 2008-09-03
> **mrmorris said:**
> You should not use Vector or arrays any longer. Do this instead:


Arrays? Why shouldn't one use arrays anymore?

---

### Post by hod139 on 2008-09-03
> **Zugzwang said:**
> Arrays? Why shouldn't one use arrays anymore?

More importantly, why would mrmorris suggest not to use Vectors anymore?  Vectors are thread safe, ArrayLists are not.  If you need to be thread safe, use Vector, if not, use ArrayList.  Saying you shouldn't use Vectors at all is wrong; just know when to use them.

---

### Post by jespdj on 2008-09-03
> **hod139 said:**
> More importantly, why would mrmorris suggest not to use Vectors anymore?  Vectors are thread safe, ArrayLists are not.  If you need to be thread safe, use Vector, if not, use ArrayList.  Saying you shouldn't use Vectors at all is wrong; just know when to use them.
Because Vector is an old legacy collection class, which has been superseded by ArrayList since Java 1.2.

You almost never really need the synchronization that Vector provides, and the synchronization overhead only makes your program run slower. In the rare case that you really need a synchronized list, use this instead of Vector:
```
List<String> list = Collections.synchronizedList(new ArrayList<String>());
```

---

### Post by hod139 on 2008-09-03
> **jespdj said:**
> Because Vector is an old legacy collection class, which has been superseded by ArrayList since Java 1.2.

What gave you that idea?  From: [http://java.sun.com/javase/6/docs/api/java/util/Vector.html](http://java.sun.com/javase/6/docs/api/java/util/Vector.html)
> 
As of the Java 2 platform v1.2, this class was retrofitted to  implement the [List]("http://java.sun.com/javase/6/docs/api/java/util/List.html") interface, making it a member of the  [ Java  Collections Framework]("http://java.sun.com/javase/6/docs/technotes/guides/collections/index.html").  Unlike the new collection  implementations, Vector is synchronized


> 
You almost never really need the synchronization that Vector provides, and the synchronization overhead only makes your program run slower. 

This is offering the same advice I gave.  Only use vector when you need to be thread-safe.

> 
In the rare case that you really need a synchronized list, use this instead of Vector:
```
List<String> list = Collections.synchronizedList(new ArrayList<String>());
```
This is not the same level of protection as a vector.  

For a long read on arguing about arrayList versus vector see:
  [http://groups.google.com/group/javaposse/browse_thread/thread/6d1e99e642d5a907/350d230dc19b2e88?#350d230dc19b2e88](http://groups.google.com/group/javaposse/browse_thread/thread/6d1e99e642d5a907/350d230dc19b2e88?#350d230dc19b2e88)

No need to continue it here.

---

### Post by tinny on 2008-09-03
> **mrmorris said:**
> You should not use Vector or arrays any longer. Do this instead:

List<String> dbTable = new ArrayList<String>(20);



Please don't kill off arrays yet :-) They are fast and a bound length.

> 
Thank you all for the responses. I need an array of Vector<String>. 


mrmorris your code defines an Arraylist of Strings, this is not what the OP wants. They want an array of the type "Vector<String>". Also using 20 as a constructor parameter doesn't do much (it just sets the initial capacity of the collection to 20, the Arraylist can still grow past this).

---

