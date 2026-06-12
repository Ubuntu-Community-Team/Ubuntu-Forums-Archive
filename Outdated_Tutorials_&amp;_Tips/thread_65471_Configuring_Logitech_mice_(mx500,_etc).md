---
title: "Configuring Logitech mice (mx500, etc)"
date: 2005-09-14
forum: Outdated Tutorials &amp; Tips
---

### Post by endy on 2005-09-14
_**A complete guide to a Logitech mouse**_

This is my guide on how to get all the buttons working properly on a logitech mouse, how to use the "logitech_applet" to enable the higher resolutions and cruise control and how to get the side mouse buttons to make forwards and back work in Nautilus and Epiphany. 

This works for my mx510, I assume it would work for the similar mx500 and mx518 and the wireless versions like the mx700 however, I haven't got all those mice so I'd appreciate it if anyone get them working to post a reply and I'll make a list of what works.


_**Section 1: Getting your mouse working on USB with evdev**_[INDENT]
I once had my mouse plugged in via the PS/2 connector and used the "ExporerPS/2" protocol in my xorg.conf file, this generally worked but the little scroll up button would also make Firefox go back a page. This is not a bug this is because the "ExporerPS/2" is made for Microsoft mice not Logitech. So what can we do about it? Well first off you need to plug your mouse into a USB port, you can't do anything else in this how to until you do that. I have unplugged my mouse from the PS/2 port and plugged it into a USB port while logged into my desktop and it worked fine so go ahead and do that now.


_1. Getting all the information you need_

Great, so we're all plugged in via USB and ready to go. Before we change anything we need to get some important information about the mouse so run the following command in your favourite terminal:

```
cat /proc/bus/input/devices
``` You should get a list of details, here's what I get and I'll highlight the bit we need to concentrate on:

```
endy@ananke:~$ cat /proc/bus/input/devices
I: Bus=0003 Vendor=046a Product=0023 Version=0027
N: Name="046a:0023"
P: Phys=usb-0000:00:02.0-7/input0
H: Handlers=kbd event0
B: EV=120003
B: KEY=7 ff800000 7ff e0b2ffdf 1cfffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046a Product=0023 Version=0027
N: Name="046a:0023"
P: Phys=usb-0000:00:02.0-7/input1
H: Handlers=kbd event1
B: EV=f
B: KEY=1 0 38000 39fa d841d7a9 9e0000 0 0 0
B: REL=40
B: ABS=ffffff01 0

[B]I: Bus=0003 Vendor=046d Product=c01d Version=2100
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:02.0-8/input0
H: Handlers=mouse0 event2 ts0
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103[/B]

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
H: Handlers=kbd event3
B: EV=40001
B: SND=6
``` We know this is the correct bit because the name "Logitech USB-PS/2 Optical Mouse". Your output will be different but the bit I've highlighted is all we need.

*Note: For mx700 users the mouse name is "Logitech USB Receiver", thanks to everyone for the info!*

_2. Editing the xorg.conf file_

Now we have the information we need to start to set up xorg. So open up your xorg.conf file in your favourite editor, mine is leafpad but as gedit is on everyone elses install by default you can type:
```
sudo gedit /etc/X11/xorg.conf
``` Now scroll down to the mouse section and instead of deleting it we're going to comment it out, to do this you put a "#" in front of each line in the section, again here is my commented section as an example:

```
#Section "InputDevice"
#    Identifier    "Configured Mouse"
#    Driver        "mouse"
#    Option        "CorePointer"
#    Option        "Device"        "/dev/input/mice"
#    Option        "Protocol"        "ImPS/2"
#    Option        "Emulate3Buttons"    "true"
#    Option        "ZAxisMapping"        "4 5"
#EndSection
``` Again, yours might look different, the important bit is to comment the whole section out, but only this section.

Next up we want to paste in out new section, make a but of room underneath (or above if you prefer) that section we just commented out and paste in the following template:

```
Section "InputDevice"
        Identifier    "Configured Mouse"
        Driver        "mouse"
    Option        "Protocol"        "evdev"
    Option        "Dev Name"        "Logitech USB-PS/2 Optical Mouse"
    Option        "Dev Phys"        
        Option        "Device"        
    Option        "Buttons"        "10"
    Option        "ZAxisMapping"        "4 5"
EndSection
``` If, when you read the details of the mouse (above) it printed a different name to "Logitech USB-PS/2 Optical Mouse" then edit that so it's right, but I suspect it will be the same. Next you'll have probably noticed there are two fields missing, "Dev Phys" and "Device". We'll fill this in now.

"Dev Phys" needs the detail from the "Phys" line from the output before, so if you look back at my example mine said "Phys=usb-0000:00:02.0-7/input1" so I would put "usb-0000:00:02.0-7/input1" in or better yet as we can use wild cards I would use "usb-*/input0" which, if anything else, looks better :)

"Device" needs the detail from the "Handlers" line, again my example was "Handlers=mouse0 event2 ts0", this time all we need it the name of what "event" it is. For me it's "event2" but before we add it to the xorg.conf file we need to make sure we use the full path which will be "/dev/input/event2".

DancingSun wisely pointed out that the button numbers after "ZAxisMapping" should be the values of the scroll wheel up and down. Use the "xev" tool in a terminal to check which button numbers these are. That is, you run "xev" in a terminal, hover the mouse over the pop up window and on the mouse push the scroll wheel up. The last line of the output in the terminal will tell you what button number you just pressed. Here is a sample from running xev, I've highlighted the button number:
```
ButtonPress event, serial 29, synthetic NO, window 0x3a00001,
    root 0x134, subw 0x0, time 10223576, (111,54), root:(126,151),
    state 0x0, **button 4**, same_screen YES

ButtonRelease event, serial 29, synthetic NO, window 0x3a00001,
    root 0x134, subw 0x0, time 10223576, (111,54), root:(126,151),
    state 0x800, **button 4**, same_screen YES
``` Note the button number down and do the same for the scroll wheel down then put it in the xorg.conf file, scroll up goes first, then scroll down. For mx510 users the above "4 5" is correct. 

DancingSun also has posted a great way to find out exactly how many mouse buttons you actually have for the "Buttons" setting in your xorg.conf file, it's explained best in DancingSun's post which you can read [here]("http://www.ubuntuforums.org/showpost.php?p=361478&postcount=30"). Thanks again DancingSun!

*Note: mx700 users report the name needs to be "Logitech USB Receiver" not "Logitech USB-PS/2 Optical Mouse" like it is for my mx510. Please refer to your output from "cat /proc/bus/input/devices" to be sure. Additionally, iverson0881 found that for the mx700 you can use "/dev/input/ts0" to work. Again check your output from earlier as you may need to change it to "ts1" or "ts2" etc... You can see iverson0881's post [here]("http://ubuntuforums.org/showpost.php?p=353244&postcount=12").*

Make sure you save the changes to your xorg file.

So to conclude, here is my example with everything filled in:

```
Section "InputDevice"
        Identifier    "Configured Mouse"
        Driver        "mouse"
    Option        "Protocol"        "evdev"
    Option        "Dev Name"        "Logitech USB-PS/2 Optical Mouse"
    Option        "Dev Phys"        "usb-*/input0"
        Option        "Device"        "/dev/input/event2"
    Option        "Buttons"        "10"
    Option        "ZAxisMapping"        "4 5"
EndSection
``` *Note: If you have another mouse with more or less buttons then you may will have to correct the "Buttons" and "ZAxisMapping" numbers, but mine are correct for the mx510. It may not seem like it has ten buttons but it does if you count every single button*


_3. Restart X_

_Warning!_
Don't restart X yet! Just before we do I have to warn you if you made a mistake in the xorg file X will not restart. But don't worry that's why we only commented out the previous settings and didn't delete them. If X fails to restart then you will end up in a text console. Log in and type the following to edit the xorg file:

```
sudo nano /etc/X11/xorg.conf
``` All you need to do is comment out the new section we just added by putting a "#" in front of each line and un-commenting the original section by deleting the "#" which is at the start of each line. Save the xorg file in nano by typing "CTRL + X" press "Y" to confirm the save and type "startx" to get back to your desktop and re-read section two carefully and correct your xorg file.


_Ok, I'm ready_
Now we're prepared, restart X by pressing "CTRL + ALT + BACKSPACE" simultaneously and hopefully after a moment you can log back in.


_4. Editing the Xmodmap file_

**** THIS SECTION IS REDUNDANT, SKIP TO SECTION 2 BELOW ** as DancingSun pointed out, using correct "ZAxisMapping" settings in your xorg.conf file is the correct way to have your scroll wheel work. See above about editing your xorg file, I will leave this section here for reference.**

*Note: prelude has found you don't necessarily need this step if you are using an mx1000. Thanks prelude!*

You probably already have an Xmodmap file but now we have more buttons available we need to correct it. Open it up with your text editor:
```
gedit ~/.Xmodmap
``` and paste the following, overwriting any previous "pointer" line:
```
pointer = 1 2 3 6 7 8 9 10 4 5
``` 
Now run xmodmap to apply these settings:
```
xmodmap ~/.Xmodmap
``` If this is the first time you created a .Xmodmap file then next time you log into gnome it will ask you if you want to automatically load it, add the file and click Ok if this happens.

Now all the buttons should work properly including the little up button above the scroll wheel. The side buttons should also make Firefox go forward and backward a page just like before but they will not work in Nautilus yet. Keep reading to see how to get that to work!

*Note: Again, if you're mouse has more or less buttons then you'll need to figure out what button numbers are the two side buttons, you can do this with the utility "xev" which you run from the terminal, hover the mouse over the pop up box and hold it still and press the side buttons. You'll see some output part of which is a button number. The two button numbers for you mouse go last in the .Xmodmap file, look at mine as an example.*[/INDENT] 
**_Section 2: Side buttons and Nautilus_**[INDENT]
We can use "xvkbd" and "xbindkeys" to bind the side mouse buttons to "ALT + LEFT" and "ALT + RIGHT" so they work as forward and backwards in Nautilus.


_1. xvkbd and xbindkeys_

Lets install "xvkbd" and "xbindkeys":

```
sudo apt-get install xvkbd xbindkeys
``` Next we need to create the configuration for them:

```
gedit ~/.xbindkeysrc
``` Now paste the following:

```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7
``` 

**Please note, the "L" and "R" from the words "left" and "right" in the square brackets above should be capitalised, this seems like a bug in the forums here that they don't display properly.**

Make sure you keep the quote marks, save the file and run "xbindkeys" in the terminal. It runs as a daemon in the background. You should now be able to test if it works in Nautilus by using the side buttons it also works in Epiphany if you use it.

*Note: Same as before, if you have different mouse buttons use xev to find out what number they are and change the "b:6" and "b:7" in the above to the correct numbers.*

_2. Adding it to your session_

Now it's working open up the gnome sessions settings "System > Preferences > Sessions" click on the "Startup Programs" tab, click "Add" and enter "xbindkeys". This makes sure it's run each time you log in, you should probably test it by logging out and back in now.
[/INDENT] **_Section 3: The logitech_applet_**[INDENT]

First of all some people use a program called LMCtl instead, but I've never had it working so I use logitech_applet, which isn't an applet by the way :) This section is for making sure your mouse is using the best resolution it can, making it more accurate which is pretty handy especially in games where that counts like Quake 3 :)


_1. Getting everything we need_

There is no logitech_applet in Synaptic so I just download the source and use the program "checkinstall" to package it and install it, you'll also need the "build-essential" packages which can be quite large so bear this in mind and the "libusb-dev" library. Once this is done you can uninstall it if you want via Synaptic. Ok so lets download and install logitech_applet:

```
sudo apt-get install checkinstall build-essential libusb-dev
wget http://freshmeat.net/redir/logitech_applet/53319/url_tgz/logitech_applet-0.4test1.tar.gz
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

I think that's everything, phew, this was longer than I expected. I hope it works for you and I haven't made too many mistakes. Please add any corrections and success stories for logitech mice other then the mx510 so we can find out what works. Oh an I can confirm this still works on breezy right now and should still work when it's released.

Thanks to linux-gamers.net who have some great guides and give me good ideas and everyone who gave me feedback and corrections :)

---

### Post by GoA on 2005-09-14
Thanks, will try this @home.

---

### Post by A-star on 2005-09-14
[QUOTE=GoA]Thanks, will try this @home.[/QUOTE]
 Does this also work with a Logitech Dual Optical

---

### Post by dlpfmVfH on 2005-09-14
This works with Breezy...I got a logitech mx510 and it works great...
thanks for the great how to....
couldn't figure out the small buttons on top with the other how to's about extra buttons...

but this worked great...

---

### Post by GoA on 2005-09-15
*) Option "Protocol" "evdev"
(**) Configured Mouse: Protocol: evdev
(**) Option "Buttons" "10"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "9 10"
(**) Configured Mouse: ZAxisMapping: buttons 9 and 10
(**) Configured Mouse: Buttons: 10
(**) Configured Mouse: Protocol: evdev
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Buttons" "10"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "9 10"
(**) Configured Mouse: ZAxisMapping: buttons 9 and 10
(**) Configured Mouse: Buttons: 10
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Dev Name" "Logitech USB-PS/2 Optical Mouse"
(**) Option "Dev Phys" "usb-*/input0"
(EE) Configured Mouse: cannot open input device
(**) Option "Dev Name" "Logitech USB-PS/2 Optical Mouse"
(**) Option "Dev Phys" "usb-*/input0"
(EE) Configured Mouse: cannot open input device
No core pointer

Fatal server error:
failed to initialize core devices

Please consult the The X.Org Foundation support 
	 at [http://wiki.X.Org](http://wiki.X.Org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

Didn't work with MX700. 

Here is the cat:

I: Bus=0003 Vendor=046d Product=c506 Version=1600
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.1-2/input0
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=103

And with xorg I used usb-*/input0 and /dev/input/event1. Don't know anymore what happened. :)

---

### Post by souled on 2005-09-15
I also have the Mx 700 but cannot get it to work. 

```
I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Logitech Mouse"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse0 ts0 event1
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3
```

When I change the xorg.conf and put in:

```
Section "InputDevice"
        Identifier	"Configured Mouse"
        Driver		"mouse"
	Option		"Protocol"		"evdev"
	Option		"Dev Name"		"PS/2 Logitech Mouse"
	Option		"Dev Phys"		"isa0060/serio1/input0"
        Option		"Device"		"/dev/input/event1"
	Option		"Buttons"		"10"
	Option		"ZAxisMapping"		"9 10"
EndSection
```

X starts fine, but I am unable to move my mouse. And yes, I do have my mouse plugged into a USB port.

---

### Post by rejser on 2005-09-15
I run in xorg.conf
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option 		"Device" "/dev/input/mice"
	Option 		"Protocol" "ExplorerPS/2"
	Option 		"Buttons" "7"
	Option 		"ZAxisMapping" "6 7"

then installed imwheel and run following script at startup

#!/bin/sh
exec xmodmap -e "pointer = 1 2 3 6 7 4 5" &
exec imwheel -k -b "67" &
exec $REALSTARTUP

and finaly  you have to put

".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

in /etc/X11/imwheel/imwheelrc ( at the bottom is ok)

This tip is from someone in this forum, couldn't find who should have the credz though, so give them to me for the moment and I will pass them on (or not)
__________________

On my logitech MX 700, backward and forward works with nautilus, xffm, firefox...

---

### Post by souled on 2005-09-15
[QUOTE=rejser]I run in xorg.conf
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option 		"Device" "/dev/input/mice"
	Option 		"Protocol" "ExplorerPS/2"
	Option 		"Buttons" "7"
	Option 		"ZAxisMapping" "6 7"

then installed imwheel and run following script at startup

#!/bin/sh
exec xmodmap -e "pointer = 1 2 3 6 7 4 5" &
exec imwheel -k -b "67" &
exec $REALSTARTUP

On my logitech MX 700, backward and forward works with nautilus, xffm, firefox...[/QUOTE]

I changed my xorg.conf to look like yours, and I ran that script. Now the scroll up and down buttons work, but the thumb buttons also scroll up and down. The lower thumb button scrolls up and the upper thumb button scrolls down. How can I fix this?

---

### Post by prelude on 2005-09-15
howdies

Ive used this guide on Breezy with a MX1000 mouse, I cant complete the guide, but its not completly fruitless. 

first off, I edited my xorg.conf like this 
```

	Option		"Protocol"		"evdev"
	Option		"Dev Name"		"Logitech USB RECEIVER"
	Option		"Dev Phys"		"usb-0000:00:1d.2-2.2/input0"
        Option		"Device"		"/dev/input/event3"
	Option		"Buttons"		"12"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"

```

and restarted X (with sudo killall gdm, logged in on a term and did sudo gdm) back in gnome the mouse worked as before the edit, but with one exception.

the thumbbuttons worked in firefox withouth any other tinkering under the hood  \\:D/ the only strangeness was that the wheel-tilt to the right registrers as scroll up while tilt left goes down and the cruise buttons registers as a single 'click' up or down, where it before the editing gave me continius scroll up/down.

then I installed xvkbd and xbindkeys and with both config files as explained in this howto applied on a MX1000 mouse gives erratic behaviour. 

HOWEVER, if you leave out the xmodmap step the mouse works as expected.
simply put, with a MX1000 mouse you dont really need xmodmap if you dont plan to use the sidetilt and crouse buttons. if you do want to use xmodmap with this guide you need to put 

```

pointer = 1 2 3 4 5 6 7 8 9 10 11 12

```
into the .Xmodmap file.

as you can see, the mousebutton-layout in xmodmap doesnt swap around any buttons. (atleast with me, youre milage may vary)
note. when xmodmap is used the continius scrolling by holding down one of the cruisebuttons works again with me.

here ends my experience, Ive havent got past the installation of the logitec applet, when I try to install it this happens.

```

checking for usb.h... no

   ERROR!  libusb header not found, get it from
   http://libusb.sourceforge.net
   or use the --with-libusb-includes option, if you have it installed
   in an unusual place

```

now Ive checked with synaptic, I have libusb. Ive tried re-installing it, Ive tried removing it completly and then installing it again but to no avail and I have no clue where the include files might be  ](*,)

ahhwell..  

my thumb buttons works, thats the important stuff.  :grin:

---

### Post by endy on 2005-09-15
**Goa**, I notice from the output of "cat /proc/bus/input/devices" you get Name="Logitech USB Receiver", try using that name in the xorg.conf file like this:
```
"Dev Name"		"Logitech USB Receiver"
```
I hope this works :)

**souled**, this is strange. It would look like the "event0" is maybe not the right one. What you can do to make sure is "ls /dev/input" and go through trying to cat each event as root and try moving your mouse. If you get loads of garbage in the terminal when you move the mouse then that "event*" is the right one. Here is an example of what I mean:

```
cat /dev/input/event0
```
If when you move the mouse nothing happens try /dev/input/event1 etc... Hopefully one of them will work and use that in your xorg.conf.

**prelude**, thanks for the update on the mx1000 and the Xmodmap file, I've updated the guide :) I also noticed that I did miss out the need to install the "libusb-dev" library to compile the logitech_applet, again I've updated the guide with "sudo apt-get install libusb-dev" :)

---

### Post by rejser on 2005-09-15
[QUOTE=souled]I changed my xorg.conf to look like yours, and I ran that script. Now the scroll up and down buttons work, but the thumb buttons also scroll up and down. The lower thumb button scrolls up and the upper thumb button scrolls down. How can I fix this?[/QUOTE]

Oh, forgot that you have to put

".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

in  /etc/X11/imwheel/imwheelrc ( at the bottom is ok)

---

### Post by iverson0881 on 2005-09-15
I have a MX700 and this worked fine although here is what I have in my xorg.conf:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Protocol"		"evdev"
	Option		"Dev Name"		"Logitech USB Receiver"	
	Option		"Dev Phys"		"usb-*/input1"
	Option		"Device"		"/dev/input/ts0"
	Option		"Buttons"		"10"
	Option		"ZAxisMapping"		"9 10"
EndSection
``` 

My mouse is connected through the Ps/2 port of the computer while keyboard is connected through USB. I have the Logitech MX Duo

---

### Post by prelude on 2005-09-15
[QUOTE=endy]
**prelude**, thanks for the update on the mx1000 and the Xmodmap file, I've updated the guide :) I also noticed that I did miss out the need to install the "libusb-dev" library to compile the logitech_applet, again I've updated the guide with "sudo apt-get install libusb-dev" :)[/QUOTE]

so thats the little bugger that stopped me from making the logitec 'applet'. when I fiddled with synaptic I saw it but I ignored it as the error message didnt say squat about any missing -dev support :roll:

dont think Ill complete it though, Im just happy my side buttons work allright  \\:D/

---

### Post by souled on 2005-09-15
[QUOTE=rejser]Oh, forgot that you have to put

".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

in  /etc/X11/imwheel/imwheelrc ( at the bottom is ok)[/QUOTE]

I did this, and the thumb buttons work, but now the up scroll button acts as the back button.

[QUOTE=endy]souled, this is strange. It would look like the "event0" is maybe not the right one. What you can do to make sure is "ls /dev/input" and go through trying to cat each event as root and try moving your mouse. If you get loads of garbage in the terminal when you move the mouse then that "event*" is the right one. Here is an example of what I mean:[/QUOTE]

Trying it this way... I get a bunch of "garbage" output when I use /dev/input/event3. Nothing happens for event 0-2. When I used event 3 in the xorg.conf, I get the same problem. Everything works, but I can't move my mouse.

---

### Post by rejser on 2005-09-16
[QUOTE=souled]I did this, and the thumb buttons work, but now the up scroll button acts as the back button.
[/QUOTE]

Mine does to, never tested that button, will try to fix during the day

---

### Post by rejser on 2005-09-16
A fixed for Logitech mx510 700 900 1000 (not 500, test 9 buttons)
(on what i wrote earlier)
I run in xorg.conf
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Buttons" "10"                       <--- change from earlier post
Option "ZAxisMapping" "6 7"

then installed imwheel and run following script at startup

#!/bin/sh
exec xmodmap -e "pointer = 1 2 3 6 7 8 9 10 4 5" &   <--- also a change
exec imwheel -k -b "67" &
exec $REALSTARTUP

and finaly you have to put

".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

in /etc/X11/imwheel/imwheelrc ( at the bottom is ok)

still the same....

---

### Post by endy on 2005-09-16
**iverson0881**, thanks for the info, I've updated the guide accordingly :)

**souled**, I suggest you try this too, refer to [iverson0881's post](http://ubuntuforums.org/showpost.php?p=353244&postcount=12)  as an example but double chek your output from "cat /proc/bus/input/devices" to make sure which "ts" you could try, ie ts0, ts1 etc...

---

### Post by Shambler on 2005-09-16
Works like a charm under Breezy with my MX500, although the correct device name for this model is: "B16_b_02 USB-PS/2 Optical Mouse"

Just 2 small corrections:

1. It has to be ```
sudo apt-get **install** checkinstall build-essential libusb-dev
``` 

2. You have to ```
chmod 755 /etc/init.d/local
``` so that it gets loaded

---

### Post by GoA on 2005-09-17
Works perfectly now with mx700 thank you so much. :)

---

### Post by endy on 2005-09-17
Thanks Shambler, I've amended the guide accordingly. Great to hear it works :)

---

### Post by poofyhairguy on 2005-09-17
This how to just saved my Linux life. For the past few days I could not log into Ubuntu because the Xserver could not detect my mouse driver. I could comment out the mouse device part and get it to work, but the mouse had minimal functions. I was scared I would have to reinstall or quit using Ubuntu because I really like to scroll. But with the info in this how to and thread I have my mouse working better than before. Awesome!

Great how to.

---

### Post by endy on 2005-09-17
Thanks! Ironically I wrote this after a very, very long day when I was completely exhausted but I had this guide in my head for a few days and just wanted to get it out. I thought I'd managed to clear up most of the mistakes but just now noticed I mistyped the topic. That's what happens when you post on forums half asleep :)

Anyway, glad to hear this helped.

---

### Post by spacemonkey on 2005-09-18
What about a MediaPlay Mouse?  Any way to get the media control buttons working?  I really miss them.

---

### Post by endy on 2005-09-18
If you can get the buttons to register with xev then all you need to do is bind them to shortcuts I guess... I don't have this mouse so I don't know what level of support there is for it. If you try please post any success stories for others to find :)

---

### Post by DancingSun on 2005-09-19
I would like to add that it is NOT necessary to remap the scroll buttons.  It seems a bit self-defeating that almost all of the guides tell you to assign buttons 9 and 10 to z-axis, but then remaps the buttons 9 and 10 to the position where buttons 4 and 5 are.   Essentially, you are telling X that buttons named 9 and 10 are your z-axis buttons, then you remap the button names so that the physical buttons 4 and 5 are named 9 and 10.  You might as well just assign 4 and 5 to the zaxismapping option and do away with remapping the buttons altogether.

I'm using MX510, and I did not go through the remapping stage when I configured my mouse, just as the user with the MX1000 mouse.

Here's how it should work:
Type the following command into your terminal:
```
xev
```
This will bring up a little window where you can move your mouse pointer into.  You can see all of the events generated by the mouse.  Try clicking each of the buttons on your mouse while the mouse pointer is inside the window.  Make sure the mouse stays stationary, or else you'll get a bunch of movement events that will make finding the button events harder.

In my case, I can clearly see that my scroll wheel generates the same button events as my cruise buttons.  So essentially they are of the same buttons (cruise up = scroll up, cruise down = scroll down).  This tells me that my MX510 have 8 functional buttons, not 10!  The number of buttons entered in xorg.conf should be the highest button number event, which is 8 in my case.  So adjust your number of buttons option accordingly!

Now, to setup the zaxismapping in xorg.conf, take note of the button events generated by the scroll buttons, and enter them into the zaxismapping option.  I believe most mice generate button events 4 and 5 for scroll wheels, and this is exactly what I have for the zaxismapping option:
```
Option		"ZAxisMapping"		"4 5"
```

BTW, this is a great guide!  I've been wanting to write one myself, but was too lazy.  On another note, endy, the first two part of this guide (the xorg.conf using evdev and button binding part) should be generic to any mice.  So you could split those parts out as a generic configuration guide to multi-button mice with scroll wheels.

---

### Post by prelude on 2005-09-19
that user would be me :P

on my mx1000 I need to have 12 buttons in xorg to make things work properly, even though xev output only reports 10 diffrent buttons.

xev reports the following buttons.

left click: button 1
middle click: button 2
right click: button 3
scroll forward: button 4
scroll backward: button 5
tilt right: button 4
tilt left: button 5
forward thumb: button 8
app. button: button 6
thumb button: button 7
cruise forward: button 4 **and** 10
cruise backward: button 5 **and** 12

as you can see, my mouse reports all buttons from 1 to 12 but skips 9 and 11. I belive those two missing buttons are the tilt-wheel and either xorg/xev is unable to recieve/see them, or logitec has built in a switch that can be sent from the host machine into the mouse telling it to report the extra buttons or not.

anyhows, my point is that not all mice might work if one enters less buttons in xorg.conf than their mice really have.

---

### Post by DancingSun on 2005-09-19
Perhaps I should put it this way:
> The number of buttons to be enter in xorg.conf equal the highest button number event recorded in xev.
Does that sound right?  I'm not trying to say one should enter less number of buttons that what their mice really have, just that one should enter the "correct" number of buttons that the mice is actually generating.

---

### Post by KompresZor on 2005-09-20
Thanks for the great guide!! 
I have an old Logitech 4 (6) button USB mouse ( M-BA47 ) and with a few minor changes this worked perfectly! All I had to do was change the setting in xorg.conf, restart X and everything worked. :grin: 

Here is my xorg.conf.
```
Section "InputDevice"
        Identifier	"Configured Mouse"
        Driver		"mouse"
	Option		"Protocol"		"evdev"
	Option		"Dev Name"		"Logitech USB-PS/2 Mouse M-BA47"
	Option		"Dev Phys"		"usb-0000:00:07.3-1/input0"
        Option		"Device"		"/dev/input/event4"
	Option		"Buttons"		"6"
	Option		"ZAxisMapping"		"4 5"
EndSection
```

---

### Post by endy on 2005-09-20
Thanks DancingSun, I can't believe I didn't notice that! I've been doing that for over a year and never thought to question what I was doing. Guide updated :)

---

### Post by DancingSun on 2005-09-20
[QUOTE=endy]Thanks DancingSun, I can't believe I didn't notice that! I've been doing that for over a year and never thought to question what I was doing. Guide updated :)[/QUOTE]
No problem!  Glad I could contribute!  Also, you might want to update the part about the number of buttons to enter in xorg.conf.

Essentially, you should enter the highest button number that is captured by xev.  I should note that to start off, one should enter a reasonably large value for the number of buttons in xev, or else some buttons will be prohibited from generating click events and won't be captured by xev.  So here's the steps to find out how many buttons your mouse really have:

[list=1]
[*]Choose a reasonably large number (usually the physical count of your mouse buttons plus the scroll wheel up and down), and enter that number in xorg.conf
[*]Use xev to find out what's the largest button number captured.  Replace what you had in xorg.conf with this number.
[/list] 
While you could enter more buttons that what your mouse really has, and it'll still work, but you will be using more system resources than what you really need.  Since the X server will add hooks to listen to events generated from those extra, non-existent buttons.

endy, you might want to add the following link on xorg.conf mouse options to the guide for reference.
[http://www.x.org/X11R6.8.2/doc/mouse5.html#21](http://www.x.org/X11R6.8.2/doc/mouse5.html#21)

prelude, you might want to take a look at the above link.  It has a section on zaxismapping with horizontal scrolling.  Although from the looks of your xev output, it looks like it won't work, but maybe you can play around with the settings a bit.  So, right now you have the tilt wheels doing vertical scrolling as well?

Also, you'll see a "resolution" option documented in the above link.  I don't know if this can replace the "logitech applet", but I guess you guys can experiment a bit with this option and see if it makes a difference.

---

### Post by endy on 2005-09-20
[QUOTE=DancingSun]No problem!  Glad I could contribute!  Also, you might want to update the part about the number of buttons to enter in xorg.conf.[/QUOTE]

Updated, and as your explanation was so good I linked to your post! Thanks again :)

---

### Post by DancingSun on 2005-09-20
[QUOTE=endy]Updated, and as your explanation was so good I linked to your post! Thanks again :)[/QUOTE]
Hmm...I don't see where the link is at?  :confused:

---

### Post by ricesteam on 2005-09-20
I just like to say, thanks for a great guide!

However it doesn't work too well with an IBM ThinkPad R31.

When I'm home, I like to plug in a USB Mx700 mouse. 

You're tutorial works and everything, but it disables my trackpoint (the little red button that acts as a mouse on these laptops).

Is it possible to have a fully functional Mx700 with trackpoint enabled?

---

### Post by Mais on 2005-09-21
The mx518 supports up to 1600 dpi resolution. Is there anyway to get this working in gnome?

---

### Post by endy on 2005-09-21
[QUOTE=DancingSun]Hmm...I don't see where the link is at?  :confused:[/QUOTE]

Sorry I don't know what happened, a forum fart or something? I did add a paragraph but  it just disappeared... Well that's fixed now!

