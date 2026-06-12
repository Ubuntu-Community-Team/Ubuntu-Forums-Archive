---
title: "java problem with linux"
date: 2007-02-14
forum: Programming Talk
---

### Post by dojo on 2007-02-14
Hey all,
          Im still getting used to the linux thing but ive been able to install the java sdk 6.0 but im have a problem, I write a simple hello world program:

```
public class newt
{  
        public static void main(String args[])
        {
           System.out.println("Hello World!");
        }
}
```
After that i compiled it with the javac command,And it compiled fine

Then i typed java newt.class and the following error apeard: Exception in thread "main" java.lang.noClassDefFoundError: newt/class

i write the code in eclipse but i compiled it manualy.If anyone can help me fix this that would be cool i have a feeling i didnt install JRE right:(

---

### Post by phossal on 2007-02-14
When you launch a compiled .class file, you want to do it like this:
```
java *newt*
```
and not like:
```
java *newt.class*
```

That may not completely resolve your problem though. Manually compiling sometimes requires that you set the classpath in the compilation command. Try without the .class extension, and then let us know.

---

### Post by dojo on 2007-02-14
i just ran java newt in the terminal and alot of errors came up made me :confused: 

but when i ran java fullpath/newt.class
Exception in thread "main" java.land.NoClassDefFoundError:/home.faris/workspace/thread/newt/class

---

### Post by rko618 on 2007-02-14
did you try running it from within eclipse?  Eclipse can compile and run the programs for you so that you don't have to mess with java and javac while coding.

---

### Post by dojo on 2007-02-14
When i clicked Run Newt 
Exception in thread "main" java.lang.ClassFormatError: newt (unrecognized class file version)
   at java.lang.VMClassLoader.defineClass(libgcj.so.7)
   at java.lang.ClassLoader.defineClass(libgcj.so.7)
   at java.security.SecureClassLoader.defineClass(libgcj.so.7)
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)
came up in the error console so it dindnt run.

Im going to try to remove all java re and re install it

---

### Post by laxmanb on 2007-02-14
You haven't set your classpath!! set an environment variable to the location where u will save your programs if you will run them manually...

eclipse/netbeans do this for you when running a program...

---

### Post by ZylGadis on 2007-02-15
Do **not** use an IDE (like Eclipse or Netbeans) to compile or run this. If you don't learn the command line, you will always be dependent on IDEs to do the details for you.

Your problem is obvious, and it is definitely not the CLASSPATH variable. You have installed jdk6 from Sun somewhere, but your default Java is still gcj (which comes preinstalled with Ubuntu). Rather than tinker with update-alternatives, you can simply do

export JAVA_HOME=/full/path/to/jdk6
and then
export PATH=$PATH:/full/path/to/jdk6/bin

Now you can do javac and java from the command line. Recompile your class first, and then try to run it again.

If you do want to tinker with update-alternatives, Phossal has a guide on installing jdk6 somewhere around.

---

### Post by Tomosaur on 2007-02-15
you're using gcj. Get rid of it, and make symbolic links to Sun's java executables (or just include the jdk/bin directory in your path). GCJ is horrible and causes far too many problems.

---

### Post by dojo on 2007-02-15
I tried running the export commands i was able to compile my program by using javac newt.java 
and i tried running it by the java command but still recived erros.Ill try and remove GCJ.

Okay i removed GCJ,and recompiled the application but when i run it i still get an error:Exception in thread "main" java.lang.UnsupportedClassVersionError: newt (Unsupported major.minor version 50.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)

does it have something to do with the fact that i am compiled the aplication using jdk1.6.0 and ran it using JRE 1.4.2 maybe they arent compatible?

---

### Post by Ramses de Norre on 2007-02-15
> **dojo said:**
> does it have something to do with the fact that i am compiled the aplication using jdk1.6.0 and ran it using JRE 1.4.2 maybe they arent compatible?

Probably... Try ```
javac -source 1.4 newt.java
java newt
```
And why is javac version 1.6 and java version 1.4?? You should keep those separate...

---

### Post by dojo on 2007-02-15
Great news i compiled it with -soruce 1.4 flag and it ran fine.Then i compiled it without the -source1.4 flag and ran it with the java with the jdk6.0 bin.Thanks  Ramses de Norre  Ramses de Norre and to everyone else who helped I can stop meesng about with hello world know:D.

