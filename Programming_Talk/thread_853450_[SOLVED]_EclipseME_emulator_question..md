---
title: "[SOLVED] EclipseME emulator question."
date: 2008-07-08
forum: Programming Talk
---

### Post by blackaardvark on 2008-07-08
Does anybody use EclipseME with ubuntu?  I'm having trouble making the emulator work  (I'm experimenting with java games). The console errors look like this:
```
/usr/share/themes/Silicon/gtk-2.0/gtkrc:64: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Silicon/gtk-2.0/gtkrc:177: Priority specification is unsupported, ignoring
java.lang.UnsatisfiedLinkError: /home/sam/Desktop/stuff1/untitled/bin/sublime.so: Can't load IA 32-bit .so on a AMD 64-bit platform
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1647)
	at java.lang.Runtime.load0(Runtime.java:769)
	at java.lang.System.load(System.java:968)
	at com.sun.kvem.Sublime.<init>(Unknown Source)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:494)
	at java.lang.Class.newInstance0(Class.java:350)
	at java.lang.Class.newInstance(Class.java:303)
	at com.sun.kvem.Lime.createLime(Unknown Source)
	at com.sun.kvem.KVMBridge.<init>(Unknown Source)
	at com.sun.kvem.KVMBridge.getBridge(Unknown Source)
	at com.sun.kvem.midp.MIDP.run(Unknown Source)
	at com.sun.kvem.environment.EmulatorInvoker.runEmulatorImpl(Unknown Source)
	at com.sun.kvem.environment.EmulatorInvoker.main(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at com.sun.kvem.environment.JVM.main(Unknown Source)
```
  
Any advice or should I just use M$?

---

### Post by tinny on 2008-07-08
> **blackaardvark said:**
> Does anybody use EclipseME with ubuntu?  I'm having trouble making the emulator work  (I'm experimenting with java games). The console errors look like this:
```
/usr/share/themes/Silicon/gtk-2.0/gtkrc:64: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Silicon/gtk-2.0/gtkrc:177: Priority specification is unsupported, ignoring
java.lang.UnsatisfiedLinkError: /home/sam/Desktop/stuff1/untitled/bin/sublime.so: Can't load IA 32-bit .so on a AMD 64-bit platform
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1647)
	at java.lang.Runtime.load0(Runtime.java:769)
	at java.lang.System.load(System.java:968)
	at com.sun.kvem.Sublime.<init>(Unknown Source)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:494)
	at java.lang.Class.newInstance0(Class.java:350)
	at java.lang.Class.newInstance(Class.java:303)
	at com.sun.kvem.Lime.createLime(Unknown Source)
	at com.sun.kvem.KVMBridge.<init>(Unknown Source)
	at com.sun.kvem.KVMBridge.getBridge(Unknown Source)
	at com.sun.kvem.midp.MIDP.run(Unknown Source)
	at com.sun.kvem.environment.EmulatorInvoker.runEmulatorImpl(Unknown Source)
	at com.sun.kvem.environment.EmulatorInvoker.main(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at com.sun.kvem.environment.JVM.main(Unknown Source)
```
  
Any advice or should I just use M$?

NO DONT USE M$

I have EclipseME working really well in Ubuntu Hardy.

How did you install Eclipse? (using synaptic package manager, or eclipse.org download?).
Did you install EclipseME from the update site? [http://www.eclipseme.org/updates/]("http://www.eclipseme.org/updates/")
Do you have a J2ME emulator installed? If so is it the WTK? What version.

Need some more info on your current setup.

---

### Post by blackaardvark on 2008-07-08
I'm using Gutsy, but I'm hesitant to upgrade as I'm limited with how much I can backup at the moment.

[This]("http://koderko.dk/J2METutorial/") inspired me to try out J2ME but it doesn't provide any help with configuring "run" so I've been trying changing this and that but to no avail!

I installed eclipse with synaptic and then added ME as a plug-in from the update site mentioned.

I've got the Sun WTK 2.5.2 which seems to be recognized by eclipse.

What am I doing wrong?

---

### Post by tinny on 2008-07-08
> **blackaardvark said:**
> I'm using Gutsy, but I'm hesitant to upgrade as I'm limited with how much I can backup at the moment.

I installed eclipse with synaptic and then added ME as a plug-in from the update site mentioned.

I've got the Sun WTK 2.5.2 which seems to be recognized by eclipse.

What am I doing wrong?

Have you followed this?

[http://eclipseme.org/docs/installation.html]("http://eclipseme.org/docs/installation.html")

Also what Java runtime is Eclipse using?

Window > Preferences > Java > Installed JRE's

You really want to use the Sun JDK. (You should install it if you dont have it)

---

### Post by blackaardvark on 2008-07-09
It works!

I installed the JDK and pointed eclipse towards this folder in the Installed JRE menu :

```
/usr/lib/jvm/
```


Thanks :)

---

### Post by tinny on 2008-07-09
> **blackaardvark said:**
> It works!

I installed the JDK and pointed eclipse towards this folder in the Installed JRE menu :

```
/usr/lib/jvm/
```


Thanks :)

This is good news. :)

It really does need to be noted somewhere that when doing development on Ubuntu you should use the Sun JDK.

---

