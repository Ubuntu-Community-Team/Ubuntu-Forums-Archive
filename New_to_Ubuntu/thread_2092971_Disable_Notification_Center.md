---
title: "Disable Notification Center"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by cheatos on 2012-12-09
Hi all,

I think theres a million posts up here, but somehow the ones I checked don't quite cut it.

I really want to disable that annoying notification center.
I already disabled the notification daemon in the startup application as can be seen in the attached picture, but the notifications still keep coming up :(

Does anyone have a better idea or can this stupid feature be removed?
I tried removing notifiacation center but then apt-get told me it will remove my complete desktop environment so I rejected the removal but maybe there is a way to get rid of it.

Thanks for your help!

---

### Post by ohnonot on 2012-12-12
i managed to uninstall it and no problem.

does apt-get want to uninstall all other desktop packages or just 1 package called lubuntu-desktop? if it's the latter, it might be a meta package which is "safe to remove".

i think there's command line utilities that un/indstall packages without checking dependencies, like dpkg?

also, i think there's several apps for notifications and some other apps might even have their own. 
i think openbox has its own. but searching "notification" in synaptic should give you all the info without saying "i think" all the time.

---

### Post by nishant1234 on 2012-12-12
its not working may be I am wrong please write the exact as it is written on console

---

### Post by ohnonot on 2012-12-12
ok, my answer wasn't very clear maybe.

tell me exactly what you want to do and i'l tell you exactly what the command line is.

---

### Post by cheatos on 2012-12-12
So what I wnat to do is remove the notfication center popups such as wireless enabled or wireless connected and such.

Its the pop-ups in the upper right corner of the screen. It also tells me when my Dropbox has new files and stuff, but I really don't need it and it keeps popping up and I want to remove it.

So, when I try to uninstall notification by the following I receive this:

```

michael@MichaelsPC:~$ sudo apt-get remove notification-daemon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  blueman lubuntu-desktop notification-daemon update-notifier
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 3,041 kB disk space will be freed.
Do you want to continue [Y/n]? 

```

Its really just the lubuntu-desktop package but I am unsure about removing this especially as the update-notifier is also part of the packages removed...
By the way, what is blueman? never used it i suppose.

---

### Post by rburkartjo on 2012-12-12
yup it is part of the lubuntu desktop so if you try to uninstall it you will remove lubuntu.

---

### Post by kalehrl on 2012-12-12
It will not remove Lubuntu so just go ahead and uninstall it.
[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveLubuntuDesktop](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveLubuntuDesktop)

---

### Post by cheatos on 2012-12-13
Well ok, I'll try it then, but did I understand the wiki page correctly that when upgrading I will have to install it again?

---

### Post by kalehrl on 2012-12-13
No, it is just a list of available packages, nothing else.

---

### Post by ohnonot on 2012-12-14
just confirming what kalehrl says. the link he's given says it all.

blueman is a bluetooth manager, not sure what it does but my bet is that there's plenty of other ways to use bluetooth.

update notifier does nothing without notification daemon so it's ok to remove it.

if it worked please mark thread solved.

---

### Post by cheatos on 2012-12-16
So I removed it and it works, now when I download stuff there's no notification about finished downloads, thanks for all your input :D

I'm marking this as solved now.

---

