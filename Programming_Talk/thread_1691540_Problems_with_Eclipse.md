---
title: "Problems with Eclipse"
date: 2011-02-20
forum: Programming Talk
---

### Post by chome4 on 2011-02-20
Don't know what I did, but I've managed to mangle Eclipse while learning how to program in Java. I've gone to Synaptic Package manager to re-install but I get the same list of errors when compiling the simplest of programs:

Exception in thread "main" java.lang.NoClassDefFoundError: hello
   at gnu.java.lang.MainThread.run(libgcj.so.90)
Caused by: java.lang.ClassNotFoundException: hello not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/home/p/Desktop/Java/], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.90)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at gnu.java.lang.MainThread.run(libgcj.so.90)
==============================================

What do I need to do to get it working again?

---

### Post by GregBrannon on 2011-02-20
I can't tell if it's an Eclipse problem or your source code, but I'm leaning towards your source code.  However, if you think the source is OK, and you suspect you've mangled Eclipse, try creating a new workspace - which should return Eclipse to a default configuration in that workspace - and try your source code there.

If that's not working, post your source code.  We can help with self-study programming projects but not homework.

---

### Post by chome4 on 2011-02-20
I think the problem is, according to the basic tutorial I'm using, is a missing reference to 'src' when a new project is started.

When I go, File, New, Project I get a 'Select a wizard' box. There's no reference to 'Java Project'. If I follow the wizard and select 'Java Project' then create a name then 'Finish', I get a menu whose drop-down is missing 'src'.

I've attached a pic of the directory structure. I don't know if this is significant. 

I'm at the very beginning of my tutorial, using the most basic of code:

public class apples {
    public static void main(String args[]){
        System.out.println("hello");
        }
        }

I've got NetBeans installed so I can continue with that, but I'm curious to know what I've done to prevent Eclipse from running the easiest program ever!!!!

What command do I run to completely remove Eclipse, or is it best to use Synaptic....

---

### Post by GregBrannon on 2011-02-20
I think you've stumbled onto the most common mistake made my new Java programmers:

The name of your file MUST be the same as the name of the public class it contains.  If your class is called "apples", then the file name must be "apples.java"  It looks like your file name may be "hello<something>", but it's hard to say for sure.

Am I right?

---

### Post by chome4 on 2011-02-20
Yep! You're correct.

The learning continues...so much for having a day off!

Thanks for your help.

---

