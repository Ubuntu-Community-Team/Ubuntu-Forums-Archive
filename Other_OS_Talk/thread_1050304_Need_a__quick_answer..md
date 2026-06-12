---
title: "Need a  quick answer."
date: 2009-01-25
forum: Other OS Talk
---

### Post by TimbuntuX on 2009-01-25
Hey everyone,

I am trying out a few different distros and need a little help. I'm not to smart in partitioning my HD but since I have all my data backed up i am willing to take some chances on really screwing it up. I couldn't find an easy way to partition my HD in vista until i founf out that i could just shrink a volume. Vista would only let me shrink it to 9gb so i figured that would be plenty to try out some distros. So I did. I installed Freespire (yuck) on the new partition and overwrote the MBR (i didn't know 50-50 on that). Anyway i now have grub installed and it lets me boot into either freespire or Vista. Now, my question is i want to get rid of Freespire and try something else. Can i just install the next distro on to the same partition? Will that just erase Freespire (i'm ok with that) and will grub still be there? Also, when i want to put things back to the way the originally were can i just use Vista's disk management utility and delete the volume and then allocate it back to drive C?

---

### Post by smartboyathome on 2009-01-25
Use a virtual machine if you are afraid of messing up. That is what I do. :)

---

### Post by kk0sse54 on 2009-01-25
> Hey everyone,
 Can i just install the next distro on to the same partition? Will that just erase Freespire (i'm ok with that) and will grub still be there? Also, when i want to put things back to the way the originally were can i just use Vista's disk management utility and delete the volume and then allocate it back to drive C?

Yes you can install another distro on the same partition as freespire and use the same swap too. I'd suggest using gparted (available on most linux liveCD's, including Ubuntu, Zenwalk etc etc) delete the freespire partition and reformat it into whatever filesystem you would like. You would then have to reinstall grub unless you have it installed on a separate /boot partition. As for restoring your computer I don't use the vista disk management utility, but if you were to use gparted again all you would have to do is delete the linux partition and it's swap and then just resize your vista partition by expanding but you would also have to restore your MBR since grub would be deleted (unless again on a seperate /boot partition) and everytime your computer booted it would look for grub not being able to find and hence you would be locked out of your vista partition.

Here's a howto on restoring your MBR and vista bootloader
[http://ubuntuforums.org/showthread.php?t=740221&highlight=restoring+mbr](http://ubuntuforums.org/showthread.php?t=740221&highlight=restoring+mbr)

---

### Post by TimbuntuX on 2009-01-25
> **C!oud said:**
> but you would also have to restore your MBR since grub would be deleted (unless again on a seperate /boot partition) and everytime your computer booted it would look for grub not being able to find and hence you would be locked out of your vista partition.

Here's a howto on restoring your MBR and vista bootloader
[http://ubuntuforums.org/showthread.php?t=740221&highlight=restoring+mbr](http://ubuntuforums.org/showthread.php?t=740221&highlight=restoring+mbr)

Hmm, yes it is best i write that down in case i can't boot into anything. Does it matter what file system i use? Which one is best?

---

### Post by kk0sse54 on 2009-01-25
Not really since there is no best, they all have their disadvantages and advantages so it usually just comes down to personal preference. The most commonplace filesystem for linux will be ext3.

---

### Post by fistfullofroses on 2009-01-25
Removal of a dual boot setup when u r done playing with Linux:

boot into Vista, right click computer, choose manage, go to disk management, remove the Linux partition.
insert your vista disc, and reboot from CD.
choose recovery.
go to a command line/terminal.
bootrec /fixmbr

---

### Post by TimbuntuX on 2009-01-25
Ooh that was scary. I tried what the link said and I entered the bootrec/fixmbr which said was successful, then bootrec/fixboot and then it said something about not being able to read the file format. Rebooted then I get the dreaded "no operating system found". Inserted the recovery CD one more time and rebooted. I found a section in there that start up recovery so i went into that and let it find and repair any problems and it did just that. Rebooted and Vista is there again, whooh!!! The i went to disk management and just expanded my C volume and all is back to normal. I think I stick with just trying distros that install inside windows, much safer. Thx for all for ur help.

---

