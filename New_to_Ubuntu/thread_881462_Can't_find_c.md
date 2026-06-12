---
title: "Can't find c:\"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by jengle3052 on 2008-08-06
Hello all. I'm very new to Linux and for the first try at it i went with Ubuntu 8.04.

I have a basic knowledge of what Linux is and why you might use it(or at least i think i do), but there are many things that I'm having a hard time with. 

I have 2 hd's and i can only find the one that ubuntu is on.

I can't get my head phones to work with skype.

And i can't get satisfactory results from wise on any games that i play, some won't start like Team Fortress 2, and others lag so much it's impossible to play like my poker program.

Is Virtual PC a option or should i just discontinue my quest and continue with what i know...Windows xp or maybe i need to go to xedona which I've been told is easier.

thanks guys

josh

---

### Post by SunnyRabbiera on 2008-08-06
In linux you do not have a C drive, instead there should be a link to your windows drive right in the menus or on your desktop unless you partitioned wrong.

---

### Post by Circus-Killer on 2008-08-06
well, where to start.
in linux, we dont have things like c: or d:. different harddrives and partitions on hard drives get *mounted* at different points in the system. for example, i have on partition for /home, and another for the rest of the system under /. bascially, each partition or disk gets mounted to a mount point, which is basically a directory. then the disk or partition can be accessed from the directory or mount point.

See [this]("http://www.tuxfiles.org/linuxhelp/mounting.html") article.

I wouldn't say you should give up. If you have to, because you desperately need your machine for serious work, then maybe, I would say yes. Or maybe suggest a dual boot. But if you not afraid of a little trial and error, then I say stick with it. You may not figure it out in a day, or even a month, but when the day comes that you feel comfortable, you'll feel free. :)

**Edit:** VirtualPC is not an option if your intention is gaming. In fact, if your intention is gaming, stick with Windows. But for everything else, try look for replacements to Windows programs rather than trying to run Windows programs non-natively.

---

### Post by jerome1232 on 2008-08-06
> **jengle3052 said:**
> 
I have 2 hd's and i can only find the one that ubuntu is on.

post the output of (is the second hard disk the one that windows is on?
```
sudo fdisk -l
```

> **jengle3052 said:**
> I can't get my head phones to work with skype.

Does sound work other than skype? skype still uses oss and plays badly with pulse audio, do a google search for 'skype ubuntu' you should find some threads that will help you configure skype.
> **jengle3052 said:**
> 
And i can't get satisfactory results from wise on any games that i play, some won't start like Team Fortress 2, and others lag so much it's impossible to play like my poker program.

Wine tries to run windows programs on linux, it isn't perfect and won't run all apps, you can find a list of apps that work with wine on their website [http://appdb.winehq.org/](http://appdb.winehq.org/) for gaming I actually just boot into windows. (it's my big toy windows xp is)
> **jengle3052 said:**
> 
Is Virtual PC a option or should i just discontinue my quest and continue with what i know...Windows xp or maybe i need to go to xedona which I've been told is easier.

thanks guys

josh

I like to run xp in virtual machine under Ubuntu for quick access to IE for those sites that don't play nice. But running Ubuntu under a virtual machine under windows may be an option for you to start learning it (gaming and compiz will definitely not work under a VM though).

Also trying various flavors of GNU/Linux is made easier inside VM's. Just to play with them and get use to how they work.

edit: I take to long, I got beat to it a couple times

---

