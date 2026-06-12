---
title: "Working USB Install That Works on any Machine"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by JerryC on 2012-08-15
Is it possible to have a working USB install that you can carry around with you and plug into any PC and boot into Ubuntu (assuming boot from USB capability).  I have a working installation copy on USB, but that's not what I'm talking about.  I would like to have a USB with "my" linux on it.  I want to be able to install programs ocasionaally to the USB without messing up the host computer.  Am I making sense?  Can this even be done?

JC

---

### Post by C.S.Cameron on 2012-08-15
Following is step by step how to install 12.04 on a 8GB flash drive:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue
At "Installation type" select "Something else".
Continue
Confirm Device is correct.
Select "New Partition Table" 
Click Continue on the drop down.
(Optional partition for use on Windows machine)
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000 bytes.
Location = Beginning.
"Use as:" = "FAT32 file system", (
And "Mount point" = /windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4000 to 6000 bytes, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1000 to 4000 bytes, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hybernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 bytes, or same size as RAM), Beginning and "Use as" = "swap area" then OK.
(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select Continue.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by JerryC on 2012-08-15
An excellent response!  Just what I'm looking for.
Thank you so very much.

JC

---

### Post by Hedgehog1 on 2012-08-16
Jerry,

I have just such a USB stick I carry in my work bag.

Not only is it great for demoing Ubuntu to folks at work, I also us it to boot up 'thrashed' windows machines and copy user data to an external USB drive.

Once the data is rescued, the IT folks then put a fresh copy of Windows on the PC and then the user can restore their documents from their USB drive.

This means you can be a hero now-and-again.  It is a VERY nice feeling.

***The Hedge***

:KS

---

### Post by JerryC on 2012-08-16
I know that feeling.  I have worked with PCs since 1982 and was one of the "PC Guys" in the office with a 175 PC network.

JC

---

### Post by DisturbedDragon on 2012-08-16
You could just use unetbootin to install to a xxGB stick with persistence.  Done and done. You can save settings and permanently install programs.

---

### Post by C.S.Cameron on 2012-08-16
Full installs and Persistent installs both have their advantages.

---

### Post by Khal1d on 2012-08-16
I have a 16GB USB Drive that I have lugging around with a persistent Ubuntu installation on it, and I've been looking for something along the lines the OP was asking about.

Persistent is cool, but I wanted "mini USB me" to come with me to work! :D

Thanks guys, I'll post a reply when I get this sorted! :P

*Edit*

P.S

As I am using a 16GB, should I make the partitioning as follows?

2,000

8,000

2,000

4,000

Respectably?

---

### Post by C.S.Cameron on 2012-08-17
I would make / a little smaller ~6000 and /home a little bigger ~4000.
You can always adjust the size later using gparted.

---

### Post by Khal1d on 2012-08-17
Success!
 
 I needed to fix some dependancies, and things were moving...in batches? (Stop, move, stop, move)
 
 In the end a sudo apt-get autoclear did the job. Good to go! :D
 
 In the end, I didnt stick to my original partitioning (played around with /home and /), but all's well that ends well!

Currently posting this from the browser on my mini-me! Otherwise known as my little linux on the go!

Thanks alot everyone! You are :KS:KS:KS:KS:KS:KS:KS

---

### Post by 25tom on 2012-08-18
Just for anyone that is looking for an alternative OS to boot live from USB, I find one called Knoppix excellent - it, like Ubuntu, is based on Debian and by default installs to USB flash disk from a CD.

---

### Post by JerryC on 2012-08-19
Do you, or anyone, know where I can download Knoppix that isn't one of the mirror sites?  I have tried three different mirror sites and they were all slow and failed the download.

JC

---

### Post by 25tom on 2012-08-19
Um, I used the German mirror, CD iso download. Took about 40 mins. Don't let your computer start the screensaver - a mistake I made which caused download fail!
It's also possible to download via bit-torrent, which I imagine is faster.
Hope this helps :)

---

### Post by JerryC on 2012-08-19
What is persistence and what does it do for you?

JC

---

### Post by 25tom on 2012-08-20
> **JerryC said:**
> What is persistence and what does it do for you?

JC

Basically, when you use a live USB drive to boot an OS, the computer does not make any changes to the fles on the USB drive. This is because excessive writing to a USB drive will greatly shorten its life. However, persistence means that during your live session, data in the RAM about changes made to settings, files created, etc, is compressed and saved in a single 'write' to the USB drive. Thus the life of the drive is maximised. In the case of Knoppix, this is done by the computer in such a way that you can seem to make changes to the files and settings, but these changes are not actually applied till shutdown.

---

### Post by JerryC on 2012-08-21
That is very interesting.  I have learned something.  I may have trashed my new flash drive by re-installing Ubuntu to it too often.  I think I have re-installed it four times plus formatting the drive three or four times including one deep format.

JC

---

### Post by JerryC on 2012-08-21
I'll have to try again when I get home.  I'm out on a trip with my RV and most wifi systems in RV parks are poor.  I found one bit torrent file, but it wouldn't even start. Do you know where to find a good working bit torrent file?

JC

---

### Post by 25tom on 2012-08-21
> **JerryC said:**
> I'll have to try again when I get home.  I'm out on a trip with my RV and most wifi systems in RV parks are poor.  I found one bit torrent file, but it wouldn't even start. Do you know where to find a good working bit torrent file?

JC
Sorry, no, I don't know that much about bit-torrent...

---

### Post by C.S.Cameron on 2012-08-21
> **JerryC said:**
> What is persistence and what does it do for you?

JC

With Ubuntu Persistence, preferences, cookies, newly installed programs, etc, are stored in a file named casper-rw.
Due to FAT32, max file size it 4GB.

You can also have a persistence file named home-rw.
It will store your home folder.

You can also use persistent partitions of the same names.
These can be any size
These partitions can be located on the flash drive or the computers hard drive.

Some people make these partitions ext2 because it is non journaling. thus making the flash drive last longer.

**I have never heard of anyone actually bricking a flash drive from running Linux on it**.

If you do the math a flash drive should last years of continuous writing.

I understand when they do fail from too many writes, no data is lost.

A good article on the subject:

[http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html](http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html)

---

### Post by mastablasta on 2012-08-21
here are the links to torrent files for knoppix: [http://torrent.unix-ag.uni-kl.de/](http://torrent.unix-ag.uni-kl.de/)

select the one with most seeders.

> **25tom said:**
> Sorry, no, I don't know that much about bit-torrent...

you donwload a torrent file and then if you have ubuntu double click it. it hsould start transmission torrent client that will download the torrent file. if oyu are in windows use utorrent or simialr client (install it first) and then double click the downloaded file.

if the torrent is not downloading make sure you have ports forwarded on your router. torrent is not just downloading it's sharing parts of the file at the same time. so others need to get access to it.

final note - make sure you limit the bandwith to suitable level. too much bandwidht and too many people will use it and you will DDOS yourself :-)

---

