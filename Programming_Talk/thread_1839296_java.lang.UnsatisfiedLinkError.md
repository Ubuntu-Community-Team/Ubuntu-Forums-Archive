---
title: "java.lang.UnsatisfiedLinkError"
date: 2011-09-05
forum: Programming Talk
---

### Post by psychok7 on 2011-09-05
hi there, i have xubuntu 11.04 64bits and i am starting to code with JavaME, i am trying to run a simple hello world and i am getting this: 

```

java.lang.UnsatisfiedLinkError: /home/psychok7/netbeans-7.0/mobility/WTK2.5.2/bin/sublime.so: /home/psychok7/netbeans-7.0/mobility/WTK2.5.2/bin/sublime.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1750)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1646)
	at java.lang.Runtime.load0(Runtime.java:787)
	at java.lang.System.load(System.java:1022)
	at com.sun.kvem.Sublime.<init>(Unknown Source)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
	at java.lang.Class.newInstance0(Class.java:372)
	at java.lang.Class.newInstance(Class.java:325)
	at com.sun.kvem.Lime.createLime(Unknown Source)
	at com.sun.kvem.KVMBridge.<init>(Unknown Source)
	at com.sun.kvem.KVMBridge.getBridge(Unknown Source)
	at com.sun.kvem.midp.MIDP.run(Unknown Source)
	at com.sun.kvem.environment.EmulatorInvoker.runEmulatorImpl(Unknown Source)
	at com.sun.kvem.environment.EmulatorInvoker.main(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at com.sun.kvem.environment.JVM.main(Unknown Source)
/home/psychok7/Documents/University Projects/MRC/MobileApplication1/nbproject/build-impl.xml:915: Execution failed with error code 1.
```

 i am using netbeans and installed the mobility plugin
how can i solve it? thanks

---

### Post by PaulM1985 on 2011-09-05
I am wondering if you have a 32-bit .so file and you are trying to load this file on a 64-bit system.

Maybe try running:
```

objdump -f sublime.so | grep ^architecture

```

and seeing what architecture the library is built for.  (I don't know what exactly this objdump will output, I copied this from another forum post to check architectures).

Paul

---

