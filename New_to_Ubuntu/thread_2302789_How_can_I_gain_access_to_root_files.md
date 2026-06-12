---
title: "How can I gain access to root files?"
date: 2015-11-13
forum: New to Ubuntu
---

### Post by chris-burmajster on 2015-11-13
I just want to see them.

Chris

---

### Post by QIII on 2015-11-13
Hello!

How would you define "root files"?  What do you want to look at?  The kernel source?  System configuration?

---

### Post by chris-burmajster on 2015-11-13
No, I just want to see some files that I backed up.

---

### Post by Lars Noodén on 2015-11-13
Retrieving the files depends on how they were backed up.  Which method did you use to backup your files?

---

### Post by oscarivera9 on 2015-11-13
To gain access and to look at system files are two different things.  There are ways to look at them without having access to them.
Do you simply want to look at hidden files? that procedure is very simple
also, where did you back up to?

---

### Post by buzzingrobot on 2015-11-13
> **chris-burmajster said:**
> No, I just want to see some files that I backed up.

"sudo ls" in a terminal in the appropriate directory will list the contents.

If you copied/backed up files to a location you have rights to modify, then you should not need the authorization boost that sudo provides.

---

### Post by chris-burmajster on 2015-11-14
I backed up the contents and would like to see them.

---

### Post by Lars Noodén on 2015-11-14
> **chris-burmajster said:**
> I backed up the contents and would like to see them.

Which command or program did you use specifically?  Please post it here so we can tell you where to look.

---

### Post by matt_symes on 2015-11-14
Hi

> **chris-burmajster said:**
> I just want to see them.

Chris

> **chris-burmajster said:**
> No, I just want to see some files that I backed up.

> **chris-burmajster said:**
> I backed up the contents and would like to see them.

You've repeated yourself three times and supplied no extra useful information.

If you want help, you'll need to supply far more information.

I would start by addressing Lars' question in the post above this one.

Kind regards

---

### Post by chris-burmajster on 2015-11-15
I used the backup supplied in Ubuntu. I backed up my files and now that I have restored them I would like to see them. I have copied them into my 2Gb drive, which is not where they were from.

---

### Post by grahammechanical on 2015-11-15
Where did you restore those files to? They should all be in the folder you extracted them to and they should be the normal type files that we access in the normal way. If we use the backup tool that comes with Ubuntu (Backups or DaJa Dup) then the backup file is an archive file. And we can use the same tool to manager the archive.

[http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/](http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/)

And then there is Archive manager or File Roller

[https://help.ubuntu.com/community/File%20Roller](https://help.ubuntu.com/community/File%20Roller)

But once we have extracted or restored the files we can work with them in the normal way. Well, that is my understanding anyway. And all this is something completely different from what might be called "root files."

Regards.

---

### Post by chris-burmajster on 2015-11-16
I restored the files to the 2Gb drive. That's the drive that I can see. The folder 'Chris' is not accessible. I would like to make it accessible.

---

### Post by yancek on 2015-11-16
You need to check who the owner of the files and the permissions on them.  Depending upon how you backed them up, you may have only root permissions.  Your posts are all too cryptic for anyone to give anything more than general suggestions.

---

### Post by leunam12 on 2015-11-16
How are you trying to access the folder 'Chris' and what happens when you try to access it? Are you getting an error message? With the 2GB drive still connected open a terminal and type lsblk and then press enter and copy the results and paste it here. Then we'll go from there.

---

### Post by Vladlenin5000 on 2015-11-16
I wonder if [this]("http://ubuntuforums.org/showthread.php?t=2302306&p=13389210#post13389210") is somehow related... 2GB suggests either a SD or USB flash. The destination drive/partition/folder shouldn't matter. Perhaps the user could, at last, explain exactly what has been done and answer the questions...
Not keeping my hopes high though because [cryptic/unintelligible]("http://ubuntuforums.org/showthread.php?t=2302054"), [unanswered/abandoned]("http://ubuntuforums.org/showthread.php?t=2301704") or [nonsensical]("http://ubuntuforums.org/showthread.php?t=2287513&p=13324227#post13324227") threads seem to be a constant with this user. Actually, [this]("http://ubuntuforums.org/showthread.php?t=2287513&p=13324227#post13324227") is the only post I could find that makes sense (sort of) and the following [post]("http://ubuntuforums.org/showthread.php?t=2270606&page=2&p=13263713#post13263713") in the same thread is spot on...

---

### Post by chris-burmajster on 2015-11-17
I'm sorry, I suffered a stroke in July, and it's affected my English. The folder is marked ROOT and I get an error message saying that I have no permissions. This is why I want help. Here is the terminal output: NAME                  MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                     8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1                  8:1    0   243M  0 part /boot
&#9500;&#9472;sda2                  8:2    0     1K  0 part 
&#9492;&#9472;sda5                  8:5    0 931.3G  0 part 
  &#9500;&#9472;ubuntu--vg-root   252:0    0 915.3G  0 lvm  /
  &#9492;&#9472;ubuntu--vg-swap_1 252:1    0    16G  0 lvm  [SWAP]
sdb                     8:16   0   1.8T  0 disk /media/chris/2GB Drive
sr0                    11:0    1  1024M  0 rom

---

### Post by buzzingrobot on 2015-11-17
> **chris-burmajster said:**
> sdb                     8:16   0   1.8T  0 disk /media/chris/2GB Drive

[B]
ls -l /media/chris[/B] in a terminal will show who owns the "chris' folder

If that is not you -- your user name -- then you can change the ownership of the folder and the files inside it.

Assuming your user name is 'chris', then this:  **sudo chown -R chris:chris /media/chris** will make 'chris' owner of the folder and its contents.

---

### Post by chris-burmajster on 2015-11-17
Thank you, buzzingrobot!

---

