---
title: "WINE, how do you install an app?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by packrat on 2008-06-04
Here's a post from another: "You can run Quicken under WINE. I run Quicken 2007 Home & Business and it works great."


Have WINE installed. Being new, how do I install Quicken? Insert Quicken app in DVD drive? Open WINE and select Configure then ADD app?

New to this so I need the help of someone that's done it and got it working...blow by blow...

Thank you.

---

### Post by django0909 on 2008-06-04
cd to the directory the setup file is in, and then do 

```
sudo wine setup.exe
```

Of course, change setup.exe for the appropriate name!

---

### Post by AnRa on 2008-06-04
Just double click the installer! :)

Don't use [FONT="Courier New"]sudo[/FONT] with wine!

---

### Post by Lord Xeb on 2008-06-04
You also want ot have have wine setup to run the proper windows emulation. 


To do so, go Wine>Wine Configuration

then go to the applications tab and select the windows version you want to emulate.

---

### Post by Lord Xeb on 2008-06-04
You cannot do that, it will bring up an message saying that it is a MS-DOS program/script that cannot be ran. You have to right click on the installer then select  "run with windows emulator"

---

### Post by Joeb454 on 2008-06-04
You *should* just be able to double click the setup file :)

---

### Post by django0909 on 2008-06-04
> Don't use sudo with wine!

Oh yeah, sorry. Without the sudo.

As a pointer though, if I double click an installer it won't let me run the file in wine. That might be because I haven't got it installed properly but then I prefer to do things with the terminal if I can.

---

### Post by packrat on 2008-06-04
Is it possible to either open the app in the DVD drive and find the *.exe file...or, copy all files on the disk to a folder labeled to identify the files using the exe file...then go to WINE Configuration the Applications Tab select WinXP as that's the OS for the Quicken package I want to install...lastly, select the executable file then "open?" Is this the process?

Thanks.

---

### Post by JoshuaRL on 2008-06-04
Yeah, that should work.

---

### Post by chrisdugdale on 2008-06-05
Sounds like playonlinux is designed for you. It is in System>Administration>Synaptic Package Manager This is what it says about itself:
PlayOnLinux is a front-end for wine. It permits you to install Windows Games and softwares on Linux.

Installs easily, I don't have the need so haven't tried actually using it myself.

---

### Post by hyper_ch on 2008-06-05
> **django0909 said:**
> Oh yeah, sorry. Without the sudo.

How about editing your previous post and remove the sudo? Some people never read the whole thread ;)

---

### Post by Joeb454 on 2008-06-05
> **hyper_ch said:**
> How about editing your previous post and remove the sudo? Some people never read the whole thread ;)

You mean there's stuff on the 1st page? ;)

---

### Post by packrat on 2008-06-07
> **packrat said:**
> Is it possible to either open the app in the DVD drive and find the *.exe file...or, copy all files on the disk to a folder labeled to identify the files using the exe file...then go to WINE Configuration the Applications Tab select WinXP as that's the OS for the Quicken package I want to install...lastly, select the executable file then "open?" Is this the process?

Thanks.

Well, it doesn't work. Followed my own advice and nothing happens...how about some basic instruction? Thanks.

---

### Post by JoshuaRL on 2008-06-09
> **packrat said:**
> Well, it doesn't work. Followed my own advice and nothing happens...how about some basic instruction? Thanks.

Have you tried looking on AppDB to see if there is any specific installation steps that need to be taken?  Wine has been doing pretty well lately and you might want to check it out.

Also, I would seriously suggest you install wine from their repos, not the Hardy one.  They're on 1.0rc4, and it's pretty sweet.  [This page on their site](http://www.winehq.org/site/download-deb) should help you get the newest version installed.  And that should keep you updated too.

---

