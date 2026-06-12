---
title: "reinstalling Ubuntu on dual boot/can't make Windows system restore disc"
date: 2014-01-28
forum: New to Ubuntu
---

### Post by snail2 on 2014-01-28
Hi, new to the forums but not to Ubuntu, still have limited experience. Installing Ubuntu on an old laptop I had once gave it a few more years of usability when it was too slow to run Windows even after a clean install, and my general experience with Ubuntu has been that it made older machines run better. It's the only OS on the laptop I own now (which is also old and unfortunately dying), and I really like it in general. When I was allowed to take an old tower that was being discarded at an office where I volunteer, I wanted to put Ubuntu on it too, but didn't want to erase the Windows XP already on it, so I decided to try making it dual-boot. In my infinite lack of wisdom I did not think to try making a recovery disc beforehand, and it was only after the Ubuntu installation went bad- it boots up but it's exceedingly slow and a little glitchy- that I realized I *couldn't*. The XP recovery disc program will only back the OS up to floppies and while I did actually manage to get ahold of some, the floppy disk drive seems to be broken. It has a functional CD drive.

The problem with the Ubuntu partition, I think, is honestly that it installed wrong. I used a USB stick, and this same USB stick did a buggy install on a different computer without partitions. Failing that, however, I'd suspect I didn't make the partition big enough. What I want to do is attempt to make a functional Ubuntu partition. I see several paths to this goal, each with different problems. 

1. Make a recovery disk, wipe and start from scratch
Requires a method of making or procuring a recovery disc. As stated previously, this computer does have a working CD drive, so I might just need some program other than the Windows default to make a recovery disc. I've seen programs that can make copies of the hard drive, but I'd assume those would also copy the bad Ubuntu partition? Or can you specify? An ideal solution would allow me to get rid of the Ubuntu partition AND give that disk space back to Windows.

2. Fix faulty Ubuntu partition
It's running sluggishly, failing to open or closing some windows, and sometimes freezing. Either the installation was borked, it's too small, or both. I'm reluctant to make it bigger unless there's an easily reversible way to do that, because so long as the Ubuntu partition doesn't work that's just eating space. I have been given the impression that just trying to reinstall will leave me with *three* partitions: the Windows one, the messed up one and a new one. If I'm wrong please correct me? Otherwise I really don't have a clue how to go about this. Downloading things on the Ubuntu side is nigh impossible because it goes so slowly.

3. Completely fresh installation of Windows OS, wiping everything else off
Requires an installation CD I don't have and don't especially want to pay for. If there's some place to get one for very cheap, let me know, but otherwise this is a terrible option. Alternatively I guess I could pirate Windows XP, but I'd prefer to find a legal (and safe) solution.

4. Completely fresh installation of Linux OS, wiping everything else off
seems like a waste when XP side works and is a useful thing to have.

If anyone has any advice I'd greatly appreciate it. Thank you in advance.

---

### Post by oldfred on 2014-01-29
You mention old laptop & Ubuntu. That may not be the best combination.
But I do run full Ubuntu 12.04 on my 6 year old laptop with 1.5GB of RAM and default Intel Video. But I do not use Unity as it needs a lot of video horsepower, so I install fallback/flashback or whatever it is called now.

Usually better to install Lubuntu on older systems as that is a lighter weight system by default.

These are Windows backup tools.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Newer Windows usually can be backed up a bit better with Windows tools. But XP may backup with Linux tools also.

 Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
fsarchiver
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page) 

If you reinstall with Something Else or manual install, you can choose to overwrite an existing partition. I always partition in advance with gparted as I do not trust the auto install options. So I create my partitions with gparted and then use Something Else to format and mount partitions.

      
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by snail2 on 2014-01-29
This is a very thorough answer! Thank you! The GParted tutorial is useful in general as well. I will try backing up with Macrium, then attempt to overwrite the current Ubuntu installation. The computer this particular scenario involves is a Compaq Evo D310, not the old laptop I mentioned (which finally died after 4 1/2 years), but being a very old tower it could probably benefit from the use of Lubuntu instead of Ubuntu as well.

If it works I'll say so and close the thread, if not I'll say what went wrong. It may take me about a week to get everything done though.

---

### Post by snail2 on 2014-02-06
Sorry I'm late! This solution worked perfectly, though I'd also like to note that lubuntu gives the option to install over one pre-existing partition while leaving the other alone. Closing the thread now. Thanks!

---

