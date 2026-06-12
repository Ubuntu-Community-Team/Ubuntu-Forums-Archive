---
title: "my ubunutusu is broke"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by schavery on 2008-07-29
I only have ubuntu because i think it might make me a little cooler.  But seriously, here is the story.  I have some windows xp on my computer, and one day it broke.  haha so i thought on ho and i want to fix it to play my wonderful lovely video games, but the boot volume or whatever was corrupted and so i had to run the fixboot command from the windows repair disk.  Now this could all be like unrelated and stuff but it is what happened just before i had this problem with my ubuntu (8.04) i dont remember which version of that i have because when i try to boot into ubuntu now it endlessly loads on the orange bar boot screen. ok so i am all like ok. i know the drill and i put my ubuntu disk in there and and then i got it all the way to the password screen on running the live disk option and oh noes my ubuntu doesnt know the alphabet anymore all shows up as boxes.  and even when i know i put my password in right it didnt let me log in.  bullhonky!
:mad::mad::mad::mad::mad::mad::mad::mad:

---

### Post by SunnyRabbiera on 2008-07-29
Actually it might be beyond a OS issue here, it could be signs of hardware failure.
Can you give us a better explanation of what is going on?

---

### Post by InfinityCircuit on 2008-07-29
When you boot up your computer, at the GRUB menu, you should be able to press "esc".  Press "e" over your Ubuntu installation, go to the line that starts with "kernel", press enter, and then remove the words "splash" and "quiet".  Press enter again to boot.  This should give a more verbose error message.

---

### Post by schavery on 2008-07-29
well windows is working fine now, but i eventually did have to do a completely new installation of it to my hdd.  now ubuntu is on a completely different hdd, so i dont see how any of these issues with windows could be a part of ubuntus problems.  my computer is self assembled so if you want any specifications or component i could let you know.  right off the bat i have amd athlon x2, and asus m2n-e motherboard.

---

### Post by SunnyRabbiera on 2008-07-29
Well you never know.
Now for your ubuntu, make sure that you burned the .iso at a low speed.
You may have a bad burn there.

---

### Post by schavery on 2008-07-29
so infinitycircuit:
this is what happened when i did what you said
the last command that came by was 
[64.069639 sd 4:0:0:0: [sdb] Attached SCSI disk

it stopped there for about two minutes then

done.
check root = bootarg cat /proc/cmdline
or missing modules, devices cat  /proc/modules ls /dev

Alert! /dev/disk/by-uuid/b33d1eb4-abba-4ed9-ba2d-55c82aa01a6d does not exist!
Dropping to a shell

bosybox v1.1.3....... built in shell (ash)

ok?

---

### Post by InfinityCircuit on 2008-07-29
Something is wrong with your /etc/fstab.  You need to boot a linux rescue cd and mount the linux partition (say it's /dev/sdb1).  Then run "blkid" and it will show the correct UUID for /dev/sdb1.  Use a text editor to change the UUID in /etc/fstab.  

Sorry but this is a bit difficult to explain in detail so I hope you get the gist of what I am saying.

---

### Post by schavery on 2008-07-29
problem:
like i said earlier, even though it was a tad confusing:
when i try to boot with the live cd and mount the volume, all the characters show up as boxes and the install does not accept my password.

---

### Post by SunnyRabbiera on 2008-07-29
did you check the disk for defects?

---

### Post by schavery on 2008-07-29
no i didnt yet i will tomorrow but i think that it works because i installed from that disk and the install worked for months
it could have been scratched though so i will check it out

---

### Post by SunnyRabbiera on 2008-07-29
its possible.

---

