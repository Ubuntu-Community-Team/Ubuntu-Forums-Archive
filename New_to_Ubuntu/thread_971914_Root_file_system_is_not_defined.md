---
title: "Root file system is not defined"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by maruf10 on 2008-11-05
when i am trying to install ubuntu 8.04 LTS the following message is displayed;
"root file system is not defined.fix it from the partitioning menu"

currently i am using Windows XP Professional
what should i do?:confused:

---

### Post by taurus on 2008-11-05
When you tell the installer which partition to install Ubuntu, you need to tell it to mount that partition as / or else you would get that error message about no root partition.

---

### Post by maruf10 on 2008-11-05
i have installed Ubuntu inside Windows
but when i am trying to boot Ubuntu the message is displayed

what should i do?

---

### Post by Bölvaður on 2008-11-05
<added>
This might not be relevant to you because you seem to have used the wubi installer which installs ubuntu from windows.
I would either suggest trying to install again and make sure you find good tutorial on how to install with wubi or do a dual setup like I describe how to do below &#8595;
</added>


I will assume that you want to dual boot.
I will also assume that you have not made any partitions yet.

_Begin to backup all personal data!!_ it should always be the first thing you do before changing stuff on your harddisk no matter what OS or filesystem is on the harddisk. Better be safe than sorry, specially when you are doing it for the first time.

Attention: I also say that you should make special partition for your personal date. This can be ignored if you want. So you are able to make only 2 partitions, swap and main one for ubuntu.

You first make partitions from windows if you have programs to do it in windows. You will need one ext3 partition that is about 8 Gig for your file system and another one for your personal files that is as big as you want it to be.. depends on how much data you will be using. Also make Linux/unix swap partition that is same size as your RAM.

If you can not do the partitions from windows you should defragment your harddisk(s) and do the rest from live cd.

Now we are ready to boot up from live cd (ubuntu cd) and set the partitions up.
Go to System -> Administration -> Partition manager

There you should make your windows partition smaller and make 3 new partitions in the empty space.
Partition #1 is ext3 with 8-10 gig
Partition #2 is ext3 with same size as your personal data will need
Partition #3 is SWAP with same size as your RAM

Apply the changes. It could take long time if there are data on the ntfs (windows) partition that has to be moved.

Now you can begin the installation



[SIZE="3"]Installing[/SIZE]
You will do it exactly like before, when you are asked for where it will be installed you chose to do it manually.

There you will see your 4 partitions including the windows partition.
Mount the 8 gig ext3 partition as "/" (without the goose legs/feet w/e)
Make sure it will be ext3, and it doesnt matter if you format it or not.

Mount the personal data partition as "/home" (again without those signs)
Make sure it will be ext3, and it doesnt matter if you format it or not.

The swap partition will be automatically detected and mounted, so no worries.

Now continue and enjoy

---

