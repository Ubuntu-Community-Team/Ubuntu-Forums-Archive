---
title: "How to check wifi from terminal?"
date: 2018-09-21
forum: New to Ubuntu
---

### Post by dualfuel on 2018-09-21
This is both exsperating, and extremely educational. The system is an HP desktop w/ Pentium 4, 2.6Ghz, 512Mb ram, 40Gb hhd. It currently has Ubuntu 17.04 installed. I figured out how to change the password and login at the terminal. I cannot find a desktop package anywhere. I cannot update, or install any packages. There is no network manager installed. Things I have tried: a. I made a Lubuntu boot USB with Rufus, changed the boot order, in the bios, to boot USB first, and got a "Non-system disk or disk error". b. Plugged in a real Tek Wi-Fi adapter. Confirmed that the OS on the hd has the rtl8192 driver files. Not sure how to proceed to mount the adapter. My thinking here, was to get the machine wirelessly connected to the internet, and Sudo apt-get packages or update. c. Learned how to mount the USB stick, download files from my phone unto the USB stick, and load them into /home/name. I cannot figure out how to find specific packages on the internet. Packages like "zip" are missing on my machine (although "tar" is there). The idea here was to bring the missing packages, or a desktop to the machine via USB stick, and install the missing packages individually. My hope was that sudo apt-get could be directed internally and the packages would install themselves.

I was given this computer. I believe it was some sort of billing server. I am starting to believe that the original administrator, modified the Ubuntu 17.04 OS to make it impossible for someone to hack. My goal is to be able to use this machine connected to the internet... I would like to try Lubuntu, but would be pleased with 17.04 if I could load Unity or PIXEL. At this point it's become a challenge to figure out what happened to this machine... very educational. Could someone please point me in a useful direction?

---

### Post by Autodave on 2018-09-21
First off, 17.04 is dead or End Of Life (EOL).  You need to get a copy of 18.04 which is the latest LTS (long term service) release.  After obtaining you preferred Linux release, make sure to put it on the USB stick as an .iso file.  Now, boot the machine to that.  From there, you can choose Try ?buntu or Install ?buntu.  Try it first and see if your wifi will work.....chance are that it will with the new release.  If not, come back here! :-)

---

### Post by TheFu on 2018-09-21
Support for 17.04 ended last January.  Stick with LTS releases only if you don't want to reinstall every 6 months. It is against forum policy to help with unsupported releases.

No computers are impossible to hack. NONE.  If it is networked, the risk of attacks increases exponentially. If the system is being used for billing, please don't connect it.

Unity has been removed as the default GUI in 18.04 and will likely only be a community project until it dies in 5-10 yrs.

Zip isn't used much on Unix systems. On a supported release, you could install a zip package.  If you expect a Windows-like experience, use Windows. Otherwise, expect to be frustrated.   Linux is not Windows. [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

I use wicd-curse to manage wifi connections, but if you can't install anything ... that isn't an option. Network adapters aren't "mounted" they need a valid driver and they will become available for configuration.

If you don't need the current applications anymore, move to a new LTS release.  16.04 or 18.04 are the options.

---

### Post by dualfuel on 2018-09-21
Thanks for the reply....the machine will not boot with the live USB I made with RUFUS.

---

### Post by dualfuel on 2018-09-21
Wheww, I totally get it, 17.04 is dead. I am not looking to keep it as an operating system. I believe Lubuntu 18.04 would be a better choice.
The problem is, 17.04 is what is installed, and it's not complete. 
Lol! I dare you to hack this computer! If you could,  that would mean it could be upgraded. Apparently it can't connect to the router, nor can it be booted from USB....it's getting farsical. 
I'll keep pecking away at it tho. Thx

---

### Post by Autodave on 2018-09-21
Get a copy of 18.04 and see if you can boot to the screen that gives you the option of either trying on installing.  If you get that far, TRY it first and see if your wifi / internet works. If so, proceed to install.  When you get to the options, choose to use the entire disk.

---

### Post by dualfuel on 2018-09-21
Is there a site where I can simply copy a bootable 32bit copy of 18.04? As it stands I don't have access to RUFUS to take a copy of the .iso and make it bootable. 
I managed to get the unetbootin.bin onto the machine....but am too ignorant to get it working. I seem to be capable of copying files to my USB drive via an OTG cable, and placing them on /home....&#128580;.
Seems like there is always one piece missing...lol.

---

### Post by TheFu on 2018-09-21
I use **dd** to make bootable flash drives from an ISO.  Copying the ISO over isn't sufficient.
I've never used rufus, but I have used Yumi.

18.04 is the latest LTS, but there have been many reports of issues.  If you have any issues with it, switch to 16.04.

---

### Post by dualfuel on 2018-09-21
Solved! I had a copy of lubuntu-18.04-desktop.iso in my home directory. I umounted a fresh USB. Then sudo dd bs=4M if=lubuntu-18.04-desktop.iso of=/dev/sdc conv=fdatasync There was some hassle because at first I sent the output to /dev/sdc1 which was what I was used to calling the USB. As soon as I got the USB booting the computer, the wifi adapter lit up and up up and away we went! Thanks for your help!!!
&#128515;

---

### Post by Geoffrey_Arndt on 2018-09-21
Glad you've got LU . . . buntu running (not sure if you actually completed an install or are just running in LIVE mode).   Your machine is quite anemic even for the lighter distro Lubuntu. 

Really, any Ubuntu based Linux distro requires at least 1 GiB ram.   Best of luck . . . (might want to look at Distrowatch.com and download the iso for even a lighter distro like "Bodhi" Linux or "antiX".

---

### Post by dualfuel on 2018-09-23
Thanks, and yes Lubuntu is installed on the machine and everything is doing fine. I am printing documents, web surfing, and using Wine and dosbox.
Next is loading my Arduino IDE and sending packet. I am extremely pleased with the performance, although I struggle with using the desktop, as I have become accustomed to using the terminal for everything.

---

