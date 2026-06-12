---
title: "adb or ./adb"
date: 2015-07-23
forum: New to Ubuntu
---

### Post by flex567 on 2015-07-23
I noticed that sometimes I run adb in terminal and sometimes ./adb (on different machines).  What is the difference?

---

### Post by grahammechanical on 2015-07-23
My guess? On one machine adb is already on the system path. On the other machine it is not. The difference could be in how you installed Android Debug Bridge on each machine.

[http://wiki.cyanogenmod.org/w/Doc:_adb_intro](http://wiki.cyanogenmod.org/w/Doc:_adb_intro)

Regards

---

### Post by flex567 on 2015-07-24
how can I see if the program is already at the system path and how can I add a program? 

If i install Android Studio did I automatically install adb also?

---

### Post by Lars Noodén on 2015-07-24
It's almost certainly the path.  Try comparing them on the different machines:

```

echo $PATH

```

You can add a program's directory to the $PATH by appending the $PATH variable itself.

---

### Post by flex567 on 2015-07-24
```
:~/Desktop$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
```

what does this mean?
It looks like adb isn't at the system path?

---

### Post by Lars Noodén on 2015-07-24
It means that if you type in a program name without a path the shell will look for it first in /usr/local/sbin/ and if it is not there then it looks in /usr/local/bin/ and then /usr/sbin/ and so on.  The variable $PATH only contains directories and each directory could contain thousands of programs or none at all.  

You can find which directory adb is in, if it is in one of the $PATH directories, using [which](http://manpages.ubuntu.com/manpages/trusty/en/man1/which.1.html)

```

which adb

```

If it is not in any of the $PATH directories, then it will say so.

---

### Post by flex567 on 2015-07-24
```
desktop:~$ which adb
/usr/bin/adb


```

so that means that adb is in /usr/bin/adb directory?
how can this be? 
I know that adb is not in /usr/bin/adb becuse adb is in /home/user/Android/Sdk/platform-tools

---

### Post by Lars Noodén on 2015-07-24
Close.  There is an adb in the /usr/bin/ directory.   If there is also a second one in /home/user/Android/Sdk/platform-tools/ then you can try looking at the two with more detail:

```

stat /usr/bin/adb
stat /home/user/Android/Sdk/platform-tools/adb

```

But given the content of $PATH, only the one in /usr/bin gets used if you just type 'adb'

---

### Post by flex567 on 2015-07-24
```
desktop:~$ stat /home/user/Android/Sdk/platform-tools/adb
stat: cannot stat ‘/home/user/Android/Sdk/platform-tools/adb’: No such file or directory


```

why do I get this response even though I know that adb is in that directory ?

---

### Post by Lars Noodén on 2015-07-24
Can you see the file with ls?  If it is there, stat should find it.  If it is not there, then stat will complain.

---

### Post by flex567 on 2015-07-24
```
desktop:~/Android/Sdk/platform-tools$ ls
adb  dmtracedump  fastboot    NOTICE.txt         sqlite3
api  etc1tool     hprof-conv  source.properties  systrace
```

---

### Post by flex567 on 2015-07-24
> **flex567 said:**
> ```
desktop:~$ stat /home/user/Android/Sdk/platform-tools/adb
stat: cannot stat &#8216;/home/user/Android/Sdk/platform-tools/adb&#8217;: No such file or directory


```

why do I get this response even though I know that adb is in that directory ?

I figured out what was the problem: cannot stat &#8216;/home/_**user**_/Android/Sdk/platform-tools/adb&#8217;: No such file or directory

---

### Post by flex567 on 2015-07-24
why are there 2 adb programs instead of one

---

### Post by Lars Noodén on 2015-07-24
Somehow you installed two.  There is one in the package 'android-tools-adb' that puts the file [/usr/bin/adb](http://packages.ubuntu.com/trusty/i386/android-tools-adb/filelist) on your system.  The normal way to do that is with the Software Center, Synaptic or APT (all more or less front-ends for the same thing) and it goes automatically.  However, if you also tried to install manually, from a tarball or something, then you will have a second copy wherever that manual process put  it.

---

### Post by flex567 on 2015-07-27
what does this symbol mean? ```
./
```

---

### Post by Lars Noodén on 2015-07-27
It's the path. If you write /usr/bin/adb, then it is adb which is in the directory /usr/bin/   If you write ./adb then it is the adb which is in the current directory.  The shortcut for the current working directory is a dot (.) and the shortcut for the directory immediately above it is two dots (..)

---

