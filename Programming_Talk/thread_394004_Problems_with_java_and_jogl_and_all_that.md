---
title: "Problems with java and jogl and all that"
date: 2007-03-26
forum: Programming Talk
---

### Post by pROOTy on 2007-03-26
Hi all,

Well, it'll be my 3rd week using ubuntu on my laptop. Gotta say I enjoy it!

BUT, since I'm studying Information Systems at the university, we learn how to program stuff using java. That's where the trouble comes in...

Recently we started using the awt and swing packages on windows based computers at the university using jogl to draw stuff in 3D.

Here are the packages we used in the last course :

```

import java.awt.*;

import java.awt.event.*;

import javax.media.opengl.*;

import javax.media.opengl.glu.*;

import com.sun.opengl.util.*;

```

When I try to compile my .java file on ubuntu this is the kind of message that comes up :

```
package javax.media.opengl.glu does not exist
import javax.media.opengl.glu.*;
```

So I thought I might have to install jogl on ubuntu, so I went here [https://jogl.dev.java.net/servlets/ProjectDocumentList?folderID=271&expandFolder=271&folderID=0](https://jogl.dev.java.net/servlets/ProjectDocumentList?folderID=271&expandFolder=271&folderID=0)

to download the binaries. But when I unzip that archive, the folder I get is "read only" and I can't copy the libjogl.so file into the i386 folder from java (where btw it tells me I don't have write permission to write to this directory). I then used the chmod command to give permissions, but still can't copy the file in the folder...

I have no idea of what I'm doing wrong, I've been looking all over the internet to find how I can compile this java file, so some help would be greatly appreciated :)

---

### Post by Ramses de Norre on 2007-03-26
You need to use sudo to get root privileges to write to the java dir:
```
**sudo** cp *jogl_stuff java_i386_dir*
```

---

### Post by pROOTy on 2007-03-26
Hi,

Yep, just figured that out right before ;)

So now I copied the files in their respective directories...but still can't compile...do I need to install freeglut? Because that's another thing I have tried and I couldn't get it to work either :confused: 

Thanks ;)

---

### Post by treak007 on 2007-03-26
This is a pretty good tutorial on setting up jogl:

[http://www.cs.umd.edu/~meesh/kmconroy/JOGLTutorial/](http://www.cs.umd.edu/~meesh/kmconroy/JOGLTutorial/)

---

### Post by pROOTy on 2007-03-27
Well that is the tutorial I followed (where I explained I couldn't copy the files). Now I managed to copy the files in the directories but still nothing's happening.

Could anyone give me the exact steps of what to install (and maybe how as well).

Yeah I know...n00bs can be a pain in the you-know-where :lolflag:

---

### Post by samjh on 2007-03-27
Have you remembered to add this?
```
import net.java.games.jogl.*;
```

---

### Post by iloveX on 2013-01-11
Frustatingly, instructions given in the README in [j3d-1_5_2-linux-i586.zip]("http://download.java.net/media/java3d/builds/release/1.5.2/j3d-1_5_2-linux-i586.zip") (from [http://java3d.java.net/binary-builds.html](http://java3d.java.net/binary-builds.html)) is not complete, and it does not contain the javax.media files. Get jmf-2_1_1e-alljava.zip from Oracle. Unzip at some place and copy all the /lib and /bin files to the /lib and /bin directories of your java installation respectively (e.g., /etc/java/jre1.7.0_10/lib). The jar jmf.jar contains your 'javax.media.*'. After a long search, got the clue from [http://stackoverflow.com/questions/10928024/where-to-get-java-media-package](http://stackoverflow.com/questions/10928024/where-to-get-java-media-package)

---

### Post by howefield on 2013-01-11
Old thread closed.

---

