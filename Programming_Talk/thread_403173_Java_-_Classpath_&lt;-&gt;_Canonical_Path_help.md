---
title: "Java - Classpath &lt;-&gt; Canonical Path help?"
date: 2007-04-06
forum: Programming Talk
---

### Post by gorded on 2007-04-06
In Java is there a way to find out out the classpath for a specific canonical path
or  to find the canonical path of a classpath.

Thanks

---

### Post by smokey edgy on 2007-04-06
Hi gorded,

Is it possible to elaborate in context what exactly you are trying to do?

Thanks.

---

### Post by gorded on 2007-04-06
Ok well im making a factory class 

atm its constructor  take an object which represents the super class of the classes you want loaded. The next parameter is an array of objects which is the parameters to instantiate the classes, now the third parameter i want to be the canonical path of the folder you want to load the classes from. 

What i do is look in the folder a get all the .class files and check that they extend from the object passed. But in order to load to class i need the classpath of the class.

So what i would like to do is be able to take this path
/home/user/programming/classs/rc/guns/      -folder containing classes
in to
rc.guns 

i think that more clear

Thanks

---

### Post by smokey edgy on 2007-04-06
Yes. Thanks for the clarification, gorded.

Now, you manage to get all the class files from the folder. Have you been able to read in the class files into a byte array buffer? I would assume that once you have that byte array, you can use [,%20int,%20int)"]http://java.sun.com/j2se/1.4.2/docs/api/java/lang/ClassLoader.html#defineClass(java.lang.String,%20byte[],%20int,%20int)]("http://java.sun.com/j2se/1.4.2/docs/api/java/lang/ClassLoader.html#defineClass(java.lang.String,%20byte[),
The first argument can be null (as you don't know what its called at this point). You can then ask the resulting Class object what its super class and perform whatever other validation you have.

---

### Post by sdrubolo on 2007-04-07
I think this may be helpful, [http://java.sun.com/javase/6/docs/api/](http://java.sun.com/javase/6/docs/api/). go to the System class, and you can find a lot of very useful stuff. for example the getProperty (String key) method (if you use the "user.dir" key you get the working directory), or you can go to the File class where there is a lot of methods you can use but you must already have the file to get the path name.
Hope this can help.

---

