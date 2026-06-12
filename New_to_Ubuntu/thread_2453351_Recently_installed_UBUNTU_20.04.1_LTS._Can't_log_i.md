---
title: "Recently installed UBUNTU 20.04.1 LTS. Can't log into my user"
date: 2020-11-08
forum: New to Ubuntu
---

### Post by berneealf on 2020-11-08
Experience level: absolute noob. I am installing Ubuntu because I am very interested in learning. Currently watching youtube courses.

Hardware:

MoBo: Gigabyte B450M DS3H
CPU: RYZEN 5 2600
GPU: Nvidia GeForce GTX 760 Windforce 2x OC 2GB Edition
RAM: 16GB Crucial Ballistix, 3000MHZ

If you need more information about hardware, let me know.

Installation:

I clean installed windows10 on my 240gb Ssd. I then reduced the partition for windows storage and created 2 partitions for Linux:

a) 32gb SWAP AREA
b) 20gb ext4 for root directory (/)

As my ssd is quite small and windows needs all the extra space it can get, I decided to try partitioning an additional drive for my /home directory. It's a 500gb Hdd. As I said, I am very interesting in learning to use Linux, so I will be playing around and very likely breaking stuff. I am interested in an independent /home partition to be able to re-install as many times as necessary without loosing all data.

c) 500gb ext4 for /home

For boot intallation, I selected the same partition where windows boot manager is.

Installation finished without problems and gnome works as well. I am offered to boot into ubuntu, windows boot manager and additional ubuntu options (which I haven't explored). I boot into Ubuntu and it seems to work fine until it prompts for my user password (this is already strange, during installation I checked the option to boot straight to desktop and not ask for a password). I enter the password and it does nothing. If I enter an incorrect password it is recognized as incorrect.

If I access terminal with ctr+alt+f3, I can confirm that my password is correct as I can log in through terminal. I have tried to google my problem and found a possible solution:

[https://www.maketecheasier.com/fix-ubuntu-login-loop/](https://www.maketecheasier.com/fix-ubuntu-login-loop/)

I have 3 problems following those instrucions:

1) the command: ls -lah | grep -i .Xauthority does nothing.
2) the command: ls -lah works but does not show a .Xauthority file
3) if I go traight to: sudo chown username:username .Xauthority, it says the .Xauthority file could not be found.

Thanks in advance for your effort.

---

### Post by ActionParsnip on 2020-11-08
Can you reset your password in the CLI? You can use the
```

passwd

```
Command. You will see no input as you type the old or new passwords. 
If you are using a wired connection to get Web access then you can probably get fully updated in CLI using 
```

sudo apt update 
sudo apt full-upgrade 

```

---

### Post by tea for one on 2020-11-08
>  I checked the option to boot straight to desktop and not ask for a password
I would re-install and ignore the option of logging in without a password. Your experience of Ubuntu will be more enjoyable.
>  32gb SWAP AREA
Ubuntu 20.04 automatically creates a swapfile. Swap partition is not needed.

---

### Post by garvinrick4 on 2020-11-08
##Reinstall making sure you check right box with password or without at install.
##Should be no problem and i enjoy a new user who reads enough to make a /home
##Can even use the swap as ext4 partition for another install down the line.
##Additional Ubuntu options holds more kernels so if your main kernel has a problem can use another always keep at least one
## Sounds like you be a fine Linux user have done your homework.

Edit: By the way welcome to the Forum you will find lots of help here and can read threads that are solved
        when they interest you. One day you will passdown what you learn, enjoy  				 				 					 						 	[**[COLOR=#000000]berneealf[/COLOR]**]("https://ubuntuforums.org/member.php?u=2153216")

---

### Post by berneealf on 2020-11-08
[I would re-install and ignore the option of logging in without a password. Your experience of Ubuntu will be more enjoyable.]

I'm not sure I understand. Will my experience with Ubuntu be more enjoyable if it prompts for password at startup?

[Ubuntu 20.04 automatically creates a swapfile. Swap partition is not needed.]

I did a manual install, so I believe I left nothing uo to Ubuntu to do automatically. I checked my drive after reading your comment and it only has the partitions I made, it did not make any additional ones. I assume it is using the SWAP AREA I made.

---

### Post by berneealf on 2020-11-08
Thanks, I will try reinstalling and try to switch kernels.

---

### Post by berneealf on 2020-11-08
Thanks I will try these commands.

---

### Post by berneealf on 2020-11-08
The full upgrade fixed the issue. Thank you sensei.

---

### Post by Impavidus on 2020-11-09
> **berneealf said:**
> 
a) 32gb SWAP AREA
b) 20gb ext4 for root directory (/)


15 years ago it was recommended to make your swap twice your memory. 8 yeas ago it was recommended to make your swap about as large as your ram. Nowadays it's recommended to use about 4GB swap. You can create a swap partition, but if you don't, Ubuntu will create a swap file on your root partition. On the other hand, 20GB for a root partition is a bit tight.

It's probably best to keep a password at login. It doesn't provide a lot of security (with physical access to the computer, it can be bypassed), but at least you won't forget the password. After a while, you can type it in 3 seconds.

---

### Post by tea for one on 2020-11-09
> **berneealf said:**
> I'm not sure I understand. Will my experience with Ubuntu be more enjoyable if it prompts for password at startup?

[COLOR="#0000FF"]More enjoyable[/COLOR] was probably not the best choice of words.

I was trying to point out that your first problem arose with logging in to your user account and there are examples in this forum where automatic log in creates additional difficulties in the future.

Perhaps, I should have written [COLOR="#0000FF"]less stressful[/COLOR].

Anyway, it's gratifying to read that the dilemma is solved.

---

