---
title: "[SOLVED] Grub loading, please wait... ERROR 17"
date: 2008-07-22
forum: Philippine Team
---

### Post by ysNoi on 2008-07-22
Guys, did you ever experienced this error on your Dual Boot Machine..?
Please help naman...! Eto ngayon problem ko..! Naka Live CD lang ako ngayon and I could access all my partitions heRe..!

Details: When I start my PC, it stocks with this error

[COLOR="Red"]Grub loading, please wait...
ERROR 17[/COLOR]

The last thing I remember is nag-install ako ng Vbox sa XP and napagana ko yung Ubuntu being the Guest OS....Eto kaya ang reason bakit nasira ang Grub ko..! :guitar:

---

### Post by thschiavo on 2008-07-22
I think 'error 17' indicates GRUB can't identify the partition type. Check
 [http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting) 
for more details. Here is the relevant entry:
"17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB."

Could be this? My problem is i'm not really sure I understand what you're writing, hehe.

---

### Post by ysNoi on 2008-07-23
Thanks men for the reply...! :)

Anyway, since I'm still on Dual Boot, one of my friends suggest to do "fixmbr" on Recovery Console...I did it and my XP already worked..!

My problem now is How To Restore the option where I choose which OS I want to use when I start my PC (i.e. the Ubuntu or XP)...

What do I do now..! Please help..! I don't want to loose from Ubuntu..! :confused::confused:

Thanks in advance..!

---

### Post by loell on 2008-07-23
you can restore grub,
 follow this guide [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by thschiavo on 2008-07-23
I did it last year, worked just fine. Anything wrong, just post here and we will try to help.

---

### Post by ysNoi on 2008-07-24
siR loell, i've been from the link that you gave..! I tried the "Quick Start" but I could not specify it...! Hindi ko masyadong kabisado..! Hirap talaga ako...! I also tried Using the Unofficial "Super Grub Disk" (Auto Super Grub Disk, As a standalone cd, and UNetbootin Super Grub Disk Loader) but it always says [COLOR="Red"]ERROR 15: File Not Found[/COLOR].

Can you walk me through for an alternative way...? Or pwede ko ring e-format muna yung partition ng Ubuntu and then install again.I have here an official CD from shipit..Please give me advice...!

Thanks....:guitar:

---

### Post by loell on 2008-07-24
> **ysNoi said:**
> 
Or pwede ko ring e-format muna yung partition ng Ubuntu and then install again.I have here an official CD from shipit..Please give me advice...!

Thanks....:guitar:

yeah that will do too, don't you have any precious files in that ubuntu partition?

---

### Post by ysNoi on 2008-07-25
**[COLOR="Blue"]waLa naman bro kasi nasa ibang partition naman mga important files ko....! buti na lang mi ganun ako..! Thanks po sa advice...! mis na mis ko na Ubuntu ko kasi..![/COLOR]** :):)

---

### Post by ch1c0dj on 2008-07-26
Check this thread I hope makatulong ito. 
Thread started by vnbuddy2002] [**HOWTO: Restore GRUB (if your MBR is messed up)**]("http://ubuntuforums.org/showthread.php?t=24113")

---

### Post by ysNoi on 2008-09-08
Hi chicodj..! Thanks po sa mga tulong nyo...! Tagal ko nakabalik dito, sorry po..

Anyway, solved na po eto. Nag-install po ako ulit coincidence naman po sa pagpalit ko ng HD.

Thank you very much guys...I love it...! :guitar:

---

