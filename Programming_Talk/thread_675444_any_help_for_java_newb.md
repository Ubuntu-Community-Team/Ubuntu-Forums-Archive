---
title: "any help for java newb?"
date: 2008-01-22
forum: Programming Talk
---

### Post by AlexenderReez on 2008-01-22
hm...i'm average c programmer....i just try to learn java ...i test eclipse ,,and it is working great.i wonder how do i  compile and run java script without using any application(like eclipse)....i noticed i can compile script with

> reez@alexenderreez:~$ javac /home/reez/testjavalec.java
  

but when i try to run it

> reez@alexenderreez:~$ java /home/reez/TestGreeting.class
Exception in thread "main" java.lang.NoClassDefFoundError: .home.reez.TestGreeting.class
   at gnu.java.lang.MainThread.run(libgcj.so.81)
Caused by: java.lang.ClassNotFoundException: .home.reez.TestGreeting.class not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.81)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at gnu.java.lang.MainThread.run(libgcj.so.81)


**i manage to create TestGreeting.class

is there anything wrong.Lastly,i think i can learn faster if i manage to compare java iwth c language.(its syntax...variable..etc)..i hope anybody can give a link..i get java tutorial using few guide in this section..but none of those give c programming to java...

---

### Post by LaRoza on 2008-01-22
See my wiki (the second one). The link is in my Learn to Program Wiki.

---

### Post by naugiedoggie on 2008-01-23
> **AlexenderReez said:**
> hm...i'm average c programmer....i just try to learn java ...i test eclipse ,,and it is working great.i wonder how do i  compile and run java script without using any application(like eclipse)....i noticed i can compile script with

 

but when i try to run it



**i manage to create TestGreeting.class

is there anything wrong.Lastly,i think i can learn faster if i manage to compare java iwth c language.(its syntax...variable..etc)..i hope anybody can give a link..i get java tutorial using few guide in this section..but none of those give c programming to java...

Hello,

Java depends on packages to define the location of class files.  Packages reflect the directory structure within which the class file is embedded.

The clue to your error is here:

```
Exception in thread "main" java.lang.NoClassDefFoundError: .home.reez.TestGreeting.class
```

When you pass in the directory structure, Java expects to find a package called home.reez in the class TestGreeting.  Evidently, it doesn't.

Try this.  Create a directory structure like this:  it doesn't matter what names you use:  org/trollope/admin.  In this directory, create a java class file:  Hello.java.  The first line in that file which is not a comment should be:  

```
package org.trollope.admin;
```

The name of the class must match the name of the file, including capitalization:

```
public class Hello {

     public static void main(String [] args){
          System.out.println("Hello, I'm Java");
     }
}
```

From the command line, compile this file in the directory immediately above org.  

```
powem@pdxpowem01 ~/src
$ javac -cp . org/trollope/admin/Hello.java

```
Then run the file like this:  

```
powem@pdxpowem01 ~/src
$ java org.trollope.admin.Hello
Hello, I'm Java

```

Java is considered a "C-based" language because of the derivation of most of its core features.  I don't know that you will find it useful to compare the two. Structurally, the two are very similar and you can write procedurally in Java, as you have been doing in C, if you wish.  But, it's naughty.  ;-)

[Java For C Programmers]("http://www.d.umn.edu/~gshute/java/c2java.html")

[Java for C Programmers -- Reference]("http://www-plan.cs.colorado.edu/~doerr/teaching/csci3308/javaforc/javaswitch.html")

Thanks.

mp

---

### Post by Alberio on 2008-01-23
simple answer?
:
> reez@alexenderreez:~$ java /home/reez/TestGreeting.class
don't type the .class

leave it as /home/reez/TestGreeting


example of the same thing happening:

```

paarth@Astarael:~/Java$ pico etc1.java
paarth@Astarael:~/Java$ javac etc1.java
paarth@Astarael:~/Java$ java etc1
hello?
paarth@Astarael:~/Java$ java etc1.class
Exception in thread "main" java.lang.NoClassDefFoundError: etc1/class
paarth@Astarael:~/Java$

```

I believe that's the same reason

p.s. run it from the folder it's in?.


ooops, the poster above me had a solution that probably works

---

### Post by jaytek13 on 2008-01-23
> **Alberio said:**
> ooops, the poster above me had a solution that probably works


But I'd consider your answer more helpful...

The simple answer is... you do not need and should not type "class.class" when trying to run a program after you compile it. It's redundant as far as java is concerned.

---

### Post by naugiedoggie on 2008-01-24
> **jaytek13 said:**
> But I'd consider your answer more helpful...

The simple answer is... you do not need and should not type "class.class" when trying to run a program after you compile it. It's redundant as far as java is concerned.

Hello,

Actually, it is not "redundant," it is wrong. The java binary considers the dot to be a part of the package and therefore translates it into a slash.  As you could have noted, had you actually looked at the error message.  

I'm sorry that you feel that my answer was not helpful.  However, to be helpful requires correct and accurate information.  

The OP had several issues inherent in what he was doing, and I tried to set him on the right track.  Java's concept of packages is, in my experience, quite confusing to beginners.  It is one reason why beginners gravitate to IDEs that hide the complexity of what they are doing -- only to find out later that their lack of understanding compounds issues and impedes debugging as they develop applications of increasing complexity.

Thanks.

mp

---

### Post by AlexenderReez on 2008-02-13
thanks

---