Mais, you could see if [lmctl](http://freshmeat.net/projects/lmctl/) works but the freshmeat page doesn't look very hopeful quoting only "800cpi". You could also try emailing the author of lmctl and/or the author of [logitech_applet](http://freshmeat.net/projects/logitech_applet/). Maybe they know how to get this done or maybe they might be able to update the tools to support the mx518 with your help :)

EDIT: I just found this page, worth a try I suppose: [http://www.linux-gamers.net/modules/news/article.php?storyid=761](http://www.linux-gamers.net/modules/news/article.php?storyid=761) :)

---

### Post by DancingSun on 2005-09-21
[QUOTE=Mais]The mx518 supports up to 1600 dpi resolution. Is there anyway to get this working in gnome?[/QUOTE]
You might want to try adding the [resolution](http://www.x.org/X11R6.8.2/doc/mouse5.html#24) option to your xorg.conf.  Let us know if that works or not.

---

### Post by Brando569 on 2005-09-21
works perfectly on my mx700 for anyone that has one heres my config file:

Section "InputDevice"
        Identifier	"Configured Mouse"
        Driver		"mouse"
	Option		"Protocol"		"evdev"
	Option		"Dev Name"		"Logitech USB Receiver"
	Option		"Dev Phys"		"usb-0000:00:1d.1-2/input0"
        Option		"Device"		"/dev/input/event3"
	Option		"Buttons"		"8"
	Option		"ZAxisMapping"		"4 5"
EndSection

great job!

---

### Post by candyman963 on 2005-09-28
OK, I'd like to add a little twist to this. I've got an MX510 set up more or less exactly as this guide says. However, in my Windows installation I have the cruise control buttons bound to page up and page down, which I find much more useful than the actual cruise control. I've tried various settings in .xbindkeysrc, but have had no luck. Anybody have an idea here?

---

### Post by DancingSun on 2005-09-28
[QUOTE=candyman963]OK, I'd like to add a little twist to this. I've got an MX510 set up more or less exactly as this guide says. However, in my Windows installation I have the cruise control buttons bound to page up and page down, which I find much more useful than the actual cruise control. I've tried various settings in .xbindkeysrc, but have had no luck. Anybody have an idea here?[/QUOTE]
It's likely that when you bind the cruise up and down buttons to page up and down, the scroll wheel will also do page up and down, because both the cruise buttons and the scroll wheel generate the same button events on the MX510.  So to X, they are essentially the same buttons.

---

### Post by nenotnom on 2005-09-30
This guide worked perfectly for me a couple of weeks ago, but now I've reinstalled Ubuntu and despite a complete lack of error messages, I can't get it to work.
The thumb buttons on my MX 510 don't do backwards/forwards, but they're changed from the default state ( where the front button is button2 and the back is b1?) so I know I did something. 
Here's some info:
-------------------------------
cat /proc/bus/input/devices:
"
I: Bus=0003 Vendor=046d Product=c01d Version=2100
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:02.1-4/input0
H: Handlers=mouse0 event4 ts0
B: EV=f
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103
B: ABS=300 0
"
My x config:
"
Section "InputDevice"
Identifier      "Configured Mouse"
Driver          "mouse"
Option          "Protocol"              "evdev"
Option          "Dev Name"              "Logitech USB-PS/2 Optical Mouse"        Option          "Dev Phys"              "usb-*/input0"
Option          "Device"                "/dev/input/event4"
Option          "Buttons"               "10"
Option          "ZAxisMapping"          "4 5"
EndSection
"
and I did the "Section 2: Side buttons and Nautilus" exactly as it said.
I want to get my thumbbuttons working, does anybody know where I should start looking?

---

### Post by DancingSun on 2005-09-30
[QUOTE=nenotnom]This guide worked perfectly for me a couple of weeks ago, but now I've reinstalled Ubuntu and despite a complete lack of error messages, I can't get it to work.
The thumb buttons on my MX 510 don't do backwards/forwards, but they're changed from the default state ( where the front button is button2 and the back is b1?) so I know I did something. 
Here's some info:
-------------------------------
cat /proc/bus/input/devices:
"
I: Bus=0003 Vendor=046d Product=c01d Version=2100
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:02.1-4/input0
H: Handlers=mouse0 event4 ts0
B: EV=f
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103
B: ABS=300 0
"
My x config:
"
Section "InputDevice"
Identifier      "Configured Mouse"
Driver          "mouse"
Option          "Protocol"              "evdev"
Option          "Dev Name"              "Logitech USB-PS/2 Optical Mouse"        Option          "Dev Phys"              "usb-*/input0"
Option          "Device"                "/dev/input/event4"
Option          "Buttons"               "10"
Option          "ZAxisMapping"          "4 5"
EndSection
"
and I did the "Section 2: Side buttons and Nautilus" exactly as it said.
I want to get my thumbbuttons working, does anybody know where I should start looking?[/QUOTE]
Refer to this post on using "xev" to get the button events generated by your mouse:
[http://ubuntuforums.org/showpost.php?p=359467&postcount=25](http://ubuntuforums.org/showpost.php?p=359467&postcount=25)
Then, post the button events generated by each of your buttons.

---

### Post by nenotnom on 2005-09-30
I think this is it:
Front thumbbutton:
LeaveNotify event, serial 29, synthetic NO, window 0x2c00001,
root 0xd6, subw 0x0, time 209594, (150,172), root:(228,269),
mode NotifyGrab, detail NotifyAncestor, same_screen YES,
focus NO, state 16
EnterNotify event, serial 29, synthetic NO, window 0x2c00001,
root 0xd6, subw 0x0, time 209810, (150,172), root:(228,269),
mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
focus NO, state 16
KeymapNotify event, serial 29, synthetic NO, window 0x0,
keys:  4294967254 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 
0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
Rear:
LeaveNotify event, serial 29, synthetic NO, window 0x2c00001,
root 0xd6, subw 0x0, time 257818, (146,161), root:(224,258),
mode NotifyGrab, detail NotifyAncestor, same_screen YES,
focus NO, state 16
EnterNotify event, serial 29, synthetic NO, window 0x2c00001,
root 0xd6, subw 0x0, time 258002, (146,161), root:(224,258),
mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
focus NO, state 16
KeymapNotify event, serial 29, synthetic NO, window 0x0,
keys:  4294967254 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 
0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

---

### Post by DancingSun on 2005-09-30
No, that's not it...it should look like something on the first post:
```
**ButtonPress event**, serial 29, synthetic NO, window 0x3a00001,
root 0x134, subw 0x0, time 10223576, (111,54), root:(126,151),
state 0x0, **button 4**, same_screen YES
**ButtonRelease event**, serial 29, synthetic NO, window 0x3a00001,
root 0x134, subw 0x0, time 10223576, (111,54), root:(126,151),
state 0x800, **button 4**, same_screen YES
```
Note the bolded text.

---

### Post by nenotnom on 2005-09-30
[QUOTE=DancingSun]No, that's not it...it should look like something on the first post:
```
**ButtonPress event**, serial 29, synthetic NO, window 0x3a00001,
root 0x134, subw 0x0, time 10223576, (111,54), root:(126,151),
state 0x0, **button 4**, same_screen YES
**ButtonRelease event**, serial 29, synthetic NO, window 0x3a00001,
root 0x134, subw 0x0, time 10223576, (111,54), root:(126,151),
state 0x800, **button 4**, same_screen YES
```
Note the bolded text.[/QUOTE]
I have nothing like that when I press either of my thumb buttons, no buttonrelease or number =(
This is after I changed stuff as mentioned in the guide mind you.

[edit]

When I changed back to default I get this:

Front:

ButtonPress event, serial 26, synthetic NO, window 0x3000001,
root 0xd6, subw 0x0, time 67358, (127,176), root:(205,273),
state 0x10, button 3, same_screen YES

ButtonRelease event, serial 26, synthetic NO, window 0x3000001,
root 0xd6, subw 0x0, time 67468, (127,176), root:(205,273),
state 0x410, button 3, same_screen YES

Rear:

ButtonPress event, serial 26, synthetic NO, window 0x3000001,
root 0xd6, subw 0x0, time 105532, (153,169), root:(231,266),
state 0x10, button 2, same_screen YES

ButtonRelease event, serial 26, synthetic NO, window 0x3000001,
root 0xd6, subw 0x0, time 105652, (153,169), root:(231,266),
state 0x210, button 2, same_screen YES

[/edit]

---

### Post by DancingSun on 2005-09-30
Follow the guide, and DON'T do the button binding section for Nautilus.  And see if the mouse still works correctly.  Try the side buttons in "xev" and in Firefox.  The forward and backward buttons should work in Firefox.

---

### Post by nenotnom on 2005-09-30
I removed "~/.xbindkeysrc" restarted X by ctrl alt backspace, and lo and behold, the keys are now reported as 7 and 6 by xev, 7 being front button. It works in firefox but not nautilus.

---

### Post by DancingSun on 2005-09-30
Well, at least we now know that your xorg.conf is working alright.  The key binding part is definitely weird...are you sure your config file was correct?  The instructions looked ok, but then again, I've never tried doing keybindings for my mouse...

Try doing the keybindings again.

---

### Post by nenotnom on 2005-09-30
created ~/.xbindkeysrc again

c&p'ed this:

"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
m:0x0 + b:7

then I ran xbindkeys from console, then I tried the keys in nautilus, didn't work =/

Weirdness!

---

### Post by DancingSun on 2005-09-30
[QUOTE=nenotnom]created ~/.xbindkeysrc again
c&p'ed this:
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
m:0x0 + b:7
then I ran xbindkeys from console, then I tried the keys in nautilus, didn't work =/
Weirdness![/QUOTE]
What about Firefox and xev?  Did the bindings kill the buttons altogether?

---

### Post by nenotnom on 2005-09-30
[QUOTE=DancingSun]What about Firefox and xev?  Did the bindings kill the buttons altogether?[/QUOTE]

It killed it allright.

---

### Post by DancingSun on 2005-09-30
[QUOTE=nenotnom]It killed it allright.[/QUOTE]
That's odd...I wonder if endy got it working with the key bindings.

I'll try it out this weekend if I have time.

---

### Post by jaakko on 2005-10-01
Thank you, this is a great guide! :D It worked fine with the new version (5.10) too.
**edit: ** I had problems with the configuration of the file .xbindkeysrc because I didn't notice that in
```

"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
m:0x0 + b:7

```
the correct buttons [Left] and [Right] must be in upper case.

**edit: **I can't write, I meant **first letter** must be in upper case. Correct buttons are Left and Right. :)

---

### Post by bob_c_b on 2005-10-02
[QUOTE=jaakko]Thank you, this is a great guide! :D It worked fine with the new version (5.10) too.
**edit: ** I had problems with the configuration of the file .xbindkeysrc because I didn't notice that in
```

"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
m:0x0 + b:7

```
the correct buttons [Left] and [Right] must be in upper case.[/QUOTE]

Yep, that fixed it for me as well, good find.

---

### Post by nenotnom on 2005-10-02
[QUOTE=jaakko]Thank you, this is a great guide! :D It worked fine with the new version (5.10) too.
**edit: ** I had problems with the configuration of the file .xbindkeysrc because I didn't notice that in
```

"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
m:0x0 + b:7

```
the correct buttons [Left] and [Right] must be in upper case.[/QUOTE]

What do you mean?

---

### Post by DancingSun on 2005-10-02
[QUOTE=nenotnom]What do you mean?[/QUOTE]
It should be "LEFT" and "RIGHT". Not "left" and "right" in the config file. 

Edit:
Try using "left" and "right" all caps in brackets. It seems like it will be auto-converted into lowercase in a post.

---

### Post by nenotnom on 2005-10-02
I tried replacing "\[Alt_L]\[left]" with "smooth" and then I used the button on a terminal, and it typed out smooth, so it seems there's something wrong with "\[Alt_L]\[left]" in particular. I didn't get any results by replacing left with LEFT either.

---

### Post by jaakko on 2005-10-02
[QUOTE=nenotnom]I tried replacing "\[Alt_L]\[left]" with "smooth" and then I used the button on a terminal, and it typed out smooth, so it seems there's something wrong with "\[Alt_L]\[left]" in particular. I didn't get any results by replacing left with LEFT either.[/QUOTE]

Try replacing it with Left (and the other one with Right).

---

### Post by nenotnom on 2005-10-02
[QUOTE=jaakko]Try replacing it with Left (and the other one with Right).[/QUOTE]

I did, and it works now! I totally owe you a cookie =D

---

### Post by DancingSun on 2005-10-02
[QUOTE=nenotnom]I did, and it works now! I totally owe you a cookie =D[/QUOTE]
Hahaha, I can't believe we got stuck on a capitalization issue for so long!  See? It's always the little stuff that get you boggled!

---

### Post by nenotnom on 2005-10-03
Yeah, can't believe I didn't try that to begin with. Such a typical solution to a problem that's just too simple to not function correctly.

---

### Post by Pulse on 2005-10-04
First of all, thanks for the guide, it's been a real help.  

I've got everything on my mx500 working with my own customizations, except for one very strange problem - the bottom "cruise control" button doesn't work if I turn cruise control off; even pressing it in xev elicits no response.  What makes this so strange is that the top cc button *does* work; it registers as button 10 in xev and works just like any other other button.

If I turn cc on, they both replicate the mousewheel as intended and both can be bound to any key in Windows with no problems, so what gives?

---

### Post by DancingSun on 2005-10-04
[QUOTE=Pulse]First of all, thanks for the guide, it's been a real help.  

I've got everything on my mx500 working with my own customizations, except for one very strange problem - the bottom "cruise control" button doesn't work if I turn cruise control off; even pressing it in xev elicits no response.  What makes this so strange is that the top cc button *does* work; it registers as button 10 in xev and works just like any other other button.

If I turn cc on, they both replicate the mousewheel as intended and both can be bound to any key in Windows with no problems, so what gives?[/QUOTE]
Can you post your xorg.conf?  Also, did you do the Xmodmap part of the guide?  It's not needed anymore.

---

### Post by Téragone on 2005-10-06
I tried to configure my mx1000 following the guide. But  X server crashed at restart. Even the keyboard doesn't work anymore.
I'm on Hoary AMD 64.
Modification to xorg.conf :
#Section "InputDevice"
#      Identifier      "Configured Mouse"
#        Driver          "mouse"
#        Option          "CorePointer"
#        Option          "Device"                "/dev/input/mice"
#        Option          "Protocol"              "ImPS/2"
#        Option          "Emulate3Buttons"       "true"
#       Option          "ZAxisMapping"          "4 5"
#EndSection
Section "InputDevice"
Identifier      "Configured Mouse"
Driver          "mouse"
Option          "Protocol"              "evdev"
Option          "Dev Name"              "Logitech USB RECEIVER"
Option          "Dev Phys"              "usb-0000:00:10.0-1/input0"
Option          "Device"                "/dev/input/event2"
Option          "Buttons"               "12"
Option          "ZAxisMapping"          "4 5"
Option          "Emulate3Buttons"       "false"
EndSection
in the Xorg log I have this :
(**) Option "Dev Name" "Logitech USB RECEIVER"
(**) Option "Dev Phys" "usb-0000:00:10.0-1/input0"
(EE) Configured Mouse: cannot open input device
(**) Option "Dev Name" "Logitech USB RECEIVER"
(**) Option "Dev Phys" "usb-0000:00:10.0-1/input0"
(EE) Configured Mouse: cannot open input device
No core pointer
Fatal server error:
failed to initialize core devices
**cat /proc/bus/input/devices**
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=402000000 3802078f840d001 f2ffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7
I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
H: Handlers=kbd event1
B: EV=40001
B: SND=6
I: Bus=0003 Vendor=046d Product=c50e Version=2500
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:10.0-1/input0
H: Handlers=kbd mouse0 event2 ts0
B: EV=120007
B: KEY=ffff0000 1000000000000 0 0 0
B: REL=103
B: LED=fc00
Any idea ?

---

### Post by DancingSun on 2005-10-06
Check the first 3 pages of this thread.  Your "Dev Phys" entry is somehow wrong.

---

### Post by Téragone on 2005-10-06
Thanks for your reply,

I changed it to:

 usb-*/input0

Still the same problem

---

### Post by DancingSun on 2005-10-06
> **T&#233 said:**
> Thanks for your reply,

I changed it to:

 usb-*/input0

Still the same problem
Try this part, mentioned in the guide:
> Note: mx700 users report the name needs to be "Logitech USB Receiver" not "Logitech USB-PS/2 Optical Mouse" like it is for my mx510. Please refer to your output from "cat /proc/bus/input/devices" to be sure. Additionally, iverson0881 found that for the mx700 you can use "/dev/input/ts0" to work. Again check your output from earlier as you may need to change it to "ts1" or "ts2" etc... You can see iverson0881's post here.

From the errors you're getting, I think you have the same problem as GoA.  He somehow got it working.  Although I'm not sure which directions he followed, but I believe it's the one above.  If that doesn't work, try PMing him and ask him about the details.  I, unfortunately, don't have access to a wireless Logitech mouse, so I can't really help much besides pointing you to resources that might be helpful.

---

### Post by Téragone on 2005-10-06
Thanks again,

I found it,

It seem that Dev Name is case sensitive, I changed :

Logitech USB RECEIVER

to

Logitech USB Receiver

(cut and paste error :smile: )

and all is almost ok. Now forward and backward work in Firefox.

The tilt left and right with the wheel doesn't work. That buttons are not trapped by xev.

---

### Post by DancingSun on 2005-10-07
Hahaha, another capitalization error!  And I just commented on the last one too! Oh the irony!

---

### Post by brj on 2005-10-07
is it also possible to program the behaviour of the buttons for all applications ?

i'd like to have a double-click when i click the scroll-wheel or the thumb-buttons  .

jakob

---

### Post by tick on 2005-10-07
I have a MX 510. My problem ist that when I set ```
"ZAxisMapping"		"4 5"
``` the wheel works perfectly, small buttons too, but the side buttons dont respond, not even in xev.

When I set "ZAxisMapping" to "7 8" all buttons are shown in xev correctly:
1 lmb
2 mmb
3 rmb
4 side front
5 side rear
6 top
7 scroll up / small button up
8 scroll down /small button down

But the side buttons are mapped to scrolling up/down and mousewheel up/down is set to leftclick/nothing.

Tick



	```
Identifier  "MX510"
   	Driver		"mouse"
	Option		"Protocol"		"evdev"
	Option		"Dev Name"		"Logitech USB-PS/2 Optical Mouse"
	Option		"Dev Phys"		"usb-*/input0"
	Option		"Device"		"/dev/input/event1"
	Option		"Buttons"		"8"
	Option		"ZAxisMapping"		"4 5"
```


```
I: Bus=0003 Vendor=046d Product=c01d Version=2100
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:10.0-1/input0
H: Handlers=mouse0 event1
B: EV=7

B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

```

---

### Post by DancingSun on 2005-10-07
[QUOTE=tick]I have a MX 510. My problem ist that when I set ```
"ZAxisMapping"		"4 5"
``` the wheel works perfectly, small buttons too, but the side buttons dont respond, not even in xev.

When I set "ZAxisMapping" to "7 8" all buttons are shown in xev correctly:
1 lmb
2 mmb
3 rmb
4 side front
5 side rear
6 top
7 scroll up / small button up
8 scroll down /small button down

But the side buttons are mapped to scrolling up/down and mousewheel up/down is set to leftclick/nothing.

Tick



	```
Identifier  "MX510"
   	Driver		"mouse"
	Option		"Protocol"		"evdev"
	Option		"Dev Name"		"Logitech USB-PS/2 Optical Mouse"
	Option		"Dev Phys"		"usb-*/input0"
	Option		"Device"		"/dev/input/event1"
	Option		"Buttons"		"8"
	Option		"ZAxisMapping"		"4 5"
```


```
I: Bus=0003 Vendor=046d Product=c01d Version=2100
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:10.0-1/input0
H: Handlers=mouse0 event1
B: EV=7

B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

```[/QUOTE]
Did you happen to have a xmodmap that remaps those buttons?

---

### Post by endy on 2005-10-07
Also, the mx510 has ten buttons, not eight. Here they are (in no particular order):

[LIST=1]
[*]LMB
[*]MMB
[*]RMB
[*]Scroll Up
[*]Scroll Down
[*]Scroll Up "Cruise Control" button
[*]Scroll Down "Cruise Control" button
[*]Side Forward
[*]Side Back
[*]"Alt-Tab" Button
[/LIST]
...even though the "Cruise Control" buttons duplicate the scroll up and down. Hope this helps!

---

### Post by DancingSun on 2005-10-07
[QUOTE=endy]Also, the mx510 has ten buttons, not eight. Here they are (in no particular order):

[LIST=1]
[*]LMB
[*]MMB
[*]RMB
[*]Scroll Up
[*]Scroll Down
[*]Scroll Up "Cruise Control" button
[*]Scroll Down "Cruise Control" button
[*]Side Forward
[*]Side Back
[*]"Alt-Tab" Button
[/LIST]
...even though the "Cruise Control" buttons duplicate the scroll up and down. Hope this helps![/QUOTE]
Well, I put "8" buttons on my xorg.conf and it works fine.  The correct number to put in is the highest button event number X receives.  So, basically enter the highest button event number that you see on xev.  You can put more, and your mouse will still work just fine.  But you'll be telling X to hog resources for button events that will never be generated.

---

### Post by Pulse on 2005-10-07
[QUOTE=DancingSun]Can you post your xorg.conf?  Also, did you do the Xmodmap part of the guide?  It's not needed anymore.[/QUOTE]
Sorry I took so long to reply, I didn't have access to a computer for a few days there.  

Here's the relevant part of my xorg.conf:
```
Section "InputDevice"
Identifier	"Configured Mouse"
Driver		"mouse"
Option		"Protocol"		"evdev"
Option		"Dev Name"		"B16_b_02 USB-PS/2 Optical Mouse"
Option		"Dev Phys"		"usb-0000:00:02.0-2/input0"
Option		"Device"		"/dev/input/event1"
Option		"Buttons"		"11"
Option		"ZAxisMapping"		"4 5"
EndSection
```

And no, I didn't do the Xmodmap thing.

Edit: I suppose now might be a good time to mention that I'm using Breezy.  I found this thread with the search function and didn't notice that it was in a forum dedicated to Hoary until after I had already posted.  It shouldn't make any difference in this case anyway.

---

### Post by DancingSun on 2005-10-08
[QUOTE=Pulse]Sorry I took so long to reply, I didn't have access to a computer for a few days there.  

Here's the relevant part of my xorg.conf:
```
Section "InputDevice"
Identifier	"Configured Mouse"
Driver		"mouse"
Option		"Protocol"		"evdev"
Option		"Dev Name"		"B16_b_02 USB-PS/2 Optical Mouse"
Option		"Dev Phys"		"usb-0000:00:02.0-2/input0"
Option		"Device"		"/dev/input/event1"
Option		"Buttons"		"11"
Option		"ZAxisMapping"		"4 5"
EndSection
```

And no, I didn't do the Xmodmap thing.

Edit: I suppose now might be a good time to mention that I'm using Breezy.  I found this thread with the search function and didn't notice that it was in a forum dedicated to Hoary until after I had already posted.  It shouldn't make any difference in this case anyway.[/QUOTE]
Hmm...you mentioned you did your own customizations, what are those?  Also by turning cruise control on and off, do you mean the logitech applet?  I didn't do the applet part myself and things are working just fine for me.  Could you disable the applet, and see if that helps?

Do you have any xmodmap file on the system?  How many physical buttons does the mx500 have?  Could you list them out and the corresponding button event that they generate?  I think generally the scroll buttons should generate button events 4 and 5.  If not, something might have remapped the button configurations.

---

### Post by Pulse on 2005-10-08
I just tried disabling the applet and it didn't work...  Well, it might have worked, but cruise control is on and the logitech applet seems to be the only way to turn it off.  I disable cruise control by using the command ```
logitech_applet -s 800
``` as opposed to ```
logitech_applet -s 800 -e
```

By "With my own customizations" I mean that my xbindkeys config file is as follows: ```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Page_Down]""
m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Page_Up]""
m:0x0 + b:7
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Delete]""
m:0x0 + b:8
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Home]""
m:0x0 + b:10
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[End]""
m:0x0 + b:9
```

The mx500 is identical to the mx510 other than the paint job and the maximum resolution, but I'll get the button events in a few minutes anyway.

Edit: Left mouse button is button 1, middle is button 2, right is button 3, mwheelup is 4, mwheeldown is 5, the forward side button is 6, backward is 7, the button in the middle of the mouse (I forget what it's called... the one that starts Logitech's crappy alt-tab replacement in Windows) is 8, the forward cruise control button is 10 (shouldn't it be 9?) and the backward cc button is nothing.

---

### Post by DancingSun on 2005-10-08
[QUOTE=Pulse]I just tried disabling the applet and it didn't work...  Well, it might have worked, but cruise control is on and the logitech applet seems to be the only way to turn it off.  I disable cruise control by using the command ```
logitech_applet -s 800
``` as opposed to ```
logitech_applet -s 800 -e
```

By "With my own customizations" I mean that my xbindkeys config file is as follows: ```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Page_Down]""
m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Page_Up]""
m:0x0 + b:7
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Delete]""
m:0x0 + b:8
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Home]""
m:0x0 + b:10
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[End]""
m:0x0 + b:9
```

The mx500 is identical to the mx510 other than the paint job and the maximum resolution, but I'll get the button events in a few minutes anyway.

Edit: Left mouse button is button 1, middle is button 2, right is button 3, mwheelup is 4, mwheeldown is 5, the forward side button is 6, backward is 7, the button in the middle of the mouse (I forget what it's called... the one that starts Logitech's crappy alt-tab replacement in Windows) is 8, the forward cruise control button is 10 (shouldn't it be 9?) and the backward cc button is nothing.[/QUOTE]
OK, here's the weird part, on my MX510 the cruise control buttons generate button events 4 and 5 (same as scroll wheel).  And the largest button event number generated is 8.  Try disabling all your key bindings and see if the mouse generates the correct button events.

---

### Post by Pulse on 2005-10-08
[QUOTE=DancingSun]OK, here's the weird part, on my MX510 the cruise control buttons generate button events 4 and 5 (same as scroll wheel).  And the largest button event number generated is 8.  Try disabling all your key bindings and see if the mouse generates the correct button events.[/QUOTE]
This is because you have cruise control enabled.  If I turn it on, the cc buttons generate button events 4 and 5, just like yours.  And yes, I've tried disabling the key bindings, both by having a blank config file and turning xbindkeys off altogether.

---

### Post by DancingSun on 2005-10-08
[QUOTE=Pulse]This is because you have cruise control enabled.  If I turn it on, the cc buttons generate button events 4 and 5, just like yours.  And yes, I've tried disabling the key bindings, both by having a blank config file and turning xbindkeys off altogether.[/QUOTE]
Try increasing the number of buttons setting in xorg.conf to something larger, like 15.  Then see if xev can capture all of the buttons or not.  When doing this, try not to have any of the keybindings on, and make sure no other programs are remapping the buttons.

---

### Post by endy on 2005-10-11
I'd just like to say thanks to DancingSun for helping out so much on this thread, I'm very busy right now so I can't read the forums as much as I would like. Thanks alot!

---

### Post by DancingSun on 2005-10-11
[QUOTE=endy]I'd just like to say thanks to DancingSun for helping out so much on this thread, I'm very busy right now so I can't read the forums as much as I would like. Thanks alot![/QUOTE]
Hey, not a problem! That's what a community is all about!:)

---

### Post by zenrox on 2005-10-11
works for the logitech lx 500 wireless desktop
and the mouse only has the std buttons on it +1 thats it
works great tho the logitech_applet works too
main reasion why i did this was to get the better res for my mouse:p

---

### Post by Brando569 on 2005-10-13
any idea on how to get the (extra) buttons to work on the logitech elite keyboard with a media player (mainly play/pause,stop,skip back and skip forward)

---

### Post by BLTicklemonster on 2005-10-14
I've got an mx 310. My keys for forward and back are 6 and 7. I followed the instructions exactly, and they worked great! Until I set xbindkeys in start programs. I restarted, and now not only do they not work, but it took out another program that was in start up that was working fine before. It was order 50, xbindkeys was 51.

I've gone through twice and it does the same each time.

Not sure where to go from here, but I'll show you what I did:

```
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"		"/dev/input/mice"
#	Option		"Protocol"		"ImPS/2"
#	Option		"Emulate3Buttons"	"true"
#	Option		"ZAxisMapping"		"4 5"
#EndSection

Section "InputDevice"
        Identifier	"Configured Mouse"
        Driver		"mouse"
	Option		"Protocol"		"evdev"
	Option		"Dev Name"		"Logitech USB-PS/2 Optical Mouse"
	Option		"Dev Phys"		"usb-0000:00:02.1-2/input0" [COLOR="Red"](tried both ways)[/COLOR]
        Option		"Device"		"/dev/input/event2"
	Option		"Buttons"		"8"
	Option		"ZAxisMapping"		"4 5"
EndSection
```

```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
  m:0x0 + b:7
```


What do I do now? 

Huh, I wonder what changing this
Option		"Emulate3Buttons"	"true"

to this
Option		"Emulate8Buttons"	"true"

and leaving 
"Buttons"		"8"
out would do?

Oh, might be perhaps... my scroll will push down, I'm counting that as a button, so 

not in order, 

1. right click
2. left click
3. scroll up
4. scroll down
5. forward
6. back
7. wierd little button behind the scroll that I never figured out
8. pressing the scroll button down

Now you said that you could enter a higher number and it would be okay, but would use extra resources so I don't think counting number 8 should be a problem.

Suggestions?

---

### Post by DancingSun on 2005-10-15
[QUOTE=BLTicklemonster]I've got an mx 310. My keys for forward and back are 6 and 7. I followed the instructions exactly, and they worked great! Until I set xbindkeys in start programs. I restarted, and now not only do they not work, but it took out another program that was in start up that was working fine before. It was order 50, xbindkeys was 51.

I've gone through twice and it does the same each time.

Not sure where to go from here, but I'll show you what I did:

```
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"		"/dev/input/mice"
#	Option		"Protocol"		"ImPS/2"
#	Option		"Emulate3Buttons"	"true"
#	Option		"ZAxisMapping"		"4 5"
#EndSection

Section "InputDevice"
        Identifier	"Configured Mouse"
        Driver		"mouse"
	Option		"Protocol"		"evdev"
	Option		"Dev Name"		"Logitech USB-PS/2 Optical Mouse"
	Option		"Dev Phys"		"usb-0000:00:02.1-2/input0" [COLOR="Red"](tried both ways)[/COLOR]
        Option		"Device"		"/dev/input/event2"
	Option		"Buttons"		"8"
	Option		"ZAxisMapping"		"4 5"
EndSection
```

```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
  m:0x0 + b:7
```


What do I do now? 

Huh, I wonder what changing this
Option		"Emulate3Buttons"	"true"

to this
Option		"Emulate8Buttons"	"true"

and leaving 
"Buttons"		"8"
out would do?

Oh, might be perhaps... my scroll will push down, I'm counting that as a button, so 

not in order, 

1. right click
2. left click
3. scroll up
4. scroll down
5. forward
6. back
7. wierd little button behind the scroll that I never figured out
8. pressing the scroll button down

Now you said that you could enter a higher number and it would be okay, but would use extra resources so I don't think counting number 8 should be a problem.

Suggestions?[/QUOTE]
Ok, you said everything work fine until you did the key bindings.  That means the problem lies in the key bindings.

First, revert your xorg.conf to what it was like before you did the key bindings.  You might want to disable the key bindings so you can make sure the mouse is working correctly.

Second, in the xbindkeys file, replace "left" and "right" with "Left" and "Right".  A few posts ago, a forumer had this problem, and finally found out it was due to the capitalization.  The reason that it is all in lowercase in the guide is actually a bug of this forum software.  Try typing "Right" in "[]" (brackets), you'll see it being coverted to all lowercase if you preview or submit the post.

---

### Post by BLTicklemonster on 2005-10-15
Totall oddity (2005 A Linux Oddity). Left the machine on last night, got up, got myself a cup o' joe, sat down to see if I could find out how to burn a cd, navigating the site, and automatically hit the back button like I always do, and it went back. .... um.

So I'll keep an eye on it, and try what you said. Thanks.


*edit:

Ooookay, restarted, the mouse buttons work fine.


**edit:

Alllrighty then. Just finished out the entire thing. got the applet going. My mouse is now a little speed demon. Thank you thank you thank you. MrBond watch out, Here I Come. :razz:

---

### Post by ember on 2005-10-16
Hmm ... I tried this howto and my thumb-buttons just do not seem to work. They do not even send events (I have a Logitech MX310).

The relevant configuration part is:
Section "InputDevice"
	Identifier	"Logitech MX310"
	Driver		"mouse"
	Option		"Protocol"		"evdev"
	Option		"Dev Name"		"PS2++ Logitech MX Mouse"
	Option		"Dev Phys"		"isa*/input0"
	Option		"Device"		"/dev/input/event1"
	Option		"Button"		"7"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection

Any ideas?

---

### Post by BLTicklemonster on 2005-10-16
[QUOTE=ember]Hmm ... I tried this howto and my thumb-buttons just do not seem to work. They do not even send events (I have a Logitech MX310).

The relevant configuration part is:
Section "InputDevice"
	Identifier	"Logitech MX310"
	Driver		"mouse"
	Option		"Protocol"		"evdev"
	Option		"Dev Name"		"PS2++ Logitech MX Mouse"
	Option		"Dev Phys"		"isa*/input0"
	Option		"Device"		"/dev/input/event1"
	Option		"Button"		"7"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection

Any ideas?[/QUOTE]


Mine is working perfectly now. Try my settings, as we have the same mouse.

---

### Post by jadugarr on 2005-10-16
I tried this guide to setup my mx510 mouse in Kubuntu Breezy.  After changing the xorg.conf file I couldn't start X and had no relevant errors, and had to revert to my old config.  
Here is what i tried: 
```
#Section "InputDevice"
	#Identifier	"Configured Mouse"
	#Driver		"mouse"
	#Option		"CorePointer"
	#Option		"Device"		"/dev/input/mice"
	#Option		"Protocol"		"ExplorerPS/2"
	#Option		"Buttons"		"7"
	#Option		"ZAxisMapping"		"6 7"
#EndSection


Section "InputDevice"
      Identifier      "Configured Mouse"
      Driver          "mouse"
      Option          "Protocol"              "evdev"
      Option          "Dev Name"           "Logitech USB-PS/2 Optical Mouse"
      Option          "Dev Phys" 	    "usb-*/input0"
      Option          "Device"   		    "/dev/input/event1"
      Option          "Buttons"               "10"
      Option          "ZAxisMapping"       "4 5"
EndSection
```

Anyone have any suggestions?

---

### Post by DancingSun on 2005-10-16
[QUOTE=jadugarr]I tried this guide to setup my mx510 mouse in Kubuntu Breezy.  After changing the xorg.conf file I couldn't start X and had no relevant errors, and had to revert to my old config.  
Here is what i tried: 
```
#Section "InputDevice"
	#Identifier	"Configured Mouse"
	#Driver		"mouse"
	#Option		"CorePointer"
	#Option		"Device"		"/dev/input/mice"
	#Option		"Protocol"		"ExplorerPS/2"
	#Option		"Buttons"		"7"
	#Option		"ZAxisMapping"		"6 7"
#EndSection

Section "InputDevice"
      Identifier      "Configured Mouse"
      Driver          "mouse"
      Option          "Protocol"              "evdev"
      Option          "Dev Name"           "Logitech USB-PS/2 Optical Mouse"
      Option          "Dev Phys" 	    "usb-*/input0"
      Option          "Device"   		    "/dev/input/event1"
      Option          "Buttons"               "10"
      Option          "ZAxisMapping"       "4 5"
EndSection
```

Anyone have any suggestions?[/QUOTE]
Check your xorg log under /var/log, and see if there's any error output there.

---

### Post by anonOmus on 2005-10-18
I cant seem to get the libXaw3d, from any of the sources including the hoary disto servers(im running breezy) any ideas?

---

### Post by BLTicklemonster on 2005-10-18
I had to do this all again, thanks to me messing up xserver. I didn't even have to set the extra buttons. It did it for me already this time. I did notice that some of the information I culled initially was slightly different this time, which I thought was odd.

But hey, it works. thanks!

---

### Post by .Danny on 2005-10-19
I've done all the steps now and everything works apart from forward/backward in nautilus/firefox. Which is why I did it in the first place.:(

I've got a Logitech MX510, anyone has any ideas what I did wrong?

---

### Post by DancingSun on 2005-10-19
[QUOTE=Lord Death]I've done all the steps now and everything works apart from forward/backward in nautilus/firefox. Which is why I did it in the first place.:(

I've got a Logitech MX510, anyone has any ideas what I did wrong?[/QUOTE]
Without additional info, nope!  Does xev show any events generated by the thumb buttons?  Let us know if there are any step that you aren't sure of, or think where it might be the problem.

---

### Post by .Danny on 2005-10-19
Nope I've done everything that was there. Didn't get any errors or anything wrong.

This is the xev output for the 2 buttons.

```
LeaveNotify event, serial 29, synthetic NO, window 0x3a00001,
    root 0x133, subw 0x0, time 12312774, (168,177), root:(186,249),
    mode NotifyGrab, detail NotifyAncestor, same_screen YES,
    focus NO, state 0

EnterNotify event, serial 29, synthetic NO, window 0x3a00001,
    root 0x133, subw 0x0, time 12313094, (168,177), root:(186,249),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
    focus NO, state 0

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  51  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

LeaveNotify event, serial 29, synthetic NO, window 0x3a00001,
    root 0x133, subw 0x0, time 12314502, (168,177), root:(186,249),
    mode NotifyGrab, detail NotifyAncestor, same_screen YES,
    focus NO, state 0

EnterNotify event, serial 29, synthetic NO, window 0x3a00001,
    root 0x133, subw 0x0, time 12314830, (168,177), root:(186,249),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
    focus NO, state 0

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  51  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

```

---

### Post by DancingSun on 2005-10-19
[QUOTE=Lord Death]Nope I've done everything that was there. Didn't get any errors or anything wrong.

This is the xev output for the 2 buttons.

```
LeaveNotify event, serial 29, synthetic NO, window 0x3a00001,
    root 0x133, subw 0x0, time 12312774, (168,177), root:(186,249),
    mode NotifyGrab, detail NotifyAncestor, same_screen YES,
    focus NO, state 0

EnterNotify event, serial 29, synthetic NO, window 0x3a00001,
    root 0x133, subw 0x0, time 12313094, (168,177), root:(186,249),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
    focus NO, state 0

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  51  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

LeaveNotify event, serial 29, synthetic NO, window 0x3a00001,
    root 0x133, subw 0x0, time 12314502, (168,177), root:(186,249),
    mode NotifyGrab, detail NotifyAncestor, same_screen YES,
    focus NO, state 0

EnterNotify event, serial 29, synthetic NO, window 0x3a00001,
    root 0x133, subw 0x0, time 12314830, (168,177), root:(186,249),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
    focus NO, state 0

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  51  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

```[/QUOTE]
Ok, it doesn't look like it captured any button events.  Did you do the key bindings part?  If so, in the xbindkeys file, replace "left" and "right" with "Left" and "Right". A few posts ago, a forumer had this problem, and finally found out it was due to the capitalization. The reason that it is all in lowercase in the guide is actually a bug of this forum software. Try typing "Right" in "[]" (brackets), you'll see it being coverted to all lowercase if you preview or submit the post.

---

### Post by .Danny on 2005-10-19
Nope still doesn't work, altough the xev output changed.

```
LeaveNotify event, serial 29, synthetic NO, window 0x3400001,
    root 0x133, subw 0x0, time 649244, (177,140), root:(261,280),
    mode NotifyGrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 0

KeyPress event, serial 29, synthetic YES, window 0x3400001,
    root 0x133, subw 0x0, time 0, (1,1), root:(1,1),
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic YES, window 0x3400001,
    root 0x133, subw 0x0, time 0, (1,1), root:(1,1),
    state 0x8, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes:

EnterNotify event, serial 29, synthetic NO, window 0x3400001,
    root 0x133, subw 0x0, time 650012, (177,140), root:(261,280),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 0

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  51  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

LeaveNotify event, serial 29, synthetic NO, window 0x3400001,
    root 0x133, subw 0x0, time 650748, (177,140), root:(261,280),
    mode NotifyGrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 0

KeyPress event, serial 29, synthetic YES, window 0x3400001,
    root 0x133, subw 0x0, time 0, (1,1), root:(1,1),
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic YES, window 0x3400001,
    root 0x133, subw 0x0, time 0, (1,1), root:(1,1),
    state 0x8, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes:

EnterNotify event, serial 29, synthetic NO, window 0x3400001,
    root 0x133, subw 0x0, time 651452, (177,140), root:(261,280),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 0

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  51  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

```


This is my xbindkeysrc..

```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7
```

[edit with big Left and Right that is..]

---

### Post by DancingSun on 2005-10-19
I still don't see any button events in your xev output.  Basically, if you point in the xev window, without moving the mouse, click on the thumb buttons, and no button events are outputted on the terminal (button event captures are shown in the guide), that means the button is not working.

Try disabling the Logitech applet, restart, and see if the mouse works correctly.  If it does, something is wrong with the applet.  If not, try the following.

Try disabling the xbindkey, restart, and see if the mouse performs correctly. If the mouse performs correctly, then something must be wrong with the xbindkey configuration.  If not, that means most likely your xorg.conf is configured incorrectly.  Make sure you are entering the correct information for your mouse.

---

### Post by .Danny on 2005-10-19
I disabled xbindkey and the buttons show correctly in xev now. The question is what is a good whats wrong with my .xbindkeysrc then?

```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7
```

[edit] I just noticed that with xbindkey disabled it's actually working in Firefox now. It would be nice to have it Nautilus as well but Firefox is the main thing why I wanted it. So I guess things are ok. :D

---

### Post by DancingSun on 2005-10-19
[QUOTE=Lord Death]I disabled xbindkey and the buttons show correctly in xev now. The question is what is a good whats wrong with my .xbindkeysrc then?

```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7
```

[edit] I just noticed that with xbindkey disabled it's actually working in Firefox now. It would be nice to have it Nautilus as well but Firefox is the main thing why I wanted it. So I guess things are ok. :D[/QUOTE]
What button event numbers did the thumb buttons generate?

---

### Post by .Danny on 2005-10-20
[QUOTE=DancingSun]What button event numbers did the thumb buttons generate?[/QUOTE]
6 and 7.

---

### Post by BLTicklemonster on 2005-10-20
Hey, do this:

"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
  m:0x0 + b:
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
  m:0x0 + b:

and then see if the buttons don't automagically start working.

If not, delete it all and save it blank and try it that way.

It worked for me the second time around. I can't explain it, because the first time they worked with the numbers entered. I don't remember if it was no numbers or blank which worked for me, and I'm not in front of my machine, but try it and see if it works for you.

---

### Post by souled on 2005-10-21
I have the same problem as Lord Death. In xev I get buttons 6 and 7 as the thumbs, but when i load xbindkeys I get that weird output for the thumb buttons. When I set the mouse buttons to "4 5" the thumb buttons didn' do antyhing, so I changed it to "9 10" and did the xmodmap thing and now the thumb buttons work. Back and forward work for FF, but xbindkeys seem to kill the thumb buttons

Running Breezy with the mx700.

---

### Post by DancingSun on 2005-10-21
[QUOTE=souled]I have the same problem as Lord Death. In xev I get buttons 6 and 7 as the thumbs, but when i load xbindkeys I get that weird output for the thumb buttons. When I set the mouse buttons to "4 5" the thumb buttons didn' do antyhing, so I changed it to "9 10" and did the xmodmap thing and now the thumb buttons work. Back and forward work for FF, but xbindkeys seem to kill the thumb buttons

Running Breezy with the mx700.[/QUOTE]
I'm assuming when you said setting the mouse buttons to "4 5" you actually meant setting the scroll buttons to "4 5".   And what's the "weird output for thumb buttons" you're getting?

Without any xmodmap and xbindkey, what butten event numbers did xev report for your scroll wheel?

Also, for reference, you might want to search this thread, I remember some users of MX700 posting their xorg.conf settings.

Generally, I would not suggest the use of xvkbd + xbindkeys to get nautilus working with the thumb buttons.  Xbindkeys just send shell commands whenever you press the thumb buttons.  Those commands are set in your xbinkey config file, in this case, we tell it to send a command that executes xvbd (the X virtual keyboard) program to input Alt+Left and Alt+Right. That's just a work around, it doesn't change the fact that nautilus does not support the thumb buttons natively.  The best solution would be to request a feature for nautilus to support additional button events.

---

### Post by prelude on 2005-10-21
say..  anyone know of a repo that has the xvkbd package for breezy?

for some reason apt-get claims it cant find that package and without it Im kinda stuck withouth tumb buttons.. ;)

---

### Post by DancingSun on 2005-10-21
[QUOTE=prelude]say..  anyone know of a repo that has the xvkbd package for breezy?

for some reason apt-get claims it cant find that package and without it Im kinda stuck withouth tumb buttons.. ;)[/QUOTE]
The thumb buttons work without doing any key bindings (or more accurately, command bindings).  After you finished the first part of the guide (xorg.conf setup), the thumb buttons should start working.  You should be able to see them generate button events in xev, and work in Firefox, and other programs that support thumb buttons.

---

### Post by anonOmus on 2005-10-23
Oopsie!

---

### Post by Donza on 2005-10-25
Ok.. this doesn't work on my laptop. If I try to boot without Logitech mouse plugged in the X-server cannot start because it can't for some reason find my touchpad anymore. With Logitech plugged in both my mouse and touchpad works fine.
My xorg.conf:
```
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"		"/dev/input/mice"
#	Option		"Protocol"		"ImPS/2"
#	Option		"Emulate3Buttons"	"true"
#	Option		"ZAxisMapping"		"4 5"
#EndSection

