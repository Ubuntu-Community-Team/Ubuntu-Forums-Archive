---
title: "Eclipse / JOGL on gutsy"
date: 2007-11-17
forum: Packaging and Compiling Programs
---

### Post by eTerNaL_eNigMa on 2007-11-17
Greetings all,

Well I have searched and searched. And obviously I am missing something :0)

Perhaps I could get a bit of help.

I am trying to get the latest jogl working in the latest eclipse on ubuntu 7.10 with java6u3 installed. (Furthermore, might be good to note this is an amd64 machine. The java installed though is 32 bit for javaws support.)

I downloaded the jogl zip (jogl-1.1.1-rc7-linux-amd64) from jogl.dev.java.net. I placed the jogl files, this includes two jars (jogl and gluegen-rt) and 4 .so files in the /usr/lib/Java6/jre/lib/ext folder.

I then loaded up eclipse, and imported a project that I have been working on. (using jogl, was working on it in windows.) I brought in all the files, and made sure the dependency structure was intact. (for my files at least).

I checked in eclipse under the package explorer, and I see that the jogl and gluegen jars are displayed there.

When hitting run, I got: 
Exception in thread "main" java.lang.UnsatisfiedLinkError: no gluegen-rt in java.library.path

Any help please?

PS: I have tried setting the native runtime libraries of the jogl and gluegen jars to the same usr/lib/Java6/jre/lib/ext folder.

I also tried opening project->properties and making sure jogl.jar and gluegen.jar were in the class build paths.

I also tried opening the run dialogue and adding the -Djava.library.path=.:/usr/lib/Java6/jre/lib/ext/jogl.jar:/usr/lib/Java6/jre/lib/ext/gluegen-rt.jar
to the VM arguments.

So I am getting a little frustrated :0)

PLEASE HELP ME ! :0)

---

### Post by eTerNaL_eNigMa on 2007-11-17
Realizing as I typed this out, That I have the 64bit jogl and 32bit java. I will go get the 32bit jogl and see if it works! Hopefully thats what the prob was! 

<-- feeling very silly, Will post back with the results.

---

### Post by eTerNaL_eNigMa on 2007-11-17
Well. This will teach me to do downloads late in the night. Installing the appropriate jogl matching my java install appears to have solved all the problems...


ugh

---

### Post by cpetzol2 on 2008-02-14
I am getting the exact same error, and I too am using Gutsy on AMD64.

I am using 32bit JVM to run the eclipse IDE, but in my project settings, I am executing my project with Java 6 64-bit.

When I was first setting up SWT, I was getting the same errors, and realized i was using a 32 bit SWT. Getting the proper version fixed all problems.

I played with SWT for a while, and then decided I wanted to start using JOGL with SWT. I downloaded "jogl-1.1.0-linux-amd64" and added jars to classpath (in the exact same manner as I did for SWT). The jogl.jar is not throwing any flags, only gluegen-rt.jar. 

Also to note, I did not do anything with the native libraries included with the jogl download. I have openGL installed, but that is not to say java is talking to it properly. 

My best guess is that I need to do more with the native libraries, although that is merely a guess. 

If anyone could send a shout on how to install the native libraries, or give any other help on what is causing the problem. Keep in mind, Im getting better with linux (going on 16 months) but Im no CLI guru, and I often overlook the obvious.

Thanks
```

Exception in thread "main" java.lang.UnsatisfiedLinkError: no gluegen-rt in java.library.path
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1682)
	at java.lang.Runtime.loadLibrary0(Runtime.java:823)
	at java.lang.System.loadLibrary(System.java:1030)
	at com.sun.gluegen.runtime.NativeLibLoader$1.run(NativeLibLoader.java:68)
	at java.security.AccessController.doPrivileged(Native Method)
	at com.sun.gluegen.runtime.NativeLibLoader.loadGlueGenRT(NativeLibLoader.java:66)
	at com.sun.gluegen.runtime.NativeLibrary.ensureNativeLibLoaded(NativeLibrary.java:399)
	at com.sun.gluegen.runtime.NativeLibrary.open(NativeLibrary.java:163)
	at com.sun.gluegen.runtime.NativeLibrary.open(NativeLibrary.java:129)
	at com.sun.opengl.impl.x11.DRIHack.begin(DRIHack.java:109)
	at com.sun.opengl.impl.x11.X11GLDrawableFactory.<clinit>(X11GLDrawableFactory.java:96)
	at java.lang.Class.forName0(Native Method)
	at java.lang.Class.forName(Class.java:169)
	at javax.media.opengl.GLDrawableFactory.getFactory(GLDrawableFactory.java:111)
	at context.SwtGL.<init>(SwtGL.java:32)

```

---

### Post by cpetzol2 on 2008-02-14
Well, if you are reading this attempting to help me, I am sorry for wasting your time. I figured it out about 60 seconds after I submit my first reply.

The solution I have is only through eclipse; I am not exactly sure how this would work with command line. The problem was with the native libraries.

To add the native libraries to your project...

In your eclipse project properties -> Java Build Path, go to your library, find the gluegen-rt.jar, expand it, and click on Native Library Location and enter the location for the native libraries that came with your JOGL download.

Simple enough, I  have just never had to deal with specific binaries in java before.

Hope it helps someone.

---

### Post by stryderjzw on 2008-03-15
Awesome, cpetzol2. Thanks for the tips.

---

### Post by jespdj on 2008-03-19
For if you encounter an UnsatisfiedLinkError in Java in the future: this means that it is missing a native library (in your case, the library named gluegen-rt.so).

---

### Post by Shin_Gouki2501 on 2008-03-19
interesting how many people lately try java and openGL , what they are up to?
Maybe somethign like this:
[http://www.hackwars.net/200803/hack-wars-unveils-new-site](http://www.hackwars.net/200803/hack-wars-unveils-new-site)

:)

---

### Post by blingo on 2008-10-16
> **cpetzol2 said:**
> Well, if you are reading this attempting to help me, I am sorry for wasting your time. I figured it out about 60 seconds after I submit my first reply.

The solution I have is only through eclipse; I am not exactly sure how this would work with command line. The problem was with the native libraries.

To add the native libraries to your project...

In your eclipse project properties -> Java Build Path, go to your library, find the gluegen-rt.jar, expand it, and click on Native Library Location and enter the location for the native libraries that came with your JOGL download.

Simple enough, I  have just never had to deal with specific binaries in java before.

Hope it helps someone.

Exactly the same problem, but Eclipse doesn't seem to remember the native library - 
I add the library, press o.k,
and if I reopen the properties -> Java Build Path....
It as if I didn't add it at all...

Anyone have an idea?

EDIT: UPDATE:

o.k now I get this as an output from the console:
int: f4240

it doesn't make any difference even if I make mistakes in the program,
or even if I put in comments the entire class -  t still outputs this.
I suspect the binary files that came with the package.

help?

---

