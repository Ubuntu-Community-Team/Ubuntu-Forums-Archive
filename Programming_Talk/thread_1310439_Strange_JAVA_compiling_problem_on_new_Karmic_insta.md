---
title: "Strange JAVA compiling problem on new Karmic install"
date: 2009-11-01
forum: Programming Talk
---

### Post by kfsorensen on 2009-11-01
Hello,

I'm having an extremely strange problem on the new install of Karmic Koala on my desktop machine.  My laptop machine, also running Karmic (but an alpha version) doesn't have the same problem, and I simply cannot figure out why.

I'm trying to compile my Java programs.  They utilize the Java Open GL (JOGL) libraries to render graphics in 3D (a whole 'nother problem I'm having in Ubuntu).

They won't compile, but here's what's totally confusing.  I set my .bashrc file just exactly the same way on my desktop as on my laptop, to include the JOGL files that I need in the compile, but when I go to compile, I get all of the error messages from the compiler indicating that it can't find the class files.

I'm no Java newbie (been coding in Java for 10 years) and I've seen this message and know what it means, but I cannot figure out WHY Java can't find these classes.

I've got my JOGL classes loaded in a directory:  /home/kirk/jogl111a

The files are in the "lib" directory: /home/kirk/jogl111a/lib

So my .bashrc file reads like this:

CLASSPATH=$CLASSPATH:/home/kirk/jogl111a/lib/jogl.jar:/home/kirk/jogl111a/lib/gluegen-rt.jar

LD_LIBRARY_PATH=/home/kirk/jogl111a/lib/

When I query the CLASSPATH and the LD_LIBRARY_PATH, I get this:

kirk@HPdesktop:~$ echo $CLASSPATH
:/home/kirk/jogl111a/lib/jogl.jar:/home/kirk/jogl111a/lib/gluegen-rt.jar

and

kirk@HPdesktop:~$ echo $LD_LIBRARY_PATH
/opt/intel/Compiler/11.1/046/lib/ia32:/opt/intel/Compiler/11.1/046/mkl/lib/32:/home/kirk/jogl111a/lib/

which seem to indicate that the necessary .jar files are in the classpath, but when I compile, it acts as if they are not there.  Any ideas why this doesn't work, and why the EXACT SAME code compiles fine on my other machine?

---

### Post by terry_a_g on 2009-11-01
Try removing $CLASSPATH in ```
CLASSPATH=$CLASSPATH:/home/kirk/jogl111a/lib/jogl.jar:/home/kirk/jogl111a/lib/gluegen-rt.jar
```
The colon at the front of your CLASSPATH is causing trouble.  I ran into this exact issue the other day, and that solved it for me.

---

### Post by kfsorensen on 2009-11-01
Any suggestion for a better CLASSPATH line in .bashrc?

Running "echo $CLASSPATH" on the other machine (the one that works) gives:

.:/home/kirk/jogl111a/lib/jogl.jar:/home/kirk/jogl111a/lib/gluegen-rt.jar

it's a very small difference (the period at the beginning) but I wonder if it might be important

---

### Post by kfsorensen on 2009-11-01
I removed CLASSPATH and got this on a query:

```
kirk@HPdesktop:~/java$ echo $CLASSPATH
/home/kirk/jogl111a/lib/jogl.jar:/home/kirk/jogl111a/lib/gluegen-rt.jar
```

But the same problem remains.  Do I need to reboot or anything like that?

---

### Post by terry_a_g on 2009-11-02
You shouldn't need a reboot.  I'm just stabbing in the dark here, but try setting your CLASSPATH=".:/home/kirk/jogl111a/lib/jogl.jar:/home/kirk/jogl111a/lib/gluegen-rt.jar" That little period, which stands for your current working directory, could solve your problem if the classes it can't find are in the same directory that you're in when you issue your compile command.  I dunno what else to recommend w/o more info like compiler errors.

---

### Post by kfsorensen on 2009-11-02
Thanks Terry, I tried what you said but it didn't work:

```
kirk@HPdesktop:~/java$ echo $CLASSPATH
.:/home/kirk/jogl111a/lib/jogl.jar:/home/kirk/jogl111a/lib/gluegen-rt.jar
```The compiler errors are thus:

```
LHRSystemModel.java:702: cannot find symbol
symbol  : method glColor3f(float,float,float)
location: interface javax.media.opengl.GL
          gl.glColor3f(1.0f, 0.0f, 0.0f);
```A hundred errors just like that, all looking for the "javax.media.opengl.GL" interface that lives in the jogl.jar file.  I know it's there, I checked, and the same program compiles and runs fine on my laptop that also has the same commands in the .bashrc file and also runs Karmic Koala, which is why I'm so utterly confused as to why this is happening.

I somehow cannot convince this computer to go look in the jogl.jar file that lives in the directory I tell it and use it for compilation.

Strangely, when I run the "javac" command like this:

```
javac -classpath /home/kirk/jogl111a/lib/jogl.jar;/home/kirk/java LHRDesign.java
```

it finds the jogl.jar files, but says:

```
javac: no source files
Usage: javac <options> <source files>
use -help for a list of possible options
bash: /home/kirk/java: is a directory
```

---