Section "InputDevice"
        Identifier	"Configured Mouse"
        Driver		"mouse"
	Option		"Protocol"		"evdev"
	Option		"Dev Name"		"Logitech USB-PS/2 Optical Mouse"
	Option		"Dev Phys"		"usb-0000:00:1d.1-1/input0"
        Option		"Device"		"/dev/input/event1"
	Option		"Buttons"		"10"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection
```

---

### Post by Sheytan on 2005-10-27
[quote=Mais]The mx518 supports up to 1600 dpi resolution. Is there anyway to get this working in gnome?[/quote]

I think it already works when you push the + and - button on the mouse pointer goes faster or slower

---

### Post by jacknel on 2005-10-29
hey guys, hope i haven't missed what i'm about to ask...

but ive been using ubuntu for the last few days now and things are running pretty well...

just wandering though in regards to the MXDUO - has anyone been able to get all the buttons to work?

i have followed this guide

[http://docs.tenshu.net/Logitech-MX-Duo-mini-HOWTO/](http://docs.tenshu.net/Logitech-MX-Duo-mini-HOWTO/)

and have got scroll and side buttons to work - what DOESNT work is the 3 small buttons (1 above and 2 below scroll wheell).

Also is there a way to do AUTO scroll for the middle mouse button like in windows?

thx

---

### Post by DancingSun on 2005-10-29
[QUOTE=jacknel]hey guys, hope i haven't missed what i'm about to ask...

but ive been using ubuntu for the last few days now and things are running pretty well...

just wandering though in regards to the MXDUO - has anyone been able to get all the buttons to work?

i have followed this guide

[http://docs.tenshu.net/Logitech-MX-Duo-mini-HOWTO/](http://docs.tenshu.net/Logitech-MX-Duo-mini-HOWTO/)

and have got scroll and side buttons to work - what DOESNT work is the 3 small buttons (1 above and 2 below scroll wheell).

Also is there a way to do AUTO scroll for the middle mouse button like in windows?

thx[/QUOTE]
Well, I have a MX510 and all of my buttons work.  Although I used the guide in linux-gamers.net, it's basically the same as the first part of the guide posted here.  Actually, with all the forumer contributions, I think the guide here is more accurate and informative than the one posted on linux-gamers.net.

On my mouse, the cruise buttons are basically recognized as the scroll wheel.  And the application switch button works as well, if you use xev (refer to the guide) you can see it generate button events, and I can use it in games to bind it to certain commands.

Auto scroll will work in Firefox if you enable it in Firefox. Go to the menu Edit -> Preferences -> Advanced.  Under "Browsing" category check "Use autoscrolling".

---

### Post by jacknel on 2005-10-30
thx for the DancingSun, autoscroll is cool - can u tell me how i might be able to make that a global thing? like for text and such as well...?


I gotta say - I haven't used XP at all today - my only concern about making the switch is outlook on XP, hate the task of learning how to Export/import my messages and such..

Secondly...

any idea how i can do the following - ?

change the top scroll button (09) to Alt+F4, lower scroll button (10) to Ctrl+W and well u get the idea... i read stuff here

[http://hocwp.free.fr/xbindkeys/](http://hocwp.free.fr/xbindkeys/)
[http://homepage3.nifty.com/tsato/xvkbd/](http://homepage3.nifty.com/tsato/xvkbd/)

but don't really have much of an idea...

thx again

---

### Post by DancingSun on 2005-10-30
[QUOTE=jacknel]thx for the DancingSun, autoscroll is cool - can u tell me how i might be able to make that a global thing? like for text and such as well...?[/QUOTE]
Auto-scroll on works if the application supports it.  I remember that's the way it works in Win2K as well.  I don't know if any other application that supports auto scroll, but then again, I'm a recent Linux convert, so my experience is limited as well.

> I gotta say - I haven't used XP at all today - my only concern about making the switch is outlook on XP, hate the task of learning how to Export/import my messages and such..
I don't use outlook, I just use my web mail, so can't help you there.  But you should read some documentation on Evolution.  It should be able to import mail from Outlook, as Evolution is made to look and work like Outlook, so that it can be its replacement on Linux.

> Secondly...

any idea how i can do the following - ?

change the top scroll button (09) to Alt+F4, lower scroll button (10) to Ctrl+W and well u get the idea... i read stuff here

[http://hocwp.free.fr/xbindkeys/](http://hocwp.free.fr/xbindkeys/)
[http://homepage3.nifty.com/tsato/xvkbd/](http://homepage3.nifty.com/tsato/xvkbd/)

but don't really have much of an idea...

thx again

Well, like I said before, on my Logitech MX510, the button events generated by the cruise buttons are the same as the butten events generated by the scroll wheel.  Which means the X.org server (the windowing system) will recognize the cruise up button as the scroll up action, and the cruise down button as the scroll down action.

That means, if I bind the cruise buttons to some command, the scroll wheel actions will also be bind to those same commands.  Assuming your mouse works the same way as mine, I don't think you'll want that to happen.

---

### Post by jacknel on 2005-10-30
oh i get it now.... i just checked events thing and you're kinda right... EG my scroll is 4 and 5 i think and my top button is 4 then when u release it's10... odd....


any idea how i can use those tools i posted to change the bottom one (not sure abt the 510, but the 700 has another button below the one below the scroll which is used to select apps in windows)

---

### Post by DancingSun on 2005-10-30
[QUOTE=jacknel]oh i get it now.... i just checked events thing and you're kinda right... EG my scroll is 4 and 5 i think and my top button is 4 then when u release it's10... odd....


any idea how i can use those tools i posted to change the bottom one (not sure abt the 510, but the 700 has another button below the one below the scroll which is used to select apps in windows)[/QUOTE]
Well, I don't use xbindkey and xvkbd at all, I think when I used it last time it gave me some unexpected results.  Can't quite remember the details.

But if you look at the guide in this thread, you'll see the instructions where it teaches you how to bind Alt+Left and Alt+Right keystrokes to the thumb buttons.  Similarly, after you get some basic understanding on how to assign the keystrokes, you could just change the button that trigger the commands and the commands itself to whatever you desire.  

For example, the guide tells you to assigned button 6 and 7, in the xbindkey configuration file it appears that "b:6" and "b:7" are references to those buttons.  I believe that the button numbers follow the butten event numbers that those buttons generate.  So, if I'm correct, you should be able to assign button 10 (since that's the button event number generated when you release the cruise up button, this doesn't happen on my mouse however, both press and release all generates button 4 events) to some other keystroke combinations.  To assign the switch application button, just assign the button event number that it generates to the corresponding command you want to invoke.  On my mouse, that would be button 8.

There's catch with all this button binding though, I think you cannot specify which programs in which certain bindings will work in.  So that means whatever program you're working with, when you press those binded buttons, the associated commands will execute.  This poses a problem when I want to map the extra buttons to in-game commands when I play my favorate computer games.  For example, if I mapped Alt+F4 to my switch application button, when I try to map that button to some other commands in a game, it will type in the keystrokes of Alt+F4 instead of indicating that the command is mapped to button 8.

---

### Post by humina on 2005-10-31
I have a logitech g5 laser mouse.  I have two problems.  The first is that my mouse can go up to 2000 dpi.  Id there any way to get past the 800 dpi limit?  Also xev gives buttons 4 and 5 to both my scroll wheel and my tilt wheel.  Any way to separate them?

---

### Post by Doc.Caliban on 2005-10-31
[QUOTE=endy]
```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7
```[/QUOTE]

Great How To, thanks!

What would the Page Up and Page Down equivelents to "\[Alt_L]\[Left]" and "\[Alt_L]\[Right]" be?

-Doc

---

### Post by Doc.Caliban on 2005-10-31
[QUOTE=Doc.Caliban]Great How To, thanks!

What would the Page Up and Page Down equivelents to "\[Alt_L]\[Left]" and "\[Alt_L]\[Right]" be?

-Doc[/QUOTE]


Got it.  Here is my config file set up the way I like it.  Button 8 is the bottom button in the wheel area.  

```

"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Page_Down]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Page_Up]""
  m:0x0 + b:7
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Home]""
  m:0x0 + b:8

```

Thanks again for the great guide!

-Doc

---

### Post by Tomas_B on 2005-11-01
I've got the MX1000 and I've had some problems getting it to work.

First of all : Not using xmodmap and just setting "ZAxisMapping" "4 5" does NOT work with the MX1000 (at least not for me)

Second : After setting the ~/.xmodmap file as I wanted it nothing happened. Found out that xvkbd wasn't in the path by default !

Now it works in both Firefox and Nautilus !! So I thought I would post some of my config for other MX1000 owners to see :

/etc/X11/xorg.conf :
```

Section "InputDevice"
         Identifier "MX1000"
         Driver     "mouse"
         Option     "CorePointer"
         Option     "Protocol"        "evdev"
         Option     "Dev Name"        "Logitech USB RECEIVER"
         Option     "Buttons"         "12"
         Option     "ZAxisMapping"    "11 12 10 9"
         Option     "Resolution"      "800"
         Option     "Emulate3Buttons" "no"
EndSection

```

/etc/gdm/PostLogin/Default
```

xmodmap -e "pointer = 1 2 3 6 7 8 11 12 9 10 4 5"

```

~/.gnomerc
```

# Lets start xbindkeys
xbindkeys

```

~/.xbindkeys
```

# Backward and Forward buttons
"xvkbd -text "\[Alt_L]\[Left]""
m:0x10 + b:6
"xvkbd -text "\[Alt_L]\[Right]""
m:0x10 + b:7

# Application-Switch button
# A-Tab doesn't work
# Use it as another Forward for now
"xvkbd -text "\[Alt_L]\[Right]""
m:0x10 + b:8

```

Thats it !!

Note : With xbindkeys running it seems like the Alt + Left combo is activated just a little too long for Firefox because FF keeps "scrolling" back through the history of webpages you have visited in the past sometimes. "killall xbindkeys" solves that problem, but then it won't work in Nautilus.

---

### Post by Rev. Nathan on 2005-11-09
Say, this worked out greatly! Sort of. Umm... for some odd reason I didn't have to install xvkbd and xbindkeys, and the back and forward buttons worked. However, I have another problem; the middle-click 'scroller' doesn't show up. That little graphic circle that comes on and helps you coast along webpages. Any idea as to what I can do to activate it?

---

### Post by DancingSun on 2005-11-09
[QUOTE=Rev. Nathan]Say, this worked out greatly! Sort of. Umm... for some odd reason I didn't have to install xvkbd and xbindkeys, and the back and forward buttons worked. However, I have another problem; the middle-click 'scroller' doesn't show up. That little graphic circle that comes on and helps you coast along webpages. Any idea as to what I can do to activate it?[/QUOTE]
Please refer to [this]("http://ubuntuforums.org/showpost.php?p=453371&postcount=111") post.

---

### Post by Rev. Nathan on 2005-11-09
[QUOTE=DancingSun]Please refer to [this]("http://ubuntuforums.org/showpost.php?p=453371&postcount=111") post.[/QUOTE]
Aww yes! Thank very much sir.

---

### Post by jonyo on 2005-11-13
[QUOTE=humina]I have a logitech g5 laser mouse.  I have two problems.  The first is that my mouse can go up to 2000 dpi.  Id there any way to get past the 800 dpi limit?  Also xev gives buttons 4 and 5 to both my scroll wheel and my tilt wheel.  Any way to separate them?[/QUOTE]

I have the MX 1000, and was having the same issue.  I found out, if you comment out the ZAxisMapping part, and put 15 for the buttons, then xev will show the tilt left and right, and the scroll up and down not at all.  So then I changed ZAxisMapping to "4 5 10 11" to see what happens, now scrolling uses 4 and 5, and tilting uses 9 and 10.

So with these settings:
```

Section "InputDevice"
        Identifier	"Configured Mouse"
        Driver		"mouse"
	Option		"Protocol"		"evdev"
	Option		"Dev Name"		"Logitech USB Receiver"
	Option		"Dev Phys"		"usb-0000:00:02.0-1/input0"
        Option		"Device"		"/dev/input/event1"
	Option		"Buttons"		"12"
	Option		"ZAxisMapping"		"4 5 9 10"
EndSection

```
result in this mapping:
Left Button = 1
Middle = 2
Right = 3
Scroll up = 4
Scroll down = 5
cruise up = 4
cruise down = 5
Back Thumb Button = 6
Forward Thumb Button = 7
Change App button = 8
Tilt Right= 9
Tilt Left = 10

So now I can scroll up and down, middle click, go back and forward in firefox, but I can't figure out how to change apps or get the tilt to make it go to the left and right...

I tried using the map keys thing to change aps, but all that did for the app switcher is send alt tab to the window, not to the windows manager, so the actual active window ended up having a tab entered.  Is there a way to make the system interpret the keystroke, and not the focused window?

I don't know where to begin to figure out the tilt button mapping...  Like I said it is recognizing it seperately from the scroll up and down, but button 9 and 10 don't get translated into scrolling left and right, and I don't know how to get it to.  The obvious way is to map it to left and right keys, but it seems there should be a better way to do it?

---

### Post by DancingSun on 2005-11-13
[QUOTE=jonyo]I have the MX 1000, and was having the same issue.  I found out, if you comment out the ZAxisMapping part, and put 15 for the buttons, then xev will show the tilt left and right, and the scroll up and down not at all.  So then I changed ZAxisMapping to "4 5 10 11" to see what happens, now scrolling uses 4 and 5, and tilting uses 9 and 10.

So with these settings:
```

Section "InputDevice"
        Identifier	"Configured Mouse"
        Driver		"mouse"
	Option		"Protocol"		"evdev"
	Option		"Dev Name"		"Logitech USB Receiver"
	Option		"Dev Phys"		"usb-0000:00:02.0-1/input0"
        Option		"Device"		"/dev/input/event1"
	Option		"Buttons"		"12"
	Option		"ZAxisMapping"		"4 5 9 10"
EndSection

```
result in this mapping:
Left Button = 1
Middle = 2
Right = 3
Scroll up = 4
Scroll down = 5
cruise up = 4
cruise down = 5
Back Thumb Button = 6
Forward Thumb Button = 7
Change App button = 8
Tilt Right= 9
Tilt Left = 10

So now I can scroll up and down, middle click, go back and forward in firefox, but I can't figure out how to change apps or get the tilt to make it go to the left and right...

I tried using the map keys thing to change aps, but all that did for the app switcher is send alt tab to the window, not to the windows manager, so the actual active window ended up having a tab entered.  Is there a way to make the system interpret the keystroke, and not the focused window?

I don't know where to begin to figure out the tilt button mapping...  Like I said it is recognizing it seperately from the scroll up and down, but button 9 and 10 don't get translated into scrolling left and right, and I don't know how to get it to.  The obvious way is to map it to left and right keys, but it seems there should be a better way to do it?[/QUOTE]
In reguards to mapping the tilt buttons, have you tried just mapping it to "Left" and "Right" keystrokes?

---

### Post by jonyo on 2005-11-13
[QUOTE=DancingSun]In reguards to mapping the tilt buttons, have you tried just mapping it to "Left" and "Right" keystrokes?[/QUOTE]

I've already tried it, and it works ok.  I was just wondering if there was a way to do it without mapping it to keystrokes, I'd rather do it the "proper" way if such a way exists...

About the application switching...  after thinking about it I remember reading something mentioned on these forums somewhere, but now I can't find it.  Anyone know of a howto somewhere that says how to set up app switching?

UPDATE:  I was playing with it some more, and I set the number of buttons to 20...  Now when tilt right, on key release it says button 120...  How is it possible that it's reporting button 120 if my max is 20?  By the way, my cruise up and down do button 11 and 12 on key release... I didn't mention that before.

---

### Post by souled on 2005-11-13
Hmmm... When I run xbindkeys, button 6 and 7 stop working. Here is the output from xev when xbindkeys is running:
```

MotionNotify event, serial 29, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x2c00002, time 635499, (52,52), root:(56,121),
    state 0x10, is_hint 0, same_screen YES

MotionNotify event, serial 29, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x2c00002, time 635507, (53,52), root:(57,121),
    state 0x10, is_hint 0, same_screen YES

MotionNotify event, serial 29, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x2c00002, time 635515, (65,52), root:(69,121),
    state 0x10, is_hint 0, same_screen YES

EnterNotify event, serial 29, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x0, time 635523, (75,54), root:(79,123),
    mode NotifyNormal, detail NotifyInferior, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  72  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

And

LeaveNotify event, serial 29, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x2c00002, time 670473, (62,62), root:(895,229),
    mode NotifyGrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 16

KeyPress event, serial 29, synthetic YES, window 0x2c00001,
    root 0x48, subw 0x0, time 0, (1,1), root:(1,1),
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic YES, window 0x2c00001,
    root 0x48, subw 0x0, time 0, (1,1), root:(1,1),
    state 0x8, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes:

EnterNotify event, serial 29, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x2c00002, time 671097, (62,62), root:(895,229),
    mode NotifyUngrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  72  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

For the other button.
```

However, when xbindkeys is not running, buttons 6 and 7 work. Here is the output of xev when xbindkeys is not running: 
```

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  72  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

ButtonRelease event, serial 30, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x2c00002, time 761612, (33,42), root:(866,209),
    state 0x10, button 6, same_screen YES

LeaveNotify event, serial 30, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x0, time 761612, (33,42), root:(866,209),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

ButtonPress event, serial 30, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x2c00002, time 761732, (33,42), root:(866,209),
    state 0x10, button 6, same_screen YES

EnterNotify event, serial 30, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x0, time 761732, (33,42), root:(866,209),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

And

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  72  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

ButtonRelease event, serial 30, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x2c00002, time 822497, (33,32), root:(866,199),
    state 0x10, button 7, same_screen YES

LeaveNotify event, serial 30, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x0, time 822497, (33,32), root:(866,199),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

ButtonPress event, serial 30, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x2c00002, time 826993, (33,32), root:(866,199),
    state 0x10, button 7, same_screen YES

EnterNotify event, serial 30, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x0, time 826993, (33,32), root:(866,199),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

```

I would like to get buttons 6 and 7 working in nautilus, but if I can't then oh well. Anyone have any ideas? Using an Mx700 on Breezy.

---

### Post by jonyo on 2005-11-14
[QUOTE=souled]Hmmm... When I run xbindkeys, button 6 and 7 stop working. Here is the output from xev when xbindkeys is running:
```

MotionNotify event, serial 29, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x2c00002, time 635499, (52,52), root:(56,121),
    state 0x10, is_hint 0, same_screen YES

MotionNotify event, serial 29, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x2c00002, time 635507, (53,52), root:(57,121),
    state 0x10, is_hint 0, same_screen YES

MotionNotify event, serial 29, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x2c00002, time 635515, (65,52), root:(69,121),
    state 0x10, is_hint 0, same_screen YES

EnterNotify event, serial 29, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x0, time 635523, (75,54), root:(79,123),
    mode NotifyNormal, detail NotifyInferior, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  72  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

And

LeaveNotify event, serial 29, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x2c00002, time 670473, (62,62), root:(895,229),
    mode NotifyGrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 16

KeyPress event, serial 29, synthetic YES, window 0x2c00001,
    root 0x48, subw 0x0, time 0, (1,1), root:(1,1),
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic YES, window 0x2c00001,
    root 0x48, subw 0x0, time 0, (1,1), root:(1,1),
    state 0x8, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes:

EnterNotify event, serial 29, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x2c00002, time 671097, (62,62), root:(895,229),
    mode NotifyUngrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  72  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

For the other button.
```

However, when xbindkeys is not running, buttons 6 and 7 work. Here is the output of xev when xbindkeys is not running: 
```

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  72  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

ButtonRelease event, serial 30, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x2c00002, time 761612, (33,42), root:(866,209),
    state 0x10, button 6, same_screen YES

LeaveNotify event, serial 30, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x0, time 761612, (33,42), root:(866,209),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

ButtonPress event, serial 30, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x2c00002, time 761732, (33,42), root:(866,209),
    state 0x10, button 6, same_screen YES

EnterNotify event, serial 30, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x0, time 761732, (33,42), root:(866,209),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

And

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  72  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

ButtonRelease event, serial 30, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x2c00002, time 822497, (33,32), root:(866,199),
    state 0x10, button 7, same_screen YES

LeaveNotify event, serial 30, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x0, time 822497, (33,32), root:(866,199),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

ButtonPress event, serial 30, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x2c00002, time 826993, (33,32), root:(866,199),
    state 0x10, button 7, same_screen YES

EnterNotify event, serial 30, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x0, time 826993, (33,32), root:(866,199),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

```

I would like to get buttons 6 and 7 working in nautilus, but if I can't then oh well. Anyone have any ideas? Using an Mx700 on Breezy.[/QUOTE]

I'm a newb to Ubuntu, but I'm learning fast ;)  When you run xbindkeys the forward and back keys work in nautilus, but the break everywhere else right?  This is kinda tedious but you might just make a shell script which calles xbindkeys, runs nautilus, waits for it to close, and when nautilus closes it kills xbindkeys...  Thats kinda overkill but it seems like it should work.  Also, anything else you are doing while you have nautilus open would not have working forward and back buttons...

---

### Post by souled on 2005-11-14
[QUOTE=jonyo]I'm a newb to Ubuntu, but I'm learning fast ;)  When you run xbindkeys the forward and back keys work in nautilus, but the break everywhere else right?  This is kinda tedious but you might just make a shell script which calles xbindkeys, runs nautilus, waits for it to close, and when nautilus closes it kills xbindkeys...  Thats kinda overkill but it seems like it should work.  Also, anything else you are doing while you have nautilus open would not have working forward and back buttons...[/QUOTE]

Thanks for the idea, but when xbindkeys is running, the buttons don't work in nautilus. They don't work anywhere :???:

---

### Post by jonyo on 2005-11-14
[QUOTE=souled]Thanks for the idea, but when xbindkeys is running, the buttons don't work in nautilus. They don't work anywhere :???:[/QUOTE]

What is in your .xbindkeysrc file?

---

### Post by DancingSun on 2005-11-14
[QUOTE=jonyo]I've already tried it, and it works ok.  I was just wondering if there was a way to do it without mapping it to keystrokes, I'd rather do it the "proper" way if such a way exists...

About the application switching...  after thinking about it I remember reading something mentioned on these forums somewhere, but now I can't find it.  Anyone know of a howto somewhere that says how to set up app switching?

UPDATE:  I was playing with it some more, and I set the number of buttons to 20...  Now when tilt right, on key release it says button 120...  How is it possible that it's reporting button 120 if my max is 20?  By the way, my cruise up and down do button 11 and 12 on key release... I didn't mention that before.[/QUOTE]
To have "proper" support for those additional buttons, the applications will need to support the additional button events themselves, such is the way firefox work with the thumb buttons.

You might want to submit a feature request to [www.gnome.org](www.gnome.org) for GNOME to support the thumb buttons in places where it makes sense, and allow GNOME to pickup the Application Switch button to invoke the alt-tab switcher.  It might never get implemented, but you'll never know.

---

### Post by souled on 2005-11-14
[QUOTE=jonyo]What is in your .xbindkeysrc file?[/QUOTE]

```

"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
  m:0x0 + b:7

```

Just copied what the HOWTO said.

---

### Post by DancingSun on 2005-11-14
[QUOTE=souled]```

"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
  m:0x0 + b:7

```

Just copied what the HOWTO said.[/QUOTE]
It should be noted that the "left" and "right" is intended to have capitalized first characters, as in "Left" and "Right".  However, the forum software will convert those letters to lowercase when they are enclosed in brackets.

---

### Post by teaker1s on 2005-11-14
reading the howto I have no output for scroll wheel left/right in xev which leaves me confused as I have a ps2 cordless mouse that is a logitech click!plus but identified as logitech explorer model 66 and I'm unsure if it's possibe to get an output and xbindkeys new and get key causes xbindkeys to crash

---

### Post by souled on 2005-11-14
[QUOTE=DancingSun]It should be noted that the "left" and "right" is intended to have capitalized first characters, as in "Left" and "Right".  However, the forum software will convert those letters to lowercase when they are enclosed in brackets.[/QUOTE]

Wow that did the trick! Thanks a lot.

---

### Post by maser on 2005-11-30
[QUOTE=Pulse]First of all, thanks for the guide, it's been a real help.  

I've got everything on my mx500 working with my own customizations, except for one very strange problem - the bottom "cruise control" button doesn't work if I turn cruise control off; even pressing it in xev elicits no response.  What makes this so strange is that the top cc button *does* work; it registers as button 10 in xev and works just like any other other button.

If I turn cc on, they both replicate the mousewheel as intended and both can be bound to any key in Windows with no problems, so what gives?[/QUOTE]

I had the same problem with my Logitech Cordless Optical TrackMan. The bottom cruise control button happens to be 12, and buttons 9 and 11 don't exist.

But now that the button works, I can't assign Ctrl+Shift+Tab to it with xbindkeys. I tried [Shift] and [Shift_L], but it just does a Ctrl+Tab.

Thanks for the guide! I don't think I'd still be using Ubuntu if I hadn't got the mouse buttons working!

maser

---

### Post by blitz666 on 2005-12-01
endy: I have an mx550 (basically a recolor of the MX510)... you must say the EXACT USB or it wont boot x (ie, I cant use that "usb-*/input0" you used, I had to type out the entire *.

Do you know any way to make button 8 (the app switch button) to be foreward and the default thumb side button for forward to be enter key?  How about to make the cruise move larger intervals? I am hoping to make this match the Win config I have for the same mouse.

When I say "sudo logitech_applet -s 400 -e", I get buttons 1-8 with the ccu and ccd being the same as wu and wd (this has been rehashed ad litem).
When I say "sudo logitech_applet -s 400", I get buttons 1-10 with the ccu being #10, and ccd does absolutely nothing.  Ap-switch is still 8, thumbs are 6/7, etc.

How can I make 9 appear, rather than have a bum button?

---

### Post by teaker1s on 2005-12-03
is evdev protocol usb only or can it be used with cordless ps2

---

### Post by DancingSun on 2005-12-03
[QUOTE=teaker1s]is evdev protocol usb only or can it be used with cordless ps2[/QUOTE]
It *should* work with any mouse.

---

### Post by keitsi on 2005-12-04
Anyone else having weird mouse speed problems with MX518?
[http://www.ubuntuforums.org/showthread.php?p=543013#post543013](http://www.ubuntuforums.org/showthread.php?p=543013#post543013)

---

### Post by CompShrink on 2005-12-10
Ok, I have the Mediaplay cordless mouse working for all but 2 buttons (not bad considering it has the standard 2 buttons, tilting clickable scroll whell, 6 media buttons, and forward/back(the broken) buttons)

So, I followed the directions for lmpcm driver, but only to a certain point. Basically, a slightly altered version follows:

Compilation
Get lmpcm_usb source tarball and uncompress it: # tar zxf lmpcm_usb-0.5.2.tar.gz
Now, change to the created directory, compile and install the driver: # cd lmpcm_usb-0.5.2
$ sudo make
$ sudo make install
Installation script installed lmpcm_usb.ko (lmpcm_usb.o for kernel 2.4) into /lib/modules/your-kernel-version/misc/ and added an entry to modules.dep file, using depmod.

Loading modules
Edit /lib/modules/your-kernel-version/misc/modules.dep and remove usbmouse and usbhid entries. This is required because these modules "steal" any kind of mouse, so we have to load lmpcm_usb first. If usbmouse and/or hid are required for any other device, just load them after lmpcm_usb. But don't forget, lmpcm_usb SHOULD LOAD FIRST that any generic mouse driver.
Loading support:
(these 3 commands should be unneccessary unless you removed these modules for something else)
Kernel 2.6
$ sudo modprobe usbcore
$ sudo modprobe uhci-hcd

$ sudo modprobe evdev


Ensure usbmouse and hid are not loaded:

Kernel 2.6
$ sudo rmmod usbmouse
$ sudo rmmod usbhid
$ sudo modprobe lmpcm_usb

At this time, your mouse should work. 


Ok, DO NOT DO ANYTHING MORE! If you read the official instructions from the guy who made it, you will probably screw up your system. I did, and now after a long and painstaking reverting process, I figured out, it works after this point.

Once you do the following, it works after reboot only when you execute the following in a terminal:
```
$ sudo rmmod usbhid
$ sudo rmmod lmpcm_usb
$ sudo modprobe lmpcm_usb
```
*note, after you execute the first line, you lose your mouse completely until you remove and reinitiate lmpcm_usb

I mapped the mediabuttons by:  System > Preferences > Keyboard Shortcuts 

I will update if I get the two side buttons working, and get the mouse loading automated. At least for me, if I removed usbhid completely, my mouse didn't work at all. I use them relatively frequently in windows, so I'd be nice if I could get them working. It's definately a lot more functional in Linux than it was yesterday at least.

---

### Post by Golgoth on 2005-12-10
Hi,

First of all, thanks for the how-to!

I want to add my config for a Logitech LX7 :

1) golgoth@laptop:~$ cat /proc/bus/input/devices

I: Bus=0003 Vendor=046d Product=c50e Version=2510
N: Name="Logitech USB RECEIVER"
P: Phys=usb-0000:00:1d.1-2/input0
H: Handlers=mouse1 event3 ts1
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

2) golgoth@laptop:~$ sudo gedit /etc/X11/xorg.conf

Section "InputDevice"
        Identifier    "Configured Mouse"
        Driver        "mouse"
    	Option        "Protocol"        "evdev"
    	Option        "Dev Name"        "Logitech USB RECEIVER"
    	Option        "Dev Phys"        "usb-*/input0"
        Option        "Device"        	"/dev/input/event3"
    	Option        "Buttons"        	"9"
    	Option        "ZAxisMapping"    "4 5 8 9"
	Option	      "Resolution"      "800"
EndSection

3) no .Xmodmap

4) golgoth@laptop:~$ gedit ~/.xbindkeysrc

"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:9
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:8
"gnome-terminal"
  m:0x0 + b:7
"nautilus"
  m:0x0 + b:6

5) :) :) :) :) :) :) :) :)

---

### Post by BLTicklemonster on 2005-12-11
Question:

What can be done for other mouse types? The beginnings look like they are pretty much generic. Suppose all I really worry about is getting forward and back buttons working, will the initial steps work?

(and if I change from one video card to another, why must I redo the mouse settings?)

---

### Post by Golgoth on 2005-12-12
Why is this thread in this section?

Why not move it to the general Customization Tips & Tricks instead of the hoary one?

Moreover, Endy, you should rename the title and erase "logitech" since I have installed my Microsoft Intellimouse Optical following your how-to!

Here is my settings:

1) golgoth@fixe:~$ cat /proc/bus/input/devices

I: Bus=0003 Vendor=045e Product=0039 Version=0300
N: Name="Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)"
P: Phys=usb-0000:00:0a.1-2/input0
H: Handlers=mouse1 event3 ts1
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103

2) golgoth@fixe:~$ sudo gedit /etc/X11/xorg.conf

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "Protocol" "evdev"
	Option "Dev Name" "Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)"
	Option "Dev Phys" "usb-*/input0"
	Option "Device" "/dev/input/event3"
	Option "Buttons" "7"
	Option "ZAxisMapping" "4 5"
EndSection

3) no .Xmodmap

4) golgoth@fixe:~$ gedit ~/.xbindkeysrc

"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
m:0x0 + b:7

:)

---

### Post by daedalusman on 2005-12-13
Well everything worked fine until I tried to use the logitech_applet. When I try the command you use I'm getting this error...

```
sudo logitech_applet -s 800 -e
001/003     046D/C50B   967300-0403     Cordless MX Duo Receiver
   Channel 1    Battery: 7    Single channel   No 800cpi support   No Horiz Roller   No Vert Roller   3 butt.
```

What is this all about, I have the MX Duo (MX700 mouse) with both running out of the USB port? Is something not setup right, all the mouse bottuns are working as they should so its not a major problem I just thought I would post it so everybody knows about it. Thanks for the great guide.

---

### Post by Golgoth on 2005-12-14
I have the same with a LX7 mouse...

---

### Post by Chris Tucker on 2005-12-16
mx510 here...
before changeing my xorg.conf, (By the way, about that, i had a lot of frustration without using /dev/input/mice as the "Device", it killed xorg on a lot of occasions with the other mentioned device names!)
anyway, since changeing xorg.con, the scroll up button just above my scroll wheel triggers two buttons! both 4 and 6. 

ButtonRelease event, serial 29, synthetic NO, window 0x4200001,
    root 0x4b, subw 0x0, time 178452, (166,4), root:(191,144),
    state 0x800, button 4, same_screen YES

ButtonRelease event, serial 29, synthetic NO, window 0x4200001,
    root 0x4b, subw 0x0, time 178636, (166,4), root:(191,144),
    state 0x0, button 6, same_screen YES

how could i fix this?
note: button 4 is scroll up, button 6 is the BACK button... so ... yea.. its kind of.. not useable.

---

### Post by DancingSun on 2005-12-16
[QUOTE=Chris Tucker]mx510 here...
before changeing my xorg.conf, (By the way, about that, i had a lot of frustration without using /dev/input/mice as the "Device", it killed xorg on a lot of occasions with the other mentioned device names!)
anyway, since changeing xorg.con, the scroll up button just above my scroll wheel triggers two buttons! both 4 and 6. 

ButtonRelease event, serial 29, synthetic NO, window 0x4200001,
    root 0x4b, subw 0x0, time 178452, (166,4), root:(191,144),
    state 0x800, button 4, same_screen YES

ButtonRelease event, serial 29, synthetic NO, window 0x4200001,
    root 0x4b, subw 0x0, time 178636, (166,4), root:(191,144),
    state 0x0, button 6, same_screen YES

how could i fix this?
note: button 4 is scroll up, button 6 is the BACK button... so ... yea.. its kind of.. not useable.[/QUOTE]
It's probably useful if you post your xorg.conf...it sounds like you've misconfigured the mouse to use the intellimouse/MS mouse driver or something.  I remember I had that very same problem when I configured my mouse as intellimouse (I have MX510).  The older guides will direct you to use that driver to enable the thumb buttons.

---

### Post by Chris Tucker on 2005-12-17
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "Protovol"              "evdev"
        Option          "Dev Name"              "Logitech USB-PS/2 Optical Mous$        Option          "Dev Phys"              "usb-*/input0"
        Option          "Device"                "/dev/input/mice"
        Option          "Buttons"               "8"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection
```

Note: Synaptics touchpad hasnt been configured yet.. i dont use its scroll button... the rest of that touchpad works fine.
i have tried changing the ZAxisMapping to 6 7 and it switches the forward and back buttons to different numbers, then xev shows 6 & 7 as my sroll events for my scrollwheel, and the proper button for the extra scroll down button. BUT the extra scroll up button is the same thing as pressing the back button AND scrolling up. regardless of the ZAxisMapping.

---

### Post by DancingSun on 2005-12-17
```
Option          "Dev Name"              "Logitech USB-PS/2 Optical Mous$        Option          "Dev Phys"              "usb-*/input0"
```
You merged 2 option lines into 1, plus you have that dollar sign in place of an "e" and a double quote.  This is how my mouse confirguration in xorg.conf looks like:
```
Section "InputDevice"
  Identifier	"Configured Mouse"
  Driver		"mouse"
  Option		"Dev Name"		"Logitech USB-PS/2 Optical Mouse"
  Option		"Protocol"		"evdev"
  Option		"CorePointer"
  Option		"Device"		"/dev/input/mice"
  Option		"Dev Phys"		"usb-*/input0"
  Option		"Buttons"		"8"
  Option		"ZAxisMapping"		"4 5"
EndSection
```

