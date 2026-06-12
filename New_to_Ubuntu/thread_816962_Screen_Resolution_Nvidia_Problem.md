---
title: "Screen Resolution Nvidia Problem"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by volpne on 2008-06-03
Hi 
My problem is screen resolution, Ive searched the forums but havent found an answer that I can understand.

I cant get the resolution higher than 800x600, in fact in the System Preferences Screen Resolution there are only two options 800x600 or 640x480.

Im running,
Ubuntu 8.04 - the Hardy Heron
on a
AMD 64 bit machine
the screen is
LG Flatron L1953TR
the motherboard is
ASRock ALive NF7G-HD720p
the on board graphic card is
NVIDIA GeForce7.


Ive tried,

sudo nano /etc/usplash.conf

I changed the values to

# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1280
yres=800

When I reboot the values 1280 x 800 are still in usplash.conf although in Systems Preferences Screen Resolution the options remain 800x600 or 640x480.

Also on boot up I now get the message,

Ubuntu is running in low-graphics mode
Your screen and graphic cards could not be detected
correctly, to use higher resolutions, visual effects or
multipe screens, you have to configure the display yourself.

The choice is to continue in low-graphic mode or, Configure, Graphic Card, Drivers, Choose Driver, NVIDIA GeForce, Test, Configuration Test Failed.

Now Im left scratching my head, I would appreciate any help.

V

---

### Post by kpkeerthi on 2008-06-03
/etc/usplash.conf lets you configure bootsplash resolution and not your desktop screen resolution. See [https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash) for more info.

To configure your display, install restricted driver for your graphics card from System -> Admin/Preferences -> Hardware Drivers. Now boot into recovery mode from GRUB. At the command prompt, enter this command```
sudo dpkg-reconfigure -phigh xserver-xorg
```
When prompted choose the display driver as **nvidia** and appropriate resolutions you monitor supports. Reboot.

---

### Post by ajmorris on 2008-06-03
hi there,
You could try the xorg configuration tool. cant remember exactly what it is called... but it is in the menus under system... it is a new feature in hardy.
You should be able to change the resolution in there, once set, restart X, and hope it works :) if it doenst work, we can edit your /etc/X11/xorg.conf file directly to make it work ;)
Alternatively, you could run sudo xfix from a terminal, and reconfigure xorg that way, or the old way, and do sudo dpkg-reconfigure xserver-xorg  (you can also add -phigh so that you dont have to set as many options)

AJ

---

### Post by Tatty on 2008-06-03
AFAIK usplash.conf only affects your bootup splash screen, your problems will lie in xorg.conf.

First you neec to install the correct drivers for your card either with the hardware drivers manager (System->Administration->Hardware Drivers) or with envyNG (which is in the repositories as envyng-gtk).

Then you need to backup your xorg.conf file with sudo cp ```
/etc/X11/xorg.conf /etc/X11/xorg.conf.my.backup
```

Then reset your xorg.conf file by reconfiguring xorg with ```
sudo dpkg-reconfigure xserver-xorg
```

note: the driver you want is the "nvidia", not "nv" driver.  nv is the open source driver and not as powerful as the propritry nvidia driver.  Unless of course you have a moral objection to closed source drivers :)

---

### Post by volpne on 2008-06-03
Ok I tried to install 
NVIDIA Accelerated Graphics Drivers, booted into Recovery and after the prompt typed,
sudo dpkg-reconfigure -phigh xserver-xorg 

after a few attempts the reply was,
xserver-xorg postinst warning overwriting possible customised configuration
file; backup in/etc/x11/xorg.conf.20080603162724

there was no choice to select anything and no mention of NVIDIA

As I was trying this at one piont I checked 
System Preferences Screen Resolution, it had changed but this time 800x600 was gone and the largest choice was 640x480 with another 8 smaller choices, then I checked if the NVIDIA drivers were still selected in the, 
System -> Admin/Preferences -> Hardware Drivers the driver was there but inactive.
I turned it on again, then went back to Preferences and this time the choice in,
System Preferences Screen Resolution was back to 800x600 or 640x480.
Then another reboot.
This time after I login the screen goes black. My monitor flashes up the message
ANALOG
out of range
80.8KHz/65Hz.

So needless to say Im now in windoze.

Any ideas.
V

---

### Post by ajmorris on 2008-06-03
as of hardy, a new feature called xfix has been implemented, boot into recovery mode again, and run sudo xfix.

---

### Post by sammydadams on 2008-06-04
you are gonna want that nvidia driver which should show up in system>administration>hardware drivers...

