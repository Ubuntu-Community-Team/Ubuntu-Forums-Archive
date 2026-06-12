---
title: "sun_java_wireless_toolkit-2.5.2_01-linuxi486..exception-help"
date: 2008-12-23
forum: Programming Talk
---

### Post by hoboy on 2008-12-23
I have installed sun_java_wireless_toolkit-2.5.2_01-linuxi486.bin on ubuntu 8.10 but when I run the example app directly in the tool ore I use Netbeans I get the following exception

Project "Audiodemo" loaded
Project settings saved
Building "Audiodemo"
Build complete
java.lang.UnsatisfiedLinkError: /home/muf/DEVS/NebeansDev/sun_java_wireless_toolkit-2.5.2_01/bin/sublime.so: /home/muf/DEVS/NebeansDev/sun_java_wireless_toolkit-2.5.2_01/bin/sublime.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1778)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1674)
	at java.lang.Runtime.load0(Runtime.java:770)
	at java.lang.System.load(System.java:1005)
	at com.sun.kvem.Sublime.<init>(Sublime.java:29)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:513)
	at java.lang.Class.newInstance0(Class.java:355)
	at java.lang.Class.newInstance(Class.java:308)
	at com.sun.kvem.Lime.createLime(Lime.java:40)
	at com.sun.kvem.KVMBridge.<init>(KVMBridge.java:46)
	at com.sun.kvem.KVMBridge.getBridge(KVMBridge.java:37)
	at com.sun.kvem.midp.MIDP.run(MIDP.java:699)
	at com.sun.kvem.environment.EmulatorInvoker.runEmulatorImpl(EmulatorInvoker.java:107)
	at com.sun.kvem.environment.EmulatorInvoker.main(EmulatorInvoker.java:135)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at com.sun.kvem.environment.JVM.main(JVM.java:103)

---

