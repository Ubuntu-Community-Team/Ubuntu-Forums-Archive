---
title: "[SOLVED] Ubuntu 8.10 - How to I activate Nvidia Driver when Hardware driver GUI Fails"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by sharkster2007 on 2008-10-31
Hiya everyone

I seem to be one of a lot of new 8.10 Users with this problem with Nvidia graphics cards.

Some of us have the drivers installed and dependancies confirmed as ok but the System>Administration>Hardware Drivers GUI fails to activate them.

Is there a command line way to activate them manually. I believe this issue to be very serious as it putting some new users off the idea of using ubuntu.

Please help us out if you can

---

### Post by talsemgeest on 2008-10-31
As far as I know, it is just a package that you need to install. Do a search in synaptic for Nvidia and install the package that looks like the driver. Sorry, I can't remember what the package is called.

---

### Post by crjackson on 2008-10-31
> **sharkster2007 said:**
> Hiya everyone

I seem to be one of a lot of new 8.10 Users with this problem with Nvidia graphics cards.

Some of us have the drivers installed and dependancies confirmed as ok but the System>Administration>Hardware Drivers GUI fails to activate them.

Is there a command line way to activate them manually. I believe this issue to be very serious as it putting some new users off the idea of using ubuntu.

Please help us out if you can

System>Admin>Software sources

Enable all the repositories except Proposed Updates. Reload and try the Hardware Drivers GUI again (You have to reboot afterwards).

---

### Post by sharkster2007 on 2008-10-31
[COLOR="SeaGreen"]INTERNET USERS: POSSIBLE FIX - Credit to Greyarea2 not myself[/COLOR]

On another thread Greyarea2 said;

> Here's my fix:

- Go to System > Administration > Software Sources

- Go to the Third-Party Software tab

- You should see 2 checkboxes; check both.

- Go to System > Administration > Update Manager

- Check for and apply updates. This will take awhile. I reccomend a good book to pass the time.

- Now try again to activate the drivers. If your problem is the same as mine, it should now work.

It seemed to refer too third party software repositories needed to tie in the driver 0n 8.10

Any idea what these files or .deb packages are?
[COLOR="Red"]
PS: I Personally don't have access to the internet so I need to download the missing files on a Windows Pc Manually on a usb stick, I can't use the update manager thats why I am asking this.[/COLOR]

---

### Post by crjackson on 2008-10-31
> **sharkster2007 said:**
> On another thread Greyarea 2 said;



It seemed to refer too third party software repositories needed to tie in the driver 0n 8.10

Any idea what these files or .deb packages are?
[COLOR="Red"]
PS: I Personally don't have access to the internet so I need to download the missing files on a Windows Pc Manually on a usb stick, I can't use the update manager thats why I am asking this.[/COLOR]

You need to connect that computer to the internet for this (at least that is the BEST way). You could find other ways but you could also pull out your last hair doing it if you're kind of new.  

If you decided to do it the hard way however, you can download the nVidia driver from their site and install as follows:

Stop the X server with this command:

**sudo /etc/init.d/gdm stop**

then run the installer with:

**sudo sh nvidia-file-name.run**

then to restart X:

**sudo /etc/init.d/gdm start**

By the way, gdm stands for "graphical display mamanger" which on my system is the "X" windows manager.

There's no PROMISS this will work. It should, but since you aren't connected to the internet and don't have access to updates and possible dependancies I have no way of knowing. If I were you, I'd disconnect that computer and drag it to an internet connection to get all the updates and just install the driver the easy way.

---

### Post by sharkster2007 on 2008-10-31
Thanks crjackson

I have the the .deb files for the Nvidia 173 drivers installed (all dependancies are ok), its just the hardware drivers enabling I have the problem with.

I've tried the .run file thing before it caused me to almost give up on ubuntu (I actually did but returned on 8.10's release).

Is there a command line to force the driver into enabling outside of the hardware drivers GUI? I would be willing to try this.

