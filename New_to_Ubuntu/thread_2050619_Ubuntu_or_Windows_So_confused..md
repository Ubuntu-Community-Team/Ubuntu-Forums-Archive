---
title: "Ubuntu or Windows? So confused."
date: 2012-08-31
forum: New to Ubuntu
---

### Post by rodtaylor on 2012-08-31
Hi!

I have just bought a Toshiba Satellite P850. Before that I used my mother's in law laptop (since I didn't have any at the time) and installed Wubi on original Vista (I hate Vista, fyi). Since then, I love Ubuntu!! Now that I've got my own laptop, that came with Win7 Home Premium installed, I am so confused to choose between Ubuntu or Win7. 

The reason being is that I am worried that Ubuntu won't be able to utilize the maximum ability of my laptop, like the dual graphics, the card reader (that I'm still unable to make it work btw), etc.

Can anyone please advise me on what to do?

Thanks before!

---

### Post by The Cog on 2012-08-31
I would suggest that you use wubi to install into windows for now, so that you can test out. If you don't like you can just uninstall, if it all works OK, then reinstall Ubuntu properly, erasing windows.

---

### Post by krustenBrot on 2012-08-31
[s]You could also try to install Ubuntu next to Vista and see how it goes. It is quite simple and you can choose which OS you like to use on boot.[/s]
See **davetv**s post. Did not know the benefits of install over wubi as i never tried wubi before. 

I got dual Graphics as well and I am using Bumblebee to use them. Works like a charm, although you have to run the programs with a prefix to utilize the Nvidia card.
[**Here**]("https://wiki.ubuntu.com/Bumblebee") is the Ubuntu Wiki entry for bumblebee. :)

---

### Post by davetv on 2012-08-31
I agree with The Cog - but further - try a wubi install firstly. If that is working, try running ubuntu off a bootable medium (cd/usb) in "live cd" mode.

If all is working to expectations (wireless, usb, sound, video, other devices) then I would consider setting ubuntu up as an alternate boot to win7 giving you a choice Ubuntu or Win7) at bootup time.

This will enable the linux system to run way more quickly than a wubi install.

There are plenty of tutorials/posts/advice on how to do this.

---

### Post by doktorOblivion on 2012-08-31
I agree with the other posts regarding wubi, try that first.  And there are plenty of posts regarding a full install or dual boot setup.  HOWEVER, I would caution you that what ever you decide to do, BACKUP your windows system prior to installing.  You can either use Win backup/restore to do this or some other program like Acronis TrueImage.  If something happens you will be thankful you did.  It is also handy if you need to move your Win7 partition elsewhere to make room and most of all your entire configuration is saved.  I recently did this to move my Win7 image from HDD to SSD and it worked fine, after a few necessary tweeks.  Have fun and good luck.

---

### Post by lopean on 2012-08-31
> **rodtaylor said:**
> Hi!

The reason being is that I am worried that Ubuntu won't be able to utilize the maximum ability of my laptop, like the dual graphics, the card reader (that I'm still unable to make it work btw), etc.

Can anyone please advise me on what to do?

Thanks before!

I have dual ati graphics cards (crossfired) on my system. I was able to successfully install the drivers and get everything working without much hassle. Heres the thread on that adventure:[http://ubuntuforums.org/showthread.php?t=2050320]("http://ubuntuforums.org/showthread.php?t=2050320") . Can't help you with the card reader though, I'm sure someone can get you going if you open up a thread to troubleshoot that. By the way I dual boot between windows 7 and Ubuntu. There are some tutorials on getting that setup correctly...and here they are! [http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/]("http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/") and [http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/) . Windows will be with me until steam for linux goes native. GL!

---

### Post by krustenBrot on 2012-08-31
Do not mix up Crossfire with Optimus! As far as I know Crossfire links 2 Graphiccards - while Optimus has 2 standalone graphic cards which work independently. One "power saving" card most common Intel HD series and a more powerful card e.g. Nvidia GTxxx . The latter will only be used by single programs which need the extra power.

---

### Post by I2k4 on 2012-08-31
I'd agree should try running them in parallel, even test drive various Ubuntu or Mint versions with Persistent Live USB (Live USB Creator or Pendrive installer) on a thumb drive.  

I've kept Windows handy for several reasons:  a) I would need "Samba" for networking with other Windows machines and can't be bothered to figure it out, a) I have regular need for some MS important Office spreadsheets with sophisticated macros, etc. that cannot work with LibreOffice, Google Docs, etc. and c) there are some photo and video post-processing apps I like and am familiar with in Windows.  

Finally, except possibly for the LTS versions I haven't tried, I've found the release / support cycle for Ubuntu too short:  I don't want to install a new OS in order to keep receiving updates and the current versions of software I'm using (this is what happened on my dual boot install of version 10 on my netbook - no more updates less than two years after installing, and I would have to replace with a much slower OS. By comparison - with no fuss or muss or performance hit - I'm still getting current software and OS updates for XP ten years after adopting it.)

---

### Post by 1clue on 2012-08-31
My fiancee has an older satellite (not that old but also vista) and kept getting viruses.

I bought a second drive of the same size.  I pulled the orginal drive out and put it in the esd bag from the new drive, then popped the new drive in the computer.

This way, I have the original hard disk in case it doesn't work out, or in case we sell the laptop.  We also have an xubuntu drive with no worries about trashing anything.

In her case, she barely used any of the 320g drive on her Windows session, and is currently using no more of the Linux drive.

IMO this is the safest (most reversible) way, if you can afford that second drive.  If at some point you decide you Do Not Ever need the original operating system, you can buy an enclosure and stuff the original drive in it.  Then you can format it to whatever you want.

---

### Post by rodtaylor on 2012-09-11
Thanks a lot for the advice!! I think I'm going to stick with Wubi now. It gives me the flexibility and once I'm good with Linux, I will install it for good.:)

---

