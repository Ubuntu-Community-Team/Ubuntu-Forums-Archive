---
title: "Ubuntu 8.10 - USB Startup Disk - not sure what is really supposed to happen"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by chipmaker on 2008-11-05
Hello,

I am a Linux and Ubuntu newbie. I want to make a bootable USB drive and now that 8.10 has an automated function for making that, I tried to do it last night. I created a bootable USB drive after running a LiveCD (made from burning an ISO downloaded from a local server (Switch, if I'm not mistaken). I followed the instructions from Pendrivelinux.com ([http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/)). But I think I'm running into some problems when I try to boot from the USB now. This is what happens (I'm running a Dell Latitude D630 laptop):

1. When I power on the laptop, I have to press F12 and select "booting from USB storage device". My USB drive is already plugged in even before I power on.

2. I select "English" from the list of languages.

3. At this point, I am presented with a menu screen and I have the choice of selecting either (1) Try Ubuntu without any change to your computer; or (2) Install Ubuntu.

When I select the first option, I get a screen with ASCII text saying "Loading. Please wait." on top, and some verbage about Ubuntu being free software and having no guarantees, etc. At the bottom of the screen, there seems to be a command line saying "ubuntu@ubuntu:~$". Nothing else happens even if I press ESC. At this point, I have to power the system off.

When I select the second option, I get through to Ubuntu booting up and a screen about partitioning the hard disk. I then press Quit and Ubuntu OS fully loads. At this point, I seem to be a Live Session User.

Is this normal or is something else supposed to happen? Can I just boot in completely into Ubuntu without going through the selections?

Nevertheless, I was able to use Ubuntu off from the LiveCD and I was able to do what I want to do, like connect to the wireless router, connect to the Internet, and try using OpenOffice. Once I'm able to get fully comfortable with using Ubuntu, I plan to install it in the laptop I plan to buy this Christmas.

Many thanks and I hope you can help.

---

### Post by seshomaru samma on 2008-11-05
I think what happened is that you created an installer on the USB and not an installation. That is yo have a Live CD on your USB and you are interested in a full installation on your USB, am I correct?

---

### Post by chipmaker on 2008-11-05
> **seshomaru samma said:**
> I think what happened is that you created an installer on the USB and not an installation. That is yo have a Live CD on your USB and you are interested in a full installation on your USB, am I correct?

Hello seshomaru samma,

Yes, that is the idea. I want to boot Ubuntu using a USB pendrive. I thought the procedure described in pendrivelinux.com is supposed to do that... I'm not sure if this is supposed to be the endresult though. :confused:

---

### Post by philinux on 2008-11-05
Did you follow this tutorial?
[http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/)

---

### Post by chipmaker on 2008-11-05
> **philinux said:**
> Did you follow this tutorial?
[http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/)

Hello philinux,

Yes, that is the tutorial I followed. However, I'm not sure why this is happening:

> 3. At this point, I am presented with a menu screen and I have the choice of selecting either (1) Try Ubuntu without any change to your computer; or (2) Install Ubuntu.

When I select the first option, I get a screen with ASCII text saying "Loading. Please wait." on top, and some verbage about Ubuntu being free software and having no guarantees, etc. At the bottom of the screen, there seems to be a command line saying "ubuntu@ubuntu:~$". Nothing else happens even if I press ESC. At this point, I have to power the system off.

I'm under the impression that I can boot straight off from the USB flash drive once I'm done.

---

### Post by philinux on 2008-11-05
Like it says in step 7.

[LIST=1]
[*]Once the installation is complete, **simply remove the CD**, restart your computer and set your boot menu or BIOS to boot from the USB device
[/LIST]
 **If all goes well**, you should now be booting from Ubuntu 8.10 on your USB flash drive, automatically saving changes you make to the casper-rw loop file as you go.

I would repeat the process. It sounds like it it failed if it's dumping you to the command prompt.

You could try the command 
startx
when it dumps you to the command line.

---

### Post by chipmaker on 2008-11-05
> **philinux said:**
> Like it says in step 7.

[LIST=1]
[*]Once the installation is complete, **simply remove the CD**, restart your computer and set your boot menu or BIOS to boot from the USB device
[/LIST]
 **If all goes well**, you should now be booting from Ubuntu 8.10 on your USB flash drive, automatically saving changes you make to the casper-rw loop file as you go.

I would repeat the process. It sounds like it it failed if it's dumping you to the command prompt.

You could try the command 
startx
when it dumps you to the command line.

I will definitely try to doing it all over tonight.

One thing that I should say, though... Because I'm trying this on a company laptop, access to the BIOS is restricted. What I did was to press F12 to manually select booting from a USB drive option. I wonder if this has anything to do with it. Unfortunately, I do not have access to a computer where I can play around with the BIOS.

---

### Post by fornix on 2008-11-05
Installing linux in a USB drive is not recommended due to repeated reads and writes.
This will shorten the life of ur USB drive.

---

### Post by snowpine on 2008-11-05
> **fornix said:**
> Installing linux in a USB drive is not recommended due to repeated reads and writes.
This will shorten the life of ur USB drive.

This is a myth--many of us on the forums are running linux on a thumb drive with no problems--and besides, even if they do wear out in, say 3 years instead of 5 years, they are very inexpensive to replace. :)

---

### Post by fornix on 2008-11-05
> **snowpine said:**
> This is a myth--many of us on the forums are running linux on a thumb drive with no problems--and besides, even if they do wear out in, say 3 years instead of 5 years, they are very inexpensive to replace. :)

Most of them say they will give lifetime warranty. Transcend says so. Have to try asking them for a replacement after say 3 years...

---

### Post by C.S.Cameron on 2008-11-05
If you are installing to USB from Windows and all you require is an install USB, not persistent, try Unibootin.
It is quick to use and simple.
The theory that installing Ubuntu to flash drive wears them out should be sent to Myth Busters, a lot of people talk about it but I have never heard of it actually happening.

---

### Post by chipmaker on 2008-11-05
> **philinux said:**
> Like it says in step 7.

[LIST=1]
[*]Once the installation is complete, **simply remove the CD**, restart your computer and set your boot menu or BIOS to boot from the USB device
[/LIST]
 **If all goes well**, you should now be booting from Ubuntu 8.10 on your USB flash drive, automatically saving changes you make to the casper-rw loop file as you go.

I would repeat the process. It sounds like it it failed if it's dumping you to the command prompt.

You could try the command 
startx
when it dumps you to the command line.

Hello,

I restarted the process of creating a USB startup disk following the instructions described in pendrivelinux.com ([http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/)). It worked somewhat better this time. I still have to go through this process:

> 1. When I power on the laptop, I have to press F12 and select "booting from USB storage device". My USB drive is already plugged in even before I power on.

2. I select "English" from the list of languages.

3. At this point, I am presented with a menu screen and I have the choice of selecting either (1) Try Ubuntu without any change to your computer; or (2) Install Ubuntu. 

I selected option 1, and Ubuntu booted up. However, it still shows as "Live session user" on the upper right hand corner. Since this is the first time I'm using Linux and Ubuntu, I'm not really sure if I'm doing this correctly. I'm wondering why I am not being prompted to create a user account and how I can log in with user account and password.

---

### Post by C.S.Cameron on 2008-11-05
You should be able to create an account using Users and Groups.
You can then click Live session user at the top right to log on.

---

### Post by fornix on 2008-11-06
> **C.S.Cameron said:**
> The theory that installing Ubuntu to flash drive wears them out should be sent to Myth Busters, a lot of people talk about it but I have never heard of it actually happening.
How far from truth you can be!
Flash drives can only allow finite writes. Its the limitation of technology used. It is not like you buy a usb drive and use it for your lifetime.
Just google out some pages about the technology used in implementing it and you would find out about the limitation.
[http://www.corsairmemory.com/_faq/FAQ_flash_drive_wear_leveling.pdf]("http://www.corsairmemory.com/_faq/FAQ_flash_drive_wear_leveling.pdf")
Also try wikipedia, howstuffworks, etc..

---

### Post by C.S.Cameron on 2008-11-06
> How far from truth you can be!
Flash drives can only allow finite writes. Its the limitation of technology used. It is not like you buy a usb drive and use it for your lifetime.
Just google out some pages about the technology used in implementing it and you would find out about the limitation.
[http://www.corsairmemory.com/_faq/FA...r_leveling.pdf](http://www.corsairmemory.com/_faq/FA...r_leveling.pdf)
Also try wikipedia, howstuffworks, etc.. 

Wish I could keep a mechanical drive working ten years.

When I run Ubuntu from flash drive, everything runs in RAM on my computer, I have never been able to get a blip when watching swap usage.
It seems that the only time I see writes to the flash drive is when saving, changing settings, installing applications and when downloading stuff.
Working on a 10 meg file I would have to save it 100 times in a day to get 1 gig of writes, at that rate the drive should last at least 30 years.

---

