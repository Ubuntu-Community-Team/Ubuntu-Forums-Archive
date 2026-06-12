---
title: "Rolling-release OS's."
date: 2007-09-29
forum: Other OS Talk
---

### Post by kellemes on 2007-09-29
I'd like to know which rolling-release OS's there currently are..

The ones I know of are..
Gentoo
Arch
FreeBSD
Debian
Foresight

Are there any more?

---

### Post by afonic on 2007-09-29
Sidux (based on Debian)

---

### Post by kellemes on 2007-09-29
> **afonic said:**
> Sidux (based on Debian)

Yes, I know.. it **is** Debian-Sid basically..
Also I heard MEPIS is going to implement the rolling-system, not sure though..

---

### Post by floke on 2007-09-29
I can heartily recommend Arch - though a bit tricky to set up (at least for me!)

---

### Post by ynnhoj on 2007-09-29
i think sourcemage/sorcerer/lunar all follow a rolling release..?  i'm not *certain*, though.. i could be wrong.

---

### Post by Antman on 2007-09-30
> **afonic said:**
> Sidux (based on Debian)

Yes, Sidux is AWESOME. I now run it on two machines as my main OS (one is a dual boot with WinXP). :guitar:

---

### Post by .aku on 2007-10-01
Frugalware, if you follow "-current" when updating..
 
Myself I'm running Zenwalk 'snapshot', which is also a rolling-release, basically..
I haven't had any bad breakage with snapshot, and it's easy to set up (for example from 4.8RC).
Just add the snapshot repo to your /etc/netpkg.conf, select the newly created snapshot mirror with "netpkg mirror", and "netpkg upgrade" away!

---

### Post by kellemes on 2007-10-01
> **.aku said:**
> Frugalware, if you follow "-current" when updating..
 
Myself I'm running Zenwalk 'snapshot', which is also a rolling-release, basically..
I haven't had any bad breakage with snapshot, and it's easy to set up (for example from 4.8RC).
Just add the snapshot repo to your /etc/netpkg.conf, select the newly created snapshot mirror with "netpkg mirror", and "netpkg upgrade" away!

Man, you bring me great news..
Frugalware has been on my want-to-try-hotlist for some time now.
Since a day or 2 I've been running Zenwalk on one of my testmachines and didn't know this was possible, I'm very much positively surprised by Zenwalk, in terms of speed, support and ease of setup so being able to "roll" would be great.

---

### Post by .aku on 2007-10-01
> **kellemes said:**
> Man, you bring me great news..
Frugalware has been on my want-to-try-hotlist for some time now.
Since a day or 2 I've been running Zenwalk on one of my testmachines and didn't know this was possible, I'm very much positively surprised by Zenwalk, in terms of speed, support and ease of setup so being able to "roll" would be great.
 
Yeah, FW is good, but I've had some segfault issues with Frugalware installer earlier, and the latest prerelease installer gives me a 'package list not found' error after selecting the packages to install.. 
 
Zenwalk has been my favourite, number 1 distro, for a long time now..
If you want stability, use the current repo, but if you're like me, and want bleeding-edge everything, then use ZW snapshot..
Select the mirror you like (I use zen-repo.meticul.eu)
then, as root:
```
vim /etc/netpkg.conf
```
 
add "Internet_mirror = [http://zen-repo.meticul.eu/](http://zen-repo.meticul.eu/)i486/snapshot" to the mirrors section in the file.
 
Save the file, then select the new snapshot mirror with
```
netpkg mirror
```
 
and select the one you created.
 
Then,
upgrade the whole system:
```
netpkg upgrade
```
 
Now you're running Zenwalk 'snapshot' 
:guitar:

---

### Post by kellemes on 2007-10-01
Thanks for the info..
Zenwalk is upgrading to snapshot at the moment.

So you're always using snapshot? Do you know at what moments these snapshots are taken? Ones a day or week?
And you have an acceptable stable system also?

I don' t really need to be bleeding edge but I just hate having to install my OS because they upgraded some packages.. that's why I'm a sucker for rolling.
I am very happy with Arch but always on the lookout for better.. :popcorn:

---

### Post by .aku on 2007-10-01
> **kellemes said:**
> Thanks for the info..
Zenwalk is upgrading to snapshot at the moment.

So you're always using snapshot? Do you know at what moments these snapshots are taken? Ones a day or week?
And you have an acceptable stable system also?

I don' t really need to be bleeding edge but I just hate having to install my OS because they upgraded some packages.. that's why I'm a sucker for rolling.
I am very happy with Arch but always on the lookout for better.. :popcorn:

