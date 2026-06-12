---
title: "Dual Boot Options"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by .Thomas on 2008-06-13
WARNING **New to Ubuntu**

I am getting a new desktop, with vista pre-loaded. I want to dual boot, but I thought it would bet
ter if I installed another fresh HD to install it on.

Step 1, put in HD
Step 2, put in Ubuntu live CD
Step 3, ??????
Step 4, Dual Boot and Profit. 

Thank you, if there is something I am missing in the equation.

---

### Post by wPwLUi3N on 2008-06-13
You don't need a new hard disk necessarily for dual booting.

Since you are new to Ubuntu, you should give [wubi]("wubi-installer.org/") a try. It is safe and effective and create nice dual boot systems.

---

### Post by .Thomas on 2008-06-13
I know you don't need to, but I want to because of space, and other  reasons. 

Should I still use the same program.

---

### Post by wolfen69 on 2008-06-13
just try the live cd first, to make sure everything will work. then make your decision. if you really wanted to use linux, a good way would have been to get a pc pre-installed with linux and add windows to it.

---

### Post by worldy on 2008-06-13
boot with Ubuntu CD
Choose where you want to install the OS in the questions regarding Partition. I think you should install it in largest continous free space ,ie your second unformatted HD(sdb),since the preinstalled glassware will take up your first HD(sda) full.

---

### Post by Gannon8 on 2008-06-13
> **wolfen69 said:**
> if you really wanted to use linux, a good way would have been to get a pc pre-installed with linux and add windows to it.Except windows will disable GRUB when installing.

As for the LiveCD, just install it to the second hard drive, and Ubuntu should auto detect the windows partition on the second drive, and configure GRUB accordingly.

---

### Post by thisiam on 2008-06-13
> **.Thomas said:**
> WARNING **New to Ubuntu**


Step 4, Dual Boot and Profit. 

Thank you, if there is something I am missing in the equation.

How are you going to profit?
besides using a better OS and not having to deal with virus/spyware......
are you thinking $$$$$ will come with ubuntu.

---

### Post by .Thomas on 2008-06-13
deleted

---

### Post by .Thomas on 2008-06-13
> **thisiam said:**
> How are you going to profit?
besides using a better OS and not having to deal with virus/spyware......
are you thinking $$$$$ will come with ubuntu.

[http://en.wikipedia.org/wiki/Underpants_Gnomes](http://en.wikipedia.org/wiki/Underpants_Gnomes)

check it out

---

### Post by kattman on 2008-06-13
Thats the way I have mine system set up!  I love IT. luckily my computer gives a Boot menu option for me to change if I need without having to go into the system bios settings..

I think the benefits are many
(1)  Hard drive fails  you can use the other!
(2)  If you sell the computer You can have all your files moved quckly
(3)  Ububtu cannot be seen from windows! 

I say its the best way to go 1 hard drive for window, another foe Ubuntu!

---

### Post by .Thomas on 2008-06-13
so when you start it up, does it say press one for windows, press two for ubuntu?

---

### Post by kattman on 2008-06-14
If I Hit "F10 + enter key" during the boot it will switch to the windows drive! No need to go into the bios setup !  

I realy think that two hard drive are the best way to go. XP on one Ubuntu on the other!

---

### Post by mailtwogopal on 2008-06-14
hi,

 am not a great user in ubuntu as i am only 15 days old to ubuntu. if u have a plan to use ubuntu in HDD, just download ubunut live cd from [here]("http://www.ubuntu.com/products/GetUbuntu/download") and burn it to a CD as an image. u can install ubuntu in two ways

 1. restart ur pc and boot via ubuntu cd
 2. with windows vista u just put CD on drive and u can see like any other CDs when loaded will autoplay, same way ubuntu cd will also auto played and opens a window where u have 3 options "try live CD" (without installing on HDD), "Install ubuntu" (in HDD), and some other 3rd option (i forgot). 

  if u click "install ubuntu" it opens "wubi" installer and u can select the drive in which u wanna install ubuntu and proceed with defaults. this is how i did and its fine working now. i think am answering as per your requirement hope. 

kudos! Go ubuntu! Go linux!

---

### Post by .Thomas on 2008-06-16
Fully understand that, trust me the live CD is getting me through until my HD comes shipped:)

I am excited that I don't have to go to the BIOS setup though. Will the F10 and enter trick work on all machines?

---

### Post by markbuntu on 2008-06-16
This is what I did with my dual hard drive windows/ubuntu setup. It is really really easy with SATA. 

plug the preinstalled windows drive into SATA2 and plug the new hard drive into SATA 1 plug on the motherboard. You really have to check this because many times a single hard drive is just plugged into any SATA plug because SATA does not care, it checks each plug in turn and looks for a drive with a boot sector, the first one it sees, it boots.

Boot Ubuntu on the live cd and install on sda. If live says that sda is ntfs then swap the plugs on the mb until it says sdb is ntfs (that is windows file format) with a small dos partition (that is windows boot sector) and sda is unformatted or something like that.

Windows will never even know Ubuntu is there and grub will not mess with the windows drive at all. 

All problems with dual boot can be avoided this way.

---

### Post by Distortedgamer on 2008-06-17
What if you already have Ubuntu installed and you are trying to put Windows on? I have a few partitions for the Ubuntu install, but no free space. How do I partition the used space to be able to install windows?

---

