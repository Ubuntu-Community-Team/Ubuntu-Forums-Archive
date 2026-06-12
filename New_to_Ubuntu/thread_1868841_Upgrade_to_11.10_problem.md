---
title: "Upgrade to 11.10 problem"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by phoenixcor on 2011-10-24
I recently upgraded from 10.04 to 11.10 and I am getting the "no such partition" Grub rescue message.  Trouble is, I am not dual booting and I all of the boards are filled with steps to get back to a running windoze os, but I am a complete convert to open source computing and do not care about windoze or have it on my box.  

On the install of 11.10 I chose to change the partition size of / and home/  but after the install and upon trying to reboot I am stuck at the "no such partition" of grub loader, 

Any suggestions?

---

### Post by jnorthr on 2011-10-25
If you are comfortable with the idea, you can jut do a full re-install and let the partition manager choose it's own settings. Do not make any choices yourself unless you REALLY known what you are doing. As you learn and become more confident you can try fresh installs later - just get it in and working first taking all the default values - they should work fine. 

There will be many more chances to play with partition management - it's almost a national sport !

---

### Post by phoenixcor on 2011-10-25
check this out. 

on my desktop i have two hdd's.  one drive is dual boot, some business programs i need only run on windoze or mac.  the other hdd is strictly ubuntu which i use for everything else and was never loaded with any other os other than ubuntu.  

for reasons unknown to me, even though i am certain i changed the partition size on the drive i intended to update (the ubuntu only drive) as i can see what drive i was altering at the install setup, the upgrade went on the disk with xp and ubuntu.  

i downloaded the grub boot repair disk, and it corrected the problem to the extent that i can bring up the dual boot disk.  once in, i can see the other disk and thankfully all the data that i needed is in tact.  

i went to the extent of disabling the dual boot disk, but now grub has seemed to override the bios hdd priority and even with the dual boot hdd disabled it keeps booting back into the xp/ubuntu hdd, strange??

that said, i have worked on my computers all day today and have accomplished many things.  got my linksys wireless adpater working, my wireless printer working, the new cable/wireless networking modem are online and somewhat have addressed my "no such partition exists"  issue addressed in the sense that i have access to my data.

that said, i would like to correct this issue with my hdd's.  i was thinking i could manually disable the hdd that ubuntu wants to start, which may force it to go the one that is the problem.  what do you think?

---

### Post by jnorthr on 2011-10-25
> **phoenixcor said:**
> check this out. 

for reasons unknown to me, even though i am certain i changed the partition size on the drive i intended to update (the ubuntu only drive) as i can see what drive i was altering at the install setup, the upgrade went on the disk with xp and ubuntu.  

=> that was probably because it was the first hdd on the drive chain and your ubuntu hdd is not the first drive <=
 -----------------------

i went to the extent of disabling the dual boot disk, but now grub has seemed to override the bios hdd priority and even with the dual boot hdd disabled it keeps booting back into the xp/ubuntu hdd, strange??

=> not strange if it's the first hdd on your chain.
-------------------------------


that said, i have worked on my computers all day today and have accomplished many things.  got my linksys wireless adpater working, my wireless printer working, the new cable/wireless networking modem are online and somewhat have addressed my "no such partition exists"  issue addressed in the sense that i have access to my data.
=> well done !!! now take backups !


that said, i would like to correct this issue with my hdd's.  i was thinking i could manually disable the hdd that ubuntu wants to start, which may force it to go the one that is the problem.  what do you think?

i'd also try disconecting the xp drive and re-connecting the ubuntu drive as the first/only drive then see if you can boot ubuntu. not a practical solution i know. 

i was thinking that if we could swap the drives so drive 1 becomes drive 2 and vice-versa AND ubuntu boots ok, then it's a question of whether windows would find it's own on the second drive. seems to be a problem either way. my guess is that xp is NOT smart enough to do that. so i'm stumped. may come back to this one tomorrow after some shut-eye :wink:

---

