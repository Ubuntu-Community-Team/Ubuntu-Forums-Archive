---
title: "Gnome 3 shell takes too long to shut down"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by NikS on 2011-10-09
Hi,
I have installed gnome 3 on Ubuntu 11.10 beta 2. When I shut down/log off the computer it takes a long time to actually do so. After some time, it first falls back to the default gnome theme and then it shuts down/logs off. While this is not the case in unity. The behavior was similar when I had installed gnome 3 on Ubuntu 10.04. Anyone has any idea why this happens and how to fix this?

---

### Post by LowSky on 2011-10-10
> **NikS said:**
> Hi,
I have installed gnome 3 on Ubuntu 11.10 beta 2. When I shut down/log off the computer it takes a long time to actually do so... how to fix this?

Don't use beta software if you want perfect results. Simple as that.

If shutdown is taking too long, more than likely its a process that is having a hard time being killed. What programs are you running in the background? Look at your system logs.

---

### Post by NikS on 2011-10-13
Thank you for your reply LowSky.

This happens even if I log off immediately after logging in. I have not added anything to run at startup other than conky. 

About your suggestion 'not to use beta', will upgrade to 11.10 stable now that its released, install gmone 3, try again and post back.

---

### Post by thatguruguy on 2011-10-13
> **NikS said:**
> Thank you for your reply LowSky.

This happens even if I log off immediately after logging in. I have not added anything to run at startup other than conky. 

About your suggestion 'not to use beta', will upgrade to 11.10 stable now that its released, install gmone 3, try again and post back.

I'm editing my response, because I didn't properly read your questions and issues.

Have you looked at your various logs to see if problems are being identified?

---

### Post by NikS on 2011-10-16
Have installed 11.10 stable but the issue still persists. The weird thing I still find is that the icon theme (which currently is ubuntu-mono-dark) falls back to gnome default (rest all themes I have set to default), shell freezes for some time (I can click on desktop icons etc.) and then it shuts down.

thatguruguy, thank you for your suggestion. I have installed some shell extensions, no error from them at-least.. Not sure what logs to check, can you please guide?

---

### Post by 23dornot23d on 2011-10-16
I removed ubuntuone as I do not use it  

It cured this problem a while back .....

used Synaptic

[[COLOR=Blue]**SCREENSHOT**[/COLOR]]("http://img703.imageshack.us/img703/4932/ubuntuone.jpg")

Not sure if this is the same problem now though .......  :confused:

---

### Post by NikS on 2011-10-16
thank you 23dornot23d. I do not use ubuntuone either, will be worth a try, anyways! :) Will post back after trying this.

---

### Post by NikS on 2011-10-16
Unfortunately that did not help! :(
Could not find anything interesting in syslog/messages log either.
Started killing known processes one at a time and logging out and looks like have found the culprit. Its Tomboy. Do not know why but when I kill it and then try to log out, system logs out immediately- no delay, no falling back to default theme, nothing! :)
Have removed it for now. Never used it anyway, I am a happy user of [tiddlywiki]("http://www.tiddlywiki.com/"). :D
Will try some iterations before I mark this thread as solved.

Thank you all for the help and suggestions. :)

---

### Post by 23dornot23d on 2011-10-16
Oh ok that explains it for me too

Because the other thing I removed were all the MONO packages ,,,, tomboy included in that

ok will advise that in future ty

I use Gnote to replace Tomboy as its written in C or C ++

---

