---
title: "How to shut down X for nvidia driver install"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by Codemastadink on 2008-09-28
Hey guys, so im trying to install a Nvidia driver, and it says you have to shut down X before you can install it.

Ive checked around and i tried to do ctr+alt+F1, but when i get there it says i need a password, i tried to just hit enter and get past it, but it didnt work, and i also tried to use my password for my account and that didnt work. 
Im not even sure this is the correct way to shut down X and install from.

Anyone know how i should go about doing this?

---

### Post by fooman on 2008-09-28
when you do ctrl-alt-f1,  you should be able to login with your user name and password.  but thats not how to kill x for the nvidia install.  to do that, open a terminal and type:

```
sudo /etc/init.d/gdm stop
```

to get back, type:

```
sudo /etc/init.d/gdm start
```

of course,  you will need your password for those commands as well.

---

### Post by Codemastadink on 2008-09-28
> **fooman said:**
> when you do ctrl-alt-f1,  you should be able to login with your user name and password.  but thats not how to kill x for the nvidia install.  to do that, open a terminal and type:

```
sudo /etc/init.d/gdm stop
```

to get back, type:

```
sudo /etc/init.d/gdm start
```

of course,  you will need your password for those commands as well.

You know, i tried that one earlier too, and did just now to be sure and i got the same message both times 

```
cody@cody-laptop:~$ sudo /ect/init.d/gdm stop
[sudo] password for cody: 
sudo: /ect/init.d/gdm: command not found

```

---

### Post by jemate18 on 2008-09-28
Maybe this will help you.. This has similar problems...