Edit: And you spelled "Protovol" wrong, it's suppose "Protocol".

---

### Post by Chris Tucker on 2005-12-17
[QUOTE=DancingSun]```
Option          "Dev Name"              "Logitech USB-PS/2 Optical Mous$        Option          "Dev Phys"              "usb-*/input0"
```
You merged 2 option lines into 1, plus you have that dollar sign in place of an "e" and a double quote.
Edit: And you spelled "Protovol" wrong, it's suppose "Protocol".[/QUOTE]
Oops. sorry, the line doesnt REALLY have that $ there and the Dev Phys line is a seperate line. when i copied that it was from pico, and the terminal was just a little narrow to show the whole word "Mouse""
And that typo in Protocol did it, its working great now, thanks for the help!

---

### Post by snellgrove on 2005-12-18
Hey all,

Think I may have something useful to add to this thread, as another slightly frustrated Logitech user!

I have the MX1000 (great mouse btw) and thanks to this guide, I have it working nicer than before.

But, I think the problem lies with firefox! (or nautilus)

If I have xbindkeys running, so the side-buttons on the mouse are mapped to Alt+Left, and Alt+Right nautilus runs great, I can navigate back and forward with my mouse (yay)

but firefox now pages up, and down with these buttons.

Killing xbindkeys, so the buttons are not mapped to anything... I guess, and suddenly firefox runs just fine, back/forward changes pages ! but suddenly nautilus doesn't do anything lol.

So we need a way of making firefox understand alt+Left/Right I would say?

or have I done something wrong! great guide guys though, my mouse is working nicer than before, definately something for the Wiki if its not already in there :)

:edit:

uhhhhh ignore me or something?!?!?!?   LOL suddenly I just found its all working .. dunno what the heck i've just done though :p :o

---

### Post by DancingSun on 2005-12-18
[QUOTE=snellgrove]Hey all,

Think I may have something useful to add to this thread, as another slightly frustrated Logitech user!

I have the MX1000 (great mouse btw) and thanks to this guide, I have it working nicer than before.

But, I think the problem lies with firefox! (or nautilus)

If I have xbindkeys running, so the side-buttons on the mouse are mapped to Alt+Left, and Alt+Right nautilus runs great, I can navigate back and forward with my mouse (yay)

but firefox now pages up, and down with these buttons.

Killing xbindkeys, so the buttons are not mapped to anything... I guess, and suddenly firefox runs just fine, back/forward changes pages ! but suddenly nautilus doesn't do anything lol.

So we need a way of making firefox understand alt+Left/Right I would say?

or have I done something wrong! great guide guys though, my mouse is working nicer than before, definately something for the Wiki if its not already in there :)

:edit:

uhhhhh ignore me or something?!?!?!?   LOL suddenly I just found its all working .. dunno what the heck i've just done though :p :o[/QUOTE]
By default, in firefox, the back and forward buttons are binded to the alt+left/right keys.  But firefox also responds to the button events generated by the thumb buttons, and it maps them to the forward and backward buttons.  Nautilus, on the other hand, does *not* respond to the thumb buttons, so that's why you need the button mappings to make the thumb buttons work in Nautilus.

---

### Post by Chris Tucker on 2005-12-18
ok, i for one am NOT happy. i swap my mouse around depending on what computer i am using. sometimes i do not plug it in at all, and use my trackpad. but with this howto, so far, when my mouse is disconnected, if reconnected to another usb port, its unusable without an X server restart. and if the mouse is not plugged in when the system powers on, X server will not start. in this case i find myself backing up my xorg.conf and then deleting the "configured mouse" sections, only to later have to re-add them and restart my xserver AGAIN later.

is there any way to correct these inconvieniences?

---

### Post by Rev. Nathan on 2005-12-20
I used this tutorial before, blindly following the instructions, not observing what went into the tutorial. Well, I found where the keys were assigned, and I added a Play/Pause control for the 'Window Switcher' button for the MX5xx series! Awesome.

But, can you set it to where it works when the window to pause it out of focus?

Lastly, my back and forward buttons stopped working since I changed the capitalization; now no matter which I save, it doesn't work. Help?

---

### Post by DancingSun on 2005-12-20
[QUOTE=Rev. Nathan]But, can you set it to where it works when the window to pause it out of focus?[/QUOTE]I'm not sure as I don't use any keyboard bindings for my mouse.  But in the System menu, there is an item called "Keyboard Shortcuts" under Preferences.  Inside, you'll see that you can bind a keyboard shortcuts for "Play (or play/pause)" under the "Sound" category.  You might want to try that and see if you can set a keyboard shortcut to it, and then bind the mouse button you want to use to that shortcut.
> Lastly, my back and forward buttons stopped working since I changed the capitalization; now no matter which I save, it doesn't work. Help?What do you mean?  Are you talking about the xbindkey configuration file?  If so, make sure that "Left" and "Right" have their first character capitalized.

---

### Post by fabs0028 on 2005-12-20
thanx a lot for the howto ... i allready had done the first part but i was wondering how to enable the side buttons with nautillus and then i fell on your guide and it worked like a charm :)

Really great thanx :)

---

### Post by BLTicklemonster on 2005-12-22
I tried following the first part to get a microsoft optical intellimouse to have forward back buttons, and it messed everything up. Had to redo either xorg or x11 or whatver pertains to mouseses.


What can I do to get an intellimouse to work right?

---

### Post by DancingSun on 2005-12-22
[QUOTE=BLTicklemonster]I tried following the first part to get a microsoft optical intellimouse to have forward back buttons, and it messed everything up. Had to redo either xorg or x11 or whatver pertains to mouseses.


What can I do to get an intellimouse to work right?[/QUOTE]
Someone on this thread has an intellimouse too, and he also posted his configuration:
[http://ubuntuforums.org/showthread.php?p=566023&highlight=intellimouse#post566023](http://ubuntuforums.org/showthread.php?p=566023&highlight=intellimouse#post566023)

---

### Post by Sp@z on 2005-12-22
Nice job man! Worked great for me and My MX 510!!!!!!!

---

### Post by kingzasz on 2005-12-23
I am stuck on the first step.  My mouse does not work when I plug it into the USB.

The output from "cat /proc/bus/input/devices" only lists the keyboard, with no entry for a mouse.

I've had problems in the past with getting any USB device to work (actually, I don't think I've ever gotten a USB device to work).  Could this be the problem?

Thanks.

---

### Post by DancingSun on 2005-12-23
[QUOTE=kingzasz]I am stuck on the first step.  My mouse does not work when I plug it into the USB.

The output from "cat /proc/bus/input/devices" only lists the keyboard, with no entry for a mouse.

I've had problems in the past with getting any USB device to work (actually, I don't think I've ever gotten a USB device to work).  Could this be the problem?

Thanks.[/QUOTE]
Yes, sounds like your USB ports are not functioning at all.  You best bring your question over to the hardware support forum.

---

### Post by Sapper2ID on 2005-12-24
I have an MX700 and I don't understand what the advantage is of doing all these steps. All I did was change 2 lines in xorg.conf.

Change "Protocol" from "ImPS/2" to "ExplorerPS/2"
Added Option "Buttons"  "7"

That's it and I have all functions in my mouse. I'm just doing what I accidently did when I used Warty, I 'm still new to Linux. I didn't install Imwheel or anything. Like I said, I originally screwed up and this worked. I've used this method on 5 different PC's I've built. 

Am I missing something?

---

### Post by DancingSun on 2005-12-24
[QUOTE=Sapper2ID]I have an MX700 and I don't understand what the advantage is of doing all these steps. All I did was change 2 lines in xorg.conf.

Change "Protocol" from "ImPS/2" to "ExplorerPS/2"
Added Option "Buttons"  "7"

That's it and I have all functions in my mouse. I'm just doing what I accidently did when I used Warty, I 'm still new to Linux. I didn't install Imwheel or anything. Like I said, I originally screwed up and this worked. I've used this method on 5 different PC's I've built. 

Am I missing something?[/QUOTE]
It is my experience that, when using the "ExplorerPS/2" protocol, the cruise up button will generate 2 button events.  That is, it will scroll up once, and then generate the "back" thumb button's event.  So, in firefox, when I cruise up, it'll scroll up by one line, then take me to the previous page that I viewed.  Using the "evdev" protocol is the only way that I've found so far to have made every button on my mouse (MX510) to work correctly.

In fact, even the "switch application" button at the center of the mouse is usable.  Just that it has no function in Linux, but the button generates events and can be binded to other commands.  I use it to bind commands when playing games.

---

### Post by Killerdackel on 2005-12-24
Most of the buttons work good now but two things are not completly done now.

1.I have the same problem that one user some pages earlyer mentioned. Sometimes when I click one of the thumb buttons my X acts if I had pressed the buttons a 100 times. I played a little bi with xbindkeys and now my configuration is the following:

```

"/usr/X11R6/bin/xvkbd -no-jump-pointer -no-repeat -xsendevent -text "\[Alt_L]\[Left]""
   b:8
 "/usr/X11R6/bin/xvkbd -no-jump-pointer -no-repeat -xsendevent -text "\[Alt_L]\[Right]""
   b:9
 "/usr/X11R6/bin/xvkbd -no-jump-pointer -no-repeat -xsendevent -text "\[Super_L]b""
   b:10
 "echo ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
   b:11
 "echo ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
   b:12

```

The -no-jump-pointer seems to work and keeps the xbkbd from jumping pointer to top of the active window. 

2. How can I say xvkbd to pres WIN_L+b? the keysim for win is Super_L but my configuration as shown above causes xvkbd to release WIN+L bevor pressing b that does't do the trick.

---

### Post by fabs0028 on 2005-12-24
Hello
well i just wanted to add a newer version of the /etc/init.d/local script that will fit better with the boot process : juste copy this 

```

#!/bin/sh

. /lib/lsb/init-functions

case $1 in
	start)
		log_begin_msg "Setting up Logitech mouse..."
		if logitech_applet -s 800 -e > /dev/null; then
			log_end_msg 0
		else
			log_end_msg 1
		fi
	;;
	
	stop)
	;;
esac

```

It should produce a clean output such as all the other init scripts

---

### Post by nutshell on 2005-12-26
This tutorial works fine for me, as long as I boot the computer with the mouse plugged in the one specific USB port I used when setting it up ... Not really useful as this is a laptop and I don't always plug in the mouse ... If I don't X won't even start!
Maybe you could add this as a warning for laptop users. Otherwise everything works fine execpthorizontal scrolling (but I havent used xmodmap).

---

### Post by Rizado on 2005-12-26
I've got a problem...
```
I: Bus=0003 Vendor=046d Product=c01d Version=2100
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:1d.2-2/input0
H: Handlers=mouse0 ts0
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103
```I've got a MX510 and as you can see I don't have any "event"... Now I have absolutely no idea what to do. Help?

---

### Post by BLTicklemonster on 2005-12-26
[QUOTE=DancingSun]Someone on this thread has an intellimouse too, and he also posted his configuration:
[http://ubuntuforums.org/showthread.php?p=566023&highlight=intellimouse#post566023](http://ubuntuforums.org/showthread.php?p=566023&highlight=intellimouse#post566023)[/QUOTE]
Thank!!! I just I mean santa just got my 11 year old a motherboard with a amd smpron 2200+ and I'm redoing everything, and it will be nice having his mouse right.

---

### Post by Brent Dax on 2005-12-27
Awesome tutorial--thank you.  I used this to get my Logitech MX600 (comes with the MX3000 kit) working pretty nicely.  However, its "zoom in" and "zoom out" buttons don't seem to be recognized.  (The "100%" button shows up as button 8.)  Any thoughts on this?  I have Buttons set to 12 just in case, but no dice.

```
I: Bus=0003 Vendor=046d Product=c513 Version=3200
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.7-3.3/input1
H: Handlers=kbd mouse0 event2 ts0
B: EV=f
B: KEY=ff0001 0 38000 39fa d841d7a9 9e0000 0 0 0
B: REL=1c3
B: ABS=ffffff01 0
```

---

### Post by atlas95 on 2005-12-27
Hello,
I have yet some problem after read all this post!

With my new mx1000 (i have buy a logitech mx3100), the button for swith task and buttons, scroll left and right generate any code with xev...

I don't know how repair this...

I past my xorg.conf below:

```
Section "InputDevice"
        Identifier    "Configured Mouse"
        Driver        "mouse"
    Option        "Protocol"        "evdev"
    Option        "Dev Name"        "ImExPS/2 Logitech Explorer Mouse"
    Option        "Dev Phys"	    "isa0060/serio1/input0"  
    Option        "Device"        "/dev/input/event2"
    Option	  "Buttons"		"12"
#    Option	  "ZAxisMapping"		"4 5"
	Option     "ZAxisMapping"    "4 5 10 9"
    Option	  "Emulate3Buttons"	"false"
    Option 	  "Resolution" "800&#8243;
    #Option 	  "CorePointer"
EndSection

```

device
```

I: Bus=0011 Vendor=0002 Product=0006 Version=0042
N: Name="ImExPS/2 Logitech Explorer Mouse"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse0 event2 ts0
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103

```
say me if you want something else

ps: sorry for my english i'm french.

---

### Post by Rizado on 2005-12-27
[QUOTE=Rizado]I've got a problem...
```
I: Bus=0003 Vendor=046d Product=c01d Version=2100
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:1d.2-2/input0
H: Handlers=mouse0 ts0
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103
```I've got a MX510 and as you can see I don't have any "event"... Now I have absolutely no idea what to do. Help?[/QUOTE]I got it working. The problem was that the evdev module wasn't loaded. Just added evdev to /etc/modules and it worked fine. I removed the old modules too.

---

### Post by ow50 on 2005-12-27
Here's one fully working **Logitech G5** configuration using imwheel.

/etc/X11/xorg.conf mouse section
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"evdev"
	Option          "Dev Name"              "Logitech USB Gaming Mouse"
	Option		"Buttons"		"8"
	Option		"ZAxisMapping"		"4 5 7 6"
	Option		"Resolution"		"800"
EndSection
```

/etc/X11/imwheel/startup.conf
```
IMWHEEL_START=1
IMWHEEL_PARAMS="-b "45678""
```

~/.imwheelrc
Configures a double click for the thumb button.
```
".*"
None, Thumb1, Button1, 2
```

As a result all buttons work. The DPI adjustment buttons work purely on hardware basis.

---

### Post by Mr_J_ on 2005-12-27
I have a Logitech MX 518.
Not everything works perfect.

1 - I use InitNG and that makes your last part about adding logitech_applet to the start is not very fruitfull.
2 - Although all the buttons you had me configure threw the howto work fine, i have still to configure 3 buttons.

The main problem is not the first, but the second.
I would like to make the extra 3 buttons work in a game, but they aren't detected at all.
I miscalculated at first and put 9 buttons in my xorg.conf, the second button below the scroll wheel registered in xev as button 8. The good news is I successfully now learned to count to 10 and modified the xorg.conf to make 10 buttons. The bad news is my mouse now does not show any of the scroll wheel surrounding buttons. Neither up or down. Not even in xev.

I tried to add some extra lines to .xbindkeysrc by copying the last line a total of 3 extra times and modifying the number of the button, but of course since xev shows none of them...they don't quite work at all.


I was thinking of why can't I just add that line about logitech_applet to sessions.

---

### Post by atlas95 on 2005-12-29
Hey, anybody can answer to me?
Mx1000 only works "fully" when it is in USB ?

If it is taht, I will buy a switch ps2>usb but you must say me if it's really this.

Thanks, sorry for my english

---

### Post by Balachmar on 2005-12-29
Hi,

Does anyone got the solid state pad of the V500 working?
It works for the up and down scrolling, but not for the left and right scrolling...
Just wondering if someone had got that to work...
I will give you some extra info:
mouse button1 = left button
mouse 2 = go left on solid state
mouse 3 = right button
mouse 4 = up on solid state
mouse 5 = down on solid state.

So to me this looks like, there is no way I would get the left right scrolling working, because it looks like it is just 1 button...

---

### Post by _simon_ on 2006-01-06
I have an MX700

I have all the buttons except for cruise up and cruise down working. (i don't have the app button working but don't use it)

What do i need to do to get cruise up/down working?

```

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=1 80000004 2000000 3002078 f840d001 f2ffffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=046d Product=c506 Version=1600
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-1/input0
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0003 Vendor=045e Product=00b0 Version=0110
N: Name="Microsoft Microsoft\uffff Digital Media Pro Keyboard"
P: Phys=usb-0000:00:02.1-1/input0
H: Handlers=kbd event2
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe
B: LED=7

I: Bus=0003 Vendor=045e Product=00b0 Version=0110
N: Name="Microsoft Microsoft\uffff Digital Media Pro Keyboard"
P: Phys=usb-0000:00:02.1-1/input1
H: Handlers=kbd event3 js0
B: EV=10000f
B: KEY=c000000 1 10000 38007 ff8739fa d941d7ff febeffdf ffefffff ffffffff fffffffe
B: REL=40
B: ABS=ffffff01 701ff

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
H: Handlers=kbd event4
B: EV=40001
B: SND=6

```

```

Section                 "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "Protocol" "ExplorerPS/2"
        Option          "Dev Name" "Logitech USB Receiver"
        Option          "Dev Phys" "0000:00:02.0-1/input0"
        Option          "Device" "/dev/input/mice"
        Option          "Buttons" "10"
        Option          "ZAxisMapping" "4 5"
EndSection

```

---

### Post by lindejos on 2006-01-08
Thanks a bunch.  This is the first thing that I have been able to do without having to bother my brother! 

I have the MX 700 and all I had to change was the mouse name and the scroll to buttons 9 and 10, but otherwise your how to was perfect.

Thank you!:razz:

---

### Post by lindejos on 2006-01-08
you might want to double check your scroll with xev.  I have the same mouse and I needed to change my z-axis mapping to buttons 9 and 10 instead of 4 and 5.

---

### Post by Balachmar on 2006-01-09
Could anyone help me out with my V500?
All info I got is in my previous post. I would really like to get the horizontal scrolling to work...

---

### Post by Big-Wayne on 2006-01-09
Greetings,
I have been trying for a few days to get the thumb button working on my Logitech Mousman Dual Optical. I don't however use it via usb as it is plugged into a KVM switcher via a PS/2. I have succeeded in getting the scroll wheel to send webpages backwards and forwards, and the thumb button to scroll, but that was not really what I was after. I want the thumb button to send webpages/nautilus back.

Here is my cat proc output;

I: Bus=0011 Vendor=0002 Product=0006 Version=005f
N: Name="ImExPS/2 Logitech Explorer Mouse"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103

xev shows buttons as follows;

left click button 1
wheel press button 2
right click button 3
scroll up button 4
scroll down button 5
thumb button 2

Notice thumb and middle wheel click are the same

My xorg.conf is edited as follows;

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option        	"Protocol"        "ImPS/2"
	Option		"Device"		"/dev/input/mice"
	Option        	"Dev Name"        "ImExPS/2 Logitech Explorer Mouse"
        Option          "Buttons"               "7"
      	Option          "ZAxisMapping"          "4 5"
EndSection

Now I know people will probably say that is not how the tutorial said to edit my xorg.conf, but I had to edit it for a PS/2 not a usb.
I did add the lines  
Option      "Dev Phys"  "isa0060/serio1/input0"
Option      "Device"      "/dev/input/event1

That crashed my xserver, so I took them out.
Any help on this matter would be greatly appreciated.

---

### Post by Big-Wayne on 2006-01-09
[QUOTE=Big-Wayne]Greetings,
I have been trying for a few days to get the thumb button working on my Logitech Mousman Dual Optical. I don't however use it via usb as it is plugged into a KVM switcher via a PS/2. I have succeeded in getting the scroll wheel to send webpages backwards and forwards, and the thumb button to scroll, but that was not really what I was after. I want the thumb button to send webpages/nautilus back.

Here is my cat proc output;

I: Bus=0011 Vendor=0002 Product=0006 Version=005f
N: Name="ImExPS/2 Logitech Explorer Mouse"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103

xev shows buttons as follows;

left click button 1
wheel press button 2
right click button 3
scroll up button 4
scroll down button 5
thumb button 2

Notice thumb and middle wheel click are the same

My xorg.conf is edited as follows;

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option        	"Protocol"        "ImPS/2"
	Option		"Device"		"/dev/input/mice"
	Option        	"Dev Name"        "ImExPS/2 Logitech Explorer Mouse"
        Option          "Buttons"               "7"
      	Option          "ZAxisMapping"          "4 5"
EndSection

Now I know people will probably say that is not how the tutorial said to edit my xorg.conf, but I had to edit it for a PS/2 not a usb.
I did add the lines  
Option      "Dev Phys"  "isa0060/serio1/input0"
Option      "Device"      "/dev/input/event1

That crashed my xserver, so I took them out.
Any help on this matter would be greatly appreciated.[/QUOTE]


Ignore the above, must have had a typo or something thumb button works as a back button in Firefox but not in nautilus.
This is my submission in xorg.conf;

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option        	"Protocol"        	"evdev"
	Option		"Device"		"/dev/input/mice"
	Option        	"Dev Name"        	"ImExPS/2 Logitech Explorer Mouse"
	Option 		"Dev Phys" 		"isa0060/serio1/input0"
	Option 		"Device" 		"/dev/input/event1
        Option          "Buttons"               "7"
      	Option          "ZAxisMapping"          "4 5"
EndSection

---

### Post by blitz666 on 2006-01-09
Post 1, section 2:

tells the user how to make the thumb's work in Nautilus

---

### Post by TheForumTroll on 2006-01-10
Great guide!

FYI my mx 500 mouse was called "B16_b_02 USB-PS/2 Optical Mouse". Dont know why, but everything works fine.

---

### Post by M3lted on 2006-01-11
woowooo

i follow the instructions and it works ,well didnt work at first , but that was bc i made a typo lol :P
after 1 hour of looking at the cfg  i noticed i put in event 0 insted of 1 lol :P
so changed it and it works great :)


Edit
now after a reboot it stopped working :(
xbindkeys is starting up but the side button dont work anymore :S
any idea's guys ?

---

### Post by Chris Tucker on 2006-01-11
is anyone else having a problem where if you unplug the mouse and plug it back in, the system does not recognize it? or if you boot without the device plugged in, xserver wont start? 
the unplug/plug in problem i think is something to do with the driver not talking to hotplug.. but the boot up not finding the mouse im not sure. is there another protocol other than "evdev" you can use?

---

### Post by lleberg on 2006-01-11
This is great!

The only problem i've got, is that i can't get the sideways scrolling to work..
It detects the sideway-scrolling actions as the same buttons as scroll up and scroll down..

There was a link explaining how to fix this in the howto, but it is broken!

---

### Post by programgeek on 2006-01-11
[QUOTE=Mr_J_]I have a Logitech MX 518.
Not everything works perfect.

1 - I use InitNG and that makes your last part about adding logitech_applet to the start is not very fruitfull.
2 - Although all the buttons you had me configure threw the howto work fine, i have still to configure 3 buttons.

The main problem is not the first, but the second.
I would like to make the extra 3 buttons work in a game, but they aren't detected at all.
I miscalculated at first and put 9 buttons in my xorg.conf, the second button below the scroll wheel registered in xev as button 8. The good news is I successfully now learned to count to 10 and modified the xorg.conf to make 10 buttons. The bad news is my mouse now does not show any of the scroll wheel surrounding buttons. Neither up or down. Not even in xev.

I tried to add some extra lines to .xbindkeysrc by copying the last line a total of 3 extra times and modifying the number of the button, but of course since xev shows none of them...they don't quite work at all.


I was thinking of why can't I just add that line about logitech_applet to sessions.[/QUOTE]

Would you mind posting you xorg.conf and other related files for other people to see?  Thank you.

---

### Post by Sandlst on 2006-01-12
Thanks Endy! Great guide, everything workd perfect for me, and now my mouse is so fast its ridiculous :)

---

### Post by cs378 on 2006-01-13
This works great :KS :KS :KS 

Thank you so much for writing this up. I also learned a lot of new stuff here too hehe

But there is one problem with me, because i am on laptop. Somtimes I unplug the Mouse from the computer so i only use the touchpad but with the xorg.conf set to the logitech mouse I can't start up X, like u said it won't start if there is error. I have to have my mouse plugged in. So my question is, is there a way so that it works even if my mouse is not plugged in?

I only did the xrog.conf, n thats it hehe

---

### Post by DancingSun on 2006-01-13
[QUOTE=cs378]This works great :KS :KS :KS 

Thank you so much for writing this up. I also learned a lot of new stuff here too hehe

But there is one problem with me, because i am on laptop. Somtimes I unplug the Mouse from the computer so i only use the touchpad but with the xorg.conf set to the logitech mouse I can't start up X, like u said it won't start if there is error. I have to have my mouse plugged in. So my question is, is there a way so that it works even if my mouse is not plugged in?

I only did the xrog.conf, n thats it hehe[/QUOTE]
This has been a common question for laptop users.  I do not own a laptop, so I do not know the correct answers.  But I did a little searching on the forum and found this thread that sounds related:

[http://ubuntuforums.org/showthread.php?t=110945&highlight=laptop+usb+mouse+touchpad](http://ubuntuforums.org/showthread.php?t=110945&highlight=laptop+usb+mouse+touchpad)

---

### Post by marcog on 2006-01-27
Finally a step-by-step guide on how to get the forward/back buttons working that actually works!

I have one small problem though. Pasting by clicking left+right buttons together no longer works. It worked fine before making the changes. I'm beginning to wonder what is more important - the forward/back buttons or pasting using left+right buttons.

I'm using an mx518 on an HP nx7010.

---

### Post by blitz666 on 2006-01-27
Where it says "emulate 3 button mouse" change that to yes instead of no.

---

### Post by marcog on 2006-01-28
I couldn't find an "emulate 3 button mouse" option.

Instead I found an "Emulate3Buttons" option set to true in my old configuration. So I copied that line into my new config.

Now the left+right click *does* paste, however I can no longer select text with the mouse! :-(

So I've removed the line again until I can find a way that works properly.

This is a section of my current xorg.conf file:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Protocol"		"evdev"
	Option		"Dev Name"		"Logitech USB-PS/2 Optical Mouse"
	Option		"Dev Phys"		"usb-0000:00:1d.0-2/input0"
	Option		"Device"		"/dev/input/event1"
**#**	Option		"Emulate3Buttons"	"true"
	Option		"Buttons"		"7"
	Option		"ZAxisMapping"		"4 5"
EndSection

```

---

### Post by RaptorRaider on 2006-02-03
This worked perfectly for my (partly broken) MX510; I think this thread deserves a small kick. ;)

---

### Post by r!ots on 2006-02-05
first of all thx for this great guide. i use a logitech mx500 and it worked perfectly for me.

i also tried to make the mouse button, which moves between windows, work by editing the ~/.xbindkeysrc so it looks like this:

```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Tab]""
  m:0x0 + b:8

```

somehow it doesn't work and i don't have any idea why not. can anyone help plz?

---

### Post by Balachmar on 2006-02-06
Still don't know how to do a correct install of the vertical scrolling with my V500.
Because sliding to the left or right results in the same button being reported by the program.

---

### Post by marcog on 2006-02-06
Have you tried changing the "Buttons" option to a higher number?

---

### Post by Balachmar on 2006-02-06
Well, it is the output generated by xev.
It only detects 5 buttons, and I thought it would be able to track any amount of buttons... How do I specify the amount of buttons then for xev?
left = 1
scroll left =2
right =3
scroll up = 4
scroll down = 5
scroll right doesn't show up anything. It does work in windows by the way.

---

### Post by RaptorRaider on 2006-02-06
[QUOTE=RaptorRaider]This worked perfectly for my (partly broken) MX510; I think this thread deserves a small kick. ;)[/QUOTE]
Had to do a reinstall of Ubuntu today, and somehow I can't get my side buttons to work correctly, even though I'm doing exactly the same as last time as far as I know.
Did something change?

Edit: I have no idea why, but after a couple of reboots it is working perfectly once again.

---

### Post by Mr_J_ on 2006-02-07
Hi!

This is the second time I followed this howto and it has worked for the most part.

I've had trouble getting my extra buttons to work both times.
I WILL get it to work even if it exausts the life out of me.:D 

Xorg.conf :
> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Protocol"		"evdev"
	Option		"Dev Name"		"Logitech USB-PS/2 Optical Mouse"
	Option		"Dev Phys"		"usb-0000:00:02.0-1/input0"
	Option		"Device"		"/dev/input/event1"
	Option		"Buttons"		"8"
	Option		"ZAxisMapping"		"4 5"
	Option		"CorePointer"
EndSection
I was thinking of adding:
> Option "Resolution" "1600"
Which I will do later and report what it does, if anything.

Before I remember trying out the number of buttons and ending up at 8 threw trial and error, but I've a few sites which seem to indicate it's 10 buttons I should count.
[COLOR="DarkOrange"]The mouse has + and - buttons which I thought were hardware controlled and not software. Can anyone clear this one up for me?[/COLOR]

I have yet to get any extra button working. Even tho I did have gdm restarts and full reboots in case I missed anything.

Xbindkeys:
> "/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:7
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[TAB]""
  m:0x0 + b:8


At first I had a bunch of problems with getting the mouse recognized under X, but after considerable fidling it seems to no longer give me too many problems.

[COLOR="DarkOrange"]I recomend changing the Howto in order to download all the necessary files before you even start.[/COLOR] I think that was one of the steps that helped fix the problem with my X not starting.

X didn't find any protocol to use, and the wildcard use in the "Dev Phys" had to be corrected, also didn't find a Core Pointer. Which was probably because I changed my existing Mouse section and didn't coment it out.
Even tho that last statement makes little sense to me, it did seem to work when I added the Core Pointer option.

---

### Post by aliencds on 2006-02-08
this worked for my g5 mouse on the first step now my side button works.. i didnt even have to to any of the other side button xmapping stuff :/

---

### Post by calgarystevens on 2006-02-10
[QUOTE=Sapper2ID]I have an MX700 and I don't understand what the advantage is of doing all these steps. All I did was change 2 lines in xorg.conf.

Change "Protocol" from "ImPS/2" to "ExplorerPS/2"
Added Option "Buttons"  "7"

That's it and I have all functions in my mouse.[/QUOTE]

MX1000 here on mine, and this worked for me also, 7 buttons working perfectly. Anyone with the ps/2 adaptor might want to try this first, it might work. Then, if not, switch to usb and follow the guide.

---

### Post by Craig Caldwell on 2006-02-21
It only took me most of the day:-k  but forward and back now work on my mx 700 thumb buttons. I usually have to do a lot more than this to feel good about myself. Linux rules... but seriously that was so much more satisfying than just plugging in a mouse and using it.


Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "Protocol" "evdev"
Option "Dev Name" "Logitech USB Receiver"
Option "Dev Phys" "usb-*/input0"
Option "Device" "/dev/input/event3"
Option "Buttons" "8"
Option "ZAxisMapping" "4 5"
EndSection

#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"		"/dev/input/mice"
#	Option		"Protocol"		"ImPS/2"
#	Option		"ZAxisMapping"		"4 5"
#EndSection


Section 2: Side buttons and Nautilus

We can use "xvkbd" and "xbindkeys" to bind the side mouse buttons to "ALT + LEFT" and "ALT + RIGHT" so they work as forward and backwards in Nautilus.


1. xvkbd and xbindkeys

Lets install "xvkbd" and "xbindkeys":
Code:
sudo apt-get install xvkbd xbindkeys
Next we need to create the configuration for them:
Code:
gedit ~/.xbindkeysrc
Now paste the following:
Code:
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
  m:0x0 + b:7


Please note, the "L" and "R" from the words "left" and "right" in the square brackets above should be capitalised, this seems like a bug in the forums here that they don't display properly.
Thank you endy and every one else who had tips tricks crushing failure and sweet success.

---

### Post by R3linquish3r on 2006-02-24
thx alot :) back and forward buttons work as soon as i set it up in xorg cause im using firefox :)

---

### Post by kayrune on 2006-02-26
Has anyone gotten the MX1000 working with Xgl ? When running Xgl, my MX1000 is detected as a 7 button mouse with the evdev driver.

---

### Post by bender unit on 2006-02-26
Hello Folks,

I was just linked to this thread from the [Wiki page based off it that explains how to configure a MX1000 mouse with Ubuntu]("https://wiki.ubuntu.com/MX1000Mouse"). Just wanted to say that I simply followed this guide and got my Logitech MX610 working (almost) perfectly under Linux now! The mouse wheel left/right scrolling as well as the side buttons for forward/backward work flawlessly now. 

Never bothered to check until now, but what amazed me even more was that the additional buttons for volume control work, too! I'm not sure if they worked before, or if this was the effect of changing the mouse driver in xorg.conf, but they work now, anyways, and do exactly what they're supposed too, even though I did nothing at all to achieve this behavior (I mean, the guide was just for the other buttons, right?).

Now the only thing that's missing is a tool that lights up the two buttons that are supposed to show incoming mails and IMs, respectively. Pressing the mail button already starts Gnome's default mail program, but if I could get the mail notification applet to light up the button when new mail arrives, I would be even happier with Ubuntu. Has anyone heard of a way to do this? Or is it rather that nobody on the forum (except me) even owns such a mouse, since searching for "mx610" doesn't return a single result? (except my post now, I guess...)

---

### Post by LycoLoco on 2006-02-27
I've got an MX518 and using this guide I got the left and right buttons working, but now I can't get the up/down/program buttons working (the 3 in the middle). When I run xev, the up and down buttons don't show anything as being read, but I know that they work in XP, so it's not dead hardware. Anyone have any ideas? :confused:

---

### Post by asktoby on 2006-03-02
When I bought my logitech mouse for kubuntu, the wheel originally didn't
work. I tried following the instructions in this thread and, while they worked, I found that my hotswapping of things like mice,
usb keys, mp3 players etc seemed a bit flakey. Sometimes the mouse died and wouldn't come back to life (light underneath was off) until I rebooted.

Anyway, after some tweaking, I found that I didn't need to do half of
the fiddly stuff described in that thread, and now I have the following
mouse section in my /etc/X11/xorg.conf

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "Emulate3Buttons" "true"
    Option         "Buttons"        "10"
    Option         "ZAxisMapping"        "4 5"
EndSection

This is for a Logitech Optical Mouse M/N:M-BT96a which I bought last
month.

HTH

---

### Post by maclaxguy on 2006-03-02
Great article, but I'm having some problems.

After following the directions, my mouse works great.
I'm on a laptop, so I constantly need to unplug and plug my mouse.  Unfortunately, after unplugging and then replugging in, the mouse does not do anything.  The trackpad still works fine, but I can't use the mouse without restarting.

When plugging it in, /var/log/messages shows this:
```
Mar  2 20:52:55 localhost kernel: [4295319.826000] usb 2-2: new low speed USB device using uhci_hcd and address 5
Mar  2 20:52:56 localhost kernel: [4295319.998000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-2
Mar  2 20:52:56 localhost input.agent[10082]:      tsdev: already loaded
Mar  2 20:52:56 localhost input.agent[10082]:      mousedev: already loaded
Mar  2 20:52:56 localhost input.agent[10082]:      evdev: already loaded
Mar  2 20:52:56 localhost usb.agent[10094]:      usbhid: already loaded
Mar  2 20:52:56 localhost input.agent[10187]:      evdev: already loaded
Mar  2 20:52:56 localhost input.agent[10197]:      evdev: already loaded
Mar  2 20:52:56 localhost input.agent[10203]:      evdev: already loaded

```

Anyone have any ideas on what to do?

I appreciate the help.

---

### Post by asktoby on 2006-03-03
When my hotplug system was glitchy, before streamlining my xorg.conf as I described 2 posts previously, I found that I could sometimes 'resurrect' a dead mouse by pressing ctrl-alt-F8 then ctrl-alt-F7 (assuming there was a 2nd login on F8). i.e. switch to a different GUI login and back again.

I have no idea how or why this worked. It didn't always work.

---

### Post by Maupertus on 2006-03-03
This may have been a problem handled in this thread, but it's so large that I'm losing oversight.

I edited the xorg.conf as stated above, and X doesn't want to load now.
So I tried to edit the file using the "sudo nano /etc/x11/xorg.conf" command offered above, but I only get a blank screen without the file I have just edited.

As a result I cannot log in to the graphical enviroment and am a bit stumped as to what to do?

So please, what do I have to do now?

---

### Post by asktoby on 2006-03-04
Capital X in your path.

sudo nano /etc/X11/xorg.conf

If in doubt, use [tab] to autocomplete whilst you type :)

---

### Post by phux on 2006-03-14
Hi,

i have trouble, getting my MX1000 to work as i want.

Vertical-Scrolling does not work at all an the output of 
```
sudo logitech_applet -s 800
``` is
```
001/003     046D/C50E   M-RAG97         MX1000 Laser Mouse
   Channel 1    Battery: 7    Single channel   No 800cpi support   No Horiz Roller   No Vert Roller   2 butt.
```

How can i enable 800cpi and cruise control?

Buttonmapping: (Button-xevNumber)
Left-1, Right-3, Middle-2, Scrollup-4, Scrolldown-5, ThumbForward-9, ThumbBackward-8, ThumbMiddle-10, WheelClickUpper-11, WheelClickLower-12

thx

---

