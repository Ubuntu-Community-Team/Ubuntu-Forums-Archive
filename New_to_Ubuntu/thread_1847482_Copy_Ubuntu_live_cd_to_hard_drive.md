---
title: "Copy Ubuntu live cd to hard drive?"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by jacknet52 on 2011-09-20
It has been recommended that I copy my cd to the hd for purposes of using MD5Sum. I'm running Ubuntu from a cd because the install blew up ( read/write errors ) and I don't know what it does after that but I'm using it right now as some kind of trial I guess. So can I copy the cd I'm working off of to my hard drive? How please? Use terminal or gui? And then use this program I'm in to run the md5sum? Thanks for your patience. Jack

---

### Post by alphacrucis2 on 2011-09-20
I think you are supposed to use the md5sum to verify the iso file that you originally downloaded before burning the cd from it. So copying the CD to disk would be a bit pointless. You could probably recreate the iso from the CD by doing a create iso CD image type function. Under windows, something like Nero can probably do that.

---

### Post by wildmanne39 on 2011-09-20
Hi, it sounds like you may have bad sectors on your hard drive, I would check that first.

Does the cd you are using have an option on the desktop to install it? if so then you can use it, if not then you can go to this link and download ubuntu and follow the directions on the download site to burn the download to disk, it can not just be copied to disk.
[http://www.ubuntu.com/](http://www.ubuntu.com/)
Thank you

---

### Post by jacknet52 on 2011-09-20
I'm defragging through windows right now. Don't know if that will indicate bad sectors or not and if that is the problem. Let me elaborate: I have 2 cd's One I created off the Ubuntu website and the other from a brand new book "Ubuntu Unleashed". Two reliable cd's I would imagine. One is 11.04 other is 10.10. Last week I did a complete install off the 11.04 and it worked fine. This week I tried a complete install and it crashed. It told me so. Then I tried the other (10.10) Same result. So then I loaded my win7 back up and tried to do a side by side install with both of them again. Same result. Read/write errors according to the dmesg file. So it seems to be hardware but wouldn't the fact that win7 loaded fine tell me it's not? By the way when it crashes it runs off the cd almost like a complete install but is self contained on cd.
addendum: Defrag completed fine. Does that indicate bad sectors?

---

### Post by wildmanne39 on 2011-09-20
Hi, windows running could just mean the error is not on the windows partition.

Defrag will not tell us if there are bad sectors.

From liveCD so everything is unmounted,swap off if necessary, change sdb6 to your 
partition(s)
```
sudo e2fsck  -p -f -v /dev/sda6
```
Thank you

---

### Post by David Andersson on 2011-09-20
> **jacknet52 said:**
> It has been recommended that I copy my cd to the hd for purposes of using MD5Sum. 

Where was that recommended?

If you want the md5sum of the iso-file from which you burned the live-cd you are currenty running, this might work

```
md5sum /dev/sr0
```

(No need to copy it for that.)

---

### Post by jacknet52 on 2011-09-20
Hi, windows running could just mean the error is not on the windows partition.
Well apparently Ubuntu did partition my hd during the attempted install. My win7 is showing only half of my disk which is what I told it to do. I just don't understand the r/w errors when it worked fine a week ago off the same cd.
Here is some more History:  It worked great for about a week and I took it to the library where I work and had it hooked up to the public server unattended mostly for a whole day and I think someone hacked in messed up all my files because I couldn't access using sudo or anything. So I decided to just wipe the HD and reinstall complete, I hadn't really saved much. I know there are better ways to fix it but I just wanted it to work again and took the easy way out. 

From liveCD so everything is unmounted,swap off if necessary, change sdb6 to your 
partition(s)
I'm sorry wildmanne but I don't understand the above. You're saying I can run this command from the cd and then...Sorry for my newness to this.
Code:
sudo e2fsck  -p -f -v /dev/sda6

---

### Post by wildmanne39 on 2011-09-20
Hi, let's clarify, are you getting errors when trying to boot from ubuntu on your hard drive? Or are these errors from the cd?
Thank you

---

### Post by jacknet52 on 2011-09-20
@wildmanne39 - I go in my bios and set it to boot from the cd. The ubuntu installer comes up. I go through all the pre-install process including partitioning. Ubuntu now says it's going to copy files. It copies for at least 5 to 8 minutes and then I get this error:
Installer crashed; were sorry the installer crashed. Please file bug report at [https://launchpad.net/ubuntu/+source/ubiquity/+filebug](https://launchpad.net/ubuntu/+source/ubiquity/+filebug) ( do not attach your details to any existing bug) and a developer will attend to the problem asap...
Then: I hit close and I get another message: Install Failed. The installer encountered an ...error ya da, ya da. I hit continue and get: System program problem detect. And it went on and on and finally it loads a desktop and is running off the cd. So I think I can do the md5sum from there correct, once I mount it?????

---

### Post by wildmanne39 on 2011-09-20
Hi, are you trying to install 11.10 by any chance? I would go with 10.04 for now.
Thank you

---

### Post by egalvan on 2011-09-21
When you boot a LiveCD, there is an option to 

"check media for error"

this will run checksums on the complete cd...


There is also an option to 

"check memory for errors"

this will run memtest86, and report bad RAM..

n.b. the wording on the options may vary a bit, but you will recognize them...

---

### Post by jacknet52 on 2011-09-21
Hi Fellows - I'm burning a new DVD and I'm going to burn it slow. I hope this solves all problems. I took those other 2 cd's to work today and tried them both on other machines and had problems with both. I really want to thank all who gave me suggestions the last two days. You deserve a special note of gratitude for all the hours you put in helping us new folks. I'll be back later with a new thread and if all goes well I'm sure I'll be back when I hit something else I can't figure out. I do look for solutions first before attempting to take up your time. Take Care, Jacknet

---

### Post by wildmanne39 on 2011-09-21
Hi, good luck!

---

