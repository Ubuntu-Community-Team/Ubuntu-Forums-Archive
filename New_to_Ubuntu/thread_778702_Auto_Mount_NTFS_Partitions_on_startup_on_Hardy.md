---
title: "Auto Mount NTFS Partitions on startup on Hardy"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by JoyceBabu on 2008-05-02
For the past few hours I have been trying to automount my NTFS partitions on startup. I have tried several of the methods after googling. But none of them seems to work. Can someone plz guide me on how to do this? Thanks

---

### Post by aheckler on 2008-05-02
Have you tried this: [http://blog.csmonkey.com/2007/04/auto-mount-ntfsfat23-in-ubuntu.html](http://blog.csmonkey.com/2007/04/auto-mount-ntfsfat23-in-ubuntu.html)

---

### Post by Joeb454 on 2008-05-02
Make sure all NTFS drives are NOT mounted currently.

Search synaptic or add/remove for "ntfs-config" (without quotes ;)) or type/paste the following into a terminal ```
sudo aptitude install ntfs-config
``` both will prompt for a password.

Once installed - click Applications>System Tools and choose NTFS-Config.

Then I believe it's pretty straight forward :)

---

### Post by aheckler on 2008-05-02
Shoot, good idea Joeb454. I keep forgeting that tool exists :-P

---

### Post by Joeb454 on 2008-05-02
I always use it if I want to automount NTFS Partitions, it's easier to newcomers than editing fstab as well

---

### Post by aheckler on 2008-05-02
Does he need ntfs-3g before he installs ntfs-config or does ntfs-config install ntfs-3g as a part of itself?

---

### Post by Joeb454 on 2008-05-02
ntfs-3g has been installed as standard since Ubuntu 7.10 :)

---

### Post by aheckler on 2008-05-02
> **Joeb454 said:**
> ntfs-3g has been installed as standard since Ubuntu 7.10 :)

Well shizz, I've been using Ubuntu since Dapper, so you'd think I'd be up on the (not so) current developments but I guess not. :-P

---

### Post by Joeb454 on 2008-05-02
:lolflag:

I only know because it was in 7.10 automounting my Windows partition (for my music) got a whole lot easier ;)

---

### Post by aheckler on 2008-05-02
Yeah, I guess that would do it. I have my whole 80 GB drive solely devoted to Ubuntu, so I guess I wouldn't really notice...

---

### Post by JoyceBabu on 2008-05-02
Thanks a lot. That worked. :)

---

### Post by ankur.gupta on 2008-05-04
i installed ntfs-config and it ask for mount point....what is mount point please help i m new to ubuntu ( i m using ubuntu 8.04)

---

### Post by JoyceBabu on 2008-05-04
You just have to provide a folder name there. Don't give the full path, just the Folder name (You don't have to create the folder, it will automatically be created).

For example, if you are mounting the 'D:' drive, then you may give 'D' as the mount point. And your drive will be mounted to 
/media/D.

From what I know, traditionally drives and files systems were mounted to /mnt, but now they are mounted to /media so that they appear on your Desktop. Somebody plz correct me, if I am wrong. :)

Hope that helps. :)

---

### Post by ankur.gupta on 2008-05-04
thanks a lot

---

### Post by echris1 on 2008-05-07
> **Joeb454 said:**
> Make sure all NTFS drives are NOT mounted currently.

Thanks for the advice,this was preventing me from see the actual menu, I just got the option to configure external write access because I had already mounted my drives, but once you unmount them it works just fine.

Thanks again!

---

### Post by Jammerdelray on 2008-05-08
worked for me too, thank you!

---

### Post by ekss on 2008-05-09
thanx

---

### Post by JBA2337 on 2008-06-02
> **Joeb454 said:**
> Make sure all NTFS drives are NOT mounted currently.

Search synaptic or add/remove for "ntfs-config" (without quotes ;)) or type/paste the following into a terminal ```
sudo aptitude install ntfs-config
``` both will prompt for a password.

Once installed - click Applications>System Tools and choose NTFS-Config.

Then I believe it's pretty straight forward :)
I installed ntfs-config, as you suggested, but I do not fully understand how to use it. I have two drives on my computer that are partitioned as NTFS, and one of these partitions also contains an extended partition that contains my linux ext3 partition and a linux swap file.

When I tried to use ntfs-config, and I selected these two NTFS partitions, so that they will be auto-mounted  when I boot my computer, the ntfs-config program asks me for "mount points" for the two NTFS partitions. I never could figure out what to type in for mount points. 

I did get my two NTFS partitions to auto-mount, but I did it by manually editing the /etc/fstab file, as suggested in the following link.
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

In the /media folder I created two new folders, 
/media/windowsC and /media/windowsD. THen I edited /etc/fstab by adding the following lines:

/dev/sdb1 /media/windowsD ntfs-3g defaults,locale=en_US.UTF-8 0 0

/dev/sda1 /media/windowsC ntfs-3g defaults,locale=en_US.UTF-8 0 0

After I saved the modified fstab file, and after rebooting my computer, both of the NTFS drives were auto-mounted. 

THanks for your original suggestions; if I had not read it, I would not havesolved my problem.

JBA2337

---

### Post by qbanqba on 2008-07-15
Finally someone who remember was a linux newbie. Thanks

---

### Post by cika.mancic on 2008-08-14
Thanks!
Nice post...

---

### Post by krusher on 2009-11-03
try to use this soft called pysdm which automatially mounts the desired drives at startup so no more mounting em over and over again.

cmd to install it:
```

sudo apt-get install pysdm

```
after installing run it by```
sudo pysdm
```

---

