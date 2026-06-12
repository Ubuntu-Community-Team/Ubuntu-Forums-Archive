---
title: "Can't install, screen goes black"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Mr.Kuchinawa on 2008-05-02
Okay, I didn't really know where to post this, but here goes:

On my Asus m2400n, I can't install ubuntu. I have tried with both 7.10 and the latest version, but when it loads the kernel to 100%, the screen goes black and the machine goes quiet. If not that, It simply reboots. This happens both when I try to check the cd for errors, install and load the livecd. 

I can confirm that the cd's themselves are without errors.
If there is any more information I can provide, I am happy to do so.

So what should I do? XP works perfectly fine

---

### Post by TeoBigusGeekus on 2008-05-02
Why don't you try the alternate cd?

---

### Post by redbob on 2008-05-02
Such thing already happened to my machine. I changed CD drive, burned Alternate, Live CD. When I changed flat cable, the problem has gone!! :popcorn:

---

### Post by Mr.Kuchinawa on 2008-05-03
Doesn't work with the livecd either. The machine is a laptop, but I'll try to get my hands on an external drive and then try again.

---

### Post by Mr.Kuchinawa on 2008-05-03
> **Mr.Kuchinawa said:**
> Doesn't work with the livecd either. The machine is a laptop, but I'll try to get my hands on an external drive and then try again.

Edit: No juice. Even with a philips exernal dvd-drive, the result is the same with both the standard and the alt. version. 

I'm really clueless as to what I should do here...

---

### Post by seshomaru samma on 2008-05-03
did you try the _alternate_CD?
(not the LiveCD)

---

### Post by Mr.Kuchinawa on 2008-05-03
> **seshomaru samma said:**
> did you try the _alternate_CD?
(not the LiveCD)

As I said, yes.

---

### Post by Rocky37 on 2008-05-03
> **Mr.Kuchinawa said:**
> Okay, I didn't really know where to post this, but here goes:

On my Asus m2400n, I can't install ubuntu. I have tried with both 7.10 and the latest version, but when it loads the kernel to 100%, the screen goes black and the machine goes quiet. If not that, It simply reboots. This happens both when I try to check the cd for errors, install and load the livecd. 

I can confirm that the cd's themselves are without errors.
If there is any more information I can provide, I am happy to do so.

So what should I do? XP works perfectly fine

I have had the same problem for the past week except my problem is with a desktop unit.  Have tried everything -- excepting the right thing:(  I have also enjoyed the complete lack of any attention.

My install to my laptop was flawless.

---

### Post by Mr.Kuchinawa on 2008-05-04
Well.. If nobody can help me.. It's bye-bye to linux from me

---

### Post by Mr.Kuchinawa on 2008-05-05
Okay, I really don't want to be a nuisance here, but I really need this to work. 

I have noticed another thing: When I tried another disto, pclinuxos, I got just the same result. However, when I tried the option "safeboot" everything goes well untill I reach "searching for loop image". It says /dev/hdc followed with [ OK ] in green colours, so I guess that's nice, however, after that it says:

Mounting loop image on /initrd/loopfs: mount: mounting /dev/loop0 on initrd/loopfs failed: invalid argument

Then, in red colour:

ERROR: Unable to mount loop filesystem,
       Commands were:
       llosetup /dev/loop0 initrd/cdrom/livecd.sqfs
       mount -r -t squashfs /dev/loop0 initrd/loopfs

       Dropping you a limited shell

Then, in white, it says "loading initrd/bin/ash

Alas, it loads busybox, which is a built-in shell.


Maybe this is just pointless, but I hope this can lead to a solution...pretty please?

---

### Post by dublued on 2008-05-05
hey there... do not despair... i'm sure you'll come to a resolution soon enough.  i'm no expert as i am new to this stuff but i've tried to install ubuntu 8.04 on 5 different systems with varying results.

what are your system specs?  more specifically, how much ram does your system have?

i made a very similar post becasue I was having the same exact problem with an old laptop of mine.  I haven't tried any of the suggested solutions yet.  hopefully this will guide you in the right direction:

[http://ubuntuforums.org/showthread.php?t=781098](http://ubuntuforums.org/showthread.php?t=781098)

---

### Post by Mr.Kuchinawa on 2008-05-06
Fixed! I installed opensuse 10.3 with the option "installation-acpi disabled"

Can anyone explain why this was necessary?

Edit: Also, I found this: [http://ubuntuforums.org/showthread.php?t=83976](http://ubuntuforums.org/showthread.php?t=83976)

---

