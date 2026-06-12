---
title: "Recursive javadoc?"
date: 2010-07-13
forum: Programming Talk
---

### Post by fiddler616 on 2010-07-13
Hello,

I have a directory full of directories full of directories of Java files, and I was wondering how to generate the javadoc for all of them at once. Thanks in advance.

---

### Post by PaulM1985 on 2010-07-13
I think Netbeans has support for this.  You could import all of you files into Netbeans and use the utility in there.  (Not sure about recursive importing of files tho :confused: )

Paul

---

### Post by fiddler616 on 2010-07-13
> **PaulM1985 said:**
> I think Netbeans has support for this.  You could import all of you files into Netbeans and use the utility in there.  (Not sure about recursive importing of files tho :confused: )

Paul

I guess that's a good Plan B, but I'd like to avoid installing and using Netbeans if I don't have to.

All I mean by "recursive" is that it will act in all subdirectories of a parent directory. In the folder src, there are are a bunch of folders: visualizer, UIcomponents, etc. In each of those folders, there are a bunch of Java files. I can't run "javadoc -private src", because it will look for Java files in src, and won't find them. Instead it'll just find two folders. 

Hopefully that cleared things up :P

---

### Post by PaulM1985 on 2010-07-13
I don't know anything about bash, but after a little bit of googling...

Maybe a script like this would work:

```
javadoc -private `find -name *java`
```

Paul

---

### Post by CptPicard on 2010-07-13
Well, those directories are Java *packages* of course (you've worked with them right, real basic stuff?)... 

[http://download.oracle.com/docs/cd/E17476_01/javase/1.4.2/docs/tooldocs/windows/javadoc.html#processingofsourcefiles](http://download.oracle.com/docs/cd/E17476_01/javase/1.4.2/docs/tooldocs/windows/javadoc.html#processingofsourcefiles)

And lots of stuff at Google from "using javadoc".

---

### Post by Reiger on 2010-07-13
Well if you have Ant the easiest thing to do is create (or update) a little ant script to contain a “target” for building Javadoc. It's fairly straightforward: 
```

<target name="javadoc" description="Build Javadoc from Java source files">
  <javadoc destdir="build/javadoc/">
    <fileset includes="**/.java" dir="src"/>
  </javadoc>
</target>

``` It just needs some more configuration attributes on the javadoc tag to make it work nicely, for which see the Ant documentation/manuals.

---

