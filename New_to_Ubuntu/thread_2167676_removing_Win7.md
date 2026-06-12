---
title: "removing Win7"
date: 2013-08-14
forum: New to Ubuntu
---

### Post by norberto2 on 2013-08-14
Hi today I install Ubuntu 12 and I was thinking in removing win7(if possible) but i dont know how. I want to have only ubuntu in my laptop.

---

### Post by papibe on 2013-08-14
Hi norberto2. Welcome to the fourm ):P

Here is a good start: [How To Remove Windows]("https://help.ubuntu.com/community/HowToRemoveWindows"). Let us know how it goes.

Come here often and have fun.
Regards.

---

### Post by norberto2 on 2013-08-14
it looks like I deleted everything from the laptop and now when I turn it on it says something about not having bootable device :confused:
What should i do?????

---

### Post by papibe on 2013-08-14
Use the Ubuntu installation media as a live CD/USB and try reinstalling grub using Boot Repair. [Here]("https://help.ubuntu.com/community/Boot-Repair")'s a guide.

Regards.

---

### Post by norberto2 on 2013-08-14
I did the Boot repair and this is what i got [http://paste.ubuntu.com/5987162](http://paste.ubuntu.com/5987162).
When I restart it still says no bootable device.....

---

### Post by DuckHook on 2013-08-14
Since it is a virgin install, you may be best served by just reinstalling Ubuntu. It will probably take you more time trying to chase down the problem than just reinstalling.

---

### Post by norberto2 on 2013-08-15
I decide to do the install but nos ti appear a screen GNU GRUB
With 4 options
Ubuntu with Linux generic
Ubuntu recovery mode
And 2 diferent memory test
If i click in the Ubuntu it says Fatal: could not load /lib module no sush file or directory....
What should I do now???


so I decided to reinstall ubuntu again, lets see what happens....

---

### Post by norberto2 on 2013-08-15
Nop it still appear. I dont know what to do......:(:(

---

### Post by Y^2om&amp;#7sgP on 2013-08-15
FWIW when I went from Win7 to pure Ubuntu I started (after doing back-up/copy of data) by using Boot n Nuke

Wipe the HDD completely then installed Ubuntu onto a virgin drive

Have done this now a few times on different machines.

---

### Post by norberto2 on 2013-08-15
How do i wipe the HDD??

---

### Post by Y^2om&amp;#7sgP on 2013-08-15
Get Boot and Nuke from

[http://www.dban.org/](http://www.dban.org/)

**_CAUTION_, it __[B]WILL** delete everything, so make sure that you've backed everything up (I usually backup important stuff onto two mediums) and any external USB HDD's or sticks are removed because it'll wipe those as well (I found the hard way a while back :mad: )[/B]

You'll need to burn it onto a cd, then boot from it.
At the prompt type 'autonuke' and it completely wipes the HDD

It usually claims to take several hours to wipe depending on the size of your HDD, but I've found that 5-10 minutes is good enough to give a fresh HDD for installation.

---

### Post by norberto2 on 2013-08-15
gonna try it.......lets see what happen..... It does not let me start(usb live/boot thing) the autonuke it says that there is a file missing
Could not find ramdisk image: /ubninit

---

### Post by crazymonkey05 on 2013-08-15
when you insert the live cd and boot it try going through the install till you get the option to do install or advanced options. choose advanced options and wipe the drive that win 7 was on

---

