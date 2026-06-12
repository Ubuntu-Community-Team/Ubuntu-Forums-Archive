---
title: "Raid status in MOTD"
date: 2013-11-13
forum: New to Ubuntu
---

### Post by knight8524 on 2013-11-13
Good Afternoon all,

This I hope should be fairly quick. I've set up a home server running RAID 5 and an SSH server. 
I've got it set up so every time I log in, it displays the array status (cat /proc/mdstat), but the personalities line at the top (for a quick health check as I log in) is unnessescary to me.

I've played round with GREP, but can't figure out a way to just make it say only the bits I need: ie:

**********************************
Welcome to the Media Server
Current Array Status is as follows:

[COLOR=#ff0000]Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] [/COLOR]
md127 : active raid5 sdc1[1] sdb1[0] sdd1[3]
      3906763776 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>
*********************************

Ie: I don't want it to display the red text.

I know this is a stupidly simple solution, but for the life of me I just can't get it to do what I want at the moment, and thought someone might be able to save me some time.

---

