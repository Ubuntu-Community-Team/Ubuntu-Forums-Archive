---
title: "newbie with graphics driver issues"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by AppState09 on 2008-05-04
This is making me nuts!!!! 

I installed Ubuntu 8.04 just a few days ago (took several days to figure it out). I've been sick of dealing with Windows XP issues from quite some time. So, I finally decided to try Linux after a classmate did a presentation on OSS last week. I still have XP on my PC, but want to get rid of it once I figure out this Ubuntu stuff. 

I'm trying to get the desktop stuff to work. I've been searching the forums for HOURS and trying everything, but still no luck. I can't seem to get my graphics driver to work. Under 'Hardware Drivers' It showed 'NVIDIA accelerated graphics driver' and 'Not in Use'. So, I enable it and it said I needed to restart, so I clicked the icon to restart. Here's where the trouble come in. When it reboots it gets stuck. The Ubuntu screen comes up with the orange bar underneath it, that bar fully loads, but then the screen goes black except for my mouse pointer, which freezes. 

My computer is a Compaq Presario. I did have a fairly new Dell which was working well, but somehow lost it in my divorce lol. Still not sure how that happened..... Anyhow, my mom had a co-worker who had this computer. It had crashed, so she gave it to my dad who got it working and gave it to me (for free!). However, I pretty much don't know anything about it. 

Thanks so much!!!!! ~Samantha

---

### Post by TeoBigusGeekus on 2008-05-04
Boot up in recovery mode from the grub menu and type
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Perhaps a reconfiguration of your graphics settings will solve the problem.

---

### Post by jimrz on 2008-05-04
It seems that many people, including myself, have had better luck by FIRST installing the appropriate Nvidia driver via Synaptic and THEN activating the driver by using System > Administration > Hardware Drivers. This worked perfectly for me on 2 machines each with different (although they both use the "-new" driver) Nvidia cards. From where you are now, you might try uninstalling all of your Nvidia stuff and the following the above process.

---

### Post by AppState09 on 2008-05-04
I did what you suggested and it came back with a warning about overwriting and back up in /etc/x11/xorg.config.20080504132918

I rebooted again and when I checked my driver, it shows it as not being in use. :confused:

---

### Post by TeoBigusGeekus on 2008-05-04
Try to enable it again. If the problem persists, then follow the procedure mentioned above to be able to boot into Ubuntu again. 
See jimrz's advice as well...

---

### Post by AppState09 on 2008-05-04
> **jimrz said:**
> It seems that many people, including myself, have had better luck by first installing the appropriate Nvidia driver via Synaptic and THEN activating the driver by using System > Administration > Hardware Drivers. This worked perfectly for me on 2 machines each with different (although they both use the "-new+ driver) Nvidia cards. From where you are now, you try uninstalling all of your Nvidia stuff and the following the above process.

at risk of exposing exactly how little I know about what I'm doing here, how do I go about uninstalling the NVIDIA stuff?

---

### Post by starcannon on 2008-05-04
Heres How I got my Nvidia Laptops and Desktops running in Hardy:
Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) sudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

5) sudo gedit /etc/default/linux-restricted-modules-common
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
		If you have some old Ubuntu repository attempts installed please run this command before you go on:

		sudo apt-get remove --purge nvidia*

		-------------------------------------------------------------------------------------------------------
		If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

		sudo nvidia-installer --uninstall

		-------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8.) CTRL-ALT-F1
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

---

### Post by AppState09 on 2008-05-04
I've tried all of the above several times and still am not getting anywhere. No doubt I'm probably screwing something up because I really just don't know what I'm doing:oops: (but am trying to learn!). 

As of right now my driver is no longer showing up at all. Any suggestions at all? I really want to get completely switched over to Linux, but the fact that I can't get this figured out has me concerned 8-[

---

### Post by jimrz on 2008-05-04
did you, BEFORE the FIRST time you tried to install the driver, back up your '/etc/X11/xorg.conf'?

---

### Post by _Narcisse_ on 2008-05-04
Hi Samantha,

