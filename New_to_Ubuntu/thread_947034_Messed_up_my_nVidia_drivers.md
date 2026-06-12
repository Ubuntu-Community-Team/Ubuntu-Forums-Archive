---
title: "Messed up my nVidia drivers"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by Amorget on 2008-10-13
Hi all, I am having a real issue with my nVidia drivers in 8.04.  I first was trying to install the 177.80 drivers from nVidia, however I found that it didn't seem to work properly as I couldn't re-enable my desktop effects.  So then I made an attempt to install both the Envy and Ubuntu drivers.. and found that neither of them worked.

I then learned about the nvidia-installer --uninstall method... so I did that and it warned me the drivers had been messed with, but I continued.  However, now I cannot reinstall either the Envy or the Ubuntu "Hardware Drivers".  They keep exiting with an error like this: " subprocess pre-installation script returned error exit status 2"

Any ideas?

Thanks,
Douglas

---

### Post by eternalnewbee on 2008-10-13
Take a look here: **[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installation_of_ATI_and_nVidia_Graphics_drivers](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installation_of_ATI_and_nVidia_Graphics_drivers)**.
Hope this will help you.

---

### Post by Amorget on 2008-10-14
Unfortunately I cannot install the Restricted or Envy drivers, the nvidia drivers installed using this method:
[http://techstop.com.au/2008/05/hardy-nvidia-beta-drivers/](http://techstop.com.au/2008/05/hardy-nvidia-beta-drivers/)

Don't seem to work...

This really sucks, it is my work laptop.

---

### Post by eternalnewbee on 2008-10-14
Did you reboot the system? Sometimes changes only take effect after a reboot..

---

### Post by Amorget on 2008-10-14
Yes, basically after every change.

---

### Post by eternalnewbee on 2008-10-14
Then you'll have to wait for more experienced users to help you out.
Sorry I couldn't be of more help to you.
Patience is a virtue...

______________________________

Ubuntu 8.04 Gnome 2.22.2 2.6.24-19-generic
AMD Athlon(tm) XP 899.219 MHz 256 KB
GeForce 7300 GT

---

### Post by SteveNorman on 2008-10-14
Do you have nvidea-settings installed? if not do this:

a thorough guide on the new nvidia driver install by starcannon

```
Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from http://www.nvidia.com/Download/index.aspx?lang=en-us
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
	5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
	5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
	7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
	7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
		-------------------------------------------------------------------------------------------------------
		If you used Envy to attempt a previous nvidia install please run this command now before you go on:

		sudo dpkg -P envy 

		-------------------------------------------------------------------------------------------------------
		If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

		sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

		-------------------------------------------------------------------------------------------------------
		If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

		sudo nvidia-installer --uninstall

		-------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
	8.a) Okay were in Command Line only now, we have a little left to do in here.
	8.b)login:
	8.c)Password:

9) sudo /etc/init.d/gdm stop
	9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
	10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, you should also be able to enable desktop effects.
```

---

### Post by SteveNorman on 2008-10-14
BTW I forgot to add that this is very similar to the technique you tried before, but it removes old drivers and replaces you X11. You will want to do the guide in its entirety with out skipping anything. HHopefully you are authorized to do that on a work comp. Just make sure you dont skip anything, and check to make sure your backup copies of your old x11/config is there before you move to far into the guide.

good luck

---

### Post by Amorget on 2008-10-14
Removing the old drivers was the part I was missing I think.  I now have working video drivers!  Thank you so much!  The only part that really gets lost in the new xorg.conf file is the touchpad settings, but I have lots of backed up xorg.conf from playing with the HDMI and other toys that don't work with this laptop (I hate Sony...)

I own the laptop, but I use it for work :)  It's a half dev machine, half experiment in Virtualization driven by my general spite for Windows Craptastic... I mean Vista.

---

### Post by SteveNorman on 2008-10-14
killer, glad it worked

---

