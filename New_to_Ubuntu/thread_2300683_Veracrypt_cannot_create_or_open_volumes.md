---
title: "Veracrypt cannot create or open volumes"
date: 2015-10-27
forum: New to Ubuntu
---

### Post by thomas58 on 2015-10-27
Hello,

I am running Lubuntu 15.10 on an IBM Thinkpad T43 with 1.5GB RAM, a 1.86GHz Intel Pentium M processor, and a 40GB HDD.  I just installed Veracrypt 1,14-Ovanir1 15.10 via PPA using the following commands:

$ sudo add-apt-repository ppa:unit193/encryption
$ sudo apt-get update
$ sudo apt-get install veracrypt

I am new to Ubuntu and may have done something wrong, for when I try to create an encrypted volume I get a message that says, "VeraCrypt Error:  Failed to get file system statistics (Error 2: No such file or directory)."  This error appears on the Volume Size page with the text, "Free space available: 0 B."  This message is in spite of the fact that the File Manager shows there are 22.9GB of free space on the HDD.

I get a different error message when I try to mount a Veracrypt container created on another computer.  In this case the message reads, "fuse: bad mount point 'MESSAGES/libc.mo': No such file or directory."

I would greatly appreciate it if anyone can tell me how to fix whatever is wrong here.

Thanks in advance for any help.

---

### Post by Vladlenin5000 on 2015-10-27
The version in that PPA is 1.14 and the latest available is 1.16. That said, it shouldn't make a difference. I just mentioned it because I see no point in using a PPA for VeraCrypt. More a of that later*.

1. The first error has been reported occasionally since the old TrueCrypt. Apparently you haven't select a location for your encrypted file. Full path is required. 
2. The second error is weird. Are you sure it is a VeraCrypt volume an not a similar one created with the old TrueCrypt? 


* I installed the version from the [official website]("https://veracrypt.codeplex.com/wikipage?title=Downloads") and tested it by creating a file in an external NTFS formatted disk (the worse case scenario), then opened it and everything worked as expected.

---

### Post by thomas58 on 2015-10-28
Hi Vladlenin5000,

Thanks for the reply and for the solution to the first error; I'd neglected to specify the full path for the encrypted volume.

Having done that, I was able to create an encrypted volume.  But when I tried to mount it, I got the same error message as when I tried to mount the volume that I'd created on the other computer.

I'll go looking for a tutorial on how to install an application from a .tar.bz2 file and try the 1.16 version from the Veracrypt website.

---

### Post by Vladlenin5000 on 2015-10-28
No need for a tutorial... :p
(It's just a compressed file; what matters is what's inside)

First you should remove the version you already installed:
```
sudo apt-get purge ppa:unit193/encryption
```
should be enough.

Then download and extract somewhere (double-click will open the native tool; click "extract"). You'll obtain 4 files, GUI and console only versions for both 32bit and 64bit (you want GUI matching your OS architecture). Just double-click the proper file, run or run in console (the latter is preferable, just in case) and follow instructions. The installation - surprisingly or perhaps not - is identical to the old TrueCrypt in every detail.

---

### Post by thomas58 on 2015-10-28
Vladlenin5000,

Thank you so much for your help.  I'd been researching how to install from .tar.bz2 files and it was looking pretty complicated.  By following your instructions I got the Veracrypt 1.16 version installed.  It successfully mounted both of my encrypted containers, so perhaps the problem was with the 1.14 version.

Anyway, all is good now and I really appreciate your assistance.

---

### Post by Vladlenin5000 on 2015-10-28
You're welcome. :p

Yes, the problem was most certainly with the 1.14 version _in that PPA_. Just guessing because I haven't tested the 1.14 from their website before.

Please use the thread tools to mark this one as solved so future forums users may benefit as well.

---