Yeah, I'm running ZW snapshot all the time.
They upgrade their snapshot repo almost daily, basically every time there is a new package or a patch, bugfix or something like that available.

I netpkg upgrade every day (on the test machine), and haven't had any bad breakage, in fact, I think I haven't had anything worth mentioning in the last 2 months..

So even ZW snapshot is quite stable, but still the packages are fresh!

:)

---

### Post by .aku on 2007-10-01
EDIT: Double post.

---

### Post by Rumor on 2007-10-01
A couple lesser known rolling release distros:

**Lunar** (mentioned earlier): [http://www.lunar-linux.org/](http://www.lunar-linux.org/)
From the "About" page:
> Updating lunar is a matter of one single command, lunar update. It fetches an updated moonbase, checks if there were any updated modules and builds those. The AMS is network aware and uses the network to acquire source code. The moonbase and core tools are updated every hour at Lunar-Linux.org.

**Paldo**: [http://www.paldo.org/](http://www.paldo.org/)
From the "About" page:
> What is paldo?

paldo is a Upkg driven GNU/Linux distribution. It's kind of a mix of a source and a binary distribution. Even though it builds packages like a source distribution it provides binary packages.

paldo stands for "pure adaptable linux distribution" and we try to accomplish this in every package. paldo comes with very few patches against its packages. We have virtually no local changes, means every patch is one which will go upstream anyway (e.g. compile fixes) or one needed by the LFS build system to enable us to boostrap correctly. It's very easy to make changes to the distro. You can change every package by providing a local version of the sources and specifications you've changed. You can even configure your system automatically through local differencial repositories (see My paldo). The whole distribution is very flexible because it's built on top of Upkg.

paldo wants to be a distribution according to the "just-works" principle. It tries to configure automatically as much as possible without user intervention. paldo is task-oriented, means, that we won't provide several programs to do one and the same task, we will select the program which we think does this task best, and include it into paldo. paldo aims to support cutting-edge technologies. It is pure NPTL based (no linuxthreads support) and therefore does not work with a Linux kernel older than 2.6.x.

Since paldo is task oriented we also have only one desktop environment, the GNOME desktop environment.

paldo does not split packages, means, all development files will be installed if you install a library. All files you need around a package will be available as soon as it is installed.

paldo only supports the x86 architecture at the moment and we do not plan to extend that much (except of the x86_64 platform). It is a _very_ popular arch making us the life very easy.

So what are the core points?

    * simplicity
    * purity - packages are only modified if they are broken in new environments
    * cutting-edge - only newest technologies gain entrance into paldo
    * binaries, although it is a source distribution
    * it's compact - all packages are installed as a whole
    * LSB and FHS compliance (we don't mean to install a LSB compliant RPM into paldo and we're not planning to add that for good reasons)



---

### Post by Antman on 2007-10-16
Wow, I'm glad I found this thread again (I completely forgot about it). I was just going to post asking about various rolling release distros. :guitar:

---

### Post by Caraibes on 2008-04-11
Nice thread... 

My feeling is that the king of rolling release is still DebianTesting...
I run it on i386, amd64 & PPC :)

I still favor Debian Stable for "entreprise ready" PC's...

...But Testing is much more fun ;)

---

### Post by Twitch6000 on 2008-04-11
PClinuxOS is another rolling release :).

---

### Post by cardinals_fan on 2008-04-11
> **.aku said:**
> Yeah, I'm running ZW snapshot all the time.
They upgrade their snapshot repo almost daily, basically every time there is a new package or a patch, bugfix or something like that available.

I netpkg upgrade every day (on the test machine), and haven't had any bad breakage, in fact, I think I haven't had anything worth mentioning in the last 2 months..

So even ZW snapshot is quite stable, but still the packages are fresh!

:)
I run Snapshot too - and it is awesome.  I have never had major breakage.  Rolling release is the only way to go, whenever I use my Ubuntu partition I always try to 'netpkg upgrade' :)

---

### Post by LunaMouse on 2008-08-05
I know this thread is old, but I love Arch so much that I just had to say so. ;D And I didn't find it hard to set up at all! It's almost like a binary Gentoo, but it's not *that* complicated.

---

### Post by mips on 2008-08-05
> **kellemes said:**
> 
FreeBSD



FreeBSD?

---

### Post by cardinals_fan on 2008-08-05
> **mips said:**
> FreeBSD?
Current is rolling ;)

---

### Post by mips on 2008-08-06
> **cardinals_fan said:**
> Current is rolling ;)

lol, I suppose you could put it that way.

---

