---
title: "java.lang.ClassFormatError"
date: 2007-08-09
forum: Programming Talk
---

### Post by Coder_wannabe on 2007-08-09
I recently installed the java sdk 1.6 in Ubuntu.  I tried to compile a simple Hello World gui and got the following error:

mcman06@MrBernard-laptop:~/workspace/HelloGui$ java HelloWorldgui 
Exception in thread "main" java.lang.ClassFormatError: HelloWorldgui (unrecognized class file version)
   at java.lang.VMClassLoader.defineClass(libgcj.so.70)
   at java.lang.ClassLoader.defineClass(libgcj.so.70)
   at java.security.SecureClassLoader.defineClass(libgcj.so.70)
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)

I am using java version 1.4.2 and javac 1.6.0.

I did an update-alternatives --config java which did not work either. I got the following message:


update-alternatives: [COLOR="Red"]unable to make /etc/alternatives/java.dpkg-tmp a symlink to /usr/lib/jvm/java-6-sun/jre/bin/java: Permission denied[/COLOR]

I am not even really sure if this was the right thing to do.  

Could some one please help.

Thanks in advance.

---

### Post by Damiel on 2007-08-09
Run in a terminal:
```
sudo update-java-alternatives -l
```

to verify that you have the JDK 6 installed correctly. It should output something like this: *java-6-sun 63 /usr/lib/jvm/java-6-sun*

Next, run:
```
sudo update-java-alternatives -s java-6-sun
```

This way both javac and java v6 will be used by default.

---

### Post by Coder_wannabe on 2007-08-09
Ok thanks.  I will try it and let you know how it goes...

---

### Post by Coder_wannabe on 2007-08-09
Thanks alot.  That did the trick
:guitar:

---

