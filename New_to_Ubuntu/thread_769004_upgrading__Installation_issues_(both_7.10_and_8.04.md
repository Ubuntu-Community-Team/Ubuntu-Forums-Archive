---
title: "upgrading / Installation issues (both 7.10 and 8.04)"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Whitehatnetizen on 2008-04-26
Hi all,

I'm fairly new at Linux in general, I was just hoping that I may find some help here.  this is the situation:

I recently bought a new dell Inspirion 530 with XP home installed (intel dual core, 4gb ram, 320gb hdd)

last week I downloaded ubuntu 7.10 and installed, initially there was an ntfs partition, and a fat 16 partition a bit of googling revealed that dell put some recovery utilities on this small partition rather than providing them on a CD.

so following the prompts I installed 7.10 with absolutely no problems.  I created a fat23 partition for swapping files between the two OS's and installed 7.10 and its swap partition as logical partitions within a 50gb extended primary partition..  grub displayed the appropriate options and I was happily dual booting.

on thursday I downloaded an 8.04 image and tried to install from that.  when booting from CD, it gave the usual ubuntu loading graphic but then dropped out to an initramfs prompt within which every keystroke was duplicated.

I was still able to reboot and access both xp and 7.10 fine.  so the next thing I tried was upgrading from within 7.10.  after downloading the files and updating all the necessary packages etc I thought I was good to go.  restarting the computer gave the grub menu.  everything looked normal exept now there were two entries for 8.04 rather than just one for 7.10.  so I shrugged and hit the first one.  this was followed by the usual ubuntu loading graphic and unfortunately dropping out into the initramfs prompt with the same bizarre keystroke duplication as when booting from the liveCD

so I did a significant amount of googling at this point and wether it's my lack of googling skills or my inexperience knowing what to look for, or both combined with my desire to not destroy my xp partition (I really really really don't want to have to reinstall xp and all the drivers) I couldn't find a satisfactory solution 

so I next I used a system recovery cd (which I downloaded from somewhere linked from the ubuntu site. (thank God I did).  This worked fine.  and in my ignorance and as a last resort I used Gparted to remove the linux partitions.

so I thought that this would remove grub also, but I was very wrong... and I'm kicking myself for not spending the time to find out more.

so I stuck my windows CD in and went into the recovery console and typed fixmbr which got rid of grub.  now my pc is as it was when I bought it minus the 50gb unalocated partition.

so now I've tried both re-installing 8.04 from the cd and 7.10 from the cd and BOTH of them are dropping out to an initramfs prompt.

so I downloaded a knoppix 5.1 liveCD because I've never had any problems with Knoppix previously on any of my computers.  This unfortunately dropped out of the install with the following message:

"Can't find knoppix filesystem, sorry.  Dropping you to a (very limited) shell)"  

the shell incidentally duplicates all my keystrokes......

At this point I would consider a complete wipe of the hard drive (although there's many many hours to put everything back) but I'm not convinced it would actually do anything.  it seems that live CD's are having issues loading into memory.....

so obviously this is not necessarily a Ubuntu problem, but I'm really hoping for some help. I have STFW, but I'm obviously searching on the wrong things or am not experienced enough to know what I'm looking at.

uhm.... help?

P.S.  obligatory smiley:  ](*,)

---

### Post by Whitehatnetizen on 2008-04-27
I really hate artificially bumping my own posts, but I was just wondering if anyone had ANY ideas where I should look next?

---

### Post by alzie on 2008-04-27
I think this is what you are looking for.  go to post #8

[http://ubuntuforums.org/showthread.php?t=587168](http://ubuntuforums.org/showthread.php?t=587168)

Check my sig for an ubuntu specific google search engine.

I hope these help you.  :)  <semi-obligatory happy face

---

