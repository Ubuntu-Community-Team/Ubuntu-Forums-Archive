---
title: "I have installed Ubuntu, but my MBR commited suicide"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by eemitchell24 on 2008-08-01
Hi,
   I am a very new newbie. I have installed Ubuntu 8.04, but when I restarted I received the Grub Error 22. (It also mentions Stage 1.5 which i did not see in the Grub directory when I looked.) I believe that this is an MBR problem and not a linux or Grub problem. 

I have tried several threads of advice on this problem from past forums.

Background:

HP Pavilion Laptop 
 120 HD (x2)
   HDA1 = Windows Vista Ultimate
   HDA2 = Win Recovery Partition

   HDB1 = Root (3.5 Gb)
   HDB2 = Swap (2.0 Gb)
   HDB3 = Boot (3.4 Gb)
   HDB4 = Home (35.0 Gb)
rest of HDB is unused (about 75 Gb)

Solutions I have tried:

    #1 From Ubuntu Live CD Terminal- "find \boot\grub\stage1" & also with   "Stage2"

Error message I receive is "find: bootgrubstage1: No such file or directory"

(I have no idea what any of that means, I was just trying the solutions that have worked for other people)

    
 #2 I have also tried from Win 98 SE CD-   "a: fdisk \mbr"

The Error message is "not fixed disks(or maybe it was "fixed  drives) found"

So, I think my question is how do I fix the MBR or replace it so that I can access both Vista and Ubuntu. Any help would be greatly appreciated

---

### Post by primolarry on 2008-08-01
You have some solutions there:

[http://ubuntuforums.org/showthread.php?t=876726](http://ubuntuforums.org/showthread.php?t=876726)

Regards,

---

### Post by sharks on 2008-08-01
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Malac on 2008-08-01
> **eemitchell24 said:**
> 
 
#1 From Ubuntu Live CD Terminal- "find \boot\grub\stage1" & also with "Stage2"
 
Error message I receive is "find: bootgrubstage1: No such file or directory"
 
(I have no idea what any of that means, I was just trying the solutions that have worked for other people)
 
 
You used the wrong slash in your find statement.
\ is used by windows / is used in linux.
Try the commands again using : find **/**boot**/**grub**/**stage1
 
Hope this helps.

---

### Post by eemitchell24 on 2008-08-01
I changed my slashes to the correct type but I still received the same result. That is the kind of mistake that I was very likely to make. I wish it had been that easy.

Thank you

---

### Post by sharks on 2008-08-01
boot ubuntu live cd , open terminal . type:> sudo grub
find /boot/grub/stage1

---

### Post by eemitchell24 on 2008-08-01
I have tried
               sudo grub
               find /boot/grub/stage1
I am now receiving "error 15: file not found"

What is an error 15, besides the obvious "file not found". 

When I started to install Ubuntu last night the first copy that I used was a bad copy. I replaced it with a good copy and Ubuntu 8.04 installed properly. I think that the first bad disk killed my MBR, It is very possible that I am not understand some of the advice being given here, but is reinstalling Grub going to help me if my MBR _really_ is corrupted? Maybe I have ask the wrong question before and I should be asking is there anyway to fix the MBR file from linux? 
    If I have got this wrong, please someone explain it to me.

---

### Post by Malac on 2008-08-01
Okay from the LiveCD have you mounted your ubuntu partition?
 
My method:
Boot LiveCD to Desktop
Open a terminal
```
sudo su
mkdir /mnt/ubuntu
mount -t ext3 /dev/[COLOR=gray]*<whatever-your-harddisk-is*[/COLOR][COLOR=black][COLOR=gray]*>*[/COLOR] /mnt/ubuntu[/COLOR]
grub
 
grub>find /mnt/ubuntu/boot/grub/stage1
 
[COLOR=gray]*will hopefully find it and give (hd*[COLOR=black]**_**[/COLOR]*,*[COLOR=black]**_**[/COLOR]*) with numbers where the '*[COLOR=black] **_**[/COLOR]* ' are*[/COLOR]
 
[COLOR=black]grub>root([COLOR=#808080]*hd*[/COLOR][COLOR=black]**_**[/COLOR][COLOR=#808080]*,*[/COLOR][COLOR=black]**_**)[/COLOR][/COLOR]
 
[COLOR=black]grub>setup([COLOR=#808080]*hd*[/COLOR][COLOR=black]**_**[/COLOR][COLOR=#808080]*,*[/COLOR][COLOR=black]**_**)[/COLOR][/COLOR]
 
[COLOR=black]grub>quit[/COLOR]
```
 
This last step shouldn't be needed but sometimes it is.
 
```
grub-install [COLOR=#808080]*hd*[/COLOR]**[COLOR=black]_**[/COLOR][COLOR=#808080]*,*[/COLOR][COLOR=black]**_**[/COLOR]
```
 
Hope this helps.

---

### Post by billgoldberg on 2008-08-01
Use the "super grub disk" live cd.

Using that you can access your windows and ubuntu installation.

You can also use it to repair the grub.

The live cd can be downloaded [here]("http://www.supergrubdisk.org/index.php?pid=5").

It's a must have for any dual booter.

---

### Post by louieb on 2008-08-01
Since you have a separate boot partition.  The find command should be.
```
find /grub/stage1
```BTW  200MB is plenty of space for /boot.  and 3.4GB is really on the low side for / (root). Might what to think about doing a reinstall and doing away with /boot - the only time you need one is on older machines that get a GRUB error 18. Or redo the partitions and give / (root) 3GB or so from /boot

---

