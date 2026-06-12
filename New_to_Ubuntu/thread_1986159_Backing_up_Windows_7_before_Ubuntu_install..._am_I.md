---
title: "Backing up Windows 7 before Ubuntu install... am I doing it right?"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by Episteme on 2012-05-24
I would like to install Ubuntu and give it a proper test drive. However, since I have a nearly full 120G SSD - I'm opting to backup windows, format, and installing to a clean drive.
 
To do the backup, I intend to boot from the Ubuntu install CD and use dd to back up /dev/sdb (my 'C' drive) to /media/ (my 'D' drive) ... and want to make sure that I'm doing it right.


To make a compressed backup image of my C drive to my D drive called backup1.img.gz
# sudo su
# dd if=/dev/sdb | gzip > /media/New\ Volume/backup/backup1.img.gz  <-- likely to take several hours 

To restore the image:
# sudo su 
# gzip -dc /media/New\ Volume/backup/backup1.img.gz | dd of=/dev/sdb

Will this work? Am I missing anything?

Thanks for reading my question.

Sean

---

### Post by traditionalist on 2012-05-24
> **Episteme said:**
> I would like to install Ubuntu and give it a proper test drive. However, since I have a nearly full 120G SSD - I'm opting to backup windows, format, and installing to a clean drive.
 
To do the backup, I intend to boot from the Ubuntu install CD and use dd to back up /dev/sdb (my 'C' drive) to /media/ (my 'D' drive) ... and want to make sure that I'm doing it right.


To make a compressed backup image of my C drive to my D drive called backup1.img.gz
# sudo su
# dd if=/dev/sdb | gzip > /media/New\ Volume/backup/backup1.img.gz  <-- likely to take several hours 

To restore the image:
# sudo su 
# gzip -dc /media/New\ Volume/backup/backup1.img.gz | dd of=/dev/sdb

Will this work? Am I missing anything?

Thanks for reading my question.

Sean

That may well work, but as a newbie to Ubuntu you should not rely on Ubuntu commands to back up other systems.

Make images of what you want to backup:

[http://www.easeus.com/disk-copy/download.htm](http://www.easeus.com/disk-copy/download.htm)

I have found that software reliable and I have used it a lot.  It is also quick and easy to use.

You can have severe problems if you try to mix formats like NTFS  and ext3 or 4. A good image obviates most problems.

Make sure to test boot your recovery media!

---

### Post by Episteme on 2012-05-24
Great little program - but... if I understand it right... this will format my second drive and make it an exact copy of my 'c' drive. Basically, a direct dd if/of from one drive to another with some error checking for good measure. Very handy (and I've added it to my toolbox, thanks!), but since I intend to keep the contents of my 'D' drive intact (it has all my files on it), it won't really fit the bill.

Instead, what I am trying to do is create a *.whatever backup file of my windows 7 'c' drive for future recovery - and store it on my 1Tb secondary drive. 

As such, I've managed to create a backup.iso.gz using my 'recipe'. 

Now, using dd is the way we did it old school - maybe there is a newer, better way? (please don't suggest Ghost... I hate what Norton did to that great little program - used to be able to boot from a floppy and create/install backups SOOOO easily... made a real gui-mess of things... but I digress). If not, I've read the latest man pages for both gzip and dd - but, what I would like to know now is... am I missing a critical switch (ie. block size), and if not, now reliable is it?  If I restore using it, will everything go back to the way it is now?  Just looking for some reassurence before I pull the trigger.

---

### Post by Paddy Landau on 2012-05-24
I recommend the application [CloneZilla]("http://www.clonezilla.org/").

It is just like, say, Norton Ghost, in that you can save a (compressed) copy of selected partitions or of the entire disk.

Unlike Norton Ghost, it is free :) but not terribly user-friendly :(.

You save the image to CD or, preferably (because it's faster), USB. Just follow the instructions on the website. Then reboot from the CD or USB and follow the instructions to back up your entire disk.

I have used CloneZilla many times for Windows and Ubuntu, and it is reliable.

---

### Post by Paddy Landau on 2012-05-24
Actually, having written my previous post, why don't you install Ubuntu on your D: drive? Then you don't have to fiddle around with backups and restores. You will still have Windows (so you will "dual-boot", i.e. whenever you restart your machine, you can choose between Windows and Ubuntu).

When you install Ubuntu, you will need to select the advanced partitioning instead of letting it do it for you. Select the partition that holds your D: drive, and use some but not all of your D: drive. I'd recommend as many Gb as you have RAM for your swap; and allow 10Gb for the operating system plus however much space you choose to save as data in Ubuntu.

Don't worry if the partitioning is not exact at first, because you can easily change Ubuntu's partition sizes later.

---

### Post by Episteme on 2012-05-24
Thanks Paddy,

I've heard of CloneZilla - and will give it a try - thanks.

Yeah - I was thinking of using my secondary drive for some, if not all, of the the linux partitions ... but in sad truth, it's almost full also... 

Cheers!

Sean

---

### Post by Paddy Landau on 2012-05-25
> **Episteme said:**
> ... my secondary drive ... it's almost full also...
Ubuntu needs just 15Gb, and that includes the swap partition and space for some data.

A third alternative is to use an external hard drive. I have done that for testing and it runs nearly as fast as when installed internally. The only thing to be extra-careful with is when you install Ubuntu, to specify the advanced options and tell it to load the boot-loader onto the external hard drive and not onto your internal hard drive (otherwise you can't use your Windows without your external drive plugged in!). If you don't know how to do that, just ask.

---

### Post by Mark Phelps on 2012-05-25
My personal recommendation is to download and install the FREE version of Macrium Reflect on your PC -- and use it to make an image backup of your Win7 install.  You can then later, restore that image to a different drive. You will need to use the option to create and burn a Linux Boot CD in order to do that.

---

