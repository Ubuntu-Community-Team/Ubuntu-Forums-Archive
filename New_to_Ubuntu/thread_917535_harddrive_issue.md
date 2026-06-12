---
title: "harddrive issue"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by crazypenguin2008 on 2008-09-12
i just got a new machine built,had to use nuke and boot to clean 2 harddrives. the 20gig western digital took the install like a dream. but when i put the second 30gig western in the box it does not boot. it goes thru the first screen on hardy,then it goes to a broken "grub" screen but not all the script is even there. 

its too much strain on my little 20gig drive. any advice on how to get the second drive to reconize?? 

do i need to take the first drive out and put the second in the first position and do a install up to the point that it partitions then quit or what?:confused::confused::confused:

---

### Post by Pro-reason on 2008-09-12
When you add hardware to a system, everything gets new identifiers.

You need to [run the grub installer]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") again, and/or amend your */boot/grub/menu.lst* file.

---

### Post by natirips on 2008-09-12
Check the jumpers on your disks, perhaps they are in a conflict. But the above post is a more probable solution to your problem.

---

### Post by crazypenguin2008 on 2008-09-12
when i pull the jumpers and restart it boots fine. ill try the commands whne i get home on sunday....im trying to brave the weekend at my girlfriends place using her windows notebook lol :lolflag:

---

