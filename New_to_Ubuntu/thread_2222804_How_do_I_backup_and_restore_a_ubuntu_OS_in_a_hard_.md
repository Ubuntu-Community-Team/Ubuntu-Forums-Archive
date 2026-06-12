---
title: "How do I backup and restore a ubuntu OS in a hard disk ? \"
date: 2014-05-08
forum: New to Ubuntu
---

### Post by ubuserone on 2014-05-08
Regarding to my previous post [http://ubuntuforums.org/showthread.php?t=2222657](http://ubuntuforums.org/showthread.php?t=2222657) and I have a new question on backup and restore.
I had made quite a lot of changes on 12.04 but I plan to try on 14.04 installing on a same partition.Somehow , if 14.04 doesn't suits me , how do I backup 12.04 and restore it with all the setting I made before without going through a painful way install every application one by another ?

This application does a full backup on OS + system data [http://www.liberiangeek.net/2012/07/backup-restore-your-whole-ubuntu-computer-using-remastersys/](http://www.liberiangeek.net/2012/07/backup-restore-your-whole-ubuntu-computer-using-remastersys/) but I doubt the way to restore when the ISO file is more than 6GB ? will it conflict with up the boot manager ?

Anymore backup tools and utilities recommend ? :)

---

### Post by sudodus on 2014-05-08
I would suggest that you make a compressed 'cloned image' of your whole drive, so that you can restore it to 'exactly' the same state except that unused space is not cloned and restored. This is what I recommend, and the cloned image will be much smaller than the original drive.

The tool Clonezilla can do the job. Get an iso file from

[http://clonezilla.org/](http://clonezilla.org/)

I suggest that you get the current ***stable*** version which I use.

-o-

It is a good idea to ***test that you can really restore the system*** to another drive of exactly the same size or bigger than the original drive. So you need one drive for the image (a directory with several files) and another drive to test restoring it.

If you don't have or don't want to get two drives for this purpose, you can use Clonezilla to clone the content from the original drive to another drive of exactly the same size or bigger. Then you should be able to replace the original drive with the cloned copy and test that it works.

---

### Post by ubuserone on 2014-05-09
> **sudodus said:**
> I would suggest that you make a compressed 'cloned image' of your whole drive, so that you can restore it to 'exactly' the same state except that unused space is not cloned and restored. This is what I recommend, and the cloned image will be much smaller than the original drive.

The tool Clonezilla can do the job. Get an iso file from

[http://clonezilla.org/](http://clonezilla.org/)

I suggest that you get the current ***stable*** version which I use.

-o-

It is a good idea to ***test that you can really restore the system*** to another drive of exactly the same size or bigger than the original drive. So you need one drive for the image (a directory with several files) and another drive to test restoring it.

If you don't have or don't want to get two drives for this purpose, you can use Clonezilla to clone the content from the original drive to another drive of exactly the same size or bigger. Then you should be able to replace the original drive with the cloned copy and test that it works.

It looks like a cloning application.I did a video search at ytube but I still can't get the part. (savedisk and saveparts ) .

---

### Post by sudodus on 2014-05-10
Yes, cloning is a way to make a complete backup, which I think you want. And Clonezilla can also make a compressed image, which needs less space. You can choose to make an image of the whole drive or of one or many partitions. (Only an image of the whole drive will restore the whole system including the bootloader.)

What do you mean with the following statement? > but I still can't get the part

---

### Post by veddox on 2014-05-10
If you don't want to use third party software, you could create a partition backup using TAR (there is a good tutorial [here]("https://help.ubuntu.com/community/BackupYourSystem/TAR")). This procedure will create a .tar.gz archive file of your file system, which you can then save to any external hard drive. Once you have done that, install 14.04 from disk. The installer is set up in such a way that it will try and keep as many of your previous settings as possible. Have fun with Trusty :D

Should you want to revert to 12.04, just follow the instructions in the above tutorial (under the subpoint "Restoring").

---

### Post by manishjagdishthatte on 2014-05-10
I am trying to clone my hdd using tuxboot / clonezilla as mentioned above on my bodhi linux / intel atom machine. Will update with my experiences.
Hope this goes thru without any major glitches :)
Manish

---

### Post by manishjagdishthatte on 2014-05-10
I cloned but the drive is not bootable. How do I make it bootable?

---

### Post by sudodus on 2014-05-10
Welcome to the Ubuntu Forums :-)

Your problem might be different from that of [ubuserone]("http://ubuntuforums.org/member.php?u=1921491"), and I think it is better that you ***start an own thread*** with a good descriptive title. You can ***post a link to your own thread*** from a reply in this thread.

> **manishjagdishthatte said:**
> I am trying to clone my hdd using tuxboot / clonezilla as mentioned above on my bodhi linux / intel atom machine. Will update with my experiences.
Hope this goes thru without any major glitches :)
Manish

> **manishjagdishthatte said:**
> I cloned but the drive is not bootable. How do I make it bootable?

How did you clone it, and how did you try to boot it? Please describe with many details :-)

- Did you clone the whole drive or 'only' some partitions?
- Windows does not boot from USB ...

---

### Post by ubuserone on 2014-05-21
> **sudodus said:**
> Yes, cloning is a way to make a complete backup, which I think you want. And Clonezilla can also make a compressed image, which needs less space. You can choose to make an image of the whole drive or of one or many partitions. (Only an image of the whole drive will restore the whole system including the bootloader.)

What do you mean with the following statement?
Any tutorial step by step guiding using Clonezilla ?
[http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/01_Save_disk_image](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/01_Save_disk_image)

What does "device image" and "device device" option ?

Lets make an example.Sda5 installed with ubuntu with the size used on the partition 10GB/80GB. 70GB unused. Planing to migrate to other partition with the partition size is lesser than 80GB or 60GB.Will it work?

---

### Post by Harsh_Parikh on 2014-05-21
You should visit  [http://www.itsfoss.com](http://www.itsfoss.com)
 for more information aboutbackup and restoring 12.04. You will also get complete iso image file for 14.04 Trusty Tahar

---

### Post by sudodus on 2014-05-21
> **ubuserone said:**
> Any tutorial step by step guiding using Clonezilla ?
[http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/01_Save_disk_image](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/01_Save_disk_image)

What does "device image" and "device device" option ?

Lets make an example.Sda5 installed with ubuntu with the size used on the partition 10GB/80GB. 70GB unused. Planing to migrate to other partition with the partition size is lesser than 80GB or 60GB.Will it work?

'Device Image' makes a compressed image of the source device. 'Device Device' makes a clone, copies from the source device to the target device including master boot record, partition table, everything except the unused and unallocated space.

Clonezilla cannot migrate a system from a bigger device or partition to a smaller one. Each partition must have its original size.

---