### Post by HotCupOfJava on 2009-11-02
Very strange - is there ANY chance the copies of those 2 .jar files don't contain the necessary .class files on that particular machine?

Just taking a stab in the dark...

---

### Post by kfsorensen on 2009-11-02
Nope, I checked.  They're in there.  Sometimes the compiler finds them when I embed the classpath statement in the javac command, but then it can't find the rest of the class files that the rest of program uses.

---

### Post by terry_a_g on 2009-11-03
bash: /home/kirk/java: is a directory

You have a semicolon in your classpath instead of a colon.  Change that semicolon to a colon and retry, but I don't see how setting it there will work any better than the environment variable.  Stranger things have happened I guess.

I'm not exactly sure how this library works, but I'm assuming it uses JNI to interface with libGL.so?  Did you build this java library on that machine, or just copy it over from your other machine?  I'm wondering if it's having trouble w/ the JNI stuff or maybe not finding the opengl libraries.  It should be finding the native libs because you did set your LD_LIBRARY_PATH though.

If you ever do find a solution to this, be sure to post it.  Hopefully it's just some silly mistake, but it sure is frustrating.

---

### Post by Arndt on 2009-11-03
Could possibly 'strace' be of help? You should be able to see what files it tries to open. Maybe the pattern is different on the two machines in some interesting way.

---

### Post by jespdj on 2009-11-03
> **kfsorensen said:**
> Strangely, when I run the "javac" command like this:

```
javac -classpath /home/kirk/jogl111a/lib/jogl.jar;/home/kirk/java LHRDesign.java
```

it finds the jogl.jar files, but says:

```
javac: no source files
Usage: javac <options> <source files>
use -help for a list of possible options
bash: /home/kirk/java: is a directory
```
That is because you are using a semi-colon ; in the classpath. On Linux you must use a colon : and not a semi-colon:

```
javac -classpath /home/kirk/jogl111a/lib/jogl.jar:/home/kirk/java LHRDesign.java
```

---

### Post by kfsorensen on 2009-11-03
No dice, when I run the compile command this way:

```
javac -classpath /home/kirk/jogl111a/lib/jogl.jar:/home/kirk/jogl111a/lib/gluegen-rt.jar:/home/kirk/java LHRDesign.java
```

it doesn't find the jogl classes at all.  I have no idea why, but changing from the semicolon to the colon was one of the first tricks I tried, with no success.

```
/home/kirk/java/util/OpenGLWriter.java:563: cannot find symbol
symbol  : method glNormal3dv(double[],int)
location: interface javax.media.opengl.GL
        gl.glNormal3dv(normal,0);
```(a hundred more errors just like this, all looking for javax.media.opengl.GL.

---

### Post by fct on 2009-11-03
Just to be sure, please paste the output of "javac -version".

---

### Post by kfsorensen on 2009-11-03
> **fct said:**
> Just to be sure, please paste the output of "javac -version".

javac 1.6.0_16

---

### Post by jespdj on 2009-11-04
> **kfsorensen said:**
> it doesn't find the jogl classes at all.  I have no idea why, but changing from the semicolon to the colon was one of the first tricks I tried, with no success.

```
/home/kirk/java/util/OpenGLWriter.java:563: cannot find symbol
symbol  : method glNormal3dv(double[],int)
location: interface javax.media.opengl.GL
        gl.glNormal3dv(normal,0);
```(a hundred more errors just like this, all looking for javax.media.opengl.GL.
Are you sure you're not mixing different versions of JOGL? There's JOGL 1.1.1 which you seem to be using, which indeed has a method glNormal3dv in class GL. But according to the [API docs of JOGL 2.x](http://download.java.net/media/jogl/jogl-2.x-docs/) there is no such method in class GL.

Make sure you're using the right version.

---

### Post by kfsorensen on 2009-11-04
I'm using the right version--I've already had the problem you described, which is why I jumped back to jogl-1.1.1.  This code compiles successfully under Windows and the same JOGL.  It even compiles successfully on my dying laptop running Ubuntu 9.10.  But on my new fast machine (and on another one I tried last night) it has this persistent problem.

---

### Post by kfsorensen on 2009-11-04
I did something differently and it worked on one of my machines--tonight I'll get home and try it on the other machine and see if my luck holds out.

I followed some of the instructions on this page:

[http://www.semiantics.com/?p=112](http://www.semiantics.com/?p=112)

and installed the JOGL libraries as root instead of as me.  I loaded them into /opt/jogl111a and then modified my .bashrc file to read like this:

```
export CLASSPATH=${CLASSPATH}:/opt/jogl111a/lib/jogl.jar
export CLASSPATH=${CLASSPATH}:/opt/jogl111a/lib/gluegen-rt.jar
export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/opt/jogl111a/lib/
```When I echoed CLASSPATH I got:

```
:/opt/jogl111a/lib/jogl.jar:/opt/jogl111a/lib/gluegen-rt.jar
```and when I echoed LD_LIBRARY_PATH I got:

```
:/opt/jogl111a/lib/
```But lo and behold the compile worked!  Which makes me wonder if the compiler didn't have the permissions to read the libraries?  Could that have been the problem?

---

### Post by kfsorensen on 2009-11-04
This "trick" did NOT work on my home desktop machine--where I really needed to have some success.  The compiler still doesn't see the libraries.

---

