---
title: "Java: Storing multiple objects"
date: 2009-01-27
forum: Programming Talk
---

### Post by Sugz on 2009-01-27
Hi
I have this problem. Where i need to store multiple objects in a file

This is what i have in mind. 

The Root Object name is the name of the file (Without the extension) And the objects thats the root objct stored are stored in the file itself.. (like a .csv file) 
However im not sure how to differentiate between the objects that are stored withing the file

Like..
X Contains many object Y's 

X object (name) is the file name like Xcontainer.csv
inside the csv file are Text representations of Objects Y

Im am wondering when extracting these Y objects, how to get each individual one?

Many thanks

-Sugz

---

### Post by heamaster on 2009-01-27
Maybe you can store one object on each line, with "," between the data?

---

### Post by leg on 2009-01-27
Can't you [serialize]("http://java.sun.com/docs/books/tutorial/jndi/objects/serial.html") your objects or have I missed the point.

---

### Post by Sugz on 2009-01-27
Ah yes i see.. 

Is it possible to nest it.. by which i mean


X Contains Many Y's Y contains many Z's

And implement serialisation and it'll store the nested Objects (Stored as a ArrayList)

---

### Post by CptPicard on 2009-01-27
Serialization works on the entire object graph.

---

### Post by kavon89 on 2009-01-27
Sounds like arrays to me.

---

### Post by CptPicard on 2009-01-27
It's the same thing from the objects in memory perspective...

---

### Post by Sugz on 2009-01-28
Well i tried to do the method using objectStreams
Using 4 classes that all implement serializable

And when i try to parse the Root Object into the in.readObject() i get this error

```
Exception in thread "main" java.io.InvalidClassException: dealership.Mercedes; local class incompatible: stream classdesc serialVersionUID = -964082445959237674, local class serialVersionUID = 5770130195886792702
        at java.io.ObjectStreamClass.initNonProxy(ObjectStreamClass.java:562)
        at java.io.ObjectInputStream.readNonProxyDesc(ObjectInputStream.java:1583)
        at java.io.ObjectInputStream.readClassDesc(ObjectInputStream.java:1496)
        at java.io.ObjectInputStream.readOrdinaryObject(ObjectInputStream.java:1732)
        at java.io.ObjectInputStream.readObject0(ObjectInputStream.java:1329)
        at java.io.ObjectInputStream.readObject(ObjectInputStream.java:351)
        at recipes.TesterClass.main(TesterClass.java:36)
TestingJava Result: 1
```

---

### Post by achelis on 2009-01-28
If you changed any of the classes between writing them and retrieving them you get the following error:

```

java.io.InvalidClassException: main.PersistMe; local class incompatible: stream classdesc serialVersionUID = -5054028162725692737, local class serialV
ersionUID = -881140295273004575
	at java.io.ObjectStreamClass.initNonProxy(ObjectStreamClass.java:562)
	at java.io.ObjectInputStream.readNonProxyDesc(ObjectInputStream.java:1583)
	at java.io.ObjectInputStream.readClassDesc(ObjectInputStream.java:1496)
	at java.io.ObjectInputStream.readOrdinaryObject(ObjectInputStream.java:1732)
	at java.io.ObjectInputStream.readObject0(ObjectInputStream.java:1329)
	at java.io.ObjectInputStream.readObject(ObjectInputStream.java:351)
...

```

In other words it looks like that's what's wrong..

I haven't read up on this but a simple test seems to show that you can make it work with changes by providing a serialVersionUID to your serialized classes.

```

private static final long serialVersionUID = -881140295273004575L;	

```

From the [API]("http://java.sun.com/j2se/1.5.0/docs/api/java/io/Serializable.html")

> 
If a serializable class does not explicitly declare a serialVersionUID, then the serialization runtime will calculate a default serialVersionUID value for that class based on various aspects of the class, as described in the Java(TM) Object Serialization Specification. However, it is strongly recommended that all serializable classes explicitly declare serialVersionUID values, since the default serialVersionUID computation is highly sensitive to class details that may vary depending on compiler implementations, and can thus result in unexpected InvalidClassExceptions during deserialization. Therefore, to guarantee a consistent serialVersionUID value across different java compiler implementations, a serializable class must declare an explicit serialVersionUID value. It is also strongly advised that explicit serialVersionUID declarations use the private modifier where possible, since such declarations apply only to the immediately declaring class--serialVersionUID fields are not useful as inherited members. 


---

### Post by Sugz on 2009-01-28
Yup its working prefectly now. Thank you all for your help :)

---

