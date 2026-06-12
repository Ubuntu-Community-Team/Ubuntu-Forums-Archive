---
title: "HOWTO Configuring Logitech mice in Ubuntu 6.06 32 bit, based on endy's HOWTO"
date: 2006-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by detyabozhye on 2006-06-03
**[SIZE="5"][COLOR="Red"]Please go to the [_new guide_]("http://ubuntuforums.org/showthread.php?t=219894"). Use this guide only if the new one fails no matter what you try.[/COLOR][/SIZE]**

_**A complete guide to a Logitech mouse**_
[COLOR="Red"]WARNING: Contains hacks, not for the faint of heart.[/COLOR]

This is endy's guide on how to get all the buttons working properly on a logitech mouse (modified by me for Ubuntu 6.06), how to use the "logitech_applet" to enable the higher resolutions and cruise control and how to get the side mouse buttons to make forwards and back work in Nautilus, Epiphany, Konqueror, etc. 

This works for my mx500, I assume it would work for the similar mx510 and mx518 and the wireless versions like the mx700 however, I haven't got all those mice so I'd appreciate it if anyone get them working to post a reply and I'll make a list of what works.


_**Section 1: Getting your mouse working on USB with evdev**_[INDENT]
First off you need to plug your mouse into a USB port, you can't do anything else in this how to until you do that.

_[COLOR="#ff0000"]0.9 You need an older version of evdev, the current one is broken.[/COLOR]_

In your terminal, type:

```
wget http://detyabozhye.com/other/xserver-xorg-input-evdev_1.0.0.5-0ubuntu2_i386.deb
```
```
sudo dpkg -i xserver-xorg-input-evdev_1.0.0.5-0ubuntu2_i386.deb
```

To avoid it updating to the new version (broken), open Synaptic Package Manager. Find xserver-xorg-input-evdev, select it, go to Package->Lock Version. Close Synaptic. The tradeoff here is that if a working new version comes out, you won't know about it.

_1. Getting all the information you need_

Great, so we're all plugged in via USB and ready to go. Before we change anything we need to get some important information about the mouse so run the following command in your favourite terminal:

```
cat /proc/bus/input/devices
``` You should get a list of details, here's what I get and I'll highlight the bit we need to concentrate on:

```
I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c025 Version=1800
N: Name="**Logitech USB-PS/2 Optical Mouse**"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0003 Vendor=049f Product=000e Version=0100
N: Name="Compaq Compaq Internet Keyboard"
P: Phys=usb-0000:00:1d.1-2/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2
B: EV=120003
B: KEY=10000 7 ff87207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: LED=7fff

I: Bus=0003 Vendor=049f Product=000e Version=0100
N: Name="Compaq Compaq Internet Keyboard"
P: Phys=usb-0000:00:1d.1-2/input1
S: Sysfs=/class/input/input3
H: Handlers=kbd event3
B: EV=3
B: KEY=20000 87a 5000d000 1e0000 0 0 0
```

*Note: For mx700 users the mouse name is "Logitech USB Receiver"*

_1.1 Adding a udev rule_

I've found that the event number for the mouse sometimes changes in 6.06, so we'll make a udev rule.

Type this in your terminal:
```
sudo gedit /etc/udev/rules.d/19-local.rules
```

and paste this into there and save it (replace the bold part with the name of your mouse and replace the underlined part with whatever you want to put there, it will be used in xorg.conf):

```
KERNEL=="event[0-9]*", SYSFS{../name}=="**Logitech USB-PS/2 Optical Mouse**", NAME="input/_mx500_"
```

_2. Editing the xorg.conf file_

Now we have the information we need to start to set up xorg. So open up your xorg.conf file in your favourite editor, mine is mousepad but as gedit is on everyone elses install by default you can type:
```
sudo gedit /etc/X11/xorg.conf
``` Now scroll down to the mouse section and instead of deleting it we're going to comment it out, to do this you put a "#" in front of each line in the section, again here is my commented section as an example:

```
#Section "InputDevice"
#    Identifier     "Configured Mouse"
#    Driver         "mouse"
#    Option         "CorePointer"
#    Option         "Device" "/dev/input/mice"
#    Option         "Buttons" "10"
#    Option         "ButtonMapping"         "1 2 3 6 7"
#    Option         "Protocol" "ExplorerPS/2"
#    Option         "ZAxisMapping" "4 5"
#    Option         "Resolution" "800"
#EndSection

``` Again, yours might look different, the important bit is to comment the whole section out, but only this section.

Next up we want to paste in out new section, make a but of room underneath (or above if you prefer) that section we just commented out and paste in the following template:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mx500" #this should be that underlined name from 19-local.rules
EndSection
```
Make sure you save the changes to your xorg file.

_3. Restart X_

_Warning!_
Don't restart X yet! Just before we do I have to warn you if you made a mistake in the xorg file X will not restart. But don't worry that's why we only commented out the previous settings and didn't delete them. If X fails to restart then you will end up in a text console. Log in and type the following to edit the xorg file:

```
sudo nano /etc/X11/xorg.conf
``` All you need to do is comment out the new section we just added by putting a "#" in front of each line and un-commenting the original section by deleting the "#" which is at the start of each line. Save the xorg file in nano by typing "CTRL + X" press "Y" to confirm the save and type "startx" to get back to your desktop and re-read section two carefully and correct your xorg file.


_Ok, I'm ready_
Now we're prepared, restart X by first logging out then pressing "CTRL + ALT + BACKSPACE" simultaneously and hopefully after a moment you can log back in.


_4. Editing the Xmodmap file_ [COLOR="Red"]The higher models, such as the MX1000, don't need this part. Thanks to adam.tropics for the heads up.[/COLOR]

```
gedit ~/.Xmodmap
``` and paste the following, overwriting any previous "pointer" line:
```
pointer = 1 3 2 4 5 8 9 6 7 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32
``` 
Now run xmodmap to apply these settings:
```
xmodmap ~/.Xmodmap
``` If this is the first time you created a .Xmodmap file then next time you log into gnome it will ask you if you want to automatically load it, add the file and click Ok if this happens.

Now all the buttons should work properly including the little up button above the scroll wheel. The side buttons should also make Firefox go forward and backward a page just like before but they will not work in Nautilus or Konqueror yet. Keep reading to see how to get that to work!

*Note: If you're mouse has more or less buttons then you'll need to figure out what button numbers are the two side buttons, you can do this with the utility "xev" which you run from the terminal, hover the mouse over the pop up box and hold it still and press the side buttons. You'll see some output part of which is a button number. The two button numbers for you mouse go last in the .Xmodmap file, look at mine as an example.*[/INDENT] 
**_Section 2: Side buttons and Nautilus, Epiphany, Konqueror, etc_**[INDENT]
We can use "xvkbd" and "xbindkeys" to bind the side mouse buttons to "ALT + LEFT" and "ALT + RIGHT" so they work as forward and backwards in Nautilus.


_1. xvkbd and xbindkeys_

Lets install "xvkbd" and "xbindkeys":

```
sudo apt-get install xvkbd xbindkeys
``` Next we need to create the configuration for them:

```
gedit ~/.xbindkeysrc
``` Now paste the following ([color=red]Note: With some updates in the Dapper flights, the bath to xvkbd changed, please update your .xbindkeysrc accordingly[/color]):

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7
``` 

**Please note, the "L" and "R" from the words "left" and "right" in the square brackets above should be capitalised, this seems like a bug in the forums here that they don't display properly.**

Make sure you keep the quote marks, save the file and run "xbindkeys" in the terminal. It runs as a daemon in the background. You should now be able to test if it works in Nautilus by using the side buttons it also works in Epiphany if you use it.

*Note: Same as before, if you have different mouse buttons use xev to find out what number they are and change the "b:6" and "b:7" in the above to the correct numbers.*

_1.1 Fixing the cruise control buttons_

*Note: Requires the package build-essential*

Install these three packages for "click" to compile:
```
libx11-dev
x11proto-xext-dev
libxtst-dev
```

Download this file: [http://bg.rifetech.com/click.tgz](http://bg.rifetech.com/click.tgz)
untar it to ~/click (or wherever you want, just remember the dir, you'll need it in the .xbindkeysrc)
then compile it:

```
cd ~/click
make
```

Then add this to you .xbindkeysrc

```
"~/click/click 4"
  m:0x0 + b:11
"~/click/click 5"
  m:0x0 + b:12
```

_2. Adding it to your session_

Now it's working open up the gnome sessions settings "System > Preferences > Sessions" click on the "Startup Programs" tab, click "Add" and enter "xbindkeys". This makes sure it's run each time you log in, you should probably test it by logging out and back in now. If you aren't running GNOME, you will need to do it another way, e.g. in XFCE, go to Xfce Menu -> Settings -> Autostarted Applications. (I haven't tried it, but that should be where to go in XFCE)
[/INDENT] **_Section 3: The logitech_applet_**[INDENT]

First of all some people use a program called LMCtl instead. This section is for making sure your mouse is using the best resolution it can, making it more accurate which is pretty handy especially in games where that counts like Quake 3 :)


_1. Getting everything we need_

There is no logitech_applet in Synaptic so I just download the source and use the program "checkinstall" to package it and install it, you'll also need the "build-essential" packages which can be quite large so bear this in mind and the "libusb-dev" library. Once this is done you can uninstall it if you want via Synaptic. Ok so lets download and install logitech_applet:

```
sudo apt-get install checkinstall build-essential libusb-dev
wget http://detyabozhye.com/other/logitech_applet-0.4test1.tar.gz
tar xvfz logitech_applet-0.4test1.tar.gz
mv ./logitech_applet-0.4test1 ./logitech-applet-0.4test1
cd ./logitech-applet-0.4test1
./configure --prefix=/usr
make
sudo checkinstall
``` 
Just hit enter when checkinstall prompts you. Now it should be installed :)


_2. Working logitech_applet_

I use the command "logitech_applet -s 800 -e" which you can run now:

```
sudo logitech_applet -s 800 -e
``` This sets the mouse resolution to it's maximum 800cpi and makes sure the "cruise control" is enabled, you'll probably have to adjust the mouse settings in gnome as it should be much more accurate now. Type "logitech_applet --help" for more information. 


_3. Load on boot_

We need to add this to a start up script so it's done automatically when the machine boots up, to do this I make a file in /etc/init.d/local where I keep local settings, so lets make that now:

```
sudo gedit /etc/init.d/local
``` Now paste the logitech_applet command, mine like the example above is:

```
echo "Setting up Logitech mouse..."
logitech_applet -s 800 -e
``` I have the echo line so I can check if it works in the boot messages, it's nice but you don't need it.

To make it executable run the following command:
```
sudo chmod 755 /etc/init.d/local
``` 
Now run the following command to make the "local" script run when the system boots:
```
sudo update-rc.d local defaults
``` Now the applet loads automatically on boot, huzzah! :)
[/INDENT] **_Conclusion_**

I think that's everything, phew, this was longer than I expected. I hope it works for you and I haven't made too many mistakes. Please add any corrections and success stories for logitech mice other then the mx510 so we can find out what works.

Thanks to endy's howto, and [http://floam.sh.nu/guides/mx1000](http://floam.sh.nu/guides/mx1000)
Please tell me if you have any problems or if I made any errors.

**Edit**: Fixed the udev rule code, thanks Rizado and khedron.
**Edit**: Fixed the path to xvkbd, thanks to XomboX
**Edit**: Added two packages that need to be installed for click to be compiled.
**Edit**: Added another package that needs to be installed for click to be compiled.
**Edit**: Changed the URL for the logitech_applet, the one on freshmeat seems to be down, so I put it on my site.
**Edit**: Added the requirement for build-essential for compiling click.

---

### Post by Cenotaph on 2006-06-04
Somehow the binds to alt+left and alt+right are causing my side buttons to stop being recognized. so they won't work with neither mozilla or nautilus

in xev the buttons are not displayed when pressed to.

what could be the cause of this?

EDIT: Solved... it's stupid really, I forgot to make the L and the R capitalised for Left and Right. My bad.

Thanks for setting up a 6.06 guide :)

---

### Post by Enigmatic on 2006-06-05
Odd, I followed your steps and restarted X, but when it comes back I just see an Nvidia splash screen and it hangs there. :?

---

### Post by crysys on 2006-06-06
I hit the same problem as Enigmatic.  Here are the last few lines of my xorg log from the failed attempt:

```
(**) Configured Mouse: Device: "/dev/input/mx510"
(EE) Unable to open evdev device "/dev/input/mx510".
(EE) PreInit failed for input device "Configured Mouse"
(II) UnloadModule: "evdev"

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x86) [0x80b4a56]
1: [0xffffe420]
2: /lib/tls/i686/cmov/libc.so.6(malloc+0x81) [0xb7e01411]
3: /usr/bin/X(xf86optionListCreate+0xb0) [0x80d135f]
4: /usr/bin/X(xf86CollectInputOptions+0x34) [0x80b6d7e]
5: /usr/lib/xorg/modules/input/wacom_drv.so [0xb737f1fd]
6: /usr/bin/X(InitInput+0x1a0) [0x809cfe5]
7: /usr/bin/X(main+0x368) [0x806df94]
8: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7db0ea2]
9: /usr/bin/X(FontFileCompleteXLFD+0x81) [0x806d611]

Fatal server error:
Caught signal 11.  Server aborting
```

