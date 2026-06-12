---
title: "java from the command line"
date: 2007-09-11
forum: Programming Talk
---

### Post by Lars Noodén on 2007-09-11
I have two files, [FONT="Courier New"]HelloWorld.class[/FONT] and [FONT="Courier New"]HelloWorld.java[/FONT], in a directory [FONT="Courier New"]~/workspace/HelloWorld\!/foo/[/FONT]
What options do I add to the java command to execute from the command line classes created in Eclipse?  

"java -cp ~/workspace/ HelloWorld" gives me the following error

[FONT="Courier New"]Exception in thread "main" java.lang.NoClassDefFoundError: HelloWorld   at gnu.java.lang.MainThread.run(libgcj.so.70)Caused by: java.lang.ClassNotFoundException: HelloWorld not found in gnu.gcj.runtime.SystemClassLoader{urls=[], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}[/FONT]

---

### Post by tenmillionmilesaway on 2007-09-11
try
```
java ~/workspace/HelloWorld\!/foo/HelloWorld
```
also are you aware that you are using the gnu gcj java rather than the sun version of java

---

### Post by Lars Noodén on 2007-09-11
> **tenmillionmilesaway said:**
> try
```
java ~/workspace/HelloWorld\!/foo/HelloWorld
```


Yes, thanks.  I've tried that but get this error anyway:


[FONT="Courier New"]Exception in thread "main" java.lang.ClassFormatError: erroneous class name   at java.lang.VMClassLoader.defineClass(libgcj.so.70)   at java.lang.ClassLoader.defineClass(libgcj.so.70)   at java.security.SecureClassLoader.defineClass(libgcj.so.70)   at java.net.URLClassLoader.findClass(libgcj.so.70)   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)   at java.lang.ClassLoader.loadClass(libgcj.so.70)   at java.lang.ClassLoader.loadClass(libgcj.so.70)   at gnu.java.lang.MainThread.run(libgcj.so.70)
[/FONT]


> **tenmillionmilesaway said:**
> ...
also are you aware that you are using the gnu gcj java rather than the sun version of java

Blissfully ignorant.  I ran apt-get install free-java-sdk.
For what it's worth, it says java version "1.4.2"gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

Anyway,
Programs made with Eclipse seem to work from within Eclipse.
Making a program via vi seems to work from the command line.

However, I'm not sure what's needed to get a program made in Eclipse to run from the command line.

---

### Post by tenmillionmilesaway on 2007-09-11
I cant really help without seeing the contents of Hello.java as im not familiar with gcj errors.
However if you run the program in eclipse and change to the debug perspective and then right click on the process in the debug box in the top left and go to properties it will show you the command line which eclipse is running your code with, this will be exactly the same as what you need to run the program from outside eclipse.

If you want sun java then search for "sun java" in synaptic and install the relevent packages. then run
```
sudo update-alternatives --config java
```
```
sudo update-alternatives --config javac
```

and choose the right version of java. (you may also need to do it for javadoc, javah etc depending on what you need)

just thought that foo might be a package, if so then the commandline will be java ```
java ~/workspace/HelloWorld\!/foo.HelloWorld
```

---

### Post by Lars Noodén on 2007-09-11
Actually, that nudged me in the right direction.
I re-did the example and this time around notice that the class does not need to have the path listed, that goes separately.  e.g.

 java -cp ./workspace/HelloWorld/ HelloWorld

---

### Post by astrobob.tk on 2010-01-01
hey guys,

i just recently was trying to install Java with command line. during the process i was given some kind of license. I assume i had to click ok, but i couldn't figure out how ? i tried it several times & thus interrupted the installation process using the "ctrl+c" command.

Then I was trying to access the synaptic package manager & it gave me this error:
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```could you pleas help me figure this out & install Java ?

P.S. I am not an advanced user

thank you

---

### Post by cyberslayer on 2010-01-01
The license screen is text-based so you need to select "OK" with the arrow keys and then press Enter.  Clicking will not work.

---

### Post by astrobob.tk on 2010-01-01
> **cyberslayer said:**
> The license screen is text-based so you need to select "OK" with the arrow keys and then press Enter.  Clicking will not work.

well yeh now it went fine. thx

but I have another question. not sure if its related to this thread.

I installed a new software which requires OpenGL. when i run it it say "Could Not Initialize OpenGL. Press Cancel to kill or OK with a possibility of data corruption".
whats the issue ?

btw Happy New Year :D

---

