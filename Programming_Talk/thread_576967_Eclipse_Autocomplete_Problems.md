---
title: "Eclipse Autocomplete Problems"
date: 2007-10-15
forum: Programming Talk
---

### Post by sixblades on 2007-10-15
I don't know exactly what it's called, but in Eclipse there's a feature wherein a list of member functions/variables for a specific class or object will pop up when you type the name of one. It's an extremely handy features, and it works so well that it's one of the main reasons I use Eclipse. This function works flawlessly in the Windows version, but in the Linux build it will lag for several seconds at a time (i.e. a list box will pop up but nothing will be in it for several seconds) and sometimes this causes Eclipse to crash (this feature also has trouble with window focus or something similar as the class-editor text-box will lose focus sometimes when the list pops up). This is EXTREMELY annoying and actually slows down my programming whenever I have to use Eclipse because every time I type in a variable it gives me a list that effectively freezes all further progress for several seconds. I really don't want to do my programming on my windows partition, for obvious reasons, and I was wondering if anyone knew a work-around or solution for this (or if it's just a bug that Linux users have to deal with).

---

### Post by sixblades on 2007-10-20
*bump*

---

### Post by tenmillionmilesaway on 2007-10-21
You could try giving eclipse more memory,  You need to edit the eclipse.ini file (its in the home directory of your eclipse install).  mine has -vmargs -Xms1024m -Xmx1024m -XX:MaxPermSize 128m or something similar.  Obviously edit this for your own amount of ram.  This is not a guaranteed fix tho.  What is the spec of your machine and what does ```
java -version
``` show?

---

### Post by sixblades on 2007-10-21
Here's the result for ```
java -version
```:

```

java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

```

When I'm in Eclipse I use the "java-6-sun" JRE for running my programs, but I don't know what Eclipse itself is running off of. 

Also, what do these mean: "-vmargs -Xms1024m -Xmx1024m -XX:MaxPermSize 128m"?

System Specs:
AMD Athlon XP 3000+ [around 2.00 GHz]
1024 MB DDR333
ATI RADEON 9800 Pro /w 256 MB memory
nVidia nForce Integrated Motherboard

---

### Post by hecato on 2007-10-21
They are options to pass to eclipse in a config file (wich one, dont remember)...

This pass to me time a go, but with the C/++ extension, I have like 1GB of RAM in that time and a good processor (let me see if I find my post) o yea here it is: [http://ubuntuforums.org/showthread.php?t=477610](http://ubuntuforums.org/showthread.php?t=477610)
 like you see I have a core2duo and 2Gb of RAM and doing some code that use like base ogre3d in that time, tacked to much time even with my specs... much time mean more than 5 minutes... lol!.

My solution was to switch to netbeans C++ at less it doesnt hang.


Also I sugest that you install the java SUN version and swithc to it with update-alternatives IIRC.

---

### Post by tenmillionmilesaway on 2007-10-21
Make it use the sun java to run eclipse.  to do this: 
```
sudo update-alternatives --config java
```

and choose the sun version

this will point the java command to the sun version rather than the gcj version.

Eclipse should run better on the sun version.

Those options are what you should put into the eclipse.ini file.  They mean

-vmargs -tell eclipse to use the following in startup
 -Xms1024m -min jvm memory in megab
  -Xmx1024m -max jvm memory in megab
-XX:MaxPermSize 128m -the perm space in megab

perm sapce is somthing to do with how many objects you can have in memory afaik.

---

### Post by AZzKikR on 2007-10-22
I can confirm that Eclipse runs better using Sun's version of the JVM.

---

### Post by leden on 2009-05-06
I had the same problem, this is the solution:
[http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)

---

