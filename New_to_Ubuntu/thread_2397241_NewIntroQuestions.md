---
title: "New/Intro/Questions?"
date: 2018-07-27
forum: New to Ubuntu
---

### Post by rmleloupjr on 2018-07-27
Howdy, 

So New here, literally.

I have a MSI GP60-2PE laptop, 16gb DDR3/1600, 250gb Samsung Evo, 2x2tb 2.5" drives. Nvidia 840 / Intel 4600. Plenty of customization, and enjoyment.

I have a Win10 Dual boot system. Took a bit to clue in, to remove the 2x 2tb drives, as my SSD was "Sata 2" instead of Sata 0... Basically discovered I had to remove them, as I had Win10 successfully installed. 40GB partition spared, and the uBuntu Studio kept failing as it "lost the drive" and couldn't find the files. Basically that means I had to remove the drive's and leave my 250gb mSata SSD in. This allowed it to be "drive 0" SDA* and let me install alongside windows easy... (Frustrating at first, but worked out).

I have my windows and ubuntu storage set to the 2tb drives, so incase of any corruption glitch or facepalm... I can just redo uBuntu or windows etc... without loss of files/media.

Looking to customize the themes thoroughly, and not sure how to. I have Terminal, know how to copy/paste.... ish... Clued in fast that CapITOLs and lower case are important...

I'm seeing Compiz Fusion setup/support (Have compiz, but not the fusion effects like cube, fire from years ago).

I'm running uBuntu Studio 18.04 successfully so far.

I am looking for a few AIO social media apps, etc. To universally interface live various social media thoroughly.

Any suggestions for speed optimizations, and anything else would be appreciated.

I occasionally do video editing with paid apps on Windows, but have seen a few freebies from Studio that look enticing. Can't wait to try them out.

And Hi,

- RMLeLoupJR

---

### Post by oldrocker99 on 2018-07-27
There are several social media apps for Linux. The best video editor is probably kdenlive. Look around, and install synaptic to make searching for files a lot more quickly and easily.

---

### Post by oldfred on 2018-07-27
With my SSD, I do change a few default settings.

       [http://arstechnica.com/gadgets/2015/04/27/ask-ars-my-ssd-does-garbage-collection-so-i-dont-need-trim-right/](http://arstechnica.com/gadgets/2015/04/27/ask-ars-my-ssd-does-garbage-collection-so-i-dont-need-trim-right/)
Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.debian.org/SSDOptimization](https://wiki.debian.org/SSDOptimization)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
Similar to what I do, except I do use ext4 , I use a daily cron task for TRIM, 
and I have Firefox on hard drive so no issues with cache. Swap is also on hard drive, but never used.
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by rmleloupjr on 2018-07-27
> **oldrocker99 said:**
> There are several social media apps for Linux. The best video editor is probably kdenlive. Look around, and install synaptic to make searching for files a lot more quickly and easily.

Been Exploring Kdenlive, looks epic.



> **oldfred said:**
> With my SSD, I do change a few default settings.

       [http://arstechnica.com/gadgets/2015/04/27/ask-ars-my-ssd-does-garbage-collection-so-i-dont-need-trim-right/](http://arstechnica.com/gadgets/2015/04/27/ask-ars-my-ssd-does-garbage-collection-so-i-dont-need-trim-right/)
Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.debian.org/SSDOptimization](https://wiki.debian.org/SSDOptimization)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
Similar to what I do, except I do use ext4 , I use a daily cron task for TRIM, 
and I have Firefox on hard drive so no issues with cache. Swap is also on hard drive, but never used.
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

Debated doing this, as i'm using a partition on my ssd separate from my initial windows install itself. That being said. If I went pure uBuntu etc, I'd jump on these options immediately.

Down the road i'll plan to do a dual boot SSD solution on my desktop, so I can best use ubuntu's performance features. (i5, 4670k @ 4.1ghz, 32gb ddr3/2400xmp, nvidia 760 2gb, X-Fi Z series pci-e, etc with triple 24" desk mount screens (Benq's).


For the social media app suggestions overall. I've seen there are tons of mixed apps. But trying to find a free all in one solution or mixed solutions overall. Just trying to not use excessive tabs if avoidable. I'm on one screen, 15.6" 1920x1080. It's nice, but. Trying to multi stream function.


For features of the old Fusion from Compiz. I'm trying to basically use the old multiple workspace solution idea's. Similar to that of the sphere, or cube rotation when switching to different sections. Used to have all those special effects in Ubuntu 9.04..... (not going that far back, this laptop might puke attempting to even use it with any drivers).

Been trying to google idea's on how to install compiz, or get an original copy of it and manually install the fusion features manually. Switch from Direct3d to Open GL or otherwise, so that I can activate everything correctly.

I'm a bit "new" / rookie when it comes to terminal. Again functionally capable of the Capital vs lower case, but just looking for alternate options.

I previously mentioned (pre edit) that i'm looking for themes, more towards feminize/pink options. Not sure where to look to do so as i'm a tad confused. Not sure if there is a program that automates installs separate from .deb easy installs, etc. Any support there, is greatly appreciated.

Thanks all,

- RMLeLoupJR

---

### Post by oldfred on 2018-07-27
You still need to make some changes to mount Linux partitions with noatime and a few other settings. Does not matter if dual booting or not. The Linux partitions need correct settings.

---

