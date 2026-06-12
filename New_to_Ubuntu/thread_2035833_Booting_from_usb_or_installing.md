---
title: "Booting from usb or installing?"
date: 2012-07-31
forum: New to Ubuntu
---

### Post by GJ1234 on 2012-07-31
Hello everybody in the Ubuntu community,

I'm really happy to say that I've successfully booted Ubuntu 12.04 LTS from my 4GB fat32 partitioned USB device.
Really excited about all the features.
I installed it with the idea of only syncing the Cyanogenmodrepo and building it from source, but I think I'll want to use it for everything!
Unfortunately I'm not that familiar with partitioning et cetera:(
So I'm asking if running Ubuntu from an usbdevice does have any major disadvantages? (storage,speed?)
I'm not planning  to install any games (I use Windows for that) and for some compatibility stuff I'm holding on to my Windows 7 OS.
How simple would it be to install them on the same C:/ without losing any data on my Windows installation and no performance drop.

Looking forward to answers!
GJ1234

---

### Post by nbetham on 2012-07-31
With regards to storage and speed USB isn't the fastest kid on the block when it comes to transferring data. Additionally depending on the tools you might install that 4GB might fill up rather quick. However it is a simple solution to just up and running with Ubuntu for a few quick things here or there. I wouldn't recommend running off of USB for anything important however. 

As far as partitioning goes, Ubuntu is pretty good at finding out what OS is installed on a drive. Given enough space Ubuntu can re-partition around Windows and play nicely with Windows on the same HDD. But with any partitioning there is a possibility of loosing data. If you do plan to go ahead with installing along-side Windows make sure you back up all your data, there is always a possibility, albeit unlikely, that the install could go sideways and wipe the drive. As well, make sure you read all the prompts in the install, I myself have once failed to do so and didn't notice that I was erasing my original partition, with all my data on it. Luckily I had backups on-hand to restore my data.

Regards,
Neil

---

### Post by GJ1234 on 2012-07-31
> **nbetham said:**
> With regards to storage and speed USB isn't the fastest kid on the block when it comes to transferring data. Additionally depending on the tools you might install that 4GB might fill up rather quick. However it is a simple solution to just up and running with Ubuntu for a few quick things here or there. I wouldn't recommend running off of USB for anything important however. 

As far as partitioning goes, Ubuntu is pretty good at finding out what OS is installed on a drive. Given enough space Ubuntu can re-partition around Windows and play nicely with Windows on the same HDD. But with any partitioning there is a possibility of loosing data. If you do plan to go ahead with installing along-side Windows make sure you back up all your data, there is always a possibility, albeit unlikely, that the install could go sideways and wipe the drive. As well, make sure you read all the prompts in the install, I myself have once failed to do so and didn't notice that I was erasing my original partition, with all my data on it. Luckily I had backups on-hand to restore my data.

Regards,
Neil

Mm okay thank you!
Is there any good guide to do so?
Just to feel more secure you know! aha
Pretty excited about this atm :)

---

### Post by nbetham on 2012-07-31
Also I forgot to mention you could use VirtualBox from Oracle to run Ubuntu inside Windows, check it out here [https://www.virtualbox.org/](https://www.virtualbox.org/). This option removes the possibility of erasing your Windows partition. If you're not planning on doing anything to CPU or graphics intensive this is by far the best option compared to dual booting. If you still want to dual boot however this: [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu) seems to be a fairly complete guide on how to do so.

Regards,
Neil

---

### Post by GJ1234 on 2012-07-31
> **nbetham said:**
> Also I forgot to mention you could use VirtualBox from Oracle to run Ubuntu inside Windows, check it out here [https://www.virtualbox.org/](https://www.virtualbox.org/). This option removes the possibility of erasing your Windows partition. If you're not planning on doing anything to CPU or graphics intensive this is by far the best option compared to dual booting. If you still want to dual boot however this: [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu) seems to be a fairly complete guide on how to do so.

Regards,
Neil

Thanks!
But I was thinking by myself, what if I do this:
[http://www.youtube.com/watch?v=b6Ycx2K2OeY&feature=related](http://www.youtube.com/watch?v=b6Ycx2K2OeY&feature=related)
until the WUBI part, so I can install Ubuntu on the space I created?
Or am I thinking to simple?

---

### Post by nbetham on 2012-07-31
If you are referring to the partitioning portion of the video the Ubuntu installer will do the same when you are installing it from USB or CD. Both essentially do the same thing, either way should yield the same results.

Regards,
Neil

---

### Post by oldfred on 2012-07-31
Wubi is fine for an extended test to see if you like Ubuntu or not. It is a file inside the Windows NTFS partition and uses the windows boot loader to boot into the grub menu.

But even the creator of wubi expects once you decide you like Ubuntu to install to partitions.
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Most new Windows 7 systems use all four primary partitions, some say just to make it more difficult to install another system to separate partitions.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

If you have a larger USB flash drive you can do a full install to that. Again USB & flash is not as speedy as a hard drive. But it is functional especially if you have a fair amount of RAM. May be a bit slow loading a larger app, but once loaded runs just as fast as it is in RAM.

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by GJ1234 on 2012-07-31
TThanks for all the help, but let me set this straight:
I can shrink the Windows partition from 600 to 525 and then install Ubuntu on the 75 GB partition?

---

### Post by oldfred on 2012-07-31
If you have not used all 4 primary partitions that will work.

Post this from liveCD:

sudo fdisk -lu

---

### Post by Dawnbandit on 2012-07-31
Try Wubi and when installing Ubuntu its Installer has a pretty simple easy to use partition editor for installing.

---

### Post by GJ1234 on 2012-07-31
> **oldfred said:**
> If you have not used all 4 primary partitions that will work.

Post this from liveCD:

sudo fdisk -lu

Sorry for being a noob, but you mean used in terms of free space?

---

### Post by oldfred on 2012-07-31
Space wise that is fine. 

You can run Ubuntu in small partitions if you houseclean often and do not save a lot of data. My / (root) with lots of applications is 11GB including  /home with .wine using most of /home.  I have that in a 30GB partition, but most of my data in a shared NTFS data partition and a Linux formated data partition. 

You could use a 20 to 25GB / (root), 2 to 4GB swap and the rest as /home or data if you want.

---

### Post by GJ1234 on 2012-07-31
> **oldfred said:**
> Space wise that is fine. 

You can run Ubuntu in small partitions if you houseclean often and do not save a lot of data. My / (root) with lots of applications is 11GB including  /home with .wine using most of /home.  I have that in a 30GB partition, but most of my data in a shared NTFS data partition and a Linux formated data partition. 

You could use a 20 to 25GB / (root), 2 to 4GB swap and the rest as /home or data if you want.

Mm okay will shrink it, if there are problems I will report!
Thanks to all, and I'm amazed with the community!

---

