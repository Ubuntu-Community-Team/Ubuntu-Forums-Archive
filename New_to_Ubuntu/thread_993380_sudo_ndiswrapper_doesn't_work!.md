---
title: "sudo ndiswrapper doesn't work!"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by E-man96 on 2008-11-25
I was following this manual [HOWTO for Dell (E1505 Wireless)]("http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+inspiron+1501"). I tried to do the command on step 4
[FONT="Lucida Sans Unicode"]sudo ndiswrapper -i bcmw15.inf[/FONT]
and it says
[FONT="Lucida Sans Unicode"]couldn't open bcmw15.inf: No such file or directory at /usr/sbin/ndiswrapper line 219.[/FONT]
Why isn't it working?

---

### Post by bobnutfield on 2008-11-25
Are you running the command from inside the directory where the .inf file is located?  You will get this error if you run it in a different directory.  Also, if you are running Intrepid 8.10, you might want to make sure that there is not native support for the Broadcom chipset you are using.  The 2.6.27 kernel GREATLY improbed wifi support

---

### Post by E-man96 on 2008-11-25
yeah, my directories are right.

---

### Post by bobnutfield on 2008-11-25
What do you get when you type:

> sudo ndiswrapper -l

---

### Post by E-man96 on 2008-11-25
my internet is only on xp.

---

### Post by bobnutfield on 2008-11-25
Well, the tutorial that you posted is a valid one and the instruction will work on the versions of Ubuntu listed.  If you have ndiswrapper properly installed, make sure you have the .inf file and the correct .sys file in your working directory, I see no reason for it not to work.  There is a GUI frontend to ndiswrapper which may make it easier for you.  It is in the repos and it is called ndisgtk.  Install it, then just point the installer to the directory where your .inf and .sys files are located.

But, as I mentioned in my first post, I believe that your chipset is natively supported in 8.10 and you would not need ndiswrapper.  Just something to consider, unless you cannot or do not want to upgrade.

---

### Post by E-man96 on 2008-11-25
your talking about dell wireless wlan card 1390 right?

---

