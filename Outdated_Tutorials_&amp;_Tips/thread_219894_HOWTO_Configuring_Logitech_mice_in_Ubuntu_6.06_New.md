---
title: "HOWTO: Configuring Logitech mice in Ubuntu 6.06: New Guide"
date: 2006-07-20
forum: Outdated Tutorials &amp; Tips
---

### Post by detyabozhye on 2006-07-20
[COLOR="Red"]*70.06.19: I've made a major update to this guide for Ubuntu 6.10 and 7.04. Tell me if I made any mistakes.*[/COLOR]

**_A COMPLETE guide to a Logitech mouse_**

*[COLOR="Red"]Note: Some have complained that this guide is too complicated (they should see the old guide, about twice the length). Well, I won't argue, but I'd like to point out that sections 2 and 3 are optional and there is an [alternative method](http://ubuntuforums.org/showpost.php?p=1295974&postcount=13) for Section 1 as well, but my method will greatly increase the functionality of the mouse.[/COLOR]*

This is my guide on how to get all the buttons working properly on a logitech mouse (loosely based on Endy's guide), how to use lmctl to enable the higher resolutions and cruise control and how to get the side mouse buttons to make forwards and back work in Nautilus, Epiphany, Konqueror, etc.

This works for my mx500, it should work for the similar mx510 and mx518 and the wireless versions like the mx700 however, they may require slightly different configurations. Higher models, such as the MX1000 and the G series definatley need config changes, especially in the xbindkeys area.

**_Prerequisite: Installing evdev_**

[INDENT]Evdev was installed by default on my system, but some people didn't have it installed by default. So if you don't, run this command to install it:

```
sudo apt-get install xserver-xorg-input-evdev
```[/INDENT]

**_Section 1: Getting your mouse working on USB with evdev_**

[INDENT]First off you need to plug your mouse into a USB port, you can't do anything else in this how to until you do that.

_1. Getting all the information you need_

Great, so we're all plugged in via USB and ready to go. Before we change anything we need to get some important information about the mouse so run the following command in your favourite terminal:

```
cat /proc/bus/input/devices
```

You should get a list of details, here's what I get and I'll highlight the bit we need to concentrate on:

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

_2. Adding a udev rule_

Adding a udev rule in MOST cases is not necessary anymore, therefore it has been removed.

_3. Editing the xorg.conf file_

First, let's back it up in case you mess anything up:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Now we have the information we need to start to set up xorg. So open up your xorg.conf file in your favourite editor, mine is mousepad but as gedit is on everyone elses install by default you can type:

```
sudo gedit /etc/X11/xorg.conf
```

Now scroll down to the mouse section and replace it with:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"Logitech USB-PS/2 Optical Mouse" #this should be the name of the device which I made bold here.
EndSection
```

Make sure you save the changes to your xorg file.

_4. Restart udev and Xorg_

_Warning!_
Don't restart yet! Just before we do I have to warn you if you made a mistake in the xorg file X will not start. But don't worry that's why we backed up the previous file. If X fails to start then you will end up in a text console. Log in and type the following to rename the current xorg.conf and restore the previous file:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-logi
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

_Ok, I'm ready_
Now we're prepared, restart evdev by typing:
```
sudo /etc/init.d/udev restart
```
Then restart Xorg by logging out and pressing Alt+Ctrl+Backspace. Then log back in.[/INDENT]

**_Section 2: Side buttons and Nautilus, Epiphany, Konqueror, etc (Optional)_**

[INDENT]We can use "xvkbd" and "xbindkeys" to bind the side mouse buttons to "ALT + LEFT" and "ALT + RIGHT" so they work as forward and backwards in Nautilus.

_1. xvkbd and xbindkeys_

Lets install "xvkbd" and "xbindkeys":

```
sudo apt-get install xvkbd xbindkeys
```

Next we need to create the configuration for them:

```
gedit ~/.xbindkeysrc
```

Now paste the following (for MX500, MX510, MX518, MX700):

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[_L_eft]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[_R_ight]""
  m:0x0 + b:7
```

*For mice with a tilt wheel (such as the MX1000), you would most likely change b:6 to b:8 and b:7 to b:9.*

Make sure you keep the quote marks, save the file and run "xbindkeys" in the terminal. It runs as a daemon in the background. You should now be able to test if it works in Nautilus by using the side buttons it also works in Epiphany if you use it.

*Note: Same as before, if you have different mouse buttons use xev to find out what number they are and change the "b:6" and "b:7" in the above to the correct numbers.*

_2. Fixing the cruise control buttons (MX500, MX510, MX700, MX1000):_

[COLOR="Red"]*Note: In Edgy and Feisty I haven't noticed this problem anymore (I've had cruise control off for a while though), but I will leave this section here because it hasn't been confirmed that the problem is gone.*[/COLOR]

Install these packages for "click" to compile:

```
sudo apt-get install build-essential libx11-dev x11proto-xext-dev libxtst-dev
```

Download and untar "click" source code into ~/.click (or wherever you want, just remember the dir, you'll need it in the .xbindkeysrc):

```
cd ~/
wget http://bg.rifetech.com/click.tgz
tar xvfz click.tgz
mv click .click

```

then compile it:

```
cd ~/.click
make
```

Then add this to you .xbindkeysrc (gedit ~/.xbindkeysrc):

```
"~/.click/click 4"
  m:0x0 + b:9
"~/.click/click 5"
  m:0x0 + b:10
```

*Note: Mice with more buttons and/or tilt wheels will most likely have different button numbers, please check in xev.*

_3. Adding it to your session_

Now it's working open up the gnome sessions settings "System > Preferences > Sessions" click on the "Startup Programs" tab, click "Add" and enter "xbindkeys". This makes sure it's run each time you log in, you should probably test it by logging out and back in now. If you aren't running GNOME, you will need to do it another way, e.g. in XFCE, go to Xfce Menu -> Settings -> Autostarted Applications.

In KDE (Thanks to msak007), you create a startup script:
```
kedit ~/.kde/Autostart/start-xbindkeys
```
Insert this into it:
```
#!/bin/sh
xbindkeys
```
Make it executable:
```
chmod +x ~/.kde/Autostart/start-xbindkeys
```[/INDENT]

**_Section 3: lomoco (Resolution, etc.) (Optional)_**

[INDENT]This section is for making sure your mouse is using the best resolution it can, making it more accurate which is pretty handy especially in games where that counts.

_1. Getting everything we need_

lomoco is in the repositories as of Ubuntu 6.10. Ok so lets install lomoco:

```
sudo apt-get install lomoco
```

_2. Working lomoco_

I use the command "lomoco -8" which you can run now:

```
sudo lomoco -8
```

_3. Load on boot_

We need to add this to a start up script so it's done automatically when the machine boots up, to do this I make a file in /etc/init.d/local where I keep local settings, so lets make that now:

```
sudo gedit /etc/init.d/local
```

Now paste the lomoco command, mine like the example above is:

```
echo "Setting up Logitech mouse..."
lomoco -8
```

I have the echo line so I can check if it works in the boot messages, it's nice but you don't need it.

To make it executable run the following command:

```
sudo chmod 755 /etc/init.d/local
```

Now run the following command to make the "local" script run when the system boots:

```
sudo update-rc.d local defaults
```

Now lomoco loads automatically on boot! :)[/INDENT]

**_Conclusion_**

I think that's everything, phew. I hope it works for you and I haven't made too many mistakes. Please add any corrections and success stories for logitech mice other then the mx500 so we can find out what works.

Thanks to endy's howto, [http://floam.sh.nu/guides/mx1000](http://floam.sh.nu/guides/mx1000), and the many people who responded to my first howto, especially pietruszka.
Please tell me if you have any problems or if I made any errors.

**Edit**: Added the need to restart the whole computer for the udev rule to take effect. I think this is where many people had trouble with my last guide.
**Edit**: Simplified the click downloading and all.
**Edit**: Added a few notes for those who complain.
**Edit**: Fixed the click path for xbindkeys.
**Edit**: Added the requirement for the evdev package since not everybody has it installed by default.
**Edit**: Replaced LMCtl with lomoco in the instructions
**Edit**: Fixed a most embarrasing error in the note at the top. :biggrin:
**Edit**: Added the KDE way to add xbindkeys to the session.
**Edit**: Did a major upgrade for Edgy and Feisty.
**Edit**: Replaced the restart part with a command to restart evdev and Xorg.

---

### Post by detyabozhye on 2006-07-21
K, this is the new guide, use the [old one]("http://ubuntuforums.org/showthread.php?t=188302") ONLY if this one fails any way you try.

---

### Post by NobodySpecial on 2006-07-21
detyabozhye - You rock!  This works perfectly with my Logitech G7.  8-)

Just have to use "Logitech USB Receiver".  Some extra config is needed for buttons, but no big deal.

---

### Post by detyabozhye on 2006-07-21
Thanks. ^_^ Prayed a lot while trying to get it to work (I do that all the time) so I can't take the credit. ^^;

---

### Post by Alexander Heß on 2006-07-23
Thanks for the howto. It works quite good on my Notebook.

I just have some problems:

- My MX518 doesn't want to do any cruising, the buttons [+] and [-] don't create any reaction in xev. I've read your comment in the other howto that these buttons work differently on a MX518, but I know for sure that you can set them up to do cruise control in Windows. The standard driver from Logitech allows these buttons to be setup as cruise control. So it should (somehow) be possible on Linux, too.

- My V500 now has all buttons working too, but instead of sending mouse6 on scrolling left and mouse7 on scrolling right, they are switched. Left gives 7 and right gives 6. I tried remapping with xmodmap, but it doesn't work. I guess I'll have to go the xbindkey-route for them to work.

The LMCtl-version you linked in this howto doesn't have support for MX510, MX518, and newer ones. There seems to be a patch for lmctl somewhere, but I couldn't find it with google. But there is a kind of replacement, called [lomoco](http://lomoco.linux-gamers.net/) with support for the newer mice.

---

### Post by kpurcell on 2006-07-23
> **detyabozhye said:**
> 

Then add this to you .xbindkeysrc:

```
"~/click/click 4"
  m:0x0 + b:9
"~/click/click 5"
  m:0x0 + b:10
```

how do I do this?

---

### Post by kpurcell on 2006-07-23
And also how do I make the wheel button a double click button?

---

### Post by skeeterflea on 2006-07-23
> **kpurcell said:**
> 
Quote:
Originally Posted by detyabozhye View Post

Then add this to you .xbindkeysrc:

Code:

"~/click/click 4" m:0x0 + b:9 "~/click/click 5" m:0x0 + b:10


how do I do this?

Yes, everything else was an excellent walk through, until I got here.

Any help is appreciated.

---

### Post by Alexander Heß on 2006-07-24
> 
how do I do this?


```

gedit ~/.xbindkeysrc

```

---

### Post by detyabozhye on 2006-07-24
> **Alexander Heß said:**
> - My MX518 doesn't want to do any cruising, the buttons [+] and [-] don't create any reaction in xev. I've read your comment in the other howto that these buttons work differently on a MX518, but I know for sure that you can set them up to do cruise control in Windows. The standard driver from Logitech allows these buttons to be setup as cruise control. So it should (somehow) be possible on Linux, too.

well, to make it do cruise control, I believe you would do the equiv of $ lmctl --sms using lomoco or something.

> **Alexander Heß said:**
> - My V500 now has all buttons working too, but instead of sending mouse6 on scrolling left and mouse7 on scrolling right, they are switched. Left gives 7 and right gives 6. I tried remapping with xmodmap, but it doesn't work. I guess I'll have to go the xbindkey-route for them to work.

hmm, what did xmodmap say? It should be possible with xmodmap.

> **Alexander Heß said:**
> The LMCtl-version you linked in this howto doesn't have support for MX510, MX518, and newer ones. There seems to be a patch for lmctl somewhere, but I couldn't find it with google. But there is a kind of replacement, called [lomoco](http://lomoco.linux-gamers.net/) with support for the newer mice.

Does it take all the same commands?

---

### Post by dantx24 on 2006-07-24
last time I enabled evdev I started getting "scheduling while atomic: xorg" infinite error loops once I installed xgl / compiz, but the buttons worked. any instances of that under the new guide? Or am i retarded for thinking that the two events were related in the first place?

excellent guides btw.

---

### Post by detyabozhye on 2006-07-24
Honestly, I don't know, since I don't really use Xgl or Compiz right now. It crashed on me too often and Compiz doesn't have all the features I would expect from a window manager yet.

---

### Post by dejitarob on 2006-07-24
For my purposes (MX500) all I had to do is edit /etc/X11/xorg.conf to contain the following under "Configured Mouse:"
```
Option "Protocol" "ExplorerPS/2"
Option "Buttons" "5"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"
```This actually works on my [Evoluent]("http://www.evoluent.com/vm3.html") mouse too :]

---

### Post by detyabozhye on 2006-07-24
> **dejitarob said:**
> Wow, you are making it a lot harder than it is--at least for an MX500. All I had to do is edit /etc/X11/xorg.conf to contain the following:
```
Option "Buttons" "5"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"
```

That won't make absolutely ALL of the buttons work, it won't make back/forward work in Nautilus, Thunar, etc, and won't give you 800 CPI resolution. It's a good solution, but I don't settle for just good. I wanted ALL of my buttons working and I wanted to be able to use my mouse at 800 CPI.

---

### Post by gurgle on 2006-07-25
> **dejitarob said:**
> Wow, you are making it a lot harder than it is--at least for an MX500. All I had to do is edit /etc/X11/xorg.conf to contain the following:
```
Option "Buttons" "5"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"
```

thanks for that. the OP was too complicated.

I cant believe setting my mx1000 mouse buttons was so much more difficult then winxp

---

### Post by killerjay_47 on 2006-07-25
Ok, let's complicate things a little.

I'm working on a laptop, and when I'm plugged in at my desk I use a Logitech LX700 Wireless Keyboard/Mouse combo. Using the above guide as a reference, I was able to make the buttons work for forward and backward. But when I disconnect the mouse to roam, my X server doesn't like the cofiguration and won't load. Then I have to go back in and comment out all the stuff I added in order to make it load X.

Is it possible to make this configuration depend on whether it detects the hardware?

Also, on my mouse there's a top button a little ways behind the scroll wheel that I'd like to map to Ctrl-T for use in firefox opening a new tab. I determined that the button is button #10 using xev, but when I tried to add the line
```
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[T]""
  m:0x0 + b:10
```
to my .xbindkeysrc and run xbindkeys it loads it so that it simply types the character 'T' when I click, and then when I removed the line (and ran xbindkeys again), it didn't stop typing the character. Restarting seemed to fix that, but I can't get the Ctrl-T to work at all. Ideas? Of course, it's moot if I can't get the configuration to work when it's not there.

I must say that I've really appreciated the guide so far.

Thanks,
jay

---

### Post by hubacap on 2006-07-25
I have been ](*,) !!!!  

I have the MX1000 and have been trying different things for a week.

I created the 19-local.rules file
```

KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", NAME="input/event9"

``` 
I backed up and edited the Xorg.conf file.
```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "evdev"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/event9"
EndSection

``` 
Restarted... that's when the gun just about came out of the cabinet. LOL


My machine started in the text shell... grrrr. 

This came from the log file.

```
(EE) xf86OpenSerial: Cannot open device /dev/wacom
    No such file or directory.
Error opening /dev/wacom : No such file or directory

``` That repeated 5 times to make a total of 6.

What am I doing wrong?? I did copy and paste where I could as to reduce typo's. I would really like the full functionality of this great mouse and at the same time have X to run. I just want to much.:-k

---

### Post by ewerx on 2006-07-25
I have a G7 and I also could not start X after the restart. 

Output from /proc/bus/input/devices that relate to my mouse:
```
I: Bus=0003 Vendor=046d Product=c51a Version=4100
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.7-4.1.2/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse0 event3 ts0
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0003 Vendor=046d Product=c51a Version=4100
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.7-4.1.2/input1
S: Sysfs=/class/input/input4
H: Handlers=kbd event4
B: EV=f
B: KEY=c0002 400 0 0 1 f80 78000 6039fa d84157ad 8e0000 0 0 0
B: REL=40
B: ABS=1 0

```

I'm not sure why there are two listed here, could that be the problem?

My 19-local.rules:
```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", NAME="input/event9"

```

My xorg.conf is identical to the example.

My X.org log file from the failed restart (only the parts that seem significant, added highlighting on what i think might be the error):
```
(II) Initializing extension GLX
**error opening security policy file /etc/X11/xserver/SecurityPolicy**
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
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
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
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/wacom"
[b](EE) xf86OpenSerial: Cannot open device /dev/wacom
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
Error opening /dev/wacom : No such file or directory[/b]
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) 3rd Button detected: disabling emulate3Button

```

Looks like the same warnings hubacap is getting... not sure what that wacom stuff is, since I don't have a tablet or anything like that. The Logitech G7 mouse and a Microsoft Keyboard are the only input devices I have.

---

### Post by kpurcell on 2006-07-25
> **ewerx said:**
>  not sure what that wacom stuff is, since I don't have a tablet or anything like that. The Logitech G7 mouse and a Microsoft Keyboard are the only input devices I have.

I'm not sue either.  I have no wacom hooked up either but I have it in my xorg.conf file too.  If I delete it it stops working.

---

### Post by detyabozhye on 2006-07-25
> **killerjay_47 said:**
> I'm working on a laptop, and when I'm plugged in at my desk I use a Logitech LX700 Wireless Keyboard/Mouse combo. Using the above guide as a reference, I was able to make the buttons work for forward and backward. But when I disconnect the mouse to roam, my X server doesn't like the cofiguration and won't load. Then I have to go back in and comment out all the stuff I added in order to make it load X.

Is it possible to make this configuration depend on whether it detects the hardware?

I believe someone replaced Option "CorePointer" with Option "SendCoreEvents" "True" to make it work. I haveb't tried it though, so I don't know.

> **killerjay_47 said:**
> Also, on my mouse there's a top button a little ways behind the scroll wheel that I'd like to map to Ctrl-T for use in firefox opening a new tab. I determined that the button is button #10 using xev, but when I tried to add the line
```
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[T]""
  m:0x0 + b:10
```
to my .xbindkeysrc and run xbindkeys it loads it so that it simply types the character 'T' when I click, and then when I removed the line (and ran xbindkeys again), it didn't stop typing the character. Restarting seemed to fix that, but I can't get the Ctrl-T to work at all. Ideas? Of course, it's moot if I can't get the configuration to work when it's not there.

I must say that I've really appreciated the guide so far.

Thanks,
jay

Try this in your .xbindkeysrc:
```
"/usr/bin/xvkbd -xsendevent -text "\[Control]\[t]""
  m:0x0 + b:10
```

Remember to first kill xbindkeys before running it again:
```
killall xbindkeys
xbindkeys
```

D_o_ itashi mashi te (You're welcome)

---

### Post by detyabozhye on 2006-07-25
> **hubacap said:**
> I have been ](*,) !!!!  

I have the MX1000 and have been trying different things for a week.

I created the 19-local.rules file
```

KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", NAME="input/event9"

``` 
I backed up and edited the Xorg.conf file.
```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "evdev"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/event9"
EndSection

``` 
Restarted... that's when the gun just about came out of the cabinet. LOL


My machine started in the text shell... grrrr. 

This came from the log file.

```
(EE) xf86OpenSerial: Cannot open device /dev/wacom
    No such file or directory.
Error opening /dev/wacom : No such file or directory

``` That repeated 5 times to make a total of 6.

What am I doing wrong?? I did copy and paste where I could as to reduce typo's. I would really like the full functionality of this great mouse and at the same time have X to run. I just want to much.:-k

Hmm, everything looks correct. Are you running regualr Xorg or Xgl?
Edit: If you're using two devices on one receiver, the post under this one may be helpful.

---

### Post by detyabozhye on 2006-07-25
> **ewerx said:**
> I have a G7 and I also could not start X after the restart. 

Output from /proc/bus/input/devices that relate to my mouse:
```
I: Bus=0003 Vendor=046d Product=c51a Version=4100
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.7-4.1.2/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse0 event3 ts0
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0003 Vendor=046d Product=c51a Version=4100
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.7-4.1.2/input1
S: Sysfs=/class/input/input4
H: Handlers=kbd event4
B: EV=f
B: KEY=c0002 400 0 0 1 f80 78000 6039fa d84157ad 8e0000 0 0 0
B: REL=40
B: ABS=1 0

```

I'm not sure why there are two listed here, could that be the problem?

My 19-local.rules:
```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", NAME="input/event9"

```

My xorg.conf is identical to the example.

My X.org log file from the failed restart (only the parts that seem significant, added highlighting on what i think might be the error):
```
(II) Initializing extension GLX
**error opening security policy file /etc/X11/xserver/SecurityPolicy**
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
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
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
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/wacom"
[b](EE) xf86OpenSerial: Cannot open device /dev/wacom
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
Error opening /dev/wacom : No such file or directory[/b]
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) 3rd Button detected: disabling emulate3Button

```

Looks like the same warnings hubacap is getting... not sure what that wacom stuff is, since I don't have a tablet or anything like that. The Logitech G7 mouse and a Microsoft Keyboard are the only input devices I have.

You have both connecting through one reciever, correct? In that case, you'ld have to set up Xorg a bit differently, and you might have to drop the udev rule. I think some people have gotten it to work, but I haven't, so I can't really say how to have both working through one receiver. It might help to look through some comments in the old thread.

These may be helpful:
[http://ubuntuforums.org/showpost.php?p=1126893&postcount=45](http://ubuntuforums.org/showpost.php?p=1126893&postcount=45)
[http://ubuntuforums.org/showpost.php?p=1155987&postcount=62](http://ubuntuforums.org/showpost.php?p=1155987&postcount=62)

---

### Post by killerjay_47 on 2006-07-25
I was able to get mine working properly using this guide, and mine is a KB/Mouse combo on one receiver. Specifically, I have the Logitech LX700.

My details from the input devices:
```
I: Bus=0003 Vendor=046d Product=c512 Version=3007
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.1-1.2/input0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c512 Version=3007
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.1-1.2/input1
S: Sysfs=/class/input/input4
H: Handlers=kbd mouse1 event4 ts1
B: EV=7
B: KEY=7fffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff 0 0 1878 d800d100 1e0000 0 0 0
B: REL=143
```

My 19-local.rules:
```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", NAME="input/event9"
```

My xorg.conf before trying what detyabozhye has suggested. It works whenever the mouse is plugged in, but not when the mouse is dosconnected.
```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "evdev"
    Option        "CorePointer"
    Option        "Device"          "/dev/input/event9"
    Option        "Buttons"        "10"
    Option        "ZAxisMapping"        "4 5"
EndSection
```

My .xbindkeys is the same as his, with a couple more options added.

I hope some of this might be of help. Best of luck; I'm off to try this when the mouse is disconnected. BTW, I got the Ctrl-T working. Thanks.

Jay


EDIT: what you suggested worked, thanks. Now, how do I get the xbindkeys daemon to run automatically when I boot?

---

### Post by detyabozhye on 2006-07-25
> **killerjay_47 said:**
> what you suggested worked, thanks. Now, how do I get the xbindkeys daemon to run automatically when I boot?

If you're running Gnome, go to "System > Preferences > Sessions" click on the "Startup Programs" tab, click "Add" and enter "xbindkeys".

In Xfce go to Xfce Menu -> Settings -> Autostarted Applications and click Add.

As for KDE, I'm not sure what the correct way is.

---

### Post by kpurcell on 2006-07-25
I tried the simple approach, ignoring the udev stuff and just added the lines at the end of my mouse section in xorg.conf.  It is as follows:

> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option 		"Buttons" 		"5"
	Option 		"ZAxisMapping" 		"4 5"
	Option 		"ButtonMapping" 	"1 2 3 6 7"
EndSection

So now my MX1000 cruise up button instead goes back.  And my the thumb button closest to me does too.  What I'd really like is to have the cruis up to cruis up and the cruise down to cruise down.  I'd also like the side buttons to go band and forth like they are supposed to and the wheel button I'd like to double click when I push it.  Any way to do that?  Or at least some of it without all this crazy, complicated stuff.  could someone post what the button mapping numbers mean and then I could just configure it the way I want.

---

### Post by detyabozhye on 2006-07-25
> **kpurcell said:**
> I tried the simple approach, ignoring the udev stuff and just added the lines at the end of my mouse section in xorg.conf.  It is as follows:

```
Quote:Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Buttons" "5"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"
EndSection
```

So now my MX1000 cruise up button instead goes back.  And my the thumb button closest to me does too.  What I'd really like is to have the cruis up to cruis up and the cruise down to cruise down.  I'd also like the side buttons to go band and forth like they are supposed to and the wheel button I'd like to double click when I push it.  Any way to do that?  Or at least some of it without all this crazy, complicated stuff.  could someone post what the button mapping numbers mean and then I could just configure it the way I want.

Note the Protocol, it's "ExplorerPS/2", it's meant for MS IntelliMouse Explorer. It will not work with all the Logitech buttons correctly no matter what you set the "ButtonMapping" to, I tried it. I don't mind anyone using that method, but you'll have to live with some buttons functioning incorrectly.

BTW, you will still need to set up xbindkeys, LMCtl, etc IF you want it to do 800+ CPI, Back/Forward in Nautilus or whatever. The "simple" method is only a replacement for the udev and evdev part, not for the rest of this guide. If I wrote this guide using the "simple method", it would still be two thirds the length.

---

### Post by BatteryCell on 2006-07-25
Lol well this ended for me early, when I first went to change xorg.conf (after the udev thing), the X server kinda booted then didnt.  Im using nvidia drivers and indeed the little nvidia picture showed up as it was supposed to. However after that it went back to the loading screen (usually it then proceeds to login).  Any reason why this happens?

---

### Post by detyabozhye on 2006-07-25
Don't know, I had that a lot when testing the current evdev. Can you tell me a bit about your mouse, setup, and give me the output of "cat /proc/bus/input/devices"? The current evdev is just a bit too picky. My [_old guide_](http://ubuntuforums.org/showthread.php?t=188302) is a bit more relliable, but a bit hacky as well and longer in length.

---

### Post by zergberg on 2006-07-25
I have the Wacom thing too. I'm not sure why it's there, but you can safely comment out the device references if you also comment out "stylus", "cursor", and "eraser" in the "Server Layout" section of xorg.conf, near the bottom.

It doesn't help anything, but it at least supresses those annoying error messages that scroll off the relevant errors when X fails to start.

---

### Post by BatteryCell on 2006-07-25
Heres the output of cat /proc/bus/input/devices
```
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=402000000 3802078f840d001 f2ffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2
B: EV=40001
B: SND=6

I: Bus=0000 Vendor=001f Product=001f Version=0000
N: Name="Mouseemu virtual keyboard"
P: Phys=
S: Sysfs=/class/input/input3
H: Handlers=kbd event3
B: EV=100003
B: KEY=1ffffffffffff ffffffffffffffff ffffffffffffffff ffffffffffffffff

I: Bus=0000 Vendor=001f Product=001e Version=0000
N: Name="Mouseemu virtual mouse"
P: Phys=
S: Sysfs=/class/input/input4
H: Handlers=mouse1 event4 ts1
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=103

I: Bus=0005 Vendor=045e Product=007b Version=0039
N: Name="Microsoft Bluetooth keyboard"
P: Phys=00:50:F2:E1:B6:20
S: Sysfs=/class/input/input5
H: Handlers=kbd event5
B: EV=12000b
B: KEY=3 ffff000000000007 ff8018780803ffff fffeffdff3cfffff fffffffffffffffe
B: ABS=1f0000000000
B: LED=407

I: Bus=0003 Vendor=046d Product=c01e Version=2200
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:02.0-8/input0
S: Sysfs=/class/input/input14
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=ff0000 0 0 0 0
B: REL=103
```

Note that this is after I tried to do the guide.

As to the setup:
the comps a a64 runnin kubuntu dapper drake (Linux kubuntu 2.6.15-26-amd64-generic)
mouse is a mx518

graphics an evga 7900 gt
hd is a seagate 160 gig
cpu is a 3800
mobo is an asus a8n sli dlx
1 gig ram

Thats pretty much it, oh and thanks for the help :-)

---

### Post by hubacap on 2006-07-26
> **detyabozhye said:**
> Hmm, everything looks correct. Are you running regualr Xorg or Xgl?
Edit: If you're using two devices on one receiver, the post under this one may be helpful.

I am using Ubuntu right out of the box so I am assuming that it is Xorg, and I have only one device on this reciever, KB is ps2.

After creating the evdev rule and especially after a reboot shouldn't it show up on a ```
ls /dev/input/
``` ? It wasn't, so I remembered another tutorial on the subject and added ACTION=="add" to my rules file to read:
```
ACTION=="add", KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", NAME="input/event9"
``` It shows up now but X still wont start after double checking for typo's and syntax errors ( limited knowledge on syntax but I tried to duplicate my interpretation of your tutorial).

](*,)](*,)](*,)](*,)](*,)  << I love this guy, he reminds me of me, never give up, he WILL break through that wall.....     one day.

EDIT: Ok, didn't realise that I needed to look at the old log file so here is the error output pertaining to the mouse.
```
(EE) PreInit returned NULL for "Configured Mouse"
``` 
The /dev/wacom error is still present in both log files so I assume that it has nothing to do with the mouse problem.

---

### Post by Eugene Seppel on 2006-07-26
Thank you for HOWTO!

And how can i overlock MX510 mouse, like in Windows?
USB max speed for mouse is 125Hz, but one program for Windows XP can overlock it up to 1000Hz (by changing driver).
I want 250Hz..

---

### Post by ewerx on 2006-07-26
> **detyabozhye said:**
> You have both connecting through one reciever, correct? In that case, you'ld have to set up Xorg a bit differently, and you might have to drop the udev rule. I think some people have gotten it to work, but I haven't, so I can't really say how to have both working through one receiver. It might help to look through some comments in the old thread.

These may be helpful:
[http://ubuntuforums.org/showpost.php?p=1126893&postcount=45](http://ubuntuforums.org/showpost.php?p=1126893&postcount=45)
[http://ubuntuforums.org/showpost.php?p=1155987&postcount=62](http://ubuntuforums.org/showpost.php?p=1155987&postcount=62)

Actually no. My keyboard is a regular Microsoft wired USB keyboard. My mouse is the Logitech G7 cordless. I have the G7 receiver connected to my monitor's  USB hub, and the keyboard goes straight to the back of the PC.
I don't really get why I would have 2 devices under the Logitech receiver -- I only have 1 cordless device, the mouse. But I'll check out those links when I have time and see if they help...

---

### Post by BatteryCell on 2006-07-26
Lol I feel stupid, the evdev driver wasnt installed... Ok I gotta go do the rest of the tutorial :D

---

### Post by BatteryCell on 2006-07-26
Ok everything works (the on the fly 400 800 and 1600 are good enough for me :) ) 
However, I was just wondering how you would bind the change application button (in windows when u hit it it gives you a little box with all the windows open and you can pick which one, its the one on the mx518 right below the lower reso.) to ALT-TAB (which does the same thing).

Im guessing it would be something like:
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Tab]""
  m:0x0 + b:8

in /root/.xbindkeysrc
Though I dont know which button the change app. button is...

Another qustion, the mouse pointer sometimes freezes on the screen and the only thing that will fix it is if I unplug and replug the mouse.  Just wondering what is causing this because I have had to move the usb to a front port so that it isnt so hard to unplug and relug and its real ugly...  
The only thing that I changed before this started happening is that I overclocked my cpu just a little, though I dont see how thats causing it and when I stop overclocking it still happened. (This comps a dual boot, and in windows the same thing happens cept a simple tap of the alt key fixes the mouse, which is still annoying).

---

### Post by detyabozhye on 2006-07-26
> **Eugene Seppel said:**
> Thank you for HOWTO!

And how can i overlock MX510 mouse, like in Windows?
USB max speed for mouse is 125Hz, but one program for Windows XP can overlock it up to 1000Hz (by changing driver).
I want 250Hz..

This may be helpful: [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+USBPolling&back=HOWTO+INDEX+Hardware](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+USBPolling&back=HOWTO+INDEX+Hardware)

---

### Post by detyabozhye on 2006-07-26
> **hubacap said:**
> After creating the evdev rule and especially after a reboot shouldn't it show up on a ```
ls /dev/input/
``` ? It wasn't, so I remembered another tutorial on the subject and added ACTION=="add" to my rules file to read:
```
ACTION=="add", KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", NAME="input/event9"
``` It shows up now but X still wont start after double checking for typo's and syntax errors ( limited knowledge on syntax but I tried to duplicate my interpretation of your tutorial).

Hmm, the udev rule should work without ACTION="add", what was your ```
cat /proc/bus/input/devices
``` again?

> **hubacap said:**
> ](*,)](*,)](*,)](*,)](*,)  << I love this guy, he reminds me of me, never give up, he WILL break through that wall.....     one day.

EDIT: Ok, didn't realise that I needed to look at the old log file so here is the error output pertaining to the mouse.
```
(EE) PreInit returned NULL for "Configured Mouse"
``` 
The /dev/wacom error is still present in both log files so I assume that it has nothing to do with the mouse problem.

Yeah, the wacom has nothing to do with it. Though on another note, it's weird that Ubuntu sets up Xorg as though it has a wacom device even if it doesn't in the first place. :-k

---

### Post by detyabozhye on 2006-07-26
> **ewerx said:**
> Actually no. My keyboard is a regular Microsoft wired USB keyboard. My mouse is the Logitech G7 cordless. I have the G7 receiver connected to my monitor's  USB hub, and the keyboard goes straight to the back of the PC.
I don't really get why I would have 2 devices under the Logitech receiver -- I only have 1 cordless device, the mouse. But I'll check out those links when I have time and see if they help...

Yeah, but your reciever seems to be recognized as both a keyboard and mouse. So somehow, you'll need to target only the mouse part.

---

### Post by detyabozhye on 2006-07-26
> **BatteryCell said:**
> Ok everything works (the on the fly 400 800 and 1600 are good enough for me :) ) 
However, I was just wondering how you would bind the change application button (in windows when u hit it it gives you a little box with all the windows open and you can pick which one, its the one on the mx518 right below the lower reso.) to ALT-TAB (which does the same thing).

Im guessing it would be something like:
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Tab]""
  m:0x0 + b:8

in /root/.xbindkeysrc
Though I dont know which button the change app. button is...

Use xev to find out which button it is. As for using it for ALT+TAB, at the moment, that's not really possible. When you do ALT+TAB, you hold ALT and press TAB a few times till you get to the app you want to get to. xbindkeys will only do a press and release of ALT+TAB. You would need to build an app yourself to do that. I started planning one, but never really got to it.

> **BatteryCell said:**
> Another qustion, the mouse pointer sometimes freezes on the screen and the only thing that will fix it is if I unplug and replug the mouse.  Just wondering what is causing this because I have had to move the usb to a front port so that it isnt so hard to unplug and relug and its real ugly...  
The only thing that I changed before this started happening is that I overclocked my cpu just a little, though I dont see how thats causing it and when I stop overclocking it still happened. (This comps a dual boot, and in windows the same thing happens cept a simple tap of the alt key fixes the mouse, which is still annoying).

hmm, looks like a hardware issue to me. I don't know.

---

### Post by BatteryCell on 2006-07-26
Um just pressing alt-F5 works too...and its button 8 so:
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[F5]""
m:0x0 + b:8
But that doesnt seem to work on mine...
And other people have said its hardware as well but i dont see how it could be seeing as I just bought a new mouse (takin the advice) and its still happening, and the vid cards pretty new 2 so...Maybe its the drivers...Ill check on that.

edit:
Wait it does work but only if all windows are minimized.

---

### Post by MilesTEG1 on 2006-07-26
Hello, does it function with the Logitech G5 ?
I have those lines with the cat /proc/bus/input/devices :
```
I: Bus=0003 Vendor=046d Product=c041 Version=4600
N: Name="Logitech USB Gaming Mouse"
P: Phys=usb-0000:00:02.0-1/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=ffff0000 0 0 0 0
B: REL=143

```

---

### Post by detyabozhye on 2006-07-26
It should. You'll just need to set up xbindkeys differently.

---

### Post by BatteryCell on 2006-07-26
Woa, now my mouse and keyboard are freezing up...any idea what could be happening?? It seems that whenever I try to apt-get or use adept they freeze and even when Im not they sometimes do. Any ideas? Maybe change my display driver from nvidia to nv?

---

### Post by detyabozhye on 2006-07-26
hmm, I never ran into that problem. You could try fresh installing on another hard drive if you have one and add modifications to your system one at a time to see which one is making your comp run weird and then remove it or replace it on your main install.

---

### Post by hubacap on 2006-07-26
> **detyabozhye said:**
> Hmm, the udev rule should work without ACTION="add", what was your ```
cat /proc/bus/input/devices
``` again?


Freshly run ```
cat /proc/bus/input/devices
``` =
```

I: Bus=0003 Vendor=046d Product=c50e Version=2500
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1f.2-1/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event2 ts0
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

``` 
I will try to be on earlier tomorrow so maybe we could chat about it if needed, I'll try to get gaim working tonight.

---

### Post by detyabozhye on 2006-07-26
And you have the udev rule set up right now and it still gives you event2, right? If so, the problem might be in the udev rule.

---

### Post by MilesTEG1 on 2006-07-27
> **detyabozhye said:**
> It should. You'll just need to set up xbindkeys differently.
How do I set up xbindkeys ?

---

### Post by detyabozhye on 2006-07-27
Well, for example, the G5 usually has button 8 do back. You would also need to change a setting for firefox to do horizontal scrolling, etc. But first you need to get the mouse working then find out the button numbers in xev before setting up xbindkeys.

---

### Post by crispy_420 on 2006-07-27
OK my back/foward work in firefox but not nautilus. Did I do something wrong? When I use the standard keyboard shortcuts (ALT+left arrow), it works fine.

Also when I try to change the resolution by using:

> sudo lmctl -8

I get this message:

> 001.002: 046d:c01d Unknown or Unsupported Logitech device
001.003: 046d:c30a Unknown or Unsupported Logitech device


I have a MX510 but other than these minor issues, I love my new ability in firefox.

---

### Post by detyabozhye on 2006-07-27
Most likely something is wrong in .xbindkeysrc. Can you post it here? and the xev output for your side buttons.

As for LMCtl, I might have to replace that with lomoco in the tut, I have to check it out first.

---

### Post by matsur on 2006-07-27
> **detyabozhye said:**
> ```
cd ~/
wget http://bg.rifetech.com/click.tgz
tar xvfz click.tgz
mv click .click

```

then compile it:

```
cd ~/.click
make
```

Then add this to you .xbindkeysrc (gedit ~/.xbindkeysrc):

```
"~/click/click 4"
  m:0x0 + b:9
"~/click/click 5"
  m:0x0 + b:10
```

Maybe I'm being dense, but shouldn't the line have ~/.click/click instead of ~/click/click as per the "mv click .click" above?

Also, I added```
"/usr/bin/xvkbd -xsendevent -text "\[Super_L]\[c]""
  m:0x0 + b:8
```to .xbindkeysrc to have the app switcher button pause amaroK. However, it just prints a "c". What am I doing wrong?

Thanks

---

### Post by BatteryCell on 2006-07-27
Um when I open up xvkbd I dont see any windows key (super l) so Im guessing thats why that doesnt work...

---

### Post by detyabozhye on 2006-07-27
correct about the click, sorry bout that. I'm going to try the super thing.

Edit: Can't really find a solution to the super key. -_-

---

### Post by matsur on 2006-07-27
I sorted out the Super situation by binding the amaroK dcop commands to mouse clicks instead of trying to get xvkbd to send the shortcut keystrokes. If anyone is curious, here is how I have set it up (m:0x40 refers to the Win key:```
"/usr/bin/dcop amarok player playPause"
  m:0x0 + b:8
"/usr/bin/dcop amarok player prev"
  m:0x40 + b:6
"/usr/bin/dcop amarok player next"
  m:0x40 + b:7
"/usr/bin/dcop amarok player seekRelative -5"
  m:0x40 + b:4
"/usr/bin/dcop amarok player seekRelative 5"
  m:0x40 + b:5
```I've also extended cruise control a bit by having Shift + cruise control button execute page up or down:```
"~/.click/click 4"
  m:0x0 + b:9
"~/.click/click 5"
  m:0x0 + b:10
"/usr/bin/xvkbd -xsendevent -text "\[Prior]""
  m:0x1 + b:9
"/usr/bin/xvkbd -xsendevent -text "\[Next]""
  m:0x1 + b:10
```Thanks for the guide, it was indispensable in setting up my new mouse. One little thing you might consider changing... I didn't have the xserver-xorg-input-evdev package installed and it seems niether did a few others. Adding mention of it to the first post would eliminate some pain and suffering :-)

EDIT: I also got shift+Scroll wheel to increment system volume. DL [this](http://hellewell.homeip.net/phillip/linux/download/programs/vol.c) tiny C file, cd to the download dir and "make vol". Move the executable "vol" somewhere appropriate. Then throw this in your .xbindkeysrc:```
"/usr/local/bin/vol +5"
  m:0x1 + b:4
"/usr/local/bin/vol -5"
  m:0x1 + b:5
```

---

### Post by crispy_420 on 2006-07-27
Here is my .xbindkeysrc

> "/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7

It was just a copy and paste job. I did nothing to change it.

Here is my xev output for my back key:

> LeaveNotify event, serial 29, synthetic NO, window 0x3400001,
    root 0x76, subw 0x0, time 3003977396, (56,175), root:(60,234),
    mode NotifyGrab, detail NotifyAncestor, same_screen YES,
    focus NO, state 16
^[[3D
EnterNotify event, serial 29, synthetic NO, window 0x3400001,
    root 0x76, subw 0x0, time 3003977548, (56,175), root:(60,234),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
    focus NO, state 16

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  118 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0


And foward:

> LeaveNotify event, serial 29, synthetic NO, window 0x3400001,
    root 0x76, subw 0x0, time 3004013103, (134,177), root:(138,236),
    mode NotifyGrab, detail NotifyAncestor, same_screen YES,
    focus NO, state 16
^[[3C
EnterNotify event, serial 29, synthetic NO, window 0x3400001,
    root 0x76, subw 0x0, time 3004013310, (134,177), root:(138,236),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
    focus NO, state 16

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  118 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0


This what you asked for right?

---

### Post by BatteryCell on 2006-07-27
> **matsur said:**
> I sorted out the Super situation by binding the amaroK dcop commands to mouse clicks instead of trying to get xvkbd to send the shortcut keystrokes. If anyone is curious, here is how I have set it up (m:0x40 refers to the Win key:```
"/usr/bin/dcop amarok player playPause"
  m:0x0 + b:8
"/usr/bin/dcop amarok player prev"
  m:0x40 + b:6
"/usr/bin/dcop amarok player next"
  m:0x40 + b:7
"/usr/bin/dcop amarok player seekRelative -5"
  m:0x40 + b:4
"/usr/bin/dcop amarok player seekRelative 5"
  m:0x40 + b:5
```I've also extended cruise control a bit by having Shift + cruise control button execute page up or down:```
"~/.click/click 4"
  m:0x0 + b:9
"~/.click/click 5"
  m:0x0 + b:10
"/usr/bin/xvkbd -xsendevent -text "\[Prior]""
  m:0x1 + b:9
"/usr/bin/xvkbd -xsendevent -text "\[Next]""
  m:0x1 + b:10
```Thanks for the guide, it was indispensable in setting up my new mouse. One little thing you might consider changing... I didn't have the xserver-xorg-input-evdev package installed and it seems niether did a few others. Adding mention of it to the first post would eliminate some pain and suffering :-)

EDIT: I also got shift+Scroll wheel to increment system volume. DL [this](http://hellewell.homeip.net/phillip/linux/download/programs/vol.c) tiny C file, cd to the download dir and "make vol". Move the executable "vol" somewhere appropriate. Then throw this in your .xbindkeysrc:```
"/usr/local/bin/vol +5"
  m:0x1 + b:4
"/usr/local/bin/vol -5"
  m:0x1 + b:5
```

Will this override the binds in firefox?

---

### Post by rmjb on 2006-07-27
Well this worked for me, thanks!

Three things though:
1. For some reason my MX500 came up as "B16_b_02 USB-PS/2 Optical Mouse" in /proc/bus/input/devices
2. My cruise control buttons were working before so I didn't have to do the part with click
3. I just reused the eventX that was listed in /proc/bus/input/devices so I wouldn't have to reboot. I hope it sticks.

Again, thanks for a great HOWTO.

- rmjb

---

### Post by matsur on 2006-07-27
> **BatteryCell said:**
> Will this override the binds in firefox?
The volume part will, but I never use Shift+scroll to go through history anyway. You could of course tie any modifier to it, the hard part was finding the C app to do it. Before I found it I wrote a script around amixer which didnt work very well.

---

### Post by Clay85 on 2006-07-28
Thank you so much! I've been looking for this since MAY!

Worked perfectly the second time I tried it. First error was completely my fault. But it leads me to a question/problem.
before I changed anything:
```

enzo@reboot:~$ ls /dev/input/
event0 event1 event2 mice mouse0 ts0

```
Here was my error:
I thought, I'll use event3 since it's next in line. Thing is, I didn't change your code (my fault for not reading thouroughly) where you change the xorg to something like Option "device" "/dev/input/event9". So I told it event3, but it was trying event9 and my X server crashed. Thank you for underlining the word WARNING. Really saved me. :)

Here is my problem:
```

enzo@reboot:~$ ls /dev/input/
event2  event9  mice  mouse0  ts0
enzo@reboot:~$

```

Where did event0 and 1 go and what did it do? Am I in trouble?

Edit: I just noticed the volume dial on my keyboard doesn't work anymore. I have the Logitech Wireless MX duo (I believe it's the mx700 mouse, not sure about the keyboard).

---

### Post by Paradoxdruid on 2006-07-28
Thank you for this guide, I followed section 1 and it worked great for my Logitech MediaPlay mouse, and with a LOT less hassle and pain then using this project: [http://daemon.prozone.ws/~david/projects/lmpcm_usb/](http://daemon.prozone.ws/~david/projects/lmpcm_usb/).

I don't want or need cruise control, but I would like my Tilt wheel to work.  I looked at [http://blog.blackdown.de/2005/03/01/tilt-wheel-mouse/](http://blog.blackdown.de/2005/03/01/tilt-wheel-mouse/)
 , but adding in a ZAxisMap line makes X crash, so no go there.  Any ideas on enabling the tilt wheel?  Additionally, when I use windows, clicking the middle wheel in Firefox pops up a little "scroll up/down" icon and mouse movement then scrolls the page.  Is this possible?

XBindKeys is also working...  so far I have this:
```
#Volume High
"dcop kmix Mixer0 setVolume 1 70"
    m:0x0 + b:13
    VolUp 

#Volume Low
"dcop kmix Mixer0 setVolume 1 20"
    m:0x0 + b:14
    VolDown 

#Toggle Pause Video
"dcop kaffeine KaffeineIface pause"
    m:0x0 + b:17
    Pause 
```

This is actually also an issue--  the "Master" volume in KMix does nothing, my real volume is controlled by the PCM volume.  But I couldn't find a dcop command to allow me to increase the volume of the PCM device (rather than set an absolute).  dcop kmix Mixer0 increaseVolume only increases the "Master" volume, and no additional parameters I've found change that.

The keys reported from xev are as follows:  Left is b1, Middle b2, Right b3, scrollup b4, scrolldown b5, tilt left b11, tilt right b12, Media key b10, side forward b9, side back b8, Volume up b13, Volume down b14, Mediaforward b15, Mediaback b16, Play b17.

Thank you all for any help...  I consider myself fairly linux literate, but getting my media mouse working has been...  harrowing.

---

### Post by detyabozhye on 2006-07-28
> **crispy_420 said:**
> Here is my .xbindkeysrc



It was just a copy and paste job. I did nothing to change it.

Here is my xev output for my back key:



And foward:




This what you asked for right?

Yes, now the Left and Right are capitalized, right?
And can you also give me the xev output for those buttons with xnidkeys turned off?

$ killall xbindkeys
$ xev

---

### Post by detyabozhye on 2006-07-28
> **Clay85 said:**
> Thank you so much! I've been looking for this since MAY!

Worked perfectly the second time I tried it. First error was completely my fault. But it leads me to a question/problem.
before I changed anything:
```

enzo@reboot:~$ ls /dev/input/
event0 event1 event2 mice mouse0 ts0

```
Here was my error:
I thought, I'll use event3 since it's next in line. Thing is, I didn't change your code (my fault for not reading thouroughly) where you change the xorg to something like Option "device" "/dev/input/event9". So I told it event3, but it was trying event9 and my X server crashed. Thank you for underlining the word WARNING. Really saved me. :)

Here is my problem:
```

enzo@reboot:~$ ls /dev/input/
event2  event9  mice  mouse0  ts0
enzo@reboot:~$

```

Where did event0 and 1 go and what did it do? Am I in trouble?

Edit: I just noticed the volume dial on my keyboard doesn't work anymore. I have the Logitech Wireless MX duo (I believe it's the mx700 mouse, not sure about the keyboard).

Hmm, I think you'll need to somehow seperate the mouse and keyboard since they probably use the same receiver. I still haven't quite figured it out though. >_<

---

### Post by detyabozhye on 2006-07-28
> **Paradoxdruid said:**
> when I use windows, clicking the middle wheel in Firefox pops up a little "scroll up/down" icon and mouse movement then scrolls the page.  Is this possible?

AFAIK, this is a Windows thing, it's just the way Windows works.

> **Paradoxdruid said:**
> XBindKeys is also working...  so far I have this:
```
#Volume High
"dcop kmix Mixer0 setVolume 1 70"
    m:0x0 + b:13
    VolUp 

#Volume Low
"dcop kmix Mixer0 setVolume 1 20"
    m:0x0 + b:14
    VolDown 

#Toggle Pause Video
"dcop kaffeine KaffeineIface pause"
    m:0x0 + b:17
    Pause 
```

This is actually also an issue--  the "Master" volume in KMix does nothing, my real volume is controlled by the PCM volume.  But I couldn't find a dcop command to allow me to increase the volume of the PCM device (rather than set an absolute).  dcop kmix Mixer0 increaseVolume only increases the "Master" volume, and no additional parameters I've found change that.

That, I don't know.

> **Paradoxdruid said:**
> I don't want or need cruise control, but I would like my Tilt wheel to work.  I looked at [http://blog.blackdown.de/2005/03/01/tilt-wheel-mouse/](http://blog.blackdown.de/2005/03/01/tilt-wheel-mouse/)
 , but adding in a ZAxisMap line makes X crash, so no go there.  Any ideas on enabling the tilt wheel?

...

The keys reported from xev are as follows:  Left is b1, Middle b2, Right b3, scrollup b4, scrolldown b5, tilt left b11, tilt right b12, Media key b10, side forward b9, side back b8, Volume up b13, Volume down b14, Mediaforward b15, Mediaback b16, Play b17.

Thank you all for any help...  I consider myself fairly linux literate, but getting my media mouse working has been...  harrowing.

Install xmodmap. Then do:

```
gedit ~/.Xmodmap
```

Paste this into there and save it:

```
pointer = 1 2 3 4 5 8 9 6 7 10 11 12 13 14 15
```

Then run xmodmap ~/.Xmodmap and if it complains about too little buttons add 16 17 etc untill it's satisfied. If it says there's too many, try deleting some starting at the end untill it works. Then give me the xev output.

---

### Post by rmjb on 2006-07-28
> **detyabozhye said:**
> Hmm, I think you'll need to somehow seperate the mouse and keyboard since they probably use the same receiver. I still haven't quite figured it out though. >_<

I think we will because is seems lmctl speeds up the sampling rate of the mouse. And since the mouse and keyboard probably use the same driver I'm having an interesting side effect... UT2004 is playing *[COLOR="Red"]blazingly[/COLOR]* fast. I don't just mean the frames are fast, but the entire game is screaming. Bots move faster, I move faster guns fire faster.

I'm thinking it's because it's getting timing info from the keyboard and since lmctl might be speeding this up it's move faster too.

- rmjb

---

### Post by rmjb on 2006-07-28
> **detyabozhye said:**
> 

[quote=Paradoxdruid;1309140]when I use windows, clicking the middle wheel in Firefox pops up a little "scroll up/down" icon and mouse movement then scrolls the page. Is this possible?

AFAIK, this is a Windows thing, it's just the way Windows works.
AFAIK, this is a Windows thing, it's just the way Windows works.
[/QUOTE]

There is an option in Firefox to enable this.

- rmjb

---

### Post by detyabozhye on 2006-07-28
> **rmjb said:**
> I think we will because is seems lmctl speeds up the sampling rate of the mouse. And since the mouse and keyboard probably use the same driver I'm having an interesting side effect... UT2004 is playing *[COLOR="Red"]blazingly[/COLOR]* fast. I don't just mean the frames are fast, but the entire game is screaming. Bots move faster, I move faster guns fire faster.

I'm thinking it's because it's getting timing info from the keyboard and since lmctl might be speeding this up it's move faster too.

- rmjb

Hmm, that's weird, LMCtl shouldn't affect keypress speed at all. :-k

---

### Post by rmjb on 2006-07-28
I'll turn off lmctl and play a game and see what happens, but I'm sure this is why.

- rmjb

---

### Post by Paradoxdruid on 2006-07-28
> **rmjb said:**
> There is an option in Firefox to enable this.

- rmjb

*deleted due to factual error*

---

### Post by matsur on 2006-07-28
Or check "Use autoscrolling" in Edit -> Preferences -> Advanced -> General.

---

### Post by Paradoxdruid on 2006-07-30
> **detyabozhye said:**
> 
Install xmodmap. Then do:
```
gedit ~/.Xmodmap
```
Paste this into there and save it:
```
pointer = 1 2 3 4 5 8 9 6 7 10 11 12 13 14 15
```
Then run xmodmap ~/.Xmodmap and if it complains about too little buttons add 16 17 etc untill it's satisfied. If it says there's too many, try deleting some starting at the end untill it works. Then give me the xev output.

Thanks for the advice.  xmodmap wanted there to be 20 buttons.

The xev output remained the same for the buttons (from my last post above).  Tilt left is button 11, tilt right is button 12.  No key registers as 6 or 7.  8 and 9 are the side "forward/back" buttons on the left of the mouse.  4 is scroll up, 5 scoll down.

I notice you set 8 and 9 before 6 and 7 in the pointer line...  should I try putting 11 and 12 there instead?

Thanks for the advice!

---

### Post by thecheat on 2006-07-30
Only having one problem. When you say:

> Make sure you keep the quote marks, save the file and run "xbindkeys" in the terminal I'm a total noob and don't know how to run that in terminal. Someone want to help me out real quick??

---

### Post by detyabozhye on 2006-07-31
> **thecheat said:**
> Only having one problem. When you say:

 I'm a total noob and don't know how to run that in terminal. Someone want to help me out real quick??

Go to Application->Accessories->Terminal, type xbindkeys in there, and hit enter.

---

### Post by detyabozhye on 2006-07-31
> **Paradoxdruid said:**
> Thanks for the advice.  xmodmap wanted there to be 20 buttons.

The xev output remained the same for the buttons (from my last post above).  Tilt left is button 11, tilt right is button 12.  No key registers as 6 or 7.  8 and 9 are the side "forward/back" buttons on the left of the mouse.  4 is scroll up, 5 scoll down.

I notice you set 8 and 9 before 6 and 7 in the pointer line...  should I try putting 11 and 12 there instead?

Thanks for the advice!

OK, try swapping 11 12 places with 6 7.
See if that changes anything.

---

### Post by rmjb on 2006-07-31
> **rmjb said:**
> I'll turn off lmctl and play a game and see what happens, but I'm sure this is why.

- rmjb

Okay that wasn't why. I commented out the lmctl line in /etc/init.d/local and rebooted, played a game and it was still freakishly fast. I'll put lmct back on in /etc/init.d/local.

- rmjb

---

### Post by Aurdal on 2006-07-31
How can I configure my 8th mousbutton to do Alt + Tab?

---

### Post by rmjb on 2006-07-31
> **Aurdal said:**
> How can I configure my 8th mousbutton to do Alt + Tab?

Or better yet, bring up a window list?

- rmjb

---

### Post by detyabozhye on 2006-07-31
The most practical solution that I know of is to write a custom window list program and launch it with button 8.

[http://ubuntuforums.org/showpost.php?p=1303372&postcount=39](http://ubuntuforums.org/showpost.php?p=1303372&postcount=39)

---

### Post by crispy_420 on 2006-08-01
Ok now everything works fine but one little thing.

I have a Logitech Elite Keyboard and it has a scroll wheel on it. Since messing with this it does not work. Is there a fix for that?

---

### Post by detyabozhye on 2006-08-01
Does it do anything in xev when you use the scroll wheel on the keyboard?

---

### Post by BatteryCell on 2006-08-01
Hm, is there any way to map unknown buttons, so like if I had a button on my keyboard that has a keycode but no "name" so to say, how would I map it?

Oh and to the windows list, if you map alt_l and f5 to button eight that brings up a windows list, but if you have any windows up then it doesnt work for me...so like the only way that it works for me is if no windows are maximized.

---

### Post by detyabozhye on 2006-08-01
> **BatteryCell said:**
> Hm, is there any way to map unknown buttons, so like if I had a button on my keyboard that has a keycode but no "name" so to say, how would I map it?

Um, I find the easiest way to do it is to use it in Keyboard Shortcuts, but I use Xfce, so I can map it to custom commands, but I don't know if that works in Gnome or KDE. You can try here for a way to do it in xbindkeys: [http://hocwp.free.fr/xbindkeys/xbindkeys.html](http://hocwp.free.fr/xbindkeys/xbindkeys.html) I haven't tried it though.

> **BatteryCell said:**
> Oh and to the windows list, if you map alt_l and f5 to button eight that brings up a windows list, but if you have any windows up then it doesnt work for me...so like the only way that it works for me is if no windows are maximized.

Well, I guess we could try searching for a window list app or a way to comunnicate with that list via D-Bus or something.

---

### Post by rmjb on 2006-08-01
One thing, my back button works in Firefox but not in Nautilus... I tried ALT+LEFT in Nautilus and that worked so I don't know why the back button doesn't.

Any ideas?

- rmjb

---

### Post by detyabozhye on 2006-08-01
is xbindkeys configured and running?
$ xbindkeys

if it is, give me your .xbindkeysrc

---

### Post by rmjb on 2006-08-01
Yeah it's running, needs to for the buttons to work in Firefox right? (I think).

Here's my ~/.xbindkeysrc:
```

###########################
# xbindkeys configuration #
###########################
#
# Version: 0.1.3
#
# If you edit this, do not forget to uncomment any lines that you change.
# The pound(#) symbol may be used anywhere for comments.
#
# A list of keys is in /usr/include/X11/keysym.h and in
# /usr/include/X11/keysymdef.h
# The XK_ is not needed.
#
# List of modifier (on my keyboard):
#   Control, Shift, Mod1 (Alt), Mod2 (NumLock),
#   Mod3 (CapsLock), Mod4, Mod5 (Scroll).
#
# Another way to specifie a key is to use 'xev' and set the
# keycode with c:nnn or the modifier with m:nnn where nnn is
# the keycode or the state returned by xev
#
# This file is created by xbindkey_config
# The structure is :
# # Remark
# "command"
# m:xxx + c:xxx
# Shift+...




#keystate_numlock = enable
#keystate_scrolllock = enable
#keystate_capslock = enable



#Back Button
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
   m:0x0 + b:8

#Forward Button
""/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
   m:0x0 + b:9

#
# End of xbindkeys configuration

```

- rmjb

---

### Post by detyabozhye on 2006-08-02
Firefox will also go back and forward on button 6 and 7, so xbindkeys isn't required for Firefox.
xvkbd should be in /usr/bin/ now instead of /usr/X11R6/bin/.
What button numbers do you get in xev for back and forward?

---

### Post by hubacap on 2006-08-02
> **detyabozhye said:**
> Hmm, everything looks correct. 

Ok, first thing I done was set the pistol down and stepped away from the computer...  Then, I glued my hair back to it's original place. 

I started this project over completely and got it all to work... YAY!!:grin: (except step 3, see edit below) Not sure what I was doing wrong and didn't try to analize it. I just started from scratch.

I did make a couple of changes because I went to the GUI version of XBindKeys-config <<main menu>Debian>Apps>Tools>XBindKeys-config>> and found some things that didn't look right in that editor, although I think it would have worked without the change.

My xbindkeysrc:
```
#back
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
   m:0x0 + b:8

#fwd
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
   m:0x0 + b:9

#ccup
"~/.click/click 4"
   m:0x0 + b:11

#ccdn
"~/.click/click 5"
   m:0x0 + b:12
``` The biggest thing is that it added a name (ie: #back) to the keybindings and a return (blank line) inbetween keybindings to separate them.

The only thing I would like to do is add an alt+tab for button 10 so I can switch between 2 programs easily. I tried different bindings to try to get the result I wanted to no avail. I noticed a "pause, hold" function in the keysymdef.h so I used it in several ways but never got any acceptable results. Could you supply some insight on this. You seem to know what you're doing...    not so much on this end. Still too new to Linux, but learning.

My alt-tab section of xbindkeysrc(commented out at the moment):
```
#side_middle
#"/usr/bin/xvkbd -sendevent -text "\[Alt_L]\[Tab]""
#   m:0x0 + b:10

``` 

[B]BTW: Thanks for the project and all the help you have provided and will provide.

Edit:[/B] After I wrote this I did step 3 with poor results. Mouse reacted VERY slowly to the point of being unusable. It seems to be very precise (more precise than I) without lmctl loaded so it is not an issue.

Thanks again for the walkthrough and help.=D>

I am running Ubunto 6.06 and a Logitech MX1000 mouse.

---

### Post by rmjb on 2006-08-02
> **detyabozhye said:**
> Firefox will also go back and forward on button 6 and 7, so xbindkeys isn't required for Firefox.
xvkbd should be in /usr/bin/ now instead of /usr/X11R6/bin/.
What button numbers do you get in xev for back and forward?

Nah, before this guide the back and forward buttons didn't work in Firefox, so this guide fixed that and I went through the xev thing with the buttons also.
xvkbd is in /usr/bin/xvkbd and /usr/bin/X11/xvkbd

- rmjb

---

### Post by detyabozhye on 2006-08-03
> **hubacap said:**
> The only thing I would like to do is add an alt+tab for button 10 so I can switch between 2 programs easily. I tried different bindings to try to get the result I wanted to no avail. I noticed a "pause, hold" function in the keysymdef.h so I used it in several ways but never got any acceptable results. Could you supply some insight on this. You seem to know what you're doing...    not so much on this end. Still too new to Linux, but learning.

My alt-tab section of xbindkeysrc(commented out at the moment):
```
#side_middle
#"/usr/bin/xvkbd -sendevent -text "\[Alt_L]\[Tab]""
#   m:0x0 + b:10

```

I haven't figured this out myself and never had the intention to do so. But since yall keep bugging me about it, I might play around with it. :D Just remember, without writing a new app that implements the window list, it will never act the way it does in Windows.

> **hubacap said:**
> [B]BTW: Thanks for the project and all the help you have provided and will provide.

Edit:[/B] After I wrote this I did step 3 with poor results. Mouse reacted VERY slowly to the point of being unusable. It seems to be very precise (more precise than I) without lmctl loaded so it is not an issue.

Thanks again for the walkthrough and help.=D>

I am running Ubunto 6.06 and a Logitech MX1000 mouse.

You're welcome. Section 3 is optional, but that behavior you described is the opposite of what usually happens, I really need to look into lomoco when I get a chance.

---

### Post by detyabozhye on 2006-08-03
> **rmjb said:**
> Nah, before this guide the back and forward buttons didn't work in Firefox, so this guide fixed that and I went through the xev thing with the buttons also.
xvkbd is in /usr/bin/xvkbd and /usr/bin/X11/xvkbd

- rmjb

Before this guide, your buttons weren't sending out the button 6 and 7 or 8 and 9 event at all, the evdev driver fixed that part, not xbindkeys.

Try the following configurations (one at a time ;)):

```
#Back Button
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[_L_eft]""
   m:0x0 + b:8

#Forward Button
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[_R_ight]""
   m:0x0 + b:9
```

```
#Back Button
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[_L_eft]""
   m:0x0 + b:6

#Forward Button
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[_R_ight]""
   m:0x0 + b:7
```

---

### Post by rmjb on 2006-08-03
> **detyabozhye said:**
> Before this guide, your buttons weren't sending out the button 6 and 7 or 8 and 9 event at all, the evdev driver fixed that part, not xbindkeys.

Ohh... well that makes sense. Will try it when I get back home.

- rmjb

---

### Post by ricesteam on 2006-08-03
W00t finally got my Logitech G7 fully functioning.  Here are my config files for reference (yours will be different)


xorg.conf
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Dev Name"      "Logitech USB Receiver"
        Option          "Dev Phys"      "usb-0000:00:1d.0-1/input0"
        Option          "Device"        "/dev/input/event1"
        Option          "Buttons"       "8"
        Option          "ZAxisMapping"  "4 5 7 8"
EndSection

```

~/.xbindkeysrc (I use the Opera browser)
```

#Back Button
"/usr/bin/xvkbd -xsendevent -text "\[BackSpace]""
   m:0x0 + b:8
#Right scroll
"/usr/bin/xvkbd -xsendevent -text "\[Right]""
   m:0x0 + b:6
#Left Scroll
"/usr/bin/xvkbd -xsendevent -text "\[Left]""
   m:0x0 + b:7

```

Originally I had lots of trouble with xbindkeys. If you can't get it working, do what detyabozhye suggest and config your keys one by one.  Remember to killall xbindkeys and rerun it to refresh the settings.

edit: "right" and "left" should both have capital first letters. ie "Right", "Left"

---

### Post by rmjb on 2006-08-03
Just a heads up, I got some linux header updates through update-manager and when I rebooted my mouse did not work.

When going through the guide initially I did not set my input/eventX to 9 but to what input/eventX was in /proc/bus/input/devices (2 in my case) and set the udev rule accordingly.

Anyhow after the update /proc/bus/input/devices listed my mouse as 3 even though the udev rule said 2.

After setting it to 9, as I should have done in the first place, and rebooting I have back my mouse.

- rmjb

---

### Post by zero17388 on 2006-08-06
hi everybody, It works!!!!! i have a wireless logitech desktop (mouse and keyboard on the same receiver) and i've tried your new Howto many times but it didn't work neither with gnome nor xgl. 
     Under gnome all my mouse's buttons were recognise by xev but my keyboard was just totally crazy (keys were upside down) and I couldn't load X under xgl ](*,) . 
     So I tried many things and thanks to the german site (I don't understand a word of germen but a french guy did), i've tried this: no udev, only the xorg.conf:

Section "InputDevice"
   Identifier   "Configured Mouse"
   Driver      "evdev"
   Option      "Name"      "Logitech USB Receiver"
   Option         "Device" "/dev/input/event2"
   Option      "Emulate3Buttons"   "false"
   Option      "WHEELRelativeAxisButtons"   "4 5"
   Option      "HWHEELRelativeAxisButtons"   "7 6"
   Option      "SendCoreEvents"   "true"
EndSection

and here's the cat:

I: Bus=0003 Vendor=046d Product=c512 Version=3900
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:10.1-2/input1
S: Sysfs=/class/input/input2
H: Handlers=kbd mouse0 event2 ts0
B: EV=7
B: KEY=7fffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff 0 0 1878 d800d100 1e0000 0 0 0
B: REL=143

Ihope it could help some people because it really mades me crazy... And sorry for my poor english but I'm french...:rolleyes:

---

### Post by ricesteam on 2006-08-06
I have the same problem as well...

Can you tell me the steps on how to set your mouse to 9 ???

I don't understand what you mean by that.


> **rmjb said:**
> Just a heads up, I got some linux header updates through update-manager and when I rebooted my mouse did not work.

When going through the guide initially I did not set my input/eventX to 9 but to what input/eventX was in /proc/bus/input/devices (2 in my case) and set the udev rule accordingly.

Anyhow after the update /proc/bus/input/devices listed my mouse as 3 even though the udev rule said 2.

After setting it to 9, as I should have done in the first place, and rebooting I have back my mouse.

- rmjb

---

### Post by ConstableRoark on 2006-08-06
So has anyone found a solution to the problem of the inactive media keys on the Logitech MX Duo and similar products?

---

### Post by rmjb on 2006-08-06
> **ricesteam said:**
> I have the same problem as well...

Can you tell me the steps on how to set your mouse to 9 ???

I don't understand what you mean by that.

Follow part 2 of section 1:
[http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894)

- rmjb

---

### Post by detyabozhye on 2006-08-07
> **ConstableRoark said:**
> So has anyone found a solution to the problem of the inactive media keys on the Logitech MX Duo and similar products?

OK, before you did this guide, was your mouse and keyboard (assuming they use one reciever) hooked up by USB or PS/2?

I'm assuming that they are now hooked up by USB, as they wouldn't be able to work with evdev on PS/2.

The kernel USB drivers don't recognize some media keys, so if you can't get anything in xev when you press media keys, most likely you won't be able to get them to work without patching the kernel (which I'm not all too sure about how to do).

---

### Post by zero17388 on 2006-08-08
well I still have a pb, the event number of my mouse changes at startup, so the udev should that but my keyboard and my mouse have the same name, "Logitech USB Receiver" so it doesn't work.
 The pb comes from the "PC Speaker" which changes its event number between the number 2 and the number 0 and so change all the event numbers.Is it possible to desactivate the "PC Speaker"? because I don't care about it...

---

### Post by zero17388 on 2006-08-08
Maybe i've found something, in fact I use the udev rules to move the event number of "PC Speaker" to "event9" and so it seems that the event number of my keyboard an mouse are not changing any more!!! So I could configure my xorg.conf. Here are my different settings:

##cat /proc/bus/input/devices
> I: Bus=0003 Vendor=046d Product=c512 Version=3900
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:10.1-2/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c512 Version=3900
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:10.1-2/input1
S: Sysfs=/class/input/input2
H: Handlers=kbd mouse0 event2 ts0
B: EV=7
B: KEY=7fffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff 0 0 1878 d800d100 1e0000 0 0 0
B: REL=143


##udev rule in /etc/udev/rules.d/19-local.rules :

> KERNEL=="event[0-9]*", SYSFS{../name}=="PC Speaker", NAME="input/event9"

##ls /dev/input/ :
> event0  event2  event9  mice  mouse0  ts0

##/etc/X11/xorg.conf :
> Section "InputDevice"
   Identifier   "Configured Mouse"
   Driver      "evdev"
   Option      "Name" "Logitech USB Receiver"
   Option      "Device" "/dev/input/event2"
   Option      "Emulate3Buttons"   "false"
   Option      "WHEELRelativeAxisButtons"   "4 5"
   Option      "HWHEELRelativeAxisButtons"   "9 8"
   Option      "SendCoreEvents"   "true"
EndSection

Hope it will works for a long but after 3 restart, still working... Hope it could help... And thanks detyabozhye, for your help maybe I will need your help soon...

---

### Post by thomasf on 2006-08-08
> **detyabozhye said:**
> 
The kernel USB drivers don't recognize some media keys, so if you can't get anything in xev when you press media keys, most likely you won't be able to get them to work without patching the kernel (which I'm not all too sure about how to do).

Yes, that's true. I use Logitech MX 3100 wireless set (keyboard + MX1000 mouse) and I have to decide - fully functional keyboard(connected by PS/2) or fully functional mouse (connected by USB). If I use USB connection, most multimedia keys don't work. I spent hours googling for solution but it seems we have to wait for appropiate kernel patch. However, I found something interesting on KernelTrap.org - [http://kerneltrap.org/node/6460]("http://kerneltrap.org/node/6460")
As you can see user LEETE posted a kernel patch. I tried to apply it but something went wrong. I'm a beginner not familiar with progamming and kernel patching issues so maybe I'm making some mistakes. This is what I've done:
1)I've made empty text file in /usr/src/linux. I've named it hid_patch
2)I've pasted the patch posted on KernelTrap into hid_patch
3)In the terminal I've issued command:
```
root@ubuntu:/usr/src/linux# patch -p0 < hid_patch
patching file drivers/usb/input/hid-core.c
patch: **** malformed patch at line 4: value[n] = min < 0 ? snto32(extract(data, offset + n * size, size), size) :
```

Any ideas?

USB keyboards are present on the market for years...I'm surprised that Linux support them only partially.

---

### Post by detyabozhye on 2006-08-08
@zero17388: Nice find! and you're welcome. ^_^

@thomasf: AFAIK, the 2.4 series kernel had better support for media keys on a USB keyboard, not sure though. The problem with patching the kernel in Ubuntu is the kernel is updated more often then some other Linux distros.

---

### Post by thomasf on 2006-08-08
> The problem with patching the kernel in Ubuntu is the kernel is updated more often then some other Linux distros.

I tried to patch kernel 2.6.17.8(from kernel.org) but I understand what you mean - there must have been some changes in code or simpy patch is broken.

---

### Post by zero17388 on 2006-08-09
I still have a pb, when the "PC Speaker" is intitially at "event0" my jeyboard is at "event1" and my mouse at "event2" so my xorg is good. But when "PC Speaker" is initially at "event2" kb is at "event0" and mouse at "event1" so my xorg isn't good any more... So tried to force "PC Speaker" at "event0" with udev but I don't know what will happen when at startup my keyboard will be at "event0" before the udev ???? Wait and see...

---

### Post by zero17388 on 2006-08-09
> So tried to force "PC Speaker" at "event0" with udev but I don't know what will happen when at startup my keyboard will be at "event0" before the udev

it doesn't work, there's no conflict but my kb and PC Speaker are on event0 and my mouse at event1 when xorg is configure for event2... Don't know what to do, maybe delete PC Speaker, if you have any idea you're welcome...

---

### Post by thomasf on 2006-08-09
> **zero17388 said:**
> Don't know what to do, maybe delete PC Speaker, if you have any idea you're welcome...

After executing command ```
sudo rmmod pcspkr
``` PC speaker disappears from /proc/bus/input/devices so maybe you should blacklist pcspkr. Try to add "blacklist pcspkr" to /etc/modprobe.d/blacklist and tell whether it helps or not.

---

### Post by zero17388 on 2006-08-09
> **thomasf said:**
> After executing command ```
sudo rmmod pcspkr
``` PC speaker disappears from /proc/bus/input/devices so maybe you should blacklist pcspkr. Try to add "blacklist pcspkr" to /etc/modprobe.d/blacklist and tell whether it helps or not.

Thanks a lot thomasf, indeed pcskr has disappear and now everything is working like a charm :D

---

### Post by ztripez on 2006-08-09
I'm using a Logitech diNovo desktop and can't get it to work at all.

A cat /proc/bus/input/devices returns:

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

I: Bus=0003 Vendor=046d Product=c70b Version=4003
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:02.0-9.2/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c70c Version=4003
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:02.0-9.3/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd mouse0 event2 ts0
B: EV=f
B: KEY=c0002 400 0 0 fff0001 f80 78000 6039fa d841d7ad 9e0000 0 0 0
B: REL=1c3
B: ABS=1 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3
B: EV=40001
B: SND=6
```

As you can se i got 2 "Logitech Logitech BT Mini-Receiver" (The bluetooth dongle).

When i make the rule I input 
"Logitech Logitech BT Mini-Receiver" instead of "Logitech USB-PS/2 Optical Mouse" but as you can se i got 2 instances for that name (kb and mouse) and how do i tell the rule wich one to choose?


When i follow the guide X won't start at all.

---

### Post by zero17388 on 2006-08-09
> **ztripez said:**
> I'm using a Logitech diNovo desktop and can't get it to work at all.

A cat /proc/bus/input/devices returns:

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

I: Bus=0003 Vendor=046d Product=c70b Version=4003
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:02.0-9.2/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c70c Version=4003
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:02.0-9.3/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd mouse0 event2 ts0
B: EV=f
B: KEY=c0002 400 0 0 fff0001 f80 78000 6039fa d841d7ad 9e0000 0 0 0
B: REL=1c3
B: ABS=1 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3
B: EV=40001
B: SND=6
```

As you can se i got 2 "Logitech Logitech BT Mini-Receiver" (The bluetooth dongle).

When i make the rule I input 
"Logitech Logitech BT Mini-Receiver" instead of "Logitech USB-PS/2 Optical Mouse" but as you can se i got 2 instances for that name (kb and mouse) and how do i tell the rule wich one to choose?


When i follow the guide X won't start at all.

  Maybe look to my previous posts, I had the same pb but thanks to thomasf now it's ok, so first you have to know if the event number of your mouse (which is 2 in your exemple). If it changes maybe your pb is the same as mine. Have you used the the udev? How looks your xorg.conf?

---

### Post by thomasf on 2006-08-09
@zero17388 - I'm glad I could help :)

It seems that I found solution to udev rule problem with USB base station used to connect 2 devices (mouse + keyboard). I've tested it on Logitech MX3100 (keyboard + MX1000 mouse). It seems that it works.

```
tomek@ubuntu:~$ cat /proc/bus/input/devices
I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c512 Version=3007
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.1-3/input0
S: **Sysfs=/class/input/input1**
H: Handlers=kbd event1
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c512 Version=3007
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.1-3/input1
S: **Sysfs=/class/input/input2**
H: Handlers=kbd mouse0 event2 ts0
B: EV=7
B: KEY=7fffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff 0 0 1878 d800d100 1e0000 0 0 0
B: REL=143

I: Bus=0001 Vendor=1461 Product=000b Version=0001
N: Name="cx88 IR (AverTV Studio 303 (M12"
P: Phys=pci-0000:01:08.0/ir0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3
B: EV=100003
B: KEY=403c310 82140000 0 0 0 0 244c000 20180 4001 921680 0 0 efd

```

I analyzed files and directories in /sys/class/input/input1 (keyboard) and /sys/class/input/input2 (mouse) and noticed that /sys/class/input/input1/device/bInterfaceNumber and /sys/class/input/input2/device/bInterfaceNumber are diffrent. 
bInterfaceNumber for input1 (keyboard) is 00 and for input2 (mouse) - 01.
This is modified udev rule which utilizes this fact:
```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", SYSFS{../device/bInterfaceNumber}=="01", NAME="input/event9"
```
I guess that ```
KERNEL=="event[0-9]*", SYSFS{../device/bInterfaceNumber}=="01", NAME="input/event9"
``` should be enough.

Can someone test it and check whether it works or not?

@ztripez - You have a bit diffrent hardware but you can try this udev rule. If, however, it won't work, solution to your problem is probably similar.

---

### Post by Damiel on 2006-08-10
just changing the name and the device in this config made my logitech mx510 work perfectly in firefox and opera (including the cruise buttons). thanks! :D 

thanks to detyabozhye too for the great xbindkeys guide.

> **zero17388 said:**
> hi everybody, It works!!!!! i have a wireless logitech desktop (mouse and keyboard on the same receiver) and i've tried your new Howto many times but it didn't work neither with gnome nor xgl. 
     Under gnome all my mouse's buttons were recognise by xev but my keyboard was just totally crazy (keys were upside down) and I couldn't load X under xgl ](*,) . 
     So I tried many things and thanks to the german site (I don't understand a word of germen but a french guy did), i've tried this: no udev, only the xorg.conf:

Section "InputDevice"
   Identifier   "Configured Mouse"
   Driver      "evdev"
   Option      "Name"      "Logitech USB Receiver"
   Option         "Device" "/dev/input/event2"
   Option      "Emulate3Buttons"   "false"
   Option      "WHEELRelativeAxisButtons"   "4 5"
   Option      "HWHEELRelativeAxisButtons"   "7 6"
   Option      "SendCoreEvents"   "true"
EndSection

...

Ihope it could help some people because it really mades me crazy... And sorry for my poor english but I'm french...:rolleyes:

---

### Post by zero17388 on 2006-08-10
> **thomasf said:**
> @zero17388 - I'm glad I could help :)

It seems that I found solution to udev rule problem with USB base station used to connect 2 devices (mouse + keyboard). I've tested it on Logitech MX3100 (keyboard + MX1000 mouse). It seems that it works.

I analyzed files and directories in /sys/class/input/input1 (keyboard) and /sys/class/input/input2 (mouse) and noticed that /sys/class/input/input1/device/bInterfaceNumber and /sys/class/input/input2/device/bInterfaceNumber are diffrent. 
bInterfaceNumber for input1 (keyboard) is 00 and for input2 (mouse) - 01.
This is modified udev rule which utilizes this fact:
```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", SYSFS{../device/bInterfaceNumber}=="01", NAME="input/event9"
```
I guess that ```
KERNEL=="event[0-9]*", SYSFS{../device/bInterfaceNumber}=="01", NAME="input/event9"
``` should be enough.

Can someone test it and check whether it works or not?

@ztripez - You have a bit diffrent hardware but you can try this udev rule. If, however, it won't work, solution to your problem is probably similar.

It works for me too, I've removed my blacklist and so activate pcskr and with your udev it's working perfectly. Thanks again, again and ... again :-P

---

### Post by trxDraxon on 2006-08-10
I have a MX518 and I have gotten the back and forward and app switcher buttons to work but I cant get the dpi up and down buttons to work.  I am not really sure what to try next as I am pretty new to getting stuff working under linux.

> raistlin@dragonstear:~$ cat /proc/bus/input/devices
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c01e Version=2200
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:02.1-3/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event2 ts0
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103



> raistlin@dragonstear:~$ sudo lmctl -8
001.003: 046d:0a01 Unknown or Unsupported Logitech device
002.002: 046d:c01e Unknown or Unsupported Logitech device

./xbindkeysrc
> "/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7
"/usr/bin/xvkbd -xsendevent -text "\[x]""
  m:0x0 + b:8


Also,under xev the dpi up and down buttons do not register events at all.

---

### Post by thomasf on 2006-08-10
Did you edit xorg.conf in order to use evdev? Default driver doesn't register events from all buttons.

---

### Post by trxDraxon on 2006-08-10
Yes I did, this is what I added to it:

> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/event9" #this should be that underlined name from 19-local.rules
EndSection

---

### Post by detyabozhye on 2006-08-10
[QUOTE=trxDraxon]raistlin@dragonstear:~$ sudo lmctl -8
001.003: 046d:0a01 Unknown or Unsupported Logitech device
002.002: 046d:c01e Unknown or Unsupported Logitech device[/QUOTE]

I replaced LMCtl with lomoco in the tutorial, try that instead of LMCtl.

---

### Post by zergberg on 2006-08-10
> **detyabozhye said:**
> OK, before you did this guide, was your mouse and keyboard (assuming they use one reciever) hooked up by USB or PS/2?

I'm assuming that they are now hooked up by USB, as they wouldn't be able to work with evdev on PS/2.

The kernel USB drivers don't recognize some media keys, so if you can't get anything in xev when you press media keys, most likely you won't be able to get them to work without patching the kernel (which I'm not all too sure about how to do).
Oddly, the kernel recognizes *most* of the keys for me, **but only without evdev on**. Granted, some aren't there and some appear as mouse buttons, but the media keys themselves were fine.

I think this is more related to evdev's handling of mouse/keyboard receiver combos (MX Cordless Desktop here) than kernel problems, at least for some buttons.

---

### Post by detyabozhye on 2006-08-10
Might be both, but the kernel issue is a known one for some keyboards.

---

### Post by trxDraxon on 2006-08-10
Okay got the cruise buttons to work with lomoco.  They now change the DPI on the fly no problem.  But they still dont create an event in xev.  What I want to get done is be able to map them to a key say F for use as a keybind in games.  Not sure what im doing wrong if im just over looking something since im a newb.  I followed the guild exactly and everything works just fine.

---

### Post by thomasf on 2006-08-11
> **zergberg said:**
> Oddly, the kernel recognizes *most* of the keys for me, **but only without evdev on**.

I confirm that.That's my case - extra keys stop working when evdev is enabled in xorg.conf (though evdev is turned on theoretically only for mouse). I found quite interesting topic on Gentoo forum - [http://forums.gentoo.org/viewtopic-t-445810.html]("http://forums.gentoo.org/viewtopic-t-445810.html") Maybe we should try newer version of evdev? But guys from Gentoo forum probably used the newest one...

UPDATE: I've checked Xorg CVS - evdev 1.1.2 is the newest one. It's already included in Ubuntu.

---

### Post by detyabozhye on 2006-08-11
Well, I guess we could try using the evdev driver for the keyboard as well, although I don't know what the results will be.

---

### Post by Tom Brokaw on 2006-08-11
Cool How-to, thanks for posting it.  I have a question:
To the best of your knowledge, will this work if the mouse is going through a KVM?  Or does it absolutely have to be plugged into a USB port?

Thanks!

---

### Post by detyabozhye on 2006-08-11
Um, I think someone had trouble with using it with a KVM when he would switch then switch back. AFAIK, that should be fixed in Edgy.

---

### Post by thomasf on 2006-08-12
> **detyabozhye said:**
> Well, I guess we could try using the evdev driver for the keyboard as well, although I don't know what the results will be.

Unfortunately, it doesn't work. With evdev, keyboard went mad - arrows stopped working, del key acted as printscreen etc. I didn't investigate this problem (it was useless because extra keys didn't work), maybe it's layout issue.

---

### Post by BatteryCell on 2006-08-12
Ok I finally figured out how to do the alt-tab thing with the mouse, well kind of.  Theres a program called Kompose, which in my opinion is actually better than alt-tab, and you can configure it so that when you move your mouse to a particular part of the screen it will automatically come up.  Not exactly a button on the mouse but I find that it works just as well.
To install just search for Kompose in synaptic or adept.
After that, just start it and then right click on the icon that appears in the  system tray, configure compose, and then pick how you want it to auto-activate.

---

### Post by glycerin on 2006-08-13
Can anyone tell me which out of all these instructions that I need to use to configure all buttons/resolution with my Microsoft Intellimouse Explorer 4.0 mouse?
```
I: Bus=0003 Vendor=045e Product=0095 Version=0419
N: Name="Microsoft Microsoft IntelliMouse&#65533; Explorer"
P: Phys=usb-0000:00:0f.2-1/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=1c3
```

---

### Post by Dougie187 on 2006-08-13
Hey, Thanks for the guide. Though it's not quite working for me. Two questions. I was wondering if anyone has gotten Lomoco to work for wireless mice. I am using a Logitech v400 right now, Best laptop mouse I have ever used. Anyways when I type sudo lomoco -8 it prints out "003.002: 046d:c518 Unsupported Logitech device: USB Receiver".

And for the next question. I was curious if you could tell me what 
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
does. Particularly what the m:0x0 is doing. I think i got the rest of it but when you told us how to do the cruise control it kind of threw me off a bit. So maybe if you could explain what the xbindkeys takes as input that would help. Thanks!

EDIT: Two things. First I got my mouse to work with the back and forward buttons using the KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", SYSFS{../device/bInterfaceNumber}=="01", NAME="input/event9"
 line. Since its wireless usb it has both the usb mouse and keyboard in events. Also What im looking for in the xbindkeyssrc thing is i want be able to bind other keys. Like say my tablet buttons because im running a tablet pc. Or maybe the windows key.

---

### Post by thomasf on 2006-08-14
> **Dougie187 said:**
> Hey, Thanks for the guide. Though it's not quite working for me. Two questions. I was wondering if anyone has gotten Lomoco to work for wireless mice. I am using a Logitech v400 right now, Best laptop mouse I have ever used. Anyways when I type sudo lomoco -8 it prints out "003.002: 046d:c518 Unsupported Logitech device: USB Receiver".

AFAIK lomoco doesn't support all Logitech mice. Look here [http://lomoco.linux-gamers.net/]("http://lomoco.linux-gamers.net/")

---

### Post by detyabozhye on 2006-08-14
> **glycerin said:**
> Can anyone tell me which out of all these instructions that I need to use to configure all buttons/resolution with my Microsoft Intellimouse Explorer 4.0 mouse?
```
I: Bus=0003 Vendor=045e Product=0095 Version=0419
N: Name="Microsoft Microsoft IntelliMouse&#65533; Explorer"
P: Phys=usb-0000:00:0f.2-1/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=1c3
```

Well, I'd say start with the evdev part and see what works and what doesn't, then we can help out further.

---

### Post by detyabozhye on 2006-08-14
> **Dougie187 said:**
> Hey, Thanks for the guide. Though it's not quite working for me. Two questions. I was wondering if anyone has gotten Lomoco to work for wireless mice. I am using a Logitech v400 right now, Best laptop mouse I have ever used. Anyways when I type sudo lomoco -8 it prints out "003.002: 046d:c518 Unsupported Logitech device: USB Receiver".

Isn't the v400 at a high resolution by default? I don't know, but I'd assume it is, being a Laser mouse.

> **Dougie187 said:**
> And for the next question. I was curious if you could tell me what 
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
does. Particularly what the m:0x0 is doing. I think i got the rest of it but when you told us how to do the cruise control it kind of threw me off a bit. So maybe if you could explain what the xbindkeys takes as input that would help. Thanks!

The m:0x0 is the state of the keyboard. And the v400 doesn't have cruise control AFAIK.

EDIT: Two things. First I got my mouse to work with the back and forward buttons using the KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", SYSFS{../device/bInterfaceNumber}=="01", NAME="input/event9"
 line. Since its wireless usb it has both the usb mouse and keyboard in events. Also What im looking for in the xbindkeyssrc thing is i want be able to bind other keys. Like say my tablet buttons because im running a tablet pc. Or maybe the windows key.[/QUOTE]

I don't get what you mean in the first part. Are you saying you're afraid the mouse will interfere with the keyboard? As for mapping those keys, I'm sure it's possible, as long as they fire an xev event, but I don't know xbindkeys enough for that.

---

### Post by Dougie187 on 2006-08-16
So. I think the v400 is 800dpi by default. But im not sure. I thought lomoco could be used for more then that so i wanted to check it out. I know that the v400 doesnt have Cruise. I just wanted it for binding other keys. I haven't gotten it to work yet. I haven't read anything that helped yet so if anyone knows how to bind keys, especially tablet buttons, that would help alot.

---

### Post by Fisslefink on 2006-08-17
This method worked for me with a Logitech UltraX Media Center Remote (Model R-RC6).  I added the rule to /etc/udev/rules.d/20-names.rules

This remote does not have a keyboard and a mouse component, per se, but the USB dongle sends commands from the remote as two separate devices:

event1: All keys that resemble keyboard keys (ie. Home, 0-9, up, down, left, right, clear, enter, back)
event2: All keys that are special to the remote (ie. play, pause, stop, close, repeat, info)

As with the Logitech MX 1000 keyboard, the boot detection order of the USB devices can change depending on where they are plugged in.  The rule below makes event2 into a static device at** /dev/input/logitechremote** so that my xorg.conf section (see below) will find it no matter where it is plugged in.  

Here is my /etc/udev/rules.d/20-names.rules with the addition in **bold**:

```
# This file establishes the device names according to Ubuntu policy.
# See udev(8) for syntax.
#
# Permissions and ownership of devices must not be set here, but in
# 40-permissions.rules; user-friendly symlinks to devices should be
# set in 60-symlinks.rules.

# CPU devices, group under /dev/cpu
KERNEL=="cpu[0-9]*",			NAME="cpu/%n/cpuid"
KERNEL=="msr[0-9]*",			NAME="cpu/%n/msr"
KERNEL=="microcode",			NAME="cpu/microcode"

# Device mapper targets
KERNEL=="device-mapper",		NAME="mapper/control"
KERNEL=="dm-[0-9]*",			OPTIONS+="ignore_device"

# IEEE1394 devices, group under their own directories
KERNEL=="dv1394-[0-9]*",		NAME="dv1394/%n"
KERNEL=="video1394-[0-9]*",		NAME="video1394/%n"

# Input devices, group under /dev/input
**KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", SYSFS{../device/bInterfaceNumber}=="01", NAME="input/logitechremote"**
KERNEL=="event[0-9]*",			NAME="input/%k"
KERNEL=="mice",				NAME="input/%k"
KERNEL=="mouse[0-9]*",			NAME="input/%k"
KERNEL=="js[0-9]*",			NAME="input/%k"
KERNEL=="ts[0-9]*",			NAME="input/%k"
KERNEL=="uinput",			NAME="input/%k"

# ISDN devices, group under /dev/capi
KERNEL=="capi",				NAME="capi20"
KERNEL=="capi[0-9]*",			NAME="capi/%n"

# Packet CD devices, group under /dev/pktcdvd
KERNEL=="pktcdvd",			NAME="pktcdvd/control"
KERNEL=="pktcdvd[0-9]*",		NAME="pktcdvd/%k"

# Sound devices, group under /dev/snd
KERNEL=="controlC[0-9]*",		NAME="snd/%k"
KERNEL=="hwC[D0-9]*",			NAME="snd/%k"
KERNEL=="midiC[D0-9]*",			NAME="snd/%k"
KERNEL=="pcmC[D0-9cp]*",		NAME="snd/%k"
KERNEL=="seq",				NAME="snd/%k"
KERNEL=="timer",			NAME="snd/%k"

# USB devices (usbfs replacement), group under /dev/bus/usb
SUBSYSTEM!="usb_device", GOTO="usb_device_end"
IMPORT{program}="usb_device_name --export %k"
ENV{USB_BUS}=="?*", ENV{USB_DEV}=="?*",	\
	NAME="bus/usb/$env{USB_BUS}/$env{USB_DEV}"
LABEL="usb_device_end"

# Video devices, group dvb devices under /dev/dvb
SUBSYSTEM!="dvb", GOTO="dvb_end"
IMPORT{program}="dvb_device_name --export %k"
ENV{DVB_ADAPTER}=="?*", ENV{DVB_DEV}=="?*", \
	NAME="dvb/adapter$env{DVB_ADAPTER}/$env{DVB_NAME}"
LABEL="dvb_end"

# Video devices, group cards under /dev/dri
KERNEL=="card[0-9]*",			NAME="dri/%k"

# Zaptel devices, group under /dev/zap
KERNEL=="zapctl",			NAME="zap/ctl"
KERNEL=="zaptimer",			NAME="zap/timer"
KERNEL=="zapchannel",			NAME="zap/channel"
KERNEL=="zappseudo",			NAME="zap/pseudo"
KERNEL=="zap[0-9]*",			NAME="zap/%n"

# Work-around for IDE devices that don't report media changes
BUS=="ide", KERNEL=="hd[a-z]", SYSFS{removable}=="1", \
	ENV{ID_MODEL}=="IOMEGA_ZIP*",	NAME{all_partitions}="%k"

# SCSI CD-ROM devices use /dev/scdN now
BUS=="scsi", KERNEL=="sr[0-9]*",	NAME="scd%n"

# USB printers need to be /dev/usb*
BUS=="usb", KERNEL=="lp[0-9]*",		NAME="usb%k"

# Other devices
KERNEL=="hw_random",			NAME="hwrng"
KERNEL=="tun",				NAME="net/%k"

```

Here are the relevant lines from my /etc/X11/xorg.conf:
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"[B]
	InputDevice    "remote" "SendCoreEvents"[/B]
EndSection
[B]
Section "InputDevice"
	Identifier  "remote"
	Driver      "evdev"
	Option	    "Name" "Logitech USB Receiver"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "evdev"
	Option	    "Device" "/dev/input/logitechremote"
	Option	    "Protocol" "evdev"
EndSection[/B]
```

Hope this helps someone.  Thanks to the other posters on this thread!

Fisslefink

---

### Post by detyabozhye on 2006-08-17
[quote=Dougie187]So. I think the v400 is 800dpi by default. But im not sure. I thought lomoco could be used for more then that so i wanted to check it out. I know that the v400 doesnt have Cruise. I just wanted it for binding other keys. I haven't gotten it to work yet. I haven't read anything that helped yet so if anyone knows how to bind keys, especially tablet buttons, that would help alot.[/quote]

Well, you would do something like this:

"/full/path/to-app -any -needed arguements"
m:0x0 + b:8 #<- replace with the button number you get in xev

---

### Post by apakatt on 2006-08-17
I have a problem.
The forward / backward doesnt work in Konqueror but it works in Opera and Firefox. 
If i check Settings - Shortcuts, forward and backward is binded to alt+left and alt+right.

Any idea what the problem could be?

---

### Post by rmjb on 2006-08-18
> **apakatt said:**
> I have a problem.
The forward / backward doesnt work in Konqueror but it works in Opera and Firefox. 
If i check Settings - Shortcuts, forward and backward is binded to alt+left and alt+right.

Any idea what the problem could be?

I had this similar problem (works in the browser, not the file manager).

My post on this is here:
[http://ubuntuforums.org/showthread.php?t=219894&page=9#post1327523](http://ubuntuforums.org/showthread.php?t=219894&page=9#post1327523)

And here's detyabozhye's solution and explanation as to why it happened:
[http://ubuntuforums.org/showthread.php?t=219894&page=9#post1332116](http://ubuntuforums.org/showthread.php?t=219894&page=9#post1332116)

Good luck.

- rmjb

---

### Post by Mr. Sinister on 2006-08-20
I followed the older version and got my mx610 to work. Then I munged things up with an update. Since then (even following this new guide), I cannot get it to work. I get the following error:
```
(II) evdev brain: Rescanning devices (1).
(**) Option "CorePointer"
(**) Configured Mouse-usb-0000:00:02.1-9.4/input1: Core Pointer
(II) Configured Mouse-usb-0000:00:02.1-9.4/input1: Found 1 absolute axes.
(II) Configured Mouse-usb-0000:00:02.1-9.4/input1: Configuring as pointer.
(**) Configured Mouse-usb-0000:00:02.1-9.4/input1: Configuring in Absolute mode.
(**) Configured Mouse-usb-0000:00:02.1-9.4/input1: AbsoluteScreen: -1.

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x86) [0x80b4a86]
1: [0xffffe420]
2: /usr/lib/xorg/modules/input/evdev_drv.so [0xb73804a3]
3: /usr/lib/xorg/modules/input/evdev_drv.so [0xb7381655]
4: /usr/lib/xorg/modules/input/evdev_drv.so(evdevNewDriver+0x44) [0xb7381c3f]
5: /usr/lib/xorg/modules/input/evdev_drv.so [0xb7380b8e]
6: /usr/bin/X(InitInput+0x1a0) [0x809cfe5]
7: /usr/bin/X(main+0x368) [0x806df94]
8: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7d99ea2]
9: /usr/bin/X(FontFileCompleteXLFD+0x81) [0x806d611]
```

Any ideas?
I'm using an mx610(lefty), which has two inputs under /proc/bus/input/devices.
```
I: Bus=0003 Vendor=046d Product=c518 Version=4202
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.1-9.4/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0003 Vendor=046d Product=c518 Version=4202
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.1-9.4/input1
S: Sysfs=/class/input/input2
H: Handlers=kbd event2
B: EV=f
B: KEY=c0002 400 0 0 1 f80 78000 6039fa d84157ad 8e0000 0 0 0
B: REL=40
B: ABS=1 0
```

---

### Post by rmjb on 2006-08-20
Try using the udev rule to set your mouse to event9... other devices might be grabing the lower event numbers.

- rmjb

---

### Post by tocky on 2006-08-20
After I've given this tutorial several tries, I've finally managed to get it work properly, with my Logitech Mx610. Thank you very much:-D

---

### Post by MikeBenza on 2006-08-20
I'm an idiot.  Apparently the number lock LED doesn't work on my laptop...that got hit at some point, and made me think my keymap was borked.  And I made a whole post about it....then I realized the proclivity for keys on the right side of the keyboard to make numbers.  And I can't delete this, so maybe some mod will spare me the embarassment.

---

### Post by ijanos on 2006-08-20
Hi! Nice howto, now my MX500 is fully functional. Except that lomoco is not start at boot. I think i did everything right, and i can see the local service is enabled but it simply not start. I see no clue in dmesg nor in the syslog. Any help?

---

### Post by n00blar on 2006-08-20
Great HOWTO, but some reason it worked on my **Logitech MX500** for a bit and then it stopped working after a couple of reboots, and now I can't figure out what's wrong. ](*,) 

Here's what my config looks like.

1.) cat /proc/bus/input/devices

shows:

I: Bus=0003 Vendor=046d Product=c025 Version=1800
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:0b.0-5/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse1 event3 ts1
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

2.)  ls /dev/input/
reads:

event0  event1  event2  event9  mice  mouse0  mouse1  ts0  ts1

3.) sudo gedit /etc/udev/rules.d/19-local.rules

reads:

KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB-PS/2 Optical Mouse", NAME="input/event9"

4.) InputDevice section in xorg.conf

reads:


Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/event9"
EndSection

I've rebooted my computer and still no luck.

Any ideas?

---

### Post by rmjb on 2006-08-21
> **n00blar said:**
> Great HOWTO, but some reason it worked on my **Logitech MX500** for a bit and then it stopped working after a couple of reboots, and now I can't figure out what's wrong.
I've rebooted my computer and still no luck.

Any ideas?

Well, it looks like your mouse is mapping to event 3 instead of 9 as it should according to the udev rule and of course your xorg.conf file is expecting your mouse on event9... maybe you can check the format, placement and permissions of your udev rule to see if it's set up properly??

- rmjb

---

### Post by detyabozhye on 2006-08-21
@Mr. Sinister: Your reciever is for both a keyboard and a mouse. A few pages back, someone mentioned what they used to get the udev rule to grab only the mouse part, so you might want to check that out as well.

@ijanos: hmm, not sure.

@rmjb: Thanks for helping out man! :)

---

### Post by rmjb on 2006-08-21
No probs, we're all a community, I just hope I don't give the users wrong advice some time.

- rmjb

---

### Post by n00blar on 2006-08-21
> **rmjb said:**
> Well, it looks like your mouse is mapping to event 3 instead of 9 as it should according to the udev rule and of course your xorg.conf file is expecting your mouse on event9... maybe you can check the format, placement and permissions of your udev rule to see if it's set up properly??

- rmjb

Hmm, sorry to sound so dumb, but you kinda lost me there. :confused: 

I've gone over the instructions and I really don't know what I'm missing.
All the files were created using sudo, so I'm assuming they have the right permissions.

I've changed the 19-local.rules to read input/event3 and I also changed my xorg.conf to /dev/input/event3 and still no luck.

It worked fine until I rebooted my system, so I don't really know what changed.

Thanks for the help though.

---

### Post by eternalsword on 2006-08-22
I have a g7 and I was trying to bind the left/right wheel clicks to go through Firefox tabs, but when I restarted X, the mouse didn't work at all. when I removed the entries from the xbindkeysrc and rebooted, the mouse worked fine.  I haven't done anything with udev.  Here's my info

cat /proc/bus/input/devices

```

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=413c Product=2003 Version=0301
N: Name="Dell Dell USB Keyboard"
P: Phys=usb-0000:00:1d.3-1/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1
B: EV=120003
B: KEY=10000 7 ff87207a c14057ff febeffdf ffefffff ffffffff fffffffeB: LED=7

I: Bus=0003 Vendor=046d Product=c51a Version=4100
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.3-2/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event2 ts0
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0003 Vendor=046d Product=c51a Version=4100
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.3-2/input1
S: Sysfs=/class/input/input3
H: Handlers=kbd event3
B: EV=f
B: KEY=c0002 400 0 0 1 f80 78000 6039fa d84157ad 8e0000 0 0 0
B: REL=40
B: ABS=1 0

```

xorg.conf

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Dev Name"      "Logitech USB Receiver"
        Option          "Dev Phys"      "usb-0000:00:1d.3-2/input0"
        Option          "Device"        "/dev/input/event2"
        Option          "Buttons"       "8"
        Option          "ZAxisMapping"  "4 5 7 8"
EndSection

```

event3 didn't work at all had an infinite atomic loop or something like that, so I tried event2 and all of the buttons are being read by xev.  in xev, the left/right wheel click events are 6 and 7, so do I need to change my ZAxisMapping?

---

### Post by kiikkuja on 2006-08-22
Thank you for the HOWTO...now my Logitech desktop comfort mouse works even with the nautilus!!!!

---

### Post by spamathon on 2006-08-22
Hey guys, firstly thanks for the great guide.  Secondly, here's my config for anyone wanting the same setup:
```
"/usr/bin/xvkbd -xsendevent -text "\[Control]\[Page_Down]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Control]\[Page_Up]""
  m:0x0 + b:7
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9
```
I'm using an **MX610** (righty) and I like to have the left and right tilt of the scroll wheel cycle left and right through my tabs in Fx.

Damn, what an arduous task.  Setting up evdev and xbindkeys was fine, but trying to find the text codes for xvkvd was a pain in the arse.  I couldn't find them listed anywhere...

In XP I bind the tilts to *Ctrl+Tab* and *Ctrl+Shift+Tab* as it has proven a little more reliable than *Ctrl+PgUp* and *Ctrl+PgDn*.  So naturally, I tried to copy that.  No dice.  xvkbd doesn't seem to like **\[Control]\[Shift]\[Tab]** or **\C\S\t** (from man pages) or any combination of those I could think of.

I ended up running xvkbd (once I figured out it was just a virtual keyboard) then trying to simulate what I wanted.  Turns out the *Ctrl+Shift+Tab* doesn't actually work properly in xvkbd (for me at least).  Firefox responds to the keypresses from my real keyboard fine; so I figure it must be a problem with xvkbd.  Hence, just settled for Ctrl+PgUp.

Works fine mostly, sometimes it moves two tabs with only one tilt (same prob both ways) - about one in every ten tilts.  Not sure if this is the mouse or evdev or xbindkeys or xvkbd or Firefox.  Too many links and not enough experience with Linux to figure it out.  Any help would be greatly appreciated. :)

---

### Post by detyabozhye on 2006-08-22
> **eternalsword said:**
> I have a g7 and I was trying to bind the left/right wheel clicks to go through Firefox tabs, but when I restarted X, the mouse didn't work at all. when I removed the entries from the xbindkeysrc and rebooted, the mouse worked fine.  I haven't done anything with udev.  Here's my info

cat /proc/bus/input/devices

```

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=413c Product=2003 Version=0301
N: Name="Dell Dell USB Keyboard"
P: Phys=usb-0000:00:1d.3-1/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1
B: EV=120003
B: KEY=10000 7 ff87207a c14057ff febeffdf ffefffff ffffffff fffffffeB: LED=7

I: Bus=0003 Vendor=046d Product=c51a Version=4100
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.3-2/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event2 ts0
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0003 Vendor=046d Product=c51a Version=4100
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.3-2/input1
S: Sysfs=/class/input/input3
H: Handlers=kbd event3
B: EV=f
B: KEY=c0002 400 0 0 1 f80 78000 6039fa d84157ad 8e0000 0 0 0
B: REL=40
B: ABS=1 0

```

xorg.conf

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Dev Name"      "Logitech USB Receiver"
        Option          "Dev Phys"      "usb-0000:00:1d.3-2/input0"
        Option          "Device"        "/dev/input/event2"
        Option          "Buttons"       "8"
        Option          "ZAxisMapping"  "4 5 7 8"
EndSection

```

event3 didn't work at all had an infinite atomic loop or something like that, so I tried event2 and all of the buttons are being read by xev.  in xev, the left/right wheel click events are 6 and 7, so do I need to change my ZAxisMapping?

xbindkeys settings would never make your X not want to start up. xbindkeys is only loaded after you log into your account. I think your problem is that the event number changed on reboot, I had the same problem and made the udev rule to overcome it. Since your reciever does both mouse and keyboard you will need to modify the udev rule to check things other than the name. There is a post about that a few pages back somewhere. My mouse is wired, so I can't really test that though.

---

### Post by detyabozhye on 2006-08-22
> **spamathon said:**
> Hey guys, firstly thanks for the great guide.  Secondly, here's my config for anyone wanting the same setup:
```
"/usr/bin/xvkbd -xsendevent -text "\[Control]\[Page_Down]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Control]\[Page_Up]""
  m:0x0 + b:7
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9
```
I'm using an **MX610** (righty) and I like to have the left and right tilt of the scroll wheel cycle left and right through my tabs in Fx.

Damn, what an arduous task.  Setting up evdev and xbindkeys was fine, but trying to find the text codes for xvkvd was a pain in the arse.  I couldn't find them listed anywhere...

In XP I bind the tilts to *Ctrl+Tab* and *Ctrl+Shift+Tab* as it has proven a little more reliable than *Ctrl+PgUp* and *Ctrl+PgDn*.  So naturally, I tried to copy that.  No dice.  xvkbd doesn't seem to like **\[Control]\[Shift]\[Tab]** or **\C\S\t** (from man pages) or any combination of those I could think of.

I ended up running xvkbd (once I figured out it was just a virtual keyboard) then trying to simulate what I wanted.  Turns out the *Ctrl+Shift+Tab* doesn't actually work properly in xvkbd (for me at least).  Firefox responds to the keypresses from my real keyboard fine; so I figure it must be a problem with xvkbd.  Hence, just settled for Ctrl+PgUp.

Works fine mostly, sometimes it moves two tabs with only one tilt (same prob both ways) - about one in every ten tilts.  Not sure if this is the mouse or evdev or xbindkeys or xvkbd or Firefox.  Too many links and not enough experience with Linux to figure it out.  Any help would be greatly appreciated. :)

The tilt wheel sends a repeated signal until you let go of it. I don't know how you would go about disabling that. Maybe lomoco might do that, but I kinda doubt it.

---

### Post by sneekie on 2006-08-22
I'm have an ibm thinkpad.  My mouse works fine now, however, I no longer can use the touchpoint or touchpad.  Anyone else experiencing this problem?

---

### Post by detyabozhye on 2006-08-22
Can you give me your cat /proc/bus/input/devices?

---

### Post by sneekie on 2006-08-23
I: Bus=0011 Vendor=0001 Product=0001 Version=ab54
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=4 2000000 3802078 fb40f001 72ffffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=000a Version=0000
N: Name="TPPS/2 IBM TrackPoint"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event2 ts0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=046d Product=c01e Version=2200
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse1 event3 ts1
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0011 Vendor=1014 Product=5450 Version=0001
N: Name="/usr/sbin/thinkpad-keys"
P: Phys=
S: Sysfs=/class/input/input4
H: Handlers=kbd event4
B: EV=3
B: KEY=3 1 20000000 100000 e0000 0 0 0

---

### Post by detyabozhye on 2006-08-23
OK, try this in xorg.conf (remember to backup):

In Section "ServerLayout", replace:

```
InputDevice "Configured Mouse"
```

with:

```
InputDevice "Configured Mouse"
InputDevice "Logitech Mouse"
```

Add a section like this:

```
Section "InputDevice"
       Identifier     "Configured Mouse"
       Driver         "mouse"
       Option         "CorePointer"
       Option         "Device" "/dev/input/mouse0" #note the device option
       Option         "ZAxisMapping" "4 5"
EndSection
```

Then change these lines in your Logitech mouse section:

```
        Identifier "Configured Mouse"
        Driver "evdev"
        Option "CorePointer"
```

to:

```
        Identifier "Logitech Mouse"
        Driver "evdev"
        Option "SendCoreEvents" "True"
```

(The Driver "evdev" part doesn't change, but it just happens to be right in between the lines that do need to be changed.)

---

### Post by sneekie on 2006-08-23
THANKS! works perfectly!  Does the corepointer option say that its the main mouse pointer?  Just wanted to learn what it was that I changed.

---

### Post by detyabozhye on 2006-08-23
You're welcome! ^_^ Yes, that's exactly what CorePointer means.

---

### Post by nanocosm on 2006-08-23
For Logitech V500 mouse you can use this .xconfigrc:

I remapped the Left/Right scroll to Cursorkeys Left/Right
This scrolls to Left/Right e.g. in Firefox instead of PageBack/PageForward

To autoload xbindkeys at startup go to
System -> Preferences -> Sessions -> "Startup Programs" Tab -> Add -> and type xbindkeys

> ###########################
# xbindkeys configuration #
###########################
#
# Version: 0.1.3
#
# If you edit this, do not forget to uncomment any lines that you change.
# The pound(#) symbol may be used anywhere for comments.
#
# A list of keys is in /usr/include/X11/keysym.h and in
# /usr/include/X11/keysymdef.h 
# The XK_ is not needed. 
#
# List of modifier (on my keyboard): 
#   Control, Shift, Mod1 (Alt), Mod2 (NumLock), 
#   Mod3 (CapsLock), Mod4, Mod5 (Scroll). 
#
# Another way to specifie a key is to use 'xev' and set the 
# keycode with c:nnn or the modifier with m:nnn where nnn is 
# the keycode or the state returned by xev 
#
# This file is created by xbindkey_config 
# The structure is : 
# # Remark 
# "command" 
# m:xxx + c:xxx 
# Shift+... 




#keystate_numlock = enable
#keystate_scrolllock = enable
#keystate_capslock = enable


#ScrollLeft-ButtonPress - Ignore this event!
""
   m:0x0 + b:7   (mouse)

#ScrollLeft-ButtonRelease
#Just send CursorKey Left
"/usr/bin/xvkbd -xsendevent -text "\[Left]""
   m:0x0 + b:11   (mouse)



#ScrollRight-ButtonPress - Ignore this event!
""
   m:0x0 + b:6   (mouse)
#ScrollRight-ButtonRelease
#Just send CursorKey Right
"/usr/bin/xvkbd -xsendevent -text "\[Right]""
   m:0x0 + b:12   (mouse)

#
# End of xbindkeys configuration


---

### Post by MilesTEG1 on 2006-08-23
Nobody has a G5 mouse here ?
If yes, do you have all buttons functional ?
Can you give the scipt you use ?

---

### Post by Tom Brokaw on 2006-08-23
> **detyabozhye said:**
> Um, I think someone had trouble with using it with a KVM when he would switch then switch back. AFAIK, that should be fixed in Edgy.

I got it to work fine with my KVM.  The only thing different was that it detects as "ImExPS/2 Generic Explorer Mouse", so the rule you make has to reflect that instead of the Logitech USB or whatever.  Again, thanks for the How-to.

---

### Post by detyabozhye on 2006-08-23
> **MilesTEG1 said:**
> Nobody has a G5 mouse here ?
If yes, do you have all buttons functional ?
Can you give the scipt you use ?

Well, do Section 1, then give me your xev output for the side button and other special buttons, and I'll tell you how to set up your .xbindkeysrc.

---

### Post by MilesTEG1 on 2006-08-24
> **detyabozhye said:**
> Well, do Section 1, then give me your xev output for the side button and other special buttons, and I'll tell you how to set up your .xbindkeysrc.

Hello,
I follow this instructions : **[Logitech G5 setpoint - enable all buttons]("http://ubuntuforums.org/showpost.php?p=1413357&postcount=17")**
> **shiver said:**
> Sure. You need to use the evdev driver to make them all work. Apparently the xorg-evdev package included in dapper is/was broken. I don't know if it still is, I installed an old version as instructed in the howto I used. I can't remember where it was so I uploaded the copy I kept.

[Right-click - Save As...]("http://www.cs.helsinki.fi/u/aaltoset/xserver-xorg-input-evdev_1.0.0.5-0ubuntu2_i386.deb")

It's a 32-bit package, though, you'll have to try something else if you have a 64-bit install.


When you have the driver installed, you need a device name for your mouse. Since you have the same mouse I believe it's the same as mine, but to be sure, type 
```
cat /proc/bus/input/devices
``` 
The output is something like this:

I: Bus=0003 Vendor=046d Product=c041 Version=4600
N: Name="**Logitech USB Gaming Mouse**"
P: Phys=usb-0000:00:11.2-2/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

The bolded part is what you need. Now, create a new udev rule for your mouse with
```
sudo nano /etc/udev/rules.d/10-mouse.rules
``` The filename above is just an example that should work.
Put this in the file:
```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Gaming Mouse", NAME="input/g5"
``` Note the name. It must be the same the /proc output gives you. The NAME with caps is the device name you give to the mouse. You can make up your own or use the one in my example.

Then insert this to /etc/X11/xorg.conf, note the device name if you used something else than in the example before. It's also a good idea to backup the file in case something goes wrong.

```
Section "InputDevice"
        Identifier  "Logitech G5"
        Driver      "evdev"
        Option      "CorePointer"
        Option      "Device" "/dev/input/g5"
EndSection
``` 
Comment out your old mouse settings (so that everything from Section to EndSection has a # in front of it). Then find the Section named ServerLayout. Remove the reference to the old mouse settings and add the new ones, so it's something like this:

```

Section "ServerLayout"
        (other lines...) 
        InputDevice    "Logitech G5" "CorePointer"
EndSection
``` 
After that, you should have all the buttons recognized, including tilting the wheel horizontally. You need to restart something to make the new udev rule to apply. I don't know what exactly so for the sake of simplicity, reboot.

X should start, if it doesn't, then revert to your backup xorg.conf and try to find out what went wrong. Now you can configure the buttons. All the guides I have read say you have to use xkbdkeys or whatever it was to map keys to get for example back/forward working in firefox but I've never needed it. 

After rebooting, my G5 mouse works great.
In firefox I have the left/right middle button function.
But the side button don't work. The resolution buttons don't allow me more resolution like in windows...

Here you have the xev output :
Whell Up -> button 4
Whell Down -> button 5
Whell Left -> button 6
Whell Right -> button 7
Left Clic -> button 1
Middle Clic -> button 2
Right Clic -> button 3
Side button -> button 8

But the 2 others buttons (for changing resolution) don't allow me to have more than 3 resolutions...

For the Whell left & right, can it be possible to have this function in nautilus and other program ?
How can I set it to only few programs ?

Ps : I don't use the following instructions, because with it i loose the autoscroll capabilities in firefox...
> I just used xmodmap so that the thumb button pastes highlighted text and opens links in new tabs in firefox, tilting the wheel horizontally is back/fwd in firefox and horizontal scroll in other apps.
To get this, type ```
xmodmap -e "pointer = 1 3 8 4 5 6 7 2 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32"
``` If you want a different configuration, try rearranging the first 8 numbers and see what which button does (I have never really been able to understand the logic in it, I just use trial and error. Maybe I'm just too dumb.)

You might want to add that command to run on startup. Chances are you are using Gnome, which I can't use that much. On KDE you can do it with an autostart config file:

```
nano ~/.kde/Autostart/mouse.desktop
``` 
Add this:

```

[Desktop Entry]
Encoding=UTF-8
Exec=xmodmap -e "pointer = **insertyourbuttonmappingshere**"
GenericName[en_US]=
StartupNotify=false
Terminal=false
TerminalOptions=
Type=Application
X-KDE-autostart-after=kdesktop"

```

Thanks
++
Miles

---

### Post by detyabozhye on 2006-08-24
To get Firefox to use the tilt wheel for horizontal scroll (the standard behavior for the tilt wheel) you need to set mousewheel.horizscroll.withnokey.action to 0 in Firefox in about:config

To make the side button go back (standard behavior for side button) do:
```
sudo apt-get install xvkbd xbindkeys
gedit ~/.xbindkeysrc
```
In there paste:
```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[_L_eft]""
  m:0x0 + b:8
```

To have different behavior in different apps, you might have to use imwheel.

---

### Post by pt123 on 2006-08-25
I have the Logitech MX 510  mouse on the PS/2 connector on my computer than using a USB connection would this guide still work for my setup?

---

### Post by detyabozhye on 2006-08-26
Evdev only works on USB.

---

### Post by adam.tropics on 2006-08-27
This is so weird, all was working, but i had an older version of evdev, so i upgraded, silly me! Still ok, except the left and right tilt have started to work back to front (right to left), and the button numbers, according to xev have changed. Added to that, changing the numbers in the xbindkeysrc has no effect at all! Any ideas?

---

### Post by rlreich on 2006-08-27
I setup everything they way it was written but when I rebooted I got a xserver fail. Now I can't get Ubu to start except in command line. Any idea what I did wrong or how to fix it?](*,)

---

### Post by mdwuznik on 2006-08-27
Do any of you know sth about the way the new hyped-up Revolution from Logitech would work under linux?

---

### Post by jadugarr on 2006-08-27
Thanks for the guide, worked great for my mx510.  It let me finally lift the hold on upgrading the evdev package (previously downgraded to Breezy version).  I think the whole reason the dapper version wasn't working for me was that I had my device named /dev/input/mx510 instead of event*.

---

### Post by spookshow on 2006-08-27
> **rlreich said:**
> I setup everything they way it was written but when I rebooted I got a xserver fail. Now I can't get Ubu to start except in command line. Any idea what I did wrong or how to fix it?](*,)


you might have done what i did, and changed the identifier in the "InputDevice" section, and not changing it to the same name as the identifier in the  "ServerLayout" section, silly me. i had x constantly not load for me until i figured that out this morning


questions about xbindkeys
i want my tilt left and tilt right to be page up and page down, as well as my back button to be, well, back.. what would i put in xbindkeysrc for that? (did some looking around, found a few things, but nothing seems to be working properly)
i have a logitech g7 mouse, and have use xev to find all the buttons (which, for some reason isn't actually showing my left and right tilt when i click em over.. any ideas?)

---

### Post by detyabozhye on 2006-08-27
> **adam.tropics said:**
> This is so weird, all was working, but i had an older version of evdev, so i upgraded, silly me! Still ok, except the left and right tilt have started to work back to front (right to left), and the button numbers, according to xev have changed. Added to that, changing the numbers in the xbindkeysrc has no effect at all! Any ideas?

Do you have xmodmap set up (do you have a ~/.Xmodmap file)?
If you do, try without it. If you still have problems, post your xev output here without xmodmap.

---

### Post by detyabozhye on 2006-08-27
> **rlreich said:**
> I setup everything they way it was written but when I rebooted I got a xserver fail. Now I can't get Ubu to start except in command line. Any idea what I did wrong or how to fix it?](*,)

Well, the description is pretty vague here, but the problem is most likely in either the udev rule or in the xorg.conf file.

---

### Post by detyabozhye on 2006-08-27
> **mdwuznik said:**
> Do any of you know sth about the way the new hyped-up Revolution from Logitech would work under linux?

Dunno, we'll need some time to get all the stuff working in it.

---

### Post by mdwuznik on 2006-08-28
Sure, anyone who owns one/got one for testing ?

---

### Post by adam.tropics on 2006-08-28
> **detyabozhye said:**
> Do you have xmodmap set up (do you have a ~/.Xmodmap file)?
If you do, try without it. If you still have problems, post your xev output here without xmodmap.

No, I'm not using xmodmap, but I just tried it, and confused the hell out of myself....been staring at this way too long!

Anyway xev says left and right tilt is 7 and 6 respectively, and so I put that in .Xbindkeysrc and still sideways scroll is back to front! I am wondering if I need a setting in xorg other than that on the howto, but have no idea. Maybe I will stare at this fresh tomorrow!

---

### Post by detyabozhye on 2006-08-28
> **adam.tropics said:**
> No, I'm not using xmodmap, but I just tried it, and confused the hell out of myself....been staring at this way too long!

Anyway xev says left and right tilt is 7 and 6 respectively, and so I put that in .Xbindkeysrc and still sideways scroll is back to front! I am wondering if I need a setting in xorg other than that on the howto, but have no idea. Maybe I will stare at this fresh tomorrow!

That is correct, you need to set a setting in firefox to make it stop going back and forward when you use the tilt wheel and set up the back button to go back in .xbindkeysrc (most likely button 8 ).

---

### Post by MilesTEG1 on 2006-08-29
> **MilesTEG1 said:**
> Hello,
I follow this instructions : **[Logitech G5 setpoint - enable all buttons]("http://ubuntuforums.org/showpost.php?p=1413357&postcount=17")**
except this : > Now you can configure the buttons. All the guides I have read say you have to use xkbdkeys or whatever it was to map keys to get for example back/forward working in firefox but I've never needed it. I just used xmodmap so that the thumb button pastes highlighted text and opens links in new tabs in firefox, tilting the wheel horizontally is back/fwd in firefox and horizontal scroll in other apps.
To get this, type ```
xmodmap -e "pointer = 1 3 8 4 5 6 7 2 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32"
``` If you want a different configuration, try rearranging the first 8 numbers and see what which button does (I have never really been able to understand the logic in it, I just use trial and error. Maybe I'm just too dumb.)

You might want to add that command to run on startup. Chances are you are using Gnome, which I can't use that much. On KDE you can do it with an autostart config file:

```
nano ~/.kde/Autostart/mouse.desktop
``` 
Add this:

```

[Desktop Entry]
Encoding=UTF-8
Exec=xmodmap -e "pointer = **insertyourbuttonmappingshere**"
GenericName[en_US]=
StartupNotify=false
Terminal=false
TerminalOptions=
Type=Application
X-KDE-autostart-after=kdesktop"

```

The instructions you see just before, I don't use it. So I don't have used the xmodmap command because with it i loose the autoscroll capabilities in firefox... (like in windows when you push the middle button and let it pushed, you will get a transpartent circle with little arrows up and right with a black point in center.)

After rebooting, my G5 mouse works great.
In firefox I have the left/right middle button function.
But the side button don't work. The resolution buttons don't allow me more resolution like in windows...

Here you have the xev output :
[B] Whell Up -> button 4
Whell Down -> button 5
Whell Left -> button 6
Whell Right -> button 7
Left Clic -> button 1
Middle Clic -> button 2
Right Clic -> button 3
Side button -> button 8[/B]

But the 2 others buttons (for changing resolution) don't allow me to have more than 3 resolutions...

For the Whell left & right, [B]can it be possible to have this function in nautilus and other program ?

[/B]** How can I set it to only few programs ?**
[/quote]


Thanks
++
Miles

---

### Post by cokhavim on 2006-08-29
> **adam.tropics said:**
> No, I'm not using xmodmap, but I just tried it, and confused the hell out of myself....been staring at this way too long!

Anyway xev says left and right tilt is 7 and 6 respectively, and so I put that in .Xbindkeysrc and still sideways scroll is back to front! I am wondering if I need a setting in xorg other than that on the howto, but have no idea. Maybe I will stare at this fresh tomorrow!

hey, i had this problem too, and i found an answer!  i just looked at the man pages for evdev and found the option to map the correct buttons to the correct axis.  so, here's the relevant section of my xorg.conf:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/event9" 
        Option          "HWHEELRelativeAxisButtons"     "7 6"
EndSection
```

happy mousing!

---

### Post by rlreich on 2006-08-29
This thread has gotten so long I'm not sure what I'm reading part of the time. I did everything at the beginning of this thread as far as changing the conf files and got a xserver crash when I rebooted. When I tried to rename the xorg.conf file i got the following error

E: Could not lock file /var/lib/apt/lists/lock-open
(Permission denied)
E: Unable to lock the list directory

This was after I had signed in with the root account and password. Any idea how to work around this? I've tried going back to previous updates as well.

---

### Post by detyabozhye on 2006-08-30
> **MilesTEG1 said:**
> The instructions you see just before, I don't use it. So I don't have used the xmodmap command because with it i loose the autoscroll capabilities in firefox... (like in windows when you push the middle button and let it pushed, you will get a transpartent circle with little arrows up and right with a black point in center.)

After rebooting, my G5 mouse works great.
In firefox I have the left/right middle button function.
But the side button don't work. The resolution buttons don't allow me more resolution like in windows...

Here you have the xev output :
[B] Whell Up -> button 4
Whell Down -> button 5
Whell Left -> button 6
Whell Right -> button 7
Left Clic -> button 1
Middle Clic -> button 2
Right Clic -> button 3
Side button -> button 8[/B]

But the 2 others buttons (for changing resolution) don't allow me to have more than 3 resolutions...

For the Whell left & right, [B]can it be possible to have this function in nautilus and other program ?

[/B]** How can I set it to only few programs ?**


Thanks
++
Miles

You would have to use imwheel to set it to only a few programs. Try searching the forums for imwheel. I personally didn't have much luck with it so I can't tell you how to make it all work properly.

---

### Post by detyabozhye on 2006-08-30
> **rlreich said:**
> This thread has gotten so long I'm not sure what I'm reading part of the time. I did everything at the beginning of this thread as far as changing the conf files and got a xserver crash when I rebooted. When I tried to rename the xorg.conf file i got the following error

E: Could not lock file /var/lib/apt/lists/lock-open
(Permission denied)
E: Unable to lock the list directory

This was after I had signed in with the root account and password. Any idea how to work around this? I've tried going back to previous updates as well.

O_O Wow, that's weird. Try starting up in recovery mode ([on the grub screen](http://yekubuntu.free.fr/warty/images/grub.png)).

---

### Post by rlreich on 2006-08-31
I tried that also. Never could get it to work.

---

### Post by BLTicklemonster on 2006-09-01
Using an MX310, this guide worked great. Way easier than the one I used before. I just came back to ubuntu after a long haitus, and let me tell you, it's the same as before. Every single thing I try to do, be it load video drivers, or get my mouse working, every thing I try messes up ubuntu. No matter that I diligently follow the instructions to a T. I noticed before that even following my own notes on how to do things would never work the same way twice. This guide, however, worked right off the bat. 

Thank you very much!!!

---

### Post by detyabozhye on 2006-09-02
You're welcome. ^_^

---

### Post by BLTicklemonster on 2006-09-04
Yer welcome. 

(my hard drive I'd loaded ubuntu on started clicking, so I had to install alllllll over again. And yep, your guide worked again!)

---

### Post by detyabozhye on 2006-09-04
> **BLTicklemonster said:**
> Yer welcome. 

(my hard drive I'd loaded ubuntu on started clicking, so I had to install alllllll over again. And yep, your guide worked again!)

hehe, my little Western Digital 7.5GB testing HD on which I had Edgy installed started clicking and died before yesterday as well.

---

### Post by msak007 on 2006-09-05
Thanks for this how-to, now I can use the forward / back buttons on my MX700 in Konqueror too :). I have a couple suggestions though. I haven't read the whole thread (just the first post which is all I needed) so I apologize if any of this has been suggested or mentioned before (I assume any modifications would be in the first post), but do you really need to restart the machine? You can issue a ```
sudo /etc/init.d/udev restart
``` to restart udev and detect new rulesets / hardware, and then just start xbindkeys manually for the current session. Also you may want to put in there for the KDE folks to get xbindkeys to start automatically, you can do the following:

1. Create a startup script
```
kedit ~/.kde/Autostart/start-xbindkeys
``` 2. Insert this into it
```
#!/bin/sh
xbindkeys
``` 3. Make it executable
```
chmod +x start-xbindkeys
``` 
Once again thanks for this easy to follow how-to, my buttons all work now.

EDIT: I almost forgot, for my MX700 I'm using the USB --> PS/2 adapter that came with it, so the output of ```
cat /proc/bus/input/devices
``` for me was "PS2++ Logitech MX Mouse" instead of "Logitech USB Receiver".

---

### Post by gannina on 2006-09-05
I'm using a Logitech mouse that has a scroll wheel that can also scroll left and right. I ran xev and it came up with buttons 11, and 12. I setup my local-19 file exactly like the one in your guide and my forward and back buttons work, but I'm not sure how to get the scrollwheel to go side to side.

---

### Post by KhaaL on 2006-09-05
for some reason, the local-rules file made my sound die. I entered exactly:

KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB-PS/2 Optical Mouse", NAME="input/event9"

where the last "input/event9" was adjusted as pointed out in the guide. What made me wonder, however, should the first KERNEL=="event[0-9]*" be changed too, or left as it is?

---

### Post by detyabozhye on 2006-09-05
> **gannina said:**
> I'm using a Logitech mouse that has a scroll wheel that can also scroll left and right. I ran xev and it came up with buttons 11, and 12. I setup my local-19 file exactly like the one in your guide and my forward and back buttons work, but I'm not sure how to get the scrollwheel to go side to side.

The scroll left and right should generate buttons 6 and 7 in xev. You would need to set up xmodmap to get it working I believe. Try this:

```
gedit ~/.Xmodmap
```

Paste this in there:
```
pointer = 1 2 3 4 5 8 9 10 11 6 7 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32
```

save and close
```
xmodmap ~/.Xmodmap
```

If if complains about too many buttons, delete some off the end untill you have the right amount. Then try xev.

---

### Post by detyabozhye on 2006-09-05
> **Khalid Rashid said:**
> for some reason, the local-rules file made my sound die. I entered exactly:

KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB-PS/2 Optical Mouse", NAME="input/event9"

where the last "input/event9" was adjusted as pointed out in the guide. What made me wonder, however, should the first KERNEL=="event[0-9]*" be changed too, or left as it is?

Hmm, that's weird. Do you still get a sound device in /proc/bus/input/devices?

---

### Post by detyabozhye on 2006-09-05
> **msak007 said:**
> Thanks for this how-to, now I can use the forward / back buttons on my MX700 in Konqueror too :). I have a couple suggestions though. I haven't read the whole thread (just the first post which is all I needed) so I apologize if any of this has been suggested or mentioned before (I assume any modifications would be in the first post), but do you really need to restart the machine? You can issue a ```
sudo /etc/init.d/udev restart
``` to restart udev and detect new rulesets / hardware, 

Didn't know that, haven't tried it. I'll try it next time I need to set up something like this.

> **msak007 said:**
> and then just start xbindkeys manually for the current session. Also you may want to put in there for the KDE folks to get xbindkeys to start automatically, you can do the following:

1. Create a startup script
```
kedit ~/.kde/Autostart/start-xbindkeys
``` 2. Insert this into it
```
#!/bin/sh
xbindkeys
``` 3. Make it executable
```
chmod +x start-xbindkeys
``` 
Once again thanks for this easy to follow how-to, my buttons all work now.

You're welcome. I'll add it.

---

### Post by bartman on 2006-09-06
Hi!
Thanks for the guide, my MX510 now works much better with FireFox. I, however, had a problem. I use a laptop so the mouse isn't plugged in all the time and if it isn't, Xorg hangs at startup.

I wrote a little script which verifies if /dev/input/event8 exists and copies a correct xorg.conf in its place. But I didn't know where to put it. So I went to the #ubuntu IRC channel where a helpful fellow suggested using the update-rc.d command. After reading through the man page it was a breeze:
```
$ sudo cp logitech-mice.sh /etc/init.d/logitech-mice.sh
$ sudo update-rc.d logitech-mice.sh start 69 S .
```
First I needed to move my script into a folder update-rc.d scans when adding a daemon/service. That folder is /etc/init.d.

Then I actually configured my script to run at the startup (S) runlevel with priority number 69. The number is essential because my X server has the priority number of 70 and I need th script to run before the X server starts.

Here's the script:
```
# logitech-mice.sh      Script to set appropriate xorg.conf regarding mouse presence
#
#/bin/bash
if [ -e /dev/input/event8 ] && [ -e /etc/X11/xorg.conf-logitech ]
then
        rm /etc/X11/xorg.conf
        cp /etc/X11/xorg.conf-logitech /etc/X11/xorg.conf
        echo " * Logitech MX510 mouse found!"
fi
if [ ! -e /dev/input/event8 ] && [ -e /etc/X11/xorg.conf-backup ]
then
        rm /etc/X11/xorg.conf
        cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
        echo " * Logitech MX510 mouse NOT found!"
fi
exit
```

Of course if you want the same, you need to change event8 to whichever eventX you configured. I also have 2 backuped xorg.confs:
- xorg.conf-backup which is a backup I made before tweaking it
- xorg.conf-logitech which contains configuration for my Logitech mouse.

Now if only somehow i could run this script whenever the udev rule run as well. I found this file:
```
$ cat /etc/udev/rules.d/030_sl-modem-daemon.rules
 # start/stop the daemon when the USB modem is connected
KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
```
I tried adding ```
RUN+="/etc/init.d/logitech-mice.sh"
```to the udev rule I created for my mouse but it doesn't work.

Any ideas?

---

### Post by detyabozhye on 2006-09-06
Take a look at this page: [http://ubuntuforums.org/showthread.php?t=219894&page=16](http://ubuntuforums.org/showthread.php?t=219894&page=16)

---

### Post by bartman on 2006-09-07
LOL, what a simple solution.

Thanks.

---

### Post by KhaaL on 2006-09-07
> **detyabozhye said:**
> Hmm, that's weird. Do you still get a sound device in /proc/bus/input/devices?

I got the guide working, i followed it again. and I got one thing to say about lomoco: WOW! I thing even typing feels more accurate now :p

One question though, when I goto system -> Preferences -> Mouse -> Motion tab, The acceleration and sensitivity values don't affect my mouse... know how to fix this, or how I can change these values manually (that is, by fiddling with a file?)

---

### Post by detyabozhye on 2006-09-07
Don't know, mouse settings always worked for me in both Gnome and Xfce.

---

### Post by kendals on 2006-09-13
I just *cannot* get my mouse to work. It's a Logitech G7 (USB), and I've followed your guide to the dot.

I've added the rule, installed evdev thingie, replaced the default xorg.conf mouse section with your one- everything! Yet the mouse still won't budge- tried restarting, and no luck. Batteries are fine- it worked before I reinstalled Ubuntu, but I just don't know how to fix it...

Here's my cat /proc/bus/input/devices list:

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

I: Bus=0003 Vendor=046d Product=c50e Version=2510
N: Name="Logitech USB RECEIVER"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="PS/2 Mouse"
P: Phys=isa0060/serio4/input1
S: Sysfs=/class/input/input2
H: Handlers=mouse1 event2 ts1
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse2 event3 ts2
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

```

My ls /dev/input/:

```
event0  event2  event3  event9  mice  mouse0  mouse1  mouse2  ts0  ts1  ts2
```

Finally, my rules stuff:

```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB RECEIVER", NAME="input/event9"
```

So yeah- it all appears right using your guide, yet the mouse is not moving, and batteries are fine (tried shifing USB position, resetting mouse, etc. to no avail) :(

---

### Post by BLTicklemonster on 2006-09-13
Do I have to do this all over again for kde?

---

### Post by kendals on 2006-09-13
*bump!*

---

### Post by BLTicklemonster on 2006-09-13
> **kendals said:**
> 

```


I: Bus=0003 Vendor=046d Product=c50e Version=2510
N: Name="Logitech USB RECEIVER"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="PS/2 Mouse"
P: Phys=isa0060/serio4/input1
S: Sysfs=/class/input/input2
H: Handlers=mouse1 event2 ts1
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3



```

My ls /dev/input/:

```
event0  event2  event3  event9  mice  mouse0  mouse1  mouse2  ts0  ts1  ts2
```

Finally, my rules stuff:

```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB RECEIVER", NAME="input/event9"
```

So yeah- it all appears right using your guide, yet the mouse is not moving, and batteries are fine (tried shifing USB position, resetting mouse, etc. to no avail) :(

Isn't receiver ... are you using a wireless mouse? receiver wouldn't be the mouse. I think you need to use the ps2 part not the usb receiver part.

Just for the heck of it, try something like this:

```
KERNEL=="event[0-9]*", SYSFS{../name}=="PS/2 Mouse", NAME="input/event9"
```

And if it works, be utterly amazed, because I'm out of my league here.

Now; my mx310's buttons don't work in kde. what to do?

---

### Post by detyabozhye on 2006-09-13
> **BLTicklemonster said:**
> Do I have to do this all over again for kde?

No, you would only need to add xbindkeys to your autostarted applications in KDE.

---

### Post by detyabozhye on 2006-09-13
@kendals:
Can I get you cat /etc/X11/xorg.conf

---

### Post by BLTicklemonster on 2006-09-13
... which I just did, and it works fine. THEN I came along and checked my email and saw your reply. Sorry I wasn't wearing my thinking cap last night. Thanks for all this neat info!

---

### Post by kendals on 2006-09-14
> **detyabozhye said:**
> @kendals:
Can I get you cat /etc/X11/xorg.conf

Never mind- turns out that for no reason, the USB receiver for my LX7 Logitech stopped receiving data from the mouse, so I got it replaced (only 7 months old, phew! Within the 12 months which saved sending to Logitech)... :)

Guide worked perfectly after that :)

---

### Post by KhaaL on 2006-09-14
I don't know if this is caused by the edev/lomoco stuff, but my wacom board is now completly unusable. I'm running edgy eft knot-2, so it MIGHT be something to do with that... any wacom users experiencing the same thing?

---

### Post by detyabozhye on 2006-09-14
From the top of my head, I think it's probably something to do with xorg.conf. You'll probably need to do something there to get the wacom working.

---

### Post by someusernoob on 2006-09-15
Seriously, configuring my new MX 400 mouse with your tutorial was easier then installing the Logitech drivers under Windows (i ended up once with a BSOD)*. 

I only needed the forward and back button to work, side scrolling is annoying anyway. But it worked, it worked great :D thank you very much.

[SIZE="1"]*this was a conlict between my chipset drivers, my nvidia drivers and setpoint... before someone thinks im trolling or flaiming[/SIZE]

---

### Post by Zieher on 2006-09-15
Hi,

first off, great HowTo. I appreciate the work done by the community, it was a reason for me to switch OS

(XP Home wouldn't let the BT-stack be started as SYSTEM, and Logicrap's software would only work correctly when logged on as admin - and for a multiuser desktop that is a waste of resource and a danger to system health)

I have a MX900 via its original BT-cradle, it works fine on the "mouse" driver, although it has one problem with the cruise control buttons: scroll up gives buttonpress b:6 and then the consecutive buttonpresses b:4 to scroll and a b:6 release after releasing cruise control button. I have tried to get it to work with evdev, but it doesn't seem to work correctly (followed your guide on page 1).

The BT-cradle is in HCI mode, because I want to sync my phone with Evolution (but that is an entirely different story). So it is not just a wireless extension of the USB Receiver.

Since I only need fwd and bck function in firefox (which I get w/o keybinding) I would be happy the way it is, except for the double function on my cruise control button.

cat:

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

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c705 Version=2704
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:03.0-2.1/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event2 ts0
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0005 Vendor=046d Product=b001 Version=2201
N: Name="Logitech Bluetooth Mouse"
P: Phys=00:07:61:16:2D:CF
S: Sysfs=/class/input/input3
H: Handlers=mouse1 event3 ts1
B: EV=f
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103
B: ABS=300 0

```

all I need to know, is if evdev will fix the double function on my mouse, or if I ought to give up and forget the cruise control:roll:

---

### Post by detyabozhye on 2006-09-16
It should, I got cruise control buttons working fine using evdev while the "mouse" driver made the cruise up (I think) also do another button.

---

### Post by infinityPlusOne on 2006-09-18
Thank you!  This works great with my MX 700.  I can scroll and use my forward/back keys when browsing.  I am a happy camper.

Cheers,

infinityPlusOne

---

### Post by detyabozhye on 2006-09-18
d_o_ itashi mashi te (you're welcome.) ^_^

---

### Post by Zieher on 2006-09-30
Hmmm, for some reason I can't get evdev to control the mouse. I set up udev rules as in first page. Either I write the rule to include "Logitech USB Receiver" and nothing happens (though movement of mouse will wake up system) or I include "Logitech Bluetooth Mouse" and X crashes on startup. xorg.conf is also setup by instructions on 1st page.

Can't post the codes (.conf, udev rule) right now because I'm currently on another machine. I'll do this in a while.

Funnily enough, "mouse" works fine with my MX900 except for the "cruise up". Momentarily I can live with the "flaw".

Does anybody know if this setup has its problems with bluetooth mice, or it's just my ineptness?

---

### Post by BLTicklemonster on 2006-09-30
Each time I have tried doing my mouse lately (been busy trying edgy, but I finally have dapper back right now), I get some kind of wacom or something in my input devices. I get stuck out of x because this appears out of the blue each time I try to get the mouse settings right. I removed the lines from xorg.conf, but still could not get into x, then I noticed:

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"

The stylus, cursor, and eraser are each part and parcel of the wacom or whatever it was. I #-ed them and now I can boot. 

Thing is, what the heck?

Also, it sure would be nice if you could take an entire section you don't want, and just 

/*
comment
the
whole
thing
out
like
this
instead
of
#
at
the
head
of
each
line
or
ctrl-k
to
remove
a
line
at
a
time
*/

But /* is not recognized, so you have to # each line. Shame.

So I guess I try to remember the name of that wacom or whatever it is and remove from synaptic, maybe? Why did it show up? I have a tablet, but it's not hooked up.

---

### Post by detyabozhye on 2006-09-30
> **Zieher said:**
> Hmmm, for some reason I can't get evdev to control the mouse. I set up udev rules as in first page. Either I write the rule to include "Logitech USB Receiver" and nothing happens (though movement of mouse will wake up system) or I include "Logitech Bluetooth Mouse" and X crashes on startup. xorg.conf is also setup by instructions on 1st page.

Can't post the codes (.conf, udev rule) right now because I'm currently on another machine. I'll do this in a while.

Funnily enough, "mouse" works fine with my MX900 except for the "cruise up". Momentarily I can live with the "flaw".

Does anybody know if this setup has its problems with bluetooth mice, or it's just my ineptness?

Yeah, get me the /proc/bus/input/devices, udev rule, and xorg.conf so I can see what's wrong.

Your mouse is wireless, correct? And the reciever can be for keyboard as well?

---

### Post by detyabozhye on 2006-09-30
> **BLTicklemonster said:**
> Each time I have tried doing my mouse lately (been busy trying edgy, but I finally have dapper back right now), I get some kind of wacom or something in my input devices. I get stuck out of x because this appears out of the blue each time I try to get the mouse settings right. I removed the lines from xorg.conf, but still could not get into x, then I noticed:

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"

The stylus, cursor, and eraser are each part and parcel of the wacom or whatever it was. I #-ed them and now I can boot. 

Thing is, what the heck?

Also, it sure would be nice if you could take an entire section you don't want, and just 

/*
comment
the
whole
thing
out
like
this
instead
of
#
at
the
head
of
each
line
or
ctrl-k
to
remove
a
line
at
a
time
*/

But /* is not recognized, so you have to # each line. Shame.

So I guess I try to remember the name of that wacom or whatever it is and remove from synaptic, maybe? Why did it show up? I have a tablet, but it's not hooked up.

I got the wacom thing in Edgy as well. It should be fine to just delete all the wacom, stylus, eraser stuff from xorg.conf. Are you saying it keeps coming back though?

---

### Post by spockrock on 2006-09-30
has anyone gotten an mx700 mouse to work in edgy?
creating a udev rule just causes x to crash, and without the rule my buttons are all messed up when using xev.

```

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "evdev"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/input/event9"
EndSection

```

---

### Post by detyabozhye on 2006-09-30
In Edgy Eft, I got it to work without the udev rule using the Name Option in xorg.conf, I haven't tried it in Dapper though, so I'm not going to edit the tutorial yet:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"Logitech USB-PS/2 Optical Mouse"
EndSection
```

---

### Post by BLTicklemonster on 2006-09-30
It only comes back if I have to dpkg reconfigure because of a video driver problem (which I was having when I tried edgy on a fresh install. I gave up and came back after a while. I'll let them smooth it out a bit more), or if I did dpkg reconfigure phigh.

But why does it come up? Quite odd.

---

### Post by spockrock on 2006-09-30
detyabozhye tried that no dice.....

---

### Post by bjorkiii on 2006-10-01
:) Just like to say thanks for the information i have finally have back and forward buttons on mx1000.

---

### Post by bjorkiii on 2006-10-01
](*,) I keep right clicking and clicking back , i keep forgetting the side buttons work.

---

### Post by detyabozhye on 2006-10-01
> **spockrock said:**
> detyabozhye tried that no dice.....

Give me the output for these commands:

cat /proc/bus/input/devices
cat /etc/X11/xorg.conf
cat /etc/udev/rules.d/19-local.rules

---

### Post by BLTicklemonster on 2006-10-01
Just reported this wacom thing as a bug:

Bug #63445

---

### Post by Zieher on 2006-10-01
re: your [answer]("http://www.ubuntuforums.org/showpost.php?p=1563820&postcount=213")

Here goes (sorry, had to help a firend touch up his flat)


cat proc...
```
I: Bus=0003 Vendor=046d Product=c705 Version=2704
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:03.0-2.1/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event2 ts0
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0005 Vendor=046d Product=b001 Version=2201
N: Name="Logitech Bluetooth Mouse"
P: Phys=00:07:61:16:2D:CF
S: Sysfs=/class/input/input7
H: Handlers=mouse1 event3 ts1
B: EV=f
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103
B: ABS=300 0

```

xorg.conf
```
Section "InputDevice"
	Identifier	"Logitech MX900"
        Driver          "evdev"
        Option          "Device"                "/dev/input/event9"
	Option		"CorePointer"
	Option		"SendCoreEvents"	"true"
        Option          "Resolution"    "800"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Logitech MX900" "CorePointer"
EndSection
```

19-local.rule
```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech Bluetooth Mouse", NAME="input/event9"
```

edit: um, yeah, the MX900 is a dual mode (HID or HCI) bluetooth mouse. I have it running in HCI mode, since I need true bt capability of the mouse cradle to sync my mobile (cellular for transatlants). again, it's not acute, it's just my hang to get it working as originally advised... 

thanks for your listening, it's refreshing to know you're not alone =)

side note (why I'm here in ubuntuworld):
lol, it is actually a logitech product, where neither the original OS (WinXP) nor the actual driver and utils kept their promise - it all only worked when logged in as admin. log on as restricted borked the mouse, plus Win would start a bt stack for EVERY user logged in at the time... what do these people get paid for?!?!

---

### Post by spockrock on 2006-10-02
> **detyabozhye said:**
> Give me the output for these commands:

cat /proc/bus/input/devices
cat /etc/X11/xorg.conf
cat /etc/udev/rules.d/19-local.rules

cat /proc/bus/input/devices
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

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c50b Version=2100
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-1/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c50b Version=2100
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-1/input1
S: Sysfs=/class/input/input3
H: Handlers=kbd mouse0 event3 ts0 
B: EV=7
B: KEY=ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff 0 0 1878 d800d100 1e0000 0 0 0
B: REL=103

```

xorg.conf
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Sep 14 15:50:24 PDT 2006

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" #"CorePointer"
    InputDevice    "Mouse0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    #Option	   "AIGLX" "true"
EndSection

Section "Files"
    FontPath        "/usr/share/X11/fonts/misc/"
    FontPath        "/usr/share/X11/fonts/TTF/"
    FontPath        "/usr/share/X11/fonts/OTF"
    FontPath        "/usr/share/X11/fonts/Type1/"
    FontPath        "/usr/share/X11/fonts/CID/"
    FontPath        "/usr/share/X11/fonts/100dpi/"
    FontPath        "/usr/share/X11/fonts/75dpi/"
EndSection

Section "Module"
    Load	   "i2c" #added
    Load	   "bitmap" #added
    Load           "extmod"
    Load           "dbe"  #commented out
#	Load  "dri"
    Load           "glx"
    Load           "record" #commented out
    Load           "xtrap" #commented out
    Load           "freetype" #commented out
    Load           "type1" #commented out
EndSection

##xorg mouse
#Section "InputDevice"
#	Identifier  "Mouse0"
#	Driver      "mouse"
#	Option	    "Protocol" "auto"
#	Option	    "Device" "/dev/input/mice"
#	Option	    "ZAxisMapping" "4 5 6 7"
#EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "evdev"
    Option         "SendCoreEvents" "true"
#    Option	   "Name" "Logitech USB Receiver"
    Option         "Device" "/dev/input/event9"
#    Option	   "ButtonMapping" "1 2 3 4 5 6 7 8 9 10 11"
#    Option		"Dev Name"		"Logitech USB Receiver"
#   Option		"Buttons"		"10"
#   Option		"CorePointer"
#   Option		"Protocol"		"evdev"
#   Option		"Dev Phys"		"usb-*/input1"
#   Option		"ZAxisMapping"		"4 5"
#   Option		"Emulate3Buttons"	"true"
EndSection

Section "Monitor"

	#DisplaySize	  360   270	# mm
 ### Comment all HorizSync and VertSync values to use DDC:
    Identifier     "Monitor0"
    VendorName     "GSM"
    ModelName      "T910BU"
    HorizSync       30.0 - 98.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
    Identifier     "Card0"
    Driver         "nvidia"
    VendorName     "nVidia Corporation"
    BoardName      "GeForce 7800 GT"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Card0"
    Monitor        "Monitor0"
    DefaultDepth   24
    Option         "TwinView" "true"
    Option         "MetaModes" "1600x1200,1600x1200"
    Option         "TwinViewOrientation" "RightOf"
    Option         "SecondMonitorHorizSync" "50-75"
    Option         "SecondMonitorVertRefresh" "60-80"
    Option         "RenderAccel" "true"
    Option         "NoLogo" "True"
    Option         "Coolbits" "1"
    Option 	   "AddARGBGLXVisuals" "True"
    Option	   "TripleBuffer" "true"
    SubSection     "Display"
        Viewport    0 0
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       4
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       8
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       15
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       16
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       24
    EndSubSection
EndSection

```

19-local.rules
```

KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", NAME="input/event4"

```

Ok I do know that in rules I tell it event 4, and in xorg I am looking at event 9.  The problem is that when If I change it so they they are both either event 9 or event 4 then X fails to load.  I have tried a bazillion combinations, and I dunno why in edgy this fails, but in dapper it worked perfectly.

---

### Post by detyabozhye on 2006-10-02
> **Zieher said:**
> re: your [answer]("http://www.ubuntuforums.org/showpost.php?p=1563820&postcount=213")

Here goes (sorry, had to help a firend touch up his flat)


cat proc...
```
I: Bus=0003 Vendor=046d Product=c705 Version=2704
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:03.0-2.1/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event2 ts0
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0005 Vendor=046d Product=b001 Version=2201
N: Name="Logitech Bluetooth Mouse"
P: Phys=00:07:61:16:2D:CF
S: Sysfs=/class/input/input7
H: Handlers=mouse1 event3 ts1
B: EV=f
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103
B: ABS=300 0

```

xorg.conf
```
Section "InputDevice"
	Identifier	"Logitech MX900"
        Driver          "evdev"
        Option          "Device"                "/dev/input/event9"
	Option		"CorePointer"
	Option		"SendCoreEvents"	"true"
        Option          "Resolution"    "800"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Logitech MX900" "CorePointer"
EndSection
```

19-local.rule
```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech Bluetooth Mouse", NAME="input/event9"
```

edit: um, yeah, the MX900 is a dual mode (HID or HCI) bluetooth mouse. I have it running in HCI mode, since I need true bt capability of the mouse cradle to sync my mobile (cellular for transatlants). again, it's not acute, it's just my hang to get it working as originally advised... 

thanks for your listening, it's refreshing to know you're not alone =)

side note (why I'm here in ubuntuworld):
lol, it is actually a logitech product, where neither the original OS (WinXP) nor the actual driver and utils kept their promise - it all only worked when logged in as admin. log on as restricted borked the mouse, plus Win would start a bt stack for EVERY user logged in at the time... what do these people get paid for?!?!

Well, the first thing that I noticed is this:

```
	Option		"CorePointer"
	Option		"SendCoreEvents"	"true"
```

You should have only one or the other, not both for one device AFAIK. Try it with only	Option		"CorePointer". If that doesn't work, try using "Logitech USB Receiver" in the udev rule again.

---

### Post by detyabozhye on 2006-10-02
> **spockrock said:**
> cat /proc/bus/input/devices
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

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c50b Version=2100
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-1/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c50b Version=2100
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-1/input1
S: Sysfs=/class/input/input3
H: Handlers=kbd mouse0 event3 ts0 
B: EV=7
B: KEY=ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff 0 0 1878 d800d100 1e0000 0 0 0
B: REL=103

```

xorg.conf
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Sep 14 15:50:24 PDT 2006

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" #"CorePointer"
    InputDevice    "Mouse0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    #Option	   "AIGLX" "true"
EndSection

Section "Files"
    FontPath        "/usr/share/X11/fonts/misc/"
    FontPath        "/usr/share/X11/fonts/TTF/"
    FontPath        "/usr/share/X11/fonts/OTF"
    FontPath        "/usr/share/X11/fonts/Type1/"
    FontPath        "/usr/share/X11/fonts/CID/"
    FontPath        "/usr/share/X11/fonts/100dpi/"
    FontPath        "/usr/share/X11/fonts/75dpi/"
EndSection

Section "Module"
    Load	   "i2c" #added
    Load	   "bitmap" #added
    Load           "extmod"
    Load           "dbe"  #commented out
#	Load  "dri"
    Load           "glx"
    Load           "record" #commented out
    Load           "xtrap" #commented out
    Load           "freetype" #commented out
    Load           "type1" #commented out
EndSection

##xorg mouse
#Section "InputDevice"
#	Identifier  "Mouse0"
#	Driver      "mouse"
#	Option	    "Protocol" "auto"
#	Option	    "Device" "/dev/input/mice"
#	Option	    "ZAxisMapping" "4 5 6 7"
#EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "evdev"
    Option         "SendCoreEvents" "true"
#    Option	   "Name" "Logitech USB Receiver"
    Option         "Device" "/dev/input/event9"
#    Option	   "ButtonMapping" "1 2 3 4 5 6 7 8 9 10 11"
#    Option		"Dev Name"		"Logitech USB Receiver"
#   Option		"Buttons"		"10"
#   Option		"CorePointer"
#   Option		"Protocol"		"evdev"
#   Option		"Dev Phys"		"usb-*/input1"
#   Option		"ZAxisMapping"		"4 5"
#   Option		"Emulate3Buttons"	"true"
EndSection

Section "Monitor"

	#DisplaySize	  360   270	# mm
 ### Comment all HorizSync and VertSync values to use DDC:
    Identifier     "Monitor0"
    VendorName     "GSM"
    ModelName      "T910BU"
    HorizSync       30.0 - 98.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
    Identifier     "Card0"
    Driver         "nvidia"
    VendorName     "nVidia Corporation"
    BoardName      "GeForce 7800 GT"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Card0"
    Monitor        "Monitor0"
    DefaultDepth   24
    Option         "TwinView" "true"
    Option         "MetaModes" "1600x1200,1600x1200"
    Option         "TwinViewOrientation" "RightOf"
    Option         "SecondMonitorHorizSync" "50-75"
    Option         "SecondMonitorVertRefresh" "60-80"
    Option         "RenderAccel" "true"
    Option         "NoLogo" "True"
    Option         "Coolbits" "1"
    Option 	   "AddARGBGLXVisuals" "True"
    Option	   "TripleBuffer" "true"
    SubSection     "Display"
        Viewport    0 0
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       4
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       8
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       15
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       16
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       24
    EndSubSection
EndSection

```

19-local.rules
```

KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", NAME="input/event4"

```

Ok I do know that in rules I tell it event 4, and in xorg I am looking at event 9.  The problem is that when If I change it so they they are both either event 9 or event 4 then X fails to load.  I have tried a bazillion combinations, and I dunno why in edgy this fails, but in dapper it worked perfectly.

OK, I think your problem is that you have two devices that register as "Logitech USB Reciever", the reciever works for both keyboard and mouse. You're going to have to get udev or xorg.conf to get only the mouse part. The problem is that I don't remember how to do that. It should be somewhere in this thread though. BTW, when changing the udev rule, run sudo /etc/init.d/udev restart.

---

### Post by spockrock on 2006-10-03
ok I have tried, but I am at the same point, my up cruise button shows up as button 4 and button 8, button 8 being one of my side buttons.  I am frazzled, grated I am in edgy, so I will just sit patiently and try to figure this, out, btw your guide worked perfectly in dapper.  I am starting to wonder maybe the evdev driver in edgy maybe not working correctly. who knows......oh well.

---

### Post by detyabozhye on 2006-10-03
Dunno, Edgy got it right with this on first try for me:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"Logitech USB-PS/2 Optical Mouse"
EndSection
```

---

### Post by spockrock on 2006-10-03
> **detyabozhye said:**
> Dunno, Edgy got it right with this on first try for me:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"Logitech USB-PS/2 Optical Mouse"
EndSection
```

ok and you did this with a udev rule??

---

### Post by detyabozhye on 2006-10-03
Nope, no udev.

---

### Post by spockrock on 2006-10-03
OMG OMG OMG OMG I LOVE YOU MORE THEN YOU COULD EVER IMAGINE....it was the udev, I will post my xorg shortly so no one else has to rack thier brain on it.

ok fixed the keyboard remap issue.  w00t thank you detyabozhye so much!!!

---

### Post by spockrock on 2006-10-03
Ok here is my edgy configuration for the mxduo.
ok no udev rule, just edit your xorg.conf

```

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "evdev"
    Option         "SendCoreEvents" "True"
    Option	   "Name" "Logitech USB Receiver"
    Option         "Device" "/dev/input/event3"
EndSection

```

the event number is the event number taken from cat /proc/bus/input/devices, same with the name I will highlight,with bold, the  parts you need to watch.  I found that you have to have the Device option otherwise your wireless keyboard will map your keys all weird.  Keyboard layout is above that pretty standard.  Also not that in serverlayout make sure you mouse isn't A CorePointer.  Delete or comment it out.

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

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c50b Version=2100
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-1/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c50b Version=2100
N: **Name="Logitech USB Receiver"**
P: Phys=usb-0000:00:02.0-1/input1
S: Sysfs=/class/input/input3
H: Handlers=kbd mouse0 **event3** ts0 
B: EV=7
B: KEY=ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff 0 0 1878 d800d100 1e0000 0 0 0
B: REL=103

```

---

### Post by detyabozhye on 2006-10-04
The event number might chang however (not sure about Edgy, does in Dapper), it might be safer to use the "Phys" or "Dev Phys" option instead of the "Device" option though if it doesn't change the event number it should be fine.

---

### Post by John.Michael.Kane on 2006-10-04
@kendals before the modifications of this guide did your LX7 work out the gate with dapper?

---

### Post by spockrock on 2006-10-04
> **detyabozhye said:**
> The event number might chang however (not sure about Edgy, does in Dapper), it might be safer to use the "Phys" or "Dev Phys" option instead of the "Device" option though if it doesn't change the event number it should be fine.

ok I will keep that in mind, I have rebooted several times, and I ams still ok, but thanks for the headsup.

---

### Post by Zieher on 2006-10-04
Ok, I don't know what's wrong. I've managed to get the mouse to work with evdev, with evdev without udev, and it still works with mouse. but under all situations I stll get two buttonpresses for cruise up (namely cruise up and page back) ](*,) 
I think I'll have to get used to the thought of letting it be.

---

### Post by John.Michael.Kane on 2006-10-04
Zieher which logitech mouse are you using? I was planning on getting an LX7.

---

### Post by Zieher on 2006-10-04
MX900 Bluetooth mouse w/ original bt cradle

---

### Post by detyabozhye on 2006-10-04
> **Zieher said:**
> Ok, I don't know what's wrong. I've managed to get the mouse to work with evdev, with evdev without udev, and it still works with mouse. but under all situations I stll get two buttonpresses for cruise up (namely cruise up and page back) ](*,) 
I think I'll have to get used to the thought of letting it be.

hmm, weird. Maybe file a bug?

---

### Post by John.Michael.Kane on 2006-10-04
detyabozhye you know if this guide works with LX7 wireless logictec mice

---

### Post by detyabozhye on 2006-10-04
It should, but I don't know for sure.

---

### Post by binatice on 2006-10-09
I got Ubuntu loaded and running on my laptop with realative ease. Every thing but my USB Mouse is work good I am using a [Logitech Notebook Mouse]("http://www.logitech.com/index.cfm/products/details/US/EN,CRID=3,CONTENTID=8142") When I use the left or middle mouse buttons they seems to have the properties of both the middle and the left button combined. AKA when I highlight text with the left button and then click in a text box with the left button it acts as if I clicked the middle button, and visa-versa. In Firefox I click on a link with the left mouse button it opens the link in the current window and in an extra tab as if I clicked the middle button, again visa-versa.

I have played with this guide to no avail ](*,) if anyone else has anyother suggestions they will be most helpful. Also, if you think I need to get a new mouse altogether, please make a suggestion. Thanks to eveyone in advance.

---

### Post by detyabozhye on 2006-10-09
Same with "mouse" driver too? O_o Weird. I'm guessing it might be the mouse messing up, does it work with other computers/OS's?

---

### Post by binatice on 2006-10-10
I works fine on Windows XP. I really don't think it is the mouse it's self, but it might be. I bought the mouse about 3 months ago.

---

### Post by detyabozhye on 2006-10-10
So, you get the same problem with the "mouse" and the "evdev" driver, or only with evdev?

---

### Post by binatice on 2006-10-10
I don't quite understand the question, but I utilized the How to here and it displays the same problems as before. If that is what your asking.

---

### Post by detyabozhye on 2006-10-10
Well, before the guide you were most likely using the mouse driver. And it was bad then too, correct?

---

### Post by erdu on 2006-10-10
I'd love to use button 10 on my mx1000 to close a window. My global shortcut for closing windows is Alt + z. However, when I write 

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[z]""
  m:0x0 + b:10

in my .xbindkeysrc file, nothing happens, the window doesn't close.  If I write:

"/usr/bin/xvkbd -xsendevent -text "\[Control]\[w]""
  m:0x0 + b:10

some windows close, some don't. Those that close, do produce a beep from the computer speaker after closing though. Any idea how I could use b:10 to close any window? Thanks...

---

### Post by NoTiG on 2006-10-10
A couple of questions....... i got the evdev driver to load and everything. However....

i want to bind my thumb button my my mouse to acting as Control....... i know from using xev, that the button is button 8. in my configuration file i tried binding it like this: 

"/usr/bin/xvkbd -xsendevent -text "\[Control]""
  m:0x0 + b:8

And it doesnt seem to work....... how do i bind it to act like control? I tried binding it to ^... but it just prints that character... 

Secondly........ using xev, my mouse buttons 1-8 were detected (i didnt notice a 2) .... that includes scroll weel up down and tilt left and right. But...... the two buttons above the scrollwheel on my mouse did not send any signals to xev.....

---

### Post by detyabozhye on 2006-10-10
> **NoTiG said:**
> A couple of questions....... i got the evdev driver to load and everything. However....

i want to bind my thumb button my my mouse to acting as Control....... i know from using xev, that the button is button 8. in my configuration file i tried binding it like this: 

"/usr/bin/xvkbd -xsendevent -text "\[Control]""
  m:0x0 + b:8

And it doesnt seem to work....... how do i bind it to act like control? I tried binding it to ^... but it just prints that character... 

xvkbd will only do a kepress event, not a key down and keyup event. I don't know if it's possible to do a key down and key up using xbindkeys.

> **NoTiG said:**
> Secondly........ using xev, my mouse buttons 1-8 were detected (i didnt notice a 2) .... that includes scroll weel up down and tilt left and right. But...... the two buttons above the scrollwheel on my mouse did not send any signals to xev.....

2 is scroll-wheel click.

---

### Post by NoTiG on 2006-10-10
hmmmm. not sure if i understand. FOr example... to open a new tab in firefox is Control + t . to open the history is control + H .... etc...... i just want to use the thumb butotn as control then my left hand for those other keys....

when i press control i hold it down.... did you mean the opposite of what you said ?

---

### Post by NoTiG on 2006-10-11
here is the output from xev when i press the button: 

KeyPress event, serial 31, synthetic YES, window 0x4200001,
    root 0x186, subw 0x0, time 0, (1,1), root:(1,1),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

and here is the output when i press the actual control button

KeyPress event, serial 31, synthetic NO, window 0x4200001,
    root 0x186, subw 0x0, time 899081723, (127,167), root:(140,263),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

hmm. i wonder what synthetic refers to.

---

### Post by binatice on 2006-10-11
> **detyabozhye said:**
> Well, before the guide you were most likely using the mouse driver. And it was bad then too, correct?

Aye, both before and after the guide. The problem remains.

---

### Post by TigPT on 2006-10-11
not worket to my Logitech V400

can you help me? ther are something that need be difrent?

thks anyway.. think this is a good tutorial for logitech users!

---

### Post by detyabozhye on 2006-10-11
> **NoTiG said:**
> here is the output from xev when i press the button: 

KeyPress event, serial 31, synthetic YES, window 0x4200001,
    root 0x186, subw 0x0, time 0, (1,1), root:(1,1),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

and here is the output when i press the actual control button

KeyPress event, serial 31, synthetic NO, window 0x4200001,
    root 0x186, subw 0x0, time 899081723, (127,167), root:(140,263),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

hmm. i wonder what synthetic refers to.

If you press control and let go, then press "w", it won't close a window in Firefox, correct? You have to HOLD control and press "w" to close a window. When you map your mouse buttons to a keyboard key, when you press the button, it'll do keypress and release right away, it won't release when you release the button. The button sends the event on press, not on release.

---

### Post by detyabozhye on 2006-10-11
> **binatice said:**
> Aye, both before and after the guide. The problem remains.

hmm, might be a bug in the kernel. I guess report a bug.

---

### Post by detyabozhye on 2006-10-11
> **TigPT said:**
> not worket to my Logitech V400

can you help me? ther are something that need be difrent?

thks anyway.. think this is a good tutorial for logitech users!

Which part isn't working? I need to know where exactly you got stuck.

---

### Post by daou on 2006-10-14
I got all the buttons on my Logitech MX Revolution working. Followed the guide but needed a few tweaks in the xorg.conf file and in the udev rule.

EDIT: lomoco doesn't seem to support the MX Revo yet.

---

### Post by damaged on 2006-10-18
Phew! Finished.

Sections 1 and 2 worked perfectly for my MX700. Thanks a bunch. :) 

I only had one little bit of confusion over this part:

> Important: the eventX part should stay as eventX, where X is a number not taken already, the current evdev driver will not take anything but eventX.)

I was about to change this bit: 

```
KERNEL=="event[0-9]*"
```

but then realised that you must have meant to change this bit:

```
NAME="input/event9"
```

Anyway, maybe a bit of extra clarification there wouldn't go astray.

I also ran into problems in the "**Section 3: lomoco (Resolution, etc.) (Optional)**" part.

I ran into this problem:

```
dave@ubuntu:~$ sudo lomoco -8
001.003: 046d:c50b Unsupported Logitech device: USB Receiver

```

Does that mean that this section doesn't apply to MX700's and other infrared mice?

I have been having trouble with my mouse in terms of its control. It seems to have a bit of life of its own sometimes and is like walking a big dog which has other ideas about where the two of you are going. ;) 

Any help with this would be great.

---

### Post by msak007 on 2006-10-18
Has anybody tried this guide in Edgy to see if it still works? I'm thinking of upgrading my Desktop to Edgy when it comes out but want to make sure my mouse still works.

---

### Post by sjust on 2006-10-19
I have done this guide in Edgy and it works for the most part. I am running xgl-beryl and that is what I set my mouse (mx510) up in. Now when I log into Gnome all the buttons are screwed up. Also when I log into XGL I have to go to sys/pref/keyboard layouts change my keboard and change back, then kill xbindkeys and restart xbindkeys for the back and foward buttons to work in nautilus. If I just kill xbindkeys and restart with out choseing another keyboard and back it wont work. I am still trying to get all my multimedia keys working on my Logitech internet navigator keyboard. I have tried hotkeys and ketouch but they seem to interfer with xbindkeys so I got rid of them. any help with these problems would be appreciated.

---

### Post by detyabozhye on 2006-10-20
> **damaged said:**
> I ran into this problem:

```
dave@ubuntu:~$ sudo lomoco -8
001.003: 046d:c50b Unsupported Logitech device: USB Receiver

```

Does that mean that this section doesn't apply to MX700's and other infrared mice?

I have been having trouble with my mouse in terms of its control. It seems to have a bit of life of its own sometimes and is like walking a big dog which has other ideas about where the two of you are going. ;) 

Any help with this would be great.

Hmm, yeah, it's probably a lomoco problem. I dunno how you would go report a bug to them.

---

### Post by detyabozhye on 2006-10-20
> **msak007 said:**
> Has anybody tried this guide in Edgy to see if it still works? I'm thinking of upgrading my Desktop to Edgy when it comes out but want to make sure my mouse still works.

I got it working in Edgy without the udev rule using the "Name" Option in xorg.conf. This doesn't really work right with the USB recievers tho, it might need the Phys or Dev Phys Option too.

---

### Post by daou on 2006-10-21
detyabozhye,

I made a howto on how to configure the MX Revolution, specifically, for Ubuntu. It's mostly from your howto with the needed tweaks. I hope you don't mind. Credit is, of course, given for your work.

[HOWTO: Logitech MX Revolution in Dapper]("http://www.ubuntuforums.org/showthread.php?t=277388")

---

### Post by John.Michael.Kane on 2006-10-21
Has any one got an lx7 working through the use of this guide on Dapper or Edgy?

---

### Post by detyabozhye on 2006-10-23
> **daou said:**
> detyabozhye,

I made a howto on how to configure the MX Revolution, specifically, for Ubuntu. It's mostly from your howto with the needed tweaks. I hope you don't mind. Credit is, of course, given for your work.

[HOWTO: Logitech MX Revolution in Dapper]("http://www.ubuntuforums.org/showthread.php?t=277388")

It's all good. I'll have to read it sometime and maybe use some things for the Edgy guide.

---

### Post by dnite on 2006-10-24
I followed this guide (as well as many other things I've found online and am at a standstill and starting to believe the newest evdev driver might be broken. If anyone can help, that would be awesome. I have a Logitech MX900. I've tried with and without the udev to get it to work. If I use the 'mouse' driver in my xorg.conf, it works just fine. But as soon as I try and use the 'evdev' driver (using "Name" "Logitech Bluetooth Mouse" and not the device at all, all though I have tried the device many times and different ways).. Basically, X just doesn't start. Here's the end of my log file... ](*,) 

```

(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evdev brain: Rescanning devices (1).
(**) Option "CorePointer"
(**) Logitech MX900-00:07:61:09:32:FB: Core Pointer
(II) Logitech MX900-00:07:61:09:32:FB: Found 2 absolute axes.
(II) Logitech MX900-00:07:61:09:32:FB: Configuring as pointer.
(**) Logitech MX900-00:07:61:09:32:FB: Configuring in Absolute mode.
(**) Logitech MX900-00:07:61:09:32:FB: AbsoluteScreen: -1.

Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: /usr/lib/xorg/modules/input/evdev_drv.so [0xb736c67b]
3: /usr/lib/xorg/modules/input/evdev_drv.so [0xb736d6fd]
4: /usr/lib/xorg/modules/input/evdev_drv.so(evdevNewDriver+0x44) [0xb736d860]
5: /usr/lib/xorg/modules/input/evdev_drv.so [0xb736c3f1]
6: /usr/bin/X11/X(InitInput+0x16f) [0x809f21f]
7: /usr/bin/X11/X(main+0x355) [0x806e5e5]
8: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d938cc]
9: /usr/bin/X11/X(FontFileCompleteXLFD+0xa1) [0x806da51]

Fatal server error:
Caught signal 11.  Server aborting

```

I've tried a lot of different things, if anyone has any ideas or needs any other information from me, just let me know...

xorg.conf (device sections) Works using Configured Mouse, log file from using Logitech MX900
```

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice	"Logitech MX900"
EndSection

Section "InputDevice"
	Identifier		"Configured Mouse"
	Driver			"mouse"
	Option "Device"		"/dev/input/mice"
	Option "Protocol"	"ExplorerPS/2"
	Option "ZAxisMapping"	"4 5"
	Option "Emulate3Buttons" "true"
	Option "CorePointer"
EndSection

Section "InputDevice"
	Identifier		"Logitech MX900"
	Driver 			"evdev"
	Option "Name"		"Logitech Bluetooth Mouse"
	Option "CorePointer"
EndSection

```

cat /proc/bus/input/devices
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

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c705 Version=2704
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-2.1/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event2 ts0 
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0005 Vendor=046d Product=b001 Version=2200
N: Name="Logitech Bluetooth Mouse"
P: Phys=00:07:61:09:32:FB
S: Sysfs=/class/input/input5
H: Handlers=mouse1 event3 ts1 
B: EV=f
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103
B: ABS=300 0

```

Thanks again!

---

### Post by dnite on 2006-10-24
Forgot to mention... I'm using a fresh copy of Edgy I just installed last night using the Nightly Live CD ....

---

### Post by detyabozhye on 2006-10-24
Have you tried Logitech USB Receiver instead of Logitech Bluetooth Mouse?

---

### Post by nchase on 2006-10-27
I tried to get this working in Edgy with a Logitech 518 and I'm pretty sure I followed the instructions correctly. I had done it before in Dapper with success, but this time, it messed up X. Has anyone had success with a 510/518 in Edgy?

---

### Post by sweetthdevil on 2006-10-28
No i was trying as well to set my mx518 up on edgy with beryl but x won't start, talking about a /dev/wacom problem.

---

### Post by detyabozhye on 2006-10-28
> **nchase said:**
> I tried to get this working in Edgy with a Logitech 518 and I'm pretty sure I followed the instructions correctly. I had done it before in Dapper with success, but this time, it messed up X. Has anyone had success with a 510/518 in Edgy?

Try doing it this way:
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "evdev"
    Option         "CorePointer"
    Option         "Name" "Logitech USB-PS/2 Optical Mouse" #<- replace with your mouse's name from /proc/bus/input/devices
EndSection
```

---

### Post by sweetthdevil on 2006-10-28
Ok i don't understand?!

on the first page, you said to edit the xorg.conf to look like this:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/event9" #this should be that underlined name from 19-local.rules
EndSection
```

and now basicly you're telling me to edit the xorg.conf to look like this?
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name" "Logitech USB-PS/2 Optical Mouse"  
EndSection
```

Here is my cat /proc/bus/input/devices
```

I: Bus=0003 Vendor=046d Product=c01e Version=2200
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:1d.1-2/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event2 ts0 
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103
```

Tell me if i understood correctly? 

Thanks for your help.

---

### Post by sweetthdevil on 2006-10-28
Well i can answer! 

Yes that was it!

It work like a charm thanks so much! ;)

---

### Post by killkoy on 2006-10-29
for me the inistial howto works with edgy with an mx518

---

### Post by gemme on 2006-10-29
Tried to bind an "Alt-Escape" action (like Alt-Tab) to one of the keys.

Why does:
```
/usr/bin/xvkbd -xsendevent -window gnome-panel -text "\[Alt]\[Escape]"
```
work from the command line (or Alt-F2 window), but not invoked by xbindkeys? :(:(:(

---

### Post by detyabozhye on 2006-10-30
Escape might have a different key "name", but I'm not sure. Or there might be a problem with the command that xbinkeys runs.

---

### Post by hotpants on 2006-11-01
I finally got all the buttons on my MX610 working using detyabozhye's suggestion in [post #272]("http://ubuntuforums.org/showpost.php?p=1678716&postcount=272"), but I've got a problem with either X or evdev.

On a fresh reboot, X fails to start, but when I comment out the new section of xorg.conf:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"Logitech USB Receiver"
EndSection
```
...and *uncomment* out the old:
```
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"		"/dev/input/mice"
#	Option		"Protocol"		"ExplorerPS/2"
#	Option		"ZAxisMapping"		"4 5"
#	Option		"Emulate3Buttons"	"true"
#EndSection
```
...things boot fine, and then I can reverse the commenting, do a Ctrl+Alt+Backspace, and voila, X starts up like a champ and all my mouse buttons work again.

Here's my Xorg.0.log:
```
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evdev brain: Rescanning devices (1).
(**) Option "CorePointer"
(**) Configured Mouse-usb-0000:00:10.0-2/input1: Core Pointer
(II) Configured Mouse-usb-0000:00:10.0-2/input1: Found 1 absolute axes.
(II) Configured Mouse-usb-0000:00:10.0-2/input1: Configuring as pointer.
(**) Configured Mouse-usb-0000:00:10.0-2/input1: Configuring in Absolute mode.
(**) Configured Mouse-usb-0000:00:10.0-2/input1: AbsoluteScreen: -1.

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: /usr/lib/xorg/modules/input/evdev_drv.so [0xb7b7d67b]
3: /usr/lib/xorg/modules/input/evdev_drv.so [0xb7b7e6fd]
4: /usr/lib/xorg/modules/input/evdev_drv.so(evdevNewDriver+0x44) [0xb7b7e860]
5: /usr/lib/xorg/modules/input/evdev_drv.so [0xb7b7d3f1]
6: /usr/X11R6/bin/X(InitInput+0x16f) [0x809f21f]
7: /usr/X11R6/bin/X(main+0x355) [0x806e5e5]
8: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d158cc]
9: /usr/X11R6/bin/X(FontFileCompleteXLFD+0xa1) [0x806da51]

Fatal server error:
Caught signal 11.  Server aborting
```

Obviously, I'd like to be able to boot without performing this process every time.  Any suggestions?

---

### Post by detyabozhye on 2006-11-01
Try adding the "Phys" or "Dev Phys" Option to xorg.conf as well. Use the output from cat /pro/bus/input/devices to get the Phys for your mouse.

---

### Post by John.Michael.Kane on 2006-11-01
I'm still wondering if anyone got this to work on an LX7. I tried,and it did not workout.

---

### Post by hotpants on 2006-11-02
Thanks for the suggestion, detyabozhye.  That didn't work, but luckily something else did.  Turns out I had a bunch of Wacom "cursor," "stylus," and "eraser" entries in xorg.conf with the comments "Tablet PC ONLY."  I certainly don't have a tablet PC, let alone any Wacom devices.  Removing that stuff and using the evdev driver as before with the "Name" option worked like a charm!```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"Logitech USB Receiver"
EndSection
```

I'm using edgy, BTW.  Hopes this helps someone...don't know why Ubuntu thought I was using a tablet, but I'm sure glad to have all my buttons working.

---

### Post by detyabozhye on 2006-11-02
> I'm still wondering if anyone got this to work on an LX7. I tried,and it did not workout.

Dapper or Edgy? Wired or wireless mouse?

---

### Post by John.Michael.Kane on 2006-11-05
LX7 is wireless. Tried under dapper,and edgy.

---

### Post by detyabozhye on 2006-11-05
Hmm, wireless mice always give me a headache (Wireless Logitech mice usually have a device for mouse and keyboard under the same name). Somehow, I've helped some people set their's up, but I don't quite understand how to make them work myself yet.

Try it with both the Name and the Phys options. Try it first in xorg.conf, and if it doesn't work, try it with udev.

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"Logitech whatever it says"
	Option		"Phys"	"whateveritisinprocbusinputdevices" # or possibly Option "Dev Phys"
EndSection
```

The udev rule that uses the Phys option, I don't remember for sure.

---

### Post by Doik on 2006-11-07
hey detyabozhye, 
thanks for the great tutorial. just helped a complete linux newbie to get more comfortable in his new environment :) 
so long
Doik

---

### Post by BLTicklemonster on 2006-11-07
I've had to redo xorg.conf, and since then, the info was added back to it, yet x fails to load, and I have to edit back to standard mouse settings. I tried to redo this with 4 instead of 9 (if you catch my drift) and still, x fails to load.

(using edgy)

---

### Post by detyabozhye on 2006-11-07
4 whats? Remember, I don't use the udev rule in Edgy. I need to write a new tut for Edgy.

---

### Post by BLTicklemonster on 2006-11-07
```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB-PS/2 Optical Mouse", NAME="input/event9"
```

I tried event4 instead of 9. (I was at work and in a hurry when I wrote that, sorry)

Well, it worked great in edgy until I had a problem with my video driver. I think I'll try removing everything then rebooting, then starting over again, and see if that works.

---

### Post by detyabozhye on 2006-11-07
In Edgy I set it up a bit differently: [http://ubuntuforums.org/showpost.php?p=1678716&postcount=272](http://ubuntuforums.org/showpost.php?p=1678716&postcount=272)

---

### Post by rmjb on 2006-11-07
Hey detyabozhye, I used your guide again for edgy and it worked once I switched to using Name instead of Device. Thanks again for a great HOWTO. I was really missing my Forward and Back buttons. I didn't know I used them that much.

Anyhow, the click part of the HOWTO isn't working for me. I downloaded the sources, compiled and set up my keys but nothing. Is that part still applicable to edgy?

- rmjb

---

### Post by detyabozhye on 2006-11-08
You're welcome. ^_^

No, in Dapper, the click part was necessary to cancel out the "extra" buttons because they acted as button one in Firefox in Opera. In Edgy, the problem is gone.

---

### Post by BLTicklemonster on 2006-11-09
Bah.

```
I: Bus=0003 Vendor=046d Product=c01b Version=1800
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:02.0-1/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0 
B: EV=7
B: KEY=3f0000 0 0 0 0 0 0 0 0
B: REL=103

```


```
Section "InputDevice"
     Identifier    "Configured Mouse"
     Driver	    "evdev"
     Option	    "CorePointer"
     Option	    "Name" "Logitech USB-PS/2 Optical Mouse" 
EndSection
```


Still nothing.

---

### Post by Kelnoky on 2006-11-10
After upgrading to edgy my extra buttons on the side of my MX518 aren't working anymore, so I looked up if there were any differences between dapper and edgy for the evdev driver and changed my xorg.conf according to what I found here:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name" "Logitech USB-PS/2 Optical Mouse"  
EndSection
```

In addition to the tiny problem that the side buttons aren't working I also got the big problem that the middle mouse button (the wheel) and the right mouse button switched their functions. So I have to do a right click with my mouse wheel and vice versa...
Solutions? :(

---

### Post by detyabozhye on 2006-11-10
Xmodmap should solve the problem. We'll just need to play around with the configuration file (~/.Xmodmap) a bit to make it right.

Install Xmodmap via Synaptic (or whatever u choose), then do:

```
gedit ~/.Xmodmap
```

paste this in there and save it:

```
pointer = 1 3 2 4 5 8 9 6 7 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32
```

And run:

```
xmodmap ~/.Xmodmap
```

And tell me what happens.

---

### Post by BLTicklemonster on 2006-11-11
Well, it said it was only going to change the first 32 of 9 buttons, so I don't know what to do about the others... koff koff... 


:)

But I have my forward and back buttons now. Only thing is, right clicking doesn't work any more. Well, it does sort of. I have to highlight stuff then press ctrl+c to copy, then all I have to do is right click and it pastes automagically. Odd, but doable.

Thanks.

---

### Post by rmjb on 2006-11-11
Hello detyabozhye, earlier you said that edgy handled the cruise control buttons so we didn't have to. It was working before I switched to evdev in my xorg.conf, but even after removing the lines in my .xbindkeysrc that called the little click too, the buttons still dont' work.

Here's the relevant part of my xorg.xonf file:
```
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "evdev"
        Option      "CorePointer"
        Option      "Name" "B16_b_02 USB-PS/2 Optical Mouse"
EndSection
```

Is there anything else that needs to be added for the cruise control?

- rmjb

---

### Post by BLTicklemonster on 2006-11-11
I may have said doable, but I meant "it will do until such time as..."

How can I make meh buttons do as I please?

---

### Post by Kelnoky on 2006-11-11
@detyabozhye

I already have that exakt line in my .Xmodmap and "xmodmap ~/.Xmodmap" had no result. (only gave out "Warning: Only changing the first 32 of 10 buttons.")

---

### Post by BLTicklemonster on 2006-11-11
```
Section "InputDevice"
   # generated from default
   Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection
```

Here is my new xorg.conf.

Each button relates to a number, and running xev in terminal will show that. Now if I knew what number, in order, in this line

pointer = 1 2 3 6 7 8 9 4 5 (picked out arbitrarilly)

related to what function, I could edit this myself. But I think it's time to open a text editor, and start testing different settings and paste results...


*edit: 

for an MX310 MOUSE...

said results being:

```
settigs were:

pointer = 1 2 3 6 7 8 9 4 5


xev said:
1 left click button 1
2
3 right click button 3
4 back side button 4 
5 forward side button 5 
6
7
8 wheel up 6 
9 wheel down 7
(clarification: xev didn't actually say that... I listed one through nine, then clicked each button and listed it next to its respective space with notation as to what was happening)
therefore:

pointer = 1 2 3 4 5 8 9 6 7
```
 
Let me clarify that a little further...

My mouse has nine buttons, so I listed 1 through nine, then drew a picture of my mouse and used xev (run from terminal) to see which button was numbered to do what. My side buttons were scrolling, numbered 4 and 5, and I knew that I wanted the wheel to scroll, so I noticed that 6 and 7 were my scroll wheels, and hey, when I scrolled, I was going forward and back in web pages, so it was simply a matter of moving the numbers around to the right places. 

and now things are groovy

HOT DANG, I FIGURED SOMETHING OUT~!!

GOD I LOVE LINUX! TRY THIS IN WINDOWS~!!! no wait, I'd not have had this problem in windows... oh well, GOD I LOVE TINKERING!!!!


I hope this will help everyone who is having problems, and thank you detyabozhye for this whole thread!


*edit:
not sure why I worried, but I rebooted just to see what would happen, and no x failure this time, and all buttons are working.

---

### Post by Kelnoky on 2006-11-11
Woot!

So, after thinking a bit - my button 2 and 3 on my mouse are switched. Well, no wonder, the pointer line was:

pointer = 1 3 2 4 5 8 9 6 7 10

So I switched the 2 and the 3 and now its back to normal again. :)


Although my side thumb buttons are still deactivated...

---

### Post by BLTicklemonster on 2006-11-11
Just wondering... if you run xev, what button numbers do the side thumb buttons show? Can you manipulate the xmodmap pointer settings from there to get desired results? It would be nice to have a way to determine exactly what choices are available so we could map out all out buttons.

---

### Post by detyabozhye on 2006-11-11
I play around with the numbers to get it right as well. There isn't a fix all line in .Xmodmap for everyone. Different people get different results with different mice.

---

### Post by BLTicklemonster on 2006-11-12
So, it looks like someone could just install xmodmap and run it, then test the numbers instead of all the rest? Well, do the dpi thing, of course... ??

---

### Post by detyabozhye on 2006-11-13
DPI is optional, it benefits gamers more than anyone else, AFAIK. I haven't done the DPI in Edgy myself yet.

---

### Post by atery on 2006-11-13
Thanks for your excellent HOWTO. I did what you've writen and my Logitech wireless trackman works very well. However, I have to change my xorg.conf back to my default one and tolerate the inconvenience because:

1. I cannot bootup properly if I am not using my trackman (if it is not plugged in or I use another normal mouse). I cannot log into X. I think this is about the udev rule thing. 

2. When I log in with my trackman plugged in and functioned well, I cannot use my touchpad on my IBM T43 laptop. But I can use the touchpad when I use the default xorg.conf settings. And I double checked there is nothing else different except the mouse part, i.e. the touchpad part is exactly the same.

Any idea how to tackle these two problems? Thanks.

---

### Post by detyabozhye on 2006-11-14
It's somewhere in this thread, search the thread for SendCoreEvents.

---

### Post by gtom on 2006-11-18
Thanks for the guide. :)

I got the thumb button working on my Mouseman Dual Optical.

How do I get the wheel (middle) button to minimize the currently in focus window?

The middle button is button 2 and Alt+F9 will is the keyboard shortcut for minimizing.

---

### Post by aniskasa on 2006-11-19
Another thank you for this howto, got my MX600 thumb buttons working properly. 

How could I get the tilt mouse to scroll web pages horizontally, or map some other functionality there? I know I need to edit the xbindkeysrc, but what should I look from xev, and what should I put to xbindkeysrc?

Here is what xev gives me:

Tilt wheel left:

```
KeyPress event, serial 33, synthetic NO, window 0x3600002,
    root 0x124, subw 0x0, time 225638, (166,34), root:(625,812),
    state 0x0, keycode 78 (keysym 0xff14, Scroll_Lock), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x3600002,
    root 0x124, subw 0x0, time 225654, (166,34), root:(625,812),
    state 0x0, keycode 78 (keysym 0xff14, Scroll_Lock), same_screen YES,
    XLookupString gives 0 bytes:
```

Tilt wheel right:

```
KeyPress event, serial 33, synthetic NO, window 0x3600002,
    root 0x124, subw 0x0, time 332396, (173,26), root:(632,804),
    state 0x0, keycode 78 (keysym 0xff14, Scroll_Lock), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x3600002,
    root 0x124, subw 0x0, time 332404, (173,26), root:(632,804),
    state 0x0, keycode 78 (keysym 0xff14, Scroll_Lock), same_screen YES,
    XLookupString gives 0 bytes:
```

100% -button:

```
KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  36  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

ButtonPress event, serial 33, synthetic NO, window 0x3600002,
    root 0x124, subw 0x0, time 396634, (149,71), root:(608,849),
    state 0x0, button 10, same_screen YES

ButtonRelease event, serial 33, synthetic NO, window 0x3600002,
    root 0x124, subw 0x0, time 396802, (149,71), root:(608,849),
    state 0x0, button 10, same_screen YES
```

The zoom +/- -buttons give me nothing.

So the 100% -button is button 10, but the tilt wheel gives me no button numbers.

The tilt wheel scrolls fine left and right in OO Spreadsheet.

in xorg.conf I have:

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "evdev"
    Option         "CorePointer"
    Option         "Device" "/dev/input/event9"
EndSection
```

In .xbindkeysrc:

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9
```

And in /etc/udev/rules.d/19-local.rules:

```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", NAME="input/event9"
```

---

### Post by msak007 on 2006-11-19
Just wanted to give you an update and let you know that I was able to successfully use the guide in Edgy as well. Everything works great!

EDIT: Forgot to mention I'm using an MX700

---

### Post by John.Michael.Kane on 2006-11-19
detyabozhye just to let you know I was unable to use the guide for an LX7 in Dapper or Edgy.


Thanks though.

---

### Post by detyabozhye on 2006-11-19
@aniskasa: You have to edit these lines in about:config for Firefox:

mousewheel.horizscroll.withnokey.action - Set this to '1'
mousewheel.horizscroll.withnokey.numlines

@SD-Plissken: Hmm, could be an evdev bug (had a bug in Dapper). I dunno why it's not working.

---

### Post by aniskasa on 2006-11-20
> **detyabozhye said:**
> @aniskasa: You have to edit these lines in about:config for Firefox:

mousewheel.horizscroll.withnokey.action - Set this to '1'
mousewheel.horizscroll.withnokey.numlines

Ummm... 8-[ Where is that about:config?

Actually, for some reason the horizontal scroll works now.

But the other issue remains, how to enable the zoom +/- -buttons?

---

### Post by detyabozhye on 2006-11-20
about:config is what you would type in the Firefox address bar, no http:// or www or whatever, just about:config

As for the +/- buttons, I'm not really sure, you might be able to do something there with lomoco. AFAIK, the MX518 and a few others use those buttons to control the resolution of your mouse without telling anything to the computer by default.

One of these commands might change that:

sudo lomoco --sms
sudo lomoco --no-sms

---

### Post by techflat on 2006-11-21
Hi there.

This is a reply with two motifs:

1: Thanks for the tutorial. It worked for me.

2: It worked for me on a Viewsonic MW405.


Cheers.

PS: Im using Ubuntu 6.10.

(Well, in case you found this post and don't know what I'm talking about, [here]("http://ubuntuforums.org/showthread.php?t=219894") is the link to the original post)

---

### Post by kobewan on 2006-11-21
Hey, I just wanted to ask a quick question before trying this out myself. In Windows XP I use Setpoint with uberoptions, which is a really cool mod to add a lot of extra functionality to Setpoint. The things that I like the most about it is that it lets you configure separate keys for different applications. For example, in Firefox I use the clickwheel left/right to change tabs; when I open up a PDF though, the wheel gets remapped to quickly change the page. I was wondering if it's possible to do this under Ubuntu. I don't really mind if it's not automatic and I have to run a script or something, but having to alter the config file and restart the computer every time I want to change my application is a little tedious. Can you please tell me if it's possible, and how to do it? Thanks.

---

### Post by detyabozhye on 2006-11-22
It's possible with imwheel, but I had trouble with getting imwheel to start up automatically. You can search the forum for imwheel.

---

### Post by ~LoKe on 2006-11-22
I'm trying to configure the DPI +/- buttons on my MX518 to do cruise control, but for some reason I can't figure it out. Xev won't show any buttons when I use them in that window.  My buttons are as follows:

1 - Left Click
2 - Scroll Wheel Button
3 - Right Click
4 - ??
5 - ??
6 - ??
7 - ??
8 - Thumb Button Left
9 - Thumb Button Right

This mouse is supposed to have only 8 buttons.  I assume three of the buttons out of the four unidentified ones are DPI +, - and application switcher.  But again, vex reports nothing.  I tried just trying it, but assigning actions to 4-7 and 10-15 and they still did nothing.

Suggestions?

**EDIT:** Interestingly enough, the application switcher button also reports as button 1, and acts like it as well.

---

### Post by detyabozhye on 2006-11-23
4 and five are scroll up and scroll down. You might need to try some lomoco commands to get the DPI buttons to report something in xev.

---

### Post by gtom on 2006-11-24
> **gtom said:**
> How do I get the wheel (middle) button to minimize the currently in focus window?

The middle button is button 2 and Alt+F9 is the keyboard shortcut for minimizing.

Any ideas please guys?

---

### Post by detyabozhye on 2006-11-24
Well, the xbindkeys shortcut should work, if it doesn't, then you might need to look up a xvkbd manual:

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[F9]""
  m:0x0 + b:2
```

---

### Post by fantasyl on 2006-11-25
Hi to all!

I'm using edgy eft with cordless trackman optical, and was able to make it to work almost flawlessy with this great step-by-step tutorial!

I can map the buttons to any key and they all work....great!

Only problem I have is that I'd like to make mouse shortcut for ALT+F4 (close window) and double clic.
I already seen a script for the latter on xbindkeys site, but don't know how to get it to work, actually.

Regarding the Alt+F4 I tried in my xbindkeysrc file:

```

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\F4""
m:0x0 + b:2
"/usr/bin/xvkbd -no-jump-pointer -no-repeat -xsendevent -text "\[Alt_L]\[F4]""
m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[F4]""
m:0x0 + b:8

```

But none of this (and other attempts) works.

In xev I can see the keys are getting pressed (Alt_L and F4 are being pressed, FOR XEV), but when I press on any windows or in nautilus nothing happens.
I read the whole xvkbd manual but actually did not understand if it's technically possible to do so...

Any help appreciated!

---

### Post by xopher on 2006-11-25
Is xserver-xorg-input-evdev really needed?

Im just saying that I do not have it installed - still my mouse works (driver evdev). 

And this is all I got in xorg.conf:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "Device"        "/dev/input/event1"
EndSection
```

---

### Post by detyabozhye on 2006-11-25
well, it's usually installed by default, and I don't think it worked when I did try without it.

---

### Post by Xuestor on 2006-11-26
Hello, This guide was awesome, just have one question.

When you edit the xbindkeysrc file, for binding backward - forward in nautilus etc, How do I change these bindings into something else? I have figured out how to bind button 7 to the BackSpace key, but then I want the button 6 to work as a minimizer, to minimize the active window.

How do I do this?

Cheers
/Xuestor

---

### Post by detyabozhye on 2006-11-27
You'll need to make button 6 do an Alt+F* combo, which I haven't figured out myself yet. :P

---

### Post by kobewan on 2006-11-28
Hm, but couldn't you remap the minimize window action to another keyboard shortcut and then use that with xbind?

---

### Post by detyabozhye on 2006-11-28
Yeah, I think so.

---

### Post by JPMaximilian on 2006-11-29
Awesome Tutorial, works perfect with my mx310.

---

### Post by fantasyl on 2006-11-30
> **detyabozhye said:**
> You'll need to make button 6 do an Alt+F* combo, which I haven't figured out myself yet. :P

Maybe this has to do with X having higher privileges then the xvkbd process, or the security option in xvkbd?

If I assign ctrl-z to mouse, it works in the app as "undo".
If, keeping ctrl-z to mouse, I assign it to "close window", than it does not close the window, but continues to work (in the app supporting it) as "undo".  This happens because If I press on my keyboard ctrl-z the app close (and does not "undo"), as the key is reserved to the X system before the app starts.

Maybe the problem is xvkbd is not executing real emulation of modifier keys (security reason?)?

However, the syntax 

```

"/usr/bin/xvkbd -xsendevent -text "\[Alt]\[F4]""
  m:0x0 + b:8 

```

simply works, because If I press the mouse button in the gnome keyboard shortcut panel, while assigning some function, I see the ouput as pressing ALT+F4....but from then on the mouse button does not work (for doing the function specified) while the key combo works normally.

---

### Post by fantasyl on 2006-11-30
Checking the xvkbd pages I tried the xtest instead of the xsendevent, and it works!!!! :D 

That was the reason the modifiers ALT+Yourkey were not working!

With this

```

"/usr/bin/xvkbd -xtest -text "\[Alt]\[F4]""
  m:0x0 + b:8

```

Now I can close all my window with the 8th mouse button!!!

GREAT! :mrgreen: 

My first (very little!) contribution to this great forum :biggrin: :biggrin:

Next step is emulating the double click....it's been done before with success? solutions?

---

### Post by detyabozhye on 2006-11-30
Awesome man! As for double clicking, it might be possible with a few lines of C code. Check out and try modifying and compiling this package, might work: [http://bg.rifetech.com/click.tgz](http://bg.rifetech.com/click.tgz)

---

### Post by JPMaximilian on 2006-11-30
Actually I did experience a problem, I get an xserver error when I try to boot my computer without a usb mouse plugged in.  X the doesn't load.  Anyone experience this?

---

### Post by detyabozhye on 2006-11-30
Use Option "SendCoreEvents" "True" insdead of Option "CorePointer"

---

### Post by iTh on 2006-11-30
I'm using kubuntu edgy with a logitech mx518 mouse.
The side buttons scroll to the left and right instead of going back and forward in konqueror.

cat /proc/bus/input/devices:
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

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="PS/2 Mouse"
P: Phys=isa0060/serio1/input1
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event2 ts0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse1 event3 ts1
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

I: Bus=0003 Vendor=046d Product=c01e Version=2200
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:1d.2-1/input0
S: Sysfs=/class/input/input4
H: Handlers=mouse2 event4 ts2
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0003 Vendor=06a3 Product=8000 Version=0120
N: Name="Chicony USB Gaming Keyboard Pro"
P: Phys=usb-0000:00:1d.3-1/input0
S: Sysfs=/class/input/input5
H: Handlers=kbd event5
B: EV=120003
B: KEY=10000 7 ff87207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: LED=7

I: Bus=0003 Vendor=06a3 Product=8000 Version=0120
N: Name="Chicony USB Gaming Keyboard Pro"
P: Phys=usb-0000:00:1d.3-1/input1
S: Sysfs=/class/input/input6
H: Handlers=kbd event6
B: EV=3
B: KEY=3078 d800d101 1e0000 0 0 0

I: Bus=0003 Vendor=06a3 Product=8000 Version=0120
N: Name="Chicony USB Gaming Keyboard Pro"
P: Phys=usb-0000:00:1d.3-1/input2
S: Sysfs=/class/input/input7
H: Handlers=event7
B: EV=3
B: KEY=7ff0000 0 0 0 0 0 0 0 0 0
```


xorg.conf:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Name"  "Logitech USB-PS/2 Optical Mouse"
#        Option          "Device"        "/dev/input/event9"
EndSection
```


.xbindkeysrc:
```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7
```

The side buttons show up as 6 and 7 in xev.

What am I doing wrong?

---

### Post by detyabozhye on 2006-12-01
Well, it seems you might not have xbindkeys running. As for button 6 and 7 doing horizontal scroll, that is normal default behavior. The mice with tilt whell have button 8 and 9 for the side buttons while 6 and 7 are the tilt.

---

### Post by iTh on 2006-12-01
Nothing changes when I run xbindkeys in konsole.

xbindkeys -v
```
displayName = :0.0
rc file = /home/ith/.xbindkeysrc
rc guile file = /home/ith/.xbindkeysrc.scm
getting rc guile file /home/ith/.xbindkeysrc.scm.
initializing guile fns...
xbindkey_wrapper debug: cmd=xbindkeys_show.
xbindkey_wrapper debug: modifier = control.
xbindkey_wrapper debug: modifier = shift.
xbindkey_wrapper debug: key = q
xbindkey_wrapper debug: cmd=xterm.
xbindkey_wrapper debug: modifier = m:0x4.
xbindkey_wrapper debug: key = c:41
xbindkey_wrapper debug: cmd=xterm.
xbindkey_wrapper debug: modifier = control.
xbindkey_wrapper debug: key = b:2
xbindkey_wrapper debug: cmd=xterm.
xbindkey_wrapper debug: modifier = alt.
xbindkey_wrapper debug: modifier = m:4.
xbindkey_wrapper debug: modifier = mod2.
xbindkey_wrapper debug: key = c:0x29

min_keycode=8     max_keycode=255 (ie: know keycodes)
"xbindkeys_show"
    Control+Shift + q
"xterm"
    m:0x4 + c:41
    Control + f
"xterm"
    m:0x4 + b:2   (mouse)
"xterm"
    m:0xc + c:41
    Control+Alt + f
starting loop...
```

---

### Post by kobewan on 2006-12-02
Use this:

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7
```

Make sure that Left and Right are capitalized properly, since I think that it is case sensitive. Then, goto the terminal and put in:

```
killall -HUP xbindkeys
```

That should reload xbindkeys with the newest settings.

I can't seem to get click to work though. When I put "~/.click/click 4" into terminal, it scrolls up just like it should. But when I use
```

"~/.click/click 4"
	b:8
```

It doesn't work. Any ideas?

Another thing that I found, might be a bug in xvkbd. If you use -no-jump-pointer along with -xtest, it doesn't let go of the modifier key. For example

```
# Try setting a bookmark
"/usr/bin/xvkbd -no-jump=pointer -xtest -text "\[B]""
b:9
```

Button9 should be set to Shift+b (its easier to just use B) but what it doees is [Shift_Press][b_Press][b_Release], so that the shift key is stuck down. You have to actually press Shift to release it, I can't figure out any other way. Is this a bug, or is there supposed to be some other way to correct this?

---

### Post by detyabozhye on 2006-12-02
Does click work if you do the full path? /home/user_name/.click/click 4

---

### Post by kobewan on 2006-12-03
No, it doesn't but I think I found out why. When the xbindkeys daemon is running, button 8 on my mouse doesn't show up in xev (doesn't mstter if anything is mapped to it or not). xev shows this when I press the button:-

Keymap notify event

93 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 
 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0

So I can't really map anything to it (at least I don't know how to). However, it correctly catches the release as a button 8 release, so I have it mapped to that for now. I'm using [http://freshmeat.net/projects/lmpcm_usb/]("http://freshmeat.net/projects/lmpcm_usb/"), by the way.

---

### Post by TrendyDark on 2006-12-03
are there guides like this for Logitech G5 Laser mice?

---

### Post by detyabozhye on 2006-12-04
The G5 should work with this guide, except you would need different settings in .xbindkeys.

---

### Post by elektronaut on 2006-12-05
I've been trying to get the tilt wheel on my Logitech LX5 working for hours now. This mouse is part of a wireless combo (Logitech S510 Media). I followed the HowTo with and without the 'udev' rule. Xserver keeps crashing all the time. Here is my latest try:
```

I: Bus=0003 Vendor=046d Product=c50c Version=2240
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:11.2-1/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c50c Version=2240
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:11.2-1/input1
S: Sysfs=/class/input/input3
H: Handlers=kbd mouse0 event3 ts0
B: EV=f
B: KEY=c0002 400 0 0 ff0001 f80 78000 6039fa d841d7ad 9e0000 0 0 0
B: REL=1c3
B: ABS=1 0

```

```
Section "InputDevice"
        Identifier      "Mouse0"
        Driver          "evdev"
        Option          "SendCoreEvents"        "True"
        Option          "Phys"                  "usb-0000:00:11.2-1/input1"
        Option          "Buttons"               "7"
        Option          "Name"                  "Logitech USB Receiver"
        Option          "ZAxisMapping"          "4 5 7 6"
        Option          "Resolution"            "800"
EndSection
```
Anybody got an idea what to try now?

---

### Post by kobewan on 2006-12-05
What do you mean that xserver keeps crashing? How do you know it keeps crashing and does it give you any error message?

You might want to try replacing 
	Option		"SendCoreEvents" 	"True"

with
	Option		"AlwaysCore"

Also, I have a couple of question. My mouse (Logitech MediaPlay) has no smart scrolling. Would it still be possible to map it so that button 6 (lower thumb button) functions as smart scroll? Lomoco detects it as an  MX1000. I can use click to make it send a button 4 click, but it doesn't function as a continuous scroll if you hold it down.

Also, I have my Logitech mouse, configured with evdev and Option "AlwaysCore", on my laptop. The mouse accelerates faster than I like, but if I go to System | Preferences | Mouse in the menu, changing the acceleration settings there only affects my touchpad. Can I change the acceleration settings of my mouse?

---

### Post by elektronaut on 2006-12-06
> **kobewan said:**
> What do you mean that xserver keeps crashing? How do you know it keeps crashing and does it give you any error message?

You might want to try replacing 
	Option		"SendCoreEvents" 	"True"

with
	Option		"AlwaysCore"

If I modify xorg.conf, log out and restart Xserver, I get a blue screen noticing me about the failure of starting Xserver. I now tried with "AlwaysCore" instead, but still it doesn't work. [Here is the logfile]("http://nopaste.info/52774c8881.html"). I don't get a clue looking at it.

---

### Post by detyabozhye on 2006-12-07
@elektronaut: I'm not sure exactly where the problem id, but the reason X isn't starting is because it's not finding the mouse; the problem is not in the "CorePointer", "SendCoreEvents", or "AlwaysCore" options.

@kobewan: smart scrolling will onlt work depending on your mouse and what lmoco supports.

---

### Post by hebetude on 2006-12-08
I came into a problem with this guide.  It works PERFECTLY, which is excellent.  However, if I remove the mouse X server fails to start.  I guess I can keep two versions of my xorg.conf, but it'd be very inconvenient waiting for X server to realize it has failed to load.

---

### Post by leonlauncher on 2006-12-08
is there any way to bind the mouse3button to the tilt buttons on a G5?

---

### Post by detyabozhye on 2006-12-08
> **hebetude said:**
> I came into a problem with this guide.  It works PERFECTLY, which is excellent.  However, if I remove the mouse X server fails to start.  I guess I can keep two versions of my xorg.conf, but it'd be very inconvenient waiting for X server to realize it has failed to load.

Change:

Option "CorePointer"

to:

Option "SendCoreEvents" "True"

---

### Post by detyabozhye on 2006-12-08
> **leonlauncher said:**
> is there any way to bind the mouse3button to the tilt buttons on a G5?

well, button 3 is only one button, you can bind or xmodmap it to one of the tilt buttons.

If you're trying to make it autoscroll, there's an option in Firefox for that, but most Linux apps don't do autoscroll with button 3.

---

### Post by leonlauncher on 2006-12-09
well im actually trying to open and close tabs with the tilt buttons in firefox, because the button3 on a G5 really sucks and im a linux noob don't understand xmodmap that much

---

### Post by bg1256 on 2006-12-10
Success! On a Logitech Mx500 running Edgy.  

The main reason I did this was internet browsing in Firefox.

In Nautilus, it doesn't go back and forth between folders, but it does scroll left and right in the file browser. I'm not sure if that's the desired effect...

Thanks for the great HowTo!

---

### Post by BLTicklemonster on 2006-12-10
By the way, xmodmap works great in Feisty. Never been able to get xkeybinds or whatever it is to work in nautilus, ever, though.

---

### Post by detyabozhye on 2006-12-11
On a tilt-wheel mouse, the tilt wheel is button 6 and 7 and the side buttons are 8 and 9, but Firefox (by default) and Opera (always) use 6 and 7 for back and forward (seems they assume you don't have a tilt wheel). The browsers should have an option to make the behaivor correct for 6, 7, 8, and 9 but untill then (and since I don't have a tilt wheel), I think I'll actually kind of enjoy this wrong behaivor.

---

### Post by daou on 2006-12-11
> On a tilt-wheel mouse, the tilt wheel is button 6 and 7 and the side buttons are 8 and 9, but Firefox (by default) and Opera (always) use 6 and 7 for back and forward (seems they assume you don't have a tilt wheel). The browsers should have an option to make the behaivor correct for 6, 7, 8, and 9 but untill then (and since I don't have a tilt wheel), I think I'll actually kind of enjoy this wrong behaivor.

This was a problem for the MX Revolution as well which was covered in the MX Revo howto. It can be fixed with a simple xmodmap command:

```
xmodmap -e "pointer = 1 2 3 4 5 7 6 8 9 10 11 12 13 14 15 16 17 18 19 20"
```

This swaps the functionality of button 6 and 7 (right and left tilts). Or, to make the change persist, add this line to ~/.Xmodmap

```
pointer = 1 2 3 4 5 7 6 8 9 10 11 12 13 14 15 16 17 18 19 20
```

---

### Post by BLTicklemonster on 2006-12-12
Yay! Adding 

```
xmodmap ~/.xmodmap
```


to the startup file in /home/yourname/.fluxbox will allow the logitech mouse to work. Now I wonder about adding locomo to fluxbox.

(for anyone who uses fluxbox, btw)

---

### Post by tweedledee on 2006-12-12
> **detyabozhye said:**
> Awesome man! As for double clicking, it might be possible with a few lines of C code. Check out and try modifying and compiling this package, might work: [http://bg.rifetech.com/click.tgz](http://bg.rifetech.com/click.tgz)

For double-clicking, look here: [http://www.ubuntuforums.org/showthread.php?t=316441](http://www.ubuntuforums.org/showthread.php?t=316441) .  It's actually quite easy using xautomation & xbindkeys.

---

### Post by sjust on 2006-12-12
I have tried this link and it worked for me [http://www.ubuntuforums.org/showthread.php?t=316441](http://www.ubuntuforums.org/showthread.php?t=316441)
I just used button 8 on my MX510

---

### Post by dejitarob on 2006-12-15
Thanks for the guide! My evoluent mouse's buttons worked without any configuration but the xbindkeys part was needed for getting the back/forward buttons to work in konqueror.

---

### Post by kobewan on 2006-12-15
I've encountered a few more problems in my ever-continuing quest to tweak my mouse to perfection. I suppose that these don't exactly apply to this thread as such, but I think some people could find their solutions useful and was hoping to get some help. In increasing order of difficulty to solve, they are:-

1. Setting up an OnScreen Display : *solved*

2. Proper application-specific settings: Right now,  I've created a few different settings files for xbindkeys, and keep a drawer on my panel with the icons of 5 or 6 different apps in it. Whenever I want to change my bindings, I just select the appropriate icon. The launched script kills xbindkeys and tells it to restart using the appropriate application's configuration file. 

Although this works reasonably well, I think it should be possible to do better than this. I was using [devilspie]("http://freshmeat.net/projects/devilspie/") yesterday, and it has pretty good window matching capabilities. Basically, I want a program that can do something like this:

if (application name = Firefox) and (focused = true) then (*run command*). 

I think programs like this *should* exist, but I haven't had any success in finding anything.

3. Setting sensitivity of second mouse : based on the information that I've found, I think this might not even be possible. I'm using an IBM Thinkpad, and my eraser nub/mouse thing in the middle of the keyboard is set as my primary mouse. Using the 'Mouse' applet in Gnome Control Center as well as 'xset m'  in the terminal only change the setting for my eraser nub. My Logitech mouse has a higher acceleration than I would like, but I am unable to change it. Setting the resolution in lomoco doesn't help either.

---

### Post by BatteryCell on 2006-12-16
Hey I got this to work perfectly before but now(after upgrade to 6.10) when I boot into X, it starts fine, but I cant move the mouse at all.  Just wondering if anybody knows the solution to this.

Edit:
Never mind I fixed it by changing 
```

Option		"CorePointer"

```
to
```

Option          "SendCoreEvents"        "true"

```

---

### Post by userundefine on 2006-12-20
Worked flawlessly on Edgy for my MX510!  Thanks a lot!

---

### Post by detyabozhye on 2006-12-21
You're welcome.

---

### Post by userundefine on 2006-12-22
Just a little tidbit to contribute, not sure if anyone has mentioned this but I saw a few people had trouble with cruise control.  If people are installing lomoco to change the cpi, they can just enable CruiseControl right there with lomoco.
> **sudo lomoco --sms**
You can see it in the man page.

Much easier than messing with xbindkeysrc IMO. :)

---

### Post by detyabozhye on 2006-12-22
yeah, in Dapper, it still sent a few more buttons as well as the cruise thing tho. That's y I had the xbindkeys thing there as well.

---

### Post by drowsy on 2006-12-23
Hi, everything works perfectly(but 'man evdev' says not to put      Option		"Device" in the xorg.conf file, so you should fix that, the right way to do this is > Section "InputDevice"
        Identifier      "MX518"
        Driver          "evdev"
        Option          "Name"                  "Logitech USB-PS/2 Optical Mouse"
        Option          "Phys"                  "usb-0000:00:1d.0-2/input0"
        Option          "ButtonNumber"          "7"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "4 5"
EndSection). 

Anyway, my question is : I want to use a side button in stardict to translate stuff, so I need to emulate pressing ALT **continuously** without releasing(I can bind the side button for just pressing it, but that would not work with stardict :( )  Anybody knows how to do this ? ](*,)

---

### Post by drowsy on 2006-12-23
from 'man evdev' : 
> Option "Device" "string"
              Specifies  the  device note through which the device can be accessed.  At this time ONLY
              /dev/input/event<N>, where <N> is an integer, are matched against this this field.
              This option uses globbing.
            **  Please note that use of this option is strongly discouraged.**

---

### Post by brazzmonkey on 2006-12-25
for a logitech MX400, i followed the method i explain here : [http://www.ubuntuforums.org/showpost.php?p=1929294&postcount=3](http://www.ubuntuforums.org/showpost.php?p=1929294&postcount=3)

---

### Post by kobewan on 2006-12-25
> **drowsy said:**
> Hi, everything works perfectly(but 'man evdev' says not to put      Option        "Device" in the xorg.conf file, so you should fix that, the right way to do this is ). 

Anyway, my question is : I want to use a side button in stardict to translate stuff, so I need to emulate pressing ALT **continuously** without releasing(I can bind the side button for just pressing it, but that would not work with stardict :( )  Anybody knows how to do this ? ](*,)

I would advise getting xautomation from the repositories, since it has a much more reliable key faking program. xvkbd doesn't work very well with modifier keys. Use your side button (e.g. button 8) to do something like this:-

```
"/usr/bin/xte 'keydown Alt_L' &"
b:8

".releasealt &"
release+b:8
```

The button press command should keep press Alt without releasing it. For some reason though, xbindkeys won't let you map the keyup event to the same button's release. You can get around this problem by putting it in a script. You should, of course, have a script in your home directory called '.releasealt' or whatever else you want to call it. I'm not very good at scripting (still new to Linux), but something this simple should still work. Anyways, the script should go something. For .releasealt:

```
#!/bin/bash
#
  /usr/bin/xte 'keyup Alt_L'
done      
```                      

Easy, right?  Of course, don't forget to make the script executable. I use variations of this technique for some pretty nice button mapping. For example, I made one of my mouse buttons a timed modifier, so hitting that button and then any other button within 2 seconds gives me a different command then hitting the button without a modifier.

Alternatively, if you just want to do something like Alt+Right Click (for example), then put this in xbindkeys:

```
"/usr/bin/xte 'keydown Alt_L' 'mouseclick 3' 'keyup Alt_L'"
b:8
```

xte is pretty sweet, and simulates mouse clicks as well. If you need any help, just ask...I spent far too many hours trying to get around various glitches in xbindkeys.

---

### Post by zorglab on 2006-12-27
Interesting howto... Great work! However, there are some points which could be done in a more easy or elegant manner. Here we go.

_1. Usage of udev_
This is actually not needed. Like someone said above, the use of the "Device" option with the evdev driver is discouraged. A better way to achieve this, is to use the combination of the "Name" and "Phys" options. For my V400 wireless mouse, this gives:
```

        Option          "Name"                  "Logitech USB Receiver"
        Option          "Phys"                  "usb-*/input0"

```
Of course, you should replace these informations with what you found in /proc/bus/input/devices. Don't forget to use the wildcard '*' in the Phys option, as the numbers following "usb-" depend on which port you connected your mouse (and you probably don't want to be forced to use the same one each time :mrgreen: ).

_2. Horizontal wheel_
Like someone said, the horizontal wheel buttons on some mice are swapped. There is an option in evdev to correct this:
```

        Option          "HWheelRelativeAxisButtons"     "7 6"

```
You'll need to check the button numbers with evdev.

_3. Core pointers_
X.org always need a core pointer in order to start. Selecting an usb mouse as a core pointer isn't the best idea, especially on a laptop. My suggestion is to leave the original mouse section as is, and add a new section (like for the synaptic touchpad) with the option "SendCoreEvents":
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Logitech Mouse"
        Driver          "evdev"
        Option          "SendCoreEvents"        "true"
        Option          "Name"                  "Logitech USB Receiver"
        Option          "Phys"                  "usb-*/input0"
        Option          "HWheelRelativeAxisButtons"     "7 6"
EndSection

```
For this to work, you also need to add a line in the "ServerLayout" section:
```

Section "ServerLayout"
        ...
        InputDevice     "Configured Mouse"
        InputDevice     "Logitech Mouse"
        ...
EndSection

```

So, that was it. I hope it will help some people. Maybe some of these remarks were already given in this thread, but I didn't had the courage to read through the 37 pages ;)

---

### Post by detyabozhye on 2006-12-27
You're correct zorglab about all that you said. Thing is, this is a Dapper guide, so things like the udev for example, were to work around the bugs in the Dapper package. I've been so busy though, that I haven't updated the guide for Edgy yet. I was thinking about making a fresh new guide for Edgy, but haven't gotten around to it yet.

---

### Post by drowsy on 2006-12-28
> **kobewan said:**
> 

```
"/usr/bin/xte 'keydown Alt_L' &"
b:8

".releasealt &"
release+b:8
```

For some reason though, xbindkeys won't let you map the keyup event to the same button's release. 

For .releasealt:
```
#!/bin/bash
#
  /usr/bin/xte 'keyup Alt_L'
done      
```                      

You dont need 'done' in this script, I think. 
And for some reason this setup(xbindkeys+xte+this cfg) leaves my X unusable -- keybord does not work. :(

---

### Post by Filiprino on 2006-12-30
Hi, I own an MX3200 combo (MX 3200 Keyboard with an MX 600 Laser mouse), which uses a unique receiver.
My "cat /proc/bus/input/devices" returns de following text:
```
I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0 
B: EV=40001
B: SND=6

*Keyboard:*
[B]I: Bus=0003 Vendor=046d Product=c517 Version=3810
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.1-1/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

*Mouse:*
I: Bus=0003 Vendor=046d Product=c517 Version=3810
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.1-1/input1
S: Sysfs=/class/input/input2
H: Handlers=kbd mouse0 event2 ts0 
B: EV=f
B: KEY=c0002 400 0 0 ff0001 f80 78000 6639fa d841d7ad 9e0000 0 0 0
B: REL=1c3
B: ABS=1 0[/B]

I: Bus=0001 Vendor=1461 Product=0004 Version=0001
N: Name="bttv IR (card=13)"
P: Phys=pci-0000:01:09.0/ir0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3 
B: EV=100003
B: KEY=40fc310 82140000 0 0 0 0 2048000 180 4001 9e0000 0 0 ffd

```
I followed the guide, and Xorg crashed while attempting to start. Then I tried the options in these two posts:
[http://ubuntuforums.org/showpost.php?p=1126893&postcount=45](http://ubuntuforums.org/showpost.php?p=1126893&postcount=45)
[http://ubuntuforums.org/showpost.php?p=1155987&postcount=62](http://ubuntuforums.org/showpost.php?p=1155987&postcount=62)

And none worked. :-S
My last xorg.conf-logi (section input device for mouse) is:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Name"                  "Logitech USB Receiver"
        Option          "Dev Phys"              "usb-0000:00:02.1-1/input1"
        Option          "ZAxisMapping"          "4 5 6 7"
        Option          "Buttons"               "12"
        Option          "Resolution"            "800"
EndSection

```

I'm splitting this post because with my xorg log I pass the maximum character limit :P.

---

### Post by Filiprino on 2006-12-30
With this config, my xorg.log returns the following text (I think that the interesting part is at the end, with a fatal error signal 11 caught, including a backtrace before that message):

```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux kiwi 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec 30 15:40:54 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "F700B"
(**) |   |-->Device "NVIDIA Corporation NV34 [GeForce FX 5200]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,01e0 card 1043,80ac rev c1 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01eb card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ee card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01ed card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,01ec card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:5: chip 10de,01ef card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,0060 card 1043,80ad rev a4 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0064 card 1043,0c11 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,0067 card 1043,0c11 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,0067 card 1043,0c11 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,0068 card 1043,0c11 rev a4 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0066 card 1043,80a7 rev a1 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 10de,006b card 1043,0c11 rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,006a card 1043,8095 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,006c card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0065 card 1043,0c11 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0d:0: chip 10de,006e card 1043,809a rev a3 class 0c,00,10 hdr 00
(II) PCI: 00:1e:0: chip 10de,01e8 card 0000,0000 rev c1 class 06,04,00 hdr 01
(II) PCI: 01:04:0: chip 11ab,4320 card 1043,811a rev 13 class 02,00,00 hdr 00
(II) PCI: 01:08:0: chip 14e4,4320 card 1737,0013 rev 03 class 02,80,00 hdr 00
(II) PCI: 01:09:0: chip 109e,036e card 1461,0004 rev 11 class 04,00,00 hdr 80
(II) PCI: 01:09:1: chip 109e,0878 card 1461,0004 rev 11 class 04,80,00 hdr 80
(II) PCI: 01:0b:0: chip 1095,3112 card 1095,6112 rev 02 class 01,04,00 hdr 00
(II) PCI: 03:00:0: chip 10de,0322 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000bfff (0x2000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xe2000000 - 0xe3ffffff (0x2000000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
(--) PCI: (1:9:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xe0000000/12
(--) PCI:*(3:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xe2000000/24, 0xd8000000/27
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
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd7ffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe5006000 - 0xe50061ff (0x200) MX[B]
	[1] -1	0	0xe0001000 - 0xe0001fff (0x1000) MX[B]
	[2] -1	0	0xe5004000 - 0xe5005fff (0x2000) MX[B]
	[3] -1	0	0xe5000000 - 0xe5003fff (0x4000) MX[B]
	[4] -1	0	0xe6085000 - 0xe608503f (0x40) MX[B]
	[5] -1	0	0xe6084000 - 0xe60847ff (0x800) MX[B]
	[6] -1	0	0xe6087000 - 0xe6087fff (0x1000) MX[B]
	[7] -1	0	0xe6000000 - 0xe607ffff (0x80000) MX[B]
	[8] -1	0	0xe6083000 - 0xe6083fff (0x1000) MX[B]
	[9] -1	0	0xe6082000 - 0xe60820ff (0x100) MX[B]
	[10] -1	0	0xe6081000 - 0xe6081fff (0x1000) MX[B]
	[11] -1	0	0xe6086000 - 0xe6086fff (0x1000) MX[B]
	[12] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[13] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[14] -1	0	0xe2000000 - 0xe2ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xe0000fff (0x1000) MX[B](B)
	[16] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[18] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[20] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[22] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[26] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe5006000 - 0xe50061ff (0x200) MX[B]
	[1] -1	0	0xe0001000 - 0xe0001fff (0x1000) MX[B]
	[2] -1	0	0xe5004000 - 0xe5005fff (0x2000) MX[B]
	[3] -1	0	0xe5000000 - 0xe5003fff (0x4000) MX[B]
	[4] -1	0	0xe6085000 - 0xe608503f (0x40) MX[B]
	[5] -1	0	0xe6084000 - 0xe60847ff (0x800) MX[B]
	[6] -1	0	0xe6087000 - 0xe6087fff (0x1000) MX[B]
	[7] -1	0	0xe6000000 - 0xe607ffff (0x80000) MX[B]
	[8] -1	0	0xe6083000 - 0xe6083fff (0x1000) MX[B]
	[9] -1	0	0xe6082000 - 0xe60820ff (0x100) MX[B]
	[10] -1	0	0xe6081000 - 0xe6081fff (0x1000) MX[B]
	[11] -1	0	0xe6086000 - 0xe6086fff (0x1000) MX[B]
	[12] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[13] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[14] -1	0	0xe2000000 - 0xe2ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xe0000fff (0x1000) MX[B](B)
	[16] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[18] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[20] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[22] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[26] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
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
	[4] -1	0	0xe5006000 - 0xe50061ff (0x200) MX[B]
	[5] -1	0	0xe0001000 - 0xe0001fff (0x1000) MX[B]
	[6] -1	0	0xe5004000 - 0xe5005fff (0x2000) MX[B]
	[7] -1	0	0xe5000000 - 0xe5003fff (0x4000) MX[B]
	[8] -1	0	0xe6085000 - 0xe608503f (0x40) MX[B]
	[9] -1	0	0xe6084000 - 0xe60847ff (0x800) MX[B]
	[10] -1	0	0xe6087000 - 0xe6087fff (0x1000) MX[B]
	[11] -1	0	0xe6000000 - 0xe607ffff (0x80000) MX[B]
	[12] -1	0	0xe6083000 - 0xe6083fff (0x1000) MX[B]
	[13] -1	0	0xe6082000 - 0xe60820ff (0x100) MX[B]
	[14] -1	0	0xe6081000 - 0xe6081fff (0x1000) MX[B]
	[15] -1	0	0xe6086000 - 0xe6086fff (0x1000) MX[B]
	[16] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[17] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[18] -1	0	0xe2000000 - 0xe2ffffff (0x1000000) MX[B](B)
	[19] -1	0	0xe0000000 - 0xe0000fff (0x1000) MX[B](B)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[24] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[25] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[26] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[27] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[28] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[29] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[30] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[31] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[32] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 0.0.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
	GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
	GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
	GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
	GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100

```

The rest is in the third post.

---

### Post by Filiprino on 2006-12-30
```

(II) Primary Device is: PCI 03:00:0
(--) Chipset GeForce FX 5200 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe5006000 - 0xe50061ff (0x200) MX[B]
	[5] -1	0	0xe0001000 - 0xe0001fff (0x1000) MX[B]
	[6] -1	0	0xe5004000 - 0xe5005fff (0x2000) MX[B]
	[7] -1	0	0xe5000000 - 0xe5003fff (0x4000) MX[B]
	[8] -1	0	0xe6085000 - 0xe608503f (0x40) MX[B]
	[9] -1	0	0xe6084000 - 0xe60847ff (0x800) MX[B]
	[10] -1	0	0xe6087000 - 0xe6087fff (0x1000) MX[B]
	[11] -1	0	0xe6000000 - 0xe607ffff (0x80000) MX[B]
	[12] -1	0	0xe6083000 - 0xe6083fff (0x1000) MX[B]
	[13] -1	0	0xe6082000 - 0xe60820ff (0x100) MX[B]
	[14] -1	0	0xe6081000 - 0xe6081fff (0x1000) MX[B]
	[15] -1	0	0xe6086000 - 0xe6086fff (0x1000) MX[B]
	[16] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[17] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[18] -1	0	0xe2000000 - 0xe2ffffff (0x1000000) MX[B](B)
	[19] -1	0	0xe0000000 - 0xe0000fff (0x1000) MX[B](B)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[24] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[25] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[26] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[27] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[28] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[29] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[30] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[31] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[32] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe5006000 - 0xe50061ff (0x200) MX[B]
	[5] -1	0	0xe0001000 - 0xe0001fff (0x1000) MX[B]
	[6] -1	0	0xe5004000 - 0xe5005fff (0x2000) MX[B]
	[7] -1	0	0xe5000000 - 0xe5003fff (0x4000) MX[B]
	[8] -1	0	0xe6085000 - 0xe608503f (0x40) MX[B]
	[9] -1	0	0xe6084000 - 0xe60847ff (0x800) MX[B]
	[10] -1	0	0xe6087000 - 0xe6087fff (0x1000) MX[B]
	[11] -1	0	0xe6000000 - 0xe607ffff (0x80000) MX[B]
	[12] -1	0	0xe6083000 - 0xe6083fff (0x1000) MX[B]
	[13] -1	0	0xe6082000 - 0xe60820ff (0x100) MX[B]
	[14] -1	0	0xe6081000 - 0xe6081fff (0x1000) MX[B]
	[15] -1	0	0xe6086000 - 0xe6086fff (0x1000) MX[B]
	[16] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[17] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[18] -1	0	0xe2000000 - 0xe2ffffff (0x1000000) MX[B](B)
	[19] -1	0	0xe0000000 - 0xe0000fff (0x1000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[26] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[27] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[28] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[29] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[30] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[31] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[32] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[33] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[34] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[35] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce FX 5200"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xD8000000
(--) NV(0): MMIO registers at 0xE2000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules/libi2c.so
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...found one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: GSM  Model: 4349  Serial#: 60998
(II) NV(0): Year: 2002  Week: 46
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NV(0): Signal levels configurable
(II) NV(0): Sync:  Separate
(II) NV(0): Max H-Image Size [cm]: horiz.: 33  vert.: 25
(II) NV(0): Gamma: 2.85
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing not preferred mode in violation of standard!(II) NV(0): redX: 0.618 redY: 0.329   greenX: 0.295 greenY: 0.600
(II) NV(0): blueX: 0.144 blueY: 0.071   whiteX: 0.283 whiteY: 0.298
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 720x400@88Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@67Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@87Hz (interlaced)
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1152x870@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 640  vsize 480  refresh: 75  vid: 20273
(II) NV(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) NV(0): #2: hsize: 800  vsize 600  refresh: 75  vid: 20293
(II) NV(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NV(0): #4: hsize: 1024  vsize 768  refresh: 70  vid: 19041
(II) NV(0): #5: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) NV(0): #6: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NV(0): #7: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 94.5 MHz   Image Size:  315 x 230 mm
(II) NV(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) NV(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 108.0 MHz   Image Size:  315 x 230 mm
(II) NV(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) NV(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) NV(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 71 kHz, PixClock max 110 MHz
(II) NV(0): Monitor name: F700B
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 appears to have a CRT attached
(II) NV(0): Using CRT on CRTC 0
(--) NV(0): VideoRAM: 131072 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): F700B: Using default hsync range of 30.00-71.00 kHz
(II) NV(0): F700B: Using default vrefresh range of 50.00-160.00 Hz
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(WW) (1280x960,F700B) mode clock 148.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(WW) (1280x1024,F700B) mode clock 135MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(WW) (1280x1024,F700B) mode clock 157.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(WW) (1600x1200,F700B) mode clock 162MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,F700B) mode clock 175.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,F700B) mode clock 189MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,F700B) mode clock 202.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,F700B) mode clock 229.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(WW) (800x600,F700B) mode clock 114.75MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(WW) (1792x1344,F700B) mode clock 204.8MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(WW) (1792x1344,F700B) mode clock 261MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(WW) (896x672,F700B) mode clock 130.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(WW) (1856x1392,F700B) mode clock 218.3MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(WW) (1856x1392,F700B) mode clock 288MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(WW) (928x696,F700B) mode clock 144MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(WW) (1920x1440,F700B) mode clock 234MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(WW) (960x720,F700B) mode clock 117MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(WW) (1920x1440,F700B) mode clock 297MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(WW) (960x720,F700B) mode clock 148.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(WW) (1152x864,F700B) mode clock 121.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(WW) (1400x1050,F700B) mode clock 122MHz exceeds DDC maximum 110MHz
(WW) (1400x1050,F700B) mode clock 151MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(WW) (1400x1050,F700B) mode clock 155.8MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(WW) (1400x1050,F700B) mode clock 184MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(WW) (1680x1050,F700B) mode clock 147.14MHz exceeds DDC maximum 110MHz
(WW) (1920x1200,F700B) mode clock 193.16MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(WW) (1920x1200,F700B) mode clock 230MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(WW) (960x600,F700B) mode clock 115MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(WW) (1920x1440,F700B) mode clock 341.35MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(WW) (960x720,F700B) mode clock 170.675MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(WW) (2048x1536,F700B) mode clock 266.95MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(WW) (1024x768,F700B) mode clock 133.475MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(WW) (2048x1536,F700B) mode clock 340.48MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(WW) (1024x768,F700B) mode clock 170.24MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(WW) (1024x768,F700B) mode clock 194.02MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1440x900" (width too large for virtual size)
(--) NV(0): Virtual size is 1280x1024 (pitch 1280)
(**) NV(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) NV(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) NV(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) NV(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) NV(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) NV(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) NV(0): *Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) NV(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) NV(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) NV(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) NV(0):  Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
(**) NV(0):  Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x800"   83.46  1280 1344 1480 1680  800 801 804 828
(**) NV(0):  Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(**) NV(0):  Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x768"   80.14  1280 1344 1480 1680  768 769 772 795
(**) NV(0):  Default mode "1152x768": 65.0 MHz, 44.2 kHz, 54.8 Hz
(II) NV(0): Modeline "1152x768"   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync
(**) NV(0):  Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) NV(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) NV(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0):  Default mode "1024x768": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)
(II) NV(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(**) NV(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) NV(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) NV(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) NV(0):  Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "840x525"   73.57  840 892 984 1128  525 525 527 543 doublescan
(**) NV(0):  Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "700x525"   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync
(**) NV(0):  Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x512"   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync
(**) NV(0):  Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) NV(0): Modeline "720x450"   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync
(**) NV(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) NV(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) NV(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) NV(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) NV(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) NV(0):  Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "576x432"   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync
(**) NV(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) NV(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(**) NV(0):  Default mode "576x384": 32.5 MHz, 44.2 kHz, 54.8 Hz (D)
(II) NV(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "512x384"   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(II) NV(0): Modeline "512x384"   39.40  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) NV(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) NV(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) NV(0):  Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
(II) NV(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
(**) NV(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) NV(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) NV(0):  Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) NV(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) NV(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) NV(0):  Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) NV(0): Modeline "320x240"   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 332 352 416  240 244 245 260 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"   12.60  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(**) NV(0):  Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "360x200"   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync
(**) NV(0):  Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x200"   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync
(**) NV(0):  Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x175"   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync
(--) NV(0): Display dimensions: (330, 250) mm
(--) NV(0): DPI set to (98, 104)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
	[1] 0	0	0xe2000000 - 0xe2ffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe5006000 - 0xe50061ff (0x200) MX[B]
	[7] -1	0	0xe0001000 - 0xe0001fff (0x1000) MX[B]
	[8] -1	0	0xe5004000 - 0xe5005fff (0x2000) MX[B]
	[9] -1	0	0xe5000000 - 0xe5003fff (0x4000) MX[B]
	[10] -1	0	0xe6085000 - 0xe608503f (0x40) MX[B]
	[11] -1	0	0xe6084000 - 0xe60847ff (0x800) MX[B]
	[12] -1	0	0xe6087000 - 0xe6087fff (0x1000) MX[B]
	[13] -1	0	0xe6000000 - 0xe607ffff (0x80000) MX[B]
	[14] -1	0	0xe6083000 - 0xe6083fff (0x1000) MX[B]
	[15] -1	0	0xe6082000 - 0xe60820ff (0x100) MX[B]
	[16] -1	0	0xe6081000 - 0xe6081fff (0x1000) MX[B]
	[17] -1	0	0xe6086000 - 0xe6086fff (0x1000) MX[B]
	[18] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[19] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[20] -1	0	0xe2000000 - 0xe2ffffff (0x1000000) MX[B](B)
	[21] -1	0	0xe0000000 - 0xe0000fff (0x1000) MX[B](B)
	[22] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[23] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[24] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[27] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[28] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[29] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[30] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[31] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[32] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[33] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[34] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[35] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[36] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[37] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xd8000000,0x8000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
(==) RandR enabled
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
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "es"
(**) Generic Keyboard: XkbLayout: "es"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evdev brain: Rescanning devices (1).
(**) Option "CorePointer"
(**) Configured Mouse-usb-0000:00:02.1-1/input0: Core Pointer
(**) Option "CorePointer"
(**) Configured Mouse-usb-0000:00:02.1-1/input1: Core Pointer
(II) Configured Mouse-usb-0000:00:02.1-1/input1: Found 1 absolute axes.
(II) Configured Mouse-usb-0000:00:02.1-1/input1: Configuring as pointer.
(**) Configured Mouse-usb-0000:00:02.1-1/input1: Configuring in Absolute mode.
(**) Configured Mouse-usb-0000:00:02.1-1/input1: AbsoluteScreen: -1.

Backtrace:
0: /usr/bin/X.schedreal(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: /usr/lib/xorg/modules/input/evdev_drv.so [0xb7c6a67b]
3: /usr/lib/xorg/modules/input/evdev_drv.so [0xb7c6b6fd]
4: /usr/lib/xorg/modules/input/evdev_drv.so(evdevNewDriver+0x44) [0xb7c6b860]
5: /usr/lib/xorg/modules/input/evdev_drv.so [0xb7c6a3f1]
6: /usr/bin/X.schedreal(InitInput+0x16f) [0x809f21f]
7: /usr/bin/X.schedreal(main+0x355) [0x806e5e5]
8: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d958cc]
9: /usr/bin/X.schedreal(FontFileCompleteXLFD+0xa1) [0x806da51]

Fatal server error:
Caught signal 11.  Server aborting


```

I don't know what to do now :-S. Ah, before trying the alternate posts, I deleted the udev rule before applying those modifications, because they didn't use the string "inputX".
Thanks and I hope this post is useful to other people.

---

### Post by Filiprino on 2006-12-30
Hello again, I have to add that I'm using Ubuntu Edgy.

---

### Post by detyabozhye on 2006-12-30
I believe the option should be "Phys" and not "Dev Phys"
First thing that comes to mind.

---

### Post by Filiprino on 2006-12-30
It didn't work :(. It's so weird, in this thread, at page 10 a user reports he also has a combo with 1 receiver (MX3100), and he could manage to configure it ok. But I try in the same way, and it just won't work.
I'm desperate, I'll try to follow again the how-to, with the modifications added by the MX3100 user.
Thanks.

---

### Post by bofphile on 2006-12-30
This guide works perfectly with my Logitech LX7. :) 
Thanks a lot detyabozhye !

---

### Post by Filiprino on 2006-12-31
Hello! :D
First of all, I have a combo of keyboard and mouse, both wireless, model MX 3200 from Logitech, and I finally got the mouse working with udev and some tweaks on the xorg.conf.
My udev rule is (19-local.rules):
```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver",SYSFS{../device/bInterfaceNumber}=="01", NAME="input/event9"
```
Now, let's see the xorg.conf. First, I added a line on the section modules, in order to load "evdev" (as stated in de man page of evdev):
```
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	**Load	"evdev"**
EndSection
```
Then, I modified the input device for the mouse:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"			"Logitech USB Receiver"
	Option		"Phys"			"usb-0000:00:02.1-1/input1"
	Option		"Device"		"/dev/input/event9"
	Option		"AbsoluteScreen"	"0"
	#Option		"Protocol"		"ExplorerPS/2"
	#Option		"ZAxisMapping"		"4 5"
	#Option		"Emulate3Buttons"	"true"
EndSection
```
Probably I can delete the option name and option phys, because it's using event9, which is already mapped to the mouse thanks to the udev rule.
The X.Org log outputs the following lines related to the mouse and keyboard:
```

(II) evdev brain: Rescanning devices (1).
(**) Option "CorePointer"
(**) Configured Mouse-usb-0000:00:02.1-1/input1: Core Pointer
(II) Configured Mouse-usb-0000:00:02.1-1/input1: Found 1 absolute axes.
(II) Configured Mouse-usb-0000:00:02.1-1/input1: Configuring as pointer.
(**) Configured Mouse-usb-0000:00:02.1-1/input1: Configuring in Absolute mode.
(**) Option "AbsoluteScreen" "0"
(**) Configured Mouse-usb-0000:00:02.1-1/input1: AbsoluteScreen: 0.
(II) Configured Mouse-usb-0000:00:02.1-1/input1: Found 5 relative axes.
(II) Configured Mouse-usb-0000:00:02.1-1/input1: Configuring as pointer.
(**) Configured Mouse-usb-0000:00:02.1-1/input1: HWHEELRelativeAxisButtons: 6 7.
(**) Configured Mouse-usb-0000:00:02.1-1/input1: WHEELRelativeAxisButtons: 4 5.
(II) Configured Mouse-usb-0000:00:02.1-1/input1: Found 8 mouse buttons
(II) Configured Mouse-usb-0000:00:02.1-1/input1: Configured 12 mouse buttons
(II) XINPUT: Adding extended input device "Configured Mouse-usb-0000:00:02.1-1/input1" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+es+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Configured Mouse-usb-0000:00:02.1-1/input1: 5 valuators.
(**) ../../src/evdev_btn.c (90): Registering 12 buttons.
    xkb_keycodes             { include "evdev+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc104)" };
(II) Configured Mouse-usb-0000:00:02.1-1/input1: Init
(II) evdev brain: Rescanning devices (2).
(II) Configured Mouse-usb-0000:00:02.1-1/input1: On

```

I simply had to add the line Option "AbsoluteScreen" "0" to the input devices. Reading the logs, evdev was assigning screen -1 to the mouse, while the "real" screen was screen 0, the one which xorg operates with.

---

### Post by spockrock on 2007-01-02
I recently swtiched to the mx5000 keyboard and mice, and got my xorg.conf working with the "AbsoluteScreen" "0" option, Filiprino....thank you so much!!


The only weird thing though is firefox uses my horizontal scroll buttons as back and forth buttons, I dunno if this is a residual effect from my previous config, or just some weird error.... :s

ok fixed horizontal scroll issue with firefox by doing about:config and then changing both those values to one.
mousewheel.horizscroll.withnokey.action
mousewheel.horizscroll.withnokey.numlines

---

### Post by Filiprino on 2007-01-02
Hi again. I've decided to switch back to the "mouse" driver, because the multimedia keys of the keyboard stopped working... and with evdev I was only getting the extra "search" button of the mouse mapped correctly (I mean, all the buttons including those thumb buttons, except search and zoom+-, where mapped with the normal driver, and with evdev also worked the search button correctly), so it simply didn't benefit me too much :-s
The USB HID driver should be rewritten in order to add full support to all buttons of any device, although we had to remap or use these tweaks on the xorg.conf, as noted on the KeyTouch webpage.
PS: Spockrock, I'm glad I could help someone else :D

---

### Post by JPMaximilian on 2007-01-05
I did a reinstall and I'm trying to get my mouse setup again, I followed these instructions the first ime, and they worked.  However, this time when I run:

sudo apt-get install xvkbd xbindkeys

I get the following error:

```
sudo apt-get install xvkbd xbindkeys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xvkbd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xvkbd has no installation candidate
```

What does that mean?

---

### Post by detyabozhye on 2007-01-05
You need to enable the universe repositories.

---

### Post by louisgag on 2007-01-08
> **Damiel said:**
> just changing the name and the device in this config made my logitech mx510 work perfectly in firefox and opera (including the cruise buttons). thanks! :D 

thanks to detyabozhye too for the great xbindkeys guide.

Horizontal scrolling still doesnt work for me, X11 fails loading with the following xorg.conf

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
#	Option		"ZAxisMapping"		"4 5"
	Option "WHEELRelativeAxisButtons" "4 5"
	Option "HWHEELRelativeAxisButtons" "7 6"
#Option "SendCoreEvents" "true"
	Option		"Emulate3Buttons"	"true"
	Option "Buttons" "9"
	Option "ButtonMapping" "1 2 3 6 7 8 9"
EndSection
```

EDIT: I also tried with option "Name" = "Logitech..." and X failed to start.

---

### Post by theoldgit on 2007-01-09
I tried the section on setting the resolution to 800 dpi and that worked fine but when i followed the instructions for that to happen in boot nothing happened ie it did not set the resolution to 800 dpi on boot. Where do i start to get this working. 
 many thanks

---

### Post by demandred87 on 2007-01-14
Just wanted to give a big thank you to [detyabozhye]("http://www.ubuntuforums.org/member.php?u=45177"). I could never get this to work Pre-Edgy. Makes a huge difference when surfing the web.

Cheers.

---

### Post by detyabozhye on 2007-01-16
Aw Thanks and you're welcome. The guide does need a bit of a rewrite since there is a bit of a more elegant way of getting it working in Edgy, but I can't find the time to rewrite it yet.

---

### Post by jhr79 on 2007-01-20
Hi!

By following several guides I have got my Logitech Mediaplay to work somehow. I'm now able to use scroll wheel to scroll both vertically and horizontally. But I can't get the media keys to work whatever I have tried.

All buttons work when testing with xev, but I'm not able to set the keyboard shortcuts in Gnome. When I select ie. "Volume down" and try to assign new shortcut it just reverts to the original when I press the corresponding mouse button. 

Any tips?

----
My current configuration is 

xorg.conf
```
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "evdev"
        Option      "CorePointer"
        Option      "Device" "/dev/input/event9"
        Option      "ZAxisMapping" "6 7 4 5"
        Option      "Buttons" "7"
EndSection
```

.Xmodmap
```
pointer = 1 2 3 4 5 7 6
```

---

### Post by detyabozhye on 2007-01-20
You gotta do something like this in your .Xmodmap as well:

```
keycode 129 = XF86Eject
```

replace the '129' with what xev gives you and 'XF86Eject' with the right key name (you can check it out on Google, I'm in a hurry, ATM).

---

### Post by jhr79 on 2007-01-21
> **detyabozhye said:**
> You gotta do something like this in your .Xmodmap as well:

```
keycode 129 = XF86Eject
```

replace the '129' with what xev gives you and 'XF86Eject' with the right key name (you can check it out on Google, I'm in a hurry, ATM).

Well, I read something like this but where do I get these codes? When pushing eg. Play-button xev shows:

```
ButtonPress event, serial 26, synthetic NO, window 0x3000001,
    root 0x76, subw 0x0, time 1125109028, (53,155), root:(63,228),
    state 0x0, button 17, same_screen YES

ButtonRelease event, serial 26, synthetic NO, window 0x3000001,
    root 0x76, subw 0x0, time 1125109156, (53,155), root:(63,228),
    state 0x0, button 17, same_screen YES

```

So the problem is that where's the code?

---

### Post by luketheduck on 2007-01-22
Hi there, firstly thanks for the guide, found it excellent for setting up my MX700 on my laptop.

I have a query though, becuase I only use my MX700 at home, when I logged on to my laptop at work this morning obviously the configuration was invalid as I don't have that mouse plugged in, and I had to revert to my backup of xorg.conf from the console

Is there any way to configure things so that I can load the MX700 settings when I'm at home, and not load them when I'm elsewhere?

---

### Post by detyabozhye on 2007-01-23
Try putting back your old mouse config along with the new one (make sure the names of the mice are different though though and make sure they're both in the serverlayout section) and changing Option "CorePointer" to Option "SendCoreEvents" "True" in the new mouse config.

---

### Post by bartman on 2007-01-24
Yeah.

This is how my xorg.conf looks like:```
Section "ServerLayout"
        ...
        InputDevice    "Synaptics Touchpad" "AlwaysCore"
        InputDevice    "Logitech Mouse"
        InputDevice    "Configured Mouse"
EndSection
        ...
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "Emulate3Buttons" "true"
        Option      "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
        Identifier  "Logitech Mouse"
        Driver      "evdev"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/input/event8"
EndSection

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
#config by user roots of Ubuntu forums
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
        Option      "MaxSpeed" "0.18"
        Option      "AccelFactor" "0.0015"
        Option      "SHMConfig" "on"
        Option      "HorizScrollDelta" "0"
EndSection
```

It works with the configurations I tried:
* touchpad only / no external mouse
* touchpad + logitech mouse

---

### Post by bg1256 on 2007-01-31
I followed this guide several months ago, and it worked on Edgy flawlessly.  However, I did a fresh edgy install, and now I'm running into problems.

First, X is crashing once I edit the xorg file.  I have event4-9 open, and I've tried all of them with no success.

Second, when I run ```
sudo apt-get install xvkbd xbindkeys
```, I get this:

```
ben@BG-Desktop:~$ sudo apt-get install xvkbd xbindkeys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xvkbd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xvkbd has no installation candidate

```

I'd love to get this working again, but I'm unsure what to do.  It seems strange to me because it worked perfectly the first time around on Edgy, and no it's not working at all.

Thanks for any help in advance.

---

### Post by tweedledee on 2007-02-01
> **bg1256 said:**
> Thanks for any help in advance.

Make sure you have the universe & multiverse repositories enabled (in /etc/sources.lst or via synaptic).

---

### Post by bg1256 on 2007-02-04
Yes, I do have all the repositories enabled.  This seems very strange to me... I've not seen anything like this before.

---

### Post by Nikron on 2007-02-05
> **Filiprino said:**
> Hello! :D
First of all, I have a combo of keyboard and mouse, both wireless, model MX 3200 from Logitech, and I finally got the mouse working with udev and some tweaks on the xorg.conf.
My udev rule is (19-local.rules):
```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver",SYSFS{../device/bInterfaceNumber}=="01", NAME="input/event9"
```
Now, let's see the xorg.conf. First, I added a line on the section modules, in order to load "evdev" (as stated in de man page of evdev):
```
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	**Load	"evdev"**
EndSection
```
Then, I modified the input device for the mouse:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"			"Logitech USB Receiver"
	Option		"Phys"			"usb-0000:00:02.1-1/input1"
	Option		"Device"		"/dev/input/event9"
	Option		"AbsoluteScreen"	"0"
	#Option		"Protocol"		"ExplorerPS/2"
	#Option		"ZAxisMapping"		"4 5"
	#Option		"Emulate3Buttons"	"true"
EndSection
```
--etc--
.


Worked perfectly with my LX3 Optical Mouse on Edgy for the first section.  Thanks for the guide.  I was wondering ifyou can set xbindkeys to be less touchy.  IE, slighting hitting my the forward button will send me forward a page, but if I touch too long it'll blast me all the way forward. Also on edgy you can do

```
sudo apt-get install lomoco
```

Thanks for the guide and any future help.

---

### Post by dfm21 on 2007-02-06
Thank you, detyabozhye!
Works like a charm for my MX310.

---

### Post by LycoLoco on 2007-02-09
*post deleted - started a separate thread for help*

---

### Post by daou on 2007-02-09
> Worked perfectly with my LX3 Optical Mouse on Edgy for the first section. Thanks for the guide. I was wondering ifyou can set xbindkeys to be less touchy. IE, slighting hitting my the forward button will send me forward a page, but if I touch too long it'll blast me all the way forward. 

If you are using xvkbd in an xbindkeys rule, you can set xvkbd's repeat delays etc. The xvkbd manual tells you how to do it.

---

### Post by nibsa1242 on 2007-02-12
This worked great on my Mx518 in edgy.  I only needed to do section 1. The side buttons magically worked as forward and back buttons automatically after doing section one, and since there is no cruise control on the 518 I ignored that section (and I prefer my + and - buttons to change resolution on the fly anyway... very useful in GIMP and gaming). I would like to be able to do something with the application switcher button, and the click wheel button. For now I'm happy with my back and forward buttons though.

---

### Post by A-1337 on 2007-02-13
Big thanks, detyabozhye!

---

### Post by bg1256 on 2007-02-14
I have a Logitech MX500 that worked flawlessly after following this guide, but after a fresh install (and kernel upgrade) it doesn't seem to be working.

edit: I'm running Edgy/Gnome

For clarity's sake, before I follow this guide, my mouse works, but the side buttons do not work.

I'll post as much information as I can.

```
cat /proc/bus/input/devices
```

yields

```
I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c025 Version=9802
N: Name="B16_b_02 USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:1d.1-2/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0 
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0003 Vendor=046d Product=c509 Version=1904
N: Name="**Logitech USB Receiver**"
P: Phys=usb-0000:00:1d.0-2/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c509 Version=1904
N: Name="**Logitech USB Receiver**"
P: Phys=usb-0000:00:1d.0-2/input1
S: Sysfs=/class/input/input3
H: Handlers=kbd mouse1 event3 ts1 
B: EV=7
B: KEY=1fffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff 0 0 3878 d801d101 1e0000 0 0 0
B: REL=103

```

Hence, my local rules would look like this:

```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Reciever", NAME="input/event9"
```

event 9 is available, and I've tried several different available events.

However, the problem seems to be with editing the xorg file.

If my xorg file looks like this:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/event9" 
EndSection
```

my mouse doesn't respond at all.

Would I be able to follow section 2 without section 1 working, if my mouse is already working without it?  Or is section 2 dependent on section 1?

---

### Post by bartman on 2007-02-14
I'm noticing the same symptoms. They appear to have started after my dapper->edgy or the recent X.org upgrade.

---

### Post by bg1256 on 2007-02-14
Well, I had success on Edgy in the past, so I don't think that is the problem.  Perhaps the recent updates to xorg are the suspect?

---

### Post by detyabozhye on 2007-02-14
The wireless mice need a bit different setup which I don't remember for sure how to do. It's somewhere in this thread, try searching this thread for "Logitech USB Reciever"

---

### Post by bg1256 on 2007-02-14
it's actually not wireless...:confused:

---

### Post by daou on 2007-02-15
The [MX/VX Revolution howto]("http://www.ubuntuforums.org/showthread.php?t=277388") tells you how to get around the problem with two "Logitech USB Receiver" fields. 

You need to make the udev rule look something like this:

```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", SYSFS{../phys}=="**usb-0000:00:1d.0-2/input1**", NAME="input/event9"
```

You need to replace the bold part with your USB location for the device that shows up in cat /proc/bus/input/devices with a "mouse" in its handlers section. I used the one bg1256 gave in his /proc/bus/input/devices.

---

### Post by bg1256 on 2007-02-16
Hmmm... changing the udev rule doesn't seem to make a difference.  I'll explore the thread you posted to see if anyone else is having a problem similar to mine.

edit: just so I'm clear, everything on the mouse works before I follow this guide except the back / forward buttons.

But, once I edit the evdev rule, the mouse does not function at all.  And I had this all working one time before, but after a fresh install of Edgy, it doesn't work...

---

### Post by sinlimites on 2007-02-17
I have a problem and i cant find in this large post.

I have a laptop with a mx500, and if i start the computer without mx500 the X doesnt starts. How i can solve it?

Thanks!!!!!

---

### Post by detyabozhye on 2007-02-17
> **sinlimites said:**
> I have a problem and i cant find in this large post.

I have a laptop with a mx500, and if i start the computer without mx500 the X doesnt starts. How i can solve it?

Thanks!!!!!

Change back to the original mouse configuration, add another mouse with a different name (eg. "LogitechMX500") using the configuration I posted here, add the name to the server layout under the first mouse, and change:

Option "CorePointer"

to:

Option "SendCoreEvents" "True"

If you need any more details, try searching the thread for "SendCoreEvents"

---

### Post by DanaG on 2007-02-26
I don't remember whether this was for Dapper or Edgy, but here's my xorg.conf.  Note that my evdev listing uses device by name: "Logitech *"  -- so it will get "USB-PS/2 Optical Mouse" AND "USB Receiver" if any are attached.  It also leaves the USB mouse hot-swappable!

Argh. xorg.conf: invalid file

---

### Post by johntelthorst on 2007-03-24
This worked fine for me in Edgy, but now that I've clean-installed the Feisty Beta, it doesn't work for me.  I went through the process step by step and double checked everything, but it doesn't work.  Has anyone else been able to get this to work in Feisty?

---

### Post by smileysmoke on 2007-03-28
i had to register just to say thanks mate! :D works like a charm on Edgy 6.10. feels so smooth.. smoother than the bad old days of windoze! :P
thanks again!

---

### Post by spockrock on 2007-03-28
> **johntelthorst said:**
> This worked fine for me in Edgy, but now that I've clean-installed the Feisty Beta, it doesn't work for me.  I went through the process step by step and double checked everything, but it doesn't work.  Has anyone else been able to get this to work in Feisty?

yeah I am experiencing the same it just does not work in feisty beta.

---

### Post by -Chi.0 on 2007-04-02
```
"/usr/bin/xvkbd -xsendevent -text "\[Shift_L]\[Control_L]\[Tab]""
  m:0x0 + b:6

```

Is this the correct way i should be doing this? The effect that i am trying to get is to use Ctrl + Tab to move cycle forward true my tabs & Ctrl + Shift + Tab to cycle backwords true the tabs. I can get Ctrl + Tab to work w/ this 

```
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Tab]""
  m:0x0 + b:7

```

But the 1st code does not work. Am i doing something wrong?](*,)

---

### Post by sudo_t43p on 2007-04-02
> **spockrock said:**
> yeah I am experiencing the same it just does not work in feisty beta.

I got it working with MX1000 bluetooth (from diNovo desktop). But now when I´m useing MX1000 RF I can´t get the tilt wheel working. If I run xev and push tilt wheel I get no "button" only:

```

KeyRelease event, serial 29, synthetic NO, window 0x3e00001,
    root 0x75, subw 0x0, time 14483532, (167,-9), root:(179,85),
    state 0x0, keycode 123 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

Tried to map tilt wheel with c:123 and c:122 but it lags and is behaving very strange. Someone else with no button in xev?

here is my .xbindkeysrc

```

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:7
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Tab]""
  b:11
"/usr/bin/xvkbd -xsendevent -text "\[Control_R]\[ISO_Left_Tab]""
  b:12
"/usr/bin/xvkbd -xsendevent -text "\[Control_R]\[w]""
  b:2
"echo ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
  b:11
"echo ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
  b:12
"echo ButtonPress 6 ButtonRelease 6 | xmacroplay -d 0 :0.0"
  b:13
"echo ButtonPress 7 ButtonRelease 7 | xmacroplay -d 0 :0.0"
  b:14

```

---

### Post by detyabozhye on 2007-04-03
> **-Chi.0 said:**
> ```
"/usr/bin/xvkbd -xsendevent -text "\[Shift_L]\[Control_L]\[Tab]""
  m:0x0 + b:6

```

Is this the correct way i should be doing this? The effect that i am trying to get is to use Ctrl + Tab to move cycle forward true my tabs & Ctrl + Shift + Tab to cycle backwords true the tabs. I can get Ctrl + Tab to work w/ this 

```
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Tab]""
  m:0x0 + b:7

```

But the 1st code does not work. Am i doing something wrong?](*,)

I can't really say since I don't know too much about xbindkeys.

---

### Post by detyabozhye on 2007-04-03
> **sudo_t43p said:**
> I got it working with MX1000 bluetooth (from diNovo desktop). But now when I´m useing MX1000 RF I can´t get the tilt wheel working. If I run xev and push tilt wheel I get no "button" only:

```

KeyRelease event, serial 29, synthetic NO, window 0x3e00001,
    root 0x75, subw 0x0, time 14483532, (167,-9), root:(179,85),
    state 0x0, keycode 123 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

Tried to map tilt wheel with c:123 and c:122 but it lags and is behaving very strange. Someone else with no button in xev?

here is my .xbindkeysrc

```

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:7
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Tab]""
  b:11
"/usr/bin/xvkbd -xsendevent -text "\[Control_R]\[ISO_Left_Tab]""
  b:12
"/usr/bin/xvkbd -xsendevent -text "\[Control_R]\[w]""
  b:2
"echo ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
  b:11
"echo ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
  b:12
"echo ButtonPress 6 ButtonRelease 6 | xmacroplay -d 0 :0.0"
  b:13
"echo ButtonPress 7 ButtonRelease 7 | xmacroplay -d 0 :0.0"
  b:14

```

Try it with xbindkeys turned off. Then change your .xbindkeysrc to not have anything for the tilt wheel buttons (if you want them to scroll horizontally).

---

### Post by spockrock on 2007-04-04
> **sudo_t43p said:**
> I got it working with MX1000 bluetooth (from diNovo desktop). But now when I´m useing MX1000 RF I can´t get the tilt wheel working. If I run xev and push tilt wheel I get no "button" only:

```

KeyRelease event, serial 29, synthetic NO, window 0x3e00001,
    root 0x75, subw 0x0, time 14483532, (167,-9), root:(179,85),
    state 0x0, keycode 123 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

Tried to map tilt wheel with c:123 and c:122 but it lags and is behaving very strange. Someone else with no button in xev?

here is my .xbindkeysrc

```

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:7
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Tab]""
  b:11
"/usr/bin/xvkbd -xsendevent -text "\[Control_R]\[ISO_Left_Tab]""
  b:12
"/usr/bin/xvkbd -xsendevent -text "\[Control_R]\[w]""
  b:2
"echo ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
  b:11
"echo ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
  b:12
"echo ButtonPress 6 ButtonRelease 6 | xmacroplay -d 0 :0.0"
  b:13
"echo ButtonPress 7 ButtonRelease 7 | xmacroplay -d 0 :0.0"
  b:14

```

Can I ask what you did and what your xorg.conf looks like, mine just refuses to work, its only the app tab button and the horizontal scrolls that do not work.....

---

### Post by sudo_t43p on 2007-04-05
> **detyabozhye said:**
> I can't really say since I don't know too much about xbindkeys.

Try with **[Control_R]\[ISO_Left_Tab]** or [Control_R]\[Pagedown]

BR,
Chrisse

---

### Post by sudo_t43p on 2007-04-05
> **spockrock said:**
> Can I ask what you did and what your xorg.conf looks like, mine just refuses to work, its only the app tab button and the horizontal scrolls that do not work.....

Don´t have my xorg left from testing this mouse  (messing arround with lots of stuff at the moment).

But if you could post the most relevant stuff from xev I can try to help you.

---

### Post by antiplex on 2007-04-08
hi folks!

after spending hours on getting my logitech mx5000 desktop-set (mouse & keyboard) both working without deactivating the keyboards media-keys i finally got almost everything going (using feisty beta!) that i wanted, so thanks for all the hints that came along in the original howto as well as in many of the postings of the preceding 43 pages (that was a lot to read!).

in _[posting #368]("http://ubuntuforums.org/showpost.php?p=1930766&postcount=368")_  user 'kobewan' recommended using 'xte' (can be found in the 'xautomation'-package) because it should handle keypress and releasevents better than 'xvfz'.
i don't doubt that this is correct but still have some problems getting things to work. what i try to do is to trigger my compiz-expose-plugin which currently is configured to use the key kombination of 'keydown Contol_L' + 'keydown Alt_L' + 'key Up' with mousebutton #10 of my logitech mx1000 bluetooth mouse. when using a keyboard, as soon as you release any of the still pressed 'Control_L' or 'Alt_L' keys, the expose-function will end.

so basically what kobewan posted sounds like it might be what i'm looking for, right? (... because some keys need to remain pressed for a while)
this is my current ~/.xbindkeysrc: ```
#button10 testing
"/usr/bin/xte 'keydown Control_L' 'keydown Alt_L' 'key Up' &"
 b:10

# workaround for releasing btn10
".btn10rel.sh &" 
 b:10 + Release

```
as you can see, i call a script (that of couse i made executable already) called '.btn10rel.sh' which has the following content:```
#!/bin/bash
#
  /usr/bin/xte 'keyup Alt_L' 'keyup Control_L'
```

when i check button10 with 'xev' without haveing 'xbindkeys' running it seems to work fine because what i get is: ```
ButtonPress event, serial 28, synthetic NO, window 0x3000001,
    root 0x52, subw 0x0, time 3558958910, (88,66), root:(100,140),
    state 0x0, button 10, same_screen YES

ButtonRelease event, serial 28, synthetic NO, window 0x3000001,
    root 0x52, subw 0x0, time 3558960073, (88,66), root:(100,140),
    state 0x0, button 10, same_screen YES

```now when i start 'xbindkeys' and run 'xev' again, this is what i get when pressing button10:```
KeyPress event, serial 31, synthetic NO, window 0x3000001,
    root 0x52, subw 0x0, time 3559859591, (130,123), root:(165,203),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 31, synthetic NO, window 0x3000001,
    root 0x52, subw 0x0, time 3559859592, (130,123), root:(165,203),
    state 0x4, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 31, synthetic NO, window 0x3000001,
    mode NotifyGrab, detail NotifyAncestor

FocusOut event, serial 31, synthetic NO, window 0x3000001,
    mode NotifyUngrab, detail NotifyPointer

FocusIn event, serial 31, synthetic NO, window 0x3000001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  1   0   0   0   32  0   0   0   1   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
``` and this when releasing it:```
EnterNotify event, serial 31, synthetic NO, window 0x3000001,
    root 0x52, subw 0x0, time 3559863870, (130,123), root:(165,203),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 12

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  82  0   0   0   32  0   0   0   1   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
```all that i can see from this is that 'Control_L' and 'Alt_L' seem to get (fake-)pressed correctly, but 'Up' or everything written to my script probably never gets (fake-)pressed which is exactly what i recognize on my desktop. what i mean is: when i press button10, nothing happens (since 'Up' seems to be missing), and after releasing button 10 'Control_L' and 'Alt_L' remain pressed until i manually press them.

the script is in my homedir, is this correct?
any ideas how to get this working?

---

### Post by detyabozhye on 2007-04-09
Yes, it should be in your home dir. A lot of the xbindkeys, kvkbd, and xte stuff is a bit over my head though, so I don't really knoe about the rest.

---

### Post by antiplex on 2007-04-10
i thought that maybe 'kobewan' could help, i already pm'ed and informed him about my previous posting.
however, i guess i solved my problem in a different way by switching from compiz to beryl where the expose-function seems to bind mousclicks in a more ... let's say logitech-friendly way. scrolling left/right works fine with xbindkeys... so everything's fine for the moment :)

---

### Post by tweedledee on 2007-04-10
> **antiplex said:**
> i thought that maybe 'kobewan' could help, i already pm'ed and informed him about my previous posting.
however, i guess i solved my problem in a different way by switching from compiz to beryl where the expose-function seems to bind mousclicks in a more ... let's say logitech-friendly way. scrolling left/right works fine with xbindkeys... so everything's fine for the moment :)

The problem with the approach you were trying is discussed at various points in another thread ([http://ubuntuforums.org/showthread.php?t=316441)](http://ubuntuforums.org/showthread.php?t=316441)), but the gist of it is that xbindkeys doesn't properly handle attempts to attach a script/function to both the press & release of a mouse button (in fact, it's much more reliable when bound to the release).  So while what you described makes sense, it won't work.  Your workaround seems to be a better solution for you.

---

### Post by dpb on 2007-04-16
Followed these how-to instructions on Edgy, and ran into a couple problems.  I was wondering if anyone could help?  Basically I'm getting the following in my Xorg log file:

```
(II) MX Rev-usb-0000:00:1d.2-2/input0: Init
(II) evdev brain: Rescanning devices (2).
(II) MX Rev-usb-0000:00:1d.2-2/input0: On
(II) MX Rev-usb-0000:00:1d.2-2/input0: Off
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "1600x1200,1600x1200"
(II) MX Rev-usb-0000:00:1d.2-2/input0: On
(II) evdev brain: Rescanning devices (3).
(II) MX Rev-usb-0000:00:1d.2-2/input0: Off
(II) MX Rev-usb-0000:00:1d.2-2/input0: Off
```

Looks like the thing is being recognized, but immediately turning off.  When I get up into X11, the mouse simply "doesn't work".

Any suggestions?

-D

---

### Post by BLTicklemonster on 2007-04-22
Fiesty's last upgrade had a new xorg or xorg.conf or something, and of course, seeing as how it was an upgrade, no, X would not load. So, I installed my nvidia drivers for the gazillionth time, thank you Ubuntu update writers for not figuring out how to make an upgrade put anyone's video drivers right (what good is a computer upgrade if it renders the computer useless until fiddled with). Of course every time I reboot now, x dies. Huh. Never had this problem before, so today I installed the driver and before starting x, I dpkg-reconfigure xserver-xorg, and guess what? There's a new section in there with mouse info. If you answer it ok all the way assuming that's correct, bam, my logitech mx 310 doesn't work. No scroll, no forward back buttons, nothing.

I have yet to fix this, and I've been working on it all evening.


Good God, they come out with the best Ubuntu version ever, and immediately dweeb it out.

Yay.

(certainly there's a fix on the horizon, but I'm thinking I'm going to drop feisty and go back to edgy if I can't find a fix for the mouse and the video drivers.)

*edit: 

Aw great, my logout screen is gone now, too.

WTF?

---

### Post by bg1256 on 2007-04-22
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

As for nvidia, here's what I did:

```
sudo apt-get install linux-restricted-modules 'uname -r'
sudo apt-get update
sudo apt-get install nvidia-glx-new
```

And apparently, some people need to:
```
sudo nvidia-glx-config enable
```

Hope it helps... for what it's worth, this guide hasn't worked for me since Dapper...oh well.

---

### Post by BLTicklemonster on 2007-04-22
For nvidia, this is what worked for me:

> **silencio said:**
> 

```

nano /etc/default/linux-restricted-modules-common

```

and add the following line to the file

```

DISABLED_MODULES="nv nvidia"

```

This solution should work when you upgrade the packages next time.


as far as the mouse, you think that dpkg will work?

---

### Post by bg1256 on 2007-04-22
dpkg should recofigure your mouse and at least get it working... though it won't get your side buttons working again.

---

### Post by detyabozhye on 2007-04-23
I haven't been keeping up with the developement of evdev, and I know of at least one better way this can be done in Edgy, but I just haven't had the time to figure out Feisty's package and update the guide. If someone could continue my work to make a Feisty guide, that'd be nice.

All I can say for now is that you can configure it without the udev rule (which makes life a lot easier) by using either Phys or Dev Phys and Name options in xorg.conf. I can't write a full blown updated guide right now though, sorry guys.

All I can say though is that this has been working after the upgrade for me though even though it's a little outdated.

---

### Post by BLTicklemonster on 2007-04-23
My problem is basically that I have 7 buttons, 6 and 7 are my side buttons, forward and back, and they show up as 2 and 3 in xev. I used to have a link in favorites to the old thread about logitech mouses where I explained how to get those to act right, but for some reason, the thread is gone. All I need is for those two to be set right and I'm good. But I can't remember how to do it.

---

### Post by inf0c0m on 2007-04-25
> **BLTicklemonster said:**
> My problem is basically that I have 7 buttons, 6 and 7 are my side buttons, forward and back, and they show up as 2 and 3 in xev. I used to have a link in favorites to the old thread about logitech mouses where I explained how to get those to act right, but for some reason, the thread is gone. All I need is for those two to be set right and I'm good. But I can't remember how to do it.

i believe im having the same issue you are in feisty. my side buttons are acting as scroll up and down, and my wheel is acting as back and forth...any help would be much appreciated!

---

### Post by detyabozhye on 2007-04-26
> **inf0c0m said:**
> i believe im having the same issue you are in feisty. my side buttons are acting as scroll up and down, and my wheel is acting as back and forth...any help would be much appreciated!

Do you have a .Xmodmap file in your home directory? If so, try and see what xev outputs if you rename the file (for backup) (requires a restart of X).

---

### Post by techstop on 2007-04-28
> **BLTicklemonster said:**
> My problem is basically that I have 7 buttons, 6 and 7 are my side buttons, forward and back, and they show up as 2 and 3 in xev. I used to have a link in favorites to the old thread about logitech mouses where I explained how to get those to act right, but for some reason, the thread is gone. All I need is for those two to be set right and I'm good. But I can't remember how to do it.

I had exactly the same problem. I had the forward / back buttons working in edgy, but a fresh install to feisty broke it, with the result that the side buttons showed as 2 and 3 in xev, just like you. After much scrutiny of my backup of xorg.conf frome edgy, I realised that my MX600 had somehow been installed as a different device. 

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection
```

That is my working xorg.conf. The line that says;

```
Option         "Protocol" "ExplorerPS/2"
```

was previously;

```
Option         "Protocol" "ImPS/2"
```

Have a look and see if yours is the same? :confused:

---

### Post by fisofo on 2007-04-29
I've had an issue in 7.04 with X Server randomly crashing at startup, but then sometimes randomly working.

After many hours of searching, (Sorry, I'm a noob at this still) I think I finally found that the issue is tied in with my mouse/keyboard combo.  I have a Logitech MX Duo (shows up as Logitech USB Receiver in devices).

When things go fine, the relevant section in my Xorg.0.log looks like:
```
(II) evdev brain: Rescanning devices (1).
(**) Option "CorePointer"
(**) Configured Mouse-usb-0000:00:1d.1-1/input1: Core Pointer
(II) Configured Mouse-usb-0000:00:1d.1-1/input1: Found 3 relative axes.
```
When it crashes, I instead get this:
```
(II) evdev brain: Rescanning devices (1).
(**) Option "CorePointer"
(**) Configured Mouse-usb-0000:00:1d.1-1/input0: Core Pointer
(WW) Configured Mouse-usb-0000:00:1d.1-1/input0: does not have core pointer capabilities
(WW) <default pointer>: No Device specified, looking for one...
(II) <default pointer>: Setting Device option to "/dev/input/mice"
```

Not only that, but none of the media keys work... aka, they don't even report the scancode or whatever it's called in a terminal.

So... what do I do?  I was thinking the answer might lie in the guide regarding this line:
```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", NAME="input/event9"
```
Can this be modified to more specifically select just the MX 700 mouse?  Can I match the Handlers of the device, or perhaps the EV/KEY/REL/LED fields?  And how?
Perhaps that would prevent the crashing and allow me to use media keys?

Thanks guys!

---

### Post by nullcore on 2007-04-29
you're a lifesaver.  having finally jumped ship to open source utopia, this has been one of my major irritants in ubuntu for the past week.  using that back button is like an extension of my thumb.  this worked fantastic for me in feisty.  i couldn't even tell you the mouse model number.  it's not on logitech's site, and if it had a model number on the bottom, it's been rubbed away.  luckily, i ended up here, and viola!  mouse satisfaction.

cheers to you.  great guide.

---

### Post by sandman55 on 2007-04-29
I tried this Guide for my MX500 and my xorg.conf bombed out (I think it was something I did wrong dont remember) and after trying all sorts of guides I came back here and very carefully followed the guide (Feisty already has evdev) I went as far as doing my xorg.conf and hey presto everything works including my side mouse buttons. Thanks detyabozhye.:guitar:

---

### Post by Braese on 2007-04-30
Great Howto, works in Feisty for me and my MX518. But how can i disable the DPI Switch Buttons? In Xen when i press the 2 Buttons there is no Number or Action. Please Help! ;)

---

### Post by detyabozhye on 2007-04-30
> **Braese said:**
> Great Howto, works in Feisty for me and my MX518. But how can i disable the DPI Switch Buttons? In Xen when i press the 2 Buttons there is no Number or Action. Please Help! ;)

If you have lomoco installed, you can try sudo lomoco --no-sms or sudo lomoco --sms and see if that helps.

---

### Post by fisofo on 2007-05-01
detyabozhye, I can certainly post elsewhere if it would be better, but I don't suppose you have any ideas from my question the other day, do you?  Your guide worked great for me in 6.10 btw!

Perhaps just point me in the right direction?

---

### Post by detyabozhye on 2007-05-01
I don't remember exactly where, but there is another thing you should add to the udev rule (if you're using udev for this, there's a better way to do it but I haven't tried it yet) to make it not confuse the mouse with the keyboard, it is somewhere in this thread, but I can't remember exactly what to search for at the moment. As for the media keys not working, it's a bug in the kernel drivers when running the keyboard on USB, AFAIK. I really need to make a new updated guide for Edgy and Feisty, but I just can't find the time, sorry. >_<

---

### Post by fisofo on 2007-05-01
No problem... now at least I know where to look, thanks for responding!

---

### Post by xi_Slick_ix on 2007-05-04
Cordless mouse - Logitech Cordless Click*!* Optical Mouse  (two AA batteries for power, USB receiver for connection)

Has one extra button besides the typical 2 + the scroll/click  -  serves to switch between windows (basically the alt + tab command in windows without the keyboard interaction)

Its a lower mouse on the logitech food chain - any ideas?

---

### Post by SigmundFreud on 2007-05-04
I have a cordless click as well. I don't believe there's a way to get that window-switch button to do what it should (or am I wrong?).

---

### Post by detyabozhye on 2007-05-04
What do you get in xev when pressing the buttons (includes scrolling)?

You should get:
left click = 1
middle click = 2
right click = 3
scroll up = 4
scroll down = 5
extra button = 6 or some other number

---

### Post by trmiv on 2007-05-06
I tried this guide in Feisty with my mx510.  It works perfectly for the forward and back buttons, however I cannot get it to work for the cruise buttons.

---

### Post by NTolerance on 2007-05-07
> **trmiv said:**
> I tried this guide in Feisty with my mx510.  It works perfectly for the forward and back buttons, however I cannot get it to work for the cruise buttons.

Same here.  I'm running Feisty and the cruise buttons on my MX518 aren't picked up by xev.

I read this on the lomoco site:

> Hint 2: on Linux, the usbmouse driver ignores the extra buttons altogether. Don't let it handle your Logitech mice -- use the generic hid driver for USB HID devices instead.

Does anyone know which driver this guide uses?

---

### Post by trmiv on 2007-05-07
> **NTolerance said:**
> Same here.  I'm running Feisty and the cruise buttons on my MX518 aren't picked up by xev.

I read this on the lomoco site:



Does anyone know which driver this guide uses?

Figured it out.  Add "--sms" to the end of the line that you use to set the resolution with lomoco and it works!

---

### Post by NTolerance on 2007-05-07
> **trmiv said:**
> Figured it out.  Add "--sms" to the end of the line that you use to set the resolution with lomoco and it works!

Tried that.  lomoco exits with no terminal output and does not appear as a running process according to ps.  Cruise buttons still do not register in xev.  Can you please post all relevant config files and your lomoco syntax?  Thanks.

---

### Post by trmiv on 2007-05-07
> **NTolerance said:**
> Tried that.  lomoco exits with no terminal output and does not appear as a running process according to ps.  Cruise buttons still do not register in xev.  Can you please post all relevant config files and your lomoco syntax?  Thanks.

I followed the guide from the first page where it details how to set the resolution.  But instead of just the line to set the resolution, mine looks like this:


```
lomoco -8 --sms
```

---

### Post by NTolerance on 2007-05-07
> **trmiv said:**
> I followed the guide from the first page where it details how to set the resolution.  But instead of just the line to set the resolution, mine looks like this:


```
lomoco -8 --sms
```

OK thanks, I'll give that a try.  But I fear that the MX518 is "special" due to the cruise buttons changing the mouse sensitivity by default regardless of what driver is loaded.  Does anyone know how to overcome this?  I bought the MX518 for its high resolution, but the sensitivity change feature drives me mad.

Edit:  Didn't work.  Looks like I'm hosed.

---

### Post by detyabozhye on 2007-05-07
> **NTolerance said:**
> Does anyone know which driver this guide uses?

It uses the evdev driver.

---

### Post by NTolerance on 2007-05-07
> **detyabozhye said:**
> It uses the evdev driver.

Looks like neither evdev nor lomoco are currently capable of utilizing the sensitivity buttons on the MX518.  :mad:

---

### Post by detyabozhye on 2007-05-07
lomoco only communicates with the mouse to change resolution or behavior of the cruise buttons, while evdev is the input driver which translates the mouse's events into the pointer moving accross the screen and all that. In other words, lomoco is output, evdev is input for the mouse, so they can work together.

---

### Post by Bart Simpson 18 on 2007-05-10
hi guys,

I need your help. 

My problem is, that when I try to write the **evdev driver** into the xorg.conf my Ubuntu 7.04 Feisty **doesn't boot up.** I get only black screen without the option to CTRL ALT F1. Nothing seems to work then.

I already tried to solve the problem with the help of my Ubuntu Forum collegue [COLOR="Red"]Paradoxdruid[/COLOR] [COLOR="Red"]**[here]("http://ubuntuforums.org/showthread.php?p=2621411#post2621411")**[/COLOR] but nothing seems to work.

**How can I get the evdev driver enabled in the xorg.conf working?**

My system specs
Dell Precision M90
2.33 GHz
2048 MB Ram
QuadroFX 3500M

thx a lot :KS

---

### Post by c.dric on 2007-05-10
thanks for the great how-to.

i got one question: i have a the LX5 mouse which has a resolution of 1100dpi
should i use lomoco and if so which resolution should i use ? 
the man page only mentions 800 or 1200dpi

thanks once again.

---

### Post by fanatik on 2007-05-11
Thanks to detyabozhye and this guide, I got my media center keyboard with built in trackball working perfectly :)

for reference here's my config:

```
$ cat /proc/bus/input/devices

I: Bus=0003 Vendor=062a Product=0205 Version=0110
N: Name="MOSART Semi. 2.4G Media Center Keyboard"
P: Phys=usb-0000:00:03.1-3/input0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3
B: EV=120003
B: KEY=10000 7 ff87207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: LED=7

I: Bus=0003 Vendor=062a Product=0205 Version=0110
N: Name="MOSART Semi. 2.4G Media Center Keyboard"
P: Phys=usb-0000:00:03.1-3/input1
S: Sysfs=/class/input/input4
H: Handlers=kbd mouse2 event4
B: EV=10000f
B: KEY=7fff 42c73b7 bf0d4440 0 0 1f0001 f84 8807c400 667bfa d971dfef 9e0040 0 0 0
B: REL=143
B: ABS=1 0
```

```
$ cat /etc/X11/xorg.conf  # well the relevant bits anyway...
Section "ServerLayout"
        Identifier     "single head configuration"
        Screen         0  "Screen0" 0 0
        InputDevice    "Configured Keyboard" "CoreKeyboard"
        InputDevice    "MCkeyboard"
        InputDevice    "Configured Mouse" "CorePointer"
        InputDevice    "MCtrackball"
EndSection

Section "InputDevice"
        Identifier  "MCkeyboard"
        Driver      "evdev"
        Option      "Name"            "MOSART Semi. 2.4G Media Center Keyboard"
        Option      "Phys"            "usb-0000:00:03.1-3/input0"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "gb"
        Option      "SendCoreEvents"  "true"
EndSection

Section "InputDevice"
        Identifier  "MCtrackball"
        Driver      "evdev"
        Option      "Name"            "MOSART Semi. 2.4G Media Center Keyboard"
        Option      "Phys"            "usb-0000:00:03.1-3/input1"
        Option      "AbsoluteScreen"  "0"
        Option      "SendCoreEvents"  "true"
EndSection

```

I have just got to configure the media keys now, but from reading all 46 pages of this thread I think it'll be quite straigtforward!! :)

---

### Post by trmiv on 2007-05-14
I followed this guide and got everything working, even did the last part with the resolution and got the resolution on my mx510 to 800 dpi.  I added --sms to end of that got my cruise buttons working.  I followed the part about making it start up automatically, and for awhile it worked.  Now suddenly over the past few days the lomoco command is not being run at startup and I have no idea why.  I reran the steps to make the /etc/init.d/local run at startup and I get the message:

```
System startup links for /etc/init.d/local already exist.
```

So it's setup to run at startup, but it's not.  Anyone have a clue why that would be?

---

### Post by MichiganMan on 2007-05-16
Used the guide with Feisty and a new mx400.  It worked quite well, including the all important side buttons (another big Thank You for the excellent guide) I just have a bit of a silly question about the resolution.  

The lomoco seems to be working, but I can't really say I notice a difference, which is to actually say I thought the mouse performed superbly before, and now it performs... superbly.  Is there a way to tell what resolution the mouse is set at?
Thank you for any help.

---

### Post by spockrock on 2007-05-18
ok so I have great news, I have my mx1000 working (sort of) with evdev, the only problem I have so far is that I have way too many buttons (not that its bad) but it recognizes all the buttons as individual buttons.  For example;

left click is 1
middle click is 2
right click is 3
wheel up is 4
wheel down is 5
back thumb is 6
forward thumb is 7
middle thumb buttons is 8
scroll (cruise) up is 9 
scroll (cruise) down is 10
horizontal scroll left is 11
horizontal scroll right is 12

the problem I am having is if in my xorg I set 	"HWHEELRelativeAxisButtons" "12 11", my horizontal scroll buttons become 13 and 14.  maybe I need to use a xodmap??

---

### Post by detyabozhye on 2007-05-18
@MichiganMan: Well, the mouse moves faster at a bigger resolution for me.

@spockrock: yeah, I think you should be able to fix it with xmodmap

---

### Post by MichiganMan on 2007-05-18
Thanks.  I've played with the command, switching, I think, between 400 and 800 cpi.  

But I'm wondering is the output I get from the command is right:  
```

sudo lomoco -8
002.002: 046d:c043 Unsupported Logitech device: USB-PS/2 Optical Mouse
```

Is this telling me that lomoco isn't working because my mx400 is unsupported?

---

### Post by detyabozhye on 2007-05-19
I think it just checks the name of the device and decides whether or not it's supported whether or not the mouse is actually capable. You might want to report a bug to the lomoco devs.

---

### Post by nullcore on 2007-05-20
ok, i have the mouse doing what i want it to, but now i'm having keyboard issues.  the media keys, which worked just fine previously, are now dead.  i have a linkysys wireless keyboard/mouse combo, one usb reciever, two peripherals.  the keyboard model number from the bottom seems to be "M/N: Y-RJ20."  i couldn't tell you the mouse model, as the info under there has long been scraped away from use, but it's a typical optical wireless mouse with a scroll wheel and a single back button.  the reciever's model is "M/N: C-BG-17-DUAL."  the keyboard functions fine as a standard no-frills deal, but i'd like to get my volume control and media player buttons back.  any help or a nudge in the right direction would be greatly appreciated.

my apologies if this has already been covered.  i couldn't find anything in the thread.  if i just happened to miss it, simply pointing me to the relevant page number would be great.

thanks in advance.

---

### Post by spockrock on 2007-05-21
hmmm this is strange but any changes I make to my .Xmodmap file does not change the buttons values, when I enter;
 xmodmap ~/.Xmodmap

the buttons stay the same, any suggestions??

---

### Post by daou on 2007-05-27
I just released btnx (Button Extension). It is a daemon that enables rerouting of mouse button events through uinput as keyboard and other mouse button combinations. This is especially useful for mice with more buttons than Gnome or KDE can properly handle, or mice that need evdev and a 100 step howto to register button events at all. No more pulling hairs with evdev, udev, xorg.conf, xvkbd, xbindkeys, and mousekeys. It has mouse auto-detection for supported mice.

Right now there is only support for:[LIST]
[*] Logitech MX Revolution
[*]Logitech VX Revolution
[*]Logitech G5
[*]Logitech MX-510[/LIST]I need hexdumps of event handlers to add support for other mice.

The installation and usage is described in the [COLOR=Blue][MX Revolution howto]("http://ubuntuforums.org/showthread.php?t=277388")[/COLOR]. The instructions for helping add support for other mice is found [COLOR=Blue][in this post]("http://ubuntuforums.org/showpost.php?p=2725453&postcount=101")[/COLOR]. Anyone with a mouse that has more than 2 buttons and a wheel can help. The instructions should be easy to follow.

The SVN repository for the project is located at [COLOR=Blue][http://svn.ollisalonen.com/btnx](http://svn.ollisalonen.com/btnx)[/COLOR]

Once people start sending in the needed info, I'll update [this list]("http://svn.ollisalonen.com/btnx/trunk/SUPPORTED_MICE") for mice that I will add support for. Make sure to check that list before helping so there won't be duplicate work. I will try adding support as soon as I can after getting the necessary info.

A big thanks to anyone who takes the time to help.

I've submitted a tutorial+tips thread on btnx. Once it's approved by the forum staff, all support and discussion of btnx will be moved there.

---

### Post by daou on 2007-05-28
The thread for btnx is now at [http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)

---

### Post by coppertrail on 2007-05-30
I have a Logitech MX-400 and went through all the steps in the first post.  The forward/back buttons don't work, but if I tilt the scroll wheel to the right, the page goes back.  A left tilt does a page forward.  I've tried changing the button values as specified in the first post to no avail.  Any thoughts?

---

### Post by Mighty_Pooh on 2007-05-31
I got it working - almost... My Mouse i Mx500
What i want to do is not to map the keys to back and forward.. 
I want to map them as aditional mousebuttons. 
Either as i did in windows by mapping the keys to F8 F9 F10 F11 and F12. 
I need the keys for World of Warcraft. 

Do any of you have any idea on how to map them to either mousebuttons or keyboard keys ?
Im using cedega and kde.

---

### Post by detyabozhye on 2007-05-31
If you don't use xbindkeys, they are already just mouse buttons. If you want to map them to existing mouse buttons (such as have two left clicks or two right clicks), you can use "click" in xbindkeys which is part of the tutorial. And to map it to keys, just change the:
```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[_R_ight]""
```
to something like:
```
"/usr/bin/xvkbd -xsendevent -text "\[F8]""
```

---

### Post by rogun on 2007-06-02
> **jhr79 said:**
> Hi!

By following several guides I have got my Logitech Mediaplay to work somehow. I'm now able to use scroll wheel to scroll both vertically and horizontally. But I can't get the media keys to work whatever I have tried.

All buttons work when testing with xev, but I'm not able to set the keyboard shortcuts in Gnome. When I select ie. "Volume down" and try to assign new shortcut it just reverts to the original when I press the corresponding mouse button. 

Any tips?

----
My current configuration is 

xorg.conf
```
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "evdev"
        Option      "CorePointer"
        Option      "Device" "/dev/input/event9"
        Option      "ZAxisMapping" "6 7 4 5"
        Option      "Buttons" "7"
EndSection
```

.Xmodmap
```
pointer = 1 2 3 4 5 7 6
```


Funny, because I have the media keys working, but can't get the horizontal scroll to work. Did you ever get the media keys working? If not, here's what I did:

1. Install xbindkeys and put this is in your .xbindkeysrc config:

```

# Volume

"xvkbd -text "\[XF86AudioRaiseVolume]""
  m:0x0 + b:13

"xvkbd -text "\[XF86AudioLowerVolume]""
  m:0x0 + b:14

# Media Control

"rhythmbox-client"
  m:0x10 + b:10

"xvkbd -text "\[XF86AudioPlay]""
  m:0x10 + b:17

"xvkbd -text "\[XF86AudioNext]""
  m:0x10 + b:15

"xvkbd -text "\[XF86AudioPrev]""
  m:0x10 + b:16

```

2. I'm not sure that this is really needed, but you *might* need to add the XF86 keysyms above to your .Xmodmap file. Here's mine:

```
keycode 122 = XF86Search
keycode 129 = XF86AudioMedia
keycode 130 = XF86WWW
keycode 162 = XF86AudioPlay XF86AudioPause
keycode 164 = XF86AudioStop
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 230 = XF86Favorites
keycode 231 = XF86Refresh
keycode 233 = XF86Forward
keycode 234 = XF86Back
```

This not only lowers and raises the volume, but also shows the indicator on the screen (something that all of the other instructions I've seen don't do, btw.)

Does the horizontal scroll wheel work for you in firefox? I tried your configuration in my xorg.conf and it didn't work for me. If it does work for you, then was there anything else needed or is that it?

UPDATE:

I think I've figured out what you meant, after realizing that I can scroll horizontally in OpenOffice apps, and presumably Nautilus as well, though I haven't tried it yet. I was testing it in firefox, where horizontal scroll registers as back and forward. I don't like this, so I'm gonna keep working to see if I can get horizontal scrolling working in firefox.

UPDATE 2:

Okay, I finally got everything working as I want with horizontal scrolling working with the scrollwheel and back/forward working with the thumb buttons. All I needed to do was add the following line to my .xbindkeysrc file to get the thumb buttons to function as back/forward in firefox and nautilus:

```
# Forward and Back

"xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x10 + b:8

"xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x10 + b:9

```

And then configuring firefox for horizontal scrolling with the scrollwheel, which already worked in Nautilus, by typing "about:config" in the address bar, to go to the config page, and changing the values of “mousewheel.horizscroll.withnokey.action” and “mousewheel.horizscroll.withnokey.numlines” both to 1.

---

### Post by TS28 on 2007-06-04
I've been trying to get the following working, but return with a 404 error:

wget [http://detyabozhye.com/other/logitech_applet-0.4test1.tar.gz](http://detyabozhye.com/other/logitech_applet-0.4test1.tar.gz)

Is anyone else experiencing this problem?  Solutions?

Thanks :)

---

### Post by detyabozhye on 2007-06-05
I think I removed that in favor of lomoco.

---

### Post by thecorch on 2007-06-09
I've gone through this tutorial, and a couple of other older ones, and I still can't get full functionality out of my keyboard and mouse.

I have the Logitech Elite Duo. I can't get cruise control to work, and locomo reports that it isn't a supported device so I can't use cruise that way either. 

I also can't get the extra buttons on my keyboard working, which seems to be a common problem around here, but none of the solutions have worked for me. It seems like its something to do with "evdev" because before I used this tutorial, and set "evdev" as the mouse driver, the keys on my keyboard worked fine but the extra mouse buttons didn't. 

Doesn't seem like I can use full functionality for my keyboard and mouse at the same time. Does anyone have a solution that maybe they haven't posted that I could try out? I swear I've tried EVERYTHING.

---

### Post by LordKelvan on 2007-06-09
Hi all:

After long last, I have finally gotten my MX518 to work properly (thanks to the excellent posts made in this thread and others at this site).  However, there is one small matter:  I have this script that I told Ubuntu to run at startup (I did this through System->Preferences->Session, and then added a startup thing), and what I have it do is execute the command "lomoco -m --sms", then a few other commands to set up evrouter.  The thing is that the lomoco line seems to be failing, and I think it has something to do with the fact that you have to run the command as root.  

Right now, I manually run the lomoco command after startup, but I would really like it to be executed as part of the script.  Does anyone know how to accomplish this?  Thanks.

Edit:

thecorch:  Could you tell me exactly what isn't working for your mouse?  I just went through hell trying to get my mouse working, maybe I can help.

---

### Post by KhaaL on 2007-06-11
I need a little bit of clarification here... in  /etc/udev/rules.d/19-local.rules, if i decide to go for, say, event9, should the line look like this:

KERNEL=="event[9]*", SYSFS{../name}=="Logitech USB-PS/2 Optical Mouse", NAME="input/event9"

or

KERNEL=="event9*", SYSFS{../name}=="Logitech USB-PS/2 Optical Mouse", NAME="input/event9"

---

### Post by detyabozhye on 2007-06-13
> **KhaaL said:**
> I need a little bit of clarification here... in  /etc/udev/rules.d/19-local.rules, if i decide to go for, say, event9, should the line look like this:

KERNEL=="event[9]*", SYSFS{../name}=="Logitech USB-PS/2 Optical Mouse", NAME="input/event9"

or

KERNEL=="event9*", SYSFS{../name}=="Logitech USB-PS/2 Optical Mouse", NAME="input/event9"

I think it's the first one, but I don't remember for sure anymore as I don't use the udev rule anymore but use the name directly in xorg.conf.

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "evdev"
    Option         "CorePointer"
    Option         "Name" "Logitech USB-PS/2 Optical Mouse"
EndSection
```

---

### Post by KhaaL on 2007-06-13
oh, well that looks a lot easier and more practical... I'll try it as soon as i get home!

---

### Post by mitchell486 on 2007-06-16
With only some slight modifications, (which btw I am an uber-noob with Linux, have only had it for like two days), it worked smashingly. :D I am excited. I missed my back button and now its finally working. Thank you so much for finding this and sharing. :D The lazy of world salute you and thank you. I owe you one.

---

### Post by KhaaL on 2007-06-17
> **detyabozhye said:**
> I think it's the first one, but I don't remember for sure anymore as I don't use the udev rule anymore but use the name directly in xorg.conf.

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "evdev"
    Option         "CorePointer"
    Option         "Name" "Logitech USB-PS/2 Optical Mouse"
EndSection
```

My man, this worked great for me... looks like setting the mouse up is even easier now since you dont need to hassle with edev rules. Even lomoco is in the repositories, so no compilation is needed.

You should update the guide with this new information :)

---

### Post by detyabozhye on 2007-06-19
> **KhaaL said:**
> You should update the guide with this new information :)

Yeah, the guide is 2 Ubuntu releases behind.

---

### Post by detyabozhye on 2007-06-19
OK, I updated the guide, let me know if I made any mistakes.

---

### Post by PilotJLR on 2007-06-30
detyabozhye - excellent howto, this works great for me! Thank you for taking the time to post this.

---

### Post by detyabozhye on 2007-06-30
You're welcome. Is there a way to change the title of this thread?

---

### Post by KhaaL on 2007-07-01
yes, i think by going edit -> go advanced, and then you can change the title...

---

### Post by gouzos on 2007-07-02
I have a** Logitech MX1000**.
I followed your guide step by step (I tried about a dozen others before)

I substituted what you said about tilt wheel mice

Now:
Right-click, Left-click and Middle-click work

Wheel-scroll, 
Tilt-wheel and
Forward and Back don't work

Page-up&down when pressed scroll just one line at a time


The middle thumb button on the right works

Can you help?

---

### Post by detyabozhye on 2007-07-02
> **KhaaL said:**
> yes, i think by going edit -> go advanced, and then you can change the title...

Tried that, but it only changed the title of the first post, not the whole thread.

---

### Post by detyabozhye on 2007-07-02
> **gouzos said:**
> I have a** Logitech MX1000**.
I followed your guide step by step (I tried about a dozen others before)

I substituted what you said about tilt wheel mice

Now:
Right-click, Left-click and Middle-click work

Wheel-scroll, 
Tilt-wheel and
Forward and Back don't work

Page-up&down when pressed scroll just one line at a time


The middle thumb button on the right works

Can you help?

With xbindkeys off, what button numbers do you get in xev for the buttons that don't work? (Buttons includes the wheel)

---

### Post by gouzos on 2007-07-02
I don't know if it is turned off. How do I turn it off?
Right now xev gives me:

Left 1
Middle 2
Right 3
Wheel left 13
Wheel right 14
Wheel up 6 
Wheel down 7
Up button 4
Down button 5
Forward 11
Back 10
Thumb 12

---

### Post by detyabozhye on 2007-07-02
To turn off xbindkeys, type this comand into the terminal:
```
killall xbindkeys
```

Check to see if you have a file in your home directory with the filename .Xmodmap (enable viewing hidden files). If you do, tell me what's inside it.

The buttons should be something like this:
```

Left 1
Middle 2
Right 3
Wheel up 4
Wheel down 5
Wheel left 6
Wheel right 7

Forward 8
Back 9
Up button 10 (or 10 + 4)
Down button 11 (or 11 + 5)
Thumb 12
```

1-7 should be in that order, while 8-12 don't have to be in that strict order.

---

### Post by gouzos on 2007-07-02
.Xmodmap says:
pointer = 1 2 3 6 7 8 9 10 11 12 4 5

I switched the xbindkeysrc entries to b:13 and b:14

I also swithed the click entries to 11 and 10 because of what xev said. Is that right?

I'll reboot and tell you what happens. 
I'll also try killing the xbindkeys and reporting what happens.

---

### Post by detyabozhye on 2007-07-02
> **gouzos said:**
> .Xmodmap says:
pointer = 1 2 3 6 7 8 9 10 11 12 4 5

OK, that was what you already had, right?
If yes, we'll need to change some things around

> **gouzos said:**
> I switched the xbindkeysrc entries to b:13 and b:14

I also swithed the click entries to 11 and 10 because of what xev said. Is that right?

I'll reboot and tell you what happens. 
I'll also try killing the xbindkeys and reporting what happens.

Um, before we do the xbindkeys, it's best to get Xmodmap sorted out.

---

### Post by gouzos on 2007-07-02
killall xbindkeys gives back:

xbindkeys:no process killed

I tried xev again, nothing changed.
My substitutions didn't work either. Should I change them back?

---

### Post by gouzos on 2007-07-02
Oh, I just noticed, My wheel works as scroll left and right. Doing what the tilt wheel should.

---

### Post by gouzos on 2007-07-02
Ok.

What should I do to Xmodmap?

---

### Post by gouzos on 2007-07-03
Making Xmodmap read:

pointer=1 2 3 4 5 ... 

got me the Wheel up & down but the rest still don't work

---

### Post by forfree on 2007-07-06
Good guide, but I have a question.  Is there a way to make my left scroll on my tilt wheel function as a middle mouse button?  I tried switching them out in xmodmap, but the problem is instead of acting like a press and release it sends a bunch of middle clicks when I hold it down to scroll.  Anyone know a way?

---

### Post by detyabozhye on 2007-07-07
> **gouzos said:**
> Making Xmodmap read:

pointer=1 2 3 4 5 ... 

got me the Wheel up & down but the rest still don't work

What does xev give now?

---

### Post by detyabozhye on 2007-07-07
> **forfree said:**
> Good guide, but I have a question.  Is there a way to make my left scroll on my tilt wheel function as a middle mouse button?  I tried switching them out in xmodmap, but the problem is instead of acting like a press and release it sends a bunch of middle clicks when I hold it down to scroll.  Anyone know a way?

Use the "click" program to emulate middle click. Can't explain at the moment cuz I gotta run.

---

### Post by forfree on 2007-07-07
Ok thanks, I've searched the repositories and google.  What's the name of the "click" program?

---

### Post by detyabozhye on 2007-07-07
> **forfree said:**
> Ok thanks, I've searched the repositories and google.  What's the name of the "click" program?

It's what I described in this part of the guide:

[QUOTE=detyabozhye]_2. Fixing the cruise control buttons (MX500, MX510, MX700, MX1000):_

[COLOR="Red"]*Note: In Edgy and Feisty I haven't noticed this problem anymore (I've had cruise control off for a while though), but I will leave this section here because it hasn't been confirmed that the problem is gone.*[/COLOR]

Install these packages for "click" to compile:

```
sudo apt-get install build-essential libx11-dev x11proto-xext-dev libxtst-dev
```

Download and untar "click" source code into ~/.click (or wherever you want, just remember the dir, you'll need it in the .xbindkeysrc):

```
cd ~/
wget http://bg.rifetech.com/click.tgz
tar xvfz click.tgz
mv click .click

```

then compile it:

```
cd ~/.click
make
```

Then add this to you .xbindkeysrc (gedit ~/.xbindkeysrc):

```
"~/.click/click 4"
  m:0x0 + b:9
"~/.click/click 5"
  m:0x0 + b:10
```

*Note: Mice with more buttons and/or tilt wheels will most likely have different button numbers, please check in xev.*[/QUOTE]

Just make it emulate button 3 instead of 4 or 5.

---

### Post by forfree on 2007-07-08
Hmm, that's giving me the same problem as remapping it.  When I hold the "scroll left" button down that's emulating the middle click, instead of just acting as a single click it sends multiple middle clicks.  Is there a way to make it behave in a hold down and release type way in ubuntu?

---

### Post by gouzos on 2007-07-08
my xorg.conf reads:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"Logitech USB RECEIVER"
	Option		"Buttons"       "12"
EndSection


Xmodpam reads

pointer = "1 2 3 4 5 6 7 8 9 10 11 12 13 14"

xev gives:
Left 1
Middle 2
Right 3

Wheel up 4
Wheel down 5
Wheel left 13
Wheel right 14

Up button 11
Down button 12

Forward 9
Back 8
Thumb 10

---

### Post by detyabozhye on 2007-07-09
> **forfree said:**
> Hmm, that's giving me the same problem as remapping it.  When I hold the "scroll left" button down that's emulating the middle click, instead of just acting as a single click it sends multiple middle clicks.  Is there a way to make it behave in a hold down and release type way in ubuntu?

The mouse itself keeps sending multiple click and release events as far as I know, so probably not.

---

### Post by detyabozhye on 2007-07-09
@gouzos:

Try making .Xmodmap read:

```
pointer = "1 2 3 4 5 13 14 8 9 10 11 12 6 7"
```

Then xev should give you:

```
Left 1
Middle 2
Right 3

Wheel up 4
Wheel down 5
Wheel left 6
Wheel right 7

Up button 11
Down button 12

Forward 9
Back 8
Thumb 10
```

---

### Post by t_tovenaar on 2007-07-10
Good howto, thanks!

---

### Post by jan. on 2007-07-10
Ah, well 50 pages of posts and exams approaching rapidly...

When I resume (either from Disk or RAM) the lomoco-Settings for my MX510 are lost and I have to run them again. Any fixes for that? I was thinking about putting a script into the appropriate folder in order to have it restore my mouse settings. Does anyone know the folder I have to put those scripts? By the way, I am using the userspace software suspend since the default suspend scripts did not work...

---

### Post by gouzos on 2007-07-10
Ok

xev gives what you said

The buttons' functionality however haven't changed.

Only Left, Middle, Right, Thumb, WhUP and WhDown work

Now what do I do?

---

### Post by detyabozhye on 2007-07-10
@t_tovenaar: ur welcome.

@jan.: I don't know since suspend to disk is completely broken on my system and I have no intentions of fixing it at the moment.

> **gouzos said:**
> Ok

xev gives what you said

The buttons' functionality however haven't changed.

Only Left, Middle, Right, Thumb, WhUP and WhDown work

Now what do I do?

OK, now set up your .xbindkeysrc like this:

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9
"any command u want"
  m:0x0 + b:10
"any command u want here too"
  m:0x0 + b:11
"and anything u want here too"
  m:0x0 + b:12
```

The first two are for your back and forward buttons, the rest you can either do what you want with, or tell me what you want them to do and I can suggest some commands. If I understood correctly, you don't have xbindkeys run at startup. Make sure it's installed and put it in your startup programs for it to work.

---

### Post by gouzos on 2007-07-11
I do have an entry in my startup programs: name: xbindkeys, command: ~/.xbindkeysrc

They don't seem to be working.

Right and left are inverted. Should I swap 6 and 7 in the xmodmap file? Also they only move the window one space even if I keep them pressed.

Up and Down I'd like to have as a faster wheel or maybe pageup and page down.


I'd also like to thank you. You have been extremely helpful. I hope we work this out.

---

### Post by detyabozhye on 2007-07-11
> **gouzos said:**
> I do have an entry in my startup programs: name: xbindkeys, command: ~/.xbindkeysrc

They don't seem to be working.

change the command to just xbindkeys
~/.xbindkeysrc is your local configuration file while xbindkeys is the actual program.

> **gouzos said:**
> Right and left are inverted. Should I swap 6 and 7 in the xmodmap file? Also they only move the window one space even if I keep them pressed.

yeah, try swapping them, that should fix it, but as for it moving only once, that's not right. IN xev it only does it once as well?

> **gouzos said:**
> Up and Down I'd like to have as a faster wheel or maybe pageup and page down.

Change:

```
"any command u want here too"
  m:0x0 + b:11
"and anything u want here too"
  m:0x0 + b:12
```

to:

```
"/usr/bin/xvkbd -xsendevent -text "\[Page_Up]""
  m:0x0 + b:11
"/usr/bin/xvkbd -xsendevent -text "\[Page_Down]""
  m:0x0 + b:12
```

in your ~/.xbindkeysrc file

> **gouzos said:**
> I'd also like to thank you. You have been extremely helpful. I hope we work this out.

you're welcome.

---

### Post by gouzos on 2007-07-11
Is xbindkeys the one in /usr/bin? I put that in but they still don't work.
(.xbindkeysrc is in my home directory. should it?) 
I also have an xmodmaprc in my home folder which says: pointer = [list of numbers]

I swapped 6 and 7. They're ok now but still I don't have constant press.

Xev says:
EnterNotify event, serial 33, synthetic NO, window 0x3a00001,
    root 0x186, subw 0x0, time 5195303, (38,45), root:(68,70),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus NO, state 16

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  4294967174 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 33, synthetic NO, window 0x3a00001,
    root 0x186, subw 0x3a00002, time 5195454, (38,45), root:(68,70),
    state 0x10, button 7, same_screen YES

LeaveNotify event, serial 33, synthetic NO, window 0x3a00001,
    root 0x186, subw 0x0, time 5195454, (38,45), root:(68,70),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus NO, state 16

---

### Post by detyabozhye on 2007-07-11
> **gouzos said:**
> Is xbindkeys the one in /usr/bin? I put that in but they still don't work.
(.xbindkeysrc is in my home directory. should it?) 

I also have an xmodmaprc in my home folder which says: pointer = [list of numbers]

yes, everything is right with xbindkeys and xbindkeysrc. You don't have xbindkeys running in your process manager after logging in? what happens when you try running xbindeys (just that, no path or anything) in the terminal?

> **gouzos said:**
> I swapped 6 and 7. They're ok now but still I don't have constant press.

Xev says:
EnterNotify event, serial 33, synthetic NO, window 0x3a00001,
    root 0x186, subw 0x0, time 5195303, (38,45), root:(68,70),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus NO, state 16

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  4294967174 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 33, synthetic NO, window 0x3a00001,
    root 0x186, subw 0x3a00002, time 5195454, (38,45), root:(68,70),
    state 0x10, button 7, same_screen YES

LeaveNotify event, serial 33, synthetic NO, window 0x3a00001,
    root 0x186, subw 0x0, time 5195454, (38,45), root:(68,70),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus NO, state 16

That "KeymapNotify" part looks like those buttons are being mapped to something, can you give me your whole .xbindkeysrc file? Do you have imwheel or any other keymap program running at startup?

---

### Post by gouzos on 2007-07-12
No, I can see xbindkeys running in my system monitor. I can kill it and start it agail from the terminal. It seems ok.

xbindkeysrc:
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
  m:0x0 + b:9
"any command u want"
  m:0x0 + b:10
"/usr/bin/xvkbd -xsendevent -text "\[Page_Up]""
  m:0x0 + b:11
"/usr/bin/xvkbd -xsendevent -text "\[Page_Down]""
  m:0x0 + b:12

I have Beryl running. you think that might be it?
I have my Thumb button (10) binded in Beryl as the scaling button and it works just fine.

---

### Post by gouzos on 2007-07-12
Also, PgUp and PgDn work but also without working continuously. Only one click at a time.

---

### Post by Unicast on 2007-07-12
Just wanted to thank **detyabozhye** for this excellent How To!

Just got the back / forward function working on my Logitech Cordless Mini Optical Mouse.

Thank you so much! :cool:

Edit: This is the contents of my .xbindkeysrc file just in case it helps others:
```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:11
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:12
```

---

### Post by John.Michael.Kane on 2007-07-13
I am currently testing a mx revolution, and wondered if there is a way to bind the push/pull thumb button to control/alt left/right arrow using the .xbindkeysrc file? This would allow the button to be used to switch work places.

---

### Post by Unicast on 2007-07-14
Just noticed that after getting the tilt wheel on my mouse to work I'm having problems logging out. When I log out I just get a black screen. Can anyone help?

Here's my xorg.conf (if it helps - and many thanks in advance!):
```
Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"Logitech USB RECEIVER" #this should be the name of the device which I made bold here.
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

EDIT: Resolved - nothing to do with this "HOWTO".

There's a problem with logging out in Feisty: [http://ubuntu1501.blogspot.com/2007/04/fix-logout-problem.html](http://ubuntu1501.blogspot.com/2007/04/fix-logout-problem.html)

Can now log out successfully! :D

---

### Post by detyabozhye on 2007-07-16
> **SD-Plissken said:**
> I am currently testing a mx revolution, and wondered if there is a way to bind the push/pull thumb button to control/alt left/right arrow using the .xbindkeysrc file? This would allow the button to be used to switch work places.

I gues it'd be something like:

```
"/usr/bin/xvkbd -xsendevent -text "\[Ctrl_L]\[Alt_L]\[_L_eft]""
  m:0x0 + b:6 #replace w/ button no.
"/usr/bin/xvkbd -xsendevent -text "\[Ctrl_L][Alt_L]\[_R_ight]""
  m:0x0 + b:7 #replace also
```

But I don't know for sure, I'm not an xvkbd expert.

---

### Post by John.Michael.Kane on 2007-07-17
> **detyabozhye said:**
> I gues it'd be something like:

```
"/usr/bin/xvkbd -xsendevent -text "\[Ctrl_L]\[Alt_L]\[_L_eft]""
  m:0x0 + b:6 #replace w/ button no.
"/usr/bin/xvkbd -xsendevent -text "\[Ctrl_L][Alt_L]\[_R_ight]""
  m:0x0 + b:7 #replace also
```

But I don't know for sure, I'm not an xvkbd expert.

No dice with the command posted, however. I did manage to get button 17 to work even though 13,and 15 are a no go.

Thanks again.

---

### Post by Sciamano on 2007-07-31
I've been using this guide for more than a year now, and the mouse (logitech MX700) has always worked fine.
Today, suddenly, the wheel stopped working: no scrolling at all.
Any idea what happened?
I tried reconfiguring everything with no success. :(

---

### Post by AnotherMuggle on 2007-08-01
Hi,
I have the back and forward buttons working in Firefox and the normal "explorer" type windows.  However, my left and right tilt wheel also move back and forward in Firefox (opposite direction to what you'd expect).  I want them to scroll left and right but it doesn't seem possible.

Can anyone help? It's an MX1000.

Thanks,
Tom Kear

---

### Post by zuzuzzzip on 2007-08-02
I'm also looking for th Ctrl Button

I found this using xev when pressing the ctrl button
```
KeyPress event, serial 33, synthetic NO, window 0x4400001,
    root 0x186, subw 0x0, time 2567725, (385,729), root:(392,777),
    state 0x10, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

```so it should work in .xbindkeysrc like so:
```
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Alt_L]\[right]""
  m:0x0 + b:7
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Alt_L]\[right]""
  m:0x0 + b:6
```but it doesn't :(
if you want to test make sure you restart xbindkeys when you've changed .xbindkeysrc, like so:
```
zuzuzzzip@ZuzuPC-ubuntu:~$ pidof xbindkeys 
7844
zuzuzzzip@ZuzuPC-ubuntu:~$ kill 7844
zuzuzzzip@ZuzuPC-ubuntu:~$ xbindkeys

```

---

### Post by yogo on 2007-08-03
Just a quick note, after a week of trying to get BTNX going and it doing absolutely nothing and I read  almost the whole 35 pages plus, I decided to try Setpoint run with Wine, that did not work.

I then tried the first few steps on the first page of this thread up tp the point that you restart your pc.

Viola, my front and back buttons worked for navigating thru web pages, Great on the steps as I got no errors.

I still can not get rid of BTNX from terminal following their command

sudo make uninstall gets this error
Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Anyways, tow things I would like number 1 is to get my application switcher to work if possible and secondly I would like to remove BTNX.

Thanks for any help and kudos for the first few steps as they worked like a charm on forward and back buttons.

---

### Post by detyabozhye on 2007-08-04
> **Sciamano said:**
> I've been using this guide for more than a year now, and the mouse (logitech MX700) has always worked fine.
Today, suddenly, the wheel stopped working: no scrolling at all.
Any idea what happened?
I tried reconfiguring everything with no success. :(

What does xev give you when you scroll?
Are you using Xmodmap and/or xbindkeys?
What is their config if you do?

---

### Post by detyabozhye on 2007-08-04
> **tomkear2006 said:**
> Hi,
I have the back and forward buttons working in Firefox and the normal "explorer" type windows.  However, my left and right tilt wheel also move back and forward in Firefox (opposite direction to what you'd expect).  I want them to scroll left and right but it doesn't seem possible.

Can anyone help? It's an MX1000.

Thanks,
Tom Kear

[http://strabes.wordpress.com/2007/04/01/disable-firefox-going-backforward-on-horizontal-scroll/](http://strabes.wordpress.com/2007/04/01/disable-firefox-going-backforward-on-horizontal-scroll/)

---

### Post by detyabozhye on 2007-08-04
> **zuzuzzzip said:**
> I'm also looking for th Ctrl Button

I found this using xev when pressing the ctrl button
```
KeyPress event, serial 33, synthetic NO, window 0x4400001,
    root 0x186, subw 0x0, time 2567725, (385,729), root:(392,777),
    state 0x10, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

```so it should work in .xbindkeysrc like so:
```
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Alt_L]\[right]""
  m:0x0 + b:7
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Alt_L]\[right]""
  m:0x0 + b:6
```but it doesn't :(
if you want to test make sure you restart xbindkeys when you've changed .xbindkeysrc, like so:
```
zuzuzzzip@ZuzuPC-ubuntu:~$ pidof xbindkeys 
7844
zuzuzzzip@ZuzuPC-ubuntu:~$ kill 7844
zuzuzzzip@ZuzuPC-ubuntu:~$ xbindkeys

```

Make sure "Left" and "Right" are capitalized. Might work then, might not.

---

### Post by detyabozhye on 2007-08-04
> **yogo said:**
> Just a quick note, after a week of trying to get BTNX going and it doing absolutely nothing and I read  almost the whole 35 pages plus, I decided to try Setpoint run with Wine, that did not work.

I then tried the first few steps on the first page of this thread up tp the point that you restart your pc.

Viola, my front and back buttons worked for navigating thru web pages, Great on the steps as I got no errors.

I still can not get rid of BTNX from terminal following their command

sudo make uninstall gets this error
Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Anyways, tow things I would like number 1 is to get my application switcher to work if possible and secondly I would like to remove BTNX.

Thanks for any help and kudos for the first few steps as they worked like a charm on forward and back buttons.

For the application switcher, you will either need a custom program or use a DE such as Xfce that has something of the sort built in.

What is BTNX, btw?

---

### Post by zuzuzzzip on 2007-08-05
> **detyabozhye said:**
> For the application switcher, you will either need a custom program or use a DE such as Xfce that has something of the sort built in.

What is BTNX, btw?
[http://ubuntuforums.org/showthread.php?t=455656&highlight=btnx](http://ubuntuforums.org/showthread.php?t=455656&highlight=btnx)

thx for your reply
still doesn't work though :D

---

### Post by yogo on 2007-08-05
deleted double post

---

### Post by yogo on 2007-08-05
@Dety 



BTNX is an app for controls on your mouse, did not work well for me and the developer rarely posts and the GUI is not user friendly.

I used the first few steps on this page and at least got my forward and back buttons to work.

I have Beryl which has an app switcher but it is keyboard related, I just wish my application switcher on my Logitech cordless click mouse worked.

---

### Post by AnotherMuggle on 2007-08-06
> **detyabozhye said:**
> [http://strabes.wordpress.com/2007/04/01/disable-firefox-going-backforward-on-horizontal-scroll/](http://strabes.wordpress.com/2007/04/01/disable-firefox-going-backforward-on-horizontal-scroll/)

Sorted now. Much appreciated :)

Strangely. Scroll left, scrolls right...and visa-versa.  Even switching the button numbers in the text files doesn't seem to change this...it always scrolls in the opposite direction.

---

### Post by zuzuzzzip on 2007-08-06
> **tomkear2006 said:**
> Sorted now. Much appreciated :)

Strangely. Scroll left, scrolls right...and visa-versa.  Even switching the button numbers in the text files doesn't seem to change this...it always scrolls in the opposite direction.
if you change the text-file, be sure you restarted xbindkeys..
by killing it and starting it again :)

---

### Post by detyabozhye on 2007-08-07
no, that needs to be changed in Xmodmap, not xbindkeys. Are you using Xmodmap tomkear, btw?

---

### Post by detyabozhye on 2007-08-07
For the application switcher, you need a program that the mouse button will run. I don't know of any really, except the one built in to Xfce: xfdesktop --windowlist

---

### Post by AnotherMuggle on 2007-08-07
> **detyabozhye said:**
> no, that needs to be changed in Xmodmap, not xbindkeys. Are you using Xmodmap tomkear, btw?

I am using xbindkeys...using the method at the start of this post.

---

### Post by detyabozhye on 2007-08-07
> **tomkear2006 said:**
> I am using xbindkeys...using the method at the start of this post.

xbindkeys makes the back and forward work in all applications. Xmodmap is seperate, and remaps your mouse buttons if they are not in the correct order. Xmodmap and xbindkeys can work together without any problems, they do different things.

---

### Post by adrianmariano on 2007-08-07
I've been trying to get the tilt wheel to work on my LX3 mouse.  This is a simple mouse.  It doesn't have buttons for all ten fingers, just three buttons plus the wheel.  But I have not found anything that will awaken the tilt wheel.  

I have tried the setup suggested on this site

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "Name"    "ImExPS/2 Logitech Explorer Mouse"           
        #Option          "Buttons"  "12"
EndSection

```

At some point the mouse changed its name to 
"Logitech USB-PS/2 Optical Mouse"

But changing the name section didn't make any difference.  The mouse works and the scrolling function of the wheel works, just not the tilt function.  In xev I see buttons 1-3 for the buttons and 4-5 for the scrolling of the wheel and nothing all all for tilt.  

Any ideas?

---

### Post by Ranganaths on 2007-08-08
hi all,

I recently installed the feisty fawn on my laptop. I am not able to configure the usb mouse with my laptop.. the right click, left click works fine,even the scroller works fine .  but the pointer moment is not there there..i pointer of the mouse doesnt move. its an optical mouse. kindly let me know how to configure it..

here  out put of the usbls

Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 002: ID 15d9:0a33
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 003: ID 0db0:6877 Micro Star International
Bus 002 Device 001: ID 0000:0000


Regards
Ranganath.S

Thank you
-R

---

### Post by estaticd on 2007-08-08
for the MX400 my .xbindkeysrc file looks like this:

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9

---

### Post by zuzuzzzip on 2007-08-08
> **estaticd said:**
> for the MX400 my .xbindkeysrc file looks like this:

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
  m:0x0 + b:9

I also have the MX400 :)
This works fine but for my horizontal scroll buttons (tilt wheel thingy) I can't get control buttons to work :(

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Alt_L]\[RIGHT]""
  m:0x0 + b:7
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Alt_L]\[LEFT]""
  m:0x0 + b:6
```
The buttons get mapped though, just so you know they're there :)

---

### Post by pbalir on 2007-08-15
I have an MX900 on U7.04 that I need to warmplug to get working each boot. The mouse works perfectly then. But it's not very satisfactory, so I tried this set of instructions.

I got to the end of Section 1, rebooted, and Ubuntu started to power up. Got the splash screen, the mouse dock light blinked, and the monitor light also blinked. A brief burst of text on the screen (unreadable) and then...nothing. Just a blank black screen.

I'm very new at this, but I managed to fix my xorg.conf file and get things working again. 

I note in other places that there are two parts to the configuration - detecting the mouse dock, then the mouse itself from its mac address.

I'm back to hotplugging...unless there is yet a better way?

Regards, and thanks for your efforts....

Paul

---

### Post by AnotherMuggle on 2007-08-16
My MX1000 seems to side scroll by default, no settings need to be changed.  However, it scrolls the opposite way to that, that it should.  Can anyone step by step (noob) me from start to finish on how to make them scroll the correct direction?

---

### Post by 5h4rk on 2007-08-17
Actually

> "/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:7


doesn't work on my mx500, instead:
> 
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9

=)

---

### Post by EXCiD3 on 2007-08-18
Worked perfectly! Thanks as without this, I probably would have gotten used to not having the incredibly handy forward and backward buttons on my MX518!

---

### Post by jeepzj on 2007-08-19
hi folks..

My MX610 locks up at random points and slows down so the cursor is non-responsive.. After a couple seconds it comes back and is ok for a little bit than locks up again.. any ides how I can fix this???

- Hubert

---

### Post by spartan777 on 2007-08-20
awesome guide!   :D :D :D :D

---

### Post by King Buttons I on 2007-08-20
I need help. I change Xorg.conf and restart the computer and X server fails to start. 
Here is the output of cat /proc/bus/input/devices:

```
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
H: Handlers=mouse0 event0 ts0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:07.2-2/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:07.2-2/input1
S: Sysfs=/class/input/input2
H: Handlers=kbd mouse1 event2 ts1 
B: EV=f
B: KEY=7fff 2c3027 bf004440 0 0 ff0001 f80 8807c000 667bfa d941dfed 9e0000 0 0 0
B: REL=143
B: ABS=1 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3 
B: EV=40001
B: SND=6
```

I have an MX600 wireless mouse that came with the MX3200 keyboard. Evdev is installed on the computer. I am running Feisty Fawn.

I have two other questions: do I need evdev to continue with the guide? And what is "Macintosh mouse button emulation"?

---

### Post by trotte on 2007-08-20
It is not metioned in the guide, but must u not also edit the Server layout  section?

This part:

[I]Section "ServerLayout"
   Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
   ** InputDevice    "Mouse0" "CorePointer"**
EndSection[/I]

Cus else I get error that no Mouse0 section exists. 

But even if I change that line to *InputDevice "Configured Mouse" "CorePointer"* I cant restart X cus CorePointer returns NULL.

Any idea why?

I tried the evdev rule method in the old guide, didnt work either.

---

### Post by stedevil on 2007-08-23
Hi, Im new here as well as to Ubuntu. I didnt read through all the (56!) pages so I apologize if it was already brought up before, but I was wondering about a specific section, specifically the part I highlighted in red

> **detyabozhye said:**
> 
_4. Restart_

_Warning!_
Don't restart yet! Just before we do I have to warn you if you made a mistake in the xorg file X will not start. But don't worry that's why we backed up the previous file. If X fails to start then you will end up in a text console. Log in and type the following to rename the current xorg.conf and restore the previous file:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-logi
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

_Ok, I'm ready_
Now we're prepared, restart your computer. [color=red]The reason you need to restart the whole computer is so that the udev rule can take effect.[/color][/INDENT]



Ok... so we need to restart udev. But why do we need to restart the entire OS to do that? At least this worked for me

```

sudo /etc/init.d/udev stop
sudo /etc/init.d/udev start

or simply 

sudo /etc/init.d/udev restart

```

In any case, thanks for the guide. My MX500 up n running as it should in no time :)

---

### Post by detyabozhye on 2007-08-24
> **King Buttons I said:**
> I need help. I change Xorg.conf and restart the computer and X server fails to start. 
Here is the output of cat /proc/bus/input/devices:

```
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
H: Handlers=mouse0 event0 ts0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:07.2-2/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:07.2-2/input1
S: Sysfs=/class/input/input2
H: Handlers=kbd mouse1 event2 ts1 
B: EV=f
B: KEY=7fff 2c3027 bf004440 0 0 ff0001 f80 8807c000 667bfa d941dfed 9e0000 0 0 0
B: REL=143
B: ABS=1 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3 
B: EV=40001
B: SND=6
```

I have an MX600 wireless mouse that came with the MX3200 keyboard. Evdev is installed on the computer. I am running Feisty Fawn.

I have two other questions: do I need evdev to continue with the guide? And what is "Macintosh mouse button emulation"?

dunno about the Mac thing, but you'll need to use more than just the name in xorg.conf because of the mouse/keyboard combo (the phys or something), but I can't remember what exactly it is because I have only an optical mouse.

---

### Post by detyabozhye on 2007-08-24
> **trotte said:**
> It is not metioned in the guide, but must u not also edit the Server layout  section?

This part:

[I]Section "ServerLayout"
   Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
   ** InputDevice    "Mouse0" "CorePointer"**
EndSection[/I]

Cus else I get error that no Mouse0 section exists. 

But even if I change that line to *InputDevice "Configured Mouse" "CorePointer"* I cant restart X cus CorePointer returns NULL.

Any idea why?

I tried the evdev rule method in the old guide, didnt work either.

That depends on what name you gave the mouse section.

---

### Post by detyabozhye on 2007-08-24
> **stedevil said:**
> Hi, Im new here as well as to Ubuntu. I didnt read through all the (56!) pages so I apologize if it was already brought up before, but I was wondering about a specific section, specifically the part I highlighted in red




Ok... so we need to restart udev. But why do we need to restart the entire OS to do that? At least this worked for me

```

sudo /etc/init.d/udev stop
sudo /etc/init.d/udev start

or simply 

sudo /etc/init.d/udev restart

```

In any case, thanks for the guide. My MX500 up n running as it should in no time :)

This guide is partly based on another one. I didn't write about the restarting part, and you are correct that is the more "correct" way of doing it.

---

### Post by DarkN00b on 2007-08-25
Just thought I'd drop in and report that everything worked fine for me after only a couple minor tweaks.

I have a new Logitech LX3 optical mouse with a rocking scroll wheel.

I had to make a minor change to the "Inputdevice" section of my Xorg.conf as follows:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
**	Option		"SendCoreEvents"	"true"**
	Option		"Name"	"Logitech USB-PS/2 Optical Mouse"
EndSection
```

I had to change the bolded text because X would not start unless my mouse was plugged in. After making that one change, X loaded perfectly on the next reboot.

I also had to swap buttons 6 and 7 to get the rocker working correctly as well as adding xbindkeys to my session startup.

Once these things were done, everything worked like a top, and all 7 functions are up and running.

Thanks!

---

### Post by djcraft on 2007-08-25
I hope this get's added into the next version of Ubuntu. I'm sure there are pletty of upset people that have no idea how to modify a conf file with such a simple entry. I know it put a bit of a bad taste in my mouth having to setup something for such a common mouse manufacturer.

---

### Post by detyabozhye on 2007-08-25
> **djcraft said:**
> I hope this get's added into the next version of Ubuntu. I'm sure there are pletty of upset people that have no idea how to modify a conf file with such a simple entry. I know it put a bit of a bad taste in my mouth having to setup something for such a common mouse manufacturer.

Agreed

---

### Post by pbalir on 2007-08-25
Me, as well.....

Paul

(I guess the Ubuntu gurus read here?)

---

### Post by XTREEM|RAGE on 2007-08-26
> **detyabozhye said:**
> This guide is partly based on another one. I didn't write about the restarting part, and you are correct that is the more "correct" way of doing it.

Can u correct this also in the guide? Or is that not possible or something? ;x

---

### Post by ptitpoul on 2007-08-26
> **King Buttons I said:**
> I have an MX600 wireless mouse that came with the MX3200 keyboard. Evdev is installed on the computer. I am running Feisty Fawn.

I have two other questions: do I need evdev to continue with the guide? 
Hello, I have the same combo (MX600 & MX3200). My advice for you is to keep the "mouse" and "kbd" drivers because there is a bug in evdev with keyboard + mouse combo : [https://bugs.freedesktop.org/show_bug.cgi?id=7625](https://bugs.freedesktop.org/show_bug.cgi?id=7625)

---

### Post by King Buttons I on 2007-08-26
> **ptitpoul said:**
> Hello, I have the same combo (MX600 & MX3200). My advice for you is to keep the "mouse" and "kbd" drivers because there is a bug in evdev with keyboard + mouse combo : [https://bugs.freedesktop.org/show_bug.cgi?id=7625](https://bugs.freedesktop.org/show_bug.cgi?id=7625)

Did you get the special buttons on the mouse and keyborad to work? If so can you tell me how you did it?

---

### Post by ptitpoul on 2007-08-27
> **King Buttons I said:**
> Did you get the special buttons on the mouse and keyborad to work?
Not all. On the mouse, zoom buttons and horizontal wheel don't work (horizontal wheel is seen as left and right keys). On the keyboard, only 8 of the about 30 extra keys work (send an event), essentially multimedia keys at the top (volume, mute, previous, play, next).

I used btnx to link my thumb buttons to next and previous functions.

---

### Post by Dark Star on 2007-08-27
Very nice guide :) I was just wondering how to configure my Mouse Wireless Logi.. Mx 3200 set in Ubuntu :D This guide is really helpful :D

---

### Post by phyrewall on 2007-08-27
Can someone either post or PM me the way (xorg and all) they got their Logitech G5 working with BTNX? Thanks

(I can't get BTNX to detect my G5)

---

### Post by XTREEM|RAGE on 2007-08-27
I have another question: Does this guide also work with Mouse PS2 or only with usb mouses? I haven tried it yet, i'm glad it worked with the usb. but does have any1 tried it?

---

### Post by detyabozhye on 2007-08-29
> **XTREEM|RAGE said:**
> Can u correct this also in the guide? Or is that not possible or something? ;x

Done. I'd rather have someone else take over the whole tutorial because sometimes it takes me too long to make needed updates to it, I just don't have the time anymore.

---

### Post by detyabozhye on 2007-08-29
> **XTREEM|RAGE said:**
> I have another question: Does this guide also work with Mouse PS2 or only with usb mouses? I haven tried it yet, i'm glad it worked with the usb. but does have any1 tried it?

AFAIK, it's USB only, but I don't know if that's changed with new versions of evdev or not.

---

### Post by XTREEM|RAGE on 2007-08-29
@detyabozhye
Nice, but to bad you dont have the time to update anymore. I wish i have the linux skills, so i could maintain this thread ;D

---

### Post by astroman on 2007-08-30
I followed the guide and my MX518 works great now, but if I try to boot with the mouse unplugged the x server does not start.  This is a problem since I'm on a laptop and I don't always have my mouse with me.  Does anyone know of a way to get around this?  I'm running Feisty 7.04 on an Inspiron E1405.

---

### Post by AnotherMuggle on 2007-08-30
My backward and forward buttons work for the most part but occasionally they do not, a reboot seems to fix this.

Does anyone know why?

---

### Post by 5h4rk on 2007-08-30
My mouse (mx500) is now tooo fast.

I tried to change motion from system > preferences > mouse > motion, but nothing happened, it seems that whatever i change there it doesnt affect the mouse...

someone know whys that?

thanks

---

### Post by measekite on 2007-09-28
> **ewerx said:**
> I have a G7 and I also could not start X after the restart. 

Output from /proc/bus/input/devices that relate to my mouse:
```
I: Bus=0003 Vendor=046d Product=c51a Version=4100
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.7-4.1.2/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse0 event3 ts0
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0003 Vendor=046d Product=c51a Version=4100
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.7-4.1.2/input1
S: Sysfs=/class/input/input4
H: Handlers=kbd event4
B: EV=f
B: KEY=c0002 400 0 0 1 f80 78000 6039fa d84157ad 8e0000 0 0 0
B: REL=40
B: ABS=1 0

```I'm not sure why there are two listed here, could that be the problem?

My 19-local.rules:
```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", NAME="input/event9"

```My xorg.conf is identical to the example.

My X.org log file from the failed restart (only the parts that seem significant, added highlighting on what i think might be the error):
```
(II) Initializing extension GLX
**error opening security policy file /etc/X11/xserver/SecurityPolicy**
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
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
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
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/wacom"
[B](EE) xf86OpenSerial: Cannot open device /dev/wacom
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
Error opening /dev/wacom : No such file or directory[/B]
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) 3rd Button detected: disabling emulate3Button

```Looks like the same warnings hubacap is getting... not sure what that wacom stuff is, since I don't have a tablet or anything like that. The Logitech G7 mouse and a Microsoft Keyboard are the only input devices I have.

I have the same setup and get the same thing, the repetition and all.  To boot up  properly make sure that you say evdev for BOTH the driver and the Protocol.

Then you should boot up as I.  However, I still cannot get my side button (most important) and the tilt left and right on the scroll wheel to work.

If you solved all of these issues please post.

---

### Post by BLTicklemonster on 2007-09-28
I installed Gusty beta fresh on a drive and only did xmodmap, and my mouse won't do my forward back thingy.

---

### Post by nibsa1242 on 2007-10-15
Can't wait to see the Gusty revision of this, I need to update mine... I didn't change anything from 6.10 to 7.04 and its been complaining about not referencing something directly as they might change with a future kernel revision. More details next time I reboot, but I think it was udev related and that hopefully isn't required anymore anyway.

---

### Post by Poka64 on 2007-10-20
This guide doesn't work for me anymore in Gutsy, it worked in both Feisty and Edgy.

The thing is, I followed the guide and got it working, I even rebooted a couple of times and it still worked. But suddenly the mouse stoped working, I had to revert back to the "mouse0" to get the damn thing working again.

The resolution thing still works, but if I try to change the settings to "evdev" "corepointer", it stops working :(

My xorg.conf (relevant part of it)
I even disabled the wiimote but it did not solve the issue with the mouse :(
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0"	
#InputDevice    "Configured Mouse" "CorePointer"
    InputDevice     "Wiimote" "AlwaysCore"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "Extensions"
Option "Composite" "true"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

#Section "InputDevice"
#Identifier	"Configured Mouse"
#Driver		"evdev"
#Option		"CorePointer"
#Option		"Name"	"Logitech USB-PS/2 Optical Mouse" #this should be the name of the device which I made bold here.
#EndSection

Section "InputDevice"
    # generated from default
Identifier     "Mouse0"
Driver         "mouse"
Option         "Protocol" "auto"
Option         "Device" "/dev/psaux"
Option         "Emulate3Buttons" "no"
Option         "ZAxisMapping" "4 5"
EndSection

#Section "InputDevice"
#Identifier	"Configured Mouse"
#Driver		"evdev"
#Option		"CorePointer"
#Option		"Device"	"/dev/input/event9"
#EndSection

#Section "InputDevice"
#Identifier	"Configured Mouse"
#Driver		"evdev"
#Option		"CorePointer"
#Option		"Device"	"/dev/input/mx510"
#EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
Identifier      "Wiimote"
Driver          "evdev"
Option          "Name"          "Nintendo Wiimote"
EndSection
```

---

### Post by Argling on 2007-10-22
Hello all.. another part-time convert joins the forums.

Been planning to sign up to these forums for a couple days, but this guide was so helpful i simply had to say: MAJOR THANKS to all those involved in the creation and evolution of this guide. Been struggling to put my mouse buttons to good use for a couple days now. Until I found this guide. 

One minor thing that kept me busy for a while: Trying to save a few "sudo"s, I opened a Root Terminal and followed the guide there. This naturally caused the "gedit ~/.xbindkeysrc" command to create the config file in the Root directory, rather than in the Home of my ordinary user. Obviously, this prevented the mouse buttons from functioning as I intended... until I learned my lesson:

"When a guide tells you to issue a command without "sudo" in front of it, it's not always because the command itself doesn't  *require*  Root access"

---

### Post by mrbamboo on 2007-10-23
I'm having trouble getting my MX518 to work on Gutsy Gibbon.
I can't get the backward and forward button to be recognized. 
Whenever I try to set the driver to "evdev" and i reboot, i get put into low graphics mode because it doesn't recognize the mouse or something. When I have the protocol set to ImPS/2 the back+forward button instead of 6 7 is interpreted as 2 and 3 according to xev. when i use ExplorerPS/2 those two buttons aren't recognized at all, xev returns some thing that ends with a lot of 0 0 0s and no button number. 

Any idea how to fix this?

---

### Post by Sol1 on 2007-10-24
I'm in the same boat.  My mouse worked fine in Feisty, but won't work at all now that I've upgraded to Gutsy.  

cat /proc/bus/input/devices will show the USB hub but not the mouse itself.  Any suggestions?

**EDIT: Nevermind, I'm an idiot...**

---

### Post by bubble_bobble on 2007-10-26
I have two mice. A logitech mx310 and a logitech lx3.

The mx310's (5) buttons all work (except for cruise control). The 2 side buttons work correctly.

I am having an issue with my lx3 (3 button mouse with tilt wheel). The middle button is recognized (it doesn't cruise control but that's not important to me), but the tilt wheel's back/forward button functions don't work.

Is there a way to define the tilt wheel's back/forward buttons by modifying some magic text file?

I have followed the guide, but have encountered a couple problems.

1) If I set my Driver to "evdev", X won't start.
2) When I sudo lomoco -8, I get the following error:

004.002: 046d:c044 Unsupported Logitech device: USB-PS/2 Optical Mouse

I would attach /proc/bus/input/devices and xorg.conf instead of straight up posting it to save space, but the system won't let me for some reason. I will just post it if someone thinks it's important.

---

### Post by madestro on 2007-11-08
Thnaks a lot !!! I have a MX518 and by doing section 1 only I was able to get the back forward and scroll wheel to function just like in Winbored. Thanks again !!!

---

### Post by BLTicklemonster on 2007-11-10
Okay, I was having fits in Gutsy, and even tried btnx which is nice, but I had several functions occur at a time when I used forward and back, so... I went back to the drawing board, and got it right with xmodmap.

First

sudo /etc/X11/xorg.conf 

then I changed the mouse to

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/psaux"
Option "Protocol" "auto"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "no"
EndSection

then

> **BLTicklemonster said:**
> ```
Section "InputDevice"
   # generated from default
   Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection
```

Here is my new xorg.conf.

Each button relates to a number, and running xev in terminal will show that. Now if I knew what number, in order, in this line

pointer = 1 2 3 6 7 8 9 4 5 (picked out arbitrarilly)

related to what function, I could edit this myself. But I think it's time to open a text editor, and start testing different settings and paste results...


*edit: 

for an MX310 MOUSE...

said results being:

```
settigs were:

pointer = 1 2 3 6 7 8 9 4 5


xev said:
1 left click button 1
2
3 right click button 3
4 back side button 4 
5 forward side button 5 
6
7
8 wheel up 6 
9 wheel down 7
(clarification: xev didn't actually say that... I listed one through nine, then clicked each button and listed it next to its respective space with notation as to what was happening)
therefore:

pointer = 1 2 3 4 5 8 9 6 7
```
 
Let me clarify that a little further...

My mouse has nine buttons, so I listed 1 through nine, then drew a picture of my mouse and used xev (run from terminal) to see which button was numbered to do what. My side buttons were scrolling, numbered 4 and 5, and I knew that I wanted the wheel to scroll, so I noticed that 6 and 7 were my scroll wheels, and hey, when I scrolled, I was going forward and back in web pages, so it was simply a matter of moving the numbers around to the right places. 

and now things are groovy

HOT DANG, I FIGURED SOMETHING OUT~!!

GOD I LOVE LINUX! TRY THIS IN WINDOWS~!!! no wait, I'd not have had this problem in windows... oh well, GOD I LOVE TINKERING!!!!


I hope this will help everyone who is having problems, and thank you detyabozhye for this whole thread!


*edit:
not sure why I worried, but I rebooted just to see what would happen, and no x failure this time, and all buttons are working.

Rebooted, and all was swell.

---

### Post by r!ots on 2007-11-17
hey,

I got a question: will this work on a notebook? does it automatically switch between the touchpad and the mouse? will it still boot without problems?
on my desktop-pc i'm having troubles booting if my MX500 isn't plugged in, so i'm wondering what will happen if i boot the notebook without the MX500 plugged in.

thx.

---

### Post by private_lock on 2007-11-23
Hello detyabozhye!

This is really a great thread, though it took me some days to read all of it. Thank you for all this work.

What I needed in addition to section one of your first posting was [_posting 369_](http://ubuntuforums.org/showpost.php?p=1935429&postcount=369) from zorglab in this thread. Maybe you can copy it or repeat the link in your tutorial.

Moreover I found it worthwhile to read these manpages:
```

man xor.conf
**man evdev**
man synaptics
man synclient
man mousedrv

```

Perhaps you can also include the firefox-horizontal-scroll-hint, because it has been asked over and over again.

Thanks a lot

---

### Post by jaguarz on 2007-11-25
Nice topic, helped me with my MX310, thanks again!

---

### Post by detyabozhye on 2007-12-02
To all the Gutsy users: This tut is quite outdated by now. It's recommended you use the mouse autodetection evdev configuration now, it looks like this:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option "evBits" "+1-2"
        Option "keyBits" "~272-287"
        Option "relBits" "~0-2 ~6 ~8"
        Option "Pass" "3"
EndSection

```

and the serverlayout section for the mouse should look like this (It cannot be corepointer!):
```
        Inputdevice     "Configured Mouse" "SendCoreEvents"
```

---

### Post by agds on 2007-12-02
> **detyabozhye said:**
> To all the Gutsy users: This tut is quite outdated by now. It's recommended you use the mouse autodetection evdev configuration now, it looks like this:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option "evBits" "+1-2"
        Option "keyBits" "~272-287"
        Option "relBits" "~0-2 ~6 ~8"
        Option "Pass" "3"
EndSection

```

and the serverlayout section for the mouse should look like this (It cannot be corepointer!):
```
        Inputdevice     "Configured Mouse" "SendCoreEvents"
```

Thanks, man.  That worked beautifully.

---

### Post by onion221 on 2007-12-02
So I replace this code```
 Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"Logitech USB-PS/2 Optical Mouse" #this should be the name of the device which I made bold here.
EndSection
```

With this  ```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option "evBits" "+1-2"
        Option "keyBits" "~272-287"
        Option "relBits" "~0-2 ~6 ~8"
        Option "Pass" "3"
EndSection
```

during the tut?

---

### Post by sonasi on 2007-12-02
> **detyabozhye said:**
> To all the Gutsy users: This tut is quite outdated by now. It's recommended you use the mouse autodetection evdev configuration now, it looks like this:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option "evBits" "+1-2"
        Option "keyBits" "~272-287"
        Option "relBits" "~0-2 ~6 ~8"
        Option "Pass" "3"
EndSection

```

and the serverlayout section for the mouse should look like this (It cannot be corepointer!):
```
        Inputdevice     "Configured Mouse" "SendCoreEvents"
```

YES!!  Thank you so much - awesome tut update!

---

### Post by FreewheelinFrank on 2007-12-05
Thanks! Worked for me with a Logitech V150.

My mouse seems to be much better behaved now.

The autodetection configuration works too.

---

### Post by FreewheelinFrank on 2007-12-05
Is there any way to switch the direction of the scroll wheel tilt function: at the moment, tilting right has the 'back' function in Firefox and Opera, which is counter-intuitive?

---

### Post by detyabozhye on 2007-12-06
> **onion221 said:**
> So I replace this code```
 Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"Logitech USB-PS/2 Optical Mouse" #this should be the name of the device which I made bold here.
EndSection
```

With this  ```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option "evBits" "+1-2"
        Option "keyBits" "~272-287"
        Option "relBits" "~0-2 ~6 ~8"
        Option "Pass" "3"
EndSection
```

during the tut?

Yes

---

### Post by detyabozhye on 2007-12-06
> **FreewheelinFrank said:**
> Is there any way to switch the direction of the scroll wheel tilt function: at the moment, tilting right has the 'back' function in Firefox and Opera, which is counter-intuitive?

Um, you'd have to play around with Xmodmap for that.

---

### Post by FreewheelinFrank on 2007-12-09
> **detyabozhye said:**
> Um, you'd have to play around with Xmodmap for that.

Thanks.

Unfortunately that mouse died soon after. :-({|=

However I found a cheap wireless mouse with side buttons. I can confirm that the instruction on page 1 (Section 2: Side buttons and Nautilus, Epiphany, Konqueror, etc (Optional)) also work for the Trust Wireless Optical Mouse MI-4910D, although I had to change the button numbers from 6 & 7 to 8 & 9.

Many thanks to detyabozhye.

---

### Post by Lazlo Woodbine on 2007-12-09
> **detyabozhye said:**
> To all the Gutsy users: This tut is quite outdated by now. It's recommended you use the mouse autodetection evdev configuration now, it looks like this:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option "evBits" "+1-2"
        Option "keyBits" "~272-287"
        Option "relBits" "~0-2 ~6 ~8"
        Option "Pass" "3"
EndSection

```

and the serverlayout section for the mouse should look like this (It cannot be corepointer!):
```
        Inputdevice     "Configured Mouse" "SendCoreEvents"
```


I'm a new Gutsy user, and have an MX 700 (from the MX Duo set - apparently not quite the same as the standalone MX 700). I've edited xorg.conf per these instructions, but it doesn't quite work for me. Running xev, I find that some of the mice buttons are mapped to the same number (right mouse button is the same as upper thumb button).

Can you help me? For an OS that appears in all other ways to be generally easier than Windows to set up, the more complex, terminal based steps that are required to get a common mouse working fully is just unbelievable!


[EDIT]  Starting up Ubuntu this morning the problem seems to have been resolved. Hopefully this was just a false alarm, and things will continue to work as expected.  [/EDIT]

---

### Post by detyabozhye on 2007-12-10
> **Lazlo Woodbine said:**
> Can you help me? For an OS that appears in all other ways to be generally easier than Windows to set up, the more complex, terminal based steps that are required to get a common mouse working fully is just unbelievable!

Yeah, Xorg is still a little silly when it comes to configuration, IMHO. But that should be fixed in Xorg 7.3 or 7.4 I believe

---

### Post by bizzu on 2007-12-23
I recently bought the new MX620, and the evdev autoconfiguration worked perfectly for me.
I only had to add 2 more lines in xorg.conf, because in /proc/bus/input/devices there were 2 devices with the same name; so I told evdev which one to configure:
```

Option		"Dev Phys"	"usb-*/input1"
Option		"Device"	"/dev/input/event2"

```

Now I'm searching for a software that can enable my mouse's 800cpi resolution... lomoco doesn't support it yet. I'm contacting lomoco's mailing list looking for support ;)
Stay tuned :popcorn:

---

### Post by cp1969 on 2007-12-27
> **bofphile said:**
> This guide works perfectly with my Logitech LX7. :) 
Thanks a lot detyabozhye !

Wow...what a thread.  I admit to not having read all 60 or so pages of it.

I got an LX7 cordless mouse as a gift and would really like to use it.  From the above post, I took encouragement as this poster is using 7.10, the same as me.  But when I look at the date of the post, it could not have been 7.10, most likely 6.06 which was the most current at that time.

Question: Anything about 7.10 that makes it incompatible with the Logitech LX7?

Thanks!

---

### Post by Weazl2000 on 2007-12-28
> **dejitarob said:**
> For my purposes (MX500) all I had to do is edit /etc/X11/xorg.conf to contain the following under "Configured Mouse:"
```
Option "Protocol" "ExplorerPS/2"
Option "Buttons" "5"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"
```This actually works on my [Evoluent]("http://www.evoluent.com/vm3.html") mouse too :]

I had to use this to get my MX620 working, Using the long method would do something weird and my nvidia driver would stop functioning. Also I'm using Gutsy Gibbon this was my only way to make it work, or at least the easiest. Thanks

---

### Post by cp1969 on 2007-12-30
> **cp1969 said:**
> Wow...what a thread.  I admit to not having read all 60 or so pages of it.

I got an LX7 cordless mouse as a gift and would really like to use it.  From the above post, I took encouragement as this poster is using 7.10, the same as me.  But when I look at the date of the post, it could not have been 7.10, most likely 6.06 which was the most current at that time.

Question: Anything about 7.10 that makes it incompatible with the Logitech LX7?

Thanks!

Finally got around to installing the LX7 wireless mouse in 7.10.

First, I installed it in XP.  No problems.  Other than having to download a 53Mb driver, it went off without a hitch.

So, I decided to try to make it work with ubuntu 7.10.  Shut down XP and booted up into ubuntu, and....surprise, it works pretty darn well without doing anything at all.  All the buttons and the wheel are functional, however the two little buttons don't function as page forward/back as they do in XP.  The left small button functions as 'open in a new tab' in Firefox; the right small button functions as right click.

So, I have a 5 button mouse that has left click, two right clicks, an open in new tab, and the wheel without doing anything at all.

I think I'm pretty happy with it as is, so I might not try to change anything unless it becomes a limitation sometime in the future.

---

### Post by Weazl2000 on 2007-12-30
> **cp1969 said:**
> Finally got around to installing the LX7 wireless mouse in 7.10.

First, I installed it in XP.  No problems.  Other than having to download a 53Mb driver, it went off without a hitch.

So, I decided to try to make it work with ubuntu 7.10.  Shut down XP and booted up into ubuntu, and....surprise, it works pretty darn well without doing anything at all.  All the buttons and the wheel are functional, however the two little buttons don't function as page forward/back as they do in XP.  The left small button functions as 'open in a new tab' in Firefox; the right small button functions as right click.

So, I have a 5 button mouse that has left click, two right clicks, an open in new tab, and the wheel without doing anything at all.

I think I'm pretty happy with it as is, so I might not try to change anything unless it becomes a limitation sometime in the future.

This is the same thing that happened to me, using the above method made everything functional except for my wheel tilt.

---

### Post by der_joachim on 2008-01-06
Thanks for this great tut! 2 Things:

Unless there is an entirely new howto for Gutsy, perhaps it would be advisable to add a Gutsy section to the first post. The earlier version works swimmingly as well in gutsy (at least it did for me), but I suspect that the autodetect method is less complicated for new users. 

The other thing is a hopefully simple question: did any MX400 owners get lomoco to play nice with their mouse?

---

### Post by detyabozhye on 2008-01-07
> **der_joachim said:**
> Thanks for this great tut! 2 Things:

Unless there is an entirely new howto for Gutsy, perhaps it would be advisable to add a Gutsy section to the first post. The earlier version works swimmingly as well in gutsy (at least it did for me), but I suspect that the autodetect method is less complicated for new users. 

The other thing is a hopefully simple question: did any MX400 owners get lomoco to play nice with their mouse?

Yeah, we need to make a new guide for Gutsy, but I personally don't have the time to do it anymore, so I don't know if I will do it.

---

### Post by anjie on 2008-01-10
Hello,

This is my first message! Firstly thanks for this nice guide for my mouse. It works quite perfectly now! Quite, why? Well, if it is plugged in, it works perfectly. But if I switch on my laptop and my mouse is not plugged in, because for example, I want to use the touchpad, the graphic interface won't load anymore. Instead I have a blue page that let me diagnose the problem.
How to solve the problem? Should I add something in my xorg.conf ?

Here it is

```


Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
EndSection

# older mouse configuration




# Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"		"/dev/input/mice"
#	Option		"Protocol"		"ImPS/2"
#	Option		"ZAxisMapping"		"4 5"
#	Option		"Emulate3Buttons"	"true"
# EndSection


Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"Logitech USB Optical Mouse"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option   	"SHMConfig" 		"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Driver		"via"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Monitor Generico"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Monitor		"Monitor Generico"
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
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

``` 

I'm running Ubuntu 7.04 !

Thanks for your kind help,

Anjie

---

### Post by tweedledee on 2008-01-11
> **anjie said:**
> Hello,

This is my first message! Firstly thanks for this nice guide for my mouse. It works quite perfectly now! Quite, why? Well, if it is plugged in, it works perfectly. But if I switch on my laptop and my mouse is not plugged in, because for example, I want to use the touchpad, the graphic interface won't load anymore. Instead I have a blue page that let me diagnose the problem.
How to solve the problem? Should I add something in my xorg.conf ?


Most likely you need to change the "option corepointer" line to "option sendcoreevents true" (as it it appears for your touchpad just below your mouse section).

---

### Post by kodacy on 2008-01-11
worked for my mx518:KS

---

### Post by anjie on 2008-01-12
> **tweedledee said:**
> Most likely you need to change the "option corepointer" line to "option sendcoreevents true" (as it it appears for your touchpad just below your mouse section).

Thanks tweedledee!! Perfect!! It worked nicely!

Bye,

Anjie

---

### Post by PLAY3ER on 2008-01-14
Thanks for this, it was driving me nuts, now it works like it does in windows.

PLAY3ER

---

### Post by charonn0 on 2008-01-24
This works perfectly for my mx518. Thanks so much!

PS,
I got the + and - keys to work by installing lomoco

```
sudo apt-get install lomoco
```

---

### Post by deserter on 2008-01-28
Found a solution for wireless Logitech LX7.

The following xorg.conf allowed xev to recognize the side buttons as buttons number 8 and 9.

```
Section "InputDevice"
	Identifier	"Logitech Wave Mouse" #The same as in Section "ServerLayout"
	Driver		"evdev"
	Option		"Device"    "/dev/input/event2" #from "cat /proc/bus/input/devices"
	Option		"SendCoreEvents"   "true"
        Option		"Name" "Logitech USB Receiver" #from "cat /proc/bus/input/devices"
EndSection
```

The problem was that the side buttons did nothing, so I used xvkbd&xbindkeys solution described in the tutorial. 
I wasn't too happy about that though... I launched Enemy Territory and it recognized them both as KP_Equals or similar.

The solution was then to:
```
sudo apt-get install xinput
xinput list
xinput set-button-map "Logitech Wave Mouse-usb-0000:00:11.2-2/input1" 1 2 3 4 5 8 9 6 7 10 11 12
```

Where "Logitech Wave Mouse-usb-0000:00:11.2-2/input1" is copied from "xinput list" output.

Now xev recognizes the buttons as 6 and 7 and everything works as it should. 
(I'm not sure if xmodmap could have done the same actually... I tried it and saw no effect - probably just misuse! :D)

Nautilus doesn't go back/forward at the moment, so I think that you have to use xbindkeys as well anyway.

---

### Post by cb_rex on 2008-01-30
To get the side buttons working on my Logitech G3 mouse I followed the guide way back on page 1, substituting b:6 for b:8 and b:7 for b:9 in xbindkeysrc, as suggested for tilt wheel mice, even though the G3 has a normal scroll wheel.

My mouse now works perfectly, thanks.

---

### Post by dvord on 2008-02-04
In my 7.10 Installation I was having problems getting these steps to work for my Logitech MX518.  In fact X bombed out on me from the first edit.

I dug up some old notes I had when I was trying to get this to work with 6.0?

I simply dropped this in:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Buttons" "5"
	Option		"ZAxisMapping" "4 5"
	Option		"ButtonMapping" "1 2 3 6 7"
	Option		"Name"	"Logitech USB-PS/2 Optical Mouse"
EndSection
```

---

### Post by danlee on 2008-02-16
This may have already been pointed out, but its a big thread and I would suggest that it be added to main page as it helped me out.

[http://www.chrisweldon.net/2007/01/19/xorg-71-and-evdev-problems-solved](http://www.chrisweldon.net/2007/01/19/xorg-71-and-evdev-problems-solved)

Basically I just needed to add:
```
“SendCoreEvents”
```
After the input mouse declaration in the ServerLayout section.
So mine looked like:
```
Section “ServerLayout”
...
InputDevice “Configured Mouse" "SendCoreEvents"
...
EndSection
```
After that it worked like a treat :D

---

### Post by sx5622 on 2008-02-27
I was able to get the side buttons on my Mx518 to work (excellent), but I was using two mice before (I had them both plugged in at the same time) and now my other mouse (trackball) doesn't work.  Any suggestions??

-Steve

I apologize for being an uber n00b.

Also, here is what my original xorg.conf looked like:

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

```

Here is what I replaced it with:

```


Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"Logitech USB-PS/2 Optical Mouse"
EndSection

```

THANKS!

---

### Post by singedwings on 2008-04-23
I have just tried the guide on page 1 on **ubuntu 8.04 rc 64bit**, but it appears not to work. After making the changes to my xorg.conf I was able to restart udev, and x. However the mouse will not respond, although the laser is lit.

I suppose that some sort of changes have been made between 7.10 and 8.04?

The extra buttons on my logitech mx518 work within firefox with the standard setup from installing ubuntu. Thus I also tried the following instructions to see if I could get the buttons to work in Nautilus anyway without the udev driver, no joy, but my linux ability is a bit limited so I do not know how to analyse what is not working in this situation.

---

### Post by tweedledee on 2008-04-24
> **singedwings said:**
> I have just tried the guide on page 1 on **ubuntu 8.04 rc 64bit**, but it appears not to work. After making the changes to my xorg.conf I was able to restart udev, and x. However the mouse will not respond, although the laser is lit.

The problem is most likely that the X developers changed evdev to no longer use the "name" option to identify devices; instead you must use a device ID.  See [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/173833](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/173833) for discussion and (in the lower half) solutions.

---

### Post by Eazy© on 2008-04-28
In Ubuntu 8.04. I need to add ```
Option         "Device" "/dev/input/event3"
``` and it works, but when I start UT2004 the mouse is acting up. I can't use the mouse at all. It's like the mouse-pointer is outside the game-window or something. When I start playing, its like having 1000000 in sensitivity on the mouse and all I see is the floor. 

I'm using Kubuntu, and in kcontrol I can choose form 50 different keyboards. Why is it that there is no mouse to choose. I think its really bad that 2008 we still have to edit xorg.conf to have all buttons on our mouse working. Isn't the mouse next to the keyboard the most important tool we use on a computer?

Well, enough whining, hope someone has an solution to my problem.

Regards
Eazy

---

### Post by Eazy© on 2008-04-28
double post

---

### Post by chrisblue on 2008-04-29
> **Eazy© said:**
> snip

I'm using Kubuntu, and in kcontrol I can choose form 50 different keyboards. Why is it that there is no mouse to choose. I think its really bad that 2008 we still have to edit xorg.conf to have all buttons on our mouse working. Isn't the mouse next to the keyboard the most important tool we use on a computer?

Well, enough whining, hope someone has an solution to my problem.

Regards
Eazy


I agree. This is an area that could use a lot more work I think. Wish I had the actual skills to do something other than just whinge :)

---

### Post by tweedledee on 2008-04-29
> **Eazy© said:**
> I'm using Kubuntu, and in kcontrol I can choose form 50 different keyboards. Why is it that there is no mouse to choose. I think its really bad that 2008 we still have to edit xorg.conf to have all buttons on our mouse working. Isn't the mouse next to the keyboard the most important tool we use on a computer?

Have you tried btnx?  You can find information via Google and in other forum threads.  It's still beta and must be compiled, but especially given that evdev is harder to work with now than in previous versions of Ubuntu, it's probably worth your time to look into it.  I think it still has a long way to go to be a major improvement over hand editing xorg.conf, but for some situations it works well.

---

### Post by totaldrk62 on 2008-04-30
> **tweedledee said:**
> Have you tried btnx?  You can find information via Google and in other forum threads.  It's still beta and must be compiled, but especially given that evdev is harder to work with now than in previous versions of Ubuntu, it's probably worth your time to look into it.  I think it still has a long way to go to be a major improvement over hand editing xorg.conf, but for some situations it works well.

I just compiled and tried btnx and it doesn't seem to work for me. I am using an MX700 and had everything working fine in 7.10 but now 8.04 isn't working right. Originally I couldn't use my mouse at all. I went back and took out the evdev lines in my xorg and used the original lines and now I have a mouse. My forward and back buttons (where my thumb sits) no longer work in Nautilus but do work fine in Firefox. Which is what I went through all the work to get evdev working for in the first place (seriously Ubuntu...hours of work to able to navigate the filesystem easily?). 

My understanding of the problem is that evdev no longer uses the "Name" option from xorg. Instead they are using the device id which I am not sure how to find. 

The 7.10 portion of my xorg that worked:
 
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"Logitech USB Receiver" 

And the relative cat info:

I: Bus=0003 Vendor=046d Product=c506 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.1-3/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.1/usb3/3-3/3-3:1.0/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=20017
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10
B: LED=ff00


Anyone have any ideas where to go from here?

---

### Post by tweedledee on 2008-04-30
> **totaldrk62 said:**
> My understanding of the problem is that evdev no longer uses the "Name" option from xorg. Instead they are using the device id which I am not sure how to find. 

In a truly brilliant move, the evdev/xorg developers decided Name was far too easy.  The id you are looking for cannot be found except by looking in /dev/input/by-id/ (or /dev/input/by-path/, but some people have reported less success with that).  From there, it's a bit of guesswork to figure out the correct device to use.  Theoretically once you have the correct id, things should work more or less as in previous versions.

---

### Post by Tetyl on 2008-05-02
Indeed, the problem is that Name no longer works. After locking up my mouse several times I've got my G5 working just fine.

I listed the /dev/input/by-id directory and saw:

```
usb-Logitech_USB_Gaming_Mouse-event-mouse
usb-Logitech_USB_Gaming_Mouse-mouse
usb-Microsoft_Microsoft_Digital_Media_Pro_Keyboard-event-kbd
```

I first tried the "usb-Logitech_USB_Gaming_Mouse-mouse" entry but that made the mouse stop responding so I tried the "usb-Logitech_USB_Gaming_Mouse-event-mouse" entry, restarted once more and that got everything working perfectly.

Here's my xorg.conf:

```
Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "evdev"
	Option "CorePointer"
	Option  "Device" "/dev/input/by-id/usb-Logitech_USB_Gaming_Mouse-event-mouse"
EndSection
```

---

### Post by Jolly Roger on 2008-05-05
Tetyl's instructions in the post above mine worked perfectly for me. i just replaced the name attribute with device and used the event-mouse entry that i found in /dev/input/by-id. awesome. thanks Tetyl!

---

### Post by FokkerCharlie on 2008-05-17
Hi All

I wonder if anyone can point me in the right direction?  I have a Logitech Trackman Wireless, which worked out of the box in Hardy, with the following exception:

The 'scroll up' button (not moving the wheel, the button above it) scrolls up in Firefox and ALSO causes the browser to go back a page.

In other apps, the scroll up button works as expected.  It looks like the button is mapped twice or something- btnx also suggested this.

My xorg.conf:
[http://www.pastebin.ca/1021083](http://www.pastebin.ca/1021083)

cat /proc/bus/input/devices:
[http://www.pastebin.ca/1021085](http://www.pastebin.ca/1021085)

Any ideas?  I have tried all sorts of shenanigans, but am stuck with this irritation!

***EDIT***  After installing xbindkeys, I see the same behaviour in nautilus!
It also is a problem in IE with XP under VirtualBox, but not when I boot into Vista.  So it looks like an Ubuntu / X / Gnome problem or something.

***ANOTHER EDIT***  running xev, when I press the up button, it returns a press for both 4 and 8- corresponding to back and up- now we're getting somewhere...  please give me the final piece of the puzzle!

Help!  I'm stuck!

Thanks in advance
Charlie

---

### Post by strider2k on 2008-06-08
I have a Logitech V200. Does anyone have mouse cursor movement problems?  When I try moving my mouse left or right, the cursor goes upleft and downright respectively.

I'm running Ubuntu 8.0.4 Hardy Heron on a Thinkpad T61.

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"Name"	"Logitech USB Receiver"
	Option		"ZAxisMapping"	"4 5"
	Option		"HWHEELRelativeAxisButtons"	"7 6"
EndSection

```

Side note: When running "xev", my left-tilt of the wheel is button 8 while right-tilt of the wheel is not captured by "xev".

---

### Post by hemebond on 2008-06-10
Documenting for future me. Logitech mx518 with **all buttons available** including the "switch application" button on the top. The xmodmap fix is for Firefox which changed to include horizontal scrolling; apparently bringing it inline with other GTK applications but breaking the ability to go back/forward using the thumb buttons.

/etc/X11/xorg.conf```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "evdev"
    Option         "Device" "/dev/input/by-id/usb-Logitech_USB-PS.2_Optical_Mouse-event-mouse"
EndSection
```~/.Xmodmap```
pointer = 1 2 3 4 5 8 9 6 7
```If there's somewhere else I should be documenting this please let me know.

---

### Post by ricardisimo on 2008-06-13
There are 16 pages to this thread, with 40 posts per page, so I hope no one will be too angry if I just ask whether my case is the same as theirs, or if some portion of this thread will pertain to me.

Since installing Kubuntu Hardy, my Logitech optical mouse (USB with a mouse port adapter plug) has proven to be far too sensitive, and I can' t seem to modify the settings enough to make it behave. Right-clicking on links in Firefox works about half the time (that is, I get a drop-menu), while the rest of the time a ghost-click selects some menu item I don't want.

Also, my screensaver never activates - I'm assuming because of more ghost-signals from the mouse -  and since this is my work comp, I kind of need to have my session lock if I'm away for too long.

Here's the pertinent lines from xorg.conf:
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection
```
Wow, even just now, when I right-clicked to get the "Paste" option, all I got to do was right-click, and it instantly pasted what was in my clipboard. At least it chose the right option for me. Thanks in advance for any help anyone can give.

---

### Post by ricardisimo on 2008-06-14
Anyone?

---

### Post by akxiii on 2008-06-27
[FONT="Verdana"]Here is how I got my G7 Logitech mouse to kick butt! I'm not sure what is entirely necessary, all I know is that it works the way I want it to :) This recognizes all keys (in xev, though I'm not sure it ever appeared correctly in there) except for the precision ones + (4) and - (5) on the mouse, but they were already working for me. I hope this helps everyone out there, because it took me staying up till [FONT="Century Gothic"]2:30[/FONT] in the am to figure out.[/FONT]

in xorg.conf
```

Section "InputDevice"
	Identifier	"Logitech G7"
	Driver		"evdev"
	Option		"Name"	"Logitech USB Receiver"
	Option		"HWHEELRelativeAxisButtons" "7 6"
	Option 		"Device" "/dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse"
EndSection
```

note: That Device portion above is all one line, copy and paste kids.

#then my server layout section looks like this

```
Section "ServerLayout"
	Identifier	"Default Layout"  
	screen 0 "Default Screen" 0 0
	Inputdevice "Logitech G7"
EndSection
```

I'm not sure if this part is needed (but it is late, and it works this way, anyway the part that is changed/added was the Inputdevice "blahblahblah" part
Ok, so save that xorg and restart udev, and reload your session (this is all explained more thoroughly in the first few lines of the very first post)

And finally I installed keybind from the first few lines of this post. Where my actual keybind file looked like this

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:7
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Home]""
  m:0x0 + b:8

```

This gets the tilt on the mouse wheel all Hunky Dory with moving forward and backwards, and sets the thumb button to go to your home page.

I didn't bother doing the "cruise" feature because I think it is dumb. If you want to bind it like the others it is the 2nd button on the mouse. Best of luck!

Also, from experience: Having CorePointer in my xorg.conf forced ubuntu to ignore my monitor settings... so yeah, it was fun working my way out of that hole repeatedly.

[SIZE="2"]For reference my computer looks like the following:
compaq keyboard mouse duo where i only use the keyboard (wireless)
logitech g7 mouse (actually had two spots in the cat file)
Hardy Heron
Compiz and Emerald are on there too making things difficult
Monitor: Dell E172FP[/SIZE]

---

### Post by babucher on 2008-07-04
Greetings,

I've spent a number of hours reading through various threads, and am stuck, so any help would be appreciated.

--- Hardware ---
Macbook Pro 4,1 (penryn CPU) 2.5 GHz
Logitech Mx500 mouse

--- Software ---
Ubuntu 8.04 ("For standard computer")


I've installed Ubuntu sucessfully, and am now trying to get my mouse buttons working, right now for the game Wolfenstein Enemy Territory.  The problem is that the thumb buttons (forward and backward) both are registering as "KP_EQUALS" instead of MOUSE4 and MOUSE5.  Here is what the buttons register as in ET.  If there is a better way of determining what they buttons linked to, I would appreciate information on that as well.

left mouse button: MOUSE1
right mouse button: MOUSE2
mousewheel up: MWHEELUP
mousewheel down: MWHEELDOWN
depressing the mousewheel: MOUSE3
forward thumb button: KP_EQUALS
backward thumb button: KP_EQUALS


I've followed the directions from the first post in this thread as follows:

sudo apt-get install xserver-xorg-input-evdev
cat /proc/bus/input/devices

--- begin quote ---
I: Bus=0003 Vendor=046d Product=c025 Version=0110
N: Name="B16_b_02 USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:1a.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2:1.0/input/input1
U: Uniq=
H: Handlers=mouse1 event1
B: EV=20017
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10
B: LED=ff00
--- end quote ---

Side question: Why does my Mx500 have a different name than the Mx500 as detected by detyabozhye in the first post?

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo gedit /etc/X11/xorg.conf

My mouse section is now:
--- begin quote ---
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"B16_b_02 USB-PS/2 Optical Mouse"
EndSection
--- end quote ---

sudo /etc/init.d/udev restart

At this point I logged out, and even restarted and logged in again.  Upon logging in (and I have done this multiple times) my mouse (and trackpad) are both nonfunctional.

Any pointers at this point would be appreciated.

Thanks

---

### Post by detyabozhye on 2008-07-04
Up through 7.10 we used evdev's autodetecting for the mouse (this is talked about somewhere in the thread). Unortunately, I hear it's been removed in 8.04, and I don't have a solution for it yet because I haven't upgraded to 8.04 yet (issues with krfb), but some people have talked about it on this thread.

---

### Post by smushi on 2008-07-21
I have a Logitech optical mouse with just one extra thumb button (so 6 buttons total).
The thumb button would always read as button 2, same as wheel down.
I followed your steps to change the driver in xorg.conf to evdev, and now it just works (i.e. I can now use the thumb button to go back in firefox, which was the whole point).
I don't quite understand why I can't seem to get it working with buttonmapping and such, but thanks anyways!

sd

---

### Post by Macdelaney on 2008-08-20
I've spent the last few days trying to get this to work and just can't crack it. The back and foward thumb buttons were working without any configuration actually, the same with the search one.

My xorg.conf file looks like this

```
Section "InputDevice"
	Identifier	"Configured Mouse"
        Driver		"mouse"
        Option          "Phys"  "usb-0000:00:02.0-2/input0"
        Option          "CorePointer"
       Option          "Name"  "Logitech MX Revolution"
       Option          "ZAxisMapping"  "4 5" 
       Option          "Resolution"    "800" 
EndSection
```

I know that instead of "mouse" the Driver line should say "evdev", but if i enter evdev there, the pointer would not work anymore. I don't know what wrong, this should be right since i have the xserver-xorg-input-evdev package installed. Is there something i'm missing???? Any help would be much appreciated.

Edit: I'm guessing my problem is the same as babucher (i read up to half the thread, but the first half :P) since I'm also on 8.04. I'll post back i find a solution.

Edit #2: As was posted a few pages back there's a discussion and some solutions for this at: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/173833](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/173833) 

Here i post a working sample of xorg.conf for my Mx Revolution, just added the Option "Device" part.
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver "evdev"
        Option "CorePointer"
        Option "SendCoreEvents" "true"
        Option "Device"  "/dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse"

       Option          "Name"  "Logitech MX Revolution" # not necessary
       Option          "ZAxisMapping"  "4 5" # not necessary
       Option          "Resolution"    "800" # doesn't make a difference
EndSection
```

---

### Post by bruno321 on 2008-12-25
Thanks to this howto and after reading a bit around these forums and some manual pages, I've managed to get the Logitech LX7 working perfectly.

Since the procedure was a bit custom, I'll post it, perhaps it will be of use to someone. First of all: I use Kubuntu 7.10.

After installing evdev, I had to edit xorg.conf like this:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice "Configured Mouse"
EndSection

 [...]

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Name"  "Logitech USB RECEIVER"
EndSection
```

Then, I installed xbindkeys, xvkbd and xmacro, and edited ~/.xbindkeysrc like this:

```

#little buttons:

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9

#tilt wheel:

"echo ButtonPress 2 ButtonRelease 2 Delay 0 | xmacroplay -d 0 :0.0"
release+b:11

"echo ButtonPress 2 ButtonRelease 2 Delay 0 | xmacroplay -d 0 :0.0"
release+b:12
```

Note that what this does is map the little left and right buttons like it is by default, but it maps the left and right wheel buttons to the middle button. This is because I wanted it to be that way. To find out that the middle button is number 2, I used xev. You could modify ButtonPress 2 ButtonRelease 2 by whatever button number you should like: that xmacroplay line just sends the signal "press and release button 2". Make sure to leave the Delay 0 at the end of the pipe, always, because xmacroplay has a bug which makes it play the last action twice. Using delay 0 is a workaround.

If you want the default config (i.e. the tilt wheel acts as horizontal scroll), I could do it like this:

```
#tilt wheel:

"/usr/bin/xvkbd -xsendevent -text "\[Left]""
b:11
"/usr/bin/xvkbd -xsendevent -text "\[Right]""
b:12
```

It didn't work as flawlessly as it should have: if you held down the wheel right, it scrolled right only a little bit, making it a bit pointless. If anyone knows how to config a smooth scroll, please say so.

In any case, using xbindkeys and proper command lines you can map the tilt wheel buttons and the right-left buttons to whatever you want. Using xvkbd you can make it "press keyboard buttons" and using xmacroplay you can make it "press mouse buttons".

---

### Post by HyperHacker on 2008-12-28
Hey, this guide is a lot of help, but I ran into a couple problems. (Just bought an MX518.)> **detyabozhye said:**
> Download and untar "click" source code into ~/.click (or wherever you want, just remember the dir, you'll need it in the .xbindkeysrc):

```
cd ~/
wget http://bg.rifetech.com/click.tgz
tar xvfz click.tgz
mv click .click

```This link is dead, and the first couple times I read it, I thought it meant to download the source and then run this command, which left me wondering where I'm supposed to download it from.

The + and - buttons (I guess those are the "cruise control" buttons?) just change the cursor speed. Two problems with this: I can't find a comfortable speed (it jumps from too slow to too fast), and I want to map those buttons to keys (maybe ctrl+home/end) like with the back/forward buttons, but they don't generate a response in xev.

Mapping the back/forward buttons to Alt+Left/Right works, but it doesn't give focus to the window like they normally would. Before if I had another window in focus, moved the mouse over Firefox, and hit Back, it would switch to Firefox and go back a page. Now it just sends Alt+Left/Right to the window in focus.

There's also a "window" button (i.e. a button with two rectangles, like the "unmaximize" icon in most window themes' title bars) below the - button, which shows up as button 10 in xev. I wanted to use this in Compiz but it only supports buttons 1 to 9; is there a workaround for that? I tried mapping it to the same as the keyboard shortcut in .xbindkeysrc, but it doesn't work; the keypress gets sent to the window and Compiz ignores it.

Lomoco doesn't recognize the mouse:```
$ sudo lomoco -8
005.002: 046d:08f0 Unsupported Logitech device: Camera
003.002: 046d:c051 Unsupported Logitech device: USB-PS/2 Optical Mouse
```

---

### Post by detyabozhye on 2008-12-28
> **HyperHacker said:**
> Hey, this guide is a lot of help, but I ran into a couple problems. (Just bought an MX518.)This link is dead, and the first couple times I read it, I thought it meant to download the source and then run this command, which left me wondering where I'm supposed to download it from.

What version of Ubuntu are you running? Most of this guide is not needed anymore for versions 8.10 and up while 8.04 and a few other versions require a slightly different setup (talked about somewhere in the thread). As for the 'click' program, you won't need it since you have a MX518 and it has a different way of handling what are known as cruise control buttons on a MX500 and similar mice.

> **HyperHacker said:**
> The + and - buttons (I guess those are the "cruise control" buttons?) just change the cursor speed. Two problems with this: I can't find a comfortable speed (it jumps from too slow to too fast), and I want to map those buttons to keys (maybe ctrl+home/end) like with the back/forward buttons, but they don't generate a response in xev.

They are the cruise control buttons on other mice, on the MX518 they have a different function (changing DPI). That function might be able to be switched on/off, but as you said later in the post, lomoco doesn't seem to support your mouse (which is needed to do the switching). Those buttons adjust the DPI of the mouse, or precision, which is needed for some games, it's not meant to adjust plain speed. To finetune the mouse speed, use the mouse settings in the control panel.

> **HyperHacker said:**
> Mapping the back/forward buttons to Alt+Left/Right works, but it doesn't give focus to the window like they normally would. Before if I had another window in focus, moved the mouse over Firefox, and hit Back, it would switch to Firefox and go back a page. Now it just sends Alt+Left/Right to the window in focus.

Right, since it emulates a keyboard shortcut, and the keyboard always affects the currently focused window. Personally, I just have my back/forward buttons mapped to button 6 and 7 which do back and forward in Opera and Firefox (as an option) and also to horizontal scroll since the MX500 doesn't have a tilt wheel. I also have the 10th button mapped to a keyboard shortcut, but the focused window thing usually doesn't bug me since I have focus following the mouse.

> **HyperHacker said:**
> There's also a "window" button (i.e. a button with two rectangles, like the "unmaximize" icon in most window themes' title bars) below the - button, which shows up as button 10 in xev. I wanted to use this in Compiz but it only supports buttons 1 to 9; is there a workaround for that? I tried mapping it to the same as the keyboard shortcut in .xbindkeysrc, but it doesn't work; the keypress gets sent to the window and Compiz ignores it.

Since the MX518 doesn't have a tilt wheel, it's sdandard mappings should be (in the latest version of Ubuntu):
1:click
2:middle click
3:right click
4:scroll up
5:scroll down
6 - unmapped
7 - unmapped
8:back
9:forward
10:window switcher

What you could do is set up Xmodmap to map it this way (I won't write exactly how to do it yet, since it usually takes a bit of playing around with it to get it right):
1:click
2:middle click
3:right click
4:scroll up
5:scroll down
6:back
7:forward
8:window switcher

> Lomoco doesn't recognize the mouse:```
$ sudo lomoco -8
005.002: 046d:08f0 Unsupported Logitech device: Camera
003.002: 046d:c051 Unsupported Logitech device: USB-PS/2 Optical Mouse
```

Seems that the latest MX518 had a hardware revision not supported by lomoco yet: [https://dev.lomoco.org/ticket/6](https://dev.lomoco.org/ticket/6)

---

### Post by HyperHacker on 2008-12-28
Yeah, changing the DPI does seem to be changing the speed. While it'd be nice to have maybe a keyboard shortcut to do that, I'd rather have the buttons mapped to things I'll use more often, and set the default DPI to something nice.
How would you do that in xmodmap?

(BTW, [https://dev.lomoco.org](https://dev.lomoco.org) has an invalid security certificate.)

---

### Post by detyabozhye on 2008-12-29
> **HyperHacker said:**
> Yeah, changing the DPI does seem to be changing the speed. While it'd be nice to have maybe a keyboard shortcut to do that, I'd rather have the buttons mapped to things I'll use more often, and set the default DPI to something nice.
How would you do that in xmodmap?

Yes, DPI does change the speed, but it's not the main purpose. For regular computing, you won't need more than 400 or 800 DPI and then just adjust the mouse speed in the control panel to your liking.

You can't change the behaivior of those buttons with Xmodmap alone. You have to actually send a signal to the mouse to change the behavior, which requires a program like lomoco. Unfortunately, it seems there's nothing out there that will work (to change the behavior of those buttons) for your mouse at the moment.

---

### Post by Hastrobal on 2009-01-22
Hello,

Is it possible to bind a number from the Numeric keypad on a mouse button ?
I have a MX518 and read your guide (good guide ;)) but unfortunally just the normal 4 is used :(. I'm playing warcraft3 and wanted to bind the numeric "4" as a hotkey on the side button of my mouse. 

I inserted into "xbindkeyssrc"

```
"/usr/bin/xvkbd -xsendevent -text "\[4]""
  m:0x0 + b:8
```

Best regards, 
Hastrobal

---

### Post by GrimRe on 2009-05-05
Hello,

9.04 is my first foray into linux and ubuntu.

I have an MX5000 mouse and MX1000 keyboard that come in the MX5000 combo.

Here is my devices printout

```
II: Bus=0003 Vendor=046d Product=c70e Version=0111
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:1a.7-1.1.3.2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.1/1-1.1.3/1-1.1.3.2/1-1.1.3.2:1.0/input/input6
U: Uniq=0007617C4B04
H: Handlers=kbd event3 
B: EV=120013
B: KEY=1000000000007 ff800000000007ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=046d Product=c70a Version=0111
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:1a.7-1.1.3.3/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.1/1-1.1.3/1-1.1.3.3/1-1.1.3.3:1.0/input/input7
U: Uniq=0007617C4B04
H: Handlers=kbd mouse1 event4 
B: EV=1f
B: KEY=837fff002c3027 bf00444400000000 fff0001 f848a27c000 667bfad941dfed 9e000000000000 0
B: REL=1c3
B: ABS=100000000
B: MSC=10: Bus=0003 Vendor=046d Product=c70e Version=0111
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:1a.7-1.1.3.2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.1/1-1.1.3/1-1.1.3.2/1-1.1.3.2:1.0/input/input6
U: Uniq=0007617C4B04
H: Handlers=kbd event3 
B: EV=120013
B: KEY=1000000000007 ff800000000007ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=046d Product=c70a Version=0111
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:1a.7-1.1.3.3/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.1/1-1.1.3/1-1.1.3.3/1-1.1.3.3:1.0/input/input7
U: Uniq=0007617C4B04
H: Handlers=kbd mouse1 event4 
B: EV=1f
B: KEY=837fff002c3027 bf00444400000000 fff0001 f848a27c000 667bfad941dfed 9e000000000000 0
B: REL=1c3
B: ABS=100000000
B: MSC=10

```

Here is my xorg.conf

```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection

```

However when I add this to the end of the file, my system display completely crashes when I try and log in, its just a screen full of weird colours and lines. CTRL + ALT + BACKSPACE doesn't even bring me back to the command line :(

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"Logitech Logitech BT Mini-Receiver" 
EndSection

```

---

### Post by berdux on 2009-06-02
greetings,
wow this is a huge thread..

i have logitech mediaplay cordless mouse. back/forward worked ok! (with keyboard shortcut alt+left and alt+right)
i would like to know the _keyboard shortcuts_ to setup these buttons on my mouse:

play/pause
next track
previous track
volume up
volume down

on my keyboard (microsoft comfort curve) there are buttons for up/down volume and a play/pause button that work fine, in xev output i do not understand anything, for exemple for volume up (keyboard) shows
when pressed:
```
FocusOut event, serial 45, synthetic NO, window 0x5a00001,
    mode NotifyGrab, detail NotifyAncestor
```
and when releasing:
```
FocusIn event, serial 45, synthetic NO, window 0x5a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 45, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

```

it shows exactly the same when i press/release volume up/down, play/pause, and mute... so i guess i am not looking on the right place :)

left click: button 1
wheel in: button 2
right click: button 3
wheel up: button 4
wheel down: button 5
back: button 8
front: button 9
media: button 10
tilt wheel left: 11
tilt wheel right: 12
volume up: button 13
volume down: button 14
next track: button 15
previous track: button 16
play/pause: button 17


also there is a "media" button and i would like it to start an application (i.e. amarok), how would i do that?

thanks in advance

---

### Post by hannahu on 2009-07-15
Hi geeks,

have just bought a dell minilaptop with ubuntu installed together with a logitech mouse, only to find that they don't provide driver software for Linux. In your instructions I seem to be missing steps 1-100 or something. I have so far only used Microsoft, so need non-geek instructions or a geek dictionary.:confused:

many thanks,
hannahu

---

### Post by Meuro on 2009-07-21
In section 2 you have to download and untar "click" source code.  I do the command as given and I get the following:

> ~$ wget [http://bg.rifetech.com/click.tgz](http://bg.rifetech.com/click.tgz)
--2009-07-21 23:29:08--  [http://bg.rifetech.com/click.tgz](http://bg.rifetech.com/click.tgz)
Resolving bg.rifetech.com... 204.13.248.125
Connecting to bg.rifetech.com|204.13.248.125|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://atrus.rifetech.com/bg/click.tgz](http://atrus.rifetech.com/bg/click.tgz) [following]
--2009-07-21 23:29:09--  [http://atrus.rifetech.com/bg/click.tgz](http://atrus.rifetech.com/bg/click.tgz)
Resolving atrus.rifetech.com... 208.97.165.192
Connecting to atrus.rifetech.com|208.97.165.192|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-07-21 23:29:09 ERROR 404: Not Found.


Is there somewhere else I can get it from?

Cheers, M

---

### Post by Meuro on 2009-07-21
Nevermind.  Google gave me the answer eventually.  I got click.tgz from [http://www.ussg.iu.edu/hypermail/linux/kernel/0504.0/1371/click.tgz](http://www.ussg.iu.edu/hypermail/linux/kernel/0504.0/1371/click.tgz)

---

### Post by M2-player on 2009-12-30
Hi! I have Microsoft Mobile Mouse 4000.
How I have to configure Super button?

```
"/usr/bin/xvkbd -xsendevent -text "\[Super_L]""
  m:0x0 + b:8
```I have default configured "Enhanced Zoom Desktop" (on Compis Fusion) as button Super + scrolling on mouse (Zoom in = <Super>Button4; Zoom out = <Super>Button5).

But I cann't zoom in/out only on mouse. The button does not work as Super.

I want to mapp my side button on mouse as Super button.
(sorry for bad english)

---

### Post by ilor on 2010-03-26
thanx works gr8 for M505

---

### Post by crazydude202 on 2010-09-12
Does this work with ubuntu 10.04?

---

### Post by 0xd5 on 2010-11-03
Sorry to revive an old thread, but I have a very similar problem to M2-player, and I was hoping someone might be able to help.  I, like M2-player, would like to map b:8 to Super_L, so that I can use the thumb button on my G7 (thumb button on G7 mouse is button b:8) along with the scroll wheel in Compiz.  I tested xvkbd by mapping b:8 to the command:

```
/usr/bin/xvkbd -xsendevent -text "\[a]"
```

which worked as expected: whenever I pressed the thumb button (b:8), the letter &#8216;a&#8217; was printed on the screen.  However, whenever I tried any of the following, I could not get it to work as expected, and I have yet to get the Super button to work:

```
/usr/bin/xvkbd -xsendevent -text "\[Super]"
```
```
/usr/bin/xvkbd -xsendevent -text "\[Super_L]"
```
```
/usr/bin/xvkbd -xsendevent -text "\[Super_L]\"
```
```
/usr/bin/xvkbd -xsendevent -text "\[Super_L]\[]"
```

For clarification, I want to use b:8 as a modifier button that I can use in conjunction with other mouse or keyboard buttons (though Compiz), preferably the left Super button.

Thanks for any help you might have!!

~David  [=

----------------------------------------------------------------------------------------------------------------

> **crazydude202 said:**
> Does this work with ubuntu 10.04?
Yes, I have used it in 10.04 with no trouble at all.

~David  [=

---

### Post by 0xd5 on 2010-11-03
Err, delete this post.  Sorry!!

---

