---
title: "Remastersys questions."
date: 2012-02-05
forum: New to Ubuntu
---

### Post by bonedriven on 2012-02-05
Hi. I am using Remastersys but after I read all its descriptions still don't quite understand the 4 kinds of backup.

1. Backup whole system
I used this once, but after that I don't know what to do? And where is the file it backed up?

2. Distcdfs, Dist, Disto. What are the differences? I don't know what is a filesystem.  

Thanks.

---

### Post by wolfen69 on 2012-02-05
[This]("http://www.dedoimedo.com/computers/remastersys.html") may help.

---

### Post by bonedriven on 2012-02-05
> **wolfen69 said:**
> [This]("http://www.dedoimedo.com/computers/remastersys.html") may help.

Thanks. But I think that link is outdated and contains misinformation too? [I]

"Dist: allows you to create a backup, **sans** your personal data, allowing you to share the "remastered" copy with other people."[/I]?

---

### Post by Bodsda on 2012-02-05
> **bonedriven said:**
> Hi. I am using Remastersys but after I read all its descriptions still don't quite understand the 4 kinds of backup.

1. Backup whole system
I used this once, but after that I don't know what to do? And where is the file it backed up?

2. Distcdfs, Dist, Disto. What are the differences? I don't know what is a filesystem.  

Thanks.

> 
Dist

Makes a usable Ubuntu environment that you can give to people, based on your installed software and configs etc, but excluding all personal info.

> 
cdfs
Can't see any mention of it, but it will be the same as dist except a live cd version.

> 
Disto
No idea where you saw that

If you can provide the link where you got this info, I might be able to help more.

Bodsda

---

### Post by bonedriven on 2012-02-05
In [this link]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html"):

[I]4) to make a distributable livecd/dvd of your system

```
sudo remastersys dist
```

5) to make a distributable livecd/dvd filesystem only

```
sudo remastersys dist cdfs
```

6) to make a distributable iso named custom.iso but only if the cdfs is already present

```
sudo remastersys dist iso custom.iso
```

cdfs and iso options should only be used if you wish to modify something on the cd before the iso is created. An example of this would be to modify the isolinux portion of the livecd/dvd[/I]

I have read your post and the explanation above. But I still don't understand the difference between them. :(

Anyway, what I want is to build my os in my vmware machine on my own laptop. Then I use remastersys to make it a custom live usb bootable os which I can use in my workplace. And it would the best if it can be a persistent live usb os too.

---

### Post by Brizvegan on 2012-02-05
> Backup whole system
I used this once, but after that I don't know what to do? And where is the file it backed up?The custom-backup.iso file (in my case) was located in /home/remastersys/remastersys.  (Click on Filesystem in Places first, then /home/remastersys/remastersys ... ).   Don't know why there are 2 remastersys folders in my case :confused:

If you want to make a live dvd, open a burning program eg. Brasero and choose "Burn image" - "burn an existing CD/DVD image to disc".
Choose a low burning speed.

If you wanted to make a live usb, maybe use the .iso file with Unetbootin, or even Startup Disk Creator - I don't know for sure if these work, I've only ever burned live dvds.

If you want to share your remastered distro - use "dist" option.
The "backup" option contains your own user files, so if you have personal files in /home they will be included in your new distro.

