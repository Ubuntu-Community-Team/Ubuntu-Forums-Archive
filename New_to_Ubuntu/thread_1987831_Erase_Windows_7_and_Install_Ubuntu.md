---
title: "Erase Windows 7 and Install Ubuntu"
date: 2012-05-26
forum: New to Ubuntu
---

### Post by ashluvsu on 2012-05-26
I had problems with "Unmountable Boot Volume" BSOD with Windows 7 installed on my Lenovo B570 laptop.
I had my friend come over and reinstall Windows 7 and Ubuntu in a dual boot.
Well he did all of that but still couldn't get WIFI working even though he installed all the necessary drivers.
I turned on my laptop this morning and still no WIFI but now I can't even access Windows 7 because I get another BSOD that says it's corrupted or there's a virus or something. Although Ubuntu does work.
I've lost any files I intended to save so now I just want to completely wipe Windows 7 and just stick with Ubuntu.
How do I do this?
I don't know how to delete Windows 7 and I've looked up things and it says something about a /home partition, whatever the heck that means. And GParted, and I don't what the heck that is either.
I can't understand any of this so I need things fully explained.
I just need internet and the ability to type up documents. That's it.

---

### Post by ikt on 2012-05-26
Assuming you are doing this on ubuntu.

1) Download ubuntu: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
2) Burn the .iso file to USB (using Start up disk creator) or to CD (using Brasero CD burner)
3) Insert CD/USB and boot off of it (usually it's by pressing F8 right when the computer turns on and select your CD drive or USB
4) Install ubuntu, just choose erase everything and completely use the disk, this will wipe everything and install Ubuntu fresh
5) Take out the USB drive/CD when you're done
6) Grats :)


> **ashluvsu said:**
> I don't know how to delete Windows 7 and I've looked up things and it says something about a /home partition, whatever the heck that means. And GParted, and I don't what the heck that is either.

/home is your home folder, it's equivalent to the My Documents part of windows, in windows you have 1 partition, the C drive, and many sub-folders (My Documents, Program Files etc), in Linux you have many partitions and many folders, the very rough equivalents: 

/ = C Drive 
/home = My Documents
/etc = Program Files

Most people have only 1 partition, but many recommend having /home as a separate partition, that way you can reinstall Ubuntu while keeping your /home in place, but at the end of the day it doesn't really matter.

Gparted is a partitioning program that lets you see and edit partitions. You can install it via the Ubuntu Software Centre.

---

### Post by 2F4U on 2012-05-26
First of all, I would suggest you boot into the liveCD and see if you can mount the Windows partition. I was in a similar situation some time ago with a nonfunctional Windows installation, but the liveCD was able to mount my drive and I could recover all relevant files to an external hard disk. It is worth giving it a try.

---

### Post by PeterP24 on 2012-05-26
> I've lost any files I intended to save so now I just want to completely wipe Windows 7 and just stick with Ubuntu.

Wait a minute - can't you access the MSWindows partition from Ubuntu? If BSOD is all you experience, then you may recover your lost files, before wiping Windows 7.

---

### Post by ashluvsu on 2012-05-26
What about the /home partition that was mentioned?
And I don't even know where or if my friend even put the files back on there and there weren't very many so I'm going to just give up and say it's a loss. I just want to be able to use WIFI and type up lecture notes.

---

### Post by wilee-nilee on 2012-05-26
> **ashluvsu said:**
> I had problems with "Unmountable Boot Volume" BSOD with Windows 7 installed on my Lenovo B570 laptop.
I had my friend come over and reinstall Windows 7 and Ubuntu in a dual boot.
Well he did all of that but still couldn't get WIFI working even though he installed all the necessary drivers.
I turned on my laptop this morning and still no WIFI but now I can't even access Windows 7 because I get another BSOD that says it's corrupted or there's a virus or something. Although Ubuntu does work.
I've lost any files I intended to save so now I just want to completely wipe Windows 7 and just stick with Ubuntu.
How do I do this?
I don't know how to delete Windows 7 and I've looked up things and it says something about a /home partition, whatever the heck that means. And GParted, and I don't what the heck that is either.
I can't understand any of this so I need things fully explained.
I just need internet and the ability to type up documents. That's it.

Post a screen shot of gparted, it would be nice to know if this is a wubi install or a partitioned dualboot so we can get your stuff, you want out of windows, and not loose the Ubuntu installed if that is not needed.

---

### Post by ashluvsu on 2012-05-26
But where would those files be??? I wasn't paying close enough attention when my friend moved them over. There was also amnesia and photoshop in Windows that I can't find. It's just like everything disappeared.

---