Ahh, Nvidia drivers. Always a big deal, don't worry you're not alone.

Did your resolution look good at first boot ? Or was it all ugly and too big ? 

My advice is to reinstall Ubuntu again, now that you've practiced on it :) , boot it and wait a little, normally, Ubuntu should prompt you after a while, asking if you want to enable proprietary drivers. 
Answer yes, and after reboot they sould normally be activated and working.
If You've mess with the configuration files without knowing what you do, that's good to clean it all. That's a good thing you want to learn and that would be a shame that these drivers discourage you to use Linux.

I used to install the drivers from Nvidia myself on my previous Unbutu installs but this time on the new version, it happened to be a bad thing, so I did exactly the same as I said before and it worked.

Just my opinion.
[B]
@jimrz[/B] : That's exactly what I forgot to ask

---

### Post by AppState09 on 2008-05-04
> **jimrz said:**
> did you, BEFORE the FIRST time you tried to install the driver, back up your '/etc/X11/xorg.conf'?

I have NO idea! yeah, completely useless information on my part, but I really have no clue.:redface: When I go into XP it shows my driver as being there and having been updated. But when I check here, I see nothing at all. 

PS: your Benjamin Franklin quote is one of my favorites.

---

### Post by Victormd on 2008-05-04
I got my nvidia drivers working in two different ways.
There is a subtlelty when installing them from the repos' or the restricted driver, and that is that you must enable all the sources in the repositories (system>administration>software sources - at least for me) then reload (or type sudo apt-get update in the terminal) and reboot. This will "fix" the restricted drivers issue (initially the driver is marked but not in use) and you'll be able to select and install from there with no problem at all. The second way to install was using Envy-ng (this is found in the repositories - go to synaptics and search for envyng)...
Note that these suggestions are for a fresh install...

---

### Post by alienexplorers on 2008-05-04
type in terminal:
> lspci
and post the results here.

---

### Post by _Narcisse_ on 2008-05-05
**@AppState09** I asked you if your resolution looked good on first boot because maybe you only need the Nvidia driver to have accelerated graphics (glx) and I thought that maybe it not usefull for you if you don't plan to use special effects or play with 3D games...

---

### Post by AppState09 on 2008-05-07
> **_Narcisse_ said:**
> **@AppState09** I asked you if your resolution looked good on first boot because maybe you only need the Nvidia driver to have accelerated graphics (glx) and I thought that maybe it not usefull for you if you don't plan to use special effects or play with 3D games...

Sorry it took so long to respond!! I've had exams...ugh...
No, my graphics did NOT look good at all. All big and weird.

---

### Post by Delever on 2008-05-07
So far I got EnvyNG to resolve downloading and instalation of graphics drivers reliably on few computers. I suggest you to give it a try.

---

### Post by AppState09 on 2008-05-07
> **alienexplorers said:**
> type in terminal:

and post the results here.

I am SO sorry it's taken me so long to post this! I've had some killer final exams this week....my brain hurts...

samantha@samantha-desktop:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce CPU bridge (rev b2)
00:00.1 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.2 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.3 RAM memory: nVidia Corporation Unknown device 01aa (rev b2)
00:01.0 ISA bridge: nVidia Corporation nForce ISA Bridge (rev c3)
00:01.1 SMBus: nVidia Corporation nForce PCI System Management (rev c1)
00:02.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:03.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:04.0 Ethernet controller: nVidia Corporation nForce Ethernet Controller (rev c2)
00:08.0 PCI bridge: nVidia Corporation nForce PCI-to-PCI bridge (rev c2)
00:09.0 IDE interface: nVidia Corporation nForce IDE (rev c3)
00:1e.0 PCI bridge: nVidia Corporation nForce AGP to PCI Bridge (rev b2)
01:00.0 VGA compatible controller: nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] (rev b1)
02:06.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
02:07.0 Multimedia audio controller: Creative Labs SB Audigy LS
samantha@samantha-desktop:~$

---

