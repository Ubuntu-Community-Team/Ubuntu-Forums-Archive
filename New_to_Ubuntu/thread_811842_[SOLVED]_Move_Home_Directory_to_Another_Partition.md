---
title: "[SOLVED] Move Home Directory to Another Partition"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by mapes12 on 2008-05-29
I'm looking to move my Home directory to another logical partition I have created on my HDD. I'm sure I saw a HOWTO the other day but when searching the forum I get an error page "Datbase Error". this is happening on 2 machines now. Does anyone have a hyperlink to the HOWTO or know how to do this please?

---

### Post by philinux on 2008-05-29
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Not sure if it's up to date?

---

### Post by Aesir09 on 2008-05-29
well how big are your home folders?

b/c a really quick idea i have is to just copy your home folder onto an ext drive or the other partition from a **live cd**?

sounds good to me

---

### Post by mapes12 on 2008-05-29
The /home directory isn't very big right now. Only a few MB's with some text files and my personal settings. I'm doing this on a test machine prior to deploying on my main machine and transferring in my photo's, mp3's etc of which there are LOADS!

I'm using an old PIII machine as a test bench to be sure whatever I deploy on my may machine doesn't screw things up. I'm also experimenting on backup routines so that I can backup my system files, /home stuff separately.

Once I'm confident I have a robust methodology to keep my Linux machine safe and secure my objective is to migrate all my stuff from my windoze machine to my main Linux machine and ditch windoze. But I need to be sure I can manage any disasters with the numerous utilities Linux provides. I can't afford to loose the stuff I have accumulated like years worth of family photo's etc.

Thanks for the replies guys.

Mark

EDIT: Currently, I keep 2 backup copies of my windoze stuff. One is your regular backup.exe and the other is a DriveimageXML image using the free utility from the folks at [www.runtime.org](www.runtime.org) - IMO much better than Ghost.

---

### Post by philinux on 2008-05-29
Having home on it's own partition makes reinstall a doddle.

In the  partition manager you just set root to be formatted and leave home as it is.

---

### Post by mapes12 on 2008-05-29
> Having home on it's own partition makes reinstall a doddle.

In the partition manager you just set root to be formatted and leave home as it is.

Exactly. I want the system files in a separate partition for this very scenario. My problem is that when I installed Ubuntu I put everything on the same partition. But, using Gparted Live CD, I have resized the original partition to create free space and then created a new ext3 partition on the free space.

My objective now is to move the /home directory from the original partition to the newly created one? I have read somewhere (but can't find it any more) that this is NOT just a cut and paste exercise.

Any help greatly appreciated.

Mark

---

### Post by sam_delta on 2008-05-29
check out those links, 

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/) <-------(i like this guide)
[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

it isnt too much trouble, you just have to backup your old home, then copy your data to your new partition mount your new partition as /home, edit fstab to make it automount, and run few commands to make ubuntu see/recognize your home (actual steps and order of steps @ the links above)

sam

---

### Post by philinux on 2008-05-29
I already gave you the link.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) :lolflag:

---

### Post by mapes12 on 2008-05-29
> I already gave you the link.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) 

Many thanks for the link.

I tried the code but ```
sudo mount -t ext3 /dev/hda1 /old
``` i.e. the second line of code came back with a bad command. The author states that the hda# needs to be replaced with the resized, new partition and destination hda#. Coincidently, my original /home directory is located at hda1 as in the command line. Unfortunately, this command results in a bad command output. I have cut and paste the text to avoid typo's.

BTW: the author does not say in which directory the user needs to be in with regarding to executing the command i.e. root, /home/user or whatever??

As you posted earlier, this tutorial is old. Therefore, is there something fresher that I'm missing?

---

### Post by mapes12 on 2008-05-29
> mark@ubuntu-laptop:~$ mkdir /mnt/newhome
mkdir: cannot create directory `/mnt/newhome': Permission denied


This was the result of the code at:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

I'm copying and pasting to avoid typos??????

The code just doesn't work.

---

### Post by sam_delta on 2008-05-29
to fix any permision denied problem, just run the command as "sudo"
ex
```
sudo <command>
```

in that specific case
```
sudo mkdir /mnt/newhome
```


sam

---

### Post by sam_delta on 2008-05-29
> **mapes12 said:**
> 
BTW: the author does not say in which directory the user needs to be in with regarding to executing the command i.e. root, /home/user or whatever??


it will work in any working directory because the commands you are typing contain full paths (paths starting from root) ex "/mnt/something" or "/home/user" commands with full paths will work in any working directory

sam

---

### Post by mapes12 on 2008-05-30
SOLVED

I followed this thread on both my desktop and my laptop and it worked! Had a few typos' in the process but /home is now on a separate partition.

[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

Thanks everyone.

---

### Post by sam_delta on 2008-05-30
no problem, enjoy ubuntu bro

sam

---