I did use the 1.0.0.5 evdev listed.  I tried with the current evdev and didn't even get the splash screen.

---

### Post by detyabozhye on 2006-06-06
I think you have a problem with the udev rule, does it work if you use ```
	Option		"Device"	"/dev/input/eventX" #X being the event number you get from "cat /proc/bus/input/devices"
``` instead of ```
	Option		"Device"	"/dev/input/mx***"
```?

---

### Post by Rizado on 2006-06-06
[QUOTE=crysys]I hit the same problem as Enigmatic.  Here are the last few lines of my xorg log from the failed attempt:

```
(**) Configured Mouse: Device: "/dev/input/mx510"
(EE) Unable to open evdev device "/dev/input/mx510".
(EE) PreInit failed for input device "Configured Mouse"
(II) UnloadModule: "evdev"

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x86) [0x80b4a56]
1: [0xffffe420]
2: /lib/tls/i686/cmov/libc.so.6(malloc+0x81) [0xb7e01411]
3: /usr/bin/X(xf86optionListCreate+0xb0) [0x80d135f]
4: /usr/bin/X(xf86CollectInputOptions+0x34) [0x80b6d7e]
5: /usr/lib/xorg/modules/input/wacom_drv.so [0xb737f1fd]
6: /usr/bin/X(InitInput+0x1a0) [0x809cfe5]
7: /usr/bin/X(main+0x368) [0x806df94]
8: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7db0ea2]
9: /usr/bin/X(FontFileCompleteXLFD+0x81) [0x806d611]

Fatal server error:
Caught signal 11.  Server aborting
```

I did use the 1.0.0.5 evdev listed.  I tried with the current evdev and didn't even get the splash screen.[/QUOTE]You have changed your udev rule to NAME="input/mx510" instead of NAME="input/mx500" right?
Make sure evdev module is loaded too. Do "lsmod | grep evdev" and if it doesn't show up do "sudo modprobe evdev" and add evdev to /etc/modules

I have a feeling it's necessary to reload udev to create the new device nodes. Not sure about it though. Just run "sudo /etc/init.d/udev restart" or reboot.

**detyabozhye**
Isn't there something missing in step 1.1? "sudo gedit /etc/udev/rules." should be something like "gksu gedit /etc/udev/rules.d/number-fancyname.rules"

---

### Post by khedron on 2006-06-06
Firstly, I would like to second Rizado. There is a typo in the udev setup instructions. Where it says
```
sudo gedit /etc/udev/rules.
```
you really mean ```
sudo gedit /etc/udev/rules.d/19-local.rules
```

Secondly, with the MX700 I have a problem with the udev rule. Your ```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", NAME="input/mx700" 
``` (edited for my configuration) will match both my keyboard and my mouse, as both of them use the same USB receiver (they are wireless, remember). I'm not familiar with udev rules: is there some other criterion I could use to distinguish the keyboard from the mouse? Or is it possible to use ```

    Option        "Dev Phys"        "usb-*/input1"
    Option        "Device"          "/dev/input/ts0"
