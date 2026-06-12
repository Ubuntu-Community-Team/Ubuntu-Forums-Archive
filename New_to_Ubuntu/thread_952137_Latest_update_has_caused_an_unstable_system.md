---
title: "Latest update has caused an unstable system"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by noorez on 2008-10-18
Hey guys...I just used update manager to update my system.....after the update I was told to restart my system...(think it was because of a Linux image update....)..

After the restart...everything seemed to move in slow motion...
Firefox did not function properly...it kept crashing after a normal close..My bookmarks were all gone.....

Can anyone tell me what happened...

using ubuntu 8.04 rite now.

---

### Post by SunnyRabbiera on 2008-10-18
In what manner did you update?
Did you update from gutsy to hardy or something?
Just wondering.

---

### Post by noorez on 2008-10-18
I just used the Update Manager GUI.....

It was not a dist upgrade....it was just 8.04 the whole time......

---

### Post by noorez on 2008-10-19
Even worse....I now have 0 bytes free on my disk...which is extremely odd since i'm sure I had a ton of free space before I made this update.......

---

### Post by shredder12 on 2008-10-19
> **noorez said:**
> Hey guys...I just used update manager to update my system.....after the update I was told to restart my system...(think it was because of a Linux image update....)..

After the restart...everything seemed to move in slow motion...
Firefox did not function properly...it kept crashing after a normal close..My bookmarks were all gone.....

Can anyone tell me what happened...

using ubuntu 8.04 rite now.
I think what you are talking about  is the new kernel update..
linux generic *-21 
To check whether the problem is because of it or not..just boot into the old kernel..well, you can do it by pressing Esc at the time the grub loads..then choose the version saying 2.6.24-19 (i am noot sure..but 19 is at the end.. :D) and boot, if your system is working fine with it..then jst boot everytime with the older version..
Hope that solves your problem..

---

### Post by reverseninja on 2008-10-19
After the latest kernel update, I noticed on my desktop that if I left firefox open and walked away, after 5-10 minutes it would crash and close itself.  That's the only oddity I've seen, and it's not that big a deal since it remembers what I had open.  :-D  I'm eager for the ibex upgrade, only 11 more days!

---

### Post by noorez on 2008-10-19
After booting into the older kernel, I still noticed the same problem!

I'll give a list of the problems here:

1. For startup, the part that is slow is after I login and I'm at my desktop. The desktop background and the top panel show up, but after that everything starts to move slow....In the notification panel where it would show programs that are being started, only the volume icon shows up right away but all the others, "Network Manager", "Pidgin", "Compiz Config Icon" take there sweet time.

2. Firefox crashes, even if I do a proper close. My bookmarks are all gone. And I can't save any logins for later such as with iGoogle. I have to login everytime.

3. For the space on my hardisk, I right-clicked on the Filesystem icon in My Computer, and part of the reading was "some contents unreadable"......what the heck happened here! I'm sure I had a fair amount of space left before I made the upgrade...but now its at zero. To verify my disk, I booted up with a live cd and used e2fsck to check the disk and no problems...The partition manager with the live cd and while started up both show that there is free space on my disk.

---

### Post by noorez on 2008-10-19
One more thing I noticed....I don't even think that my disk is being read properly....

When I right clicked on Filesystem to see what was happening..I noticed that the part that says "XX items....totaling XX GB", the number of GB was a lot more then what I had even allocated to the partition using Ubuntu!

---

### Post by sdowney717 on 2008-10-19
```

I'm eager for the ibex upgrade, only 11 more days!

```

just do it it works great for me. Been using it since alpha 6.
Ibex right now is really good.

---

### Post by noorez on 2008-10-19
Lol.....sorry but that really doesn't help at the moment......

When the 8.10 does come out, It would be impossible for me to do an upgrade over the internet since now I have no space to download the updated files.........

I have to actually fix my current problem first....

---

### Post by noorez on 2008-10-20
Anyone have an answer for me.....I know its a lot to ask but I could use some help...Please!

---

### Post by noorez on 2008-10-20
Ok, after a quick check, I got the following results.

1) Ubuntu says it has a filesystem size of a number that is way over the amount that I allocated to that partition....(even if all other disks are unmounted)...and 0 bytes

2) Under windows xp: windows xp says that partition is of the correct size and has zero bytes

3) Gparted reads the filesystem size correctly and the amount of space used up correctly

does this help any?

---

### Post by shredder12 on 2008-10-21
Well once i had a similar problem related to firefox. It was acting as if it forgets everything everytime after a restart...
to fix it i jst ran this command..
```
sudo chown -R *username:username* /home/*username*/.mozilla/
```
Just write you username in place of *username*..
and for you disk space problem...
first of all check if you are all your windows partitions are unmounted while you check your disk space..
and if that's not the case then check for the folder which occupies most of the space..
sometimes log files...occupy a lot of space..(yes believe it or not i have faced such a problem..they actually occupied around 2-3 GB) well just go to /var/log and
there execute this command 
```
du -sh 
```
this will give you the space..of the folder..
just tell me what happens after you do all this..

---