### Post by joe_geek on 2006-03-15
For those of you who managed to get an LX7 working:

my xev only recognizes as following
left click: button 1
right click: button 3
scroll click: button 2
scroll up: button 4
scroll down: button 5

here's where it gets weird:
scroll left: button 2
scroll right: nothing comes up

for those two buttons that would do page back/forward in Windows:
page back: button 2
page forward: button 3

I followed [Golgoth]("http://ubuntuforums.org/showthread.php?p=561025&highlight=lx7#post561025")'s tutorial, but I'm not getting the page back/forward and scroll left/right for obvious reasons. 
Does anyone know how to get xev to recognize the mouse buttons on the LX7?

---

### Post by beerorkid on 2006-03-15
[QUOTE=kayrune]Has anyone gotten the MX1000 working with Xgl ? When running Xgl, my MX1000 is detected as a 7 button mouse with the evdev driver.[/QUOTE]

This guide has been awesome for the last 10 or so times I have installed breezy.  I am using dapper flight 5 with the compiz XGL and this fix does not work anymore.

Is that a dapper issue or a compiz/XGL problem.  I am betting it is the compiz/XGL cuz it does some pretty strange stuff which I hardly understand dealing with xorg.conf.

Just wondering if anybody has any ideas.

---

### Post by fizz on 2006-03-15
Not sure whats up, i followed the guide to a t, but for whatever reason, when i start X, i get

Unknow Protocol "evdev"

Im using a MX700 and set it up according to how others have done it also.

thanks

---

### Post by souled on 2006-03-15
[QUOTE=fizz]Not sure whats up, i followed the guide to a t, but for whatever reason, when i start X, i get

Unknow Protocol "evdev"

Im using a MX700 and set it up according to how others have done it also.

thanks[/QUOTE]

Edit: Oops. I thought this was in a different thread. Haha, my mistake.

---

### Post by r3n0z on 2006-03-16
worked great for my mx310, think i have the lowest model number so far :P

anyhow there's something satisfying about configuring it yourself

---

### Post by Brunellus on 2006-03-18
[QUOTE=beerorkid]This guide has been awesome for the last 10 or so times I have installed breezy.  I am using dapper flight 5 with the compiz XGL and this fix does not work anymore.

Is that a dapper issue or a compiz/XGL problem.  I am betting it is the compiz/XGL cuz it does some pretty strange stuff which I hardly understand dealing with xorg.conf.

Just wondering if anybody has any ideas.[/QUOTE]
Just wanted to confirm the dapper issue.  I suspect it is an XGL/Compiz issue, because I actually had my MX510 thumb buttons up and running in "vanilla" Dapper.  

Just the same, I'd be interested to know how a fix might be effected.

---

### Post by pwner4once on 2006-03-18
Well I am sure it's a compatibility issue between Dapper and XGL. I am using Dapper 6.04 right now and all my side buttons are working. I am using Logitech MX510.

Hearing about the no side button news, it makes me want to avoid trying out XGL. 

btw regarding the guide. Everyone is using _    Option        "Protocol"        "evdev"_ and seem to be working for you guys. Well for me, I would get something saying evdev doens't exist and such. Think this is rather a Dapper issue. anyways, it works flawless even if you use _Option "Protocol" "ExplorerPS/2"_

so try that if u can't get X working again with evdev. 

alright, my mouse is finally working. WOOT! thanks to all contributers :D

---

### Post by kayrune on 2006-03-18
The evdev, buttons not working is a XGL issue, it has nothing to do with ubuntu/dapper. The same thing happens on Gentoo.

---

### Post by beerorkid on 2006-03-18
I have not gotten all of it to work correctly yet, still messing with it.

but from this post: [http://ubuntuforums.org/showthread.php?t=135360](http://ubuntuforums.org/showthread.php?t=135360)

good ol xmodmap like back in hoary.

I at one time had the two buttons on the top and bottom of the wheel to work like page forward/backward, but the wheel did the same as well.

I am hoping that I can get it to work with dapper/XGL
will let you know if I do.

mx510

---

### Post by makhand on 2006-03-22
Ok, there are a couple of big problems that i'm having that I think are quite ridiculous. I'm using an MX1000

1. If i dont have the mouse plugged in when I start up, X crashes. I have to plug the mouse in to get my laptop to work now. Pretty annoying

2. I have a dual monitor setup. These shortcuts only work for one of the monitors!! On the laptop screen, i can side scroll and go back and forward in history, on the other monitor (crt), i get none of this functionality. 

any ideas?

---

### Post by tellnes on 2006-03-23
The guide worked great! thanx alot:)

However i cannot install the logitech applet..

When i try to  apt-get install checkinstall build-essential libusb-dev
I know the output is in Norwegian, however, it basically says some of the packages it needs is still under "incomming", while in synaptic it says it is installed.
------------------------------------------------------------------
i get this meesage: Les pakkelister ... Ferdig
Byggjer kravtre ... Ferdig
Nokre av pakkane kunne ikkje installerast. Dette kan koma av at du har
valt ein umogleg situasjon. Dersom du brukar den ustabile utgåva av
distribusjonen, kan det òg henda at nokre av pakkane som trengst ikkje
er laga enno eller at dei framleis ligg i «Incoming».
Følgjande informasjon kan hjelpa med å løysa situasjonen:

Følgjande pakkar har krav som ikkje er oppfylte:
  libusb-dev: Krav: libusb-0.1-4 (= 2:0.1.10a-17ubuntu1) men 2:0.1.11-6 skal installerast
-------------------------------------------------------------------

Seems like i have a wrong ver of libbus, i have the 2.0.1.11-6, but it says in the output its gonna be installed..

Anyone know howto get the right ver of libus installed without meesing up everything leaving me with a system without mouse;)

---

### Post by sYs^ on 2006-03-25
[QUOTE=fizz]Not sure whats up, i followed the guide to a t, but for whatever reason, when i start X, i get

Unknow Protocol "evdev"

Im using a MX700 and set it up according to how others have done it also.

thanks[/QUOTE]

I have the same problem with MX510, any ideas?

---

### Post by Corbelius on 2006-03-26
[QUOTE=sYs^]I have the same problem with MX510, any ideas?[/QUOTE]

Run modprobe -l in console and check if u have evdev driver, example:

/lib/modules/2.6.15.5-ck7-ubuntu/kernel/drivers/input/evdev.ko

Put "evdev" string in ur /etc/modules and try again.

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

evdev
#lp
#mousedev
#psmouse
#rtc
#sbp2
#sr_mod
#usbcore
#sd_mod

---

### Post by sYs^ on 2006-03-26
Thanks for the answer, but

I had evdev in modules, there was another problem (just figured out, in this minute:p) , I had to change the xorg.conf:

```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "evdev"
#    Option        "Protocol"       "evdev"
    Option        "Dev Name"       "Logitech USB-PS/2 Optical Mouse"
    Option        "Dev Phys"       "usb-*/input2"
    Option        "Device"         "/dev/input/event0"
    Option        "Buttons"        "10"
    Option        "ZAxisMapping"   "4 5"
EndSection

```

But there's still another problem, if I scroll up fast in FireFox (1.5.0.1 swiftfox) it goes back one page.

---

### Post by detyabozhye on 2006-03-30
Works awesomely! Now, what should I map button 8 to? hmm...

"/usr/bin/dominate_the_world -muahahahahaha""
  m:0x0 + b:8

---

### Post by irjason on 2006-03-31
I have a Logitech MX518. By following these directions I was able to get it working. However, I use an Iogear MiniView USB KVM switch to change between my Ubuntu PC and my XP box. When I would toggle PC's the mouse would not respond while I was using the evdev protocol. It seems the KVM causes problems here. 
I discovered that if I used "ExplorerPS/2" all buttons work, and the mouse continues to work when I toggle back and forth with the KVM.
Below is the mouse section of my xorg.conf in case anyone else is having this problem. 

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
    	Option          "Dev Name"             "Logitech USB-PS/2 Optical Mouse"
	Option		"CorePointer"
	Option          "Dev Phys"              "usb-*/input0"
	Option		"Device"		 "/dev/input/mice"
	Option		"Protocol"		 "ExplorerPS/2"
    	Option          "Buttons"        	 "10"
	Option		"ZAxisMapping"         "4 5"
EndSection

```

---

### Post by detyabozhye on 2006-03-31
When I set it up, I had a problem, like someone else here, that when scrolling up  using the cruise control button, it would also select text, and the button acted like a left-click as well as scroll up. in xev it would report it as button 4 and 10, I fixed it by changing:
```

         Option        "ZAxisMapping"         "4 5"
```
to:
```

         Option        "ZAxisMapping"         "4 5 9 10"
```

---

### Post by scooper on 2006-04-03
[QUOTE=irjason]I have a Logitech MX518. By following these directions I was able to get it working. However, I use an Iogear MiniView USB KVM switch to change between my Ubuntu PC and my XP box. When I would toggle PC's the mouse would not respond while I was using the evdev protocol. It seems the KVM causes problems here. 
I discovered that if I used "ExplorerPS/2" all buttons work, and the mouse continues to work when I toggle back and forth with the KVM.
[/QUOTE]

I have the same mouse and the same problem when using a KVM.  The mouse just freezes when I switch back to the Linux session using evdev.  One time it did recover somehow, but other times it didn't.

Is there a way to force it to recover?  I could tolerate binding a script to a key and restarting the mouse manually.

Otherwise what does the ExplorerPS/2 setup look like?  Does it require xmodmap?

I mainly wanted to confirm another KVM problem with this great solution.  I'll search for an answer in the meantime.

Cheers,
Steve

---

### Post by evergreen on 2006-04-04
Hi I have a mx518 when I run "cat /proc/bus/input/devices" in terminal I get this

I: Bus=0003 Vendor=046d Product=c01e Version=2200
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:02.0-2/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=ff0000 0 0 0 0
B: REL=103

so I tryed this in my config

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "Protocol" "evdev"
Option "Dev Name" "Logitech USB-PS/2 Optical Mouse"
Option "Dev Phys" "usb-0000:00:02.0-2/input0"
Option "Device" "/dev/input/event1"
Option "Buttons" "10"
Option "ZAxisMapping" "4 5"
EndSection

This doesn't work 

I don't see anyone getting **S: Sysfs=/class/input/input1** when they run "cat /proc/bus/input/devices"

What is S: Sysfs=/class/input/input1 and do i need to add it to my config somehow? Any help would be great, thanks

---

### Post by Baikonur on 2006-04-04
Could someone help please, I have an mx500, but when I use the xorg.conf configures given, I get a kernel panic, saying "0Kernel panic - not syncing: Fatal exception in intterrupt".

---

### Post by beerorkid on 2006-04-05
well I found a simple fix for me mx510, XGL, dapper only works in dapper

from trorion here: [http://ubuntuforums.org/showthread.php?t=150116&highlight=mx510](http://ubuntuforums.org/showthread.php?t=150116&highlight=mx510)

make your xorg.conf have this in it.  Of course comment out your currently working one just in case ;)
```
Section "InputDevice"
  Identifier  "Configured Mouse"
  Driver      "mouse"
  Option      "CorePointer"
  Option      "Device" "/dev/input/mice"
  Option      "Protocol" "ExplorerPS/2"
  Option      "Emulate3Buttons" "false"
  Option      "Buttons" "5"
  Option      "ZAxisMapping" "4 5"
  Option      "ButtonMapping" "1 2 3 6 7"
  Option      "Resolution" "800"
EndSection
```

As trorion mentions, make sure that this line: Option      "Device" "/dev/input/mice" matches your old working line

---

### Post by gamerzl on 2006-04-05
does this work in kubuntu?

---

### Post by detyabozhye on 2006-04-05
100% sure it should work, that file is the Xorg configuration, if the config works, it'll work regardless of the desktop environment.

---

### Post by evergreen on 2006-04-06
Thanks beerorkid I Tryed out your config & It works great In Firefox, Giving the forward & back page functions :-D Gonna have a play about to try & get it working in Nautilus.

---

### Post by beerorkid on 2006-04-06
well the thanks goes to [trorion](http://ubuntuforums.org/member.php?u=72350)

I was home nursing a sprained ankle and decided I was gonna figure out the last little thing that bugged me.

Glad it is working for others.

---

### Post by mfarley on 2006-04-07
Has anone been able to get speed / acceleration working using an xorg.conf like this?

```

Section "InputDevice"
  Identifier  "Configured Mouse"
  Driver      "mouse"
  Option      "CorePointer"
  Option      "Device" "/dev/input/mice"
  Option      "Protocol" "ExplorerPS/2"
  Option      "Emulate3Buttons" "false"
  Option      "Buttons" "5"
  Option      "ZAxisMapping" "4 5"
  Option      "ButtonMapping" "1 2 3 6 7"
  Option      "Resolution" "800"
EndSection

```

I've tried both driver "mouse" and driver "evdev" -- no matter what happens I can't change the resolution / speed / accel.

I'm using a PS/2 mouse.

---

### Post by evergreen on 2006-04-08
Hi mfarley just to let you know the above config allows me to change my resolution with the two arrow buttons above & bellow the scroll wheel to the three different settings i think 400/800/1200? I'm kind of new to linux so I don't know how much I can help. The only thing I see is I have my mouse plugged into a USB port not PS/2

---

### Post by PsychoBrat on 2006-04-08
This may have been covered by one of the other million posts in this thread, but a rehash with slightly different wording can only help for the loveable lost Googlers out there! ;)

To get my Logitech MX510 working from a base Dapper Drake Flight 6 install (with some acceleration tweaks done through UI configuration tools in Gnome), I tried following several over-complicated (for my particular case) guides, then realised I could do away with all their stuff and make only a few small changes. My current /etc/X11/xorg.conf contains an *InputDevice* section as follows:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "10"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 6 7"
#       Option          "Emulate3Buttons"       "true"
EndSection
```

The important (modified) lines are:

```
Section "InputDevice"
        Option          "Buttons"               "10"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 6 7"
#       Option          "Emulate3Buttons"       "true"
EndSection
```

...but you should be able to leave *Emulate3Buttons* on if you really want; it just fakes click from the third mouse button when buttons 1 and 2 are pressed together - not something that's too useful on a 10 button (including both scroll directions) mouse! :P

*ZAxisMapping* specifies which buttons to treat as the scroll-wheel. *ButtonMapping* specifies, in order of physical buttons, a list of button signals to send. So mine tells it that buttons 4 and 5 'pretend' to be 6 and 7 respectively. My other buttons are working as expected too (auto-scroll buttons are fine, window switch button just acts as another left button), so I presume they're implicitly mapped to their 'natural' signals (i.e. 8 to 8, 9 to 9, 10 to 10). (???)

This works fine for me in Firefox, but not other apps such as Nautilus. Does anyone know if this is expected (i.e. that you need to emulate keystrokes like ALT+{LEFT | RIGHT} from mouse clicks anyway)?

---

### Post by makhand on 2006-04-08
I've asked this before, and i'll try once more. 
I'm doing this on a laptop. 
These instructions work mostly fine for me. Except there are some catches. 
1. I cannot get the mouse to work if it is not plugged in when X starts. 
2. If the laptop goes into sleep/screensaver mode, it doesnt wake up and work with the mouse anymore (only the touchpad works at this point). 
3. I have a dual monitor setup (I plug a monitor into my laptop) and all the functionality in this thread only works on the laptop lcd screen. As soon as my mouse travels to the other monitor, it loses all its power (beyond just normal point and click).

I made my synaptic touchpad my corepointer because it was the only way i saw to make X start at all without having the mouse plugged in at all times. 

please help. Thanks

---

### Post by whector on 2006-04-10
hi! does anyone know how to get mx700 work in Dapper?

---

### Post by antidrugue on 2006-04-12
> **PsychoBrat]This may have been covered by one of the other million posts in this thread, but a rehash with slightly different wording can only help for the loveable lost Googlers out there!  said:**
> 

I tryed numerous complicated guides as well, without much success (some combinations of udev, evdev, xbindkeys, etc.).

[QUOTE=PsychoBrat]
My current /etc/X11/xorg.conf contains an *InputDevice* section as follows:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "10"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 6 7"
#       Option          "Emulate3Buttons"       "true"
EndSection
```

WOW! That works!

Many thanks to you, "PsychoBrat". That was EXACTLY what I was looking for.

Works perfectly with my Logitech MX500, on Debian Etch (KDE 3.5.2).

---

### Post by Craig Caldwell on 2006-04-14
[QUOTE=antidrugue]I tryed numerous complicated guides as well, without much success (some combinations of udev, evdev, xbindkeys, etc.).



WOW! That works!

Many thanks to you, "PsychoBrat". That was EXACTLY what I was looking for.

Works perfectly with my Logitech MX500, on Debian Etch (KDE 3.5.2).[/QUOTE]
PsychoBrat's method got my mx700 mouse working in firefox but not nautilus.
I'll try the xbindkeys method next but I'm not sure it works with dapper 64.

---

### Post by Craig Caldwell on 2006-04-14
Ok the xbindkeys method does work with 64 bit dapper.

---

### Post by Grimmy on 2006-04-20
I should start reading howto threads backwards!

Thanks PsychoBrat.. This worked fine for my MX518 under Dapper Flight 6:

[QUOTE=PsychoBrat]
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "10"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 6 7"
#       Option          "Emulate3Buttons"       "true"
EndSection
```
[/QUOTE]

Now maybe I can help you:

[QUOTE=PsychoBrat]
This works fine for me in Firefox, but not other apps such as Nautilus. Does anyone know if this is expected (i.e. that you need to emulate keystrokes like ALT+{LEFT | RIGHT} from mouse clicks anyway)?[/QUOTE]

I got it working in Nautilus using the following from the first post:

[QUOTE=endy]
_1. xvkbd and xbindkeys_

Lets install "xvkbd" and "xbindkeys":

```
sudo apt-get install xvkbd xbindkeys
``` Next we need to create the configuration for them:

```
gedit ~/.xbindkeysrc
``` Now paste the following:

```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7
``` 

**Please note, the "L" and "R" from the words "left" and "right" in the square brackets above should be capitalised, this seems like a bug in the forums here that they don't display properly.**

Make sure you keep the quote marks, save the file and run "xbindkeys" in the terminal. It runs as a daemon in the background. You should now be able to test if it works in Nautilus by using the side buttons it also works in Epiphany if you use it.[/QUOTE]

---

### Post by makhand on 2006-04-20
[QUOTE=makhand]I've asked this before, and i'll try once more. 
I'm doing this on a laptop. 
These instructions work mostly fine for me. Except there are some catches. 
1. I cannot get the mouse to work if it is not plugged in when X starts. 
2. If the laptop goes into sleep/screensaver mode, it doesnt wake up and work with the mouse anymore (only the touchpad works at this point). 
3. I have a dual monitor setup (I plug a monitor into my laptop) and all the functionality in this thread only works on the laptop lcd screen. As soon as my mouse travels to the other monitor, it loses all its power (beyond just normal point and click).

I made my synaptic touchpad my corepointer because it was the only way i saw to make X start at all without having the mouse plugged in at all times. 

please help. Thanks[/QUOTE]

Well, i had a pretty brilliant idea. I've sort of resolved issue 3. To get the mouse keys to work with my second monitor, i simply opened up a terminal in that monitor and started 'xbindkeys' there. Unfortunately, i dont know how to make this automatic since xbindkeys is already being started automatically using System>Preferences>Sessions>Startup Programs. Somehow this does not apply to the second monitor.

Edit: xbindkeys has an optional parameter in which it allows you to specify the displays. for my dual monitor system, i simply have two programs execute (using Startup Programs). I use:
```

xbindkeys -X :0.0
xbindkeys -X :0.1 
```

---

### Post by detyabozhye on 2006-04-25
I got evdev working on Dapper perfectly (requires xmodmap and xbindkeys).
WARNING: This is not a full guide, please refer to post one in this thread for 800dpi resolution, back/forward in nautilus, etc.

First I did this to find out the name of my mouse:
```
cat /proc/bus/input/devices
```
Here's my output with the info I need in bold:
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
Then I did this:
```
sudo gedit /etc/udev/rules.d/19-local.rules
```
and put this into the file and saved it (replace the bold part with the name of your mouse and replace the underlined part with whatever you want to put there, it will be used in xorg.conf):
```
KERNEL=="event[0-9]*", SYSFS{../name}=="**Logitech USB-PS/2 Optical Mouse**", NAME="input/_mx500_"
```
Then I changed my mouse section in xorg.conf to this:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/_mx500_" #this should be that underlined name from 19-local.rules
EndSection
```
Then I made my ~/.Xmodmap look like this:
```
pointer = 1 3 2 4 5 8 9 6 7 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32
```
Next I fixed cruise control (requires the compiling stuff; build-essential and all that I believe):
Download this file: [http://bg.rifetech.com/click.tgz](http://bg.rifetech.com/click.tgz)
untar it to ~/click (or wherever you want, just remember the dir, you'll need it in the .xbindkeysrc)
then compile it:
```
cd ~/click
make
```
Then I changed my ~/.xbindkeysrc to _include_ this:
```
"~/click/click 4"
  m:0x0 + b:11
"~/click/click 5"
  m:0x0 + b:12
```

Credits: This article and [http://floam.sh.nu/guides/mx1000](http://floam.sh.nu/guides/mx1000)
Let me know if I made any typos or mistakes.
EDIT: I don't think this works in Xgl, I haven't tried, but I doubt it will.

---

### Post by ashrack on 2006-04-25
I ahve a MS INTELLI MOUSE OPTICAL. And my side 2buttons work great in FIREFOX. But I still want them to work in NAUTILUS so I followed the following guide to the letter:
[QUOTE=endy]_**A complete guide to a Logitech mouse**_

**_Section 2: Side buttons and Nautilus_**[INDENT]
We can use "xvkbd" and "xbindkeys" to bind the side mouse buttons to "ALT + LEFT" and "ALT + RIGHT" so they work as forward and backwards in Nautilus.


I have a MICROSOFT INTELLIMOSE OPTICAL. And I got side buttons working great in Firefox. So then I wanted them to also work in NAUTILUS. So I followed this guide:
_1. xvkbd and xbindkeys_

Lets install "xvkbd" and "xbindkeys":

```
sudo apt-get install xvkbd xbindkeys
``` Next we need to create the configuration for them:

```
gedit ~/.xbindkeysrc
``` Now paste the following:

```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7
``` 

**Please note, the "L" and "R" from the words "left" and "right" in the square brackets above should be capitalised, this seems like a bug in the forums here that they don't display properly.**

Make sure you keep the quote marks, save the file and run "xbindkeys" in the terminal. It runs as a daemon in the background. You should now be able to test if it works in Nautilus by using the side buttons it also works in Epiphany if you use it.

*Note: Same as before, if you have different mouse buttons use xev to find out what number they are and change the "b:6" and "b:7" in the above to the correct numbers.*
[/QUOTE]
But they dont work and even worse also they stop working in FF! 
This is my XEV output when pressing the side buttons:
```
ButtonPress event, serial 26, synthetic NO, window 0x3600001,
    root 0x4c, subw 0x0, time 3488431120, (86,50), root:(493,393),
    state 0x10, button 6, same_screen YES

ButtonRelease event, serial 26, synthetic NO, window 0x3600001,
    root 0x4c, subw 0x0, time 3488431272, (86,50), root:(493,393),
    state 0x10, button 6, same_screen YES

ButtonPress event, serial 26, synthetic NO, window 0x3600001,
    root 0x4c, subw 0x0, time 3488431560, (86,50), root:(493,393),
    state 0x10, button 7, same_screen YES

ButtonRelease event, serial 26, synthetic NO, window 0x3600001,
    root 0x4c, subw 0x0, time 3488431712, (86,50), root:(493,393),
    state 0x10, button 7, same_screen YES

```
and my XORG.CONF
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
#for IntelliMouse's 7 buttons
	Option          "Buttons"               "7"
	Option		"ButtonMapping"		"1 2 3 6 7"
```

ps. Am using DAPPER BETA! Could this be the cause for it not workin?
ps2. In NAUTILUS I checked if ALT_L and ALT_D if they go back and forth and they do

---

### Post by detyabozhye on 2006-04-25
[QUOTE=ashrack]I ahve a MS INTELLI MOUSE OPTICAL. And my side 2buttons work great in NAUTILUS. But I still want them to work in NAUTILUS so I followed the following guide to the letter:[/QUOTE]
:confused: If you have an MS mouse, why are you asking in a Logitech thread?

---

### Post by Golgoth on 2006-04-25
[QUOTE=detyabozhye]:confused: If you have an MS mouse, why are you asking in a Logitech thread?[/QUOTE]

I used this method with an MS Intellimouse and Breezy and it worked very well as I explained in a [previous post]("http://ubuntuforums.org/showpost.php?p=566023&postcount=143")...

That's why he may ask for help.

The problem is that I does not have this mouse anymore so ashrack, I can not help you...

---

### Post by detyabozhye on 2006-04-25
Should I make a full blown guide on how to make the MX500 work with evdev on Dapper?

---

### Post by ashrack on 2006-04-26
[QUOTE=Golgoth]I used this method with an MS Intellimouse and Breezy and it worked very well as I explained in a [previous post]("http://ubuntuforums.org/showpost.php?p=566023&postcount=143")...

That's why he may ask for help.

The problem is that I does not have this mouse anymore so ashrack, I can not help you...[/QUOTE]
But they still dont work in NAUTILUS! And they even stop workin in FIREFOX if I do:
```
gedit ~/.xbindkeysrc

"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
m:0x0 + b:7
```
Could this be because am using DAPPER?

@detyabozhye
Because its pretty similar.

---

### Post by Giga on 2006-04-28
DancingSun,

Do you know if there is logitech applet to install in amd64?
i got a log error that says:


dpkg: error processing /home/giga/logitech-applet-0.4test1/logitech-applet-0.4test1_0.4test1-1_x86_64.deb (--install):
 package architecture (x86_64) does not match system (amd64)
Errors were encountered while processing:
 /home/giga/logitech-applet-0.4test1/logitech-applet-0.4test1_0.4test1-1_x86_64.deb


Thanks

---

### Post by gzs on 2006-04-29
Logitech MX518

I did everything in the guide (Omitting section 1.4 and I did not install the applet) and X would not start after the initial process.

I went back and completely redid it to insure I did not make a mistake, and again, X was "misconfigured" and would not start.

I used Nano to edit out the previously entered information and left it as default. The scroll wheel and left/right click worked previously so, I just used xbindkeys to get the Forward/Back (mouse 8/9) to work correctly.

All is well! I'm using Dapper Flight-6 by the way.

---

### Post by detyabozhye on 2006-04-29
Look at my post in this thread for (partial) Dapper instructions, the link is in my sig.

---

### Post by Golgoth on 2006-04-30
[QUOTE=ashrack]But they still dont work in NAUTILUS! And they even stop workin in FIREFOX if I do:
```
gedit ~/.xbindkeysrc

"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
m:0x0 + b:7
```
Could this be because am using DAPPER?

@detyabozhye
Because its pretty similar.[/QUOTE]

I used this how-to with breezy... I did NOT try with the intellimouse and dapper.
So Yes, it could be like this because you are using dapper since evdev has changed...
Are "\[Alt_L]\[Left]" and "\[Alt_L]\[Right]" well capitalized in your xbindkeysrc?

---

### Post by mucha on 2006-05-02
detyabozhye, your guide worked perfect in xgl, but I used xte instead of click. Thanks! :)

---

### Post by detyabozhye on 2006-05-02
You're welcome! ^_^

---

### Post by Rizado on 2006-05-03
> **detyabozhye]I got evdev working on Dapper perfectly (requires xmodmap and xbindkeys).
WARNING: This is not a full guide, please refer to post one in this thread for 800dpi resolution, back/forward in nautilus, etc.

First I did this to find out the name of my mouse:
```
cat /proc/bus/input/devices
```
Here's my output with the info I need in bold:
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
Then I did this:
```
sudo gedit /etc/udev/rules.d/19-local.rules
```
and put this into the file and saved it (replace the bold part with the name of your mouse and replace the underlined part with whatever you want to put there, it will be used in xorg.conf):
```
KERNEL=="event[0-9]*", SYSFS{../name}=="**Logitech USB-PS/2 Optical Mouse**", NAME="input/_mx500_"
```
Then I changed my mouse section in xorg.conf to this:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/_mx500_" #this should be that underlined name from 19-local.rules
EndSection
```
Then I made my ~/.Xmodmap look like this:
```
pointer = 1 3 2 4 5 8 9 6 7 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32
```
Next I fixed cruise control (requires the compiling stuff said:**
> http://bg.rifetech.com/click.tgz[/url]
untar it to ~/click (or wherever you want, just remember the dir, you'll need it in the .xbindkeysrc)
then compile it:
```
cd ~/click
make
```
Then I changed my ~/.xbindkeysrc to _include_ this:
```
"~/click/click 4"
  m:0x0 + b:11
"~/click/click 5"
  m:0x0 + b:12
```

Credits: This article and [http://floam.sh.nu/guides/mx1000](http://floam.sh.nu/guides/mx1000)
Let me know if I made any typos or mistakes.
EDIT: I don't think this works in Xgl, I haven't tried, but I doubt it will.I can't get it working properly :(
Creatin /dev/input/mx510 and using that works perfect but all extra buttons are recognized as a leftmouse click in firefox :confused: 

This is what xev tell me when I use my side buttons. ```
ButtonPress event, serial 31, synthetic NO, window 0x1000001,
    root 0x135, subw 0x0, time 4219485450, (169,0), root:(1461,76),
    state 0x0, button 8, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0x1000001,
    root 0x135, subw 0x0, time 4219485578, (169,0), root:(1461,76),
    state 0x0, button 8, same_screen YES

ButtonPress event, serial 31, synthetic NO, window 0x1000001,
    root 0x135, subw 0x0, time 4219486730, (169,0), root:(1461,76),
    state 0x0, button 9, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0x1000001,
    root 0x135, subw 0x0, time 4219486946, (169,0), root:(1461,76),
    state 0x0, button 9, same_screen YES

```I guess this looks alright. I'm using Kubuntu Dapper and in konqueror it doesn't seem to use the buttons as left click. And I didn't have any .Xmodmap or .xbindkeysrc so I created them.

---

### Post by detyabozhye on 2006-05-03
[QUOTE=Rizado]I can't get it working properly :(
Creatin /dev/input/mx510 and using that works perfect but all extra buttons are recognized as a leftmouse click in firefox :confused: 

This is what xev tell me when I use my side buttons. ```
ButtonPress event, serial 31, synthetic NO, window 0x1000001,
    root 0x135, subw 0x0, time 4219485450, (169,0), root:(1461,76),
    state 0x0, button 8, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0x1000001,
    root 0x135, subw 0x0, time 4219485578, (169,0), root:(1461,76),
    state 0x0, button 8, same_screen YES

ButtonPress event, serial 31, synthetic NO, window 0x1000001,
    root 0x135, subw 0x0, time 4219486730, (169,0), root:(1461,76),
    state 0x0, button 9, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0x1000001,
    root 0x135, subw 0x0, time 4219486946, (169,0), root:(1461,76),
    state 0x0, button 9, same_screen YES

```I guess this looks alright. I'm using Kubuntu Dapper and in konqueror it doesn't seem to use the buttons as left click. And I didn't have any .Xmodmap or .xbindkeysrc so I created them.[/QUOTE]
Do you have xmodmap and xbindkeys installed?
If not:
```
sudo apt-get install xmodmap
```
```
sudo apt-get install xbindkeys
```
From the description of your problem, it seems xmodmap is not installed.

---

### Post by siorai on 2006-05-04
> **detyabozhye]
Next I fixed cruise control (requires the compiling stuff said:**
> http://bg.rifetech.com/click.tgz[/url]
untar it to ~/click (or wherever you want, just remember the dir, you'll need it in the .xbindkeysrc)
then compile it:
```
cd ~/click
make
```
Then I changed my ~/.xbindkeysrc to _include_ this:
```
"~/click/click 4"
  m:0x0 + b:11
"~/click/click 5"
  m:0x0 + b:12
```

Credits: This article and [http://floam.sh.nu/guides/mx1000](http://floam.sh.nu/guides/mx1000)
Let me know if I made any typos or mistakes.
EDIT: I don't think this works in Xgl, I haven't tried, but I doubt it will.

I've run into a roadblock here. I've edited my xorg.conf, 19-local.rules, and Xmodmap pretty much well exactly like you have. My mouse is being shown as "B16_b_02 USB-PS/2 Optical Mouse" when I cat /proc/bus/input/devices so I'm of course using that. At least at this point my mouse is working like it was. Everything is fine except the side buttons do nothing in Firefox. When I use xev, it does show the side buttons as 6 and 7 so that looks right, but they're just not doing anything. With xev showing the buttons like that is it something wrong with my config, or is it possibly something wrong with Firefox?

Edit: Just noticed something... In Firefox, the side buttons are actually doing something. In the code windows on this page, the side buttons will cause the scroll bar to move back and forth horizontally... 

My second problem is when I try to run make for click. I get the following:

```
siorai@dagon:~/click$ make
gcc -Wall -c -o click.o click.c
click.c:3:22: error: X11/Xlib.h: No such file or directory
click.c:4:34: error: X11/extensions/XTest.h: No such file or directory
click.c: In function &#8216;main&#8217;:
click.c:9: error: &#8216;Display&#8217; undeclared (first use in this function)
click.c:9: error: (Each undeclared identifier is reported only once
click.c:9: error: for each function it appears in.)
click.c:9: error: &#8216;dpy&#8217; undeclared (first use in this function)
click.c:9: warning: implicit declaration of function &#8216;XOpenDisplay&#8217;
click.c:22: warning: implicit declaration of function &#8216;XTestFakeButtonEvent&#8217;
click.c:22: error: &#8216;True&#8217; undeclared (first use in this function)
click.c:22: error: &#8216;CurrentTime&#8217; undeclared (first use in this function)
click.c:26: error: &#8216;False&#8217; undeclared (first use in this function)
click.c:29: warning: implicit declaration of function &#8216;XCloseDisplay&#8217;
make: *** [click.o] Error 1

```

I'm at a loss as to how to interpret that. I realize the second and third lines show things to be missing, but how would I go about fixing that?



Edit: Ok, got my forward/back working now. I started to think about what I might have changed with the Firefox config. I realized that I had changed the option for changing tabs with the scroll wheel. It's mousewheel.horizscroll.withnokey.action 2. I had set it to 0 to disable that "feature." Well, I put it back to default and the forward/back works and as an added bonus, the mousewheel no longer scrolls between tabs. :D  Still at a loss about the click problem, but it's not a huge deal.

---

### Post by detyabozhye on 2006-05-04
> **siorai]My second problem is when I try to run make for click. I get the following:

```
siorai@dagon:~/click$ make
gcc -Wall -c -o click.o click.c
click.c:3:22: error: X11/Xlib.h: No such file or directory
click.c:4:34: error: X11/extensions/XTest.h: No such file or directory
click.c: In function &#8216 said:**
>  Error 1

```

I'm at a loss as to how to interpret that. I realize the second and third lines show things to be missing, but how would I go about fixing that?

Seems you're missing these two packages:
```
libx11-dev
x11proto-xext-dev
```
Install them via Synaptic cuz they have a bunch of dependencies, so I wouldn't want to try to install them via command line.

---

### Post by Rizado on 2006-05-04
[QUOTE=detyabozhye]Do you have xmodmap and xbindkeys installed?
If not:
```
sudo apt-get install xmodmap
```
```
sudo apt-get install xbindkeys
```
From the description of your problem, it seems xmodmap is not installed.[/QUOTE]xbindkeys wasn't installed but 
xmodmap was, the problem was .Xmodmap wasn't autoloaded so I had to make a script to do that.

What is the click tool and script actually doing?

---

### Post by detyabozhye on 2006-05-04
[QUOTE=Rizado]xbindkeys wasn't installed but 
xmodmap was, the problem was .Xmodmap wasn't autoloaded so I had to make a script to do that.

What is the click tool and script actually doing?[/QUOTE]
They're making button 11 and 12 do button 4 and 5 because those buttons act as left click in Opera and Firefox. The cruise control buttons send 4 and 5 as well as 11 and 12 at the same time.

---

### Post by Rizado on 2006-05-06
Well, there was some updates yesterday and today and I think I remember evdev was updated. Anyway when I rebooted evdev driver doesn't work anymore. Am I the only one with the problems?

BTW this is on dapper.

---

### Post by siorai on 2006-05-06
[QUOTE=Rizado]Well, there was some updates yesterday and today and I think I remember evdev was updated. Anyway when I rebooted evdev driver doesn't work anymore. Am I the only one with the problems?

BTW this is on dapper.[/QUOTE]

I just had this happen as well. Everything was fine until I actually restarted then X won't start, complaining about not having a valid CorePointer. :-(

---

### Post by detyabozhye on 2006-05-06
The new evdev is sort of broken at the moment, they should fix it soon I think. I haven't been able to find a workaround for it to use at the moment, so I have the old version of evdev right now. [bug #43100](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-input-evdev/+bug/43100)

---

### Post by kemosabe79 on 2006-05-07
Great HOWTO. I used it with a MX310 and it works great. I tried it because it has essentially the same specs as the MX510, and it worked. Might want to add the MX310 to your list. :)This was done in Breezy, BTW...using 8 buttons not 10.

---

### Post by Rizado on 2006-05-07
Ok, Where can I get the old driver?

EDIT: I found a old working version on the cd.

---

### Post by detyabozhye on 2006-05-07
If anyone else is looking for it, here it is: [http://ftp.kfki.hu/linux/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_1.0.0.5-0ubuntu2_i386.deb](http://ftp.kfki.hu/linux/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_1.0.0.5-0ubuntu2_i386.deb)

---

### Post by siorai on 2006-05-07
[QUOTE=detyabozhye]If anyone else is looking for it, here it is: [http://ftp.kfki.hu/linux/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_1.0.0.5-0ubuntu2_i386.deb](http://ftp.kfki.hu/linux/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_1.0.0.5-0ubuntu2_i386.deb)[/QUOTE]

That link isn't working anymore. I was able to find the files here though: [http://mir2.ovh.net/ubuntu/pool/main/x/xserver-xorg-input-evdev/]("http://mir2.ovh.net/ubuntu/pool/main/x/xserver-xorg-input-evdev/") but I'm not sure how to apply the patch, that is what the .diff file is right?

---

### Post by clov on 2006-05-10
I get this when I run .xbindkeysrc
```

