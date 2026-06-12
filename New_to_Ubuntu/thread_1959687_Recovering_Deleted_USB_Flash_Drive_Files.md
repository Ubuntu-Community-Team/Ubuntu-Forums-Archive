---
title: "Recovering Deleted USB Flash Drive Files?"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by marenkar on 2012-04-16
Hi,

So, in the interest of nostalgia and related emotions, I'm interested in possibly recovering files deleted files from my flash drive. So with that, I have a couple of questions:

1. If I deleted files from my flash drive and emptied trash, should recovery be targeted on the flash drive or the hard drive? 

2. I reformatted the flash drive at one point in time, will the files that existed before the reformatting (I think I probably deleted those files and emptied trash before I reformatted it) still be able to be recovered?

I don't think I wiped the flash drive though.

I should also point out that I've been using Ubuntu all this time.

---

### Post by evilsoup on 2012-04-16
When you delete files on a memory stick, they are not actually deleted but are instead moved to a .trashes directory on the memory stick. When you empty the trash, however, then they are properly removed. If you want to recover anything from there... well, I *think* it can be done, but really you are talking about professional data recovery services.

Since it's been reformatted (and presumably used since then)... well, do you have any friends in the FBI? Because I think even they would be out of luck. Sorry, I think your files are lost forever.

---

### Post by ronaldbrijo on 2012-04-16
You can use a data recovery program to scan the flash drive.

I found this thread:
[http://ubuntuforums.org/showthread.php?t=1312695](http://ubuntuforums.org/showthread.php?t=1312695)

---

### Post by audiomick on 2012-04-16
I think the program you are looking for is probably dd-rescue. Never used it, but I've followed a thread or two where people have recovered stuff that I would have thought was gone for good.

Your target is the flash drive.

I must say, I wouldn't be too hopeful. If you have been using the flash drive since you did the re-format, your chances are probably pot luck at best. If it hasn't been used since the re-format, you've got a look in at least.

Have a read here:
[https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")

---

### Post by Bashing-om on 2013-01-17
marenkar; and all -

Here is another, I have not tried it so can not vouch for it.

install scalpel in ubuntu in terminal
```
sudo apt-get install scalpel
```then run below step to recover your files
create a folder name lostdata
then:
```
sudo scalpel <path and drive> <options>
``` -o is used to genarate recovered files to folder lostdata
ie:
```
sudo scalpel /dev/sda1 -o lostdata
```note:there’s no guarantee that Scalpel will succeed in recovering your files, but at least there’s a chance.
[INDENT][INDENT]just my 2 pounds worth.

[/INDENT][/INDENT]

---

### Post by MyR on 2013-01-17
I've had success with recovering files using testdisk.  Very recently I used it to recover a partition table that windows made fubar.

It sounds to me like you should still be able to recover some files.

good luck!

---

### Post by mapes12 on 2013-01-18
+1 for Testdisk. You can also try Photrec.

---

### Post by Paqman on 2013-01-18
> **mapes12 said:**
> +1 for Testdisk. You can also try Photrec.

Photorec is part of the [testdisk]("apt:testdisk") package. So the package you install is testdisk, but the program you want for the job is photorec.

---

### Post by sudodus on 2013-08-02
> **Paqman said:**
> Photorec is part of the [testdisk]("apt:testdisk") package. So the package you install is testdisk, but the program you want for the job is photorec.
+1

---

### Post by Mark Phelps on 2013-08-08
Niilllysoly:  While it may be obvious to you -- you should have mentioned that your "fixes" only work running MS Windows -- and since this is an Ubuntu forum, not an MS Windows forum, that won't help anyone running only Ubuntu.

---

### Post by dj722000 on 2013-08-08
You can use testdisk and photorec. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) However, do note though, when you delete something from a disk or mem stick, then save to it after that, it is a very good chance that you wrote over what you deleted. Normally when you delete something and you want to recover it, you should immediately stop what you are doing and recover it so there is no chance of writing over it. However, there is chances that it has not been written over, maybe, this is where you are at currently and in some cases you can recover the files if it has not been written over. I recommend before doing anything, go on youtube and watch some videos of how testdisk and photorec work. There is some really good videos on it.

Also note, even though you formatted, there is still a chance you can recover it.

---

### Post by MyR on 2013-08-09
Please guys, this thread is over a year old.

---

### Post by alesterw on 2014-06-19
In case your files have been lost form your USB flash drive then try out Remo Recover it can easily help you out to get back deleted files from flash drive within a matter of seconds.

---

### Post by mark196 on 2015-02-12
You may try this [usb flash drive data recovery guide]("http://www.asoftech.com/articles/undelete-files-from-usb-drive.html"). It is easy to follow and can recover lost files from USB flash drive.

---

