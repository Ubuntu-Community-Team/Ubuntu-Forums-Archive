---
title: "issue with graphics not showing up in JPanel -- java app"
date: 2008-04-14
forum: Programming Talk
---

### Post by badperson on 2008-04-14
Hi,

I'm writing a simple java app that has a swing gui that grabs some data out of a mysql database. 

The swing gui has a graphic image painted on to it. The image is stored in a directory where the app can get to it with a relative path. 

I had this weird issue, where I made an executable jar, double clicking the jar file executes the app, but the image isn't visible. 

But when I launch it in a terminal window by typing
java -jar jarfile.jar,

it launches and does show the image. 
Anyone else ever run into an issue like this?
bp

---

### Post by Zugzwang on 2008-04-14
See [this thread]("http://ubuntuforums.org/showthread.php?t=669277") for the reason. Note that if an Image can't be loaded, you won't receive an Exception since Image loading is typically done asynchronously.

---

### Post by badperson on 2008-04-15
gotcha...so I should write the code so an exception is thrown when it can't find the file?

Also, from reading the post you linked to, can I set the classpath in the manifest file? Currently, I have the following line in the manifest:

```
Class-Path: lib/dep/mysql-connector-java-5.0.4.jar
```

could I just add a line to include the directory in the same line that the jar files for the dependencies are located? like this...


```
Class-Path: lib/dep/mysql-connector-java-5.0.4.jar lib/images
```

thanks for the reply,
bp

---

### Post by Zugzwang on 2008-04-16
> **badperson said:**
> gotcha...so I should write the code so an exception is thrown when it can't find the file?
What I meant was that the loading of an image could have failed even though there hasn't been an exception thrown. This is quite uncommon in Java - Everywhere else (e.g. when loading a text file) you receive Exceptions when it doesn't work. This isn't the case here, so I just mentioned it here because this is unexpected by most people, so it can easily be forgotten.

> **badperson said:**
> 
Also, from reading the post you linked to, can I set the classpath in the manifest file? 
I don't know. But I do know that the way it was intended to be done is to *add* your image to the JAR file and get its path using the "Class.getResource()" function. The idea behind this is: If your application depends on it, you have to ship it along with it anyway and then why not add it to the JAR as well?

---

