---
title: "I can't install this software !!!!"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by Vampiree on 2008-08-08
Hello.Ubuntu is very good OS.I have a problem in install some softwares in ubuntu.Please Help me.How do I can install these softwares :
[http://sourceforge.net/project/showfiles.php?group_id=96830](http://sourceforge.net/project/showfiles.php?group_id=96830)
[http://sourceforge.net/project/showfiles.php?group_id=69022](http://sourceforge.net/project/showfiles.php?group_id=69022)
[http://sourceforge.net/project/showfiles.php?group_id=92664](http://sourceforge.net/project/showfiles.php?group_id=92664)

:KS:popcorn::):(:guitar::lolflag::mad:

---

### Post by hyper_ch on 2008-08-08
what did you try sofar?

---

### Post by Crafty Kisses on 2008-08-08
Looks to me like you have to compile those files, have you compiled them?

---

### Post by ad_267 on 2008-08-08
How to install anything in Ubuntu: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Looks like you have to compile those so have a look at the .tar.gz source code section. Also looks like some were .jar files you can run with java.

---

### Post by Crafty Kisses on 2008-08-08
> **ad_267 said:**
> How to install anything in Ubuntu: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Looks like you have to compile those so have a look at the .tar.gz source code section. Also looks like some were .jar files you can run with java.

Yeah, make sure you have build-essentials.

```
sudo apt-get install build-essentials
```

---

### Post by Vampiree on 2008-08-08
> **Codename said:**
> Looks to me like you have to compile those files, have you compiled them?
I can't compile them.How do I can compile them ?

---

### Post by atihimself on 2008-08-08
try this page, [http://www.linuxforums.org/forum/ubuntu-help/60462-how-compile.html](http://www.linuxforums.org/forum/ubuntu-help/60462-how-compile.html)

---

### Post by Vampiree on 2008-08-09
When I type make It don't work and says : [I]make: *** No targets specified and no makefile found.  Stop.
[/I]

---

### Post by BLTicklemonster on 2008-08-09
? I thought .jar files were like java or something, lol.

Hey if you get that going, post back how you did it, that sounds like some really cool stuff!!!

---

### Post by Crafty Kisses on 2008-08-09
> **Vampiree said:**
> When I type make It don't work and says : [I]make: *** No targets specified and no makefile found.  Stop.
[/I]

Did you type in the directory?

---

### Post by Shanoes on 2008-08-09
> **Vampiree said:**
> Hello.Ubuntu is very good OS.I have a problem in install some softwares in ubuntu.Please Help me.How do I can install these softwares :
[http://sourceforge.net/project/showfiles.php?group_id=96830](http://sourceforge.net/project/showfiles.php?group_id=96830)
[http://sourceforge.net/project/showfiles.php?group_id=69022](http://sourceforge.net/project/showfiles.php?group_id=69022)
[http://sourceforge.net/project/showfiles.php?group_id=92664](http://sourceforge.net/project/showfiles.php?group_id=92664)


The first one (Lentikit) is a Java archive (".jar"). To run it you just need to have Java installed.

Click 'Add / Remove Applications' and search for 'Java', you should find an application called 'Sun Java 6 Runtime', install it.

Once you have done this you should be able to run Lentikit by right clicking on the 'lentikit-0.1.1.jar'  file and selecting 'Open with Sun Java 6 runtime'.

---

### Post by Vampiree on 2008-08-09
> **Codename said:**
> Did you type in the directory?

Yes I did.I type in the directory!!!!!
:(:(:(:(:(:
::mad::mad::mad:

---

### Post by starcannon on 2008-08-09
The links you listed are broken, please either say exactly what programs you are trying to install or fix links.

In many if not most cases, the programs your looking for are already compiled and available in:

System->Administration->Synaptic Package Manager

Always look there first, save compiling a program for your last ditch effort.

---

### Post by t0p on 2008-08-09
> **Codename said:**
> Yeah, make sure you have build-essentials.

```
sudo apt-get install build-essentials
```

Just a small point: the package is actually called **build-essential**

```
sudo apt-get install build-essential
```

---

