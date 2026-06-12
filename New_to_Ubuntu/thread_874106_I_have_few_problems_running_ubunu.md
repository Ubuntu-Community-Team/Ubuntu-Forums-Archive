---
title: "I have few problems running ubunu"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by anaemic on 2008-07-29
Long story short: The PC: Athlon XP, Gigabyte GA-7N400, 2 hard drives attached to it N.1: 20GB ext3 N.2:120GB ntfs. Occasionally it just doesn't start at all (see picture) and the sound has some noise issues. When you boot it's OK, but if you play something with loud high frequency sound it starts the noisy part sometime it stops after a while some times it doesn't at least until I restart the X. I have tried some "solutions" for problems close to these but in vain.

---

### Post by eightmillion on 2008-07-29
That looks like your hard drive is failing. I would switch over to the 120GB drive and see if you still got errors.

---

### Post by anaemic on 2008-07-30
The problem is it was running fine on XP. And I'm more concerned about the sound issues. Oh, and yeah I tried installing Ubuntu on the 120 but the 20 was still there. Should I try the 120 on only ?

---

### Post by anaemic on 2008-07-30
OK, after messing around a bit more I got the sound to "sound" right. But it doesn't behave good, as I listen to some music through Rhythmbox I pause or stop them and try to play something on youtube and it has no sound after that the rhythmbox can't play either. I think that I got it by using OSS but don't think it's good. Please help. I don't want XP back on this PC.

---

### Post by anaemic on 2008-08-01
Come on people, I know you can do it. I like the Ubuntu community because it has answers for everything. Help me with this. I know you can do it.

---

### Post by Paqman on 2008-08-01
Have you tried booting up into a LiveCD and fscking the disk.

---

### Post by anaemic on 2008-08-03
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda1: clean, 108781/1134240 files, 681076/4524297 blocks

This is what I get. Do I need to specify some extra parameters?
And what about the sound. Give me hints: How can I get which driver it is using, and can I try to change it until I get a desirable results. Or should I get a new sound card :D (repeating, sound and hdd workded perfect under XP). And btw the hdd problem seems to happen even when trying to boot the LiveCD. It's like every fourth or fifth time I start the PC.

---

