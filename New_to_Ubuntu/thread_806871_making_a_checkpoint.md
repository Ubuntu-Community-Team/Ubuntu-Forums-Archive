---
title: "making a checkpoint"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by miesnerd on 2008-05-25
I am trying out KDE4, and last time I played with widgets, things got hairy fast and I couldnt undo what I had done to get a useable desktop. 
However, I installed Kubuntu on a sepearate partition, and it is pretty and useable now.
I want to try to get the widgets working, but I am at a place where I would like to be able to undo everything and go back to if the widgets do not work.
Is there a way to declare a "checkpoint" so to speak, in the event that plasma messes up again?

---

### Post by bwhite82 on 2008-05-25
Its best to make a backup to an external drive. I am not aware of "restore points" for linux, that does not however, mean that similar software does not exist. BTW, love the use of the word "hairy" in this context. I've heard it used in Iraq but not when describing linux problems. :)

-Cheers

---

### Post by miesnerd on 2008-05-25
hairy is part of my crazy vocab. 
Ive been told by professors that I have a very "old" vocab. Im in my 20's, but I've even had papers I was asked to revise because I used outdated words such as "upon".
Nevertheless, I guess what I am looking for is something similar to Windows' "restore point". That's probably a good way of putting it.

---

### Post by Littleweseth on 2008-05-25
Offtopic :

>hairy is part of my crazy vocab.
>Ive been told by professors that I have a very "old" vocab. Im in my 20's, but I've even had papers I was asked to revise because I used outdated words such as "upon".

... your instructors consider 'upon' to be an outdated word? Wow - words like that look right at home in academic writing, at least in my opinion. NB : I'm Australian - so it's a subtly altered version of the Queen's English i got shoved down my throat. :)

Ontopic :
I haven't actually used or installed kde4, but all the data that has to do with **you** (as a user) lives in your home directory - /home/lws for me. If you do a 'ls -al ~/' in a terminal, you will see the folders you usually see in your home folder, plus a whole heap of hidden files and folders with names that start with '.', like so;

[lws@daedalus:~]$ ls -al ~/
[snip...]
drwxr-xr-x   4 lws  users     4096 2007-08-18 18:51 .java
drwx------   4 lws  users     4096 2007-05-18 18:27 .kde
-rw-------   1 lws  users      487 2008-05-10 20:13 .kderc
[...snip]

I'm assuming that plasma/kde4 config all lives in your home directory (if you don't need to sudo to configure things, this is the case.) If you want to take a 'restore point', it's as simple as : take a copy of all the hidden dot files and folders, which represent your personal config and data, and dump them somewhere else. (you can accomplish this by cp -R ~/.* ~/old-dots/ or similar.)

More practically, you can *problably* get away with just backing up the dot folders which look relevant - .kde/, .kde4/, .plasma/, etc, would look like good candidates.

Postscript : If you want to take more complete steps in case of you futzing things up, you should also consider taking a snapshot of /etc, where all your system-wide (i.e. not specific to you) configuration files live. If you really really want a complete 'system restore' style snapshot, you can mothball the entire partition into an archive  -google may know how to do this, but i don't have the specifics right now.

HTH. :)
-lws :wq

---

### Post by bwhite82 on 2008-05-25
There's flyback: [http://bernaz.wordpress.com/2008/01/19/flyback-a-time-machine-backup-utility-for-linux/](http://bernaz.wordpress.com/2008/01/19/flyback-a-time-machine-backup-utility-for-linux/)

---

### Post by phread59 on 2008-05-25
OT, hairy is a word I know well.  I'm 50 and that is a well established term.  Don't hear it much anymore.  But I've been in a few "hairy" situations before.

Mark Shuman

BTW I tried KDE 4.0, didn't like it at all.  I like 3.5 much better.  I have Fedora 9 KDE waiting to be installed on Monday.  I'm going to add 3,5 if I can I hope there will be an option at the login screen that will allow using either like Ubuntu has.  I'll see later on.

---

### Post by miesnerd on 2008-05-25
thanks.
Im checking out flyback right now.
Per the more pertinent discussion on the word "upon", the biggest issue in question was my masters thesis, and the most important rule there is to have a good thesis advisor (which I do) and then do whatever they tell you.
My advisor (and I got quite a kick out of this) went on to tell me that since I grew up in a conservative church environment, that must be why I use the word upon.
I could care less.
BTW, the widgets seem to be working so far, which leads me to think that previously, my problem wasnt with having dual monitors, it was with the xorg.conf.
When I was playing with KDE4 before, I used my twinview settings from ubuntu, and im now thinking that was the problem.
Here, I'm using my nvidia settings to have seperate X displays and so far, I seem to not have any problems.
We'll see.

---

