---
title: "kernel programming using ubuntu"
date: 2009-09-12
forum: Programming Talk
---

### Post by orrorin on 2009-09-12
Hello,

I'm a linux kernel newbie and want to "play/dig deeper" into the linux kernel. I want to do this using Ubuntu (9.04 x86).

To be able to do this, I'd like to use the same kernel repository (pref.. svn) as the one that is being used by Ubuntu. I ofcourse won't be checking in any code into that repository. Can some one give me some pointers on how to go about doing this?

---

### Post by hal10000 on 2009-09-12
just install the kernel source package:
[COLOR="Red"]sudo apt-get install linux-source[/COLOR] 
Thus you'll get always the same kernel-source as the currenty installed ubuntu-kernel.

Now move into the directory /usr/src .You will see a file called linux-source-2.6.28.tar.bz2
This is a zipped file. You can extract it with
[COLOR="Red"]cd /usr/src && sudo tar -xvjf linux-source-2.6.28.tar.bz2[/COLOR] in a terminal window
Now you have the linux-source code in the directory /usr/src/linux-source-2.6.28

If you want to compile your own kernel, take a look at the Master Kernel Thread: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

But if it comes to point 4 (downloading the kernel sources from kernel.org), skip this point if you want the same kernel sources as your currently installed ubuntu, because if you download this source, you will get the sources from kernel.org, which does'nt have the ubuntu-patches

---

### Post by jpkotta on 2009-09-12
[https://wiki.ubuntu.com/KernelTeam/KernelGitGuide](https://wiki.ubuntu.com/KernelTeam/KernelGitGuide)

But I would just use the linux-source package.  Also, read [http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/).

---

### Post by moma on 2009-09-12
Hello,
See also these kernel notes
[http://www.futuredesktop.org/kernel.html](http://www.futuredesktop.org/kernel.html)

ps. do not forget [Android...]("http://www.futuredesktop.org/developing_android_apps_on_ubuntu.html")

---

### Post by soltanis on 2009-09-12
Bear in mind that Linus Torvalds hates svn (and cvs); they use git.

---

### Post by orrorin on 2009-09-14
Thanks everyone for all the pointers. They all look very useful to me. Also, I hope it is ok to post occasional questions about the kernel on this forum.

---

### Post by tatrefthekiller on 2009-09-17
You can read Linux Device Drivers (free book) to learn about module programming.

---

