---
title: "Noob questions !"
date: 2012-05-29
forum: New to Ubuntu
---

### Post by Mshabk on 2012-05-29
Hi,
 
okay i'm interested in linux and i want to try it, so i searched that Ubuntu is the most commonly used.
 
So, i want to run it in my Laptop that has a windows 7. Is that possible?
and how? and can i run two operating system in the same laptop?
what about the files? can i transfare them to the new system?
and what should i know about linux coz i'm a Big noob?
 
please anyone Explain every little detail ( if there is picture that will be helpful )
by the way, english is not my first language so if there is any mistake ( ignore it ) :lolflag:

---

### Post by carl4926 on 2012-05-29
First thing to do is try the Live CD
It boots to a working desktop, running from the CD. See how it feels, you can create a bootable USB if you prefer.

When you have the desktop running from either the cd or a usb, it would be handy if you open a terminal and post the result of

```
sudo fdisk -l
```From that we can see what a mess of partitions windows has in place. Much hinges on this detail.

---

### Post by gnusci on 2012-05-29
IT is very simple to have both OSes, just use Windows installer for Ubuntu Desktop

[http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

But you can try it first without install it

[http://www.ubuntu.com/download/help/try-ubuntu-before-you-install](http://www.ubuntu.com/download/help/try-ubuntu-before-you-install)

---

### Post by Primefalcon on 2012-05-29
I'd recommend install beside windows, there's an option for that during a standard installation.

just boot from a flash drive, choose install and just choose the option install beside Ubuntu, you'll then be show  partition screen where you can shrink the Windows partition and create a Ubuntu partition... then you simply install to said partition

Full walk-through here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

As stated above though try without installing first (option from booting from a usb), to see make sure there's no issues with drivers or such first

---

### Post by fantab on 2012-05-29
> **Mshabk said:**
> So, i want to run it in my Laptop that has a windows 7. Is that possible?and how? and can i run two operating system in the same laptop?
what about the files? can i transfare them to the new system?
and what should i know about linux coz i'm a Big noob?
 
please anyone Explain every little detail ( if there is picture that will be helpful )
by the way, english is not my first language so if there is any mistake ( ignore it ) 

** Yes, you can dual-boot Windows and Ubuntu from same Hard Disk [HDD] on same laptop.
** Ubuntu can read and write to NTFS (Windows) HDD partitions but you cannot use Linux partitions in Windows.

Refer to the following Links to get a hang of Linux:

[**Linux for Beginners**]("http://www.linfo.org/newbies.html"), [**Linux is NOT Windows**]("http://linux.oneandoneis2.org/LNW.htm")

[**How to Dual-Boot**]("https://help.ubuntu.com/community/WindowsDualBoot"), [**Dual-Boot Illustrated**]("http://members.iinet.net.au/%7Eherman546/p23.html") (info here is bit old but you will get the idea)

You will have to Partition your HDD to accommodate Ubuntu: So to know what you have post a screen shot of your HDD Partitions from Windows.

---

### Post by codemaniac on 2012-05-29
As suggested above a live cd will give you an enviroment to play with the Linux system without installing on the hard disk .This also helps in testing if your hardware plays well with Ubuntu .You can download Ubuntu Live/Installation cd from the below link .
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by mastablasta on 2012-05-29
ubuntu manual is also a good place to start. there is an online manual and also a community made manual (see my signature) with a lot of pics and all...

---

### Post by Shadius on 2012-05-29
> **Mshabk said:**
> Hi,
 
okay i'm interested in linux and i want to try it, so i searched that Ubuntu is the most commonly used.
 
So, i want to run it in my Laptop that has a windows 7. Is that possible?
and how? and can i run two operating system in the same laptop?
what about the files? can i transfare them to the new system?
and what should i know about linux coz i'm a Big noob?
 
please anyone Explain every little detail ( if there is picture that will be helpful )
by the way, english is not my first language so if there is any mistake ( ignore it ) :lolflag:

Like the others have suggested. Get a feel for Ubuntu with the LiveCD before actually installing it. Also, taking the Ubuntu Tour might help to get you acquainted. 

[Ubuntu Tour]("http://www.ubuntu.com/ubuntu") Click on "Start tour".

---

### Post by Mshabk on 2012-05-29
> **gnusci said:**
> IT is very simple to have both OSes, just use Windows installer for Ubuntu Desktop
 
[http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)
 
But you can try it first without install it
 
[http://www.ubuntu.com/download/help/try-ubuntu-before-you-install](http://www.ubuntu.com/download/help/try-ubuntu-before-you-install)
 
 
[LEFT]okay, i will try it first so that i can know if my hardware linux compatible. but how !
is there a way to test all my hardware when i'm on linux? 
 
Hopefull by midnight i will be a linux user![/LEFT]

---

### Post by Shadius on 2012-05-29
> **Mshabk said:**
> [LEFT]okay, i will try it first so that i can know if my hardware linux compatible. but how !
is there a way to test all my hardware when i'm on linux? 
 
Hopefull by midnight i will be a linux user![/LEFT]

You could burn the Ubuntu LiveCD or make a Live USB. You'll need to download the Ubuntu installation file first. 

Installation file: [Ubuntu Desktop]("http://www.ubuntu.com/download/desktop")

Method 1: [Burn a CD on Windows]("http://www.ubuntu.com/download/help/burn-a-cd-on-windows")

Method 2: [Create a USB stick on Windows]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows")

---

### Post by Mshabk on 2012-05-29
my laptop is hp Pavilion dv6 
My processor is intel i7 2nd generation
i have the AMD Radeon
Network adapter from intel
6 MB ram
so please could you provide with tips so that i can have full Experiance with Ubuntu

---

### Post by Mshabk on 2012-05-29
> **Shadius said:**
> You could burn the Ubuntu LiveCD or make a Live USB. You'll need to download the Ubuntu installation file first. 
 
Installation file: [Ubuntu Desktop]("http://www.ubuntu.com/download/desktop")
 
Method 1: [Burn a CD on Windows]("http://www.ubuntu.com/download/help/burn-a-cd-on-windows")
 
Method 2: [Create a USB stick on Windows]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows")
 
i will use the first method.
 
after i burn do i just restat and it will apper automaticaly? or do i have to do something?

---

### Post by Shadius on 2012-05-29
> **Mshabk said:**
> my laptop is hp Pavilion dv6 
My processor is intel i7 2nd generation
i have the AMD Radeon
Network adapter from intel
6 MB ram
so please could you provide with tips so that i can have full Experiance with Ubuntu

Follow my previous post.

---

### Post by nipunshakya on 2012-05-29
> **Mshabk said:**
> i will use the first method.
 
after i burn do i just restat and it will apper automaticaly? or do i have to do something?

[http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html)
 This might help you out...
Start from the topic:** Boot into Ubuntu live CD Session** of the webpage.

Hope that will help u out...

Happy Linuxing

---

### Post by Shadius on 2012-05-29
> **Mshabk said:**
> i will use the first method.
 
after i burn do i just restat and it will apper automaticaly? or do i have to do something?

Since you chose method 1, now you have to make sure that Windows boots from the CD-ROM first. That means you'll have to access your BIOS and change the boot order. Post back if you need details on how to access your BIOS.

---

### Post by Mshabk on 2012-05-29
> **Shadius said:**
> Since you chose method 1, now you have to make sure that Windows boots from the CD-ROM first. That means you'll have to access your BIOS and change the boot order. Post back if you need details on how to access your BIOS.
 
Yes please, every possible detail that will help me.

---

### Post by Shadius on 2012-05-29
> **Mshabk said:**
> Yes please, every possible detail that will help me.

You'll have to restart your computer and keep tapping one of these buttons: **F2**, **Del**, or **F12**. Either one of those will get you to the BIOS. Next you'll have to use your keyboard to navigate the BIOS menu. Look for the **BOOT** heading column, the boot order will be in there. 

Here's a link that'll help you. 

[BIOS]("http://pcsupport.about.com/od/fixtheproblem/ss/bootorderchange.htm")

**READ IT FIRST!**

---

### Post by Mshabk on 2012-05-29
> **Shadius said:**
> You'll have to restart your computer and keep tapping one of these buttons: **F2**, **Del**, or **F12**. Either one of those will get you to the BIOS. Next you'll have to use your keyboard to navigate the BIOS menu. Look for the **BOOT** heading column, the boot order will be in there. 
 
Here's a link that'll help you. 
 
[BIOS]("http://pcsupport.about.com/od/fixtheproblem/ss/bootorderchange.htm")
 
**READ IT FIRST!**
 
Okay, thanks! i have enugh info ( hopefully ).
if there is any info that will help please add it. i will be visiting this topic frequently for in problem that i wil face.

---

### Post by Shadius on 2012-05-29
> **Mshabk said:**
> Okay, thanks! i have enugh info ( hopefully ).
if there is any info that will help please add it. i will be visiting this topic frequently for in problem that i wil face.

Change the boot order so that the CD-ROM is the first on the list, then save and exit. Restart the laptop with the Ubuntu LiveCD in the CD-ROM drive and you'll be greeted with Ubuntu! Select **Try Ubuntu**. Then you'll be able to test out Ubuntu for yourself! Hmm...I think that covers it.

---

### Post by morhin on 2012-05-29
From one noob to another.

I tried several ways to go about dealing with a new system. I luckily ran into a book at the library that got me and ubuntu up and running. It hasn't always been without speedbumps but it's enough to keep me from running back to windows. Actually, I'm learning to have some fun with ubuntu.

It's a book by Rickford Grant with Phil Bull call "Ubuntu for non-geeks".

I have the one for version 10.04, which I'm now running. It covers bunches of stuff from how to get started to dual boots and on and on. 

I won't move to version 12.04 until that book hits the stands for that version.

I highly recommend it. Otherwise I was going crazy trying to chase down information using google and the forums. Half the time I didn't even know what questions to ask. 

Good luck and hang in there... it's worth it.

Morhin

):P

---