### Post by ashluvsu on 2012-05-26
And what is gparted? That's another one of my problems. No idea what that is.
And it was a dualboot. Not a wubi install. That I do know.

---

### Post by wilee-nilee on 2012-05-26
> **ashluvsu said:**
> And what is gparted? That's another one of my problems. No idea what that is.
And it was a dualboot. Not a wubi install. That I do know.

Gparted is the equivalent to the disk manager in windows basically.

You use it to resize partitions and make partitions on HD's and a few other things. In the ubuntu terminal run this.

```
sudo apt-get install gparted
```Type the password, you wont see it let it install then close the terminal and then open the menu and type gparted it will show. Open it, then type in the menu, screenshot, and choose your choice of shot.

---

### Post by carl4926 on 2012-05-26
> **ashluvsu said:**
> And what is gparted? That's another one of my problems. No idea what that is.
And it was a dualboot. Not a wubi install. That I do know.
Garted is a partitioning application, you'll find it on the live cd
Press PrtSc to take a snapshot of what you see
Post it here

/home is your user partition. Typically it's
swap
/ (root)
/home

---

### Post by PeterP24 on 2012-05-26
you want to save the files from windows partition but you don't know were exactly they reside inside the windows partition? Is this correct?

---

### Post by Sgt-Slyde on 2012-05-26
"gparted" is a tool that lets you re-partition your hard drive (or change the size of the partitions - very powerful tool with lots of options).  Not sure if it's included anymore when you download the huge file to install Ubuntu or if you have to download it later (I think I had to download/install it later).

The command to get it and install it on Ubuntu is:

>sudo apt-get install gparted

or you can go into the Ubuntu Software Center, type "gparted" into the search window, and install it using "point-and-click" with your mouse.

I HIGHLY recommend you make sure you have a good copy of the installation CD ready before you start trying to use gparted, though - it can be easy to accidentally delete stuff from your drive that makes your system unusable and the best fix for that would be to re-install Ubuntu - and THAT can only be done if you already had the install CD ready to go BEFORE you started running gparted.

---

### Post by ashluvsu on 2012-05-26
I hope I did that right...

---

### Post by ashluvsu on 2012-05-26
Nope. I just want to wipe Windows 7 and keep Ubuntu. But also somehow fix my WIFI problem.

---

### Post by ashluvsu on 2012-05-26
How can I check that my Ubuntu install CD I just burned actually works?

---

### Post by PeterP24 on 2012-05-26
you test it - put it in your dvd tray and reboot the computer. Make sure you have bios set up to boot from cdrom first!

---

### Post by ashluvsu on 2012-05-26
Should I then just try and reinstall it and erase Windows?

I honestly have no idea what I'm doing. This is so frustating.

---

### Post by PeterP24 on 2012-05-26
may I suggest you focus on the current issue of wiping Windows? Then you should open another thread on the issue of wifi.

---

### Post by PeterP24 on 2012-05-26
> **ashluvsu said:**
> Should I then just try and reinstall it and erase Windows?

I honestly have no idea what I'm doing. This is so frustating.

Nope you don't need to wipe everythin and reinstall ubuntu - it is called LiveCD - it would give you an functional OS without touching ANYTHING - the idea was to see if the newly burned CD/DVD or whatever is functional. Then, it was suggested to have it in case something went wrong.

From what you say, you have a functional Ubuntu OS - there is no need to reinstall it - just to fix that wifi issue - but I suggested in another post to focus first on deleting the windows partition - because the trick is to remove windows without hurting Ubuntu.

By the way - do you know if Lenovo has the habbit of keeping the drivers on a hidden partition?

---

### Post by PeterP24 on 2012-05-26
If lenovo shipped your computer without a driver CD, and it keeps the drivers on a hidden partition - then you must take care to backup that partition first - you may need those drivers in the future.

The plan is to use gparted to delete the windows partition. If everything goes well, then you won't need the liveCD after all - it was created so you can reinstall ubuntu if you, somehow manage to damage it in the process of removing windows.

---

### Post by ashluvsu on 2012-05-31
I finally navigated through Windows and found my files thank god.
I couldn't fix Windows so I just wiped it and installed Ubuntu 12.04. I previously had 11.10 installed.
But my wireless still didn't work.
I found a forum post about Jupiter and a hardware reset.
I installed Jupiter through terminal and a wired connection and then I shut down my computer  and took out the battery and unplugged it and held the power button for 30 seconds.
I'm not sure which one of those two things did it, but I'm posting this from my wireless connection and Ubuntu 12.04 has been working with minimal problems(:

---

### Post by latinlightning on 2012-05-31
Since you managed to get rid of W7 and now have a functioning wireless connection, could you please mark the thread as solved?

Thank you.

---