The internet idea is sound but sadly not an option for me (think next time i'll buy a laptop instead LOL).

I thank you for trying to help me though, it's much appreciated :-)

---

### Post by talsemgeest on 2008-10-31
So the driver is already installed? If that is the case, there is no reason to activate it, you should have all of the benefits.

---

### Post by sharkster2007 on 2008-10-31
[COLOR="Lime"]NONE INTERNET CONNECTED USERS: MANUAL SOLUTION[/COLOR]

Web source for .deb packages is [http://packages.ubuntu.com/intrepid/nvidia-173-kernel-source]("http://packages.ubuntu.com/intrepid/nvidia-173-kernel-source")

> I have installed [COLOR="SeaGreen"]dkms_2.0.20.4-0ubuntu_all.deb[/COLOR] & [COLOR="SeaGreen"]nvidia-173-kernel-source_173.14.12-1-0ubuntu4_i386.deb[/COLOR] as these are the only parts required by 8.10 the other dependancies are already installed as standard.

I now assume that my driver is installed and in place but when I go to SYSTEM>ADMINISTRATION>HARDWARE DRIVERS and select NVIDIA ACCELERATED GRAPHICS DRIVER (VERSION 173)and click enable, it seems to want to go to the internet (which i haven't got) but i don't know why as the driver and its dependancies are installed already.

UPDATE: MISSING FILE LOCATED - PROBLEM NOW SOLVED 

The missing file is [COLOR="SeaGreen"]nvidia-glx-173_173.14.12-1-0ubuntu4_i386[/COLOR] from the same site as above with this installed go to:

SYSTEM>ADMINISTRATION>HARDWARE DRIVERS select NVIDIA ACCELERATED GRAPHICS DRIVER (VERSION 173) click enable, an arrow sholud appear asking you to restart your system

After restarting your system the driver will enable, select your desktop effects from appearances and your done enjoy

PS: double click the .deb files on desktop to install them

[COLOR="DeepSkyBlue"]*UPDATE 6th November 2008: I now have a better manual solution for Nvidia drivers & activation, compiz settings, nvidia settings and 3d cube set-up located below.*[/COLOR]

[http://ubuntuforums.org/showthread.php?t=973038&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=973038&highlight=nvidia)

Sharkster2007

---

### Post by phidia on 2008-10-31
From a terminal you can run/enter "glxgears" and see if you're getting a decent fps or not-also look in the device > driver section of /etc/X11/xorg.conf to see which driver is in use there.

You didn't say what model nvidia card you have but the legacy cards are no longer supported in 8.10.

Well xorg since hardy with the change to xorg 7.4 is really confusing see this [thread here]("http://ubuntuforums.org/showthread.php?t=965548&page=2"), and hope that helps.

---

### Post by sharkster2007 on 2008-10-31
Sorry phidia

Your quite correct My card is a Nvidia 6600GT (AGP) Version.

PC Specs: 2.4 Pentium 4, 1gb Ram, 3 HDD's 160gb IDE (Windows XP), 80gb IDE (Ubuntu), 160GB Firewire. (MACHINE IS DUAL BOOT CAPABLE)

---

### Post by cariboo on 2008-10-31
I am just in the process of installing Intrepid final. I had a heck of a time downloading the drivers from my preferred mirror. I finally had to change to the main server in order to download the drivers. to make sure you have downloaded all the files go to /var/cache/apt/archives/partial and see if there is anything there. If there is nothing there backup to /etc/cache/apt/archives and see if you have the following files:

```
nvidia-1XX-kernel-source_1XX.80-0ubuntu2_amd64.deb
nvidia-glx-1XX_1XX.80-0ubuntu2_amd64.deb
nvidia-settings_1XX.78-0ubuntu2_amd64.deb

```

where the XX is the driver you selected to download, it could be 177 or 173. If you have the above three files installed you should have a working Nvidia driver.

Jim

---

### Post by sharkster2007 on 2008-10-31
I've just got that to work on my PC 30mins ago cariboo907 you are right that is the correct way to get it to work I can confirm that too

I've finally done it not using the internet to update 

AT LAST, IT WORKS :-)

---

### Post by sharkster2007 on 2008-11-01
Greyarea2 has the internet connected solution [http://ubuntuforums.org/showthread.php?t=965741]("http://ubuntuforums.org/showthread.php?t=965741")
and now I've added my sharkster2007 manual one for none internet connected users.

---

### Post by sharkster2007 on 2008-11-06
6th November 2008 I now have a better manual solution for Nvidia drivers & activation, compiz settings, nvidia settings and 3d cube set-up located here.

[http://ubuntuforums.org/showthread.php?t=973038&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=973038&highlight=nvidia)

Sharkster2007

---

