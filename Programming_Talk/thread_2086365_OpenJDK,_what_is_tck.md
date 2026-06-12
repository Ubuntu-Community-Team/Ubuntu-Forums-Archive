---
title: "OpenJDK, what is tck ?"
date: 2012-11-20
forum: Programming Talk
---

### Post by jaho22 on 2012-11-20
I want to use openjdk for my site applet, openjdk should be open source, but what is tck license and tck itself ?

Do i need to check the compability of my applets with oracle jre, by some way ?

Does any one have any experience about compabilites, i think i need a bit of a help with this compabilites with openjdk and oracle jre itself.

Can i just write applet with openjdk and set the applet to my homesite and let all the people use my applet, even if they use my applet with oracle jre ?

This is a bit confusing to newbie as there is so many different java versions.

---

### Post by Unterseeboot_234 on 2012-11-20
It is incumbent on YOU to enforce anything you patent. And, in American courts anyway, when you file suit the other party gets to claim their location is the place to meet up. 

TCK is a Oracle tool to check your code against the JRE plug-in you use for deployment. When you download the TCK you learn you are not covered on embedded or mobile applications.

There is a lot of confusion about modifying the Java API while Oracle sues Google over Android. Sun, the original owner of Java, successfully sued Microsoft for a token award of $1 million USD. Microsoft was pushing JScript using Windows widgets and selling the technology. The end result is Microsoft no longer includes Java as a supported feature of their products. Their browser will pop-up warnings about Java.

[http://skife.org/java/jcp/2010/12/07/the-tck-trap.html]("http://skife.org/java/jcp/2010/12/07/the-tck-trap.html")

In short, Java code is no problem generally speaking. Modifying the plug-in of any flavor does have issues. In general with all licenses you agree to publish the owner's identification.

And, nobody cares really unless some serious money is being generated.

---

### Post by jaho22 on 2012-11-21
I still need a bit more information about tck on openjdk.

If i use openjdk then do i allways need to check that people can use my applications or applets with oracle jre too.

Most of my client computers are sure for a home computers with oracle jre, so if i use openjdk for developing, then do i need to check that my applications and applets are fullfilled with compatibility with main oracle jre.

---

### Post by slickymaster on 2012-11-21
An implementation of Java is everything needed to run a Java program - the main components of which are a Java Virtual Machine and the class libraries. J2SE is the most common Java implementation used, though it's not completely free.

Java Technology Compatibility Kit (or TCK) certifies that your implementation adheres to the Java Specification Requests (or JSR ).

TCK is in many ways a rubber stamping. It doesn't stop software from working properlly, it only prevents it from being officially called Java, as it hasn't passed all the officially-certified compatibility tests (they are what defines what is and isn't Java). The situation is similar to Unix - there are many Unix-like operating systems out there (Linux being the best known), but relatively few go to the expense of becoming certified as Unix, and thus allowed to use the Unix trademarks.

You should take a look at the [OpenJDK FAQ]("http://openjdk.java.net/faq/") for implementations meeting the requirements of the OpenJDK TCK License Agreement.

---