---

### Post by laxmanb on 2007-02-15
I definitely think it is the classpath... he's saved it somewhere where Java doesn't look in by default...

anyway... try passing the "-classpath <working directory>" option while running... see if it works...

---

### Post by davholla on 2007-02-24
I have the same problem.  I can compile but I get 
```
Exception in thread "main" java.lang.UnsupportedClassVersionError: Iloveyoli (Unsupported major.minor version 50.0
```
When I try to log at my version I get 
```
Exception in thread "main" java.lang.UnsupportedClassVersionError: Iloveyoli (Unsupported major.minor version 50.0
```

This is a free install of ubuntu (one week) and java.
My path looks a bit strange :-

```
Exception in thread "main" java.lang.UnsupportedClassVersionError: Iloveyoli (Unsupported major.minor version 50.0
```

---

### Post by davholla on 2007-02-24
Surprisingly this worked after a reboot.

---

### Post by geakMonkey on 2007-02-26
okay, I need to reread this thread for more minutia but I am having this same issue:

Exception in thread "main" java.lang.NoClassDefFoundError: org/red5/server/Standalone

when I run ./red5.sh for the Red5 ([http://osflash.org/red5](http://osflash.org/red5)). Since I am not a Java developer but admin a server, now an Ubuntu server, I would like to know what is causing this  type of error. 

Is this an error because classes need to be defined by compiling the code with javac?

Thanks

---

### Post by Ramses de Norre on 2007-02-26
```
Exception in thread "main" java.lang.NoClassDefFoundError: org/red5/server/Standalone
```

This happens when the class you're referring to: 
[LIST]
[*]has no main method (wont be the case if it's a software package you got);
[*]isn't in the specified location;
[*]is compiled with a wrong version of javac.
[/LIST]

The last one seems the most plausible here, what's the output of java -version and what's the one described in the system requirements? What's the output of echo $CLASSPATH ?

---

### Post by phossal on 2007-02-26
Those of you having problems launching red5, are you launching from the .jar file, or using a startup script something like this (red5.sh):
```
#!/bin/bash

for JAVA in "$JAVA_HOME/bin/java" "/usr/bin/java" "/usr/local/bin/java"
do
  if [ -x $JAVA ]
  then
    break
  fi
done

if [ ! -x $JAVA ]
then
  echo "Unable to locate java. Please set JAVA_HOME environment variable."
  exit
fi

exec $JAVA -Djava.security.manager -Djava.security.policy=conf/red5.policy -cp red5.jar**:conf:$CLASSPATH org.red5.server.Standalone**
```

You might consider starting your own threads (if you haven't already) on Red5, because the type of troubles you're having are typically going to be different than those of a person trying to compile and run simple classes from the command line.

---

### Post by geakMonkey on 2007-02-27
> **phossal said:**
> Those of you having problems launching red5, are you launching from the .jar file, or using a startup script something like this (red5.sh)...

You might consider starting your own threads (if you haven't already) on Red5, because the type of troubles you're having are typically going to be different than those of a person trying to compile and run simple classes from the command line.

Yes, I am using the red5.sh. Basically, you are saying that this is not about 

my@machine# red5.sh 

not finding the java paths but is a specific to compiling java?

---

### Post by geakMonkey on 2007-02-27
> **Ramses de Norre said:**
> ```
Exception in thread "main" java.lang.NoClassDefFoundError: org/red5/server/Standalone
```

The last one seems the most plausible here, what's the output of java -version and what's the one described in the system requirements? What's the output of echo $CLASSPATH ?

I am getting nothing - a blank when,

#echo $CLASSPATH

---

### Post by phossal on 2007-02-27
All of the statements about finding JAVA_HOME, echo $CLASSPATH, etc, are just the methods those of us who are trying to help you use for verifying that you have not only installed Java's JDK, but that its commands, like *java* and *javac*, can be found by your system. 

The problem I'm noticing is that even with Java installed properly, running the startup script for Red5 does not necessarily guarantee success. I get the same error. I haven't had any time to look through it more though. I downloaded the .tar.gz file and tried to run the script. That's as far as I got.

---

### Post by geakMonkey on 2007-02-27
> **phossal said:**
> All of the statements about finding JAVA_HOME, echo $CLASSPATH, etc, are just the methods those of us who are trying to help you use for verifying that you have not only installed Java's JDK, but that its commands, like *java* and *javac*, can be found by your system. 

The problem I'm noticing is that even with Java installed properly, running the startup script for Red5 does not necessarily guarantee success. I get the same error. I haven't had any time to look through it more though. I downloaded the .tar.gz file and tried to run the script. That's as far as I got.

Ok.

My issue is that I am both new to Ubuntu (been on Mandrake since '98) but mostly never dealt with Java besides a beginners class I attended while working at Borland way back. So, I I spent a lot of time installing Java 1.4 and it seemed that I had an error that was telling me that I needed Java 1.5. - I thought. So, I un/installed to Java 1.6.

I get this when I,

echo $PATH

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

I checked the net for some red5 with Ubuntu but did not see much. I need to track it more.

I should ask: How do I set the $CLASSPATH?

---

### Post by geakMonkey on 2007-02-28
BTW: I set the CLASSPATH to 

export CLASSPATH=/usr/lib/jvm/java-6-sun-1.6.0.00/bin/

and, I am still getting the same error for ./red5.sh:

Exception in thread "main" java.lang.NoClassDefFoundError: org/red5/server/Standalone

---

### Post by unwiredbrain on 2007-03-02
I installed the JRE and the JDK from _[3v1n0]("http://3v1n0.tuxfamily.org")_'s repository using his amazing *make-jpkg-mustang* Debian package.
Then I ran
```
sudo update-alternatives --config java
sudo update-alternatives --config javac
sudo update-alternatives --config javadoc
sudo update-alternatives --config javah
```
to instruct Ubuntu where to search for Java binaries and documentation.

That's it.

I don't know what's the situation for NetBeans 5.5, but unfortunately, you have to manually point Eclipse where to look for Java.

You can find more informations on _[3v1n0's website]("http://3v1n0.tuxfamily.org")_ and especially on his _[repository page]("http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/")_.

---

### Post by phossal on 2007-03-02
Interesting. What's the point of it? That's even worse than the package in backports.

---

### Post by unwiredbrain on 2007-03-02
> **phossal said:**
> That's even worse than the package in backports.
Why?

---

### Post by geakMonkey on 2007-03-05
Finally, Red5 is running. What seems to be the last issue-hurdle for me was this. When I uninstalled Java 1.4 then installed Java5 then Java6, I lost my Ant. After installing the ant today, I was able BUILD Succsesfully for the first time.

So the lesson learned - look for ant, run ant, then start red5 server using red5.sh.

---

### Post by bleers on 2007-03-06
Try to run ./red5.sh from the current directory where it's located.
It worked for me.  :-)

---

### Post by geakMonkey on 2007-03-07
> **bleers said:**
> Try to run ./red5.sh from the current directory where it's located.
It worked for me.  :-)

Hi, it does work. But is there a best location to run it from?

For instance:

/usr/loca
/var/local

???

---

### Post by bleers on 2007-03-08
allright, the location is up to you...
I prefer to have custom sources into /opt or /usr/local..
/var more means variable sized files... for example logs.

---

### Post by geakMonkey on 2007-03-09
> **bleers said:**
> allright, the location is up to you...
I prefer to have custom sources into /opt or /usr/local..
/var more means variable sized files... for example logs.

 That is the kind of answer I am seeking. I have never used /opt but I do use /usr/local. Thanks much.

---

### Post by Pedrihno on 2007-05-16
Install sun's jdk
Uninstall gcj

export JAVA_HOME=/full/path/to/jdk6
and then
export PATH=$PATH:/full/path/to/jdk6/bin

or

you can write a script to use directly the java you need:

/full/path/to/jdk6/bin/java <filename>

PW

---

### Post by lthanga on 2007-10-10
I had the same problem and had to remove the other versions of java using synaptic to resolve it.
Hope it helps.
Laguna

---

### Post by DaMaster_Architect on 2007-10-21
Hello,

I am having the same problem, but after trying to fix the problem all day using suggested fixes from this thread and other places, I still did not solve the problem.

I recently started learning to program in java, and I am currently trying out some examples from this website: 
[http://72.5.124.55/docs/books/tutorial/uiswing/components/frame.html]("http://72.5.124.55/docs/books/tutorial/uiswing/components/frame.htmlng/components/frame.html")
I am getting an error when trying to run the following java application:
[http://72.5.124.55/docs/books/tutorial/uiswing/examples/components/FrameDemoProject/src/components/FrameDemo.java]("http://72.5.124.55/docs/books/tutorial/uiswing/examples/components/FrameDemoProject/src/components/FrameDemo.java")

When I enter in console:
```
rian@inez:~/java$ javac FrameDemo.java
rian@inez:~/java$ java FrameDemo

```

..I constantly get the following error:

```

Exception in thread "main" java.lang.NoClassDefFoundError: FrameDemo (wrong name: components/FrameDemo)
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
        at java.net.URLClassLoader.access$000(URLClassLoader.java:56)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
```

and this is the part where I have no idea of how to fix it.
After a lot of search, I found out it had something to do with the classpath, if I am correct.

I tried the following:
- removing gcj
- setting JAVA_HOME, CLASSPATH, and PATH
- trying to run the application in eclipse, but gives the same error
- running and compiling with #java -cp "." FrameDemo
- relogging, rebooting (you never know)
...amongst other things, I cannot remember.

However, I have no idea what classpath exactly is, therefore I don' t understand and I don't know how to set a correct classpath.

Some extra information:
```
rian@inez:~/java$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

```

```
rian@inez:~/java$ javac -version
javac 1.6.0_03

```

```
rian@inez:~/java$ echo $CLASSPATH


```

Could someone explain to me what I am doing wrong? 
I would greatly appreciate that! :)

---

### Post by Ramses de Norre on 2007-10-21
Cd to the root folder of your app, thus the folder which should contain "components" (which seems to be the package where FrameDemo resides in) and run **java -cp . components.FrameDemo** from there.

---

### Post by DaMaster_Architect on 2007-10-21
Thanks for your fast reply, ramses!

Unfortunately, the coomand you suggested did not solve my problem entirely, although I did not get the same error as before, but a different one:

```
rian@inez:~/java$ java -cp . components.FrameDemo
Exception in thread "main" java.lang.NoClassDefFoundError: components/FrameDemo
```

However, I noticed that outcommenting "package components;" makes the application run.

I do not have any dependancies with this file, am I missing something?
Something like a file "components"?

thanks!

---

### Post by hecato on 2007-10-21
I havent touch java from a long time, also didnt read the entire thread... but from what I can remember, if you put 

```
package some;
```Inside a file, thus that 1 file should be inside a folder called some.

That mean that if you have some/file.java thus file.java would have the line "package some;"

And like I see and with reference to C (for include files), then they should be called from a directory where the paths make sense... in this case, they should be called from the parent directory, where it can find the subfolder (or child) "some".

That can be why you get the error about your "no package" or some like that IIRC.

---

### Post by hecato on 2007-10-21
try this:

> 
$ **mkdir test**
$ **cd test/**
$ **mkdir components**
$ **cd components/**
$ **wget [http://72.5.124.55/docs/books/tutorial/uiswing/examples/components/FrameDemoProject/src/components/FrameDemo.java](http://72.5.124.55/docs/books/tutorial/uiswing/examples/components/FrameDemoProject/src/components/FrameDemo.java)**
--16:28:11--  [http://72.5.124.55/docs/books/tutorial/uiswing/examples/components/FrameDemoProject/src/components/FrameDemo.java](http://72.5.124.55/docs/books/tutorial/uiswing/examples/components/FrameDemoProject/src/components/FrameDemo.java)
           => `FrameDemo.java'
Conectando a 72.5.124.55:80... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 1,097 (1.1K) [text/plain]

100%[=====================================================================================================================================>] 1,097         --.--K/s             

16:28:11 (160.04 MB/s) - `FrameDemo.java' guardado [1097/1097]

$ **javac FrameDemo.java** 
$** cd ..**
$ **java -cp $(pwd) components.FrameDemo**

Also you can use -cp . is quasi the same thing.

---

### Post by tenmillionmilesaway on 2007-10-21
hecato is correct.  if your file is in a package then it needs to be in a folder with the same name as the package.  Then to run it make sure you are in the directory with the package folder and do ```
java packagename.classname
```

As for the -cp bit i have only ever done -cp when i needed to add on a third party jar file.

In your case FrameDemo.java should be in a folder called components.

To compile cd in to components.  javac FrameDemo.java
cd .. (out of components)
java components.FrameDemo

---

