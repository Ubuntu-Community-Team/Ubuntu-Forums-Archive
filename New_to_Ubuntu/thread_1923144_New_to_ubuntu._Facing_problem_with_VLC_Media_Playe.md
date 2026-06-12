---
title: "New to ubuntu. Facing problem with VLC Media Player."
date: 2012-02-10
forum: New to Ubuntu
---

### Post by inf1nity on 2012-02-10
Hello everyone,

I downloaded Ubuntu 11.1 Oneiric Ocelot yesterday. Its already up and running. I am using it alongside Windows XP Professional.

While in windows, I had 4 partitions. Windows was installed in C:. when installing ubuntu I couldn't understand what partioning was all about, so i went with the default options.

Well the user interface is very good(better than windows), and the time it takes to start up and shutdown is very less. But there are some problems i faced-

While in windows, I had 4 partitions. Windows was installed in C:. when installing ubuntu I couldn't understand what partioning was all about, so i went with the default options.

1. Now i had all my music in E: in windows. in ubuntu when i create a link to the songs folder on desktop, it works, but after rebooting the link becomes invalid. I then copied all music to /home/music. But the same problem persists.

2. In vlc media player, i added some songs to the playlist, and then i saved the playlist as .xspf. But after reboot, the songs that in the list were gone..!(The .xspf file was still there, but it was empty.)

Please provide a solution to this problem. Thanks in advance. :)

P.S.- Should i install Ubuntu 11.04 or 10.04 LTS in place of 11.10..??
P.S. Maybe i need some understanding of the linux file system and how it is different from windows. Can someone please guide me on this, suggest some e-books..?

---

### Post by pqwoerituytrueiwoq on 2012-02-10
if you want your windows E:\ on ubuntu use the fstab file to set it up like that you can make ~/Music go to that partition

in a terminal run *man fstab* (also googling fstab howto is useful)

"I had 4 partitions"
how did it install, a mbr partition table only allows 4 partitions max Ubuntu needs at least 1 and it will not delete one by default (My XP pro cd will only allow 3 partitions)
as for the playlist issue idk i use rhythmbox for music which auto finds my music in my music folder

---

### Post by oklokl on 2012-02-10
smplayer 
Video

audacious
Audio
Recommendations 

VLC bug..

sudo apt-get install smplayer audacious

---

### Post by Learning Linux 2011 on 2012-02-11
I'm a little confused.  Your music is on the Windows E drive?  Did you copy and paste the music to your Ubuntu Music folder?  Or did you just play the music straight off of your E drive?
If you just play the music off of your E drive, you need to mount the E drive before you can play the music again.  If you copy and paste the music into Ubuntu, you won't have that problem.

---

### Post by inf1nity on 2012-02-18
The playlist problem is solved..! Here's what i did.
I copied my music from E: to /home/Music . 
Instead of saving as an .xspf, i saved it as a .m3u8 playlist.

Now it works..!!
Thanks everyone for their suggestions..!!
And please can someone explain why any shortcuts to any files that are on my Windows drives(Local Disks), become invalid after i restart the computer..?

---

### Post by inf1nity on 2012-02-18
:(

---

### Post by androssofer on 2012-02-18
> **kaustbh said:**
> 
And please can someone explain why any shortcuts to any files that are on my Windows drives(Local Disks), become invalid after i restart the computer..?

the windows partitions are part of windows (as you might guess) so when ubuntu starts it loads up its own patitions etc for you, but ignores the windows 1s as its not part of ubuntu. you have to tell it to load them yourself...  this is called 'mounting'. when you double click the windows partition in the ubuntu file browser you tell ubuntu to mount the windows partition for use.. 

when you create a shortcut it points to where the windows partition was mounted.. however when you restart and mount it again, it will probably have a different address.. so the shortcut points to the wrong place..

its probably easy enough to tell ubuntu to mount it automaticly for you on boot to the same place each time.. but alas, i've never tried so dont know how...

---

### Post by mastablasta on 2012-02-19
these 2 links might help:
official docs: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
how to: [http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14](http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14)

how did you install Ubuntu? side by side or using wubi?

as for the file system and such check out my signature for a link to Ubuntu manual project. it's for an older version but most things apply (appart from the main GUI).

for new version of userfriendly Ubuntu desktop "guide" for 11.10 check out this link:
[https://help.ubuntu.com/11.10/ubuntu-help/index.html](https://help.ubuntu.com/11.10/ubuntu-help/index.html)

---

### Post by inf1nity on 2012-02-19
I installed ubuntu using the CD. I booted from the cd and then set up a dual boot system. And one more question, is this version of ubuntu (11.10 Oneiric Oncelot) stable ?

---

### Post by MG&amp;TL on 2012-02-19
> **kaustbh said:**
> I installed ubuntu using the CD. I booted from the cd and then set up a dual boot system. And one more question, is this version of ubuntu (11.10 Oneiric Oncelot) stable ?

Yes, there are three types of Ubuntu, one is released every six months:

-unstable/testing-where we do the interesting testy stuff for next release. 12.04 is this currently.

-release. These get updates for a year and a half after release. 11.10 is the most recent, but 11.04 & 10.10 is still supported. Fully stable.

-LTS. Every two years, we get a release that is a Long Term Support release, these get updates for previously three and now five years. 6.04, 8.04 and 10.04 have been the LTS releases so far. 10.04 is beginning to show its age now, 12.04 will replace it in a few months' time. If you want stability, I suggest LTS, but I really wouldn't recommend 10.04 now unless you like the UI*

Hope that clears a few things up.

*We've had a new UI, called Unity, from 11.04 onwards, but some people prefer the old one, so quite a few are still in 10.04.

---

### Post by inf1nity on 2012-03-01
hey guys can please sm1 tell me how to start a new thread. I forgot it..!! :@

---

### Post by mastablasta on 2012-03-02
go to for example absolute beginners talk and click the **new thread** button in top left corner.

---

### Post by inf1nity on 2012-03-03
> **mastablasta said:**
> go to for example absolute beginners talk and click the **new thread** button in top left corner.

Thanks dude, I got it. Check out my new thread please.

[http://ubuntuforums.org/search.php?searchid=85615823](http://ubuntuforums.org/search.php?searchid=85615823)

---

