---
title: "On shutdown/restart.....it shows black screen and text."
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Rukaru on 2008-05-24
When I turn off or restart the computer on ubuntu, it shows a black screen with white text right after the desktop goes away.  I don't know what it is saying because it goes very fast.  I think it was something to do with connection. Everything still works fine, but I don't remember it ever doing this before.  It's been almost a week since I first saw it and it happens every time I restart or shut down...and I've done it a lot.  So, what is this?  Should I be worried? :confused:

---

### Post by RATM_Owns on 2008-05-24
Happens to me sometimes.
Nothing happens. You shouldn't be worried.

---

### Post by Rukaru on 2008-05-24
> **RATM_Owns said:**
> Happens to me sometimes.
Nothing happens. You shouldn't be worried.
Thanks, that makes me feel better.  So, can anyone tell me what this is and why it didn't happen before but is now?

---

### Post by Inxsible on 2008-05-24
> **Rukaru said:**
> Thanks, that makes me feel better.  So, can anyone tell me what this is and why it didn't happen before but is now? Its probably because a SIGKILL/SIGTERM was not sent to one of the running apps in time before the computer started shutting down.

Does this happen everytime now or just occasionally?

---

### Post by Rukaru on 2008-05-24
> **Inxsible said:**
> Its probably because a SIGKILL/SIGTERM was not sent to one of the running apps in time before the computer started shutting down.

Does this happen everytime now or just occasionally?

I think every time.

---

### Post by stoogiebuncho on 2008-06-04
Just wanted to jump in here and say this is happening to me every time I shutdown as well.  Ever since upgrading to 8.04.  It still shuts down fine, but it doesn't look as pretty.

I'm trying to write down what it says as it blinks on and off.  If I get anything interesting, I'll post it back here.

---

### Post by mudrain911 on 2008-07-11
Hardy is doing the same for me. I get the black background with white scrolling text, then I get a black screen for 2 or 3 seconds then the splash, then my computer shuts down.

BTW i have Xubuntu... just incase it's different for Xfce than it is for Gnome.

---

### Post by stoogiebuncho on 2008-07-12
My shutdown is working correctly now.  It wasn't anything I did, it just fixed itself after I installed one of the many batches of updates.

This is good for me, but bad in that I still have no idea what was causing it, or what fixed it.

Good luck with yours.

---

### Post by mudrain911 on 2008-07-16
Anyone have any ideas at all?

---

### Post by SteveNorman on 2008-07-16
I think its just the order in which things are shutting down. Looks like X is shutting down before some of the other Daemons. Im sure there is a way to change the order if it bothers you. With mine I beleive my NIC is what causes it. I am assuming I keep my network connection after X gdm whatever shutsdown, then the eth1 shutsdown, then the rest of the system. Mine has always done that. 

There is probably a log file that list everything going on for your start/shutdowns.

---

### Post by mudrain911 on 2008-07-16
yeah that makes sense, but why am I not getting the splash screen for the full time after that? After all the text scrolls by, it cuts off without warning... I'm a bit new to ubuntu so I don't know all about changing the order daemons and stuff.

---

### Post by SteveNorman on 2008-07-21
To be honest I am not sure. I know there is a start up-manager under system>administration. That could be the place to chose what starts up when.
   In Linux you will find there are configuration files for just about everything. I think part of the trick to controlling any distro's performance is by learning the config files and how to alter them to suit your needs. I am in the process of learning that myself. I would hate to give you advice that will hose your system, as I have done that myself a few times. 

The config files are in text format,,you basically find the one you need and open it in a text editor like vi, emacs or even gedit. You then alter the info there to meet your needs, save it and restart your desktop or computer. So the order is:

1 Find the config file you need
2 back it up so you have 2 copies of it
3 open the old copy in a text editor
4 change the file how you need
5 save and exit
6 restart the desktop or computer

If you hosed it copy the backup back to the config file and start over.

I really recommend getting a couple of good unix tutorials under your belt so you can learn how to backup, copy, create, and read files in unix/linux. I liked this one:

[http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)

There are GUI windows type things that can help you mess with the system,, but if you crash your desktop you will be working from the command line anyways, so its a good thing to know how to do. 

The thing to think of with Linux and in Unix is that the kernel is stable,,thought the desktops and front end programs may not be. The real power IMHO is in the command line, pain in the azd to learn coming from windows/mac, but it gets addictive and lets you really feel like you are controlling your computer. 

If this gets any worse,, post it again in several sections and one of the more advanced users will help. This forum is great, but I have noticed people get tied up pretty easy. Good luck!

---

