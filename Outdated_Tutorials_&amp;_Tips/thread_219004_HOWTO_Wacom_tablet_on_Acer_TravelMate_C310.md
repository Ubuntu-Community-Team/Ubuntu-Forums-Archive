---
title: "HOWTO: Wacom tablet on Acer TravelMate C310"
date: 2006-07-19
forum: Outdated Tutorials &amp; Tips
---

### Post by prizrak on 2006-07-19
Installing needed package GUI directions (for Gnome only)

On the upper panel click on "System"
Choose "Administration"
Choose "Synaptic Package Manager"
Click "Search" in the search field type in "wacom-tools" and change the look in field to "Name".
You will have one result right click it and choose "Mark for installation"
Click "Search" in the search field type in "xinput"
You will have one result right click it and choose "Mark for installation"
Click the "Apply" button on top. 


Installing needed package command line directions 
```
sudo apt-get install wacom-tools xinput
```

Now on to the "fun" part. 
Open up terminal Applications>Accessories>Terminal (Gnome)
```

sudo gedit /etc/X11/xorg.conf
```
Now look through the file to find this section
```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"

```
Next edit your file to look like this (exactly like this)
```

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS4"
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS4"
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS4"
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"
EndSection

```
Restart your X server (if you don't know how to don't worry about it for now).

After this is done don't close the terminal (or open it again if you did) and type in (this turns right click on for your stylus)
```

/usr/X11R6/bin/./xinput set-button-map stylus 1 3 2 4

```

Now on the top panel click on "System" 
Choose "Preferences"
Choose "Sessions" and click on it
Go to the "Startup Programs" tab 
Click the "Add" button and copy paste the above code into the "Startup Command" text box. 

If you restarted your xserver then you are done, if you don't know how to feel free to just restart the computer (Not necessary) if you are feeling adventurous hitting <Ctrl>+<Alt>+<Backspace> will restart your xserver (doesn't work too well on some systems).

---

### Post by solanas on 2007-11-06
I'm trying this tip on my ubuntu 7.10 but I get this error:

```

$ /usr/X11R6/bin/./xinput set-button-map stylus 1 3 2 4
unable to find device stylus

```

I would love to be able to use my pen.

---

### Post by solanas on 2007-11-09
I found this italian article about the ubuntu installation over tablet pc acer travelmate C310. It's very good because it fix many problems on this tablet.

[http://wiki.ubuntu-it.org/Hardware/Notebook/AcerTravelmateC310]("http://wiki.ubuntu-it.org/Hardware/Notebook/AcerTravelmateC310")

---

### Post by kahi on 2007-12-02
IMHO changing the xorg.conf settings is not the ideal way to go here since xorg.conf already contains default pen configuration sections with reasonable settings. the device it refers to is called /dev/input/wacom. So, I figured why not create a symlink to the device that represents your tablet (in the case of the C310 usually something like /dev/ttyS0 after setting up the serial line properly).
All this can be achieved using udev.
Just add a file to your /etc/udev/rules.d directory (I named it 69-persistent-user.rules) with the following contents:

[B]SUBSYSTEM!="tty", GOTO="persistent_user_end"
KERNEL=="ttyS0", SYMLINK+="input/wacom", RUN+="/bin/setserial /dev/ttyS0 port 0x6F8 irq 6 autoconfig"
LABEL="persistent_user_end"
[/B]

Quite possibly, you can get rid of the first and last lines of the file without any adverse effects, but I found it to better blend in with the rest of the rules.d directory from an aesthetic point of view ;-)

HTH, guys! Any comments and suggestions will be greatly appreciated!

---

### Post by johnnylavah on 2008-02-22
> **kahi said:**
> IMHO changing the xorg.conf settings is not the ideal way to go here since xorg.conf already contains default pen configuration sections with reasonable settings. the device it refers to is called /dev/input/wacom. So, I figured why not create a symlink to the device that represents your tablet (in the case of the C310 usually something like /dev/ttyS0 after setting up the serial line properly).
All this can be achieved using udev.
Just add a file to your /etc/udev/rules.d directory (I named it 69-persistent-user.rules) with the following contents:

[B]SUBSYSTEM!="tty", GOTO="persistent_user_end"
KERNEL=="ttyS0", SYMLINK+="input/wacom", RUN+="/bin/setserial /dev/ttyS0 port 0x6F8 irq 6 autoconfig"
LABEL="persistent_user_end"
[/B]

Quite possibly, you can get rid of the first and last lines of the file without any adverse effects, but I found it to better blend in with the rest of the rules.d directory from an aesthetic point of view ;-)

HTH, guys! Any comments and suggestions will be greatly appreciated!


worked great....THANKS!

---

### Post by Hanyo on 2008-04-27
I tried doing the editing from prizrak, but it doesn't work.  I also restarted the computer several times. When I go and look at the startup for the wacom-tool there is a message below it saying I need kernel and X.Org support.  I am not sure what the errors mean.  I have done searches for X.Org and get hits on Hardware Drivers, that are installed.

I am using 8.04, and pretty new to Linux.  I would appreciate any help.

Thank you!

---

### Post by johnnylavah on 2008-07-04
> **Hanyo said:**
> I tried doing the editing from prizrak, but it doesn't work.  I also restarted the computer several times. When I go and look at the startup for the wacom-tool there is a message below it saying I need kernel and X.Org support.  I am not sure what the errors mean.  I have done searches for X.Org and get hits on Hardware Drivers, that are installed.

I am using 8.04, and pretty new to Linux.  I would appreciate any help.

Thank you!

did you ever get it working?

---

### Post by DouglasAWh on 2008-10-02
```

username@5686:~$ /usr/X11R6/bin/./xinput set-button-map stylus 1 3 2 4
unable to find device stylus

```

so, um, yeah...

---

### Post by dwpurser on 2010-04-14
Type: **xinput --list**
Look for the stylus device. In my case, it was "Wacom Serial Tablet PC Pen Tablet/Digitizer"

So then I could type: **xinput set-button-map "Wacom Serial Tablet PC Pen Tablet/Digitizer" 1 3 2 4**

---

### Post by Saber27 on 2010-04-20
I have been following this thread for quite some time.  I have the exact same Issue with my C310.  Unable to find Stylus.  It is not listed when I run xinput --list.  Everything else works on this machine, except the stylus.  I am new to Ubuntu, and could have sworn that when I originally installed the program, that the stylus worked.  I have tried all recommended fixes, (learning a lot as I go).  Have trashed the display more than a couple of times but still have no functional stylus.

Any help would be appreciated.

---

### Post by Saber27 on 2010-05-03
Okay,  I had some time on my hands and wanted to try a re-creation.  Swapped out my 100g hard drive for a spare 60g I had laying around.  Did a full install of 9.04 and the stylus works with no other inputs, tweats, edits, etc.  It appears that the 'stylus' is identified as the Wacom Tablet PC Pen/Digitizer.  Using these instructions, I was able to set the right click button.  Now all I need to do is get it to work on the 100g drive and work with a rotated screen.

---

