---
title: "Looking to Remaster an Existing iso file of Lubuntu"
date: 2014-02-28
forum: New to Ubuntu
---

### Post by Javelin Dan on 2014-02-28
I would like to customize my own version of an existing iso of Lubuntu to make a bootable, installable DVD or USB. I first looked at a tutorial on "Ubuntu Customization Kit". It looked like it had a nice GUI and was fairly easy to use (a must for me). But when I installed it and clicked on it in "System Tools", all I got was an open terminal window with no script, not even a flashing cursor. I don't know what to do with that.

I did some more Googling, and read good things about "Reconstructor" a web app that is supposed to allow the same function. When I tried to log on the web site, it failed to connect. I then found multiple threads on the Ubuntu forums, but every time I tried to follow one, it said "software has been removed". 

I've also played with "Clonezilla", but I think it just creates a new iso out of my existing system which is too large for a DVD. I could use some help.

---

### Post by thenh813 on 2014-02-28
Have you heard of remastersys?
It is console based and also has a gui, but really easy to use.



Usage of remastersys 3.0.4-2 is as follows:
 
   sudo remastersys backup|clean|dist [cdfs|iso] [filename.iso]
 
 
Examples:
 
```

   sudo remastersys backup

```
                                        (to make a livecd/dvd backup of your system)
```

 sudo remastersys backup custom.iso

```
(to make a livecd/dvd backup and call the iso custom.iso)
```

 sudo remastersys clean

```
(to clean up temporary files of remastersys)
```

 sudo remastersys dist

```
(to make a distributable livecd/dvd of your system)
```

 sudo remastersys dist cdfs                                    

```
(to make a distributable livecd/dvd filesystem only)
```

 sudo remastersys dist iso custom.iso

```
(to make a distributable iso named custom.iso but only if the cdfs is already present)

   cdfs and iso options should only be used if you wish to modify something on the cd before the iso is created.  An example of this would be to modify the isolinux
   portion of the livecd/dvd.
 
I use:
 ```

sudo remastersys dist /home/<MYNAME>/Desktop/CustomLinux.iso

```

---

### Post by thenh813 on 2014-02-28
I could tell you how to add the repo, but to save you the trouble I uploaded the DEBs for you.
Install the core and GTK parts, then download the correct GUI.
The files are encrypted for security and I guarantee you I have not modified them.



Core Files: [https://mega.co.nz/#!YEBSVQRS](https://mega.co.nz/#!YEBSVQRS)
Password for Core Files: Z2-6_Gfc6pbgt5xo8yr5xKhIUt9LwB2mR4GzSGXqkNY

GTK Part: [https://mega.co.nz/#!ZQ4mFTQa](https://mega.co.nz/#!ZQ4mFTQa)
Password for GTK Part: vU-Bt9jTU1ajfHJgWd0YBHE5S-XYxfZ0NuShS33sfD0



GUIs:

i386 [32 BIT]: [https://mega.co.nz/#!kAwyDayJ](https://mega.co.nz/#!kAwyDayJ)
Password for i386 GUI: YdoQLAmsnJG9MXULg3WVjx0zINZ2W7w3iVWwFP1G5mQ

AMD64 [64 BIT]: [https://mega.co.nz/#!cUJEFKxQ](https://mega.co.nz/#!cUJEFKxQ)
Password for AMD64 GUI: lyrW4ETHS4N-xs1GlxNGNBxs9GtNNEFNc39SeWP6EqY



Please note: Install the GUI version for the CPU type you have, not both.


PS: Nice signature


EDIT: I noticed in another thread you already tried remastersys and had problems. I wonder if the version I linked to will have the same problems.

---

### Post by Javelin Dan on 2014-02-28
thenh813 - 

Thanks for offering a hand. Yeah, I did try and fail with Remastersys due to the file size. I tried to clone a customized version of Lubuntu I have on a separate partition. I know that Remastersys limits you to 4 GB or thereabouts, and when I opened Gparted to see how much real estate I was sucking up with that install, it was a little over 14 freakin' GB! I did load it down with Libre Office, Gimp, and a couple of different sound and graphics apps, but man..that really surprised me! I'm assuming that an iso file is somehow compressed and that's how a basic install fits on a DVD, so that's why I was looking for a way to customize an existing iso of Lubuntu. If you or anyone else has any other ideas, I'm all ears...

---

### Post by C.S.Cameron on 2014-02-28
I cut and pasted what I found here by Tachyons last week and it installed fine:

[http://askubuntu.com/questions/133272/how-do-i-install-remastersys](http://askubuntu.com/questions/133272/how-do-i-install-remastersys)

On 140214 Fragadelic posted in the Forums that Remastersys for 12.04 and 12.10 would remain at the repo for another year.
And should work with current versions of Ubuntu

---

### Post by Javelin Dan on 2014-03-01
C.S.Cameron -

 I actually did find this same tutorial and followed it, and I think Remastersys actually worked but I got a message at the end of the process that my file size was too big. Again, I believe with Remstersys you are limited to close to 4 GB, and my installation shows up in Gparted at a tick over 14GB. Thanks, though.

---

### Post by Javelin Dan on 2014-03-06
In the last couple of days I've discovered a few things about Remastersys. It turns out that the "Distribution" version does work for me. I knew this before, but what I didn't realize was that while I thought it only saved basic, default software like the master iso, it actually saved all my added software. Heavy hitters like the complete Libreoffice suite, Asunder, Gimp and Shotwell, Remastersys and others were all saved in the "Distribution" iso. Since this was a clean install on a seperate partition, about the only thing I can see that didn't get carried over was a few jpegs that I included for additional backgrounds. 

Here's the thing that confounds me: The "distribution" iso weighed in at 1.3 Gb - plenty small enough to burn to a DVD with room to spare. However, when I try to burn the "Backup" version with no more differences than listed above, it seems to run normally till I get a message at the end that the process failed because the file was too large (which as I understand it maxes out at about 4GB). Can anyone explain what makes the difference?

In any event, while Remastersys doesn't work exactly as I hoped (the installer is a little quirky), it works well enough to mark this thread as "solved". If anyone can shed some light, please enlighten me.

---

