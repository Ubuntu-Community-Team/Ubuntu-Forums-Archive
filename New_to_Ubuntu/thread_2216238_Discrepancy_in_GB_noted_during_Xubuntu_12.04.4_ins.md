---
title: "Discrepancy in GB noted during Xubuntu 12.04.4 install"
date: 2014-04-10
forum: New to Ubuntu
---

### Post by elvis6 on 2014-04-10
I have a PC with Xubuntu version 13.10 currently installed.
It used about 5 GB of hard disk space.
Then I went to attempt to install Xubuntu version 12.04.4, to replace the other version, and at the beginning of the install, it said that it would need and use only about 5GB of space, as well. I chose the option for a full install (not to tryout) and I chose the option to wipe the hard disk clean during the install. But then, a few steps later, the screen says it will use about 83 GB of space !
I had to quit the install, because I do not even have 83 GB of space.
How and why did it go from saying it needed 5 GB, to needed 83 GB, during the same install ?

---

### Post by Impavidus on 2014-04-11
5GB of hard disk space seems reasonable as a lower limit. That's about the size of a default system. If you want to install some additional software or want to actually do something with your computer you'll need a bit more, but with 20GB you should be able to get a decent system.

83GB on the other hand is ridiculous. Unless you somehow opt to install about every piece of software available from the repos. So if you just install the system and don't ask to install any additional software or updates, how much disk space does it want?

---

### Post by mcduck on 2014-04-11
Are you absolutely sure it wasn't, for example, saying it's going to format a 83GB partition or something like that? Since I'm quite sure there isn't anything at that point of install telling you how much space it's exactly going to use...

---

### Post by elvis6 on 2014-04-11
> **Impavidus said:**
> 5GB of hard disk space seems reasonable as a  lower limit. That's about the size of a default system. If you want to  install some additional software or want to actually do something with  your computer you'll need a bit more, but with 20GB you should be able  to get a decent system.

83GB on the other hand is ridiculous. Unless you somehow opt to install  about every piece of software available from the repos. So if you just  install the system and don't ask to install any additional software or  updates, how much disk space does it want?
> **mcduck said:**
> Are you absolutely sure it wasn't, for example, saying it's going to format a 83GB partition or something like that? Since I'm quite sure there isn't anything at that point of install telling you how much space it's exactly going to use...

So, here is what each screen says. I figured it'd be easier for you all to answer my question, if you could see what I see.

_**1st Screen options -**_ 2 Choices  -Try Xubuntu or Install Ubuntu
                            I chose to Install Xubuntu
_**2nd Screen -**_ "For best results, please ensure the computer has at least 4.3 GB of available drive space,
                   and is able to connect to the internet'
                  "Xubuntu uses third-party software to display Flash, MP3, and other media to work some wireless hardware"
                  I checked the above option to install the 3rd-party software.
_**3rd Screen -**_ 2 Choices : 
                  a) "Erase disk and install Xubuntu"        
                  b) "Something else : can create or resize partitions yourself or choose multiple partitions for Xubuntu"
                  I chose the 1st option, to erase disk and install
_**4th Screen -**_ "Select drive" and there is a drop-down menu for the drive with just one choice, named "SCSI1 (0,0,0) (sda) 82.3 GB ATA HDS728080PLAT20"
                  Under that, it says :
                  "The entire disk will be used
                   Xubuntu
                   /dev/sda (ext 4)
                   82.3 GB"
                  Underneath that, it says :
                  2 Partitions will be deleted. Use the advanced partitioning tool for more control"

So, I'm a little unclear about that 4th screen. On one hand it says, the entire disk will be used, followed by 82.3 GB statement.
I do know my hard drive has something in the neighborhood of 82 Gigs. When I checked properties currently, it says 69.4 of 80.2 GB are bing used.
So, I'm not sure if it is telling me that the whole software is actually 82.3 GB, or if it's just saying that it detects about 82.3 GB of space on my drive.
It is not clear at all, due to the lack of description on the screen.
Can any of you elaborate ?
I'm afraid that if it does indeed take up 82.3 GB, it may freeze up my whole PC, from being full, unless I'm wrong about that.
So, I'm a little scared to attempt the install. Or is it safe to do so ?

---

### Post by Impavidus on 2014-04-11
In the fourth screen it's just informing you that it will use the entire disk to create new partitions. The 5GB is the amount of data it has to write and therefore the minimum amount of disk space you have to allocate to Ubuntu. In the fourth step it informs you that you allocated the entire drive to Ubuntu, wiping two existing partitions. This is fine. The installer will just wipe the drive and then create some largely empty partitions with an Ubuntu install.

---

### Post by elvis6 on 2014-04-12
> **Impavidus said:**
> In the fourth screen it's just informing you that it will use the entire disk to create new partitions. The 5GB is the amount of data it has to write and therefore the minimum amount of disk space you have to allocate to Ubuntu. In the fourth step it informs you that you allocated the entire drive to Ubuntu, wiping two existing partitions. This is fine. The installer will just wipe the drive and then create some largely empty partitions with an Ubuntu install.

Thank you very much, sir !
Your interpretation of that, gave me the peace of mind to proceed with the installation, which was a success !
Case solved !

---

### Post by Impavidus on 2014-04-12
Good. Can you mark this thread as solved? Go to thread tool (top of the page) &#8594; mark as solved.

If you have any problems with your installed system feel free to start a new tread.

---

