---
title: "Disk imaging - Will it work if done via windows ?"
date: 2014-02-06
forum: New to Ubuntu
---

### Post by hebdave on 2014-02-06
Hi I have just downloaded Ext2Fsd which is a windows file system driver that shows up my linux partition via windows. I then decided to take a partition image via aomei backupper of the partition. Now to me its job done. But what happens if I ever need to restore my linux operating system ?

Could I format my partiton if required. Re-install the ubuntu operating system. Then go to restore the image and it would send the extra files needed to have a working system again. i.e. I could re-boot after image restore via windows into ubuntu and it would be as good as new ? 

Or is it a case of you would not be 100% sure but probably 'yes'.

I must confess I am new to imaging too so its all a learning experience for me. My reasoning doing this via windows is I needed to be able to read linux files via windows occasionally anyway so thought I could then use my same imaging software from there too.

Thanks for your help!

---

### Post by Dave_L on 2014-02-06
In theory, a partition image is a partition image, so it should work.  When I was still transitioning from Windows to Linux, I used TeraByte utilities for backing up both Windows and Linux partitions.

But it would be best to do an actual test. Back up a Linux partition, erase (zero or format) the partition, restore it and verify that the restore worked.

---

### Post by Gone fishing on 2014-02-06
I use clonezilla on the excellent Parted Magic [http://partedmagic.com/](http://partedmagic.com/) live CD which has many useful utilities that can for example help you recover lost partitions, unformat etc.

---

### Post by hebdave on 2014-02-07
Hi I tried to format and got this error -

Error creating file system

An error occured while performing an operation on "224 GB file system.(Partition 6 of partition 3 of ATA WDC WD5000BPVT-80HXZT3): The device is busy.

Is this something to do with the image I took as I did a partition image CHECK in windows and I am not certain if it restores during checking to actually check it. I think but could easily be wrong that I had a similar error pop up in windows after an image was taken and checked. Having said this I have no idea if its related and it might be nothing to do with the error above. As mentioned before i use Aomei backupper which has a good internet reputation. The error above was what happened when I clicked format  today. I went to the disk utitlity via dash home(applications) entered 'disk' and then opened 'disk utility'. I clicked on the partition ext4 and then erase and format or similar to that.

What is happening and do you require further information from me perhaps. Should I look up a log or use the terminal. I don't know to much yet about it. I have typed in commands in the past which went okay before.

Thank you very much :eek:

---

### Post by Dave_L on 2014-02-07
You tried to format a partition as ext4 using AOMEI Backupper?  Personally I wouldn't trust a Windows tool to create a Linux file system.

Since the error was issued by that tool, it might be best to ask the vendor for help: [http://www.aomeitech.com/support.html](http://www.aomeitech.com/support.html)

---

### Post by sudodus on 2014-02-07
> **Gone fishing said:**
> I use clonezilla on the excellent Parted Magic [http://partedmagic.com/](http://partedmagic.com/) live CD which has many useful utilities that can for example help you recover lost partitions, unformat etc.

+1 for Clonezilla. I download it directly from the Clonezilla web site, but it should make no difference, except maybe which version you get.

---

### Post by Dave_L on 2014-02-07
My only gripe about clonezilla is that the interface is hard to understand.  I'm reluctant to recommend it to someone who's not proficient with using shell commands. Maybe that's improved in recent versions.

---

### Post by sudodus on 2014-02-07
*Dave_L*, Clonezilla is still text-based (mainly text based menus). That could be a problem. In that case we can look for linux backup programs in general.

*hebdave*, would you prefer a program with a graphical user interface? In that case ***Simple Backup*** might be a good linux alternative. But there are several programs, that can do similar things, either cloning/imaging, making backup, or synchronizing.

---

### Post by newb85 on 2014-02-07
I wouldn't trust any Windows tool to preserve permissions on a Linux system, either.

---

### Post by hebdave on 2014-02-07
High thanks for the advice. However I am more paricually focusing on the error message itself that I have and why when I go into the disk utility and press format disk it then shows the error. Its most likely I have dreamed up what I told you and it was like this before any imaging. ie - not related to the disk imaging. I think we need to take a look at what the error is. Does anyone know what it is as all errors have meaning I'd of thought if they are a named error. Not that am not thankful for you help of course with the other advice which I am noting as we go along.

Cheers :)

---

### Post by newb85 on 2014-02-07
It sounds to me like you're trying to change a partition the system has mounted. You'll have to unmount it first.

---

### Post by sudodus on 2014-02-07
I would not rely on a backup via Ext2Fsd in windows.

***Device busy*** usually means that the device is mounted and cannot be unmounted, and therefore the program cannot do its job (in this case create a file system, if I understand it correctly).

Editing partitions and creating file systems should be done when the computer is booted from another drive, for example an Ubuntu CD/DVD/USB drive.

---

### Post by hebdave on 2014-02-07
Oh right , so when any person who uses ubuntu needs to change anything they use there cd/usb creator to alter the partitions. And if 'yes' do I then have to unmount it always too ? I will try and find something from the ubuntu documentation if you recommend I go there and read that. Computing never comes naturally to me hence coming to a beginners forum to got beginners advice I guess.

Thanks.

---

### Post by sudodus on 2014-02-07
> **hebdave said:**
> Oh right , so when any person who uses ubuntu needs to change anything they use there cd/usb creator to alter the partitions. And if 'yes' do I then have to unmount it always too ? I will try and find something from the ubuntu documentation if you recommend I go there and read that. Computing never comes naturally to me hence coming to a beginners forum to got beginners advice I guess.

Thanks.

You cannot change partitions that are mounted. In my opinion you should not change partitions on the same drive as you have booted from. So when you want to change partitions on the internal drive, you should boot from an external drive, and an Ubuntu CD/DVD/USB drive is a good drive to boot from.

If the partitions that you want to change were automounted, when you booted from the other drive, you should unmount them before you start editing. You can check which partitions are mounted with the terminal window command

```
df
```

You can unmount partitions with the file manager, or with with the terminal window command umount, for example
```

sudo umount /dev/sda1
```

for the first partition on device /dev/sda, which is often the (first) internal drive.

---

### Post by hebdave on 2014-02-13
High I have only just got round to imaging. Ive been getting a multi-boot usb key working as a computer tool kit. As some of you I am sure must do I use 'Yumi' for this. Now I am using Partion magic as a multi-purpose tool as I think one of you advised. I went to the start menu in the Partiton magic distro desktop and found that there was a entry saying 'disk imaging'. Please note this in not clonezilla or gparted. I highlighted the ext3fd or some similar name to that. I did this because the extended partition showed 'blank' with no Gigabytes next to that entry. I therefore assumed as the ext3fd had the correct ubuntu GByte number it was cool. How ever when I pressed return after highlighting it nothing happened. I could not find any instructions from the program that made sense or there wasnt any I cant remember. A yumi program might be okay to advise me on. I have hirens boot cd on yumi multi boot which has partition magic with gparted and clonezilla and also that other start menu imaging program -(the one that did not seem to work described above)

I then decided to try clonezilla which also has no real instructions to it that I can see that made sense for the imaging type I required. I did try to understand what material they had but to me it did not describe what I needed.

So I looked on the net and found some help there but again it was not really specific on imaging. I was looking at this article [http://draalin.com/using-parted-magic-to-clone-a-partition/](http://draalin.com/using-parted-magic-to-clone-a-partition/) and it goes through the screenshot menus. I am not 100 % certain if I select Device to image **or** Device to Device in the first screen. And then after this part it does thankfully seem more obvious from the screenshots. I am a bit worried about clonezilla as it is my first imaging experience and my computing skills are pretty bad compared to people on here at least. Overall I'd be average in computing skills but not compared to you guys- I'd be a beginner. For example I'd be vague in partition excercises but slowly starting to grasp and understand things. I've read about 5 articles on partition imaging but each article leaves me with a question on something. I cannot really grasp a full understanding from them. It appears you need experience as well as trial and error to some degree  to my mind to sort out computer situations if at beginners level. I do believe you can still help me easily though. The link above would show you the Steps I can potentially take and I was hoping you could do 10 steps for me to follow if its that many. First I'd need to tell you what I need to do though. 

I need to make a disk image not a clone. I believe a clone might wipe my entire external drive (not sure). I want to make an image therefore instead which I believe goes to a file. I am making an image from my internal linux partition to my external hard drive. I therefore am thinking if clonezilla ends up being used I need to select '[COLOR=#0000cd]Device - image working with disks or partitions using images'[/COLOR] from there first selection named in blue on clonezillas first screen. That is instead of selecting the [COLOR=#000080]Device - Device[/COLOR] selection underneath it. Although the [COLOR=#000080]device to device[/COLOR] one does looks tempting too as I do need to make an image of one disk partition and send it to an external disk in my case. But they call it a hard disk not an external drive and it may mean backup to another internal hard drive instead I am not sure ? Also it looks odd to me as it does not have the word 'image' in its title so it may be cloning and not an image. 

Also since reading articles on cloning some say it wipes the external disk of its current contents too. Since I have other things on that external disk I am making sure I do the right thing by checking with you. I assume from reading on the net that an imaging is often a file and a clone is a replica so it means the clone can do bad things to external disks. Welcome to the world of a computing beginner folks ! - Sorry ! 

I'd appreciate 5-10 steps for imaging as files therefore if you'd be so kind to help me out ? My ubnuntu installation is alongside windows and on its own partition - I tend to select the partition which is has the Gigabytes labelled next to it which is the right number for my linux one. This is because different programs say different things making it confusing. Correct me if I am wrong to do this please - thanks ! It should be easy enough for me to follow if you can provide steps for me. 

Yes I do like graphic interfaces ideally as I am used to windows computing programs which seem to be easier to me normally. Clonezilla at first appearance has lines that make sense where you just make the selection and hit return. If long term I would get confused with clonezilla please don't advise me to use it though- many thanks !

I'm hoping someone will be kind enough to help me and realise I am trying my best with what I am aware of. I won't do anything I don't feel confident about so don't worry that you might be responsible for any mistake I make. Not that you would worry of course :D

---

### Post by monkeybrain20122 on 2014-02-13
> **hebdave said:**
> 
I'd appreciate 5-10 steps for imaging as files for me therefore if you'd be so kind to help me ? My ubnuntu installation is alongside windows and on its own partition - I tend to select the partition which is has the Gigabytes labelled next to it which is the right number for my linux one. This is because different programs say different things making it confusing. Correct me if I am wrong to do this please - thanks ! It should be easy enough for me to follow if you can provide steps for me. 
 

I use fsarchiver for imaging and restoring my Linux systems, it is fast and easy to use and                 more flexible than clonezilla.

[http://ubuntuforums.org/showthread.p...3#post12923983]("http://ubuntuforums.org/showthread.php?t=2204491&p=12923983#post12923983") See post #8 for brief instructions.    
More  [http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)
You can use it on the Ubuntu partition for sure, but I don't know anything about Windows, don't have it, don't use it (except in Vbox)

There is a third party gui call qt4-fsarchiver (on source forge) but I am not seeing the point as you really only need two commands, one for cloning, the other for restore.

---

### Post by hebdave on 2014-02-13
Thanks for that program monkeybrain I will see if the others can help me on some of the more specific questions first. Just to say I may be sounding more confused than I really am. I can follow guided help on the above mentioned  , Many thanks.

Just to say monkeybrain the link I read on fsarchiver to a beginner could be misunderstood. I read the first command and if it was just that I put in the terminal that is fine :p , but when you went into detail it sounds like you need to alter that command with numbers etc. That leaves a beginner to linux confused as you don't know whether to leave the command as it is or change it. I assume the restoration command stays the same. It is possible I should use the GUI.
 
I also should say when I read gparted instructions it told you to do it one way which was understandable but it then said if you had to restore several times it may affect the partitions. It then said you need to do other preparation work to get round that- thats where I got confused in what it was asking. So with gparted I genuinely was trying to see what it means but struggling. Clonezilla did not seem obvious for the other reasons stated above. I have used linux for only 3 weeks and I am not an experienced massively experienced with windows prior. I estimate it taking me 6 months to get to grips with linux which is fair enough - it should not be to bad I'd of thought.

I'll wait for help - many thanks !

---

### Post by monkeybrain20122 on 2014-02-13
fsarchiver creates a file which you can store anywhere. You can call it a clone or an image or whatever, but it is just a compressed archive of your file system and meta information such as uuid and disk labelling, there is no risk of wiping your drive.

---

### Post by hebdave on 2014-02-13
Thanks for answering the other questions as well thats kind of you :p. I have edited my above answer back to you again as I was confused on some bits of your thread on fsarchiver. I'd be intrested on what others say too since seeing a bigger picture could hugely benefit me before shooting off in one direction. Thanks all and thanks MB for your answers !

---

