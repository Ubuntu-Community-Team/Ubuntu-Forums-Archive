---
title: "UnsatisfiedLinkError while trying to start a J2ME application"
date: 2008-08-29
forum: Programming Talk
---

### Post by DoDoENT on 2008-08-29
Hello everyone! I'm trying to create a little J2ME application on my 64-bit hardy heron, but even before I've written a single line of code, I tried to start some demo projects and I get the following error:

java.lang.UnsatisfiedLinkError: /opt/java_wireless/bin/sublime.so: /opt/java_wireless/bin/sublime.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1647)
	at java.lang.Runtime.load0(Runtime.java:770)
	at java.lang.System.load(System.java:1005)
	at com.sun.kvem.Sublime.<init>(Unknown Source)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:513)
	at java.lang.Class.newInstance0(Class.java:355)
	at java.lang.Class.newInstance(Class.java:308)
	at com.sun.kvem.Lime.createLime(Unknown Source)
	at com.sun.kvem.KVMBridge.<init>(Unknown Source)
	at com.sun.kvem.KVMBridge.getBridge(Unknown Source)
	at com.sun.kvem.midp.MIDP.run(Unknown Source)
	at com.sun.kvem.environment.EmulatorInvoker.runEmulatorImpl(Unknown Source)
	at com.sun.kvem.environment.EmulatorInvoker.main(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at com.sun.kvem.environment.JVM.main(Unknown Source)

Can someone help me please?

---

### Post by odyniec on 2008-08-29
You probably need to run the demos with a 32-bit JVM. See this blog post -- it's about running 32-bit Eclipse, but it should give you some hints:
[http://dmartin.org/weblog/eclipse-on-ubuntu-linux-for-amd64](http://dmartin.org/weblog/eclipse-on-ubuntu-linux-for-amd64)

---

### Post by tinny on 2008-08-29
Need some more info.

Are you talking about a mobile phone application? (Mobile Information Device Profile (MIDP))

If so do you have a J2ME emulator installed on your system?

[http://java.sun.com/products/sjwtoolkit/](http://java.sun.com/products/sjwtoolkit/)

---

### Post by DoDoENT on 2008-08-30
> **odyniec said:**
> You probably need to run the demos with a 32-bit JVM. See this blog post -- it's about running 32-bit Eclipse, but it should give you some hints:
[http://dmartin.org/weblog/eclipse-on-ubuntu-linux-for-amd64](http://dmartin.org/weblog/eclipse-on-ubuntu-linux-for-amd64)

Thanks. This could be the solution as Sun Wireless Toolkit has probably 32-bit natives and I am trying to run this on a 64 bit JVM. I'll try this next month because I'm out of bandwith for this one.

---

