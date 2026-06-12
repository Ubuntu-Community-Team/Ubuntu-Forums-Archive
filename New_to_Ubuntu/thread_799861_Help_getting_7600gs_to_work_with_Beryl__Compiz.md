---
title: "Help getting 7600gs to work with Beryl / Compiz"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by The Jinx on 2008-05-19
Hi,

I've been searching around and I noticed that the nVidia 7600gs has been giving its users some trouble. Has anyone managed to get the 7600gs up and running with Beryl or Compiz. I just want to get some eye candy up and running on my PC.

Thanks,
Jinx

---

### Post by techno-mole on 2008-05-19
i use a 7600gs and ive never had any trouble, works from the get go.
im running compiz from git, awn and screenlets (although im having a little trouble getting the screenlets to auto start, nothing to do with the graphics though)
whats the problem ?

---

### Post by The Jinx on 2008-05-19
well currently im running Ubuntu 8.04 from the live cd. When i load up I notice a fd0 error and when it finally gets to the desktop the screen is off to the right by a couple of clicks. I tried initiating the advance graphics thing so I can get some wobbily but no go. I don't even think Ubuntu detects it at all....

looking foward to your assistance

---

### Post by wolfen69 on 2008-05-19
> **The Jinx said:**
> well currently im running Ubuntu 8.04 from the live cd. **When i load up I notice a fd0 error** and when it finally gets to the desktop the screen is off to the right by a couple of clicks. I tried initiating the advance graphics thing so I can get some wobbily but no go. I don't even think Ubuntu detects it at all....

looking foward to your assistance

if you dont need your floppy, go into your BIOS and disable your floppy drive. if your screen is off to the right, use the controls on your monitor to move the screen over.(vertical adjustment)

---

### Post by wolfen69 on 2008-05-19
did you go to system>preferences>appearance>visual effects and enable extra?

---

### Post by starcannon on 2008-05-19
Heres a guide I put together for getting Nvidia Cards working, I have several computers with 6,7, and 8 series cards in them, laptops and desktops, works for all of them. Hope it helps, be sure to follow the guide completely even if you've done parts of it before.

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

### Post by techno-mole on 2008-05-19
it may be a driver issue ? not sure though, but when i run from the live cd i cant enable desktop effects, and from a fresh install i have to install an nvidia driver.
eg - first start up from fresh install, go to system - preferences - appearance, click on enable advanced desktop effects, i then get a message about the an nvidia driver needs to be installed (non proprietary driver i think it is) i then install said driver, restart system, then hey presto once the system is booted up, i go to system - preferences and then appearance, enable advanced desktop effects and of i go.

so im not sure, but it maybe something to do with the driver thats on the disc ? or maybe a disc error ? (as in the live cd) as for the fd0 error, disabling the floppy disc drive will probably sort that.

as for the screen being off center, do you have a flat panel ? (tft, lcd) i do, and i have an auto adjust button (some have a setting in the menu) all i do is press it and it will reset the screen to the right place.

@ starcannon, can that be done while using the live cd ? i had never thought to try and install the driver, but then i run ubuntu as my main os, so as i mentioned i do the driver install bit once ive installed the os.

---

### Post by starcannon on 2008-05-19
@techno-mole I never really tried doing it from live CD, this is my post install method of getting my nvidia cards working perfectly.

If you can boot, but can not get to the desktop let me know, I have a guide that you can use with nothing but the command line as well.

---

### Post by techno-mole on 2008-05-19
i can honestly say that apart from edgy (i think it was edgy) i havent had much trouble getting my card to work, i did used to have problems with the card when i used envy to install the drivers, but now it just does it automatically and bobs your mothers brother.

ive never had trouble on the first boot, the desktop is always there, and like i said if i let the system sort it out itself i end up with a driver that works well with my card, least i think it does, cant say ive noticed any errors ?

cheers for the info though, i shall make a note of that, and if i have trouble ill let you know, i will no doubt be on the forums screaming help :-)

---

### Post by The Jinx on 2008-05-19
okay from my understanding I have already disabled my floppy drive. When I went into the BIOS and under the boot order I have CD / DVD as first, Hard Drive as second, and I disabled third and fourth.

The error that I get is:

[###.######] Buffer I/O error on device fd0 logical block 0

didn't quite get the numbers before the message.

and as for the graphical visual effects I will do a fresh install on my old 20gb 5400rpm harddrive tonight to see if it will correct the problem.

---

### Post by starcannon on 2008-05-19
I would likely try commenting out the floppy drive in the /etc/fstab file

```
gksudo gedit /etc/fstab
put a # in front of any floppy device lines
save
reboot
```

---