./.xbindkeysrc
./.xbindkeysrc: line 1: /usr/X11R6/bin/xvkbd -xsendevent -text [Alt_L][Left]: No such file or directory
./.xbindkeysrc: line 2: m:0x0: command not found
./.xbindkeysrc: line 3: /usr/X11R6/bin/xvkbd -xsendevent -text [Alt_L][Right]: No such file or directory
./.xbindkeysrc: line 4: m:0x0: command not found

```

my .xbindkeysrc looks like this:
```

"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9

```
(I own a mx610 buttons 8 and 9 are my thumb buttons)

Does anyone knows what my problem is?
I've tried to have .xbindkeysrc without " " but than it says:
```

^[[3D./.xbindkeysrc: line 2: m:0x0: command not found
^[[3C./.xbindkeysrc: line 4: m:0x0: command not found

```
](*,)

---

### Post by detyabozhye on 2006-05-10
you're supposed to run xbindkeys, not ./.xbindkeysrc

---

### Post by clov on 2006-05-10
[QUOTE=detyabozhye]you're supposed to run xbindkeys, not ./.xbindkeysrc[/QUOTE]

#-o](*,)  thkx

---

### Post by daedalusman on 2006-05-10
Does any one have an idea when the evdev driver will work again in dapper? I really want to get my mouse buttons working again, its really annoying having to click on the back foward buttons in firefox and nautilus. I would drop back to the older version but I'm not really sure how to go about doing that, if someone could help me out there in the mean time that would be great for the time being. Thanks for the info.

---

### Post by detyabozhye on 2006-05-10
Here's the old evdev package: [http://detyabozhye.com/other/xserver-xorg-input-evdev_1.0.0.5-0ubuntu2_i386.deb](http://detyabozhye.com/other/xserver-xorg-input-evdev_1.0.0.5-0ubuntu2_i386.deb)

---

### Post by Rizado on 2006-05-11
You can start synaptic and search for xserver-xorg-input-evdev and mark it. Press Ctrl + E, select the older one and press force version, apply and it'll probably ask you to insert your cd. Make sure you don't update it again until the bug is fixed.

---

### Post by siorai on 2006-05-11
[QUOTE=detyabozhye]Here's the old evdev package: [http://detyabozhye.com/other/xserver-xorg-input-evdev_1.0.0.5-0ubuntu2_i386.deb](http://detyabozhye.com/other/xserver-xorg-input-evdev_1.0.0.5-0ubuntu2_i386.deb)[/QUOTE]

Awesome. Thank you very much.

---

### Post by makhand on 2006-05-11
Is there a way to not have the mouse as the 'CorePointer', but instead send core events (so you can start without it present), but still be able to plug it in later and have it automatically detected and working? This is for a laptop

---

### Post by tonyo46 on 2006-05-23
Thank you for this HowTo, but I have a problem now :
- my touchpad doesn't work...
- if I unplug my mouse, and then replug it, it doesn't work anymore, and I have to restart x-server

How could I solve those problems ?

---

### Post by detyabozhye on 2006-05-23
I think you'd have to make the touchpad as another pointer using the mouse(?) driver for that. I'm not sure how to make it all work though.

---

### Post by makhand on 2006-05-23
[QUOTE=tonyo46]
- my touchpad doesn't work...
- if I unplug my mouse, and then replug it, it doesn't work anymore, and I have to restart x-server[/QUOTE]

I have similar problems and have not gotten much help here. I think to get the touchpad to work, i had to make it 'CorePointer', while making the mouse 'SendCoreEvents'. I'll attach a snippet of my xorg.conf file below

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option          "CorePointer"        
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"1"
	Option		"SHMConfig"		"on"
	Option		"AccelFactor"		".0008"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
	Option		"SendCoreEvents"	"true"	
        Option          "Protocol"              "evdev"
        Option          "Dev Name"              "Logitech USB Receiver"
        Option          "Dev Phys"              "usb-*/input0"
        Option          "Device"                "/dev/input/event2"
        Option          "Buttons"               "12"
        Option          "ZAxisMapping"          "4 5 7 6"
	Option		"Resolution"		"800"
 EndSection

...

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Default Screen"
	Screen 1 	"VGA" RightOf "Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection
```

as far as how to make it work after unplugging the mouse, I have NO clue and would really appreciate some help also. If you figure it out, please post.

---

### Post by tonyo46 on 2006-05-24
thank you makhand but I still don't have my touchpad working !
I tried all the combinations possible...

I'm looking for a way to return to my previous config properly because, now, I can't use my laptop without my mouse.
What do I have to do to return to a basic configuration ? if I only change my xorg.conf, the system crashes...

---

### Post by makhand on 2006-05-24
[QUOTE=tonyo46]I'm looking for a way to return to my previous config properly because, now, I can't use my laptop without my mouse.
What do I have to do to return to a basic configuration ? if I only change my xorg.conf, the system crashes...[/QUOTE]

Yes, xorg.conf is a pretty sensitive file to mess with. Any little mistake screws everything up. 

Get to a place where you can type command line commands. For example, if you can get X working at all, you can open a terminal. If X is crashing and giving you error messages, you can press Ctrl +Alt+F6 to get to a place where you can login and type commands. Even if X is sort of working, to where you can use your keyboard, type those keys. 
 
once there, login, then do: 
```
sudo dpkg-reconfigure xserver-xorg
```
This should take you through the basic configuration ubuntu does on install. Usually you just go with whatever option it gives you and it should be fine. You will probably want to keep your mouse unplugged during this process. (it may be the other way around, but it doesnt take long either way). 

Let me know if that restores you to your normal system.

---

### Post by tranzndance on 2006-05-27
Hello,

Thank you for the tutorial. I would like to program the side buttons to do copy and paste. I tried to edit the code myself but can't get it to work.

How can I change the following to use ctrl V and C?
```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
  m:0x0 + b:7
```

I checked out [http://homepage3.nifty.com/tsato/xvkbd/](http://homepage3.nifty.com/tsato/xvkbd/) to see the syntax for "control" but I don't really get it, especially since it doesn't match what you use for "alt".

To make sure the setup is correct, I used the code you provided, and I was able to navigate forward and backward with the side buttons.

---

### Post by R3linquish3r on 2006-05-29
I dont have Xmodmap loaded, but I do have Xbindkeys loaded. Weird thing is my cruise control work as they should but my side buttons do nothing and XEV doesn't even seem to recognise them ](*,) . I'm using an MX510. Heres some of my info if it helps:

```
I: Bus=0003 Vendor=046d Product=c01d Version=2100
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:10.3-2/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event1 ts0 
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103
```

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "evdev"
    Option         "Dev Name"        "Logitech USB-PS/2 Optical Mouse"
    Option         "Dev Phys"        "usb-0000:00:10.3-2/input0"
    Option         "Device"          "/dev/input/event1"
    Option         "Buttons"         "10"
    Option         "ZAxisMapping"    "4 5"
EndSection
```

```
# Volume Up
"amixer set Master,0 5%+"
   m:0x0 + c:176

# Volume Down
"amixer set Master,0 5%-"
   m:0x0 + c:174

# Toggle Volume
"amixer set Master,0 toggle"
   m:0x0 + c:160

"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9

```

Heres the XEV Output for my two side buttons:

```
MotionNotify event, serial 30, synthetic NO, window 0x2400001,
    root 0x135, subw 0x0, time 2145993778, (115,2), root:(325,234),
    state 0x10, is_hint 0, same_screen YES

MotionNotify event, serial 30, synthetic NO, window 0x2400001,
    root 0x135, subw 0x0, time 2145993786, (115,1), root:(325,233),
    state 0x10, is_hint 0, same_screen YES

MotionNotify event, serial 30, synthetic NO, window 0x2400001,
    root 0x135, subw 0x0, time 2145993794, (117,1), root:(327,233),
    state 0x10, is_hint 0, same_screen YES

MotionNotify event, serial 30, synthetic NO, window 0x2400001,
    root 0x135, subw 0x0, time 2145993802, (117,0), root:(327,232),
    state 0x10, is_hint 0, same_screen YES
```

Does anyone see anything wrong? I've been working two days on this and still no solution :(.

---

### Post by R3linquish3r on 2006-05-29
Well after a half hour of working with Xmodmap I finally have my forward and back buttons working. The only thing still broken is my top cruise control which xev seems to think is bound the button 4 AND button 6. I never use it anyway so it isn't really a big deal I'm just glad to have a side buttons :)

---

### Post by gelse on 2006-05-31
after some struggle i managed to get my mouse working with evdev - seems that driver "mouse" doesnt recognize the evdev protocol, but it works with driver "evdev".
but there is still one problem left:
i have an (old) MX500, which reports as "B16_b_02 USB-PS/2 Optical Mouse"
here the relevant parts of my xorg.conf:
```
Section "InputDevice"
	Identifier    "evdev Mouse"
	Driver        "evdev"
	Option        "Protocol"        "evdev"
	Option		"SendCoreEvents"	"true"
	Option        "Dev Name"        "B16_b_02 USB-PS/2 Optical Mouse"
	Option        "Dev Phys"        "usb-0000:00:1d.0-1/input0"
	Option        "Device"        "/dev/input/event4"
	Option        "Buttons"        "10"
	Option        "ZAxisMapping"        "4 5 7 6"
EndSection
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option          "CorePointer"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection
```
the relevant output from xorg.log:
```
(II) evdev brain: Rescanning devices (1).
(**) Option "SendCoreEvents" "true"
(**) evdev Mouse-usb-0000:00:1d.0-1/input0: always reports core events
(II) evdev Mouse-usb-0000:00:1d.0-1/input0: Found 3 relative axes.
(II) evdev Mouse-usb-0000:00:1d.0-1/input0: Configuring as pointer.
(**) evdev Mouse-usb-0000:00:1d.0-1/input0: WHEELRelativeAxisButtons: 4 5.
(II) evdev Mouse-usb-0000:00:1d.0-1/input0: Found 8 mouse buttons
(II) evdev Mouse-usb-0000:00:1d.0-1/input0: Configured 10 mouse buttons
....
(II) XINPUT: Adding extended input device "evdev Mouse-usb-0000:00:1d.0-1/input0" (type: MOUSE)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
....
(**) evdev Mouse-usb-0000:00:1d.0-1/input0: 3 valuators.
(**) ../../src/evdev_btn.c (90): Registering 10 buttons.
(II) evdev Mouse-usb-0000:00:1d.0-1/input0: Init
....
(II) evdev brain: Rescanning devices (2).
(II) evdev Mouse-usb-0000:00:1d.0-1/input0: On

```
and here some output from xev:
mwheel up:
```
ButtonPress event, serial 30, synthetic NO, window 0x3a00001,
    root 0x52, subw 0x0, time 2323091254, (162,119), root:(176,550),
    state 0x0, button 4, same_screen YES

ButtonRelease event, serial 30, synthetic NO, window 0x3a00001,
    root 0x52, subw 0x0, time 2323091254, (162,119), root:(176,550),
    state 0x800, button 4, same_screen YES

```
mwheel down:
```
ButtonPress event, serial 27, synthetic NO, window 0x3a00001,
    root 0x52, subw 0x0, time 2323134100, (173,14), root:(187,445),
    state 0x0, button 5, same_screen YES

ButtonRelease event, serial 27, synthetic NO, window 0x3a00001,
    root 0x52, subw 0x0, time 2323134100, (173,14), root:(187,445),
    state 0x1000, button 5, same_screen YES
```
button in above the mwheel:
```
ButtonPress event, serial 27, synthetic NO, window 0x3a00001,
    root 0x52, subw 0x0, time 2323300554, (175,19), root:(189,450),
    state 0x0, button 9, same_screen YES

ButtonPress event, serial 27, synthetic NO, window 0x3a00001,
    root 0x52, subw 0x0, time 2323300554, (175,19), root:(189,450),
    state 0x0, button 4, same_screen YES

ButtonRelease event, serial 27, synthetic NO, window 0x3a00001,
    root 0x52, subw 0x0, time 2323300554, (175,19), root:(189,450),
    state 0x800, button 4, same_screen YES

ButtonRelease event, serial 27, synthetic NO, window 0x3a00001,
    root 0x52, subw 0x0, time 2323300706, (175,19), root:(189,450),
    state 0x0, button 9, same_screen YES
```
as long as that button is pressed, it toggles button 4 press and release in between the button9 events.
the button below the mwheel:
```
ButtonPress event, serial 27, synthetic NO, window 0x3a00001,
    root 0x52, subw 0x0, time 2323388549, (178,9), root:(192,440),
    state 0x0, button 5, same_screen YES

ButtonRelease event, serial 27, synthetic NO, window 0x3a00001,
    root 0x52, subw 0x0, time 2323388549, (178,9), root:(192,440),
    state 0x1000, button 5, same_screen YES

```
the button below that button:
```
ButtonPress event, serial 27, synthetic NO, window 0x3a00001,
    root 0x52, subw 0x0, time 2323451513, (177,22), root:(191,453),
    state 0x0, button 8, same_screen YES

ButtonRelease event, serial 27, synthetic NO, window 0x3a00001,
    root 0x52, subw 0x0, time 2323451673, (177,22), root:(191,453),
    state 0x0, button 8, same_screen YES
```
the two buttons on the side work like a charm as buttons 6 and 7

my problem is:
when i DID NOT use evdev, it reported and recognized MORE buttons than it did now with evdev (have to relog to check it with evdev again, i'll post it if you tell me to)
in both cases the front button reported the mwheelup and an own button as described above, when i used the mouse-protocol, it reported the button on the other side of the mwheel as an own event.

any ideas how i can get rid of that extra-toggling the mwheel in the front, and how i can get all 10 buttons to work?

(using ubuntu dapper drake with xgl working - like a charm on dell inspiron 9300, even the side-slot for SD-cards works! had to tell that, sorry... ;) )
ah, and btw - no xmodmap yet, as that doesnt affect the xev at all - does it?

---

### Post by NT4usB on 2006-06-01
Configuring Logitech mice... with a twist.
Following your guide, I was able to get my Mx310 to work as advertized.
Thank you for that!
Now for the twist.
I would like the left (thumb/back) button to act like the middlebutton. Several apps I run require use of middlebutton and trying to click the scrollwheel without spazzing is tough. In Firefox, I rarely use back and when I do, rightclick contextmenu is fine. (In windoz) I use left (back) button to open links in new tabs and close tabs.
I don't use the right (forward) button at all and use the top button  for closeapp.
Any tips on how to tweak the left (back) button to act like middlebutton?
ed: While we're at it, any way to get the scroll wheel to go a page at a time instead of three lines (or whatever) it does now? I'm wearing the poor thing out browsing these forums!
:o
* Happy Linux user for going on 3 weeks now!*

---

### Post by lleberg on 2006-06-02
Hi!
I used this guide quite a while ago, and got it working great.

But, yesterday i upgraded to Dapper, everything is fine, except for my mouse!
I couldn't get into  using the setup so i used the old one..

The error says it can't find evdev. or that it's unknown.
But the package xserver-xorg-input-evdev is up to date..

Anyone else who knows this problem?

---

### Post by siorai on 2006-06-02
[QUOTE=lleberg]Hi!
I used this guide quite a while ago, and got it working great.

But, yesterday i upgraded to Dapper, everything is fine, except for my mouse!
I couldn't get into  using the setup so i used the old one..

The error says it can't find evdev. or that it's unknown.
But the package xserver-xorg-input-evdev is up to date..

Anyone else who knows this problem?[/QUOTE]

The most up to date evdev is broken. Go back to page 28 in this thread. detyabozhye has posted xserver-xorg-input-evdev_1.0.0.5-0ubuntu2_i386.deb. Install that and then lock it in synaptic. Just remember that if you do a dist-upgrade, that evdev will be updated and you'll have to replace it with this older version again.

---

### Post by lleberg on 2006-06-02
Well. i found a workaround. or whatever i should call it.

Set the driver to evdev instead of mouse. and change the protocol to ImPS/2 instead of evdev.

And, this thread only has 15 pages, TOO BAD! :D

---

### Post by antidrugue on 2006-06-02
[QUOTE=PsychoBrat]This may have been covered by one of the other million posts in this thread, but a rehash with slightly different wording can only help for the loveable lost Googlers out there! ;)

To get my Logitech MX510 working from a base Dapper Drake Flight 6 install (with some acceleration tweaks done through UI configuration tools in Gnome), I tried following several over-complicated (for my particular case) guides, then realised I could do away with all their stuff and make only a few small changes. My current /etc/X11/xorg.conf contains an *InputDevice* section as follows:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "10"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 6 7"
#       Option          "Emulate3Buttons"       "true"
EndSection
```

The important (modified) lines are:

```
Section "InputDevice"
        Option          "Buttons"               "10"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 6 7"
#       Option          "Emulate3Buttons"       "true"
EndSection
```

...but you should be able to leave *Emulate3Buttons* on if you really want; it just fakes click from the third mouse button when buttons 1 and 2 are pressed together - not something that's too useful on a 10 button (including both scroll directions) mouse! :P

*ZAxisMapping* specifies which buttons to treat as the scroll-wheel. *ButtonMapping* specifies, in order of physical buttons, a list of button signals to send. So mine tells it that buttons 4 and 5 'pretend' to be 6 and 7 respectively. My other buttons are working as expected too (auto-scroll buttons are fine, window switch button just acts as another left button), so I presume they're implicitly mapped to their 'natural' signals (i.e. 8 to 8, 9 to 9, 10 to 10). (???)

This works fine for me in Firefox, but not other apps such as Nautilus. Does anyone know if this is expected (i.e. that you need to emulate keystrokes like ALT+{LEFT | RIGHT} from mouse clicks anyway)?[/QUOTE]

In Dapper, *PsychoBrat*'s instructions work flawlessly.

---

### Post by phatmonkey on 2006-06-02
[QUOTE=antidrugue]In Dapper, *PsychoBrat*'s instructions work flawlessly.[/QUOTE]
Back/forward in firefox does not seem to be working for me with these instructions.

---

### Post by antidrugue on 2006-06-02
[QUOTE=phatmonkey]Back/forward in firefox does not seem to be working for me with these instructions.[/QUOTE]

Back/forward work for me in Firefox. Here is the relevant part in */etc/X11/xorg.conf*:

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Resolution"            "800"
        Option          "Buttons"               "10"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 6 7"
EndSection

```

Nothing else than */etc/X11/xorg.conf* was changed on my install. I have a MX500 from Logitech.

---

### Post by xeta on 2006-06-02
MX518 not working. Tried countless configs listed in this thread.


Relevant info: 

Xorg
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Resolution"            "800"
        Option          "Buttons"               "10"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 6 7"
EndSection

```

/proc/bus/input/devices
```

stang@silva:~$ cat /proc/bus/input/devices
I: Bus=0003 Vendor=046d Product=c01e Version=2200
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:0b.0-1/input0
S: Sysfs=/class/input/input0
H: Handlers=mouse0 ts0 event0
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103


```

xev
```

ButtonPress event, serial 29, synthetic NO, window 0x2800001,
    root 0x135, subw 0x0, time 2526076444, (170,97), root:(182,197),
    state 0x10, button 8, same_screen YES

ButtonPress event, serial 29, synthetic NO, window 0x2800001,
    root 0x135, subw 0x0, time 2526077132, (168,98), root:(180,198),
    state 0x10, button 9, same_screen YES

```

---

### Post by xeta on 2006-06-02
Forgot to mention: Dapper.

---

### Post by detyabozhye on 2006-06-02
Look here: [http://ubuntuforums.org/showthread.php?p=955049#post955049](http://ubuntuforums.org/showthread.php?p=955049#post955049)
and here: [http://ubuntuforums.org/showpost.php?p=992685&postcount=272](http://ubuntuforums.org/showpost.php?p=992685&postcount=272)

---

### Post by Mr_J_ on 2006-06-02
MX518 has 8 buttons not 10. The plus and minus are not going to work.
I have one. Made it work. Just installed 6.06 so lost the xorg...

---

### Post by opticyclic on 2006-06-02
This worked great with Breezy, but now I have upgraded to Dapper I have had to revert to the previous conf to stop X from crashing.
Any changes I seem to make to the mouse section seems to crash X :confused: 
Its frustrating not to have the thumb buttons and the up/down buttons on my MX510 work ](*,) ```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

#Section "InputDevice"
#        Identifier    "Configured Mouse"
#        Driver        "mouse"
#    	Option        "Protocol"        "evdev"
#    	Option        "Dev Name"        "PS2++ Logitech MX Mouse"
#    	Option        "Dev Phys"        "isa0060/serio1/input0"
#        Option        "Device"        	"/dev/input/event2"
#	Option      "Buttons" "10"
#	Option      "ZAxisMapping" "4 5"
#EndSection
```

---

### Post by Cenotaph on 2006-06-03
hmm... does anyone managed to get the side buttons to work in nautilus with Dapper?

---

### Post by detyabozhye on 2006-06-03
I'll write a full guide for Dapper and evdev when I get a chance, for now refer to my signiture.

---

### Post by opticyclic on 2006-06-03
I have a minor improvement.
I copied and edited [gelses xorg.conf ]("http://ubuntuforums.org/showpost.php?p=1071965&postcount=290")
I now have evdev working and my xorg.conf looks like this```
Section "InputDevice"
	Identifier    	"Configured Mouse"
	Driver        	"evdev"
	Option        	"Protocol"        	"evdev"
	Option		"SendCoreEvents"	"true"
	Option        	"Dev Name"        	"PS2++ Logitech MX Mouse"
	Option        	"Dev Phys"        	"isa0060/serio1/input0"
	Option        	"Device"        	"/dev/input/event2"
	Option        	"Buttons"        	"11"
	Option        	"ZAxisMapping"        	"4 5"
EndSection
```The thing is xev doesn't report any button presses when I press the side buttons of my MX510
```
LeaveNotify event, serial 29, synthetic NO, window 0x1c00001,
    root 0x119, subw 0x1c00002, time 2578353718, (40,39), root:(45,85),
    mode NotifyGrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 16

EnterNotify event, serial 29, synthetic NO, window 0x1c00001,
    root 0x119, subw 0x1c00002, time 2578354041, (40,39), root:(45,85),
    mode NotifyUngrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  25  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

```
However, when I have my ~/.xbindkeysrc set to ```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7
```xev reports the button presses as 8 and 9
It seems to be the ~/.xbindkeysrc that is causing a problem when I change 6 and 7 to 8 and 9
Do I need to modify anything in xorg.conf when I make changes to ~/.xbindkeysrc?

---

### Post by detyabozhye on 2006-06-03
1) Xgl works with evdev differently from regular Xorg, so if you are running Xgl, that may be part of your problem.

2) Use xmodmap to make the side buttons 6 an 7. Refer to my sig to see how.

---

### Post by Gtaylor on 2006-06-03
This works for me with a Logitech MX510 on Dapper. xmodmap seems to be quite unreliable:

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "5"
        Option          "ButtonMapping"         "1 2 3 6 7"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "false"
EndSection

```
The only problem is the button above the scroll wheel makes the browser go back instead of scrolling up, but I never use that silly little thing anyway. Thumb buttons work, mouse wheel scrolling works. You do -NOT- need any .xmodmap or imwheel modifications for this to work, just this edit of xorg.conf.

---

### Post by detyabozhye on 2006-06-03
Two problems with that: you already mentioned that the button above the scroll wheel works funny, some people use that button (I do).

The other problem is the tilt wheel won't work with that setup.

---

### Post by Gtaylor on 2006-06-03
[QUOTE=detyabozhye]Two problems with that: you already mentioned that the button above the scroll wheel works funny, some people use that button (I do).

The other problem is the tilt wheel won't work with that setup.[/QUOTE]
Assuming you don't use the top button, it's fine :) The original posts and replies don't work at all on my setup, this is a big step up from having nothing to having something.

And tilt wheel? What? On an MX510? I have a scroll wheel and that works fine.

---

### Post by detyabozhye on 2006-06-03
I mean for the higher models, and the link in my sig works with the older version of evdev perfectly.

---

### Post by DancingSun on 2006-06-04
[QUOTE=opticyclic]I now have evdev working and my xorg.conf looks like this```
Section "InputDevice"
	Identifier    	"Configured Mouse"
	Driver        	"evdev"
	Option        	"Protocol"        	"evdev"
	Option		"SendCoreEvents"	"true"
	Option        	"Dev Name"        	"PS2++ Logitech MX Mouse"
	Option        	"Dev Phys"        	"isa0060/serio1/input0"
	Option        	"Device"        	"/dev/input/event2"
	Option        	"Buttons"        	"11"
	Option        	"ZAxisMapping"        	"4 5"
EndSection
```The thing is xev doesn't report any button presses when I press the side buttons of my MX510[/QUOTE]
I used yours as a template and this worked fine for me in Ubuntu 6.06.  Here's mine:

```
Section "InputDevice"
     Identifier  "Mouse0"
     Driver      "evdev"
     Option      "Dev Name" "Logitech MX510"
     Option      "Dev Phys" "usb-0000:00:02.0-2/input0"
     Option      "Device" "/dev/input/event1" # (cat /proc/bus/input/devices)
     Option      "SendCoreEvents" "true"
     Option      "Buttons" "8"
     Option      "ZAxisMapping" "4 5"
EndSection
```

I don't have any mappings and the thumb buttons works fine in xev and in firefox.

---

### Post by opticyclic on 2006-06-04
[QUOTE=detyabozhye]1) Xgl works with evdev differently from regular Xorg, so if you are running Xgl, that may be part of your problem.

2) Use xmodmap to make the side buttons 6 an 7. Refer to my sig to see how.[/QUOTE]I don't think I am running Xgl. How can I tell?
I don't fully understand how xmodmap works. 
Your guide doesnt explain how to modify it for myself.
If I follow your guide X returns NULL for the Configured mouse.

All the buttons, inc. cruise control work perfectly with the basic conf
(I don't need to install click)
Its just the side buttons that are getting to me

**DancingSun: **You say you don't have any mappings.
Do you have your ~/.xbindkeysrc set?

---

### Post by opticyclic on 2006-06-04
Praise Be! [-o< 
The side buttons now work on my MX510! \\:D/
I followed this guide here
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Mouse+Buttons](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Mouse+Buttons)

xorg.conf now looks like this```
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "evdev"
        Option      "Device" "/dev/input/event2" # (cat /proc/bus/input/devices)
        Option      "Name" "Logitech MX510"
EndSection
```~/.xbindkeysrc looks like this```
"xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x10 + b:8
"xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x10 + b:9
```and ~/.Xmodmap looks like this ```
pointer = 1 3 2 4 5 8 9 6 7 10
```

---

### Post by detyabozhye on 2006-06-05
I set up a full guide here for evdev in Dapper.
[http://ubuntuforums.org/showthread.php?t=188302](http://ubuntuforums.org/showthread.php?t=188302)
I might change the HOWTO though, once I experiment with the new evdev driver which didn't work the last time I tried.

---

### Post by Gtaylor on 2006-06-05
Hrmm, apparently that button that I said was broken is only funky in Firefox. It appears to work just fine in everything else I've tried it with, must be a strange Firefox binding or something.

For MX510 users on Dapper, just set your mouse up in xorg.conf and don't bother with all this other stuff. Requires no real hacking and won't make your box act funky through later upgrades.

---

### Post by detyabozhye on 2006-06-06
Well, I'd say both methods are good. Those who don't have tilt wheel and don't mind a button working weird and want a simple solution, they can use your method.

But if people want their tilt wheel working and all the buttons too and they don't mind doing some work, my guide is for them.

---

### Post by Gtaylor on 2006-06-06
As mentioned, the **MX510** doesn't have a tilt wheel and the button works fine, Firefox has a weird binding that can be easily fixed. Hence, **anyone with an MX510 requires no special configuration**. I can't speak for others models, but for the **MX510**, this is fine. No tilt wheel, buttons are fine, etc.

It really is best to avoid installing and pinning outside packages and modifying a lot of config files if you can. Hence my recommendation for any **MX510** users to use the simple method. I'm going to do some more research and see if the other more advanced Logitech mice can be made to work within xorg.conf too.

---

### Post by GarethMB on 2006-06-06
i have x700 and i'm using aiglx and compiz the method described on the first page doesn't work for me. Does anyone know where i can find info on this?

Ie. i can't start x with new settings in xorg.conf

---

### Post by detyabozhye on 2006-06-06
[QUOTE=Gtaylor]As mentioned, the **MX510** doesn't have a tilt wheel and the button works fine, Firefox has a weird binding that can be easily fixed. Hence, **anyone with an MX510 requires no special configuration**. I can't speak for others models, but for the **MX510**, this is fine. No tilt wheel, buttons are fine, etc.

It really is best to avoid installing and pinning outside packages and modifying a lot of config files if you can. Hence my recommendation for any **MX510** users to use the simple method. I'm going to do some more research and see if the other more advanced Logitech mice can be made to work within xorg.conf too.[/QUOTE]
I know, I'm talking about mice like the Logitech MX1000 and Microsoft Intellimouse Explorer 4.0 (Wireless version is 2.0, I believe). They have tilt wheels, which won't work unless you use evdev. BTW, that's not exactly a Firefox problem, it's the driver, it's sending extra button signals, which it shouldn't. Both Firefox and Opera accept button signals higher than 7 as button 1 while the rest of the applications ignore higher numbers.

Currently, the evdev driver in Dapper is somewhat messed up, that's why it takes so many steps, like in my guide. Ideally, all it should take is editing xorg.conf, and if you want back/forward working in Nautilus, Konqueror, Epiphany, etc. you would also use xbindkeys, same as you would with your configuration.

---

### Post by detyabozhye on 2006-06-06
[QUOTE=GarethMB]i have x700 and i'm using aiglx and compiz the method described on the first page doesn't work for me. Does anyone know where i can find info on this?

Ie. i can't start x with new settings in xorg.conf[/QUOTE]
This guide won't work in Ubuntu 6.06, use this one: [http://ubuntuforums.org/showthread.php?t=188302](http://ubuntuforums.org/showthread.php?t=188302)
Or if you want am easier method, and don't mind one button acting a little weird, use Gtaylor's method.

---

### Post by px79 on 2006-06-13
Thanks for this great tutorial!

I am another Laptop user struggling with a Synaptics touchpad and a Logitech MX510 USB mouse. Up to now I discovered the following facts:

1. If you have your mouse NOT plugged in and start X it might crash, if your mouse is set as "CorePointer". A better way is to set the MX510 to "SendCoreEvents" and make the touchpad the "CorePointer", since this will always be "plugged in".

2. If you make your MX510 "SendCoreEvents", xmodmap won't be abel to rearrange the mouse buttons. Since xmodmap affects ONLY the "CorePointer". But you can use xinput (I guess you have to download it first). In my case the following line does the job:
```
xinput set-button-map MX510 1 2 3 6 7 8 4 5
```
"MX510" is the device name as defined in xorg.conf:
```
Section "ServerLayout"
	[...]
	InputDevice    "TouchPad"	"CorePointer"
	InputDevice    "MX510"		"SendCoreEvents"
EndSection

Section "InputDevice"
	Identifier  "TouchPad"
	Driver      "synaptics"
	Option      "Device" "/dev/input/mice"
	Option      "Protocol" "auto-dev" 
	Option      "LeftEdge" "1700"
	Option      "RightEdge" "5300"
	Option      "TopEdge" "1700"
	Option      "BottomEdge" "4200"
	Option      "FingerLow" "25"
	Option      "FingerHigh" "30"
	Option      "MaxTapTime" "180"
	Option      "MaxTapMove" "220"
	Option      "VertScrollDelta" "100"
	Option      "MinSpeed" "0.09"
	Option      "MaxSpeed" "0.25"
	Option      "AccelFactor" "0.0015"
	Option      "SHMConfig" "on"
EndSection

Section "InputDevice"
	Identifier  "MX510"
	Driver      "mouse"
	Option	    "Protocol" "evdev"
	Option      "Dev Name" "Logitech USB-PS/2 Optical Mouse"
	Option      "Dev Phys" "usb-*/input0"
	Option      "Device"   "/dev/input/mice"
	Option	    "Buttons" "8"
	Option	    "ZAxisMapping" "7 8"		# scroll wheel events
EndSection
```

3. What I didn't manage up to now: To enable full hotplug support. Which means, the MX510 will be recognized and enabled everytime I plug it in. But according to this information I guess it is not possible at the moment:
> Currently (as of release 6.7), the XOrg server does not support any form of hotplug for input devices. The server knows about those devices that were present and configured at the time it was started, but it is not possible to add or remove devices during the lifetime of the server.[http://wiki.x.org/wiki/XInputHotplug#head-ee046c3b0e1c1c1a9568779cc6a10159f2b7f063]("http://wiki.x.org/wiki/XInputHotplug#head-ee046c3b0e1c1c1a9568779cc6a10159f2b7f063")

There is a "hack" especially for this problem, but I didn't get it working: You may want to google for "X11_USBMICE_HACK".

4. What I discovered: If you start the X server with your mouse plugged in, you can remove it and plug it back in another USB port: You only have to switch away from the X server (e.g. ALT + CTRL + F1) and back to the X server (ALT + F7). But if you started X with your mouse unplugged I haven't found a way to tell X that the mouse is there now. :-( 

5. If you do not need the cruise control buttons, there IS a way to "enable full hotplug support". Since the touchpad will always be plugged in, X will always be aware of this device. So all you have to do is use the same "data stream" for your touchpad and your mouse:
In your xorg.conf set Option "Device" to "/dev/input/mice" and Option "Protocol" to "auto" for both devices (maybe the last part may be skipped for the touchpad).
If you have set the settings that way, you can plug your MX510 in whenever you want and it will work (at least on my laptop). But since you no longer use the "evdev" protocol your cruise-control-up-button will send a false back-button-event additionally.

That's what I know by now. If someone has any additional information, I would be happy to take note of those. :)

---

### Post by Poka64 on 2006-06-24
I followed the guide on the first page and I can't get this working, getting some io104 errror when I try to startx :(

this is my configs/cat on device etc..

```
I: Bus=0003 Vendor=046d Product=c01d Version=2100
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:13.1-1/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 ts0 event1
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

```

My xorg.

```
Section "InputDevice"
        Identifier    "Configured Mouse"
        Driver        "mouse"
    Option        "Protocol"        "evdev"
    Option        "Dev Name"        "Logitech USB-PS/2 Optical Mouse"
    Option        "Dev Phys" "usb-*/input0"        
    Option        "Device" "/dev/input/event1"       
    Option        "Buttons"        "10"
    Option        "ZAxisMapping"        "4 5"
EndSection
```

Anything that I can do to solve this ? :neutral:

Edit: Found the solution for Dapper: [http://www.ubuntuforums.org/showthread.php?t=188302](http://www.ubuntuforums.org/showthread.php?t=188302)

---

### Post by sinaen on 2006-07-04
Hello here. for about a second I thougt I was about to get crazy. you just babbled about buttons...
as john crichton says... "I don't care about the buttons" its a later problem.
finally at page 33 I saw that **some others** also had the same inclination to the same problem as I had had.;) 

What I discoverd with my laptop is that you cannot uncomment the standard mouse. "Configured Mouse" and I tried to set my logitech lx700 on an independent identifier. as you all know you should have wacom support (anyway I have it and i may have had it installed before and forgotten about it) in your files too. :-s 
And that doesn't screw up your X so why not I thought, if that can be there. And you don't have any wacom but have the support. Why cannot it be another identifier? :rolleyes: (that sounded something like yoda might have reasoned out 8-[ )

Said and done it worked like a charm. now I have 8 buttons. 
But I currently only use the scroll-wheel (buttons is a later problem) maybe ill install Counter-strike again.. it was a long time ago I had a mouse to play with.

This is my code. You should all be xorg.conf gurus by now. so you should manage it pretty easily.

```

Section "InputDevice"
**      Identifier      "Configured Mouse"**
      Driver          "mouse"
      Option          "CorePointer"
      Option          "Device"                "/dev/input/mice"
      Option          "Protocol"              "ExplorerPS/2"
      Option          "ZAxisMapping"          "4 5"  
      Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
**       Identifier    "logitech"**
       Driver        "mouse"
       Option        "Protocol"        "evdev"
       Option        "Dev Name"        "Logitech USB-PS/2 Optical Mouse"
       Option        "Dev Phys"        "usb-0000:00:1d.0-2/input0"
       Option        "Device"        "/dev/input/event2"
       Option        "Buttons"        "8"
       Option        "ZAxisMapping"        "4 5"
EndSection

Section "InputDevice"
      Identifier      "Synaptics Touchpad"
      Driver          "synaptics"
      Option          "SendCoreEvents"        "true"
      Option          "Device"                "/dev/psaux"
      Option          "Protocol"              "auto-dev"
      Option          "HorizScrollDelta"      "0"
EndSection


```
second code:
```
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
**        InputDevice     "logitech"**
EndSection

```

So when I set up this and rebooted. (yes that was neccesary and I don't know why.) it worked and it **scrolled** :p \\:D/

---

### Post by Znero on 2006-07-06
Hello.
I now have an MX 518 Mouse. After i Started with it, it worked great, and i was able to use the Side buttons to go trough Sites in Firefox. But i didnt work in Nautilus. Now i followed the Tutorial, and the Buttons now even dont work in Firefox.

Heres my xorg.conf:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/event2"
Option      "Name" "Logitech USB-PS/2 Optical Mouse"
	Option		"Protocol"		"evdev"
	Option		"ZAxisMapping"		"4 5"
        Option      "Buttons" "10"
        Option      "Resolution" "1600"
Option        "Dev Phys"        "usb-0000:00:03.0-1/input0"
EndSection
```

I didnt edit the xmodmap File, because it was said it is not necessary.

My xbindkeysrc is
```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
  m:0x0 + b:7
```
but with Capitols at Left/Right.

I didnt install the Logitech Applet, because it seems to only affect the DPI, not the Keys. And it also looks a bit out of date... (last changed 1 jear 9 months ago)

Can someone help me?

---

### Post by detyabozhye on 2006-07-06
1) This tutorial was meant for Breezy, see my signiture for Dapper.

2) Logitech Applet still works even though it's not the newest thing around. (Yes, it's only used for the DPI here)

3) Use xev to find out which button numbers are fired when you press buttons . (Talked about in the tut)

