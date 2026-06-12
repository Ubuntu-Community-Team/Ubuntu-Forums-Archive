---
title: "Freeing up disk space for an upgrade"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by brodiesel on 2008-09-07
Hey all, I looked for this in the search but couldn't find the exact question I had. I installed Gutsy a few days back, and have had a few problems (excessively long blank boot screen, crashing after trying to quit "Battle for Westnoth") and decided to upgrade to Hardy, upon which I received this message:

"The upgrade aborts now. The upgrade needs a total of 1180M free space on disk '/'. Please free at least an additional 80.0M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."


So, when I was originally doing the install, I tried to give the Ubuntu partition more space, but the partition utility was using some very confusing numbers, and I ended up leaving ~70 gigs of my 80 gig drive to XP. Soooo I've tried to go back to change the sizes of the partitions, and it will let me change the XP partition but won't let me change the locked Ubuntu partition. I read somewhere online that I can "simply unmount the partition" but when I tried that I was told :
"The partition could not be unmounted from the following mountpoints:

/

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually."

... which I don't know how to do. 

Long story short, any suggestions? Should I change partition sizes and upgrade? Should I uninstall ubuntu all together and reinstall as Hardy? If so, how do I ununstall Gutsy? 

Any info appreciated....

---

### Post by anjilslaire on 2008-09-07
You need to boot using your Ubuntu install CD to resize the Ubuntu partitions. The "/" is obviously in use while you're running the system

So, boot the Live CD, and use the partion manager from there to resize them, then boot back into the installed OS & upgrade.

---

### Post by brodiesel on 2008-09-09
that did the trick. btw, what are the reasons they advise 10g for the ubuntu partition? is it bad that i only have 8 allotted?

the other larger question is how i create a partition that has files (eg music, movies, pics) that can be used by both xp and hardy. any suggestions?

---

### Post by anjilslaire on 2008-09-09
10gig is just a nice round number for the OS. Gives it room to grow, temp files, etc.

Create a partion & format it as FAT32. Both OSes can read that format.

---

### Post by daefu on 2008-11-02
Maybe somebody can help me. I don't really understand my filesystem.
Clicking on Places / Computer shows me:
[LIST]
[*]/ (3.5 GB free)
[*]CD ROM
[*]IBM_Preload (5.9 GB free)
[*]/media/hda5/ (4.2 GB free)
[*]Filesystem (1.2 GB free)
[/LIST]
Are these different partitions?
I guess that the update can only use the free space in Filesystem. Can I tell it to use other freespace. 
Can I move Free Space from other partitions (?) into Filesystem. How can I do this safely?
Thank you for your help!

---

