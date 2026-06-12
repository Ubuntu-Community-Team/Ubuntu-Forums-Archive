---
title: "Making Packages with Java"
date: 2009-06-02
forum: Programming Talk
---

### Post by ThewhiteLynx on 2009-06-02
Beginning programming with Java

I am trying to generate packages which I can import into my other programs, how do I go about this? Currently I have a main folder for my programs and then I used Bluej to generate a new project in which I made a package and put in a test class. How do I make it so that I can import this package into my other applications which are based in said main folder? I think the problem is I need to set the Classpath environment, but I have no idea how to do so and moreover I am not sure if BlueJ does this automatically or not, or perhaps I am merely not using the right import statement?  I just typed 'import testpackage,' do I need to include it's file location or anything?

Miscellaneous question:  What is a programming library?  I keep hearing the term used, but I am at a loss.  

Thanks,

Lynx

---

### Post by Reiger on 2009-06-02
A programming library is a library of pre-programmed functions/stuff. So you don't have to do that but can `borrow/share' the code of the library. ;)

A JAR file is *the* package format within Java software. By and large libraries/packages tend to be bottled in their own JAR's/sub-JAR's. All you must then do in your `calling JAR' is making sure that the `called JAR' is on the classpath. For every libraries distributed with your JVM by its vendor (e.g. SUN or IBM) this is automatically the case. For other libraries you can make this `automatic' by installing them in the 3rd party extensions folder (but be warned that doing this with your own program libraries is worse than bad practice). 

For your own libraries (that you write yourself) you can use the Manifest file to specify the (additional) Classpath you require. I suggest you read up on:
1) Classpaths
2) Creating a Manifest file for a JAR file
3) Using your IDE of choice to work with `build' and `run' configurations
4) Using your IDE of choice to generate the Manifest files required.

---

### Post by froggyswamp on 2009-06-03
[http://www.digilife.be/quickreferences/PT/Build%20your%20own%20Java%20library.pdf](http://www.digilife.be/quickreferences/PT/Build%20your%20own%20Java%20library.pdf)

---