afterward if you are still having resolution issues (or if you have already tried this)...

you might try opening up terminal and typing nvidia-settings and click on X Server Display Configuration...this'll get you started (if it isnt installed, just install it)

...or, the more brute force method

try going into filesystem>etc>X11 you'll be editing xorg.conf as root (best bet is also to back this up using as xorg.conf.bak or something just in case) 
scroll down until almost the bottom and check out the screen section which will likely look something like this:
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

and add a subsection under "Defaultdepth" line that says this:

SubSection     "Display"
        Modes      "1024x768"
    EndSubSection

this should force 1024x768 resolution...you can add more reslotuions in that same spot too...
all together it'll look like:

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
        SubSection     "Display"
              Modes      "1024x768"
        EndSubSection
EndSection


worth a try =)

---

### Post by volpne on 2008-06-04
Hi again,

well I finally got the screen back on thanks to ajmorris, xfix worked. 

Although the screen resolution at the login has returned to 800 x 600. 

The NVIDIA accelerated graphics drivers in the System->Administration->Hardware Drivers is on, in use, active.

Now if I go to 
System->Administration->Nvidia X server settings, 
I get,
You dont appear to be using NVIDIA x drivers
please edit your X configuration file nvidia-xconfig

Now in terminal i enter,
sudo nvidia-xconfig
the reply is,
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

Well at lest Im back in Ubuntu, and I can almost smell that full screen resolution.

Thanks again
V

---

### Post by volpne on 2008-06-04
Hi 
just to up date.

If I try,
>sudo xfix
The reply is,
>sudo: xfix: command not found

or if I try,
>sudo dpkg-reconfigure xserver-xorg
I get to the xorg reconfigure page but it only deals with Keyboard options.

then if I try
>nvidia-settings 
It replys that the nvidia x driver dose not appear try nvidia-config
so I try
>sudo nvidia-config 
the answer is
>sudo: nvidia-config: command not found


if I try and use
>/etc/X11/xorg.conf /etc/X11/xorg.conf.my.backup
I receive the message,
>bash: /etc/X11/xorg.conf: Permission denied

Again in
>(System->Administration->Hardware Drivers) the Nvidia drivers are ON.

I also went through Synaptic Package Manager and installed,
 envyng-gtk and envyng core,


So the only option Ive still to try from the suggestions are,

"we can edit your /etc/X11/xorg.conf file directly to make it work"

and

"or, the more brute force method try going into filesystem>etc>X11"

How can I edit directly or how can I get into filesysetem.

Any ideas would be great
Thanks
V

---

### Post by philinux on 2008-06-04
Just to check where you are. Have you blacklisted the nv nvidia modules?