4) The new xvkbd packages have a different path for xvkbd, please see my sig for details.

---

### Post by Jorenko on 2006-07-08
This actually worked for me in Dapper with my MX700 with no additional packages installed; I just had to switch from Driver "mouse" and Option "Protocol" "evdev" to Driver "evdev":

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Dev Name"      "Logitech USB Receiver"
        Option          "Dev Phys"      "usb-*/input0"
        Option          "Device"        "/dev/input/event1"
        Option          "Buttons"       "8"
        Option          "ZAxisMapping"  "4 5"
EndSection
```

Thanks, guys!

---

### Post by ensiferum on 2006-07-14
I have mx500.

I found its very simple to get all buttons working using imwheel.

xorg.conf:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"             "ExplorerPS/2"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "4 5"
EndSection

start imwheel with
"imwheel -b "0089"

and its all set.

and yeah in imwheel.rc i only have

".*"
None,Up,Alt_L|Left
None,Down,Alt_L|Right

and thats that.

---

### Post by mandark on 2006-07-15
I have an old logitech mouse attached to a serial port<not usb or ps/2> on my comp.....it works fine with windows98/xp ,but isnt getting detected in ubuntu...ie i cant move the pointer around!!......is there anywhere i can find the drivers for the mouse..or is it just plain incompatible??

---

### Post by nickless on 2006-07-15
```
Error opening /dev/wacon : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
      No such file or directory
Error opening /dev/wacon : No such file or directory
No core pointer
```
I am pretty shure, that I've done everything right. Here's my xorg.conf:
> Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "Protocol" "evdev"
    Option        "Dev Name" "Logitech USB-PS/2 Optical Mouse"
    Option        "Dev Phys" "usb-*/input0"
    Option        "Device" "/dev/input/event2"
    Option        "Buttons" "8"
    Option        "ZAxisMapping" "4 5"
EndSection

#Section "InputDevice"
#    Identifier     "Configured Mouse"
#    Driver         "mouse"
#    Option         "CorePointer"
#    Option         "Device" "/dev/input/mice"
#    Option         "Protocol" "ExplorerPS/2"
#    Option         "ZAxisMapping" "4 5"
#    Option         "Emulate3Buttons" "true"
#EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection
But I am not shure what those wacom-devices are. I use no fancy stuff, just keyboard and mouse :D When I comment them out, it can't find my monitor... funny, hum? Confirmed "Dev Name", "Dev Phys" and "Device" everything like  cat said

---

### Post by mect on 2006-07-19
So I've tried lots of things to get my logitech mediaplay mouse working, including the driver by David Oliveira, with no luck.  I then tried following the steps introduced in this thread, but couldn't ever get xserver to work.  Finally, I found something that I will be content with for now as it appears that I have most of the buttons working.  Volume works, as do the play next and previous buttons.  While I can't get them to do anything yet, the back forward buttons give a button number in xev, so hopefully I can get those working.  All I did was assign a multimedia keyboard layout under regional settings.  Maybe someone has posted this before, but I've never seen it and thought I'd share just incase this is useful to someone else.  For me personally, the BTC 5090 works quite well for both my keyboard (generic multimedia) and my mouse.  Anyways, if you can't get anything else to work, you can try this.

---

### Post by StackError on 2006-07-31
Hello:

the url for the logitech_applet is 404! :<
i googled it but all links lead back to frogmouth.net

Ne one have a live link????

Thx

S

---

### Post by Malta Soron on 2006-08-09
I've got an MX518. I got the side buttons working in Firefox, but I wasn't succesfull in Nautilus. Although xev indicated that I should use button 6 and 7, it didn't work, so after trying for 45 minutes (and reconfiguring X.org like 7 times) I left it out.
There is a problem with the logitech applet:

```
jos@jos:~$ wget http://freshmeat.net/redir/logitech_applet/53319/url_tgz/logitech_applet-0.4test1.tar.gz
--17:54:58--  http://freshmeat.net/redir/logitech_applet/53319/url_tgz/logitech_applet-0.4test1.tar.gz
           => `logitech_applet-0.4test1.tar.gz'
Resolving freshmeat.net... 66.35.250.168
Connecting to freshmeat.net|66.35.250.168|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://www.frogmouth.net/logitech_applet-0.4test1.tar.gz [following]
--17:54:59--  http://www.frogmouth.net/logitech_applet-0.4test1.tar.gz
           => `logitech_applet-0.4test1.tar.gz'
Resolving www.frogmouth.net... 125.62.93.225
Connecting to www.frogmouth.net|125.62.93.225|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
17:55:00 ERROR 404: Not Found.

```

---

### Post by spacepirates on 2006-08-12
I've got a mx310 (mx 310) and cannot get it to work. i've been working on this for three days now, and am to the point where i am randomly assigning numbers hoping it might work.

the buttons have changed numbers now (scroll up/down was 4/5, now the side buttons scroll and are 4/5)

xev gives me no button number for (originally) the side buttons (now it gives no numbers for the scroll wheel)

i fear i have ruined the mouse configuration beyond repair...

```
#normal mouse settings
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

#logitech - side buttons for mouse
#Section "InputDevice"
#        Identifier	"Configured Mouse"
#        Driver		"mouse"
#	Option		"Protocol"		"evdev"
#	Option		"Dev Name"		"Logitech USB-PS/2 Optical Mouse"
#	Option		"Dev Phys"		"usb-0000:00:02.0-6/input0"
#        Option		"Device"		"/dev/input/event2"
#	Option		"Buttons"		"8"
#	Option		"ZAxisMapping"		"4 5"
#EndSection
```

is my xorg.conf for the moment (the logitech mouse settings are off of ticklemonster's), everytime i try to alter the file X crashes on reboot.

can someone please help me (a) restore the orignal mouse settings and then (b) get these side buttons to work and then maybe (c) figure out the code to have them switch workspaces?

thanks in advance!

---

### Post by dids22 on 2006-08-22
hey
i didnt read the all thread.
i got a problem, after i edited xorg file and restart xserver
i got message that thier is problem with xserver (i dont remmber its  exactly)
i give you  detail for what i did

first this is the output of cat /proc/bus/input/devices
```
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=046d Product=c025 Version=1800
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:02.0-4/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2
B: EV=40001
B: SND=6


```

and the output of xorg after i edited him
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"		"/dev/input/mice"
#	Option		"Protocol"		"ExplorerPS/2"
#	Option		"ZAxisMapping"		"4 5"
#	Option		"Emulate3Buttons"	"true"
#EndSection

Section "InputDevice"
        Identifier    "Configured Mouse"
        Driver        "mouse"
    Option        "Protocol"        "evdev"
    Option        "Dev Name"        "Logitech USB-PS/2 Optical Mouse"
    Option        "Dev Phys"        "usb-0000:00:02.0-4/input0"
        Option        "Device"      "/dev/input/event1"  
    Option        "Buttons"        "10"
    Option        "ZAxisMapping"        "4 5"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection



```

---

### Post by dids22 on 2006-08-22
i do all right?
ho i forget- my mouse is mx500

and now for the last output (xorg.0.log)
```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux chch-desktop 2.6.15-25-386 #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 22 15:00:20 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(==) |-->Input Device "Configured Mouse"
(WW) The core pointer device wasn't specified explicitly in the layout.
	Using the first mouse device.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,00e1 card 0000,0000 rev a1 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,00e0 card 1458,0c11 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,00e4 card 1458,0c11 rev a1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,00e7 card 1458,5004 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,00e7 card 1458,5004 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,00e8 card 1458,5004 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:05:0: chip 10de,00df card 1458,e000 rev a2 class 06,80,00 hdr 00
(II) PCI: 00:06:0: chip 10de,00ea card 1458,a002 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,00e5 card 1458,5002 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0a:0: chip 10de,00e3 card 1458,b002 rev a2 class 01,01,85 hdr 00
(II) PCI: 00:0b:0: chip 10de,00e2 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,00ed card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,00f1 card 1682,2119 rev a2 class 03,00,00 hdr 00
(II) PCI: 02:0b:0: chip 11ab,4320 card 1458,e000 rev 13 class 02,00,00 hdr 00
(II) PCI: 02:0d:0: chip 1095,3512 card 1095,6512 rev 01 class 01,04,00 hdr 00
(II) PCI: 02:0e:0: chip 104c,8025 card 1458,1000 rev 01 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:11:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xfaffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:14:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
	[4] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[5] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[6] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[7] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfb000000 - 0xfcffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x500fffff (0x100000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] rev 162, Mem @ 0xf8000000/24, 0xe0000000/28, 0xf9000000/24
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfc004000 - 0xfc007fff (0x4000) MX[B]
	[1] -1	0	0xfc008000 - 0xfc0087ff (0x800) MX[B]
	[2] -1	0	0xfc009000 - 0xfc0091ff (0x200) MX[B]
	[3] -1	0	0xfc000000 - 0xfc003fff (0x4000) MX[B]
	[4] -1	0	0xfd001000 - 0xfd001fff (0x1000) MX[B]
	[5] -1	0	0xfd000000 - 0xfd000fff (0x1000) MX[B]
	[6] -1	0	0xfd005000 - 0xfd0050ff (0x100) MX[B]
	[7] -1	0	0xfd004000 - 0xfd004fff (0x1000) MX[B]
	[8] -1	0	0xfd003000 - 0xfd003fff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[14] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[15] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[16] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[17] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[18] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[21] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[22] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[23] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[24] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[25] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[26] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[27] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[28] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[29] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[30] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[31] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfc004000 - 0xfc007fff (0x4000) MX[B]
	[1] -1	0	0xfc008000 - 0xfc0087ff (0x800) MX[B]
	[2] -1	0	0xfc009000 - 0xfc0091ff (0x200) MX[B]
	[3] -1	0	0xfc000000 - 0xfc003fff (0x4000) MX[B]
	[4] -1	0	0xfd001000 - 0xfd001fff (0x1000) MX[B]
	[5] -1	0	0xfd000000 - 0xfd000fff (0x1000) MX[B]
	[6] -1	0	0xfd005000 - 0xfd0050ff (0x100) MX[B]
	[7] -1	0	0xfd004000 - 0xfd004fff (0x1000) MX[B]
	[8] -1	0	0xfd003000 - 0xfd003fff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[14] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[15] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[16] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[17] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[18] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[21] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[22] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[23] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[24] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[25] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[26] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[27] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[28] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[29] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[30] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[31] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfc004000 - 0xfc007fff (0x4000) MX[B]
	[5] -1	0	0xfc008000 - 0xfc0087ff (0x800) MX[B]
	[6] -1	0	0xfc009000 - 0xfc0091ff (0x200) MX[B]
	[7] -1	0	0xfc000000 - 0xfc003fff (0x4000) MX[B]
	[8] -1	0	0xfd001000 - 0xfd001fff (0x1000) MX[B]
	[9] -1	0	0xfd000000 - 0xfd000fff (0x1000) MX[B]
	[10] -1	0	0xfd005000 - 0xfd0050ff (0x100) MX[B]
	[11] -1	0	0xfd004000 - 0xfd004fff (0x1000) MX[B]
	[12] -1	0	0xfd003000 - 0xfd003fff (0x1000) MX[B]
	[13] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[14] -1	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[16] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[20] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[21] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[22] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[23] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[24] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[27] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[28] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[29] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[30] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[31] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[32] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[33] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[34] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[35] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[36] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[37] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA X Driver  1.0-8762  Mon May 15 13:09:21 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfc004000 - 0xfc007fff (0x4000) MX[B]
	[5] -1	0	0xfc008000 - 0xfc0087ff (0x800) MX[B]
	[6] -1	0	0xfc009000 - 0xfc0091ff (0x200) MX[B]
	[7] -1	0	0xfc000000 - 0xfc003fff (0x4000) MX[B]
	[8] -1	0	0xfd001000 - 0xfd001fff (0x1000) MX[B]
	[9] -1	0	0xfd000000 - 0xfd000fff (0x1000) MX[B]
	[10] -1	0	0xfd005000 - 0xfd0050ff (0x100) MX[B]
	[11] -1	0	0xfd004000 - 0xfd004fff (0x1000) MX[B]
	[12] -1	0	0xfd003000 - 0xfd003fff (0x1000) MX[B]
	[13] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[14] -1	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[16] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[20] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[21] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[22] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[23] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[24] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[27] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[28] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[29] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[30] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[31] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[32] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[33] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[34] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[35] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[36] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[37] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfc004000 - 0xfc007fff (0x4000) MX[B]
	[5] -1	0	0xfc008000 - 0xfc0087ff (0x800) MX[B]
	[6] -1	0	0xfc009000 - 0xfc0091ff (0x200) MX[B]
	[7] -1	0	0xfc000000 - 0xfc003fff (0x4000) MX[B]
	[8] -1	0	0xfd001000 - 0xfd001fff (0x1000) MX[B]
	[9] -1	0	0xfd000000 - 0xfd000fff (0x1000) MX[B]
	[10] -1	0	0xfd005000 - 0xfd0050ff (0x100) MX[B]
	[11] -1	0	0xfd004000 - 0xfd004fff (0x1000) MX[B]
	[12] -1	0	0xfd003000 - 0xfd003fff (0x1000) MX[B]
	[13] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[14] -1	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[16] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[23] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[24] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[25] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[26] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[27] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[29] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[30] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[31] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[32] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[33] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[34] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[35] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[36] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[37] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[38] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[39] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[40] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[41] 0	0	0xfa0003b0 - 0xfa0003bb (0xc) IS[B]
	[42] 0	0	0xfa0003c0 - 0xfa0003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce 6600 GT at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.57.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6600 GT at PCI:1:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (CRT-1)
(--) NVIDIA(0): Samsung SyncMaster (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (83, 84); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[2] 0	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfc004000 - 0xfc007fff (0x4000) MX[B]
	[8] -1	0	0xfc008000 - 0xfc0087ff (0x800) MX[B]
	[9] -1	0	0xfc009000 - 0xfc0091ff (0x200) MX[B]
	[10] -1	0	0xfc000000 - 0xfc003fff (0x4000) MX[B]
	[11] -1	0	0xfd001000 - 0xfd001fff (0x1000) MX[B]
	[12] -1	0	0xfd000000 - 0xfd000fff (0x1000) MX[B]
	[13] -1	0	0xfd005000 - 0xfd0050ff (0x100) MX[B]
	[14] -1	0	0xfd004000 - 0xfd004fff (0x1000) MX[B]
	[15] -1	0	0xfd003000 - 0xfd003fff (0x1000) MX[B]
	[16] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[17] -1	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B](B)
	[18] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[19] -1	0	0xf8000000 - 0xf8ffffff (0x1000000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[26] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[27] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[28] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[29] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[30] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[31] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[32] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[33] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[34] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[35] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[36] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[37] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[38] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[39] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[40] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[41] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[42] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[43] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[44] 0	0	0xfa0003b0 - 0xfa0003bb (0xc) IS[B]
	[45] 0	0	0xfa0003c0 - 0xfa0003df (0x20) IS[B]
(II) NVIDIA(0): Setting mode "1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "evdev"
(EE) Configured Mouse: Unknown protocol "evdev"
(EE) PreInit failed for input device "Configured Mouse"
(II) UnloadModule: "mouse"
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(EE) Configured Mouse: Unknown protocol "evdev"
(EE) PreInit failed for input device "Configured Mouse"
(II) UnloadModule: "mouse"
(WW) No core pointer registered
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
No core pointer

Fatal server error:
failed to initialize core devices

```

do you know what the problem and how to fix it?
thnks

---

### Post by detyabozhye on 2006-08-22
If you're using Dapper, check the guide linked in my sig.

---

### Post by dids22 on 2006-08-23
i got the same probleam 
> Fatal server error:
failed to initialize core devices

---

### Post by pwner4once on 2006-08-25
i followed through the guide but i just can't get throug the xorg.conf part. it always gives me some kind of error. and say it's trying to find /sbin/wacom? O_O how is that even related to anything?

---

