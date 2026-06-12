---
title: "bought laptop put linux on want send back to seller how to get rid of all linux parti"
date: 2018-05-01
forum: New to Ubuntu
---

### Post by idaaa on 2018-05-01
please the easiest way 

to reset pc seems not enough still many partit there 
maybe other traces too...
createt by trying lot of usblive  linuxes which at end not work...also wubis etc

please easy 

maybe exists a program?

because one buys laptop on net 

one tries linux instal full to see if real will work sees pc  not ok for that 

so how get it back ???



have win 10


 getting verry stressed

---

### Post by kerry_s on 2018-05-01
use win 10 to make a recovery drive, just like you do for linux.
windows 10 has that built in. use it to wipe the disk & install win 10 back on.

---

### Post by yancek on 2018-05-01
Did you buy the computer with some unknown operating system already on it?  
Did you then unscuccessfully try to install some Linux, Ubuntu?
If you had some other operating system pre-installed, what was it?
Did you create a recovery disk for it, if it was windows?
If it was windows, you should be able to download  a recovery disk for whichever version you might have.

---

### Post by duister on 2018-05-02
If you still have win10 on it, you can just use administrative tools / Disk Management, and remove the unknown/linux partitions, and create a new NTFS partition in the free space.

If you only have gnu/linux on it, you can just use the win10 installer/or win10 recovery (if it is still there), and use the whole diskspace for a new win10 installation.

---

### Post by idaaa on 2018-05-02
it looks like u can see on pic 
i dont think so it looked when pc arrived
win 10 works

but no reset of win even the longest ...erase every thing.... changes this

maybe seller will claim not give part 

 money back because of that ...;((


to use this tools delete part + expand ...thats is to understand from 100+1 threads can cause even more damage if i maybe delete a part of win ..boat loader etc stuff....

i understand now why so few people use linux
it s riskkyyy

and deinstall not clear at all......


is really no program from ubuntu+ linux fans which brings automatically sure comfortaly with no scare heart attack all back?



thank u verry for answering me


[https://photos.app.goo.gl/L0llTZ5Pm8nkKaPN2   ]("https://photos.app.goo.gl/L0llTZ5Pm8nkKaPN2")

---

### Post by #&amp;thj^% on 2018-05-02
I think and feel that knowledge is the biggest hurdle for folks new to Linux of any kind (Ubuntu Debian Arch Gentoo Devuan Fedora Slackware BSD)
And without some very basic knowledge of how things work first, then yes the "frustration" level can be very high. (We have to learn to make her walk before we can make her run ;))
For your Issue though it just might be>> that you take your machine into a shop and have them reinstall Windows 10 back on it.
For the record I have used linux "only" in some form, for over 13 years now, and I would not change that period.
Good Luck and Best Regards :)

---

### Post by kerry_s on 2018-05-02
just wipe the drive & send it back, tell them you had to wipe for security. because it had work stuff.

---

### Post by idaaa on 2018-05-02
i pressed reset laptop 

i lasted for hours the reseting reinstalling win10

but still look all like u see on pics of link u see them?

win10 on it works 


i just want to get it to look like it was when i got it


i have feeling linux is like a trap first they write is so easy to get it to install beside and try it if u like it  ..beginner quide ...

but they dont tell how to get it away that u can give laptop back for example..

i cant find any link on net for that ..:((


this question can not be so unusual???

pleas ca u not write what to do in my case u see on pic it looks very messssyyy:((((

---

### Post by kerry_s on 2018-05-02
all i see is ntfs in the pics, that's windows not linux. 
linux is ext4, the swap is a linux thing, but ubuntu does not install a swap partition.

you can't blame linux, this is on you. there's a reason you can run it live to test your hardware. if you jumped the gun & installed without testing it's your fault.

if your windows 10 is up & running all you have to do is use the disk manager to delete the empty ntfs partitions & resize to take up the space.

---

### Post by idaaa on 2018-05-02
so if i delete all nfts then it will look like before?
thak for aqnswering with me

ca u tell me what i have to delete?on my pic that i dont delete some windows...

zorin live worked but after instal was not installed so that would work!!

i deleted it with ubuntu os-deinstal os  deleter searchig internet for that for hours!!


live iso  test is not saying it will work! thats a linux lie!!

---

### Post by kerry_s on 2018-05-02
to me it looks like p4, p5, p6, p7 would be safe to delete.

---

### Post by yancek on 2018-05-02
If you plan to use only windows, it would seem to me that it would make more sense to use the windows tools such as Disk Management as it would show the windows partitions with drive letters which you won't see on Linux.  Make sure you don't delete the first partition which is the efi partition and contains windows boot files.  You might have better luck at a windows forum since you want to install and use windows.

---

### Post by idaaa on 2018-05-03
hallllooo so what to delet away????

---

### Post by yancek on 2018-05-03
Windows creates a number of partitions which often aren't accessible or seen by users.  The only partition you have that you would need to delete is partition 6 which is the Linux swap partition.  I don't know what partitions 5 and 7 are, they contain hardly and data but windows may use them.  Partition 4 has 484MB of data so that is probably used or necessary.  Ubuntu didn't create any ntfs partitions so delete 6 and leave the rest alone.

---

### Post by Odisej on 2018-05-06
It is hard to help if there is little information on what you did and how you did it.

If your laptop came with legal Windows 10 get Windows 10 ISO  and reinstall it. 

It seems you took a lot of wrong steps and you should not blame linux for that.

---

### Post by hier-kommt-luis on 2018-05-08
Are you actually sure that reseller would take it back when OS has been changed? If yes, so you should do a recovery from win 10, as kerry_s mentioned

---

### Post by monkeybrain20122 on 2018-05-08
Still don't know why you want to return the machine. 

Sounds like you want to return the machine because there is no  Windows on it. But the seller won't take it without Windows, so you try to put Windows back so they would take it. But if you succeed in putting Windows back why do you still want to return it?? The logic sounds confusing.

if hardware works then all you need is to slap some OS on it, whether Windows or Linux. 

It seems that it is your own fault rather than Linux's. I don't think you could install Windows on that machine with your approach if that pc hasn't come with Windows preinstalled. If you pay some guy $20 he could install Windows for you in no time. Just need a recovery iso and do some partitioning. And I suspect Linux would work too.

P.S. don't try to dualboot if you don't even know how to install either OS on its own. Dualbooting is an advanced operation.

P.P.S If the goal is to install Windows 10, wouldn't MicroSoft's forum be a more appropriate venue for the question? Also the pic looks like Mint rather than Ubuntu.

---