[http://ubuntuforums.org/showpost.php?p=5082510&postcount=2](http://ubuntuforums.org/showpost.php?p=5082510&postcount=2)

---

### Post by volpne on 2008-06-04
Hi philinux,

Im unsure of Blacklist and how to find it,

But I did follow the instructions from the link.

I downloaded from Nvidia
I seemed to get rid of old drivers etc,
I then went to the command line and after a few attempts I completed the instructions.
I even seen the Nvidia splash up (first time) just before the log in. 

BUT
I am back to the dreaded blank screen after password.
with a message from the monitor,

ANALOG
out of range
80.8KHz/65Hz

so now im back in windows.

---

### Post by volpne on 2008-06-05
Hi
Today I tried xfix to get the screen to return, but alas when I try  Ubuntu it goes to the moving orange bar (splash up) before going straight to the command line.
This is the result also in recovery.

How can I go from command line to the desktop enviroment.

---

### Post by missionx on 2008-06-05
to start desktop use command
start xserver

to edit xorg.conf
sudo gedit

this will open the text editor in root, then select open and browse to the filesystem>etc>x11>xorg.conf  file and edit it and save and then restert xserver or restart computer and changes should take effect

---

### Post by volpne on 2008-06-05
Hi missionx
When I log in on the command line, then type in.
 
>name@computer start xserver
>start: need to be root
>name@computer sudo start xserver
>start: unkown job: xserver

any clues to what to do now.

---

### Post by Xiong Chiamiov on 2008-06-05
I believe the command is just
```

startx

```

---

### Post by volpne on 2008-06-05
Hi Xiong Chiamiov

when I type startx, it goes through a few things before I get the error message.

fatal server error:
caught signal 11  server aborting
giving up
xinit: connection reset by peer (errno 104): unable to connect to xserver
xinit: no such process (errno 3): server error

---

### Post by volpne on 2008-06-05
How about a new install,
Is it safe to reinstall over my current ubuntu

---

### Post by starcannon on 2008-06-05
nvidia-xconfig is the xorg.conf configurator for the official Nvidia Binaries.

I've written a guide for manual installation of the Nvidia Binaries that you can download from nvidia.com

You can see the guide I wrote at post #6 here:

[http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia)

Good luck and if you decide to use my guide, don't skip steps, even if you have done them previously, just methodically go through the guide; this is how I set up all of my Nvidia Cards, this method works flawlessly for me.

---

### Post by volpne on 2008-06-05
Hi starcannon,

At the moment I cant get to the terminal, 
Ubuntu goes straight to command line after the splash screen with the orange bar.
In command line I cant get into the desktop enviroment.

startx etc is not working.

---

### Post by philinux on 2008-06-05
You can do all of the things in the guide from the command line.

In fact for the latter part you stop gdm anyway.

---

### Post by volpne on 2008-06-05
I have tried a similar approach 

[http://ubuntuforums.org/showpost.php?p=5082510&postcount=2](http://ubuntuforums.org/showpost.php?p=5082510&postcount=2)
posted by EXCiD3

Now Im tring
[http://ubuntuforums.org/showthread.p...ghlight=nvidia](http://ubuntuforums.org/showthread.p...ghlight=nvidia)
posted by starcannon

but I cant get past,

4) gksudo gedit /etc/modules

the reply is

(gksudo:5765): Gtk-warning **: cannot open display

---

### Post by philinux on 2008-06-05
Then since this is an emergency use

sudo gedit

Or sudo nano

---

### Post by starcannon on 2008-06-05
> **philinux said:**
> Then since this is an emergency use

sudo gedit

Or sudo nano

+1 for sudo nano, I actually do the entire thing from command line using nano. I just put together the gksudo gedit guide for those more comfortable in the gui.

So yeah, like philinux said, this entire guide can be implemented from command line, just use ```
sudo nano
``` instead of ```
gksudo gedit
```

GL

---

### Post by volpne on 2008-06-05
Hi
Ok I followed the instructions replacing,
>gskudo gedit
with
>sudo nano

All went well.

Nvidia was already in modules so I didnt need to add.

Then at,
>sudo ./NVIDIA*.run
I get the message
>There appears to be already driver version 173.14.05
Then on the next screen
>No matching precompiled kernal interface was found at the NVIDIA ftp site.
Then the next question is about a 32 bit system, with the message  > WARNING; Zour driver installation has been altered since it was initally installed: This may happen for example if you have since installed the NVIDIA drivers through a mechanism other than NVIDIA-installer.

Although when I finish with
>sudo /etc/init.d/gdm start
and press enter it boots up, NVIDIA splash screen, then log in and password all in the Ubuntu desktop screen. Unfortunalty after the password, I get the dreaded black screen again.
With the monitor message.

ANALOG
out of range
80.8KHz/65Hz. 

It gets worst.

So I go and buy a digital cabel for the monitor, then when I try to boot up, it goes to the command line instead of the ubuntu desktop enviroment for the log on.

aaarrrrgggghhhhhh.

---

### Post by starcannon on 2008-06-05
okay hang in there, lets try this:

```
sudo /etc/init.d/gdm stop
sudo rm /etc/X11/xorg.conf
sudo nvidia-xconfig
sudo /etc/init.d/gdm start

```

reply back with how that turns out.

---

### Post by volpne on 2008-06-05
right I entred the four lines, but at, 
>sudo nvidia/xconfig
a message says,
>WARNING: unable to locate/open x configuration file.
>New x confiuration file written to '/etc/X11/xorg.conf'

Then when I enter,
>sudo /etc/init.d/gdm start
the screen flickers but returns to the command line.

---

### Post by starcannon on 2008-06-05
Okay you've got a new xorg.conf written by nvidia-xconfig now.

Screen flickers and goes to cli again though...

*scratches head*

I'm a bit at a loss, lets get you back to a gui to start with:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

That should get you back into a no frills vesa driver so you can get back to the desktop, if it does let me know, and if you like we can arrange a VNC session.

---

### Post by volpne on 2008-06-06
Hi again,

When I enter,
>sudo dpkg-recongigure -phigh xserver-xorg

the reply is
>xserver-xorg postinst warning;
>overwriting possibly-customised configuration
>file; backup in /etc/X11/xorg.conf.20080606080752

---

### Post by volpne on 2008-06-06
Ok 
If I give up and want to do a new install, do I need to clear, delete or format the partition, or can I just reinstall on top of the old installation straight from the CD?

---