```
instead of /dev/input/mx700, like for Breezy?

---

### Post by XomboX on 2006-06-06
Nice HOWTO, but it works till section2 for me.
I can not get xbindkeys to work :-(

Xbindkeys simply doesn`t work for mouse buttons :-(
Can someone help me?

How can I get to know the "action"? 
For example I want to run minimalize firefox with my thumb button. Where can I find the code for action "minimalize"?

Thanks for help!

---

### Post by ironfistchamp on 2006-06-06
Using the evdev package from the link posted here I still get 

     Unknown protocol: "evdev"

What's gone wrong? This is the section from my xorg.conf

   Section "InputDevice" 
       Identifier "Configured Mouse" 
       Driver "mouse"
       Option         "CorePointer" 
       Option "Protocol" "evdev" 
       Option "Dev Name" "Logitech USB Receiver" 
       Option "Dev Phys" "usb-0000:00:02.0-3/input0"
       Option "Device"   "mouse1 event3 ts1"
       Option "Buttons" "10" 
       Option "ZAxisMapping" "4 5" 
   EndSection

I read that using careful ZAxisMapping you don't need to use xmodmap

Thanks

Ironfistchamp

---

### Post by XomboX on 2006-06-06
ironfistchamp:
I think there is a mistake in your xorg.conf. You should write "evdev" instead "mouse" after driver option.

Finally:
Section "InputDevice"
Identifier "Configured Mouse"
Driver "[COLOR="Red"]evdev[/COLOR]"
Option "CorePointer"
Option "Protocol" "evdev"
Option "Dev Name" "Logitech USB Receiver"
Option "Dev Phys" "usb-0000:00:02.0-3/input0"
Option "Device" "mouse1 event3 ts1"
Option "Buttons" "10"
Option "ZAxisMapping" "4 5"
EndSection

---

### Post by ironfistchamp on 2006-06-06
Thanks I'll give that a try.

EDIT: I tried that and now when I try starting gdm I get the error

   *** glibc detected *** malloc(): memory corruption(fast): 0x082484a0 ***

I went to recovery from the GRUB menu and it hung. It was at a part mentioning IPv6. I'm not 100%

can someone help?

Thanks

---

### Post by detyabozhye on 2006-06-06
[QUOTE=Rizado]**detyabozhye**
Isn't there something missing in step 1.1? "sudo gedit /etc/udev/rules." should be something like "gksu gedit /etc/udev/rules.d/number-fancyname.rules"[/QUOTE]
Yes, thanks for pointing that out, fixed it.

---

### Post by detyabozhye on 2006-06-06
[QUOTE=khedron]Firstly, I would like to second Rizado. There is a typo in the udev setup instructions. Where it says
```
sudo gedit /etc/udev/rules.
```
you really mean ```
sudo gedit /etc/udev/rules.d/19-local.rules
```
[/QUOTE]
Thanks, fixed.
[QUOTE=khedron]
Secondly, with the MX700 I have a problem with the udev rule. Your ```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", NAME="input/mx700" 
``` (edited for my configuration) will match both my keyboard and my mouse, as both of them use the same USB receiver (they are wireless, remember). I'm not familiar with udev rules: is there some other criterion I could use to distinguish the keyboard from the mouse? Or is it possible to use ```

    Option        "Dev Phys"        "usb-*/input1"
    Option        "Device"          "/dev/input/ts0"
```
instead of /dev/input/mx700, like for Breezy?[/QUOTE]
I think it should work without udev like in Breezy, but I had the input number change once while using Dapper Beta, and it made my X crash at startup, so I used the udev rule. Honestly, my knowledge of udev isn't so great either, so I don't know how you would distinguish the keyboard and mouse with it.

---

### Post by detyabozhye on 2006-06-06
[QUOTE=XomboX]Nice HOWTO, but it works till section2 for me.
I can not get xbindkeys to work :-(

Xbindkeys simply doesn`t work for mouse buttons :-(
Can someone help me?

How can I get to know the "action"? 
For example I want to run minimalize firefox with my thumb button. Where can I find the code for action "minimalize"?

Thanks for help![/QUOTE]
First you must find out which command does minimize in you window manager settings (GNOME: System->Prefrences->Keyboard Shortcuts, XFCE: Xfce Menu->Settings->Window Manager Settings->Keyboard, etc.)

Mine is Alt+F8

So I would change whichever thumb button I want to fo the minimization in my .xbindkeysrc to this:
```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[F8]""
  m:0x0 + b:6 #replace 6 with whichever button it will be
```

---

### Post by detyabozhye on 2006-06-06
[QUOTE=ironfistchamp]Using the evdev package from the link posted here I still get 

     Unknown protocol: "evdev"

What's gone wrong? This is the section from my xorg.conf

   Section "InputDevice" 
       Identifier "Configured Mouse" 
       Driver "mouse"
       Option         "CorePointer" 
       Option "Protocol" "evdev" 
       Option "Dev Name" "Logitech USB Receiver" 
       Option "Dev Phys" "usb-0000:00:02.0-3/input0"
       Option "Device"   "mouse1 event3 ts1"
       Option "Buttons" "10" 
       Option "ZAxisMapping" "4 5" 
   EndSection

I read that using careful ZAxisMapping you don't need to use xmodmap

Thanks

Ironfistchamp[/QUOTE]
Your device option is also incorrect, try changing it to:
```
   Section "InputDevice" 
       Identifier "Configured Mouse" 
       Driver "evdev"
       Option         "CorePointer" 
       Option "Dev Name" "Logitech USB Receiver" 
       Option "Dev Phys" "usb-0000:00:02.0-3/input0"
       Option "Device"   "/dev/input/event3"
   EndSection
```
If that doesn't work, try without the "Dev Name" and "Dev Phys" options

ZAxisMapping doesn't have any effect on the current evdev driver.

---

### Post by ironfistchamp on 2006-06-06
I shall make the changes if I can get into my OS. It is totally tanked atm. Not good. 

Thanks

Ironfistchamp

---

### Post by NT4usB on 2006-06-07
For those who like to use the thumb button to open and close tabs (middlebutton) in Firefox, the mapping for a Mx310  is:
pointer = 1 3 6 4 5 10 9 2 7 8 11..

How can I make the scroll wheel go a page at a time instead of the 3 or so lines it goes now?

---

### Post by ironfistchamp on 2006-06-07
Used a live CD to edit the udev rules (i.e. remove them) as recommended by friend. No luck. Then edited xorg.conf back to the old "no evdev" configuration. Worked like a charm. 

I guess evdev just isn't for me. If anyone can shed some light on this that would be great.

Thanks

Ironfistchamp

---

### Post by XomboX on 2006-06-07
[QUOTE=detyabozhye]First you must find out which command does minimize in you window manager settings (GNOME: System->Prefrences->Keyboard Shortcuts, XFCE: Xfce Menu->Settings->Window Manager Settings->Keyboard, etc.)

Mine is Alt+F8

So I would change whichever thumb button I want to fo the minimization in my .xbindkeysrc to this:
```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[F8]""
  m:0x0 + b:6 #replace 6 with whichever button it will be
```[/QUOTE]

Thank you for your answer. However it still doesn`t work ](*,) 

I have the same command (in GNOME: System->Prefrences->Keyboard Shortcuts) as you: ALT+F8.

I have got a Logitech mouseman Dual optical with 6 buttons (wheel = 2 buttons -up and down) connected in USB.
I have done all the things which are described in the guide (edited files: xorg.conf, 19-local.rules, .Xmodmap, .xbindkeysrc).

Then:
- when I run xev and press my thumb button it says:

[I]ButtonPress event, serial 29, synthetic NO, window 0x2a00001,
    root 0x4c, subw 0x0, time 2913354372, (65,104), root:(70,892),
    state 0x10, button 6, same_screen YES[/I]

- then I run "xbindkeys" in terminal and looking forward to working thumb button but i does nothing

- I run xev again and press my thumb button again and now it says:

[I]EnterNotify event, serial 26, synthetic NO, window 0x2200001,
    root 0x4c, subw 0x0, time 2913518473, (87,96), root:(165,191),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
    focus NO, state 16[/I]

[I]KeymapNotify event, serial 26, synthetic NO, window 0x0,
    keys:  76  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0[/I]


[COLOR="Blue"]**xorg.conf**[/COLOR]
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mouseman" #this should be that underlined name from 19-local.rules
EndSection

[COLOR="Blue"]**/etc/udev/rules.d/**[/COLOR]
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB-PS/2 Optical Mouse", NAME="input/mouseman"

[COLOR="Blue"]**~/.Xmodmap**[/COLOR]
pointer = 1 3 2 4 5 8 9 6 7 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32

[COLOR="Blue"]**~/.xbindkeysrc**[/COLOR]
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[F8]""
  m:0x0 + b:6 #replace 6 with whichever button it will be

[COLOR="Red"]IMPORTANT:[/COLOR]
I should mention there isn`t any xvkbd file in "/usr/X11R6/bin/". There is only "X" file.
Then I look for "xvkbd" in nautilus it finds: "/etc/X11/app-defaults/XVkbd" It is the only XVkbd file I have on my harddisk.

So, I hope it`s enough. Would you be so kind and help me with that problem? When I can not use my thumb button I feel like without one finger :-(

Thx!!

XomboX

---

### Post by detyabozhye on 2006-06-07
OK, I remember now! With some updates, the path to xvkbd changed. Replace ```
/usr/X11R6/bin/xvkbd
``` with ```
/usr/bin/xvkbd
```

Edit: Fixed the HOWTO.

---

### Post by detyabozhye on 2006-06-07
[QUOTE=ironfistchamp]Used a live CD to edit the udev rules (i.e. remove them) as recommended by friend. No luck. Then edited xorg.conf back to the old "no evdev" configuration. Worked like a charm. 

I guess evdev just isn't for me. If anyone can shed some light on this that would be great.

Thanks

Ironfistchamp[/QUOTE]
Removing the udev rules won't autimatically make it work. If you want, you can try to use the event instead of creating a udev rule.

Try:
```
cat /proc/bus/input/devices
```
And rememer the highlighted number from here:
```
I: Bus=0003 Vendor=046d Product=c025 Version=1800
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/class/input/input0
H: Handlers=mouse0 **event0** ts0
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0003 Vendor=049f Product=000e Version=0100
N: Name="Compaq Compaq Internet Keyboard"
P: Phys=usb-0000:00:1d.1-2/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1
B: EV=120003
B: KEY=10000 7 ff87207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: LED=7fff

I: Bus=0003 Vendor=049f Product=000e Version=0100
N: Name="Compaq Compaq Internet Keyboard"
P: Phys=usb-0000:00:1d.1-2/input1
S: Sysfs=/class/input/input2
H: Handlers=kbd event2
B: EV=3
B: KEY=20000 87a 5000d000 1e0000 0 0 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3
B: EV=40001
B: SND=6
```
And change your Device option in xorg.conf to:
```
       Option          "Device"        "/dev/input/**event0**"
```
However, I use udev because yesterday my event number for the mouse was 1, today it's 0. It changes on my system, so I can't recommend it.

---

### Post by sirkelley on 2006-06-07
Hello guys, I got everything working on my mx510 except for one minor problem. I couldn't compile the click for cruise control buttons. I'll post the error and see if anybody know why I couldn't get it fixed. :KS ```
gcc -Wall -c -o click.o click.c
click.c:3:22: error: X11/Xlib.h: No such file or directory
click.c:4:34: error: X11/extensions/XTest.h: No such file or directory
click.c: In function ‘main’:
click.c:9: error: ‘Display’ undeclared (first use in this function)
click.c:9: error: (Each undeclared identifier is reported only once
click.c:9: error: for each function it appears in.)
click.c:9: error: ‘dpy’ undeclared (first use in this function)
click.c:9: warning: implicit declaration of function ‘XOpenDisplay’
click.c:22: warning: implicit declaration of function ‘XTestFakeButtonEvent’
click.c:22: error: ‘True’ undeclared (first use in this function)
click.c:22: error: ‘CurrentTime’ undeclared (first use in this function)
click.c:26: error: ‘False’ undeclared (first use in this function)
click.c:29: warning: implicit declaration of function ‘XCloseDisplay’
make: *** [click.o] Error 1

```

---

### Post by ironfistchamp on 2006-06-07
Well trying without udev but with evdev just got me the same results so I don't whats going on. Guess I'm just not that lucky.

Oh well lifes like that

thanks for the help people maybe when the next evdev comes out ill  try again

Ironfistchamp

---

### Post by detyabozhye on 2006-06-07
> **sirkelley]Hello guys, I got everything working on my mx510 except for one minor problem. I couldn't compile the click for cruise control buttons. I'll post the error and see if anybody know why I couldn't get it fixed. :KS ```
gcc -Wall -c -o click.o click.c
click.c:3:22: error: X11/Xlib.h: No such file or directory
click.c:4:34: error: X11/extensions/XTest.h: No such file or directory
click.c: In function &#8216 said:**
>  Error 1

```

Install these two packages and any dependencies they have via Synaptic:
```
libx11-dev
x11proto-xext-dev
```

---

### Post by moose6589 on 2006-06-08
I went through the instructions, and now I can use the back and forward keys on my MX500 in Nautilus and Firefox, so that is fine and good. 

However, I now have a weird problem. It seems that right-click has been remapped onto my middle mouse button, so when I click that, the right-click menu comes up, and the right-click button doesn't seem to do anything anymore. How can I fix this?

---

### Post by Duffman on 2006-06-08
```
I: Bus=0011 Vendor=0002 Product=0005 Version=0063
N: Name="ImPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio2/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

```

Thats what mine looks like even though its the mx518 usb mouse?

Is that right and should i just continue on with the howto?

---

### Post by pietruszka on 2006-06-08
[QUOTE=Duffman]```
I: Bus=0011 Vendor=0002 Product=0005 Version=0063
N: Name="ImPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio2/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

```

Thats what mine looks like even though its the mx518 usb mouse?

Is that right and should i just continue on with the howto?[/QUOTE]

I have mx518 and I'm using the newest evdev driver.  I couldn't get it to work with the old driver + xmodmap for some reason.  What I had to do is create a SYMLINK to the /dev/input/eventX where X is the number that gets assigned to  the mouse.  The only name that the new evdev driver would work with was input/eventX where X is a number (even though udev would create them and I was able to use them with "cat /dev/mx518" for example.)  
So I noticed that my mouse would always get either input/event1 or input/event3 and also that input/event0 was not used by anything I cared for.  So I've created following udev rule:
```

KERNEL=="event[13]", SYSFS{../name}=="Logitech USB-PS/2 Optical Mouse", SYMLINK="input/event0"

```

So now /dev/input/event0 always points at the correct event # for my mouse.

Next I pointed xorg.conf to /dev/input/event0 and it works like a charm now.  Even the side buttons get recognized w/o using xmodmap.

Hope that helps someone.

---

### Post by XomboX on 2006-06-08
Guyzzz, can not you relly help me with the problem on the previous page (2)? 
I don`t know what else should I try :-(

Thank you a lot.

---

### Post by zAo on 2006-06-08
Thanks, but it causes my machine to freeze! Rebooted in Single User Mode and found:
```

zao@amd:~$ tail /var/log/Xorg.0.log
(EE) PreInit returned NULL for "Configured Mouse"
(WW) No core pointer registered
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) evdev brain: Rescanning devices (2).
No core pointer

Fatal server error:
failed to initialize core devices

```
My xorg.conf:
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/g5"
EndSection

```
My /etc/udev/rules.d/19-local.rules:
```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Gaming Mouse",NAME="input/g5"
```

All ideas are welcome :)

---

### Post by detyabozhye on 2006-06-08
[QUOTE=moose6589]I went through the instructions, and now I can use the back and forward keys on my MX500 in Nautilus and Firefox, so that is fine and good. 

However, I now have a weird problem. It seems that right-click has been remapped onto my middle mouse button, so when I click that, the right-click menu comes up, and the right-click button doesn't seem to do anything anymore. How can I fix this?[/QUOTE]
Try switching "2" and  "3" places in .Xmodmap

---

### Post by detyabozhye on 2006-06-08
[QUOTE=Duffman]```
I: Bus=0011 Vendor=0002 Product=0005 Version=0063
N: Name="ImPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio2/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

```

Thats what mine looks like even though its the mx518 usb mouse?

Is that right and should i just continue on with the howto?[/QUOTE]
well, if it's plugged into the USB, it should work, but the Phys does look weird there, so I don't know if it will work.

---

### Post by detyabozhye on 2006-06-08
[QUOTE=XomboX]Guyzzz, can not you relly help me with the problem on the previous page (2)? 
I don`t know what else should I try :-(

Thank you a lot.[/QUOTE]
I posted it here: [http://ubuntuforums.org/showpost.php?p=1107499&postcount=20](http://ubuntuforums.org/showpost.php?p=1107499&postcount=20)
Did you try that?

---

### Post by detyabozhye on 2006-06-08
[QUOTE=zAo]Thanks, but it causes my machine to freeze! Rebooted in Single User Mode and found:
```

zao@amd:~$ tail /var/log/Xorg.0.log
(EE) PreInit returned NULL for "Configured Mouse"
(WW) No core pointer registered
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) evdev brain: Rescanning devices (2).
No core pointer

Fatal server error:
failed to initialize core devices

```
My xorg.conf:
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/g5"
EndSection

```
My /etc/udev/rules.d/19-local.rules:
```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Gaming Mouse",NAME="input/g5"
```

All ideas are welcome :)[/QUOTE]
what happens when you try just using "/dev/input/eventX" (X being event number)?

---

### Post by XomboX on 2006-06-09
[QUOTE=detyabozhye]I posted it here: [http://ubuntuforums.org/showpost.php?p=1107499&postcount=20](http://ubuntuforums.org/showpost.php?p=1107499&postcount=20)
Did you try that?[/QUOTE]

Yes, I have tried it. Well, the thumb button works as a bakward in firefox, but it does nothing in nautilus. When I run xev, it correctly recognizes the thumb button as button number 6!! Good step :) Thank you, man!

This is my .xbindkeysrc:

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
  m:0x0 + b:2

I want the middle button to work as forward and thumb button as backward. However it doesn`t work. The problem must be in xbindkeys.

Notice: when I run" xbindkeys -key" and I click whichever mouse button, it does nothing. It can only recognize keyboard buttons. Isn`t the problem somewhere here?

---

### Post by moose6589 on 2006-06-09
[QUOTE=detyabozhye]Try switching "2" and  "3" places in .Xmodmap[/QUOTE]
Thanks, that did the trick.

---

### Post by souled on 2006-06-09
I'm trying to 'make' click, but I'm getting this error.
```
gcc -Wall -o click click.o -L /usr/X11R6/lib/ -lX11 -lXtst
/usr/bin/ld: cannot find -lXtst
collect2: ld returned 1 exit status
make: *** [click] Error 1

```
I installed the two packages listed before, but I'm still getting this error. Anyone have a fix for this?

---

### Post by detyabozhye on 2006-06-09
[QUOTE=XomboX]Yes, I have tried it. Well, the thumb button works as a bakward in firefox, but it does nothing in nautilus. When I run xev, it correctly recognizes the thumb button as button number 6!! Good step :) Thank you, man!

This is my .xbindkeysrc:

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
  m:0x0 + b:2

I want the middle button to work as forward and thumb button as backward. However it doesn`t work. The problem must be in xbindkeys.

Notice: when I run" xbindkeys -key" and I click whichever mouse button, it does nothing. It can only recognize keyboard buttons. Isn`t the problem somewhere here?[/QUOTE]
well, to test and see if it is xbindkeys or not, try to make button 6 (or whichever) launch a known app, like gedit (if ur running Gnome), for example:
```
"/usr/bin/gedit"
  m:0x0 + b:6
```
If it launches gedit, then it's not xbindkeys.

Remember, when you change .xbindkeysrc, you should restart xbindkeys:
```
killall xbindkeys
xbindkeys
```

---

### Post by detyabozhye on 2006-06-09
[QUOTE=souled]I'm trying to 'make' click, but I'm getting this error.
```
gcc -Wall -o click click.o -L /usr/X11R6/lib/ -lX11 -lXtst
/usr/bin/ld: cannot find -lXtst
collect2: ld returned 1 exit status
make: *** [click] Error 1

```
I installed the two packages listed before, but I'm still getting this error. Anyone have a fix for this?[/QUOTE]
Try installing xlibs-dev

---

### Post by XomboX on 2006-06-10
[QUOTE=detyabozhye]well, to test and see if it is xbindkeys or not, try to make button 6 (or whichever) launch a known app, like gedit (if ur running Gnome), for example:
```
"/usr/bin/gedit"
  m:0x0 + b:6
```
If it launches gedit, then it's not xbindkeys.

Remember, when you change .xbindkeysrc, you should restart xbindkeys:
```
killall xbindkeys
xbindkeys
```[/QUOTE]

OK. I have just tried it. It nothing has changed. The thumb button still works as a backwards in firefox only. Xbindkeys ignores my .xbindkeysrc.

I also tried to bind CTRL+N, but it didn`t work too. So the problem is not in mouse but in XBINKEYS.
```
"/usr/bin/gedit"
    m:0x14 + c:37
    Control+Mod2 + Control_L
```

So what next shall I try?

Thx!

---

### Post by detyabozhye on 2006-06-10
hmm, that's weird, I don't know what can be done in this case. Maybe you could give imwheel a go?

---

### Post by XomboX on 2006-06-10
[QUOTE=detyabozhye]hmm, that's weird, I don't know what can be done in this case. Maybe you could give imwheel a go?[/QUOTE]

What a pitty :-k   Thank you for your selfsacrifice, detyabozhye!
[COLOR="Red"]
Is here anyone who has got all-buttons working [/COLOR][COLOR="Blue"]Logitech Mouseman Dual optical[/COLOR]?

---

### Post by Skaman on 2006-06-11
Does this HOWTO works even if I connect the mouse using the PS2 Port?
> I: Bus=0011 Vendor=0002 Product=0002 Version=0064
N: Name="PS2++ Logitech MX Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event2 ts0
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103


---

### Post by Skaman on 2006-06-11
[QUOTE=Skaman]Does this HOWTO works even if I connect the mouse using the PS2 Port?[/QUOTE]
i answer myself: doesnt](*,)

---

### Post by XomboX on 2006-06-11
I reinstalled the Ubuntu and now the thumb button works for "/usr/bin/gedit"!!!!

Look:

[COLOR="Blue"]
xombox@Brusinka:~$ [/COLOR]xbindkeys -v

displayName = :0.0
rc file = /home/xombox/.xbindkeysrc
rc guile file = /home/xombox/.xbindkeysrc.scm
getting rc guile file /home/xombox/.xbindkeysrc.scm.
WARNING : /home/xombox/.xbindkeysrc.scm not found or reading not allowed.
2 keys in /home/xombox/.xbindkeysrc

min_keycode=8     max_keycode=255 (ie: know keycodes)

"/usr/bin/gedit"
    m:0x0 + b:2   (mouse)
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
    m:0x0 + b:6   (mouse)

starting loop...
[COLOR="Red"](I pressed the middle button)[/COLOR]
Button press !
e.xbutton.button=2
e.xbutton.state=16
"/usr/bin/gedit"
    m:0x0 + b:2   (mouse)
Start program with fork+exec call
Button release !
e.xbutton.button=2
e.xbutton.state=528
Catch CHLD signal -> pid 6684 terminated 

[COLOR="Red"](I pressed the thumb button)[/COLOR]
Button press !
e.xbutton.button=6
e.xbutton.state=16
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
    m:0x0 + b:6   (mouse)
Start program with fork+exec call
Catch CHLD signal -> pid 6692 terminated
Button release !
e.xbutton.button=6
e.xbutton.state=16

---

### Post by Brent Dax on 2006-06-11
I have a much simpler configuration that seems to work.  No udev, just this:

```
# The Logitech mouse
Section "InputDevice"
	Identifier "Logitech MX600"
	Driver "evdev"
	
	Option "Name" "Logitech USB Receiver"
	Option "Phys" "*/input1"
	
	Option "SendCoreEvents" "true"
EndSection

# Another wireless mouse I use sometimes
Section "InputDevice"
	Identifier "Wireless Notebook Mouse"
	Driver "evdev"

	Option "Name" "Microsoft Microsoft Wireless Optical Mouse® 1.00"
	
	Option "SendCoreEvents" "true"
EndSection
```My main mouse is an MX600 (comes with the MX3000 keyboard); I plug it into my laptop occasionally.  As you can see, I also have a little Microsoft portable mouse for travel.  This configuration (plus a little bit of xbindkeys magic to make the back and forward buttons switch between Compiz workspaces) seems to work like a charm, except that the "zoom in" and "zoom out" buttons don't work.  I can plug and unplug my mice with impunity and boot with none, one, or all of them present.  It's great.

---

### Post by ADVERSiTY on 2006-06-13
Great guide, everything works great except...

I have to restart my system 1-3 times in order to use my mouse/keyboard. I have an MX3100 desktop (Mx1000 & multimedia keyboard [LX700??]) and when GDM loads neither my mouse nor keyboard works. After rebooting a few times (sometimes once) all works fine and all of my buttons work once inside GNOME.

Possibly something to do with my keyboard & mouse using the same hub? I have two instances of "Logitech USB Receiver" when performing cat /proc/bus/input/devices

Any advice?

---

### Post by detyabozhye on 2006-06-13
hmm, I don't know, that's a tough one.

---

### Post by ADVERSiTY on 2006-06-14
I forgot to add that it doesn't do this *every* time on boot, it appears to be random. Sometimes I can boot rightup and have everything working, other times it won't. I wonder if this has anything to do with changing event number? Although I used the "NAME" method, so I'm not sure if that would affect it.

I can deal with it though, as it's not all that big of a problem, just kind of an annoyance. I'm just happy to have all of my buttons working :)

---

### Post by fargoth on 2006-06-14
funny, i got the middle button acting like the right button and the right button acting like the middle button.... and <button 10> (the one above the scroll down button acts like the left button.....)

whats wrong with my settings?

oh, and i stopped doing the HOWTO after the part with click, because it wont compile.... if you could help me with that too, id be greatful... it says:
```


gcc -Wall -o click click.o -L /usr/X11R6/lib/ -lX11 -lXtst
/usr/bin/ld: cannot find -lXtst

```

---

### Post by fargoth on 2006-06-14
well, if anyone get the message i got, just install libxtst-dev.

anyway... this wierd button behaviour is making me nuts!
anyone knows whats wrong?

---

### Post by fargoth on 2006-06-14
ok.... i don't know if it's only my mx500... but using 1 3 2 in Xmodmap is wrong... 1 2 3 makes the buttons work fine.

---

### Post by fargoth on 2006-06-14
i tried adding 
```

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Tab]""
  m:0x0 + b:10

```
but that doesn't do what Alt+tab does.... how can i emulate Alt+tab with my mouse? (im using compiz...)

---

### Post by detyabozhye on 2006-06-14
[QUOTE=fargoth]i tried adding 
```

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Tab]""
  m:0x0 + b:10

```
but that doesn't do what Alt+tab does.... how can i emulate Alt+tab with my mouse? (im using compiz...)[/QUOTE]
Alt+Tab only works while it's being pressed, so you can't really make it di the Alt+Tab thing on Linux unless you build an application switcher app yourself. But since you're running compiz, you could map it to F12 (or if you changed it, the key for the Expose like feature) to activate the Expose like thing. :)

---

### Post by jnev on 2006-06-15
[QUOTE=fargoth]ok.... i don't know if it's only my mx500... but using 1 3 2 in Xmodmap is wrong... 1 2 3 makes the buttons work fine.[/QUOTE]

my mx510 works the same... when it was 1 3 2 the middle click was switched with the right click.

---

### Post by detyabozhye on 2006-06-16
[QUOTE=jnev]my mx510 works the same... when it was 1 3 2 the middle click was switched with the right click.[/QUOTE]
It depends on your X server and driver I guess. For me, regular Xorg and 1 3 2 do it, with Xgl I have to change it to 1 2 3.

---

### Post by fargoth on 2006-06-16
[QUOTE=detyabozhye]Alt+Tab only works while it's being pressed, so you can't really make it di the Alt+Tab thing on Linux unless you build an application switcher app yourself. But since you're running compiz, you could map it to F12 (or if you changed it, the key for the Expose like feature) to activate the Expose like thing. :)[/QUOTE]

i change the line to:
"/usr/bin/xvkbd -xsendevent -text "\[F12]""
  m:0x0 + b:10

but it still doesnt work... 
xev gave me this:
```

KeyPress event, serial 31, synthetic YES, window 0x3a00001,
    root 0x52, subw 0x0, time 0, (1,1), root:(1,1),
    state 0x0, keycode 96 (keysym 0xffc9, F12), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic YES, window 0x3a00001,
    root 0x52, subw 0x0, time 0, (1,1), root:(1,1),
    state 0x0, keycode 96 (keysym 0xffc9, F12), same_screen YES,
    XLookupString gives 0 bytes:

EnterNotify event, serial 31, synthetic NO, window 0x3a00001,
    root 0x52, subw 0x0, time 3733416567, (81,136), root:(95,207),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  82  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

```

it says i pressed F12 doesn't it?... wonder why compiz won't act like it does to normal F12 key-stroke...

any ideas?

---

### Post by detyabozhye on 2006-06-16
If you hit F12 on the keyboard, does it work?

---

### Post by tellnes on 2006-06-17
I edited this post, after seeing all i missed was a L and a R in the config..it works now..great howto!!:razz:

---

### Post by firezip on 2006-06-17
Can the author re look and re-edit this? The first time I did this my Ubuntu just locked up and I had to do a clean install.  Thanks :)

---

### Post by detyabozhye on 2006-06-17
[QUOTE=firezip]Can the author re look and re-edit this? The first time I did this my Ubuntu just locked up and I had to do a clean install.  Thanks :)[/QUOTE]
Well, I would need to know exactly what happened to see why it locked up, I don't know what error messages you got or whatever, so I don't know what I could edit. BTW, always remember to make a backup of xorg.conf, so in case something goes wrong, you can revert back to the old settings.

---

### Post by fargoth on 2006-06-18
[QUOTE=detyabozhye]If you hit F12 on the keyboard, does it work?[/QUOTE]

yep pressing F12 on the keyboard does what it should do... but the mouse won't do it even though it seems to generate the keypress for F12....
any ideas?

---

### Post by lennox on 2006-06-19
THANK YOU detyabozhye!

It is really important for me to have the side keyes of my MX1000 working as forward and backward while browsing, and your howto did the trick.
:D :D :D :D :D 
For me it worked with the normal evdev in Dapper (1:1.1.2-0ubuntu3), the thing I was missing was the changed path to xvkbd.
Also I did not need the udev stuff (until now), my xorg.conf looks like this:
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Name"                  "Logitech USB Receiver"
        Option          "Dev Phys"              "usb-0000:00:10.0-1/input0"
        Option          "ZAxisMapping"          "4 5 6 7"
        Option          "Buttons"               "12"
        Option          "Resolution"            "800"
EndSection
```
I found out in Xlog that xorg automatically maps the buttons 6 and 7 to horizontal scrolling (which is their purpose), and that directly worked.
In old evdev my mouse was recognized as having 12 buttons (which is true), but now Xlog says it has 20. I dont know why, but the only thing that changes is that I have to add some more numbers when using xmodmap (which I do to map the middle mouse button to the side button as that one does not work properly anymore).
```

! Swap middle mouse button and side mouse button
pointer = 1 10 3 4 5 6 7 8 9 2 11 12 13 14 15 16 17 18 19 20

! make caps lock escape
remove Lock = Caps_Lock
keysym Caps_Lock = Escape

```
I kept in the latter part because I think it is useful (especially for vim users).

---

### Post by Attila on 2006-06-19
Hi all, I've followed the howto and my mx510 works well, but when I go to university and I take with me a mini-mouse (and I left the mx510 at home) Xserver wouldn't start because the mx510 device isn't plugged in.
I have to edit everytime xorg.conf and reboot.

Another thing is that when I'm using my mx510 the touchpad seems disabled, and when I don't use logitech mouse everything ok...:mad:

---

### Post by detyabozhye on 2006-06-19
[QUOTE=fargoth]yep pressing F12 on the keyboard does what it should do... but the mouse won't do it even though it seems to generate the keypress for F12....
any ideas?[/QUOTE]
Hmm, it does F12 here, I'll try it next time I'm in Xgl and see what I get.

---

### Post by detyabozhye on 2006-06-19
[QUOTE=Attila]Hi all, I've followed the howto and my mx510 works well, but when I go to university and I take with me a mini-mouse (and I left the mx510 at home) Xserver wouldn't start because the mx510 device isn't plugged in.
I have to edit everytime xorg.conf and reboot.

Another thing is that when I'm using my mx510 the touchpad seems disabled, and when I don't use logitech mouse everything ok...:mad:[/QUOTE]
Some else has this working correctly, they left the mouse with the "mouse" driver and added the evdev mouse as well, and they changed "CorePointer" to "SendCoreEvents" I believe. I don't have a laptop, so I can't really test this.

---

### Post by fargoth on 2006-06-19
[QUOTE=detyabozhye]Hmm, it does F12 here, I'll try it next time I'm in Xgl and see what I get.[/QUOTE]

thanks, i'll be waiting for your answer, it really is wierd.

---

### Post by Attila on 2006-06-19
[QUOTE=detyabozhye]Some else has this working correctly, they left the mouse with the "mouse" driver and added the evdev mouse as well, and they changed "CorePointer" to "SendCoreEvents" I believe. I don't have a laptop, so I can't really test this.[/QUOTE]
How can I do it?

---

### Post by detyabozhye on 2006-06-20
[QUOTE=Attila]How can I do it?[/QUOTE]
I can't guarentee it'll work, because I haven't tried it, but I guess you would leave the "mouse" mouse and add the evdev mouse to xorg.conf, then replace ```
	Option "CorePointer"
``` with ```
	Option "SendCoreEvents" "true"
``` in the evdev mouse.

---

### Post by brownrl on 2006-06-20
This seems to work for the browser ok except:

There is this really annoying thing with firefox. 

Sometimes when you hit back, thumb button on the MX1000 it will go all the way back to the very first page that you opened. Not just back one page.

You can see that it is like stuck in a loop. All previous pages flash up.

I added -no-repeat to the xvkbd command in xbindkeys

"xvkbd -no-repeat -text "\[Alt_L]\[Left]""
   m:0x10 + b:8 + Release
"xvkbd -no-repeat -text "\[Alt_L]\[Right]""
   m:0x10 + b:9 + Release


No Luck, is there something more that I should do?

Thanks
Rob

---

### Post by Xecuter on 2006-06-23
Has someone got their MX700 working? I haven't and I'm tired of guessing. Please give me a quick guide.

---

### Post by detyabozhye on 2006-06-23
It should, but you might have to change the .Xmodmap around and it might work with the current evdev driver, can't give any guarentees tho.

---

### Post by phoenix42 on 2006-06-23
[QUOTE=fargoth]yep pressing F12 on the keyboard does what it should do... but the mouse won't do it even though it seems to generate the keypress for F12....
any ideas?[/QUOTE]

Hi,
I had the same problem - I solved it by simply replacing F12 with Button10 in gset-compiz -> shortcuts -> plugins -> scale. It's not using xbingkeys but the result is the same.
Hope I helped.


P.S.: First post - \\:D/

---

### Post by fargoth on 2006-06-23
[QUOTE=phoenix42]Hi,
I had the same problem - I solved it by simply replacing F12 with Button10 in gset-compiz -> shortcuts -> plugins -> scale. It's not using xbingkeys but the result is the same.
Hope I helped.


P.S.: First post - \\:D/[/QUOTE]

congrats on the first post :-D 
it didn't work for me though... Button10 does nothing when i put it as a shortcut... and i deleted the xbindkeys entry...

---

### Post by MikeMLP on 2006-06-27
Linux newbie here:

I'm stuck when I try to start mapping forward and back in nautilus

~$ sudo apt-get install xvkbd xbindkeys
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xvkbd

what does this mean?

---

### Post by detyabozhye on 2006-06-27
[QUOTE=MikeMLP]Linux newbie here:

I'm stuck when I try to start mapping forward and back in nautilus

~$ sudo apt-get install xvkbd xbindkeys
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xvkbd

what does this mean?[/QUOTE]
You need to enable the Universe repositories, see: [https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages](https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages)

Welcome to Ubuntu forums, btw. ^_^

---

### Post by souled on 2006-06-27
How come when I try to set the path for click it won't work? I moved click and click.o to /usr/bin, and it won't work. However, when it's in ~/click/click, it will work... I've tried just setting click (because it's in my $PATH) and also /usr/bin/click, but it still won't work.

Regardless of the path I set to click, that portion in the xbindkeyrc will only work if the click folder is located at ~/click... Even if I set the path to /usr/bin/click, if I have click at ~/click, it will work. I don't want to have this folder in my home folder, is there a way I can move it to wherever I want?

---

### Post by detyabozhye on 2006-06-27
hmm, I don't know, I haven't tried. Do you think it could work if you made the folder ~/.click (<- hidden)?

---

### Post by souled on 2006-06-27
Nope... .click will not work.

---

### Post by basementjack on 2006-06-28
Hi

Just upgraded to Dapper yesterday and is still having a problem with my mouse. I tried following the guide to the best of my skills, but alast is left with a semi-functioning mouse.

The problem seems to be that the event the side buttons make isn't recognized. In xev it is described as a "LeaveNotify EnterNotify KeymapNotify" of course with a lot of infomation that's impossible to copy. :wink:

Does anyone have an idea what is wrong here?

_xorg.conf(mouse)_
```
Section "InputDevice"
        Identifier "Configured MX700 Mouse"
        Driver "evdev"
        Option "CorePointer"
        Option "Protocol"       "evdev"
        Option "Dev Name"       "Logitech USB Receiver"
        Option "Dev Phys"       "usb-*/input0"
        Option "Device"         "/dev/input/mx700"
        Option "Buttons" "10"
        Option "ZAxisMapping" "4 5"
EndSection
```
The following sections have been completed:
 - installing the old evdev
 - locked the version to the evdev
 - udev
 - editing the xorg.conf
 - xmodmap (may or may not be here the problem lies, since I have directly copy the example from this HowTo into my ~/.Xmodmap, but I doubt it.)
 - xbindkeys (installed when using breezy, have updated the path to xbindkeys and xvkbd)
The rest have been skipped untill I get my sidebuttons working. :confused:

---

### Post by detyabozhye on 2006-06-28
What do you get in xev with xbindkeys turned off?

---

### Post by basementjack on 2006-06-28
Without xbindkeys xev shows the button-presss and -release events, I already checked that it works in Firefox. So far so good, however Nautilus does not work without the xbindkeys (but it didn't work with it either).

The problem then becomes how to get Nautilus working. :/

---

### Post by spockrock on 2006-06-28
thanks so much I got my mouse working perfectly.....

---

### Post by detyabozhye on 2006-06-28
[QUOTE=basementjack]Without xbindkeys xev shows the button-presss and -release events, I already checked that it works in Firefox. So far so good, however Nautilus does not work without the xbindkeys (but it didn't work with it either).

The problem then becomes how to get Nautilus working. :/[/QUOTE]
I wanted to know the button numbers shown in xev, but since they work in Firefox, they should be 6 an 7 then. So, the problem is most likely in xbindkeys or xvkbd.

---

### Post by mikwig on 2006-06-29
Thankyou this worked well for me - and my Mouse is Samsung.

Actually it is a logitech m-uv96 distributed by Samsung. So people
with Sumsung usb opticle mice - try this out.

---

### Post by ratsalad on 2006-07-03
I'm trying to get this to work on a 6.06 amd64 install... anyone have ideas where I can find a amd64 build of evdev 1.0.0.5? I can't find it anywhere :evil:

---

### Post by monomaniacpat on 2006-07-03
I have a Microsoft Wireless Optical Mouse 2.0 connected through USB and sharing with the comfort keyboard. Would this guide help it's functionality? I often have trouble clicking the mouse button. This problem is specific to linux.

Help would be most appreciated.

---

### Post by detyabozhye on 2006-07-03
[QUOTE=monomaniacpat]I have a Microsoft Wireless Optical Mouse 2.0 connected through USB and sharing with the comfort keyboard. Would this guide help it's functionality? I often have trouble clicking the mouse button. This problem is specific to linux.

Help would be most appreciated.[/QUOTE]
I think it should, but I would recommend trying the current evdev driver first with the Microsoft mouse since the new evdev driver only seems to break with the Logitech MX500. Also, the .Xmodmap file and part of the .xbindkeysrc file (the click part) I have are Logitech MX500 specific.

---

### Post by kaje on 2006-07-05
sigh...

I can't get any of this to work. I have the mx518 mouse. I'm running Ubuntu 6.06 Dapper Drake. I downgrade evdev in the details provided at the beginning of the howto.

My xorg.conf is setup as specified:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/event1"
EndSection
```

cat /proc/bus/input/devices produces the following:

```
I: Bus=0003 Vendor=046d Product=c01e Version=2200
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:02.0-1/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

```

When I restart X, my computer freezes at a black screen with an underscore cursor and I have to reboot the PC.

---

### Post by Sciamano on 2006-07-06
Could someone find the* logitech_applet-0.4test1.tar.gz* file?

When I write this command in the terminal:

```
 wget http://freshmeat.net/redir/logitech_applet/53319/url_tgz/logitech_applet-0.4test1.tar.gz

```

I receive the following:

```
--10:39:12--  http://freshmeat.net/redir/logitech_applet/53319/url_tgz/logitech_applet-0.4test1.tar.gz
           => `logitech_applet-0.4test1.tar.gz'
Resolving freshmeat.net... 66.35.250.168
Connecting to freshmeat.net|66.35.250.168|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://www.frogmouth.net/logitech_applet-0.4test1.tar.gz [following]
--10:39:13--  http://www.frogmouth.net/logitech_applet-0.4test1.tar.gz
           => `logitech_applet-0.4test1.tar.gz'
Resolving www.frogmouth.net... 125.62.93.225
Connecting to www.frogmouth.net|125.62.93.225|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
10:39:15 ERROR 404: Not Found.

```

---

### Post by detyabozhye on 2006-07-06
OK, try this instead:

```
 wget http://detyabozhye.com/other/logitech_applet-0.4test1.tar.gz

```

I put the tar.gz on my site

---

### Post by Sciamano on 2006-07-06
Thanks detyabozhye!

---

### Post by detyabozhye on 2006-07-06
You're welcome ^_^

---

### Post by Znero on 2006-07-07
I've followed the HowTo, now my Side-buttons work in Firefox and Nautilus.

But the "cruise"-feature doesnt work. I guess with cruise you mean when you click with the mousewheel, an round cursor appears and you just have to move your mouse to move around a site, right?

How do i get this Working?

Here are my settings: (I'm using an MX 518 ):

xorg.conf
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mx518"
EndSection
```
xmodmap
```
pointer = 1 3 2 4 5 8 9 6 7 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 
```
xbindkeysrc
```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7
"~/click/click 4"
  m:0x0 + b:11
"~/click/click 5"
  m:0x0 + b:12 
```

And another Question: Any way to use the full 1600 DPI of my mouse?

---

### Post by kaje on 2006-07-07
> **kaje said:**
> sigh...

I can't get any of this to work. I have the mx518 mouse. I'm running Ubuntu 6.06 Dapper Drake. I downgrade evdev in the details provided at the beginning of the howto.

My xorg.conf is setup as specified:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/event1"
EndSection
```

cat /proc/bus/input/devices produces the following:

```
I: Bus=0003 Vendor=046d Product=c01e Version=2200
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:02.0-1/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

```

When I restart X, my computer freezes at a black screen with an underscore cursor and I have to reboot the PC.

Anyone know what's going on here?

---

### Post by detyabozhye on 2006-07-07
> **Znero said:**
> But the "cruise"-feature doesnt work. I guess with cruise you mean when you click with the mousewheel, an round cursor appears and you just have to move your mouse to move around a site, right?

How do i get this Working?

No, cruise control on Logitech mice is those two little buttons abouve and below the scroll wheel that scroll when you hold them. I don't think it is possible to have the round scroll cursor in Linux like in Windows.

> **Znero said:**
> And another Question: Any way to use the full 1600 DPI of my mouse?

I believe you would have to patch logitech_applet or LMCtl and recompile it for that. I haven't tried it though, so I don't know how it would work.

---

### Post by detyabozhye on 2006-07-07
> **kaje said:**
> Anyone know what's going on here?

I believe some people got it to work by specifying only the name like:
```
	Option		"Name"	"Logitech USB-PS/2 Optical Mouse"
```

I haven't gotten it working that way yet, so I don't know if it will work for you or not.

When you restart does the event number stay the same when you do "cat /proc/bus/input/devices"? It changed on my system and that prevented it from starting up.

Other than that, I don't know.

---

### Post by kaje on 2006-07-07
I get a bunch of these errors when I try to load X. I can't see the rest of it because I'm at a command prompt and can't scroll up.

(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument

---

### Post by detyabozhye on 2006-07-07
Hmm, well that got me. I guess you have a Wacom tablet? Maybe there's some interference?

---

### Post by kaje on 2006-07-08
> **detyabozhye said:**
> Hmm, well that got me. I guess you have a Wacom tablet? Maybe there's some interference?

I don't even know what that is.

---

### Post by detyabozhye on 2006-07-08
Did you try udev the way I have it?

---

### Post by kaje on 2006-07-08
> **detyabozhye said:**
> Did you try udev the way I have it?

Yeah and I remember it giving me an error about /input/mx518 not existing.

---

### Post by detyabozhye on 2006-07-08
Beats me, I don't know what else to recommend. -_-

---

### Post by kaje on 2006-07-08
It appears I finally got it working. Thanks detyabozhye!

Quick question.

In your Xmodmap example you had 32 buttons setup.

I kept getting errors to get it down to 9, so I deleted most of the numbers and had:

**"pointer = 1 3 2 4 5 8 9 6 7"**

Then, my scroll wheel (mouse button 3 usually) was acting as my right click, so I switched the 2 and 3 around and now I have:

**"pointer = 1 2 3 4 5 8 9 6 7"**

My question is, does Mouse button 3 (click the scroll wheel straight down) work in Firefox, etc for the automatic scroller function that it does in Windows/Mac OS X? It's not working for me and I'm not sure if my pointer setting is correct. My two side buttons are working correctly, though.

---

### Post by detyabozhye on 2006-07-08
There's a typo in KERNEL there, you have KERN[COLOR="Red"]A[/COLOR]L

---

### Post by kaje on 2006-07-08
> **detyabozhye said:**
> There's a typo in KERNEL there, you have KERN[COLOR="Red"]A[/COLOR]L

Wow..i'm surprised it still worked with that typo. :-k

---

### Post by PingunZ on 2006-07-08
kristof@TuXoR:~$ wget [http://detyabozhye.com/other/xserver-xorg-input-evdev_1.0.0.5-0ubuntu2_i386.deb](http://detyabozhye.com/other/xserver-xorg-input-evdev_1.0.0.5-0ubuntu2_i386.deb)
--10:04:36--  [http://detyabozhye.com/other/xserver-xorg-input-evdev_1.0.0.5-0ubuntu2_i386.deb](http://detyabozhye.com/other/xserver-xorg-input-evdev_1.0.0.5-0ubuntu2_i386.deb)
           => `xserver-xorg-input-evdev_1.0.0.5-0ubuntu2_i386.deb'
Resolving detyabozhye.com... failed: Temporary failure in name resolution.
kristof@TuXoR:~$

---

### Post by HAARP on 2006-07-08
I've followed the Howto. Mouse is working flawlessly, BUT it doesn't work anymore with VMware. When i boot up a machine, I just get the pointer in the middle of the screen. Clicking works alright, but I can't move the pointer at all. I've tried setting the mouse to **/dev/input/duop** (which is my mouse device) with no success.
Any ideas?

---

### Post by detyabozhye on 2006-07-08
> **kaje said:**
> In your Xmodmap example you had 32 buttons setup.

I guess it's just the way it does it with the MX500, it's not supposed to have 32 buttons, but it does. As far as I know, both the MX500 and the MX518 are supposed to have 10 buttons.

> **kaje said:**
> I kept getting errors to get it down to 9, so I deleted most of the numbers and had:

**"pointer = 1 3 2 4 5 8 9 6 7"**

Then, my scroll wheel (mouse button 3 usually) was acting as my right click, so I switched the 2 and 3 around and now I have:

**"pointer = 1 2 3 4 5 8 9 6 7"**

Just another bug, 1 2 3 ... is the correct way, but it swapped right click and middle click on my MX500 so I had to do 1 3 2 ...

> **kaje said:**
> My question is, does Mouse button 3 (click the scroll wheel straight down) work in Firefox, etc for the automatic scroller function that it does in Windows/Mac OS X? It's not working for me and I'm not sure if my pointer setting is correct. My two side buttons are working correctly, though.

AFAIK, that's a Windows/Mac only thing, I've never seen it done on Linux, though I think it could be done.

---

### Post by detyabozhye on 2006-07-08
> **PingunZ said:**
> kristof@TuXoR:~$ wget [http://detyabozhye.com/other/xserver-xorg-input-evdev_1.0.0.5-0ubuntu2_i386.deb](http://detyabozhye.com/other/xserver-xorg-input-evdev_1.0.0.5-0ubuntu2_i386.deb)
--10:04:36--  [http://detyabozhye.com/other/xserver-xorg-input-evdev_1.0.0.5-0ubuntu2_i386.deb](http://detyabozhye.com/other/xserver-xorg-input-evdev_1.0.0.5-0ubuntu2_i386.deb)
           => `xserver-xorg-input-evdev_1.0.0.5-0ubuntu2_i386.deb'
Resolving detyabozhye.com... failed: Temporary failure in name resolution.
kristof@TuXoR:~$

It was a downtime, it's up right now.

---

### Post by detyabozhye on 2006-07-08
> **HAARP said:**
> I've followed the Howto. Mouse is working flawlessly, BUT it doesn't work anymore with VMware. When i boot up a machine, I just get the pointer in the middle of the screen. Clicking works alright, but I can't move the pointer at all. I've tried setting the mouse to **/dev/input/duop** (which is my mouse device) with no success.
Any ideas?

I don't have VMWare, so I don't know.

---

### Post by Znero on 2006-07-09
> **detyabozhye said:**
> No, cruise control on Logitech mice is those two little buttons abouve and below the scroll wheel that scroll when you hold them. I don't think it is possible to have the round scroll cursor in Linux like in Windows.

Okay, but this feature also doesnt work. Xev doesnt recognize the [+] and [-] buttons at my mouse.

---

### Post by kaje on 2006-07-09
Odd..

I installed Ubuntu in a virtual machine using Parallels, and went to setup my mouse in there and can't get the buttons to work.

When running the command cat /proc/bus/input/devices I get

N: Name="ImExPS/2 Generic Explorer Mouse"

as my mouse name instead of the N: Name="Logitech USB-PS/2 Optical Mouse"


So I put KERNEL=="event[0-9]*", SYSFS{../name}=="ImExPS/2 Generic Explorer Mouse", NAME="input/mx518"

in my udev and the extra buttons still don't work. Hmmm

---

### Post by Zym0tiC on 2006-07-09
> **Znero said:**
> Okay, but this feature also doesnt work. Xev doesnt recognize the [+] and [-] buttons at my mouse.

I have the same problem, followed the whole howto (excelent btw!) but the cruiser buttons won't work :(

checked with xev if the button codes are correct and those are.

---

### Post by kaje on 2006-07-09
Hey detyabozhye,

When I go into xev and test my buttons with my mx518, my Scroll Up and two side buttons are both being registered as button 4. What's up with this?

---

### Post by detyabozhye on 2006-07-09
> **Znero said:**
> Okay, but this feature also doesnt work. Xev doesnt recognize the [+] and [-] buttons at my mouse.

Does it react to them when xbindkeys is off and without xmodmap modifying the numbers?
(temporarily rename ~/.Xmodmap to ~/.Xmodmap-bak, restart X, killall xbindkeys, then try xev)

---

### Post by detyabozhye on 2006-07-09
To the MX518 users, it seems to me that MX518 acts different from the MX500. Can you guys tell me what the button numbers for all the buttons are in xev without xmodmap and xbindkeys?
```
~$ mv .Xmodmap .Xmodmap-bak
```
restart X

If xbindkeys is running:
```
killall xbindkeys
```
```
xev
```

---

### Post by Znero on 2006-07-09
> To the MX518 users, it seems to me that MX518 acts different from the MX500. Can you guys tell me what the button numbers for all the buttons are in xev without xmodmap and xbindkeys?

Left mousebutton:
button 1
Right mousebutton:
button 3
Wheel click:
button 2
Wheel forward:
button 4
Wheel backward:
button 5
[+]:
-nothing happens-
[-]:
-nothing happens-
Sidekey forward:
button 9
Sidekey backward:
button 8
Tab-key:
button 10

---

### Post by kaje on 2006-07-09
> **detyabozhye said:**
> To the MX518 users, it seems to me that MX518 acts different from the MX500. Can you guys tell me what the button numbers for all the buttons are in xev without xmodmap and xbindkeys?


In parallels:


Left mousebutton:
button 1
Right mousebutton:
button 3
Wheel click:
button 2
Wheel forward:
button 4
Wheel backward:
button 5
[+]:
-nothing happens-
[-]:
-nothing happens-
[B]Sidekey forward:
button 4
Sidekey backward:
button 4[/B]
Tab-key:
-nothing happens-


In the bold is where my problem is occurring, but don't know if the problem is with Parallels or with my Xorg.conf.

---

### Post by detyabozhye on 2006-07-09
OK, what happens if you try the same thing using the latest evdev driver in the repository? Some people said it worked with their mouse. It seems to be an MX500 specific problem that I have.

WARNING: Keep the old driver somewhere where you will remember where it is in case X doesn't start up, such as you home folder, so you can type sudo dpkg -i xserver-[tab key] in the commaind line if X dosn't start up.

---

### Post by detyabozhye on 2006-07-09
Another note for the MX518 users: The + and - buttons above and below the scroll wheel are not cruise control buttons on the MX518, only on the MX500 and MX510 (maybe others too, I don't know). On the MX518, they control the sensativity of the mouse, maybe through the computer, maybe not, I don't know for sure. Even if you would be able to make them be cruise control buttons, they probably won't send a repeated signal and therefore wouldn't be "cruising".

---

### Post by kaje on 2006-07-09
> **detyabozhye said:**
> OK, what happens if you try the same thing using the latest evdev driver in the repository? Some people said it worked with their mouse. It seems to be an MX500 specific problem that I have.

WARNING: Keep the old driver somewhere where you will remember where it is in case X doesn't start up, such as you home folder, so you can type sudo dpkg -i xserver-[tab key] in the commaind line if X dosn't start up.

With updated evdev, both side buttons continue being button 4. I think it's a parallel problem. Can't get much information on it though because their forums are dead.

---

### Post by Eugene Seppel on 2006-07-12
Thank you, detyabozhye, all works on MX510!
But why we should use xserver-xorg-input-evdev_1.0.0.5-0ubuntu2 ?
Is it bug and was it submitted to Ubuntu bug tracking system?
Having locked packages is inconveniently...:(

---

### Post by FrancoNero on 2006-07-12
looking at the very first post of this topic, there's another entry on people's "why I don't  switch to Linux" list ;-) the magic word is: GUI

---

### Post by gurgle on 2006-07-12
^^ touche. i wish there was something similar to uberoptions on the pc, where you can configure every mouse button to a keystroke, etc.

---

### Post by detyabozhye on 2006-07-12
> **Eugene Seppel said:**
> Thank you, detyabozhye, all works on MX510!
But why we should use xserver-xorg-input-evdev_1.0.0.5-0ubuntu2 ?
Is it bug and was it submitted to Ubuntu bug tracking system?
Having locked packages is inconveniently...:(

Yes, it is a bug and is submitted to the bug tracking system, but so far the bug hasn't been fixed. [bug # 43100](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-input-evdev/+bug/43100)

---

### Post by detyabozhye on 2006-07-12
> **FrancoNero said:**
> looking at the very first post of this topic, there's another entry on people's "why I don't  switch to Linux" list ;-) the magic word is: GUI

What do u mean? The terminal in Accessories->Terminal is a GUI app! LOL

---

### Post by detyabozhye on 2006-07-12
> **gurgle said:**
> ^^ touche. i wish there was something similar to uberoptions on the pc, where you can configure every mouse button to a keystroke, etc.

What do you mean by "on the pc"? PC is hardware, Windows and Linux are software. I don't know about Windows, but on Linux you can use xbindkeys and xvkbd to achieve that.

---

### Post by basementjack on 2006-07-12
I do not know why, but after a couple of reboots where I didn't change any configurations, it just starting working.
So with the guide, I got these working:
 - MX700 mouse with nVidia 440MX gfxcard.
 - MX500 mouse with Ati Radon R250 gfxcard.

---

### Post by FrancoNero on 2006-07-12
> **detyabozhye said:**
> What do u mean? The terminal in Accessories->Terminal is a GUI app! LOL

nice attitute for promoting linux ;-)) *lol*

some people might feel a little too stoneage  if they are asked to use a "text console"

---

### Post by kaje on 2006-07-12
I think he means that one of the downsides to linux is there aren't many apps for setting things up where you check checkboxes, click mouse to bind, etc. You have to know all the commands and what values to give to those commands (sometimes by having to know and perform other commands) to achieve certain functions.

---

### Post by wieman01 on 2006-07-12
Hey Guys, 

I don't want to beat a dead horse but I have issues with my MX700 which is sharing the receiver with a wireless (Logitech) keyboard. 

Would anybody mind posting his/her "Xmodmap" and "xorg.conf" file for my reference? Perhaps I have missed something here.

I was following this howto but my mouse would go crazy and show erratic behavior every time I log on to my system (Dapper 6.06, KDE v3.5). I am seriously running out of ideas...

---

### Post by detyabozhye on 2006-07-12
> **kaje said:**
> I think he means that one of the downsides to linux is there aren't many apps for setting things up where you check checkboxes, click mouse to bind, etc. You have to know all the commands and what values to give to those commands (sometimes by having to know and perform other commands) to achieve certain functions.

Not to worry, GUI Xorg configuration tools are on their way.

---

### Post by detyabozhye on 2006-07-12
> **wieman01 said:**
> Hey Guys, 

I don't want to beat a dead horse but I have issues with my MX700 which is sharing the receiver with a wireless (Logitech) keyboard. 

Would anybody mind posting his/her "Xmodmap" and "xorg.conf" file for my reference? Perhaps I have missed something here.

I was following this howto but my mouse would go crazy and show erratic behaviour every time I log on to my system (Dapper 6.06, KDE v3.5). I am seriously running out of ideas...

I believe someone got this working by using the "Name" Option in Xorg.conf, but I'm not sure and can't test it because all I have is an MX500.

---

### Post by wieman01 on 2006-07-12
> **detyabozhye said:**
> I believe someone got this working by using the "Name" Option in Xorg.conf, but I'm not sure and can't test it because all I have is an MX500.

Yes, I tried the name option as well, but the mouse would only work fine within the first few minutes after startup. Then then same problem would occur (erratic mouse behavior).

---

### Post by Xecuter on 2006-07-13
Great howto! I've allmost got it working on my mx700. 

First: After restarting X i got this error: [http://ubuntuforums.org/showpost.php?p=1100399&postcount=4](http://ubuntuforums.org/showpost.php?p=1100399&postcount=4)
I simply restarted my computer and then the sidebuttons worked. In firefox that is.

So I continued.

After completing and restarting the sidebuttons don't work at all.
xev output:
```
LeaveNotify event, serial 29, synthetic NO, window 0x2e00001,
    root 0x75, subw 0x0, time 1743615784, (97,105), root:(112,207),
    mode NotifyGrab, detail NotifyAncestor, same_screen YES,
    focus NO, state 16

EnterNotify event, serial 29, synthetic NO, window 0x2e00001,
    root 0x75, subw 0x0, time 1743615919, (97,105), root:(112,207),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
    focus NO, state 16

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  117 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

```

Need a litle help.


At last. The mx700 has got a button on top wich is supposed to work as ALT+TAB, but currently works at button 1. xev shows it as button 10.

---

### Post by detyabozhye on 2006-07-13
> **Xecuter said:**
> Great howto! I've allmost got it working on my mx700. 

First: After restarting X i got this error: [http://ubuntuforums.org/showpost.php?p=1100399&postcount=4](http://ubuntuforums.org/showpost.php?p=1100399&postcount=4)
I simply restarted my computer and then the sidebuttons worked. In firefox that is.

So I continued.

After completing and restarting the sidebuttons don't work at all.
xev output:
```
LeaveNotify event, serial 29, synthetic NO, window 0x2e00001,
    root 0x75, subw 0x0, time 1743615784, (97,105), root:(112,207),
    mode NotifyGrab, detail NotifyAncestor, same_screen YES,
    focus NO, state 16

EnterNotify event, serial 29, synthetic NO, window 0x2e00001,
    root 0x75, subw 0x0, time 1743615919, (97,105), root:(112,207),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
    focus NO, state 16

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  117 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

```

Need a litle help.

So, I don't really understand whether you got this working or not. If you don't have it working, what does your ~/.xbindkeysrc file look like?

> **Xecuter said:**
> At last. The mx700 has got a button on top wich is supposed to work as ALT+TAB, but currently works at button 1. xev shows it as button 10.

At the moment, there are no Linux apps that I know of that would do the ALT+TAB the way button 10 does in Windows. You can't make it just do plain ALT+TAB because it would press and release, you would need an app that would continue staying up after release. If you run Compiz, you can map it to do the Expose thing. Right now, I have my button 10 mapped to F5 to reload web pages.

---

### Post by wieman01 on 2006-07-13
> **Xecuter said:**
> Great howto! I've allmost got it working on my mx700.

Xecuter, 

Would you mind sharing your "xorg.conf", "Xmodmap", and "udev" with us so that I can figure out what wrong with my settings? 

I have a wireless keyboard together with a MX700 mouse sharing the receiver.

Thanks in advance.

---

### Post by Xecuter on 2006-07-14
> **wieman01 said:**
> Xecuter, 

Would you mind sharing your "xorg.conf", "Xmodmap", and "udev" with us so that I can figure out what wrong with my settings? 

I have a wireless keyboard together with a MX700 mouse sharing the receiver.

Thanks in advance.

This is just the mouse part. I do not share a keyboard at the same receiver so it migth not help. But anyways:
Xorg.conf
```
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"		"/dev/input/mice"
#	Option		"Protocol"		"ExplorerPS/2"
#	Option		"ZAxisMapping"		"4 5"
#EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"[CODE]
```
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mx700"
EndSection[/CODE]

Xmodmap
```
pointer = 1 3 2 4 5 8 9 6 7 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32
```

Udev
```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", NAME="input/mx700"
```


> So, I don't really understand whether you got this working or not. If you don't have it working, what does your ~/.xbindkeysrc file look like?And I qoute myself:> After completing and restarting the sidebuttons don't work at all.

xbindkeysrc
```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
  m:0x0 + b:7

"~/click/click 4"
  m:0x0 + b:11
"~/click/click 5"
  m:0x0 + b:12

```

> At the moment, there are no Linux apps that I know of that would do the ALT+TAB the way button 10 does in Windows. You can't make it just do plain ALT+TAB because it would press and release, you would need an app that would continue staying up after release. If you run Compiz, you can map it to do the Expose thing. Right now, I have my button 10 mapped to F5 to reload web pages.
Yes, I know that there's a buttonPress and buttoRelease:
buttonPress = ALT+TAB press
buttonRelease = ALT+TAB release
And you would choose between apps with the scrollwheel.
Get it?

---

### Post by wieman01 on 2006-07-14
Thank you. This is very nice. I will try it when I am back home.

---

### Post by rejser on 2006-07-14
Strange, I get a message that something else is using those buttons (they get recognized in xev). I've killed off all things that could interfere with the mouse but still!
Any tips?

---

### Post by detyabozhye on 2006-07-14
> **Xecuter said:**
> xbindkeysrc
```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
  m:0x0 + b:7

"~/click/click 4"
  m:0x0 + b:11
"~/click/click 5"
  m:0x0 + b:12

```

I assume you capitalized "Left" and "Right" in your file? Other than that, it looks fine to me.

> **Xecuter said:**
> Yes, I know that there's a buttonPress and buttoRelease:
buttonPress = ALT+TAB press
buttonRelease = ALT+TAB release
And you would choose between apps with the scrollwheel.
Get it?

Theoretically, that sounds good, but in reality the ALT+TAB list doesn't work that way AFAIK. You would need to build a custom ALT+TAB replacement application for that.

---

### Post by detyabozhye on 2006-07-14
> **rejser said:**
> Strange, I get a message that something else is using those buttons (they get recognized in xev). I've killed off all things that could interfere with the mouse but still!
Any tips?

Can you post the error message here?

---

### Post by Xecuter on 2006-07-14
> **detyabozhye said:**
> I assume you capitalized "Left" and "Right" in your file? Other than that, it looks fine to me.


Oh! It works! :D Thanks man!!

---

### Post by rejser on 2006-07-14
> **detyabozhye said:**
> Can you post the error message here?

There isn't any real error message, only says, "the button is already in use by another software"

---

### Post by detyabozhye on 2006-07-14
> **Xecuter said:**
> Oh! It works! :D Thanks man!!

You're welcome.

---

### Post by detyabozhye on 2006-07-14
> **rejser said:**
> There isn't any real error message, only says, "the button is already in use by another software"

Hmm, that's really weird.

---

### Post by wieman01 on 2006-07-15
Hi, 

I got my mouse working (Cordless MX Duo with MX700 Mouse) but after a few minutes working with it, the mouse wheel would go crazy and go up & down erratically so that I have to restart my computer. 

Has anybody experienced the same thing? I am thinking of replacing my keyboard & mouse now... It worked fine under Windows.

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
    	Identifier      "Configured Mouse"
    	Driver          "evdev"
	Option          "CorePointer"
	Option          "Dev Name"             "Logitech USB Receiver"
	Option          "Dev Phys"             "usb-*/input1"
	Option          "Device"               "/dev/input/mx700"
	Option          "Protocol"             "evdev"
EndSection

Help is highly appreciated. Thanks.

---

### Post by ATT-Half on 2006-07-15
> 
_1.1 Fixing the cruise control buttons_

Install these three packages for "click" to compile:
```
libx11-dev
x11proto-xext-dev
libxtst-dev
```

Download this file: [http://bg.rifetech.com/click.tgz](http://bg.rifetech.com/click.tgz)
untar it to ~/click (or wherever you want, just remember the dir, you'll need it in the .xbindkeysrc)
then compile it:

```
cd ~/click
make
```

Then add this to you .xbindkeysrc

```
"~/click/click 4"
  m:0x0 + b:11
"~/click/click 5"
  m:0x0 + b:12
```

_2. Adding it to your session_

Now it's working open up the gnome sessions settings "System > Preferences > Sessions" click on the "Startup Programs" tab, click "Add" and enter "xbindkeys". This makes sure it's run each time you log in, you should probably test it by logging out and back in now. If you aren't running GNOME, you will need to do it another way, e.g. in XFCE, go to Xfce Menu -> Settings -> Autostarted Applications. (I haven't tried it, but that should be where to go in XFCE)
[/INDENT] **_Section 3: The logitech_applet_**[INDENT]


hi i'm stuck in this spot i got those 3 install but how do i compile what's the command?
libx11-dev
x11proto-xext-dev
libxtst-dev

click is /home dir like you suggested
when i type in terminal
cd ~/click ternial turn to this 
halfgimp@halfgimp-desktop:~/click$
then i type: make =
 bash: make: command not found
also tried combining:
 make libx11-dev and  make x11proto-xext-dev i'm lost here ](*,) 

been trying to figure out this like crazy i only been using linux for 4 days :p

---

### Post by ATT-Half on 2006-07-15
nevermind i think it work i skip to Section 3: The logitech_applet and then when back now it work :-?

---

### Post by detyabozhye on 2006-07-15
> **ATT-Half said:**
> hi i'm stuck in this spot i got those 3 install but how do i compile what's the command?
libx11-dev
x11proto-xext-dev
libxtst-dev

click is /home dir like you suggested
when i type in terminal
cd ~/click ternial turn to this 
halfgimp@halfgimp-desktop:~/click$
then i type: make =
 bash: make: command not found
also tried combining:
 make libx11-dev and  make x11proto-xext-dev i'm lost here ](*,) 

been trying to figure out this like crazy i only been using linux for 4 days :p

You need to install the automake stuff for compiling, for which I don't remember the exact package names.

---

### Post by ATT-Half on 2006-07-15
thx detyabozhye you comfirm my worst fear that it did not do anything when i put in the command.

anyone here remember automake thingy i need :-k [-o<  

if i search Sysnaptic Package Manager for automake the only thing i got install from that section is **[COLOR="DarkSlateBlue"]pkg-config install version 0.20-1[/COLOR]**  anyone???.
i see on the list bunch of automake1.4 - 1.9 and other stuff not sure what should i get ?

this should also be added to the quide by the way.

---

### Post by detyabozhye on 2006-07-15
I have 1.4 and 1.9 installed.

---

### Post by ATT-Half on 2006-07-15
> **detyabozhye said:**
> I have 1.4 and 1.9 installed.

nope that's not it still getting 
bash: make: command not found

---

### Post by detyabozhye on 2006-07-15
I think I remember now, you need to install build-essential.

---

### Post by ATT-Half on 2006-07-15
> **detyabozhye said:**
> I think I remember now, you need to install build-essential.


is this the right output that should happen?

halfgimp@Halfgimp-desktop:~$ cd ~/click
halfgimp@Halfgimp-desktop:~/click$ make
gcc -Wall -c -o click.o click.c
gcc -Wall -o click click.o -L /usr/X11R6/lib/ -lX11 -lXtst
halfgimp@Halfgimp-desktop:~/click$

:-D 
if it is thank you so much and make sure to add to quide 
for all future nooblet :rolleyes:

---

### Post by detyabozhye on 2006-07-15
> **ATT-Half said:**
> is this the right output that should happen?

halfgimp@Halfgimp-desktop:~$ cd ~/click
halfgimp@Halfgimp-desktop:~/click$ make
gcc -Wall -c -o click.o click.c
gcc -Wall -o click click.o -L /usr/X11R6/lib/ -lX11 -lXtst
halfgimp@Halfgimp-desktop:~/click$

:-D 
if it is thank you so much and make sure to add to quide 
for all future nooblet :rolleyes:

Yeah, that's what's supposed to happen. K, I'll add it.

---

### Post by SaxmanTy on 2006-07-15
Hey guys
I had the side buttons working fine on my mx700. Actually, for some reason, i never had to run xvkbd and xbindkeys, and the side buttons worked perfect in Nautilus and Firefox.  But anyway, after installing Xgl and Compiz the side buttons stopped working.  I ran the comand ```
xmodmap ~/.Xmodmap
``` and I get and error > bad number of buttons, must have 7 instead of 32
 Can someone who is using Xgl post what their Xmodmap file lookes like for the mx700.  I know I need seven numbers, but which seven and in what order?

---

### Post by wieman01 on 2006-07-16
> **SaxmanTy said:**
> Hey guys
I had the side buttons working fine on my mx700. Actually, for some reason, i never had to run xvkbd and xbindkeys, and the side buttons worked perfect in Nautilus and Firefox.  But anyway, after installing Xgl and Compiz the side buttons stopped working.  I ran the comand ```
xmodmap ~/.Xmodmap
``` and I get and error  Can someone who is using Xgl post what their Xmodmap file lookes like for the mx700.  I know I need seven numbers, but which seven and in what order?

The number has changed to 32 after installing Xgl, etc. in my case as well. So you will have to change your .Xmodmap settings accordingly. On page 14 of this thread is an example for the MX700. This will help.

---

### Post by wieman01 on 2006-07-16
Mouse showing erratic behavior:

Obviously this happens when you configure xmodmap incorrectly (to answer my own question)... So the right settings for MX700 in connection with the "Cordless MX Duo" are (after defining a "udev" rule as described in this howto):

**_xorg.conf:_**
> Section "InputDevice"
    	Identifier      "Configured Mouse"
    	Driver          "evdev"
	Option          "CorePointer"
	Option          "Dev Name"		"Logitech USB Receiver"
	Option          "Dev Phys"             	"usb-*/input1"
	Option          "Device"               	"/dev/input/mx700"
EndSection

**_.Xmodmap:_**

> pointer = 1 3 2 4 5 8 9 6 7 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32

Sidebuttons and mousewheel work like a charm now.

---

### Post by zergberg on 2006-07-16
Ok, my MX700 now works _almost_ perfectly, however...

My Cruise Control buttons "work" per se, but not as I'd like. Instead of cruise scrolling, they slowly inch down the screen--and only if pressed repeatedly. Anyone know how to fix this?

Also, a somewhat more grave problem: making my mouse function properly has somehow made it so the extra keys on my Logitech Cordless Elite do not function at all--nothing in xev at all, though they do work fine if I switch back to the regular mouse entry in xorg.conf Personally, I'd kinda like at least my media keys back, though the remainder of the extra keys would be nice too. How do I get them back?

Two more small things:
- it should be added that you need to log out and back in (or something) to get the udev rule to work. This confused me for a good long while.
- my xfce Autostarted Applications doesn't seem to do, well, anything. Odd.

---

### Post by xtek on 2006-07-17
Very nice guide that you put up here, it helped me get my mouse working to my liking.  There is however a problem, and I will try to explain as best I can with my limited knowledge of linux.

I have 2 machines here (1 windows, 1 linux) that I use a KVM with.  Everything works in linux up untill the point when I switch to the windows box using the KVM.  Once I go back to linux I find the mouse isn't working.  I have done some searching on the web/forum about the problem but there dosen't seem to be a fix for it anywhere.  I did some investigating trying to figure out what went wrong, and I noticed something.  When I check to see if the device changed I find this.
[B]
Before:[/B]

```

cat /proc/bus/imput/devices

I: Bus=0003 Vendor=046d Product=c01e Version=2200
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:02.0-2.1.2/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse1 event4 ts1
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

```

**After:**

```

cat /proc/bus/input/devices

I: Bus=0003 Vendor=046d Product=c01e Version=2200
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:02.0-2.1.2/input0
S: Sysfs=/class/input/input6
H: Handlers=mouse1 event4 ts1
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

```

You will notice that the line **"S: Sysfs=/class/input/input1"** changed to **"S: Sysfs=/class/input/input6"**.

It appears that it has changed the input value when it redetects the mouse making it act like a different device.  I have been able to get this to work by killing X and restarting it making thus allowing it find the mouse again using the current value.

My question is this:  Is there a way to create a cron like job that will poll for the information and automatically update it as needed?

---

### Post by deepspring on 2006-07-17
Works well with my G5 Laser. :twisted:

--snip--
 
**Final Edit (I promise!):**

Still can't get button 8 to work (thumb button). ](*,) 

Other than that everything else works perfectly.

If anyone else has a G5 laser mouse like me, just skip the .Xmodmap part of the main tutorial. If you have already done the .Xmodmap part just rename file.

If you followed the guide properly, you're G5 should be setup like:

Left Button => Normal
Right Mouse Button => Normal
Pressing the Scroll Down => Middle Click
Pressing the Scroll Wheel Left / Right => Forward / Back (Nautilus/FF)
Forward / Back Scroll => 3 Lines Up / Down

---

### Post by detyabozhye on 2006-07-17
> **zergberg said:**
> Ok, my MX700 now works _almost_ perfectly, however...

[QUOTE=zergberg;1261557]My Cruise Control buttons "work" per se, but not as I'd like. Instead of cruise scrolling, they slowly inch down the screen--and only if pressed repeatedly. Anyone know how to fix this?

Seems like cruising is turned off in the mouse, you'll need to turn it on with [LMCtl](http://www.bedroomlan.org/~alexios/coding_lmctl.html)

> **zergberg said:**
> Also, a somewhat more grave problem: making my mouse function properly has somehow made it so the extra keys on my Logitech Cordless Elite do not function at all--nothing in xev at all, though they do work fine if I switch back to the regular mouse entry in xorg.conf Personally, I'd kinda like at least my media keys back, though the remainder of the extra keys would be nice too. How do I get them back?

Hmm, I never used my media keys, but when I tried, my media keys didn't do anything in xev either on my Compaq keyboard.

> **zergberg said:**
> Two more small things:
- it should be added that you need to log out and back in (or something) to get the udev rule to work. This confused me for a good long while.
- my xfce Autostarted Applications doesn't seem to do, well, anything. Odd.

Basically, you need to log out and hit ALT+CTRL+Backspace to restart X and then log back in.

---

### Post by detyabozhye on 2006-07-17
> **xtek said:**
> Very nice guide that you put up here, it helped me get my mouse working to my liking.  There is however a problem, and I will try to explain as best I can with my limited knowledge of linux.

I have 2 machines here (1 windows, 1 linux) that I use a KVM with.  Everything works in linux up untill the point when I switch to the windows box using the KVM.  Once I go back to linux I find the mouse isn't working.  I have done some searching on the web/forum about the problem but there dosen't seem to be a fix for it anywhere.  I did some investigating trying to figure out what went wrong, and I noticed something.  When I check to see if the device changed I find this.
[B]
Before:[/B]

```

cat /proc/bus/imput/devices

I: Bus=0003 Vendor=046d Product=c01e Version=2200
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:02.0-2.1.2/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse1 event4 ts1
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

```

**After:**

```

cat /proc/bus/input/devices

I: Bus=0003 Vendor=046d Product=c01e Version=2200
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:02.0-2.1.2/input0
S: Sysfs=/class/input/input6
H: Handlers=mouse1 event4 ts1
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

```

You will notice that the line **"S: Sysfs=/class/input/input1"** changed to **"S: Sysfs=/class/input/input6"**.

It appears that it has changed the input value when it redetects the mouse making it act like a different device.  I have been able to get this to work by killing X and restarting it making thus allowing it find the mouse again using the current value.

My question is this:  Is there a way to create a cron like job that will poll for the information and automatically update it as needed?

Hmm, I don't know, it may or may not be possible, it should be, but I'm not sure how. Unhooking and hooking the mouse back up has caused some trouble for people before.

---

### Post by detyabozhye on 2006-07-17
> **deepspring said:**
> Works well with my G5 Laser. :twisted:

--snip--
 
**Final Edit (I promise!):**

Still can't get button 8 to work (thumb button). ](*,) 

Other than that everything else works perfectly.

If anyone else has a G5 laser mouse like me, just skip the .Xmodmap part of the main tutorial. If you have already done the .Xmodmap part just rename file.

If you followed the guide properly, you're G5 should be setup like:

Left Button => Normal
Right Mouse Button => Normal
Pressing the Scroll Down => Middle Click
Pressing the Scroll Wheel Left / Right => Forward / Back (Nautilus/FF)
Forward / Back Scroll => 3 Lines Up / Down

Can I get the xev output for your buttons?

Pressing the scroll wheel left and right should scroll horrizontaly. The correct button events for that are 6 and 7. The problem is that some browsers (eg. Firefox, Opera) do back and forward for 6 and 7. 8 and 9 should be back and forward in browsers, file managers, etc. Basically, it's a bit messy at the moment.

Edit: Actually, all GTK+ and QT applications do scroll horizontaly for button 6 and 7. As for Firefox, it's not a true GTK+ application and Opera overrides button 6 and 7 when it is possible to go back or forward.

---

### Post by deepspring on 2006-07-17
> **detyabozhye said:**
> Can I get the xev output for your buttons?

Yeah no problem.

xev output (minus the crap):
```

ButtonRelease event, serial 28, synthetic NO, window 0x1800001,
    root 0x52, subw 0x0, time 2133896483, (81,25), root:(89,436),
    state 0x110, button 1, same_screen YES

ButtonPress event, serial 28, synthetic NO, window 0x1800001,
    root 0x52, subw 0x0, time 2133898691, (81,25), root:(89,436),
    state 0x10, button 2, same_screen YES

ButtonRelease event, serial 28, synthetic NO, window 0x1800001,
    root 0x52, subw 0x0, time 2133899759, (81,25), root:(89,436),
    state 0x410, button 3, same_screen YES

ButtonPress event, serial 28, synthetic NO, window 0x1800001,
    root 0x52, subw 0x0, time 2133904196, (81,25), root:(89,436),
    state 0x10, button 4, same_screen YES

ButtonRelease event, serial 28, synthetic NO, window 0x1800001,
    root 0x52, subw 0x0, time 2133905102, (81,25), root:(89,436),
    state 0x1010, button 5, same_screen YES

ButtonRelease event, serial 28, synthetic NO, window 0x1800001,
    root 0x52, subw 0x0, time 2133910494, (81,25), root:(89,436),
    state 0x10, button 6, same_screen YES

ButtonPress event, serial 28, synthetic NO, window 0x1800001,
    root 0x52, subw 0x0, time 2133911471, (81,25), root:(89,436),
    state 0x10, button 7, same_screen YES

ButtonRelease event, serial 28, synthetic NO, window 0x1800001,
    root 0x52, subw 0x0, time 2133873552, (86,25), root:(94,436),
    state 0x10, button 8, same_screen YES

```

Button 1 is the left mouse button.

Button 2 is the Middle Button (pressing the mouse wheel in).

Button 3 is the right mouse button.

Buttons 4 and 5 is moving the mouse wheel forward and back.

Buttons 6 and 7 is pressing the mouse wheel left and right.

Button 8 is the thumb button.

.xbindkeys file:
```

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[**L**eft]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[**R**ight]""
  m:0x0 + b:7

```

/etc/X11/xorg.conf file:
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/g5laser"
EndSection

```

/etc/udev/rule.d/19-local.rules file:
```

KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Gaming Mouse", NAME="input/g5laser"

```

I removed the .Xmodmap file, because I found that it didn't matter what order I set the buttons to in it I would end up with:
-- Pressing Mouse Wheel Down => Right Click
-- Pressing Right Mouse Button => Middle Click

After removing the custom .Xmodmap, everything started working properly.

I just can't seem to bind Button 8 to anything.

---

### Post by detyabozhye on 2006-07-17
OK, change the .xbindkeys file to:
```

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[**L**eft]""
  m:0x0 + b:8

```

This will make the side button do back. Button 6 and 7 (tilt wheel) are for horizontal scrolling, you'll need to change some Firefox config to make it do what it should in Firefox. Regular GTK+ and QT apps already know what to do with 6 and 7.

---

### Post by deepspring on 2006-07-17
> **detyabozhye said:**
> OK, change the .xbindkeys file to:
```

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[**L**eft]""
  m:0x0 + b:8

```

This will make the side button do back. Button 6 and 7 (tilt wheel) are for horizontal scrolling, you'll need to change some Firefox config to make it do what it should in Firefox. Inscape, GIMP, and a handful of apps already know what to do with 6 and 7.

Cheers! works great.

Still trying to figure out firefox's issues.

---

### Post by detyabozhye on 2006-07-17
> **deepspring said:**
> Cheers! works great.

Still trying to figure out firefox's issues.

Set:
mousewheel.horizscroll.withnokey.action to 0
mousewheel.horizscroll.withnokey.numlines to 2

---

### Post by deepspring on 2006-07-17
> **detyabozhye said:**
> Set:
mousewheel.horizscroll.withnokey.action to 0
mousewheel.horizscroll.withnokey.numlines to 2

Thanks mate, works brilliantly :KS

---

### Post by detyabozhye on 2006-07-17
Doitashimashite (you're welcome)! ^_^

---

### Post by zergberg on 2006-07-18
lmctl only gives me 002.002: 046d:c50b Unknown or Unsupported Logitech device, presumably because I have an MX700, and it's actually a "Logitech USB Receiver." Cruise still doesn't work.

Does anyone have a workaround (or at least an explanation) for the "No Media Keys" problem I mentioned earlier?

---

### Post by detyabozhye on 2006-07-19
**[SIZE="5"][COLOR="DarkRed"]I've figured out a way to get the current evdev working with the MX500, but it will require a lot of changes here. Should I edit this guide for the current evdev, or should I leave this one and create a new guide?[/COLOR][/SIZE]**

---

### Post by detyabozhye on 2006-07-19
> **zergberg said:**
> Does anyone have a workaround (or at least an explanation) for the "No Media Keys" problem I mentioned earlier?

I might have a solution to this problem, but I need to test it first.

---

### Post by Poka64 on 2006-07-20
> I've figured out a way to get the current evdev working with the MX500, but it will require a lot of changes here. Should I edit this guide for the current evdev, or should I leave this one and create a new guide?

Create a new guide.

---

### Post by detyabozhye on 2006-07-20
K, made a new guide, it's not up yet though.

---

### Post by detyabozhye on 2006-07-21
K, new guide is here: [http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894)

---

### Post by geezerone on 2006-11-01
I have MX510 and find that the side buttons perform scroll up/dwn? help plz:)

---

### Post by detyabozhye on 2006-11-01
um, do you have xmodmap set up? If so, what's your .Xmodmap file look like?

---

### Post by geezerone on 2006-11-16
Which xmodmap file as there are loads?

thanks

---

### Post by detyabozhye on 2006-11-16
The file is ~/.Xmodmap (~/ means your home directory, .Xmodmap has a dot in front of it to make it a hidden file, and remember that Linux file names are case sensetive).

Check in Synaptic if xmodmap is installed and run gedit ~/.Xmodmap to see the xmodmap file.

---

### Post by r!ots on 2006-11-22
does this still work in edgy?

i remember last time i upgraded (from breezy to dapper) the evdev was broken and therefore i didn't have a working X-server. it took me a while to figure out the problem and i would like to upgrade ubuntu flawlessly this time.
has anyone tried it yet?

---

### Post by detyabozhye on 2006-11-23
Um, you can try the method in my sig on Edgy, although I use some modifications on it too.

---

### Post by greppi on 2007-08-02
I have a problem ... when I bind:
```

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[F4]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Control]\[w]""
  m:0x0 + b:7

```

and when I click on side button ( MX 518 ),_ speaker on PC make a voice_ (it takes about 50 miliseconds), and after that window close (CRTL+W) ...
Why speaker make a voice ?

---

### Post by detyabozhye on 2007-08-04
Maybe you have a sound set on closing a window. Other than that, I can't think of another reason why it would do that. Or are you talking about the system speaker that does nothing but beep?

---

