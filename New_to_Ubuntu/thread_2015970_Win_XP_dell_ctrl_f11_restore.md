---
title: "Win XP dell ctrl f11 restore"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by biohzrd87 on 2012-07-03
So I think I may have jumped the gun a bit and got myself too excited to start in the ubuntu world. I just got a Dell XPS m1210 from my grandma. I know its kinda old but I decided I could use it as a second laptop at my house to play around and learn with, something I am not scared to break. She had it full to the max when I got it so instead of killing myself trying to clean it out I decided to just use the dell restore by using the ctrl+f11 at boot up. I got everything going good and started to get things updated on the windows side so I decided to dual boot with ubuntu 12.04 lts. I went back to the windows side and got everything going again except now I can not get it to update to win xp service pack 3. I wanted to go back to windows only for the moment and finish all updates before I dual booted this time but now when I press ctrl+f11 at the boot up I just get the machine beeping at me and it goes into the normal boot menu, I think its called grub? My grandma says she has the recovery disk the machine came with but I dont know if she will ever find them. I want to be able to get this back to factory so I can run the updates fully and then dual boot it. 

When I sudo fdisk -l I get this


Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders, total 153356490 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       64259       32098+   6  FAT16
/dev/sda2   *       64260    79681102    39808421+   7  HPFS/NTFS/exFAT
/dev/sda3       143090955   153340424     5124735   db  CP/M / CTOS / ...
/dev/sda4        79681534   143089663    31704065    5  Extended
/dev/sda5        79681536   141012991    30665728   83  Linux
/dev/sda6       141015040   143089663     1037312   82  Linux swap / Solaris

can any one tell me how I can get back to factory, or atleast get the ctrl+f11 to work again? I have been looking around but some of these forum have gotten me confused, I have a little to nothing knowledge of ubuntu right now.

---

### Post by mikewhatever on 2012-07-04
Hi, and welcome to the forums. Can you clarify a few thing:

Why do you want to go back to the factory state? Haven't you done the restore procedure very recently? What does ctrl-f11 do other then factory restore?

---

### Post by biohzrd87 on 2012-07-04
Hey thanks for your reply but I actually figured out how to use the factory restore. What was happening was that I could not upgrade the xp side of my machine to service pack 3. I actually found another thread, after a lot of searching, that pointed me towards DSRfix. I ran that and was to get back into the dell system restore partition and fix my machine.

---

### Post by mikewhatever on 2012-07-05
Glad you got it solved, however, for the benefit of the future readers, you might want to post a link to the page that helped you.

---

### Post by biohzrd87 on 2012-07-05
Oh yeah sorry I forgot that. Here is the link to the page that helped me out [DSRfix]("http://www.goodells.net/dellrestore/") also this [thread]("http://ubuntuforums.org/showthread.php?t=1763835") helped out.

---

