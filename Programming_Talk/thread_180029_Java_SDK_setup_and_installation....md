---
title: "Java SDK setup and installation..."
date: 2006-05-21
forum: Programming Talk
---

### Post by encompass on 2006-05-21
I have learned java this last year in school and would like to begin programming on my own with it this summer to further improve my programming skills.  I have experience in C and perl but can't seem to figure out the way that java likes to compiles its code.

I have got both the jdk and java runtime installed in my /opt/ directory.  I can compile the .java files with javac however, can't run them because it give me this error...
> jason@lappy:/opt/j2sdk1.4.2_11/bin$ ./java /home/jason/PROGRAMMING/java/myfirstjavaprog.class
Exception in thread "main" java.lang.NoClassDefFoundError: /home/jason/PROGRAMMING/java/myfirstjavaprog/class
jason@lappy:/opt/j2sdk1.4.2_11/bin$
as I don't want to lose what little java I know so far... can anyone help me get this setup right...
I am still so knew I use the keyboard class.  But that is for another day.
I also am trying to avoid eclipse as I love good ol nano on my 200mb ram lappy.

---

### Post by thumper on 2006-05-21
You are running java from /opt/j2sdk1.4.2_11/bin
The default CLASSPATH does not know the location of /home/jason/PROGRAMMING/java/myfirstjavaprog.class

That is what the error is from.

Post back what the default CLASSPATH is.

I'm not entirely certain as I haven't touched java for some time.

---

### Post by encompass on 2006-05-22
I am sorry, but I don't know how to get that information.  is it a variable somewhere?
Thanks for the help so far...
export CLASSPATH=(WHAT)
and could you explain if possible why it has to be set?

---

### Post by thumper on 2006-05-22
Unless you have set one it is likely to be empty (like mine is)
```
tim@spike:~/sandbox/prog$ echo $CLASSPATH

tim@spike:~/sandbox/prog$ env | grep CLASS
tim@spike:~/sandbox/prog$ 

```
There's two ways...

What package is your class in?

---

### Post by encompass on 2006-05-23
Class path... coudl you tell me what that is and what it is for?  how do I set that up?
something to do with export CLASSPATH... but that do I set it at...
I set it to the dir where my class was but it still didn't work

---

### Post by thumper on 2006-05-23
The CLASSPATH is used by the JAVA runtime to find classes (surprise :) )

The CLASSPATH should contain either directories or jar files.

Lets say you have a class called Foo in package bar.  The directory layout should look like
```

src-dir/
src-dir/bar
src-dir/bar/Foo.java
src-dir/bar/Foo.class  # assuming that it is in the same location

```
Note: this is not the way to do it, but illustrates a point.
In this situation the src-dir should be in the CLASSPATH, or set on the command line for java
```
$ java --classpath /full/path/to/src-dir bar.Foo
```

Note: learn [ant](http://ant.apache.org)

---

### Post by encompass on 2006-05-27
Hate to saw it... but java was too hard to set up for my simple programming mind...
I have started to learn python and am loving it... I love how powerful it is.  Sorry to take all your time just to move to something else.

---

### Post by jvictor on 2006-05-27
Well Java is not a tuff language.. IMHO.. yes it suits a set of problems , whereas python suits a different set of problems. So comparing bwn Java/Python/C may not be a good Idea.

---

### Post by gekkio on 2006-06-12
If you haven't abandoned Java yet, here's the solution:

First of all, I recommend you to get the Sun Java JDK package:
```
sudo apt-get install sun-java5-jdk
```
(it's in multiverse, so you might need to edit your /etc/apt/sources.list to include multiverse repos)

After installing it, you'll have the necessary java tools in your PATH, which greatly simplifies working with Java.
Then you can do
```
cd /home/jason/PROGRAMMING/java/
java myfirstjavaprog
```
**Note that the .class extension is not used when calling java**. You are supposed to only give the name of your class.
(This is the actual problem you had. Don't worry, you're not the first one to make this mistake. :p )
You actually tried to call class called class in package myfirstjavaprog, which would look like this (doesn't really work, because AFAIK you can't use the keyword 'class' as a class name) :
```
package myfirstjavaprog;

public class class{
}
```
Oh, and if you want to call java from /opt (instead of using the sun-java5-jdk package), you should do
```
./java -cp /home/jason/PROGRAMMING/java myfirstjavaprog
```
instead. -cp specifies the classpath(s) you want to use (and myfirstjavaprog is without .class).

---

