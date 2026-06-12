---
title: "Vista / Ubuntu partitioning"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by G_iBuntu on 2008-11-30
Hi, 

I'm looking to install ubuntu on my laptop pc, 
Currently I'm running Vista, i have made several attempts to resize my hard drive to free some space for ubuntu...this has resulted in major failure for the moment:lolflag:

System:
Vista
Dual core 2ghz 
2gb of ram 
110 of HDD (2 partitions) 


My hard drive is a 110Gb drive 

i have a primer partition of 80gb (50 used by vista only almost) the maximum shrinking i can do on this one is reduce it to 60gb 
a second, called logical drive 26gb
a third part not used 

[[IMG]http://img234.imageshack.us/img234/8042/49760190xp9.th.jpg[/IMG]](http://img234.imageshack.us/my.php?image=49760190xp9.jpg)[[IMG]http://img234.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)



please help me on this one, i can't find the way to partition my drive correctly to install Ubuntu :(

Many thanks 

Gm

---

### Post by zzHanks on 2008-11-30
Ubuntu should detect other operating systems and do that for you, if I remember correctly.

Just boot the LiveCD, select 'Install' and you'll be guided through it.

---

### Post by G_iBuntu on 2008-11-30
with the Live cd, Ubuntu want's to format my whole drive and instal ubutnu on the 110gb. I guess because the unallocated space is in front our after my extended partition 

I want dual boot with vista :(

---

### Post by dxplosiv1 on 2008-11-30
zzHanks is right tho. If i remember, it has on option to use the entire hard disk, then another option that opens partition manager and lets you drag the size of you 110gb partion down...It's been a while, but I'm pretty certain.

---

### Post by zzHanks on 2008-11-30
I have a dual-boot (two hard drives).

If possible, I recommend that, to be on the save side.

@dxplosiv1: It probably does not detect Windows.[URL="http://ubuntuforums.org/member.php?u=417413"]
[/URL]

---

### Post by whitethorn on 2008-11-30
I'd be pretty careful with partitioning with vista.  From what I've read a couple months back (might've been fixed by now)  Vista had/has a problem when you resize the partition with a non vista method.  The best way would be to see how much vista will let you free up, and use that space to install ubuntu into.  But you do have enough space for ubuntu (if you plan on using the partition with 26 gig).  If you want to install to that drive, I would first delete it in vista.  

Right click and delete partition.  

Bootup the Live cd, and choose Manual when asked by the partition editor, choose the partition you deleted in windows.

---

### Post by ajgreeny on 2008-11-30
Take care, however, as it looks as if you have some files on the 26GB partition.  You will either need to copy them to the 80GB partition first, or make sure they are backed up somewhere.  I would suggest also that you only use the vista disk management tools to edit your current vista partition as other third party applications like gparted have caused problems to some people in the past.  Once you have the space free, you can then use gparted to edit it for ubuntu without any risk.

You did not tell us what is actually on the various partitions either, or why there is a 3.16 unallocated partition at the end of the disk.  Is that a result of your attempt to partition the disk already, or was it there before?

It may be possible to use the 26 GB partition and add that and the 3.16 GB together to make the space for ubuntu, but without knowing more about what is on the partitions at the moment, it is difficult to be more exact.

---

### Post by G_iBuntu on 2008-11-30
Ok, I'm on UBUNTU! :KS:KS 

I found the solution,

the unknown files on the second drive was a "pagefile.sys" file...used to give a pc an extra boost of memory when needed. I had to de-activate that option in Windows system option. 

Secondly I deleted my second drive with gParted, 

Thirdly I reduced the size of my primary drive where vista is installed on, 

so I Had just vista & some free space on the same drive and all the rest unallocated space. 

... I installed Ubuntu following this tutorial (great tutorial by the way) [http://www.breizh-ardente.fr/article/partitionnement-avance](http://www.breizh-ardente.fr/article/partitionnement-avance)
(in french) 

All went great, ubuntu booted as he should, updated 243 files :lolflag: 

then i try Vista again and then... tadaaaaa [COLOR="Blue"]**BLUE SCREEN!**[/COLOR]! ERROR 4444432232 bla bla bla bla bla ... however i was prepared! 

I had downloaded the Vista restore disk the day before 
You can get it here --> [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

I had to do a STARTUP REPARE...took ages, an hour or something (stress-full moments hahaha) .... and then Vista was alive again! All is running normal. 

I'm a happy man, I installed successfully Ubuntu and vista in Dual boot on my PC

This may help some other people who maybe have the same problem.


--------------------------------------------- 
CASE CLOSED 
--------------------------------------------- 

Thanks all for you're fast answering! Long live Ubuntu

---

