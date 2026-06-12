---
title: "Unable to boot windows 7 after trying to install ubuntu 12"
date: 2013-02-11
forum: New to Ubuntu
---

### Post by edu4rd on 2013-02-11
Hi ,

As i mentioned in title i was trying to install ubuntu from a live cd ( I`ve burned the iso on USB stick ) .

You know you have the option the try or to install ,i hit install and the by "mistake" i clicked the option named : Something else because 1st option was about to delete all my windows files.

After i ve clicked on Something else i knew something wrong is about to happen and then i`ve click quit ,i did not hit install ,i know i have connected to wifi and then asked me about my location and i pressed Quit .

Tried to boot my windows ...but there was no windows to boot .
I have so many data on my hdd and i dont want to lose it .

When i use the gpart i get this : see attachement .

I dont know how is possible to mess my whole other partitions .

Thank you and i`m waiting for your instructions .

I will try testdisk in a moment .

but i dnno witch partition to select : 

Select a media (use Arrow keys, then press Enter):
>Disk /dev/sda - 1000 GB / 931 GiB - TOSHIBA MK1059GSM  (this is my HDD ) 
 Disk /dev/sdb - 4001 MB / 3816 MiB - Verbatim STORE N GO
 Disk /dev/mapper/ubuntu-root - 991 GB / 923 GiB - TOSHIBA MK1059GSM
 Disk /dev/mapper/ubuntu-swap_1 - 8531 MB / 8136 MiB - TOSHIBA MK1059GSM
 Disk /dev/dm-0 - 991 GB / 923 GiB - TOSHIBA MK1059GSM
 Disk /dev/dm-1 - 8531 MB / 8136 MiB - TOSHIBA MK1059GSM

---

### Post by Mopar1973Man on 2013-02-11
Apparently from the screen shot there is no windows partition left. Look like you told the Ubuntu installer to use the entire drive which it did and over-wrote the windows partition.

---

### Post by black3agl3 on 2013-02-11
Very sorry to say this but from your screenshot, it seems you just simply deleted your windows partition. Might be possible to recover data from it but this is beyond what i've been through...

And it would help if you could give a numbered list of the things you did, one after the other. Leaving out details like  "something wrong is about to happen" would allow people to focus on what you did exactly.

> 
You know you have the option the try or to install ,i hit install and  the by "mistake" i clicked the option named : Something else because 1st  option was about to delete all my windows files.

You chose "Something Else" from the install screen? Wasnt there an option "Install Ubuntu and windows side by side" by any chance?

> After i ve clicked on Something else i knew something wrong is about to  happen and then i`ve click quit ,i did not hit install ,i know i have  connected to wifi and then asked me about my location and i pressed Quit  .
Just clicking on "something else" would not have deleted your windows partition. Did you actually do anything else?



/dev/sda Was this the drive windows was on?
/dev/sdb What is this one actually? Didnt see it in your screenshot?

---

### Post by psilentrain1 on 2013-02-11
The Ubuntu partition is using 931GB, only 245MB unallocated, with no other partitions. If there is no other drive, your Windows was overwritten. Sorry.

---

### Post by grahammechanical on 2013-02-11
The USB memory stick is sdb. My guess.

It is also my guess that Windows 7 was using up the allowed 4 primary partitions. In this case the Installer cannot offer to Install Alongside. It most probably means that the Do Something Else option cannot allow the creation on new partitions (which it needs to do) without deleting some other partition/partitions. This does not happen without notification.

Regards.

---

### Post by black3agl3 on 2013-02-11
> **grahammechanical said:**
> 
It is also my guess that Windows 7 was using up the allowed 4 primary partitions.

Ouch. Never known anybody who uses 4 partitions for windows only.

Just a question. The 4 primary partitions limit is per drive?

---

### Post by grahammechanical on 2013-02-11
> The 4 primary partitions limit is per drive?

Yes. To have more than 4 partitions we must have one of the primary partitions set as an Extended partition. Then we can create inside that extended partition any number of Logical partitions.

I have 1 primary, 1 primary/extended and 7 logical partitions, including one for swap.

Microsoft has its own way of getting around this 4 primary partition limit that complicates things further.

GPT

[http://msdn.microsoft.com/en-gb/library/windows/hardware/gg463525.aspx]("http://msdn.microsoft.com/en-gb/library/windows/hardware/gg463525.aspx")

and Dynamic disks

[http://msdn.microsoft.com/en-gb/library/windows/desktop/aa363785(v=vs.85).aspx]("http://msdn.microsoft.com/en-gb/library/windows/desktop/aa363785(v=vs.85).aspx")

I do not think that Ubuntu can install on a Dynamic disk set up. 

Regards.

---

### Post by edu4rd on 2013-02-11
[black3agl3]("http://ubuntuforums.org/member.php?u=1034589") : Dont know for sure how that would delete my partition because i quited the process when i know that it will  mess my hard drive .
There was no option to install side by side . 

/dev/sda  is my hard drive , i dont see the other partition and i dont know how i could mess the rest of partition .

I forgot to mention what my windows partition was encrypted with TrueCrypt .
When  i run sudo testdisk i get this .

Also ...maybe if you get the hdd out and plug it into another computer ...maybe i will be able to see my partition or ...i hope soo .

Some good news after all : scanning my dev/sda/  :p
Maybe i will manage to restore it ,i have to wait to see what is happening when 100% is done .

---

### Post by Mark Phelps on 2013-02-11
If testdisk doesn't recovery your partitions, you can try using Windows to do it, but to do that, you would need to do the following:
1) Hook the drive up to a Windows PC
2) On the Windows PC, download the Minitool Partition Wizard Boot CD ISO file
3) Burn that file to a CD
4) Boot from the CD
5) See if the app provides you a Partition Recovery option.  IF it does, try that (pointing to the damaged drive) and see if it works.

If it doesn't offer you the option, you would have to buy their commercial version -- and even then, there is no guarantee that it will work.

I would suggest an alternative app for recovering files but your encryption would prevent that from working.

---

### Post by edu4rd on 2013-02-11
I think i have some luck ,after all scan i have found my documents from one partition .
Tomorrow will be interesting to copy to another hdd .

I`ll keep you posted .

---

### Post by edu4rd on 2013-02-18
Problem almost solved .
I did manage to recover all data from all my partitions ,now i`ll have to try to recover windows partition witch was encrypted with truecrypt .

Wish me luck .


Does anyone can gimme some advice ?about recovering that partition ?or maybe just how to mount it ?because i see the hole  HDD not just the encrypted partition .

Thank you .

---

