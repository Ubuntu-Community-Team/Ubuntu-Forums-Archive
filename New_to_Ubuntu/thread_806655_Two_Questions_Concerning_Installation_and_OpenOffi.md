---
title: "Two Questions Concerning Installation and OpenOffice"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by jacobh on 2008-05-25
Hello all!

First of all, excuse the long post and my weak grasp of Ubuntu terminology...

I installed Ubuntu a few days ago on my old AMD64 desktop computer, and I have thoroughly been enjoying it so far. I really haven't had too much in the way of problems either... everything is very intuitive. I liked it so much in fact that I talked my friend into upgrading his Windows XP laptop to Ubuntu, and this is where the problems start. 

My friend spilled wine all over his laptop a few months ago, but it has been working fine since, except for his CD-drive. So in order to get Ubuntu working we used UNetbootin to install without a CD ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)). It seemed to be working fine, but upon completion of the setup we discovered that Unetbootin had downloaded and installed Ubuntu 6.06 and what's more, it seems that there is no graphical user interface. The system boots directly into the terminal. I tried using some sudo commands in the terminal, but we can't get a connection to the internet.

So my questions are:
1. How do we upgrade to Ubuntu 8.04 given the condition of the laptop (from Ubuntu 6.06, no CD, no GUI, maybe no internet)?
2. Is there a way to redo the entire Ubuntu installation without using UNetbootin, but also without using a CD?
3. and totally unrelated: Can I get OpenOffice 3.0 Beta to work on an AMD64 Ubuntu computer (it seems that it only supports 32-bit OS)?

I hope your patience hasn't failed you and that we together may find a solution to this devilish problem.

---

### Post by shifty_powers on 2008-05-25
right, do you have a usb port on the laptop and a spare usb stick?

---

### Post by hyper_ch on 2008-05-25
All the options from installing ubuntu:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

but upgrade from 6.06 without cd, without internet seems impossible to me...

dunno about OOo... you could compile it from source if you want to ;)

---

### Post by shifty_powers on 2008-05-25
could you not use the 32-bit deb and force arhitecture during installation?

---

### Post by jacobh on 2008-05-25
stuff at my disposal:

- external HDD 320gb
- dualbooted Ubuntu 8.04 / Windows XP AMD 64 desktop
- windows XP laptop
- 2gb USB stick
- my friend's laptop does have a USB port, yes

regarding OOo: what exactly does 'compiling from source' entail?

---

### Post by shifty_powers on 2008-05-25
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

you will have to go into the bios of the laptop to enable it to boot from the usb stick ;)

---

### Post by jacobh on 2008-05-25
> **shifty_powers said:**
> could you not use the 32-bit deb and force arhitecture during installation?

I think I did download the 32-bit deb, but after extracting I try to right click the deb packages and select "open with package installer" (if my memory serves me correct) and I get an error message saying it's the wrong architecture.

and about the Unetbootin installation: I selected the 'image' option for installation, instead of selecting either 'kernel' or 'distribution'. I had already downloaded an ISO image of ubuntu 8.04.

---

### Post by shifty_powers on 2008-05-25
yeah you will do, as it is a 32-bit deb on a 64-bit system.

however, you can force it to install anyways.

brb on that one ;)

---

### Post by shifty_powers on 2008-05-25
```
sudo dpkg -i --force-all package_name.deb
```

you would need to run that command from the terminal, from wihtin the oo folder, with, obviously, the right package name...

and this

[http://ubuntuforums.org/showthread.php?t=474790&highlight=force+32-bit](http://ubuntuforums.org/showthread.php?t=474790&highlight=force+32-bit)

might be useful ;)

---

### Post by jacobh on 2008-05-25
i extracted by right-clicking the downloaded OOo file and clicking extract here, which creates another folder on my desktop with all the deb files within. i think there are 46. does this mean i write the command

sudo dpkg -i --force-all package_name.deb 

46 times with each individual package name? is there really not an easier way to do this?

---

### Post by shifty_powers on 2008-05-25
heh, you don't have to do that for all of them.

there is one deb that will do the whole install for you.

and any reason why you MUST have oo3? whats wrong with 2.4? ;)

---

### Post by shifty_powers on 2008-05-25
> **jacobh said:**
> i extracted by right-clicking the downloaded OOo file and clicking extract here, which creates another folder on my desktop with all the deb files within. i think there are 46. does this mean i write the command

sudo dpkg -i --force-all package_name.deb 

46 times with each individual package name? is there really not an easier way to do this?

and no, you replace package_name.deb with the deb name.

eg.

sudo dpkg -i --force-all oo3.deb

---

### Post by jacobh on 2008-05-25
the reason i want OOo 3.0 beta is because i'm having trouble opening some powerpoint *.ppt files with the OOo 2.4 Presentation app. i thought that maybe having the newest version would solve the problem. any other workarounds? the error message i get is "general input/output error"

---

### Post by shifty_powers on 2008-05-25
try

[http://www.mediaconverter.org/](http://www.mediaconverter.org/)

you can use it to convert from the *.ppt file to a *.odp file ;)

---

### Post by jacobh on 2008-05-25
what is the terminal command to run something from the CD-drive? i think the CD-drive may be working again...

another update: also found internet.

can the installation be made easier given these developments?

thanks

---

### Post by jacobh on 2008-05-25
> **shifty_powers said:**
> heh, you don't have to do that for all of them.

there is one deb that will do the whole install for you.

and any reason why you MUST have oo3? whats wrong with 2.4? ;)

which deb will do the whole install for me? i've tried three so far, it seems to be installing the particular package but not them all.

i tried the first three 'core' debs and also one called 'ooobasis3.0-en-us_3.0.0-2_i386.deb'

any ideas?

---

### Post by shifty_powers on 2008-05-25
heh, will download and get back to you ;)

---

### Post by jacobh on 2008-05-25
thanks so much for your help so far

concerning the laptop:
i think the cd-rom drive is alive. what are the steps i must take to boot from the cd-rom drive? can i do it from within the terminal? or should i do it before ubuntu is loaded?

---

### Post by shifty_powers on 2008-05-25
if you mean you want to boot a live-cd, then you need to go into the bios and change the boot order, so that the cd-drive comes before the hard drive.

can't help you beyond that as i don't know the bios of the laptop ;)

---

### Post by shifty_powers on 2008-05-25
right, cd into that directory in the terminal. then

```
sudo dpkg -i --force-all *.deb
```

that should install all the debs in one go for you, forcing the 32-bit architecture ;)

---

### Post by jacobh on 2008-05-26
ok that seemed to work. but there is nothing new in my applications menu. where do i find the apps?

---

### Post by jacobh on 2008-05-26
i managed to get ubuntu 8.04 on the laptop using the USB stick method prepared with the Live USB program created by probono: [https://launchpad.net/liveusb](https://launchpad.net/liveusb) 

so thanks for all the help on this matter. 

still can't find OpenOffice 3.0 but maybe i should be asking in the forum for 64-bit users.

---

### Post by shifty_powers on 2008-05-26
heh, no it doesn't add itself to your app menu.

you'll need to create a launcher with the command:

```
/opt/openoffice.org3/program/soffice
```

;)

---

