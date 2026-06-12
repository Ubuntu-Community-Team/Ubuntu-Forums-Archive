---
title: "Ubuntu 14.04 LTS (unable to boot)"
date: 2015-07-08
forum: New to Ubuntu
---

### Post by wtkmichael on 2015-07-08
Hi,

Please help me with boot problem.I have tried the boot-repair but it didnt show me the "recommended repair" button. The only button i can see is :Summary"
The summary of boot repair @ [http://paste.ubuntu.com/11841487/](http://paste.ubuntu.com/11841487/)

Thank you.


screenshot
---------- base64 image snipped by sandyd----------

---

### Post by VMC on 2015-07-08
Did you do the boot-repair running the ubuntu-live? There's no grub.cfg file. 
Did this ever work, and what version ubuntu?

---

### Post by grahammechanical on 2015-07-08
Ubuntu is not installed. Ubuntu should be in sda1. 

Regards.

---

### Post by yancek on 2015-07-08
Did you accept the default options for Ubuntu during the install?  It does not appear your installation was successful.  The message that sda1 has an "unknown filesystem" is troubling as is the fact that the standard boot files on the partition do not appear.  Answers to the questions above by VMC should help.

---

### Post by wtkmichael on 2015-07-08
It's Ubuntu 14.04 LTS.
The Ubuntu is running fine for 6 months. And suddenly it can't boot. Therefore I tried to do boot repair but i not able to repair it since it show me the file system is unknown (as shown in screenshot)

Can help to analyze the error log @ [http://paste.ubuntu.com/11841487/](http://paste.ubuntu.com/11841487/)

---

### Post by VMC on 2015-07-08
Not sure what I'm looking at:```

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
```

Then further on it states:```
/dev/sda1 * 2,048 241,819,647 241,817,600 83 Linux
```

When grub menu comes up, if you push '**c**' you should see a  '**grub>**' prompt. You can investigate further. For example ```
ls (hd0,1)/
``` to see if sda1 is there.
See if you have grub.cfg file. type ```
ls (hd0,1)/boot/grub
``` from grub prompt to see if its really there. If it is, then ```
configfile (hd0,1)/boot/grub/grub.cfg
```should give some error or message if it doesn't boot.

Also while still using '**gurb>**' prompt, type '**set**' return. At the bottom it will show you where the grub boot partition is located.

---

### Post by sandyd on 2015-07-08
Instead of dragging the image to the post, please use the 'Manage Attachments' button near the bottom of the post while editing. Dragging the image onto the post causes the browser to convert the image to base64, which results in an unviewable image.

Thanks!

---

### Post by wtkmichael on 2015-07-09
Hi all,

Thanks for the replies.
I attached my picture again[ATTACH=CONFIG]263100[/ATTACH]


when i tried to boot.. it shows me :
[B][I]Loading Operation System ...
error : unknown filesystem.
Entering rescue mode...
grub rescue> ls
(hd0) (hd0,msdos5) (hd0,msdos1)[/I][/B]

---

### Post by VMC on 2015-07-09
From that picture something remove linux filesystem from sda1. From a terminal does '**sudo fdisk -l**' show the same thing? It should.

---

### Post by wtkmichael on 2015-07-09
> **VMC said:**
> From that picture something remove linux filesystem from sda1. From a terminal does '**sudo fdisk -l**' show the same thing? It should.
i've been using my ubuntu for more than 6 months without problem. The hard disk (ssd) only installed with Ubuntu. Attached is the screenshot. 
[ATTACH=CONFIG]263104[/ATTACH]

---

### Post by oldfred on 2015-07-09
Did you have an abnormal shutdown or force shutdown? That can cause file corruption.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

---

### Post by wtkmichael on 2015-07-10
> **oldfred said:**
> Did you have an abnormal shutdown or force shutdown? That can cause file corruption.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

[ATTACH=CONFIG]263113[/ATTACH]

sudo e2fsck -f -y -v /dev/sda1

Thanks!! I am now able to boot! 
Thanks

---

