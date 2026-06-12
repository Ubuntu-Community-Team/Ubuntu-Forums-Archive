---
title: "disk upgrade erased everything"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by tanyac on 2008-11-30
perhaps i am inept and this is what would normally happen, but i know i did my last upgrade by disk and did not lose everything. I installed 8.10 today with a disc... and everything now appears to be gone. i would really like to think it is somewhere on my harddrive, but i have no idea how to go about finding the files. 

my computer looks like its the first time its been used, there is nothing but the operating system.

any help... just let me know the info you need.

---

### Post by Zzl1xndd on 2008-11-30
the big question is how did you do the "Upgrage"? Did you place the disk in while the system was running, or did you restart and install??

---

### Post by tanyac on 2008-12-01
i restarted

---

### Post by hyper_ch on 2008-12-01
then you installed from disk and did not upgrade :(

---

### Post by DGortze380 on 2008-12-01
then you didn't upgrade, you installed.

boot your live cd, open a terminal and type sudo gparted.

Post a screenshot of that window. Don't change anything yet.

---

### Post by tanyac on 2008-12-01
just to be perfectly clear so i dont mess things up worse...

do i start the computer with the disc in the drive, and then choose the run ubuntu without changes (sorry paraphrasing, the first option) and then open a terminal and do as you say?

---

### Post by DGortze380 on 2008-12-01
> **tanyac said:**
> just to be perfectly clear so i dont mess things up worse...

do i start the computer with the disc in the drive, and then choose the run ubuntu without changes (sorry paraphrasing, the first option) and then open a terminal and do as you say?

yes.

I'm just trying to see whether or not your old data is totally gone.

I need that screenshot to tell whether you installed over everything (you probably have, and unfortunately your data will be difficult or impossible to recovery); or if you just installed a dual boot system and resized the original (in which case, we can easily recover your data).

---

### Post by tanyac on 2008-12-01
screenshot attached.

thanks for your help...

---

### Post by DGortze380 on 2008-12-01
sorry to be the bearer of bad news... you've previous installation has been erased. chances of getting all of your data back are non-existent, you may recover some with tools like test disk or dd rescue. 

If you plan to attempt data recovery on the drive, either make an image or bit for bit copy before mounting the drive again. For that, look at tools like mkisofs and dd.

---

### Post by Foolishgrunt on 2008-12-01
Just to make sure this is clear...

If you restart your computer and boot from the disk before installing, then it will do a clean install and not save any of your data. If you insert the disk while the system is running and upgrade from there, then it will only install the new components and all of your previous settings will be saved.

---

### Post by tanyac on 2008-12-01
sigh...

well thanks for the help. unfortunately I dont think i am savvy enough to try what you describe above, since i dont know what any of it means. 

i lost a book i was writing. :( i have an older version, but i lost about two weeks of work i cannot redo.

---

### Post by DGortze380 on 2008-12-01
> **Foolishgrunt said:**
> Just to make sure this is clear...

If you restart your computer and boot from the disk before installing, then it will do a clean install and not save any of your data. If you insert the disk while the system is running and upgrade from there, then it will only install the new components and all of your previous settings will be saved.

Correct. 

The more important information is to ALWAYS backup your data before any major changes to your system.

---

### Post by otamotacon on 2008-12-01
thats pretty much the way it works

---

### Post by hyper_ch on 2008-12-02
> **DGortze380 said:**
> The more important information is to ALWAYS backup your data before any major changes to your system.

No, not only when you do something major.... ALWAYS have backups. your harddisk may fail from one day to another without doing anything major.

---

### Post by resander on 2008-12-02
Very sad you lost your data....

The Ubuntu install script should check if there is data on the disk and warn the user clearly that  ALL YOUR WORK IN PROGRESS WILL BE LOST IF YOU CONTINUE....

---

### Post by hyper_ch on 2008-12-02
> **resander said:**
> The Ubuntu install script should check if there is data on the disk and warn the user clearly that  ALL YOUR WORK IN PROGRESS WILL BE LOST IF YOU CONTINUE....

It does... but years of "software installing on windows" is just like:

click yes, click yes, click yes, click yes - without reading anything.

---

### Post by tanyac on 2008-12-02
> **DGortze380 said:**
> sorry to be the bearer of bad news... you've previous installation has been erased. chances of getting all of your data back are non-existent, you may recover some with tools like test disk or dd rescue. 

If you plan to attempt data recovery on the drive, either make an image or bit for bit copy before mounting the drive again. For that, look at tools like mkisofs and dd.

thanks for your help. i would like to try a data recovery, but what you describe above i do not know how to do... so unless you want to do some beginer hand holding i think i am screwed. 

it is unfortunate, i lost two weeks of heavy editing i have been doing to a book i am writing (my last back up was 2 weeks ago to an external), plus i lost so much music an dphotos that i didnt have backed anywhere. :(

---

### Post by tanyac on 2008-12-02
> **hyper_ch said:**
> It does... but years of "software installing on windows" is just like:

click yes, click yes, click yes, click yes - without reading anything.

the only thing i remember it asking me was whether i wanted to save it to a specific part of the drive, or save it to the largest part of free space... which made me believe that space on my drive was still being taken up by all of my data. oh well. at least i had the important stuff backed up... just not since 2 weeks ago.

i was just so sure of myself because this is how i did previous updates. but that small detail of restarting i guess makes a big difference. 

again, thanks to all of you for your help.

---

### Post by hyper_ch on 2008-12-02
well, if you want to recover data, then (1) get a drive of equal size or larger and (2) image the original drive to the new one with "dd".

Then you can start recovering.

---

### Post by tanyac on 2008-12-02
> **hyper_ch said:**
> well, if you want to recover data, then (1) get a drive of equal size or larger and (2) image the original drive to the new one with "dd".

Then you can start recovering.

i have an external drive i can use.

but i dont know how to image the drive and i dont know what "dd" is. sorry i am a super novice.

---

### Post by hyper_ch on 2008-12-02
do you have at least equal the space on your external drive as your internal drive is large?

if so, what filesystem format has your external drive?

---

### Post by tanyac on 2008-12-02
yeah the external is twice the size i am pretty sure. right now on the external i just have things i save to back up or transfer between computers at home and work. Its a LACIE drive, i am not sure what you mean by file system.

---

### Post by hyper_ch on 2008-12-02
is the filesystem ext3 or ntfs or fat32 or xfs or reiserfs or or or?

---

### Post by tanyac on 2008-12-02
> **hyper_ch said:**
> is the filesystem ext3 or ntfs or fat32 or xfs or reiserfs or or or?

oh! 

NTFS

thanks for your patience!

---

### Post by lisati on 2008-12-02
> **hyper_ch said:**
> It does... but years of "software installing on windows" is just like:

click yes, click yes, click yes, click yes - without reading anything.
):P Been there, done that......
> **tanyac said:**
> oh! 

NTFS

thanks for your patience!

Any chance that any of your recent work is saved on your external hard drive? If you're in luck there might be enough there to help save you some mucking around.

---

### Post by hyper_ch on 2008-12-02
the external drive is ntfs?

---

### Post by tanyac on 2008-12-02
it says ntfs when i check the properties when it is plugged into my computer. 

and to the other post... yeah, i have a version saved from 2 weeks ago... but in the past 2 weeks i was unfortunately very productive.

---

### Post by mkvnmtr on 2008-12-02
Just to give you a little hope. There is a good chance that most of your home folder it outside of the new install and you will be able to find it. Listen to these guys and if yuou are not sure ask them again.

---

### Post by hyper_ch on 2008-12-03
you then have to

(1) start the live cd
(2) install ntfs-3g to mount the external drive also with write
(3) find out what the internal and what the external drive is (names)
(4) then open a terminal an run
```

sudo dd if=/dev/sdX of=/media/external/sdX.iso

```
where /dev/sdX is your internal drive (very likely /dev/sda) and /media/external is where you have mounted the external drive to.

Be careful here!!!

Once you have made that backup, you can start trying to recover the data with some forensic tools. I heard good thing about photorec but never used it.

---

### Post by tanyac on 2008-12-03
okay ... I will try this tomorrow night when i have time off work. I will let you know if i run into any issues.

thanks again so much, even if i cant recover stuff I am very grateful for everyones help and patience.

---

### Post by hyper_ch on 2008-12-03
well, basically you make a 1:1 copy of your internal harddisk on your external one (stored as file) and then you can use forensic tools to try and recover data from your internal harddisk.

---

### Post by DGortze380 on 2008-12-03
> **hyper_ch said:**
> you then have to

(1) start the live cd
(2) install ntfs-3g to mount the external drive also with write
(3) find out what the internal and what the external drive is (names)
(4) then open a terminal an run
```

sudo dd if=/dev/sdX of=/media/external/sdX.iso

```
where /dev/sdX is your internal drive (very likely /dev/sda) and /media/external is where you have mounted the external drive to.

Be careful here!!!

Once you have made that backup, you can start trying to recover the data with some forensic tools. I heard good thing about photorec but never used it.

I've never used dd with anything but an empty drive... wont this start at the beginning and overwrite anything already on his external? Or am I wrong and it will start at the first free block?

---

### Post by hyper_ch on 2008-12-03
you will have to mount the external drive frist.. hence the path /media/external/sdX.iso where sdX.iso just just the new filename on the external drive which is moutned at /media/external.

---

