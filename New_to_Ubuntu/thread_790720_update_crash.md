---
title: "update crash"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by astathios on 2008-05-11
hello,
i was trying to upgrade from 7.10 to 8.04,
evrything ws running perfect but at the end the upgrade gave me an error and it stopped,im afraid to restart cause of a possible crash.is any i can do to check or retrieve the upgrade?
any help plz
thank you

---

### Post by Joeb454 on 2008-05-11
What was the error?

---

### Post by astathios on 2008-05-11
was durring the initramfs update and i think it was about virtuall box
or something like that, 
thank you

---

### Post by astathios on 2008-05-11
bump

---

### Post by nynoah on 2008-05-11
open your terminal and run this

sudo dpkg --configure -a

let the system configure all unconfigured packages and then retry update manager or retry installing.

Part of the problem you are having and a lot of other peopleare  having concerning ugrading, is people are running programs that are not from Canonical or synaptic.  So when you upgrade, you upgrade your system with all the stuff that is in the repos, but things that are not in the repros will mess your system up.  This is why for me and my advice to most people when they upgrade, is to back up ALL YOUR FILES YOU WANT TO KEEP and then do a clean install.

---

### Post by Tom--d on 2008-05-11
If that happend to me, I would back up all my files. 

The.. reboot and see what happens.

---

### Post by astathios on 2008-05-11
thank you all for your reply,
i tryed with sudo dpkg --configure -a nothing happen. u see i was in the last stage of upgrade .
i have keep everything in back up but i couldnt move the file to my external disc  the transfer was cutting in the middle. This is the reason i worry for the restart.
any other idea before i procced with restart?
thank you again

---

### Post by nynoah on 2008-05-11
do you have an external hard drive?  If not, get one that is big enough or burn all your files you need to data DVDs.  Back all your things up.  Even if you have a problem, sometimes you can mount your hard drive using the live boot cd and copy your files over to an external HD or even a spare internal HD if you have one.  I have done this when I messed up my Ubuntu in the past.  

Me personally, I would (after all my files are backed up) do a fresh install.  Maybe someone else has a better idea.  But at this point, back up everything you can so you don't worry so much.

---

### Post by astathios on 2008-05-11
ok i restart
most is working great exept my grafik card it use the basic drivers
is an ati x1400. the emerald is out of order and half of the compiz. i tryed to install the drivers with envy but the problem remains
any help would be greatfull

---