### Post by BLTicklemonster on 2006-09-01
> **spacepirates said:**
> (the logitech mouse settings are off of ticklemonster's), everytime i try to alter the file X crashes on reboot.

can someone please help me (a) restore the orignal mouse settings and then (b) get these side buttons to work and then maybe (c) figure out the code to have them switch workspaces?

thanks in advance!

Hey, definitely follow the guide here:

[http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894)

I just came back to Ubuntu after being away for a while (things to do I could only do in Windows, and I didn't need the distraction of Ubuntu being around, lol) and it worked first time. 

Thank you detyabozhye for that great guide!!!

---

### Post by geezerone on 2006-10-04
Hi

Tried configuring my MX510 and added the xbind code but the 'side' buttons don't show a button ID using 'xev' but just the following. The scroll buttons were working by default ok and these numbers are 8 and 9:

a FocusIn event, serial 29, synthetic NO, window 0x3000001,
    mode NotifyNormal, detail NotifyNonlinear

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

EnterNotify event, serial 29, synthetic NO, window 0x3000001,
    root 0x4c, subw 0x0, time 354632351, (155,165), root:(850,291),
    mode NotifyNormal, detail NotifyAncestor, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  76  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

---

### Post by hockeysk8 on 2006-12-27
I have posted complete instructions that are specific to the Logitech MX Revolution mouse at [http://rootsmith.ca/mxrev-linux.html]("http://rootsmith.ca/mxrev-linux.html").

---

### Post by Simon80 on 2007-01-13
I don't think I found similar info in this thread, so here's a [link]("http://ubuntuforums.org/showthread.php?t=65062") to my posting in a different thread, with instructions for how to get logitech_applet to run whenever a Logitech mouse is plugged in, rather than on boot.  Also, rather than adding a script in /etc/init.d, it would have been easier to run

sudo crontab -e

and then add a line into the crontab like so:

@reboot <command>

I got that from the Ubuntu Guide at some point.  However, it's not necessary now that you have a udev rule running the command.

---

### Post by Bryan Larsen on 2007-01-26
If it doesn’t work, try plugging it into a different USB port. I had everything configured correctly, and my Xorg.0.log output had lots of stuff about finding the mouse, detecting the buttons, et cetera, but then it had the lines:

(II) LogitechVX-usb-0000:00:1d.1-2/input0: On
(II) LogitechVX-usb-0000:00:1d.1-2/input0: Off

and my mouse wasn’t working. Removing the dongle from my powered USB hub and plugging it into my mainboard made everything work.

---

### Post by Jeeks on 2007-02-01
Ok, I fixed m Revolution VX but I would really like to know what is the syntax for the Fn key.

Another thing would be appreciated, the thumb buttons I assigned to Pgup and Pgdn but I would like it if I click and hold it will keep executing the key and not execute it only once. Is there a way to do that?

---

### Post by geezerone on 2007-02-25
Still can't get side buttons on my MX510 working (6 and 7) which in firefox move page down/up.

I have tried xmodmap to no avail. Here is my latest xorg info:

```
Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "Buttons" "7"
	Option	    "ZAxisMapping" "4 5"
	Option	    "ButtonMapping" "1 2 3 6 7"
	Option	    "Emulate3Buttons" "true"	
	#Option 	    "Resolution" "800
```

---

### Post by geezerone on 2007-03-05
<bump> Anyone??

---

### Post by DancingSun on 2007-03-05
> **geezerone said:**
> <bump> Anyone??

Make sure you follow Section 1 of the first post.  I see that your xorg.conf entry is not correct.

The Section 1 of the first post should at least get the side buttons working in Firefox as backward/forward.  To make it work in Nautilus, you'll need to do the key bindings.

It may be best to disable all your key binding for your mouse when following the instructions in the first post.

---

### Post by geezerone on 2007-03-07
Thanks for answering. Would the guide apply to using the mouse on PS/2 port also?

---

### Post by DancingSun on 2007-03-07
> **geezerone said:**
> Thanks for answering. Would the guide apply to using the mouse on PS/2 port also?

It should.  You can always disable your current mouse configuration in xorg.conf by commenting it out.  If the new configuration doesn't work, just delete the new configuration and enable the old one.

---

### Post by freakavoid on 2007-03-09
In case someone encounters the same problem:

Evdev doesn't support AllowMouseOpenFail, so if you want to use this driver on a computer which doesn't have the mouse plugged in all the time (e.g. a laptop) you might want to make your touchpad your primary input device i.e. corepointer and set the SendCoreEvents option in the configured mouse section to true. 

So, no more
```
No core pointer

Fatal server error:
failed to initialize core devices
```
(Actually this was for the searchers among us)

---

### Post by geezerone on 2007-03-11
Well, my cat /proc/bus/input/devices is as follows:

```
I: Bus=0011 Vendor=0002 Product=0002 Version=0064
N: Name="PS2++ Logitech MX Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event2 ts0
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

```

I inserted the following:

```
Section "InputDevice"
        Identifier    "Configured Mouse"
       Driver        "mouse"
  	Option        "Protocol"        "evdev"
    	Option        "Dev Name"        "PS2++ Logitech MX Mouse"
   	Option        "Dev Phys"        "isa0060/serio1/input0"
        Option        "Device"        	"/dev/input/event2"
    	Option        "Buttons"        	"10"
   	Option        "ZAxisMapping"  	"4 5"
EndSection
```

I restarted X but wouldn't start with "atomic" error :confused: 

I am using MX510 PS/2.

---

### Post by AnRkey on 2007-03-11
The more people who make a fuss about this spec the better. We need something like this for Ubuntu.

[https://blueprints.launchpad.net/ubuntu/+spec/gui-mouse-configuration](https://blueprints.launchpad.net/ubuntu/+spec/gui-mouse-configuration)

Take a look at the spec and subscribe to it to follow progress.

---

### Post by geezerone on 2007-03-17
Any ideas?

---

### Post by Rhombuss on 2007-03-17
I've tried this out using Ubuntu 6.10 with an MX500.

I followed the instructions but it won't reinitialize X.  I keep having to recover the initial parameters to get back into X.  I'm not sure if I'm doing something incorrectly, as it doesn't appear that many others have had problems reinitializing X, just getting the thumb buttons to work, etc.

Does it matter if I have my mouse plugged into my USB keyboard?  I was wondering if that would affect how the xorg.conf addresses are assigned for the USB devices.

Any help is appreciated!

---

### Post by geezerone on 2007-03-18
Try posting your xorg.conf here so it can be studied.

(still no thumb action here :(  )

---

### Post by Rhombuss on 2007-03-18
This is my xorg.conf:

> Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

#Section "InputDevice"
#       Identifier    "Configured Mouse"
#       Driver         "mouse"
#    	Option        "Protocol"	"evdev"
#    	Option        "Dev Name"     "B16_b_02 USB-PS/2 Optical Mouse"
#    	Option        "Dev Phys"       "usb-0000:00:1d.0-2.1/input0"
#       Option        "Device"        	"/dev/input/event1"
#    	Option        "Buttons"         "10"
#    	Option        "ZAxisMapping"    "4 5"
#EndSection

And this is my device listing (I included the mouse and keyboard hub listings):

> I: Bus=0003 Vendor=046d Product=c025 Version=9802
N: Name="B16_b_02 USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:1d.0-2.1/input0
S: Sysfs=/class/input/input0
H: Handlers=mouse0 event0 ts0 
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0003 Vendor=099a Product=800a Version=0102
N: Name="  Keyboard Hub"
P: Phys=usb-0000:00:1d.0-2.3/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=120003
B: KEY=10000 7 ff87207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: LED=7

I: Bus=0003 Vendor=099a Product=800a Version=0102
N: Name="  Keyboard Hub"
P: Phys=usb-0000:00:1d.0-2.3/input1
S: Sysfs=/class/input/input2
H: Handlers=kbd event2 
B: EV=f
B: KEY=c0002 400 0 0 1 c00 78000 2639fa d841d7ad 9e0000 0 0 0
B: REL=40
B: ABS=1 0


Thanks.

Hmm, I just noticed now that it's displaying my mouse as event0 and my keyboard hubs as event1 and event2.  Originally when I did the modifications, my keyboard hubs were event0 and event2, while my mouse was event1 (hence the event1 entry in the xorg.conf).  Perhaps I should take the mouse off my keyboard and plug it straight into my motherboard USB ports?

---

### Post by richdurhm on 2007-03-23
hey guys i have an mx 600 i tried this and now my mouse doens't work at all neither on windows i have to use my old mouse now any suggestions????? im me on aim at richdurhm

---

### Post by geezerone on 2007-03-23
It would make no diff to windows.

---

### Post by Skidpad on 2007-03-23
Just for reference, here's my X11 file.  I'm using an MX610 mouse.  The only thing that doesn't work is my cruise control; fwd/back/volume/scroll all work.  Cruise control (auto-scrolling when clicking the wheel and moving the mouse) is my next project.

[b]
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
        Option          "ButtonMapping"         "1 2 3 6 7" 
	Option		"Emulate3Buttons"	"true"
EndSection
[/b]

---

### Post by bryonak on 2007-04-01
Having only read the beginning of the thread I don't know if it's already been mentioned, but I'll post it anyways...
The solution with Xmodmap & xbindkeys has worked for me, with following exception to the .xbindkeysrc:

```

"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7

``` [COLOR="Red"][SIZE="5"]*[/SIZE][/COLOR]

instead of (as described on the first page):

```

"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
  m:0x0 + b:7

```

The difference being only the capitalization of "left" and "right"


Here's my xorg.conf:

```

Section "InputDevice"
        Identifier    "Configured Mouse"
        Driver        "evdev"
        Option        "CorePointer"
        Option        "Dev Name"        "Logitech USB-PS/2 Optical Mouse"
        Option        "Dev Phys"        "usb-*/input0"
        Option        "Device"          "/dev/input/event1"
        Option        "Protocol"        "evdev"
        Option        "Buttons"         "10"
        Option        "ZAxisMapping"    "4 5"
        Option        "ButtonMapping"   "1 2 3 4 5 6 7 8 9 10"
EndSection

```

and my .Xmodmap

```

pointer = 1 2 3 4 5 6 7 8 9 10 11 12

```


[COLOR="Red"][SIZE="5"]*[/SIZE][/COLOR] After previewing my post, it seems like the forum script converts "Left" and "Right" to "left" and "right", no matter whether I capitalize them in the reply text area... probably because of the brackets. Point is, "left" & "right" didn't work for me, "Left" & "Right" does.

---

### Post by Jump on 2007-04-03
> **Skidpad said:**
> Just for reference, here's my X11 file.  I'm using an MX610 mouse.  The only thing that doesn't work is my cruise control; fwd/back/volume/scroll all work.  Cruise control (auto-scrolling when clicking the wheel and moving the mouse) is my next project.

[b]
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
        Option          "ButtonMapping"         "1 2 3 6 7" 
	Option		"Emulate3Buttons"	"true"
EndSection
[/b]

THANK YOU!!!!

The original post did not work for me, but your recommendation worked perfectly on my MX518 w/ Edgy 6.10.

Thanks again!!!!!

:guitar:

---

### Post by sandman55 on 2007-04-04
I have a logitec MX500 and I havent been able to get it to work after the first bit 
sudo gedit /etc/X11/xorg.conf
but before I continue (and I'm going to try a few things) I want to know is this thread for  Dapper? or only edgy because I'm working with Dapper. Thanks

---

### Post by sandman55 on 2007-04-05
Can anyone answer are the instructions in this thread for Dapper or Edgy

---

### Post by detyabozhye on 2007-04-06
They're for Breezy as far as I remember. I have the ones for Dapper in my signiture which work for some in Edgy as well.

---

### Post by sandman55 on 2007-04-06
Thanks for that detyabozhye I was just about to install Edgy but I will try your site first, Im using Dapper to practice on first

---

### Post by Angry penguin on 2007-04-28
I am having difficulty getting this to work with my logitech mx500. I get the error:
unknown protocol "evdev"
and "failed to initialize core devices"

and something about wacom not initializing or something.

xorg:
```

#Section "InputDevice"
   # Identifier    "Configured Mouse"
   # Driver        "mouse"
   #  Option        "Device"          "/dev/input/event9"
   # Option        "Protocol"       "evdev"
   # Option        "ZAxisMapping"   "4 5"
   # Option        "Dev Name"       "Logitech USB-PS/2 Optical Mouse"
   # Option        "Dev Phys"        "usb-0000:00:02.0-1/input0"
  #  Option        "Buttons"        "9"
 #   Option		"CorePointer"
#EndSection

```

```

I: Bus=0003 Vendor=046d Product=c025 Version=0110
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:02.0-1/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse1 ts1 event1 
B: EV=20007
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103
B: LED=ff00

```

any ideas? I have been try to get this mouse to work since warty...

---

### Post by AnRkey on 2007-04-29
> **Angry penguin said:**
> I am having difficulty getting this to work with my logitech mx500. I get the error:
unknown protocol "evdev"
and "failed to initialize core devices"

and something about wacom not initializing or something.

xorg:
```

#Section "InputDevice"
   # Identifier    "Configured Mouse"
   # Driver        "mouse"
   #  Option        "Device"          "/dev/input/event9"
   # Option        "Protocol"       "evdev"
   # Option        "ZAxisMapping"   "4 5"
   # Option        "Dev Name"       "Logitech USB-PS/2 Optical Mouse"
   # Option        "Dev Phys"        "usb-0000:00:02.0-1/input0"
  #  Option        "Buttons"        "9"
 #   Option		"CorePointer"
#EndSection

```

```

I: Bus=0003 Vendor=046d Product=c025 Version=0110
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:02.0-1/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse1 ts1 event1 
B: EV=20007
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103
B: LED=ff00

```

any ideas? I have been try to get this mouse to work since warty...
Thist post works for Feisty >> [http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894)

It's pretty good and easy to do. It shows how to install evdev in the firt step or two.

Let us know if it works.

AnRkey

---

### Post by Angry penguin on 2007-04-29
> **AnRkey said:**
> Thist post works for Feisty >> [http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894)

It's pretty good and easy to do. It shows how to install evdev in the firt step or two.

Let us know if it works.

AnRkey

Unfortunately, I have already tried that tutorial as well. I believe evdev is installed by default in feisty because when I tried installing it, apt told me it was already. Despite the fact that evdev is installed, It still tells me unknown protocol, which makes no sense. Unless there is something that needs to point to it, or its looking in the wrong place. :confused:

EDIT: I think I have it figured out, I just had to pretty much use the default config for my mouse and add xbindkeys to get side buttons working in nautilus and firefox. Thanks!

---

### Post by DancingSun on 2007-04-29
> **Angry penguin said:**
> I am having difficulty getting this to work with my logitech mx500. I get the error:
unknown protocol "evdev"
and "failed to initialize core devices"

and something about wacom not initializing or something.

xorg:
```

#Section "InputDevice"
   # Identifier    "Configured Mouse"
   # Driver        "mouse"
   #  Option        "Device"          "/dev/input/event9"
   # Option        "Protocol"       "evdev"
   # Option        "ZAxisMapping"   "4 5"
   # Option        "Dev Name"       "Logitech USB-PS/2 Optical Mouse"
   # Option        "Dev Phys"        "usb-0000:00:02.0-1/input0"
  #  Option        "Buttons"        "9"
 #   Option		"CorePointer"
#EndSection

```

```

I: Bus=0003 Vendor=046d Product=c025 Version=0110
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:02.0-1/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse1 ts1 event1 
B: EV=20007
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103
B: LED=ff00

```

any ideas? I have been try to get this mouse to work since warty...

I noticed that, at a glance, your "Device" line in xorg.conf indicates "event9" while your cat output indicates "event1".

For what it's worth, I've fiddled around with my mouse configuration on and off, and I don't remember when did I last change it, but it seems like I can get by with just 3 lines of configuration code:
```
Section "InputDevice"
    Identifier     "Mouse1"
    Driver         "evdev"
    Option         "Device" "/dev/input/event9"
EndSection
```

---

### Post by AnRkey on 2007-04-29
Angry penguin: Glad to know it's working :)

AnRkey

---

### Post by measekite on 2007-09-27
> **iverson0881 said:**
> I have a MX700 and this worked fine although here is what I have in my xorg.conf:

```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Protocol"        "evdev"
    Option        "Dev Name"        "Logitech USB Receiver"    
    Option        "Dev Phys"        "usb-*/input1"
    Option        "Device"        "/dev/input/ts0"
    Option        "Buttons"        "10"
    Option        "ZAxisMapping"        "9 10"
EndSection
```My mouse is connected through the Ps/2 port of the computer while keyboard is connected through USB. I have the Logitech MX Duo

Could you post your /proc/bus/input/devices FILE

---

### Post by measekite on 2007-09-27
Originally Posted by **Angry penguin** 					[[IMG]http://ubuntuforums.org/images/uf/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=2556614#post2556614") 				
 				[I]I am having difficulty getting this to work with my logitech mx500. I get the error:
unknown protocol "evdev"
and "failed to initialize core devices"

and something about wacom not initializing or something.[/I]
     Option         "Device" "/dev/input/event9"
EndSection[/code][/quote]


I get exactly the same thing.  I do not know what to do next.  If you solve this one please post.  If anybody else has some ideas I sure would like to here them.

---

### Post by measekite on 2007-09-28
> **Angry penguin said:**
> I am having difficulty getting this to work with my logitech mx500. I get the error:
unknown protocol "evdev"
and "failed to initialize core devices"

and something about wacom not initializing or something.

xorg:
```

#Section "InputDevice"
   # Identifier    "Configured Mouse"
   # Driver        "mouse"
   #  Option        "Device"          "/dev/input/event9"
   # Option        "Protocol"       "evdev"
   # Option        "ZAxisMapping"   "4 5"
   # Option        "Dev Name"       "Logitech USB-PS/2 Optical Mouse"
   # Option        "Dev Phys"        "usb-0000:00:02.0-1/input0"
  #  Option        "Buttons"        "9"
 #   Option        "CorePointer"
#EndSection

``````

I: Bus=0003 Vendor=046d Product=c025 Version=0110
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:02.0-1/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse1 ts1 event1 
B: EV=20007
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103
B: LED=ff00

```any ideas? I have been try to get this mouse to work since warty...

I had the same thing.  I solved this by changing
Driver        "mouse"  to
Driver        "evdev"

All of the errors go away and the computer will boot X find.  The initial problem remains:  side button does not work.

---

### Post by Lord C on 2007-10-19
I have a MX1000 and I have spent hours trying to get the drivers to work as in this (and other very similar tutorials).

Here's my xorg.conf

Section "InputDevice"
    Identifier     "Logitech MX1000"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

#Section "InputDevice"
#    Identifier    ""Logitech MX1000"
#    Driver        "mouse"
#    Option        "Protocol"        "evdev"
#    Option        "Dev Name"        "Logitech USB RECEIVER"
#    Option        "Dev Phys"        "usb-*/input0"
#    Option        "Device"	    "/dev/input/event2"
#    Option        "Buttons"         "12"
#    Option        "ZAxisMapping"    "4 5"

#Section "InputDevice"
#Identifier 	"Logitech MX1000"
#Driver 		"evdev"
#Option			"CorePointer"
#Option 		"Protocol" 	"evdev"
#Option 		"Name" 	"Logitech USB RECEIVER"
#Option 		"Dev Phys" 	"usb-0000:00:10.0-2/input0"
#Option 		"Device" 	"/dev/input/mx1000"
#Option 		"Buttons" 	"12"
#Option 		"ZAxisMapping" 	"11 12 10 9"
#Option 		"Resolution" 	"800"
#Option			"Emulate3Buttons"	"false"
#EndSection

First block works obviously, default rubbish.
Second block gives error "Unknown protocol: evdev" even though of course evdev is installed.
With the third block, I tried editing udev, everything. Was getting NULL, it wasn't finding the device.

---

### Post by Lord C on 2007-10-19
Turns out I was giving far too much information to xorg.conf, all it needed was the device name.

For a more up to date tutorial, follow [https://help.ubuntu.com/community/MX1000Mouse](https://help.ubuntu.com/community/MX1000Mouse)

---

### Post by XavierGr on 2007-10-21
Following the tutorials I finally managed to get Kubuntu to recognize nearly all the keys on my G7 mouse. Though, despite all the reading I've never read about how to enable the resolution buttons.

In my case the default resolution of 800 dpi is identical for my habits, so  I want to utilize those two buttons with page up/down events (for fast scrolling). Any ideas on how to make those buttons configurable?

Thanks in advance.

---

### Post by XavierGr on 2007-10-21
To answer my own post:
Searching the net I encountered [this guide]("http://wiki.archlinux.org/index.php/Get_All_Mouse_Buttons_Working").
Using the tool near the botom of the page (g5hack), it should be able to remap the resolution (+,-) buttons too. 
Unfortunately it doesn't work for me, I hope that I am doing something wrong and I will be able to correct the problem.

---

### Post by MilitantPotato on 2007-11-26
```
Section "InputDevice"
	Identifier "Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device" "/dev/input/mice"
	Option		"Protocol" "ExplorerPS/2"
	Option		"ZAxisMapping" "4 5"
	Option		"ButtonMapping" "1 2 3 6 7"
	Option		"Emulate3Buttons" "true"
EndSection
```

Worked for a MX518 on Kubuntu Gutsy 7.10 in firefox.  Resolution changes also work.

---

### Post by superteodj on 2007-11-29
hi everyone!
my first post... my first question :) :
i configured the xbindkeysrc file as 

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xtest -text "\[Alt_L]\[F4]""
  m:0x0 + b:8
```

for a mx518. but, the alt+F4 combo doesnt work -.-... if leave te standard config ( alt_l+right) it works properly, but not with alt+F4 to close windows...
what's wrong?

thanks everyone ^^
ciao!

---

### Post by AbtZ on 2007-12-14
Great guide, now I can finally go back and forward with the mouse in Nautilus (something I think should be enabled by default, really).

Thanks!

---

### Post by Shakey_Jake33 on 2008-01-08
Awesome guide, works a charm :)

---

### Post by Exar Kun on 2008-01-10
I cant make my MX510 works with compiz-fusion it works fine when I disable it (compiz). I also try edved but when GDM starts half of the screen freeze this is how i configure xorg.conf. I don´t mind the extra buttons I just want to scroll up to work

> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"Buttons"	"5"
	Option		"ZAxisMapping"	"4 5"
	Option		"ButtonMapping"	"1 2 3 6 7"
EndSection 

---

### Post by harold4 on 2008-01-10
The following allows for all buttons, aside from the back/forward to work on my mx518.

```

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Resolution" "800"
Option "Buttons" "10"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"
EndSection

```

xev sees back/forward as button 6/7, but it is ignored by firefox and konqueror.

---

### Post by geezerone on 2008-01-12
My MX510 works apart from back/forward too - acts as scroll up.

Wonder if the latest Ubuntu has fixed this mouse button problem?

---

### Post by highstead on 2008-01-19
Hopefully someone still trolls here.  I've followed the guide but every time i've implemented it i get a graphical problem.  Now I've had this problem before when tweaking Xorg and its been with regards to the dual monitors but this would suggest that i'm not closing something?  My mouse section looks like this.

xorg.conf
[INDENT]Section "InputDevice"
    # generated from default
    Identifier    "Mouse0"
    Driver        "mouse"
    Option        "Protocol"        "evdev"
    Option        "Dev Name"        "Logitech USB-PS/2 Optical Mouse"
    Option        "Dev Phys"        "usb-0000:00:0a.0-1/input0"
    Option        "Device"          "/dev/input/event1"
    Option        "Buttons"         "10"
    Option        "ZAxisMapping"    "4 5"
#   Identifier     "Mouse0"
#   Driver         "mouse"
#   Option         "Protocol" "auto"
#   Option         "Device" "/dev/psaux"
#   Option         "Emulate3Buttons" "no"
#   Option         "ZAxisMapping" "4 5"
EndSection[/INDENT]

Devices:
[INDENT]I: Bus=0003 Vendor=046d Product=c01e Version=0110
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:0a.0-1/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=mouse1 event1
B: EV=7
B: KEY=ff0000 0 0 0 0
B: REL=103[/INDENT]


Kept Mouse0 because they section 'ServerLayout' Seems to refer to it.

Cheers

---

### Post by Microtome on 2008-01-24
> **highstead said:**
> Hopefully someone still trolls here.  I've followed the guide but every time i've implemented it i get a graphical problem.  Now I've had this problem before when tweaking Xorg and its been with regards to the dual monitors but this would suggest that i'm not closing something?  My mouse section looks like this.

xorg.conf
[INDENT]Section "InputDevice"
    # generated from default
    Identifier    "Mouse0"
    Driver        "mouse"
    Option        "Protocol"        "evdev"
    Option        "Dev Name"        "Logitech USB-PS/2 Optical Mouse"
    Option        "Dev Phys"        "usb-0000:00:0a.0-1/input0"
    Option        "Device"          "/dev/input/event1"
    Option        "Buttons"         "10"
    Option        "ZAxisMapping"    "4 5"
#   Identifier     "Mouse0"
#   Driver         "mouse"
#   Option         "Protocol" "auto"
#   Option         "Device" "/dev/psaux"
#   Option         "Emulate3Buttons" "no"
#   Option         "ZAxisMapping" "4 5"
EndSection[/INDENT]

Devices:
[INDENT]I: Bus=0003 Vendor=046d Product=c01e Version=0110
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:0a.0-1/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=mouse1 event1
B: EV=7
B: KEY=ff0000 0 0 0 0
B: REL=103[/INDENT]


Kept Mouse0 because they section 'ServerLayout' Seems to refer to it.

Cheers

Try checking out this page

[https://help.ubuntu.com/community/MX1000Mouse](https://help.ubuntu.com/community/MX1000Mouse)

This worked for me even though I am using a Logitech G5 and Gutsy. Plus it was much easier than the previous method. Which I too have spent hours trying to make work on my set-up. Of course you mileage may vary. Check out what changes I made to the directions on the page I listed above.


```

cat /proc/bus/input/devices

```
```

I: Bus=0003 Vendor=046d Product=c049 Version=0111
N: Name="Logitech USB Gaming Mouse"
P: Phys=usb-0000:00:10.2-2/input0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=mouse1 event1 
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

```
xorg.config
```

#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"	"/dev/input/mice"
#	Option		"Protocol"	"ImPS/2"
#	Option		"ZAxisMapping"	"4 5"
#	Option		"Emulate3Buttons"	"true"
#EndSection

Section "InputDevice"
        Identifier      "Logitech G5"
        Driver          "evdev"
        Option          "Name"          "Logitech USB Gaming Mouse"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection

```
Notice I only commented out the original mouse set up as I had to go back to that a couple of times to finally get it straightened out. You must also do the same to the Section "ServerLayout" seen here:
```

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
#	Inputdevice	"Configured Mouse"
        InputDevice     "Logitech G5" "CorePointer"
EndSection

```
The important part for this is to just comment out the "Configured Mouse" line and add the next line using the same Identifier, in my case "Logitech G5"
Hope this helps. 

Check me out, my first post is actually a contribution. :shock:

-Micro

---

### Post by ccdee on 2008-02-16
hmmmm


well my 518 works in every Linux except this one... tried Ubuntu, XUbuntu... but after 1 click the mouse is Stuck... no movement or click possible anymore.... so i can't even get a terminal up :S

---

### Post by skunkbad on 2008-02-16
I have a Logitech LX7, and running Ubuntu 7.10, and can't get the back/forward buttons working. I've looked at many of the guides here in the forum, and haven't been successful.

This is the mouse section of my xorg.conf:

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

#Section "InputDevice"
#       Identifier    "Configured Mouse"
#       Driver        "mouse"
#   	Option        "Protocol"        "evdev"
#   	Option        "Dev Name"        "Logitech USB RECEIVER"
#   	Option        "Dev Phys"        "usb-*/input0"
#       Option        "Device"          "/dev/input/event2"
#   	Option        "Buttons"        "10"
#   	Option        "ZAxisMapping"        "4 5"
#EndSection

```

I of course had it commented the other way, but it wasn't working.

Any help is appreciated.

---

### Post by orrie on 2008-03-01
I have now runned:
```
cat /proc/bus/input/devices
```

.. and that didn't do the thing.
I see the NVIDIA-splash and then X restarts and I see the Nvidia-splash again and then it restarts, and this keeps going on..

```

orrie ~ ;) cat /proc/bus/input/devices
...
...
I: Bus=0003 Vendor=046d Product=c01e Version=0110
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:0a.0-2/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=7
B: KEY=ff0000 0 0 0 0
B: REL=103
...
...


orrie ~ ;) cat /etc/X11/xorg.conf
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "no"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "Protocol"        "evdev"
    Option        "Dev Name"        "Logitech USB-PS/2 Optical Mouse"
    Option        "Dev Phys"        "usb-*/input0"
    Option        "Device"        "/dev/input/event2"
    Option        "Buttons"        "10"
    Option        "ZAxisMapping"        "4 5"
EndSection


#Section "InputDevice"
#    Identifier     "Configured Mouse"
#   Driver         "mouse"
#    Option         "CorePointer"
#    Option         "Device" "/dev/input/mice"
#    Option         "Protocol" "ImPS/2"
#    Option         "ZAxisMapping" "4 5"
#    Option         "Emulate3Buttons" "true"
#EndSection

Section "Monitor"
    Identifier     "Standard skjerm"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8800 Ultra]"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 Ultra"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8800 Ultra]"
    Monitor        "Standard skjerm"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x800" "1280x768" "1024x768"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: 1440x900 +1440+0; DFP-0: nvidia-auto-select +0+0, DFP-1: 1280x768 +1440+0; DFP-0: nvidia-auto-select +0+0, DFP-1: 1024x768 +1440+0"
EndSection

orrie ~ ;) cat /var/log/Xorg.0.log

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux ubuntu 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64
Build Date: 18 January 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar  1 22:03:53 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Configured Mouse"
(WW) The core pointer device wasn't specified explicitly in the layout.
	Using the first mouse device.
(**) Option "Xinerama" "0"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7cdb20
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,02f4 card 10de,02f4 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,02fa card 10de,02fa rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 10de,02fe rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 10de,02f8 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,02f9 card 10de,02f9 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,02ff card 10de,02ff rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,027f card 10de,027f rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,027e card 10de,027e rev a2 class 05,00,00 hdr 80
(II) PCI: 00:04:0: chip 10de,02fb card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:08:0: chip 10de,0369 card 1043,cb84 rev a1 class 05,00,00 hdr 00
(II) PCI: 00:09:0: chip 10de,0360 card 1043,cb84 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:09:1: chip 10de,0368 card 1043,cb84 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:09:2: chip 10de,036a card 1043,cb84 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:0a:0: chip 10de,036c card 1043,cb84 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:0a:1: chip 10de,036d card 1043,cb84 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:0c:0: chip 10de,036e card 1043,cb84 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:0d:0: chip 10de,037f card 1043,cb84 rev a2 class 01,01,85 hdr 80
(II) PCI: 00:0d:1: chip 10de,037f card 1043,cb84 rev a2 class 01,01,85 hdr 80
(II) PCI: 00:0d:2: chip 10de,037f card 1043,cb84 rev a2 class 01,01,85 hdr 80
(II) PCI: 00:0e:0: chip 10de,0370 card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:0e:1: chip 10de,0371 card 1043,81f6 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:10:0: chip 10de,0373 card 1043,cb84 rev a2 class 06,80,00 hdr 00
(II) PCI: 00:11:0: chip 10de,0373 card 1043,cb84 rev a2 class 06,80,00 hdr 00
(II) PCI: 00:16:0: chip 10de,0375 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0194 card 1682,2253 rev a2 class 03,00,00 hdr 00
(II) PCI: 02:0b:0: chip 104c,8023 card 1043,815b rev 00 class 0c,00,10 hdr 00
(II) PCI: 03:00:0: chip 1095,3132 card 1043,819f rev 01 class 01,80,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:4:0), (0,1,1), BCTRL: 0x001c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:9:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:14:0), (0,2,2), BCTRL: 0x0a04 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfdf00000 - 0xfdffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:22:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x0194) rev 162, Mem @ 0xfa000000/24, 0xe0000000/28, 0xf8000000/25, I/O @ 0xac00/7, BIOS @ 0xfbfe0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[1] -1	0	0xfdeff000 - 0xfdeff07f (0x80) MX[B]
	[2] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]
	[3] -1	0	0xfdfff000 - 0xfdfff7ff (0x800) MX[B]
	[4] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[5] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[6] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[7] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[8] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[9] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[10] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[11] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[12] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[13] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[14] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[15] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[16] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[17] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[18] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[19] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[20] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B]
	[21] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[22] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[23] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[24] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[25] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[26] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[28] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[29] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[30] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[31] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[32] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[33] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[34] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[35] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[36] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[37] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[38] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[39] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[40] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[41] -1	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[1] -1	0	0xfdeff000 - 0xfdeff07f (0x80) MX[B]
	[2] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]
	[3] -1	0	0xfdfff000 - 0xfdfff7ff (0x800) MX[B]
	[4] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[5] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[6] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[7] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[8] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[9] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[10] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[11] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[12] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[13] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[14] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[15] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[16] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[17] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[18] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[19] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[20] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B]
	[21] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[22] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[23] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[24] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[25] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[26] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[28] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[29] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[30] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[31] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[32] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[33] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[34] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[35] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[36] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[37] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[38] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[39] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[40] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[41] -1	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[5] -1	0	0xfdeff000 - 0xfdeff07f (0x80) MX[B]
	[6] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]
	[7] -1	0	0xfdfff000 - 0xfdfff7ff (0x800) MX[B]
	[8] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[9] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[10] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[11] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[12] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[13] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[14] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[15] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[16] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[17] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[18] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[19] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[20] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[21] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[22] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[23] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B]
	[27] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[28] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[29] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[30] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[31] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[32] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[33] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[34] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[35] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[36] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[37] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[38] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[39] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[40] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[41] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[42] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[43] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[44] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[45] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[46] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[47] -1	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:34:02 PST 2008
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  169.12  Thu Feb 14 17:53:48 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[5] -1	0	0xfdeff000 - 0xfdeff07f (0x80) MX[B]
	[6] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]
	[7] -1	0	0xfdfff000 - 0xfdfff7ff (0x800) MX[B]
	[8] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[9] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[10] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[11] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[12] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[13] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[14] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[15] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[16] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[17] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[18] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[19] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[20] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[21] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[22] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[23] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B]
	[27] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[28] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[29] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[30] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[31] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[32] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[33] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[34] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[35] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[36] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[37] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[38] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[39] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[40] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[41] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[42] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[43] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[44] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[45] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[46] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[47] -1	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[5] -1	0	0xfdeff000 - 0xfdeff07f (0x80) MX[B]
	[6] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]
	[7] -1	0	0xfdfff000 - 0xfdfff7ff (0x800) MX[B]
	[8] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[9] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[10] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[11] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[12] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[13] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[14] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[15] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[16] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[17] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[18] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[19] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[20] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[21] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[22] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[23] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[24] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[25] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[26] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[29] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B]
	[30] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[31] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[32] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[33] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[34] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[35] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[36] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[37] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[38] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[39] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[40] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[41] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[42] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[43] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[44] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[45] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[46] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[47] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[48] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[49] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[50] -1	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B](B)
	[51] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[52] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Screen0" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "DFP-0: nvidia-auto-select +0+0, DFP-1: 1440x900 +1440+0; DFP-0: nvidia-auto-select +0+0, DFP-1: 1280x768 +1440+0; DFP-0: nvidia-auto-select +0+0, DFP-1: 1024x768 +1440+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 8800 Ultra (G80) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 786432 kBytes
(--) NVIDIA(0): VideoBIOS: 60.80.18.00.13
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8800 Ultra at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(0):     Samsung SyncMaster (DFP-1)
(--) NVIDIA(0): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
(--) NVIDIA(0): Samsung SyncMaster (DFP-1): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Samsung SyncMaster (DFP-1): Internal Dual Link TMDS
(II) NVIDIA(0): Display Devices found referenced in MetaMode: DFP-0, DFP-1
(II) NVIDIA(0): Assigned Display Devices: DFP-0, DFP-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0,DFP-1:1440x900+1440+0"
(II) NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0,DFP-1:1280x768+1440+0"
(II) NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0,DFP-1:1024x768+1440+0"
(II) NVIDIA(0): Virtual screen size determined to be 2880 x 900
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[5] -1	0	0xfdeff000 - 0xfdeff07f (0x80) MX[B]
	[6] -1	0	0xfdff8000 - 0xfdffbfff (0x4000) MX[B]
	[7] -1	0	0xfdfff000 - 0xfdfff7ff (0x800) MX[B]
	[8] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[9] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[10] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[11] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[12] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[13] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[14] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[15] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[16] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[17] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[18] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[19] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[20] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[21] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[22] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[23] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[24] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[25] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[26] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[29] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B]
	[30] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[31] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[32] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[33] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[34] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[35] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[36] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[37] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[38] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[39] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[40] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[41] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[42] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[43] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[44] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[45] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[46] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[47] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[48] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[49] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[50] -1	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B](B)
	[51] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[52] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode
(II) NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0,DFP-1:1440x900+1440+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "no"
(**) Generic Keyboard: XkbLayout: "no"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "evdev"
(EE) Configured Mouse: Unknown protocol "evdev"
(EE) PreInit failed for input device "Configured Mouse"
(II) UnloadModule: "mouse"
(EE) Configured Mouse: Unknown protocol "evdev"
(EE) PreInit failed for input device "Configured Mouse"
(II) UnloadModule: "mouse"
(WW) No core pointer registered
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
No core pointer

Fatal server error:
failed to initialize core devices

```


How to fix it?
I've done it before, but doesn't remember much except fixing /etc/X11/xorg.conf.

---

### Post by AnRkey on 2008-03-02
Hi everyone

I am sure by now that this mouse button issue is driving everyone nuts. Vote here [http://brainstorm.ubuntu.com/idea/120/](http://brainstorm.ubuntu.com/idea/120/) for a mouse gui tool that already exists to be integrated into one of the next releases of Ubuntu.

And here is the launchpad listing for it >> [https://bugs.launchpad.net/ubuntu/+bug/146160](https://bugs.launchpad.net/ubuntu/+bug/146160) 

AnRkey

---

### Post by Teura on 2008-03-08
Ok, I have a problem with setting my MX900 mouse properly with this. Everytime I do this, my monitors gets messed up totally.

Normally, after Grub I get some blank screen and then login, but after I've done this change, first comes some text lines about boot, then Nvidia splash on both monitors, then same text, then again splash, and again text. It does this for a while, until it gives me the window about ubuntu running on low graphics mode on main monitor, second is not receiving image and is on standby 
And imagelink to how I see it: [http://koti.mbnet.fi/samikorh/Linux/low.jpg]("http://koti.mbnet.fi/samikorh/Linux/low.jpg").


Then, using keyboard, as seeing the mouse is kinda hard when you need to press the buttons, I can get to desktop, which looks the same, [http://koti.mbnet.fi/samikorh/Linux/desk.jpg]("http://koti.mbnet.fi/samikorh/Linux/desk.jpg").
Top half is totally messed up, and bottom left shows top right picture when bottom left shows top right.

So, is there any easy fix for this, or have I missed something? 
The link to MX1000 configuring a few posts above didn't work even though the poster also said about graphics problems after this, it gives the same result. I've tried searching around forums, with no avail.

And some specs / files that might be of importance in solving.
C2D E6600, 2bg ddr2 800mhz, Geforce 8800 GTS 512 (169.09 drivers, installed with Envy), Sony G500 21" CRT (main) and LG 99G 19" CRT(2nd, configured as separate X-screens with Xinerama), MX900 mouse (the same as MX500, only with Bluetooth), Logitech cordless elite for Bluetooth keyboard and 7.10 Gutsy 64-bit version of Ubuntu

The result of cat /proc/bus/input/devices, with only mouse revelant data (first is keyboard as far as I know, I left it there in case I have indeed had them wrong)
```
I: Bus=0003 Vendor=046d Product=c703 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.0-2.1/input0
S: Sysfs=/class/input/input7
U: Uniq=14F65B
H: Handlers=kbd event2 
B: EV=120003
B: KEY=1000000000007 ff800000000007ff febeffdfffefffff fffffffffffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c703 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.0-2.1/input1
S: Sysfs=/class/input/input8
U: Uniq=14F65B
H: Handlers=kbd mouse1 event3 
B: EV=f
B: KEY=7fff002c3027 bf00444000000000 ff0001 f808837c000 667bfad941dfed 9e000000000000 0
B: REL=143
B: ABS=100000000
```

And what I have changed to the xorg.conf mouse section.
```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "Protocol"        "evdev"
    Option        "Dev Name"        "Logitech USB Receiver"
    Option        "Dev Phys"        "usb-0000:00:1d.0-2.1/input1"
    Option        "Device"        "/dev/input/event3"
    Option        "Buttons"        "10"
    Option        "ZAxisMapping"        "4 5"
EndSection
```

If more details are needed, I'll happily post them.

---

### Post by geezerone on 2008-03-31
The following gets nearly all buttons working on my MX510 with the exception of the glide (press wheel down into mouse) which is shown on xev as button 2. The configurable button doesn't do anything either but doesn't show up under xev.

Anyone got the glide (various speed up/down scroll) to work?

TIA :-k

```
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Resolution" "800"
Option "Buttons" "10"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"
EndSection
```

---

### Post by geezerone on 2008-03-31
Also the up arrow performs 'go back' function:confused:

---

### Post by orrie on 2008-03-31
Adding the line below in bold font, does work excellent for me with MX518.

```

Section "InputDevice"
  Identifier    "Configured Mouse"
  Driver         "mouse"
  Option        "CorePointer"
  Option        "Device" "/dev/input/mice"
  Option        "Protocol" "ExplorerPS/2"
  Option        "ZAxisMapping" "4 5"
  Option        "ButtonMapping" "1 2 3 6 7"
  **Option    "Emulate3Buttons" "true"**
EndSection

```

---

### Post by AnRkey on 2008-04-01
Hi every1

Just a reminder that all these problems can be fixed if we all vote for this idea on [http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com)

[http://brainstorm.ubuntu.com/idea/120](http://brainstorm.ubuntu.com/idea/120)

Hopefully someone will pick it up and start working on it soon.

Thanks,

R

---

### Post by m1garand on 2008-07-09
Why does my mouse in Hardy LiveCD work fine(scroll, back, forward)?   And after installing Hardy, we have to go through all of this?

---

### Post by kiev on 2008-08-13
If I add Option        "Protocol"        "evdev"
my usb mouse not work!

heelp!!!

---

### Post by Armaron on 2008-09-12
> **kiev said:**
> If I add Option        "Protocol"        "evdev"
my usb mouse not work!

heelp!!!

Try:

Driver "evdev"

instead of the Option thing. Don't forget to put a # infront of the

Driver "mouse"

line.

EDIT -

On the mouse is a button that in windows is like Alt+Tab. How can I get that functionality back?

---

### Post by detyabozhye on 2008-09-14
> **Armaron said:**
> On the mouse is a button that in windows is like Alt+Tab. How can I get that functionality back?

You'll need a program with a window list and bind the button to the command for that. Xfce has one built in, it's xfdesktop -windowlist. Other DE's need a seperate program for that.

---

### Post by Armaron on 2008-09-15
Ok, I seem to have a bit of an annoying problem on my hands.

Each time I restart, I need to go into the console and give the xorg.conf file the right event handler for my mouse. I haven't gotten it to work automatically so that the X server knows which event is my mouse. Any idea's on how to do it?

P.S. detya, do you know a program to do that for ubuntu with the gnome desktop? I'd rather not switch to the Xfce desktop. :)

---

### Post by detyabozhye on 2008-09-17
> **Armaron said:**
> Ok, I seem to have a bit of an annoying problem on my hands.

Each time I restart, I need to go into the console and give the xorg.conf file the right event handler for my mouse. I haven't gotten it to work automatically so that the X server knows which event is my mouse. Any idea's on how to do it?

P.S. detya, do you know a program to do that for ubuntu with the gnome desktop? I'd rather not switch to the Xfce desktop. :)

You can use udev, but this thread is very old and the method of setting up the mouse has long since changed. If you click to see the thread in my signiture, somewhere towards the end of it people talk about the new way of configuring it. For example, my current set up is:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "Device" "/dev/input/by-id/usb-Logitech_USB-PS.2_Optical_Mouse-event-mouse"
EndSection

```

---

### Post by reg4c on 2008-10-08
Excellent

I used the xbindkeys with --keys thing to make the nautilus for forward and backwards with SHIFT MOUSE DOWN and SHIFT MOUSE UP

Thanks a lot

---

### Post by BassKozz on 2008-11-04
I am having a hellava time getting my M_x_500 working in Intrepid, this seems like the right place to post, but I feel this information is a bit dated since Input Devices aren't handled by Xorg.conf anymore but instead by HAL...
I've already posted a whole novel on my research thus far in another thread, so rather then repost it all here, I hope you don't mind me linking to it: [Mouse Wheel Broken in Intrepid]("http://ubuntuforums.org/showthread.php?t=970711")

If anyone can help PLEASE [-o<

[[IMG]http://brainstorm.ubuntu.com/idea/120/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/120/)

---

### Post by jimgeroul on 2008-11-10
I have the "Trust MI7700R wireless laser" mouse witch has 8 buttons.
4 wheel buttons (up, down, left, right) - WORKING
2 side buttons (thumb1, thumb2) - WORKING
2 media buttons (for zoom in-out) - NOT WORKING

why i can't have these 2 buttons enabled??
Button Mapping for them should be "button 10" and "button 11" but they are not even recognized from xev. everything else works perfectly by default (ubuntu 8.10 intrepid).

What can i do?? can i enable them?

---

### Post by detyabozhye on 2008-11-11
@BassKozz: @jimgeroul: What do you get in xev for all the buttons?

---

### Post by jimgeroul on 2008-11-11
this is what i get when i press all mouse buttons. As you will see all button except buttons 10,11 have an "entry". When i press button 10 or 11 nothing happens, nothing is changing :(

```
KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  62  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5006722, (33,25), root:(584,427),
    state 0x110, button 1, same_screen YES

LeaveNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x0, time 5006722, (33,25), root:(584,427),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

ButtonPress event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5007428, (33,25), root:(584,427),
    state 0x10, button 3, same_screen YES

EnterNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x0, time 5007428, (33,25), root:(584,427),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 1040

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  4294967206 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5007474, (33,25), root:(584,427),
    state 0x410, button 3, same_screen YES

LeaveNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x0, time 5007474, (33,25), root:(584,427),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

MotionNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5008554, (31,26), root:(582,428),
    state 0x10, is_hint 0, same_screen YES

MotionNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5008562, (30,27), root:(581,429),
    state 0x10, is_hint 0, same_screen YES

MotionNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5008570, (29,27), root:(580,429),
    state 0x10, is_hint 0, same_screen YES

MotionNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5008578, (28,27), root:(579,429),
    state 0x10, is_hint 0, same_screen YES

MotionNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5008586, (28,28), root:(579,430),
    state 0x10, is_hint 0, same_screen YES

ButtonPress event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5010394, (28,28), root:(579,430),
    state 0x10, button 2, same_screen YES

EnterNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x0, time 5010394, (28,28), root:(579,430),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 528

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  4294967206 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5010578, (28,28), root:(579,430),
    state 0x210, button 2, same_screen YES

LeaveNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x0, time 5010578, (28,28), root:(579,430),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

LeaveNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5012466, (28,28), root:(579,430),
    mode NotifyGrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 2064

EnterNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5012466, (28,28), root:(579,430),
    mode NotifyUngrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  4294967206 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonPress event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5012467, (28,28), root:(579,430),
    state 0x10, button 4, same_screen YES

EnterNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x0, time 5012467, (28,28), root:(579,430),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 2064

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  4294967206 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5012467, (28,28), root:(579,430),
    state 0x810, button 4, same_screen YES

LeaveNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x0, time 5012467, (28,28), root:(579,430),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

LeaveNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5013114, (28,28), root:(579,430),
    mode NotifyGrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 4112

EnterNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5013114, (28,28), root:(579,430),
    mode NotifyUngrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  4294967206 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonPress event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5013115, (28,28), root:(579,430),
    state 0x10, button 5, same_screen YES

EnterNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x0, time 5013115, (28,28), root:(579,430),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 4112

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  4294967206 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5013115, (28,28), root:(579,430),
    state 0x1010, button 5, same_screen YES

LeaveNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x0, time 5013115, (28,28), root:(579,430),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

LeaveNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5013850, (28,28), root:(579,430),
    mode NotifyGrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 16

EnterNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5013850, (28,28), root:(579,430),
    mode NotifyUngrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  4294967206 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonPress event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5013851, (28,28), root:(579,430),
    state 0x10, button 6, same_screen YES

EnterNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x0, time 5013851, (28,28), root:(579,430),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  4294967206 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5013851, (28,28), root:(579,430),
    state 0x10, button 6, same_screen YES

LeaveNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x0, time 5013851, (28,28), root:(579,430),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

LeaveNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5014578, (28,28), root:(579,430),
    mode NotifyGrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 16

EnterNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5014578, (28,28), root:(579,430),
    mode NotifyUngrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  4294967206 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonPress event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5014579, (28,28), root:(579,430),
    state 0x10, button 7, same_screen YES

EnterNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x0, time 5014579, (28,28), root:(579,430),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  4294967206 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5014579, (28,28), root:(579,430),
    state 0x10, button 7, same_screen YES

LeaveNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x0, time 5014579, (28,28), root:(579,430),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

MotionNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5014762, (27,28), root:(578,430),
    state 0x10, is_hint 0, same_screen YES

LeaveNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5014794, (27,28), root:(578,430),
    mode NotifyGrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 16

EnterNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5014794, (27,28), root:(578,430),
    mode NotifyUngrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  4294967206 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonPress event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5014802, (27,28), root:(578,430),
    state 0x10, button 7, same_screen YES

EnterNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x0, time 5014802, (27,28), root:(578,430),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  4294967206 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5014803, (27,28), root:(578,430),
    state 0x10, button 7, same_screen YES

LeaveNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x0, time 5014803, (27,28), root:(578,430),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

LeaveNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5016634, (27,28), root:(578,430),
    mode NotifyGrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 16

EnterNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5016635, (27,28), root:(578,430),
    mode NotifyUngrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  4294967206 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonPress event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5016636, (27,28), root:(578,430),
    state 0x10, button 8, same_screen YES

EnterNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x0, time 5016636, (27,28), root:(578,430),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  4294967206 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5016637, (27,28), root:(578,430),
    state 0x10, button 8, same_screen YES

LeaveNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x0, time 5016637, (27,28), root:(578,430),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

ButtonRelease event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5016810, (27,28), root:(578,430),
    state 0x10, button 8, same_screen YES

LeaveNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5017322, (27,28), root:(578,430),
    mode NotifyGrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 16

EnterNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5017323, (27,28), root:(578,430),
    mode NotifyUngrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  4294967206 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonPress event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5017324, (27,28), root:(578,430),
    state 0x10, button 9, same_screen YES

EnterNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x0, time 5017324, (27,28), root:(578,430),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  4294967206 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5017324, (27,28), root:(578,430),
    state 0x10, button 9, same_screen YES

LeaveNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x0, time 5017324, (27,28), root:(578,430),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

ButtonRelease event, serial 34, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 5017514, (27,28), root:(578,430),
    state 0x10, button 9, same_screen YES

```

---

### Post by detyabozhye on 2008-11-11
@jimgeroul: try installing lomoco and try turning on/off the cruise control: [http://manpages.ubuntu.com/manpages/gutsy/man1/lomoco.html](http://manpages.ubuntu.com/manpages/gutsy/man1/lomoco.html) That might have some effect on the media buttons.

Edit: Then again, it might not work since that's not a Logitech mouse.

---

### Post by jimgeroul on 2008-11-13
I installed lomoco and made the changes you said but nothing... maybe my Trust mouse is not 100% supported and there is nothing i can do.
Thanks for you help though!

---

### Post by carthage on 2009-01-02
thank u so much it worked for me [http://ubuntuforums.org/images/smilies/icon_biggrin.gif](http://ubuntuforums.org/images/smilies/icon_biggrin.gif)

---

### Post by Dirtneck on 2009-03-20
**[COLOR="Blue"]Specific requirement: assign a modifier to a thumb button[/COLOR]**

I'm trying to configure the thumb/side buttons of a Logitech MX620 to work as I need. I play WoW and want to assign a modifier only to those buttons (pressing the backward thumb button should work the same as holding shift on the keyboard)

The reason this poses a problem:

The thumb buttons do not perform the same as other buttons like Mouse button 1. 

**Using xev:**

**Example using Mouse Button 1**:
1) I press mouse button 1
2) the keydown event is triggered
3) I release mouse button 1
4) the keyup event is triggered



**Example using a thumb button**:
1) I press a thumb button
2) the keydown event is triggered AND immediately the keyup event also triggers
3) I release mouse button 1
4) n/a

So in my attempt to emulate a shift modifier, if I assigned 'Shift_L' to the thumb button I would expect to press the thumb button and then press a letter on the keyboard and I should get an uppercase letter printed. However, what actually happens with those actions is Shift_L gets pressed and depressed and then the letter is printed without the modifier.

I know this is not a mechanical limitation of the buttons as it those buttons can indeed work the way I need in windows using logitech product software.

Note: I haven't tried to get the mentioned app working with wine yet but really dont want to resort to that anyways.

I don't know if xmodmap would resolve my issue but hopefully someone with a full understanding of it could reply. As of right now, modmap is the blind direction I'll be taking.



Here's my Xbindkeysrc which I'm pretty sure has no bearing but might help:

[COLOR="Teal"][SIZE="1"][FONT="Verdana"]	
	
# Logitech Custom Mouse buttons [MX620]:
# ===============================================================================================
# 1) Left Click
# 2) Middle Mouse Button
# 3) Right Click
# 4) Scroll Up
# 5) Scroll Down
# 6) Wheel L-Tilt
# 7) Wheel R-Tilt
# 8) Side-Backward
# 9) Side-Forward
# 10) Search Button ??? 	 

   
	# ==============================================================================================
	# ----------------------------------------------------------------- Left-Side Buttons ----------
	# --> Logitech Fwd
	"/usr/bin/xte 'key Alt_R' &"
	   m:0x0 + b:9			# Forward

	# --> Logitech Bck
	"/usr/bin/xte 'key Shift_R' &"
	   m:0x0 + b:8			# Backward
	# ==============================================================================================


	# ==============================================================================================
	# --------------------------------------------------------------- Mouse Wheel Tilting ----------
	# --> Logitech L-Tilt
	"/usr/bin/xte 'keydown Alt_R' 'keydown Shift_R' 'key K' 'keyup Shift_R' 'keyup Alt_R' &"
	   m:0x0 + b:6			# Left Tilt = Shift+Alt+R
	   
	# --> Logitech R-Tilt
	"/usr/bin/xte 'keydown Alt_R' 'keydown Shift_R' 'key L' 'keyup Shift_R' 'keyup Alt_R' &"
	   m:0x0 + b:7			# Right Tilt = Shift+Alt+L
	# ==============================================================================================


	# ===============================================================================================
	# Zboard Custom Keys:
	# ===============================================================================================

	# --> Zboard Pause Key
	"/usr/bin/xte 'keydown Alt_R' 'keydown Shift_R' 'key P' 'keyup Shift_R' 'keyup Alt_R' &"
	    m:0x10 + c:127
	    Mod2 + Pause 				# Gaming pad; Pause key
	# --> Zboard Cons Key
	"/usr/bin/xte 'keydown Alt_R' 'keydown Shift_R' 'key O' 'keyup Shift_R' 'keyup Alt_R' &"
	    m:0x10 + c:49
	    Mod2 + grave 				# Gaming pad; Cons key
	# ==============================================================================================

[/FONT][/SIZE][/COLOR]

---

### Post by Dirtneck on 2009-03-20
BTW: I've noticed in this thread that people have problems getting any event to work in xbindkeys. 
[COLOR="Red"]
**Check that xbindkeys is successfully running**[/COLOR]


1) Make sure xbindkeys process is stopped or you wont be able to save the xbindkeysrc file.
2) attempting to start xbindkeys may fail on _syntax errors_ in the xbindkeysrc file.
3) check to see if there's any other listener processes running that inhibit xbindkeys from starting: run **xbindkeys -v** to see if it starts ok... It will complain if xbindkeys is already started or if there's another event listener causing trouble.

---

### Post by dnquark on 2009-07-21
I am having trouble remapping the one-touch search button on Logitech MX Revolution (apparently it generates keycode 225).  I tried to edit xmodmap to remove the XF86Search binding from keycode 225, and it's no longer there; then I tried to use xbindkeys with xmacro to issue some alternative keypresses for keycode 225, but nothing seems to work - the search button still brings up the search dialog!  Does anyone have a fix?..

---

### Post by expxe on 2009-11-25
OMG, is there a simple install program to do all of this? lets keep it simple people!

---

### Post by detyabozhye on 2009-11-26
Most of it actually works out of the box now. This tutorial is a few years old and shouldn't keep getting bumped anymore.

---

### Post by expxe on 2009-11-28
> **detyabozhye said:**
> Most of it actually works out of the box now. This tutorial is a few years old and shouldn't keep getting bumped anymore.

my logitech mx rev doesn't exactly "work out of the box", ubuntu needs proper mouse drivers from logitech really

---