> [http://ubuntuforums.org/showthread.php?t=905295](http://ubuntuforums.org/showthread.php?t=905295)

---

### Post by jemate18 on 2008-09-28
and mybe this one.. check out the last page... last post

> [http://ubuntuforums.org/showthread.php?t=909735&page=3](http://ubuntuforums.org/showthread.php?t=909735&page=3)

---

### Post by fooman on 2008-09-28
> **Codemastadink said:**
> 
```
cody@cody-laptop:~$ sudo /ect/init.d/gdm stop
[sudo] password for cody: 
sudo: /ect/init.d/gdm: command not found

```

its:

```
sudo /[COLOR="Red"]etc[/COLOR]/init.d/gdm stop 
```

not: 

```
sudo /[COLOR="Red"]ect[/COLOR]/init.d/gdm stop
```

---

### Post by jerome1232 on 2008-09-28
Just fyi your going to need the build essential package. Those linked posts are waaaay offtopic installing this driver isn't THAT hard; Follow these steps if your downloaded driver was downloaded to your desktop, else modify the cd command accordingly

```
sudo apt-get update
sudo apt-get install build-essential
#now hit ctrl+alt+F1
sudo /etc/init.d/gdm stop
cd Desktop
chmod +x NV[hit tab once to auto complete]
sudo ./NV[now hit tab once it should auto-complete the name]
sudo /etc/init.d/gdm start
```


There is a fairly good how to on this in the forums I will find it and link it for you

edit: Found it, it was hiding from me I swear [http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver](http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver)

---

### Post by Codemastadink on 2008-09-28
> **jerome1232 said:**
> Just fyi your going to need the build essential package. Those linked posts are waaaay offtopic installing this driver isn't THAT hard; Follow these steps if your downloaded driver was downloaded to your desktop, else modify the cd command accordingly

```
sudo apt-get update
sudo apt-get install build-essential
#now hit ctrl+alt+F1
sudo /etc/init.d/gdm stop
cd Desktop
chmod +x NV[hit tab once to auto complete]
sudo ./NV[now hit tab once it should auto-complete the name]
sudo /etc/init.d/gdm start
```


There is a fairly good how to on this in the forums I will find it and link it for you

edit: Found it, it was hiding from me I swear [http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver](http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver)

Well, i followed those steps, and wen my computer came back up, it said that it could not detect a video card or driver, and now im forced to run in low quality mode with 800x600 res... How do i fix this?

---

### Post by jerome1232 on 2008-09-28
What vmodel card do you have?

You can uninstall that driver by hitting ctrl+alt+f1 and typing this command, might be a single - instead of two it's been a very long time since I've been forced to resort to nvidia's installer. 

(I just use the one in the repos or envyng on my computers) Have you tried the other install methods avaible on that guide I linked?
```
cd Desktop
sudo ./NV[tab] --uninstall
```

---

### Post by fooman on 2008-09-28
while your in that low graphics mode...try bringing up a terminal and type:

```
sudo nvidia-xconfig
```

then try logging out (ctrl-alt-backspace) and back in again...or reboot.  see if that helps.

---

### Post by Codemastadink on 2008-09-28
> **fooman said:**
> while your in that low graphics mode...try bringing up a terminal and type:

```
sudo nvidia-xconfig
```

then try logging out (ctrl-alt-backspace) and back in again...or reboot.  see if that helps.

This is what i got, i'll log out and back in and see what happens 

```

cody@cody-laptop:~$ sudo nvidia-xconfig
[sudo] password for cody: 

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


```

Yea.. that did nothing

---

### Post by skullmunky on 2008-09-29
1. just out of curiosity, what card do you have?
2. i take it you tried activating the nvidia driver through the desktop, the easy way, and it didn't work, so you're using the installer package from NVIDIA?
3. if that's true; did that install process go smoothly?


if you've managed to get out of X by stopping gdm, and you're trying to get the driver installed and X configured nicely, another way to test quickly is 
```

startx

```

if there's a problem, this will just put you back to the terminal nicely and give you debugging output.

---

### Post by Codemastadink on 2008-09-29
> **skullmunky said:**
> 1. just out of curiosity, what card do you have?
2. i take it you tried activating the nvidia driver through the desktop, the easy way, and it didn't work, so you're using the installer package from NVIDIA?
3. if that's true; did that install process go smoothly?


if you've managed to get out of X by stopping gdm, and you're trying to get the driver installed and X configured nicely, another way to test quickly is 
```

startx

```

if there's a problem, this will just put you back to the terminal nicely and give you debugging output.

Um well i already installed the driver(i think), i went through the process and i thought it was good..

---

### Post by Codemastadink on 2008-09-29
Pretty much my card or driver arent recognized anymore.. How would i get it fixed?

---

### Post by jerome1232 on 2008-09-29
It would be really helpful if you could answer some of our questions so we can effectively help you.

What model is this Graphics card? If you are unsure the output of this command should tell
```
sudo lshw -C video
```

Did you try the other methods of installation? (installing nvida-glx-new or installing and running envyng)

---

### Post by Codemastadink on 2008-09-29
> **jerome1232 said:**
> It would be really helpful if you could answer some of our questions so we can effectively help you.

What model is this Graphics card? If you are unsure the output of this command should tell
```
sudo lshw -C video
```

Did you try the other methods of installation? (installing nvida-glx-new or installing and running envyng)

Its a Nvidia GeForce 8600 GS

What do you mean by

> Did you try the other methods of installation? (installing nvida-glx-new or installing and running envyng)

Could you expand on this? Im not sure what it is

---

### Post by jerome1232 on 2008-09-29
In my first post I gave this how to for installing nvidia drivers
[http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver](http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver)

Gives you from easiest to the hardest instructions on installing an nvidia driver.

first method is through the Restricted Driver Manager, second using envy, third the way you've been trying, and lastly blacklisting some drivers and installing the way you've been trying. 

It steps you through them all in that guide. I would actually start with envyng as it installs the latest nvidia driver, and I see the current version, 173.14.12, is the first to provide support for your card 8600 GS so the Restricted Driver Manager will probably be to outdated for you.

---

### Post by Codemastadink on 2008-09-29
> **jerome1232 said:**
> In my first post I gave this how to for installing nvidia drivers
[http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver](http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver)

Gives you from easiest to the hardest instructions on installing an nvidia driver.

first method is through the Restricted Driver Manager, second using envy, third the way you've been trying, and lastly blacklisting some drivers and installing the way you've been trying. 

It steps you through them all in that guide. I would actually start with envyng as it installs the latest nvidia driver, and I see the current version, 173.14.12, is the first to provide support for your card 8600 GS so the Restricted Driver Manager will probably be to outdated for you.

So i tried to do this again, with the guide
"IV.  Tricky Way After Clean Installation"

It installed nicely, but when i started GDM it again said that my video card and driver could not be detected. So it had to run in low graphics mode. When i go to App>Sys tools>Nvidia X Server Settings i get a message

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

When i do
```

cody@cody-laptop:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

So it doesn't really help any, or maybe i just don't know how to use this information

---

### Post by Codemastadink on 2008-09-30
bump

---

### Post by skullmunky on 2008-09-30
@Codemastadink: patience, you can give the worldwide open source community more than 24 hours before bumping your thread, you know ... 


post your /etc/X11/xorg.conf

if you use startx instead of starting gdm, do you get any errors?

---

### Post by Codemastadink on 2008-10-01
> **skullmunky said:**
> @Codemastadink: patience, you can give the worldwide open source community more than 24 hours before bumping your thread, you know ... 


post your /etc/X11/xorg.conf

if you use startx instead of starting gdm, do you get any errors?


Ok, this is my /etc/X11/xorg.conf

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce 8 Series"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"NVIDIA GeForce 8 Series"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	1
	Vendorname	"NVIDIA"
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

```


Ok well i tried to just start X and this is what i got.

```

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock

Invalid MIT-MAGIC-COOKIE-1 keygiving up.
xinit: Recourses temporarily unavailable (errno 1w1):Unavailable to connect to X server
Xinit: No such process (errno 3) server error

```

---

### Post by Codemastadink on 2008-10-03
........

---

### Post by skullmunky on 2008-10-03
1.  when you ran startx, did you already quit the existing X session?

meaning, use Ctrl-Alt-F2 (or F1, or F3, or F4, etc.) to get another virtual terminal, then log in, then stop the x session by doing

```

/etc/init.d/gdm stop

```

?

if so, and you don't have any X running (Ctrl-Alt-F7 or Ctrl-Alt-F8), then try removing that lock file it's complaining about:

```

sudo rm /tmp/.X0-lock

```

and then try startx again.

Your xorg.conf is a failsafe one, apparently, which is why the 640x480 resolution.  It DOES look like it's using the nvidia driver correctly, so I'd be interested to see if you get any errors related to the nvidia driver when you startx.

If you -are- able to get into the desktop without errors, is the nvidia-settings program still saying you're not really using the nvidia driver?

In some ways it seems like the problem is with detecting your monitor, not the card... btw what kind of monitor, and what resolution was it giving you before you tried installing the nvidia driver?

someone probably already suggested this, but there's also this command you can try (maybe again...):
```

 sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by Codemastadink on 2008-10-04
> **skullmunky said:**
> 1.  when you ran startx, did you already quit the existing X session?

meaning, use Ctrl-Alt-F2 (or F1, or F3, or F4, etc.) to get another virtual terminal, then log in, then stop the x session by doing

```

/etc/init.d/gdm stop

```

Wow ok, so before i didnt stop X i guess cuz i never did gdm stop, so i did then and started X and it came back up as it was before i tried to install the driver, it is now at 1440x900 res. But, when i try to open anything that u need privileges for, i get an error about running as root.
EDIT: I play around a little and now i can get into those root programs and such. But i can not do 3D effects, such as compiz things. I can not do anything like this
> **skullmunky said:**
> 
In some ways it seems like the problem is with detecting your monitor, not the card... btw what kind of monitor, and what resolution was it giving you before you tried installing the nvidia driver?


It is the monitor on my laptop, i believe before the resolution was 1440x900 also..

```

$ sudo dpkg-reconfigure -phigh xserver-xorg 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20081004115345

```


EDIT#2: Also if i go to Applications>System Tools>NVIDIA X Server Settings. I get a message that reads
 "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

And when i try to run it heres what i get
(It says to run as root so i did this first, and then again without(Different results))

```

cody@cody-laptop:~$ sudo nvidia-xconfig
sudo: nvidia-xconfig: command not found
cody@cody-laptop:~$ nvidia-xconfig
The program 'nvidia-xconfig' can be found in the following packages:
 * nvidia-xconfig
 * nvidia-glx
 * nvidia-glx-new
Try: sudo apt-get install <selected package>
bash: nvidia-xconfig: command not found

```

---

### Post by Codemastadink on 2008-10-05
Up

---

### Post by skullmunky on 2008-10-10
did you try what it suggested ... ?

```

sudo apt-get install nvidia-xconfig

```

---

### Post by Codemastadink on 2008-10-13
> **skullmunky said:**
> did you try what it suggested ... ?

```

sudo apt-get install nvidia-xconfig

```

```
sudo apt-get install nvidia-xconfig
[sudo] password for cody: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-xconfig is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by skullmunky on 2008-10-14
> **Codemastadink said:**
> ```
sudo apt-get install nvidia-xconfig
[sudo] password for cody: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-xconfig is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Congratulations, you've stumped the chump!! :lolflag:

I think we've got to start over from the beginning w/ troubleshooting this one, I'm gonna read back over this whole thread & see what I can come up with.  In 6 years I've never been defeated yet by an nvidia driver installation so I ain't giving up, but there's something peculiar going on here.

---

### Post by SteveNorman on 2008-10-14
this technique from starcannon seems to work for most people Make sure to not skip any steps

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

### Post by Chookah on 2008-10-18
> **fooman said:**
> when you do ctrl-alt-f1,  you should be able to login with your user name and password.  but thats not how to kill x for the nvidia install.  to do that, open a terminal and type:

```
sudo /etc/init.d/gdm stop
```

to get back, type:

```
sudo /etc/init.d/gdm start
```

of course,  you will need your password for those commands as well.

When I do the *gdm stop* it doesnt take me back to a prompt, I can type text & press enter but nothing happens.  I'm forced to reboot

---

### Post by phidia on 2008-10-18
> **Chookah said:**
> When I do the *gdm stop* it doesnt take me back to a prompt, I can type text & press enter but nothing happens.  I'm forced to reboot

Try Alt+Ctrl+F1 to open another tty, and get the prompt.

---

### Post by RATM_Owns on 2008-10-18
Try
```
sudo /etc/init.d/gdm stop &
```
And press enter when the command is done.

---

### Post by medic2000 on 2008-10-18
Hey guys i just installed the new nvidia driver on my ArchLinux and my X has broken too.

With the same error!: "Can't detect Device"

---

