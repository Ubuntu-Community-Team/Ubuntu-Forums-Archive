---
title: "[SOLVED] Geany, Java, and JDOM - package org.jdom does not exist"
date: 2008-03-14
forum: Programming Talk
---

### Post by oni5115 on 2008-03-14
As the title mentioned, I cannot seem to get Geany to find JDOM.  When I try to compile my code it points me to the line:
```

import org.jdom.*;

```
and tells me package org.jdom does not exist.


I've downloaded JDOM, built it, and got the jdom.jar file.  I've put that in /usr/local/share/java/j   (where I intend to put any other libraries like that if I need them for something.)

I've modified my .bashrc to include the CLASSPATH.

Running env outputs a lot of stuff, including:
CLASSPATH=.:/usr/local/share/java/jdom.jar

running echo $CLASSPATH outputs:
.:/usr/local/share/java/jdom.jar

If I open a terminal in the directory with my java file, I can successfully compile it using javac <name>.java   just fine.

Any ideas on how to make Geany compile the code?  Is there something special I have to do in Geany to get it to recognize the location of the jdom.jar?

---

### Post by ZylGadis on 2008-03-14
You are aware that .bashrc is a configuration file for bash, right? Anything you put inside is only valid for a bash session. I would assume Geany does not start bash to use javac, and invokes javac directly instead. Try tinkering with Geany's options, it should allow you to specify a classpath somewhere if it is any good (I have no experience with it). If it does not, you can always pass the classpath as an option to javac.

---

### Post by mssever on 2008-03-14
Another option is /etc/profile. Stuff set there applies to the entire session (of every user on your machine, which might not be what you want). You have to log out and back in for the changes to take effect.

---

### Post by oni5115 on 2008-03-14
About the .bashrc, good to know.  I've never really done all that much with shell scripting or configuration.  I had a post that mentioned to add a for loop to load all the jars to the .bashrc, which did make it work for the command line.  (At least it got me half way there!).

As for being able to set the class path, I'm not sure.  I haven't really found that as an option anywhere in Geany 0.11.  Though I do have access to the compile commands, so I likely could have done that as well.

Putting it into the /etc/profile worked just fine.  (I'm really the only user of the machine at this point, so it doesn't matter).  Thanks!

---

### Post by oni5115 on 2008-03-16
I just wanted to add a bit more as well.  After doing some reading into Java's extension mechanism, I found yet another way to make this work, and probably the most 'official' way.

That is, to add the jar to your JRE's /ext directory.  
Normally this can be found under: 
/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/ext


Note: This was actually the first thing I tried, but I got the wrong directory. 
/usr/lib/jvm/java-6-sun-1.6.0.03/ext

I've copied it to both directories to be absolutely certain it works for both compilation and execution and now it works even without it being in my classpath variable.


Just thought I'd post this solution as well, in case anyone else does the same thing I did and completely misses where the ext directory is in Linux.

---

### Post by DenKain on 2008-04-10
I thought it would be best for me to post my issue in this thread since it is almost exactly my issue. I do not use Geany though whatever that is. I installed JDom through the Synaptic Package Manager (libjdom1-java). I then restarted the machine and tried to import org.jdom.* and was told that it does not exist by Netbeans 6.0. My question is where does Ubuntu store jdom and how do I call it?

---

### Post by mssever on 2008-04-11
> **DenKain said:**
> I thought it would be best for me to post my issue in this thread since it is almost exactly my issue.Generally, it's best to post separate questions in separate threads. Include a link if appropriate.

> I do not use Geany though whatever that is. I installed JDom through the Synaptic Package Manager (libjdom1-java). I then restarted the machine and tried to import org.jdom.* and was told that it does not exist by Netbeans 6.0. My question is where does Ubuntu store jdom and how do I call it?

Geany is an IDE.

If you look in Synaptic, you'll see a listing of the files installed by a particular package. The only time I tried netbeans, I had to get it through a website, not the package manager, which means that you might have to tell it where Ubuntu keeps its files. I'm no Netbeans expert, nor am I a Java programmer, so I can't tell you much more.

---

### Post by oni5115 on 2008-04-24
I'm not sure actually, I had downloaded JDom from the website and compiled it myself, didn't realize it was in the repositories :lolflag:

So I had the jdom.jar file after the compiling finished and could copy it wherever I needed too.

---

### Post by a9bejo on 2008-04-24
> **oni5115 said:**
> 
That is, to add the jar to your JRE's /ext directory.  


It is **bad practice** to do this. You are polluting the global classpath with third party libraries this way, and this can lead to problems. For example, if you have another program that uses a library in a different version.  Or if you ship software with too many/less dependencies than necessary.

Instead, always set the classpath **explicitly** for your program using the interpreters -classpath option . Depending on what you are doing, there are many options on what level you want to do this: A local shell script that calls the interpreter, a setting in your IDE, an (executable) [jar](http://java.sun.com/docs/books/tutorial/deployment/jar/downman.html) file with the classpath set in a manifest file, an observed directory within a j2ee container.  

Have a look at [Ant](http://ant.apache.org/) (for smaller projects) and [Maven](http://maven.apache.org/) (for larger, team based scopes).

---