Someone here has made a live usb stick with a remastersys .iso:
[http://www.techsupportalert.com/content/make-your-own-customized-bootable-linux-live-cd-or-usb-stick.htm](http://www.techsupportalert.com/content/make-your-own-customized-bootable-linux-live-cd-or-usb-stick.htm)

---

### Post by Brizvegan on 2012-02-05
Just did an experiment ...

I took a recent remastersys custom-backup.iso file, opened Startup Disk Creator on Linux Mint 9 and created a live bootable usb stick with 2gb of persistence (on a 4gb SanDisk Cruzer).

It's working fine - am posting from it now.  :)

When I booted up with it, at the remastersys bootsplash, I pressed Tab, and typed at the end of the line:
> live acpi=off  I should mention that I used "backup" mode, and that I have no data in my /home - I have a separate data partition symlinked to /home.   So the .iso was well under the 4gb file size limit.

Also, in my source system (gnome) I have installed "ubiquity-frontend-gtk" from Synaptic Package Manager.  You need this in the system you're backing up if you want to install your live usb to a hard drive. 
Without it, there is no install option on your live usb/dvd at boot.

---

### Post by bonedriven on 2012-02-06
Thank you, Brizvegan!

Luckily, I don't need to install it to a hard drive (against the rules of our univerisity?).

I just built a live cd iso with Remastersys dist mode in my vmware machine, and used LiLi to create a persistent live usb. But don't know why when I boot it up, it showed "Invalid or corrupted kernel image".

And now I seem to understand what is backup mode and dist mode of Remaster. But what about the other two, "Distcdfs" and "Distiso"? In what circumstances should I use those?

---

### Post by Brizvegan on 2012-02-06
> when I boot it up, it showed "Invalid or corrupted kernel image".  Can you boot your live usb?  Does it boot up to the desktop?   Is it usable?

> But what about the other two, "Distcdfs" and "Distiso"? In what circumstances should I use those?      I don't know, to be honest  :???:   

I just know that the "simple" modes of "backup" and "dist" have worked ok for me.

This website may shed a little more light on "Distcdfs" and "Distiso":
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)
> cdfs and iso options should only be used if you wish to modify something  on the cd before the iso is created.  An example of this would be to  modify the isolinux portion of the livecd/dvd You could try the Remastersys forum as well:
[http://www.remastersys.com/forums/index.php?PHPSESSID=95v44b1il476rmu54imomb0lj5&board=38.0](http://www.remastersys.com/forums/index.php?PHPSESSID=95v44b1il476rmu54imomb0lj5&board=38.0)

---

### Post by bonedriven on 2012-02-06
> **Brizvegan said:**
> Can you boot your live usb?  Does it boot up to the desktop?   Is it usable?


I am not sure what you mean. I created an iso file with remaster in my vmware machine (Dist mode). I copied the custom.iso to my host machine. Then I used LiLi(usb bootable system creater) to create the persistent live usb on my 8G pendrive with it. Then I tried to boot it up and failed.

I had the options to choose during boot though:"1. persistent mode; 2. Live cd mode...etc." But all of them lead me to the same error message "Invalid or corrupted kernel image".

---

### Post by Brizvegan on 2012-02-06
> Then I tried to boot it up and failed. Oh ....I thought it had worked for you :(

In your VMware machine, do you have Startup Disk Creator installed in your linux distro?

Tutorial on Startup Disk Creator:
[http://www.tuxgarage.com/2011/06/create-persistent-bootable-usb-drive.html?](http://www.tuxgarage.com/2011/06/create-persistent-bootable-usb-drive.html?)  
or [http://www.upubuntu.com/2011/07/how-to-create-bootable-ubuntu-usb-flash.html](http://www.upubuntu.com/2011/07/how-to-create-bootable-ubuntu-usb-flash.html) 

Could you try to make your live usb with this program **in linux, in your virtual machine**? 
As mentioned above, I had success with it in Mint 9.  It boots up with no problems.

Who knows, you may have more success with it than the windows program.
Can only give it a try :)

---

### Post by bonedriven on 2012-02-06
Hi Brizvegan.

OK, I'll try building it in my virtual machine. Hope I have enough space for it though.

---

### Post by Brizvegan on 2012-02-06
This may be why your live usb didn't boot ...
"why is Remastersys is not compatable with Windows USB maker programs?":
[http://www.remastersys.com/forums/index.php?topic=1443.0](http://www.remastersys.com/forums/index.php?topic=1443.0)

So it looks like you'll either have to use Startup Disk Creator or Unetbootin in linux.

Also, Startup Disk Creator requires a flash drive formatted in FAT or FAT32.

---

### Post by bonedriven on 2012-02-06
> **Brizvegan said:**
> This may be why your live usb didn't boot ...
"why is Remastersys is not compatable with Windows USB maker programs?":
[http://www.remastersys.com/forums/index.php?topic=1443.0](http://www.remastersys.com/forums/index.php?topic=1443.0)

So it looks like you'll either have to use Startup Disk Creator or Unetbootin in linux.

Also, Startup Disk Creator requires a flash drive formatted in FAT or FAT32.

Thanks Brizvegan! You saved me! I built a live usb under linux. Now it's working very well! I would have tried more reinstallation if you had not told me to do it under linux. :o

I'd like to mark the thread to "solved" but still, we haven't got an answer about the "distcdfs" and "distiso". Also, I noticed in my custom live usb system, there's a "2.1Gb filesystem". What is that? I can't open it either. When I built the system with Remastersys, I set the persistent capacity to 1.9Gb. What is this 2.1Gb filesystem in my os? :confused:

---

### Post by Brizvegan on 2012-02-06
Good you had some success with it.

> Also, I noticed in my custom live usb system, there's a "2.1Gb  filesystem". What is that? I can't open it either. When I built the  system with Remastersys, I set the persistent capacity to 1.9Gb. What is  this 2.1Gb filesystem in my os?  I don't think it's possible to access the filesystem on the live usb.   I  think that's just the way the "live" environment works.   

When I open System Monitor (in Mint 9) > File Systems - with the 4gb live usb plugged in it shows this:

Device - /dev/sdb1      
Directory - /media/1969-9FFS
                Type - vfat
    Total - 3.7Gib
Free - 916.2MiB
Available - 916.2MiB
Used - **2.8GiB**
76%

It's beyond me  :grin:

You may get some answers to these questions on the Remastersys forum -  the link is above.

cheers
Brizvegan

---

