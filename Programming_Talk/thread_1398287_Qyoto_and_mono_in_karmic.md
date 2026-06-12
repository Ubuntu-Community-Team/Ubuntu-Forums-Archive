---
title: "Qyoto and mono in karmic"
date: 2010-02-04
forum: Programming Talk
---

### Post by Rizado on 2010-02-04
I'm trying to get the Qyoto bindings to work with mono in Kubuntu Karmic. It's not going too well... I've installed everything with qyoto and kimono in it's name from the repos but I can't figure out how to use them. As soon as I try "using Qyoto" I get: ```
error CS0246: The type or namespace name `Qyoto' could not be found. Are you missing a using directive or an assembly reference?
```
I've been trying out the qyoto-tutorials in /usr/share/qyoto-examples/tutorial but they won't compile. 

How do I make the monocompiler actually find the namespaces? I mean, just placing some files anywhere on the drive won't necessarily make csc find it. Do I miss some packages? I'm pretty new to mono and C# but there has to be something similar to classpath in java right? I can't seem to find anything at all on the subject but I figure there should be a simple solution, maybe it's just too simple :o

---

### Post by Rizado on 2011-01-19
So about a year later I have decided to give qyoto (and mono) another try. Monodevelop seem to be a joy to work with now :) Feels really fast and solid.

Anyway, the problem is solved very easily by rightclicking References under the project name in the left panel and selecting edit references. qt-dotnet needs to be selected :) I just thought I'd add this here in case someone else stumbles on the same problem, as I couldn't find any answers on google.

Here's a pretty nice tutorial: [http://zetcode.com/tutorials/qyotosharptutorial/introduction/](http://zetcode.com/tutorials/qyotosharptutorial/introduction/)

---

