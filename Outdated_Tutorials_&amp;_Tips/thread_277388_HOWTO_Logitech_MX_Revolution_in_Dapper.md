---
title: "HOWTO: Logitech MX Revolution in Dapper"
date: 2006-10-14
forum: Outdated Tutorials &amp; Tips
---

### Post by daou on 2006-10-14
[SIZE=2]
[U][B][COLOR=DarkRed] UPDATE - May 26, 2007 : A new method

[/COLOR][/B][/U][COLOR=DarkRed][COLOR=Black]MX and VX users can now use btnx to easily get additional functionality from their buttons. The thread for btnx is here: [/COLOR][/COLOR][/SIZE][http://ubuntuforums.org/showthread.php?p=2727025](http://ubuntuforums.org/showthread.php?p=2727025)
[SIZE=2][COLOR=DarkRed][COLOR=Black]All discussion relating to btnx has been moved there.


[/COLOR][/COLOR][/SIZE][SIZE=2] [U][B]
OLD GUIDE:: stop here if you used the method above[/B][/U]
--------------------------------------------------------------------------------------

This is a guide to get your Logitech **MX Revolution** to work under Dapper (or Edgy). I have heard that it works for **VX Revolution** just as well, with the button numbers mapped differently. This guide is based on detyabozhye's "[HOWTO: Configuring Logitech mice in Ubuntu 6.06: New Guide]("http://ubuntuforums.org/showthread.php?t=219894")" and Andy's "[Logitech MX Revolution in Linux]("http://andy.hillhome.org/blog/2006/09/27/logitech-mx-revolution-in-linux/")". For configuring Logitech mice, other than the MX/VX Revolution, have a look at detyabozhye's great howto.

**_Color guide: _**
[COLOR=DarkRed]Red: You should really read these.[/COLOR]
[COLOR=Blue]Blue: Optional, but recommended reading.[/COLOR]

**NOTE:** [COLOR=Blue]*This guide is actually heavily :rolleyes:  based on detyabozhye's guide (link above). This guide adds to his, describing how to get MX/VX Revolution to work. I decided to make a new guide because of the number of tweaks required.*[/COLOR]

1. Make sure the USB receiver is plugged in and that you have evdev installed:

```
$ sudo apt-get install xserver-xorg-input-evdev
```2. [COLOR=Blue]The first part of detyabozhye's guide binds the mouse to an event. It works, but after a reboot the event can change and xserver might fail to start. For me it happened every time and I always had to check and edit in the new event. The other method that the guide explains is making a udev. This is what we will do, but his method for making a udev rule will not work for an MX/VX Revolution.[/COLOR]

Now let's find some info about your input devices. Type:

```
$ cat /proc/bus/input/devices 
```A whole bunch of text should have been dumped on your terminal. Here is mine:

```
[B]I: Bus=0003 Vendor=046d Product=c51a Version=4101
N: Name="Logitech USB Receiver"[/B]
**P: Phys=usb-0000:00:02.0-3/input0    <----- Mouse USB location**
S: Sysfs=/class/input/input0
**H: Handlers=mouse0 event0 ts0**
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0003 Vendor=046d Product=c51a Version=4101
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-3/input1         <---- Mouse search button, works already so we don't need it
S: Sysfs=/class/input/input1
H: Handlers=kbd event1
B: EV=f
B: KEY=c0002 400 0 0 1 f80 78000 6039fa d84157ad 8e0000 0 0 0
B: REL=40
B: ABS=1 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0006 Version=0042
N: Name="ImExPS/2 Logitech MX Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse1 event3 ts1
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0003 Vendor=046d Product=c512 Version=3007
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-2/input0
S: Sysfs=/class/input/input4
H: Handlers=kbd event4
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c512 Version=3007
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-2/input1
S: Sysfs=/class/input/input5
H: Handlers=kbd mouse2 event5 ts2
B: EV=7
B: KEY=7fffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff 0 0 1878 d800d100 1e0000 0 0 0
B: REL=143

```The output contains your keyboard, mice, etc. I highlighted the important part. If you are like me, you have more than one Logitech mouse and need to know which one of these sections point to the MX/VX Revolution. You need to find the section where the product and version ID is:

[/SIZE][SIZE=2]--------------------[/SIZE][SIZE=2]IDs for MX Revolution--------------------
[B]Vendor=046d Product=c51a Version=4101
Name="Logitech USB Receiver"

[/B][/SIZE][SIZE=2]--------------------[/SIZE][SIZE=2]IDs for VX Revolution--------------------
[B]Vendor=046d Product=c518 Version=4204
Name="Logitech USB Receiver"[/B][/SIZE]
[SIZE=2] 
There are two of these, both are for the MX/VX Revolution, but you need to use the the section where the output looks like:

[/SIZE]**[SIZE=2]Phys=usb-XXXX:XX:XX.X-X/input0[/SIZE]**
[SIZE=2] **Handlers=mouseX eventX**

The X is a number. For example, in my output it was "[/SIZE][SIZE=2]Phys=usb-0000:00:02.0-3/input0" and [/SIZE][SIZE=2]"Handlers=mouse0 event0". This refers to the mouse. [/SIZE][SIZE=2]The most important part of information in the section is the physical location because this is what we bind the udev rule to:

**P: Phys=usb-0000:00:02.0-3/input0**

Your physical USB location will be different. [COLOR=DarkRed]Make sure you copy the info after the "Phys=" word from YOUR ;) output.[/COLOR]
[COLOR=DarkRed]
[COLOR=Blue]Note: [/COLOR][/COLOR][/SIZE][SIZE=2][COLOR=Blue]The other section with the same IDs, but with "input1" for the physical location (Phys) and [/COLOR][/SIZE][SIZE=2][COLOR=Blue]"Handlers=kbd eventX" also refers to the mouse, but it interprets events from that input as keyboard events.[/COLOR][/SIZE][SIZE=2][COLOR=Blue] Apparently this is for the search button, but we don't have to take it into consideration. [/COLOR][/SIZE][SIZE=2]



3. With the physical location you can now make a udev rule. Make sure you have udev installed. Type:

```
$ sudo apt-get install udev
```Now make the udev rule. Type:

```
sudo gedit /etc/udev/rules.d/19-local.rules
```Now add the following line into the new text file, but edit the bolded part:

```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", SYSFS{../phys}=="**usb-0000:00:02.0-4/input0**", NAME="input/event9"

```[COLOR=DarkRed]Replace the bold text with whatever you got for the USB location in step 2.[/COLOR]

[COLOR=Blue]
Note: why bind the rule to a physical location? After all, this means that whenever you remove the USB RF-receiver and plug it back in into a different port, the physical location will change. This means the xserver will not boot.
One reason: it's the only way udev can know which device you want to bind to an event (event9 in this case). If we were to bind it to a name like "Logitech USB Receiver", udev would see at least two devices with that name, or in my case 4! It would not know which one to choose. The rule cannot be made with the SysFs input number because these change. The rule cannot be made using the vendor id, product id, and version number, because MX/VX Revolution has two of these. One is recognized as a mouse and the other as a keyboard (for the mouse search button). The only way to make the udev work is by binding it to a physical location. Remember to always plug it in into the same port.
If someone finds a fix for this, please let me know.
[/COLOR] 

4. Now, with the udev rule, you can start editing your xorg.conf file. [COLOR=DarkRed]If you aren't familiar with your xorg.conf file (meaning you don't know it by heart), make sure you make a backup of it:[/COLOR]

```
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```Now open it for editing:

```
$ sudo gedit /etc/X11/xorg.conf
```Add the following section into the xorg.conf:

```
Section "InputDevice"
    Identifier        "MX Rev"     #VX Rev users can type "VX Rev"
    Driver            "evdev"
    Option            "Device" "/dev/input/event9"
    Option            "Protocol" "auto"
    Option            "CorePointer"
EndSection
```Now find the **"Section "ServerLayout""** in the xorg.conf file. Add the following line inside the section:

```
InputDevice "MX Rev"
```or if you are a VX Rev user and typed "VX Rev" into the identifier,
[/SIZE][SIZE=2] ```
InputDevice "VX Rev"
```[/SIZE][SIZE=2]You might also want to comment your old mouse from the server layout (Input Device "Configured Mouse"), also also the Section "InputDevice" with the same name ("Configured Mouse"). Commenting a line is done with a '#' character.
For example, after editing my ServerLayout, this is what it looked like:

[COLOR=DarkRed]*Don't copy this straight into your xorg.conf*[/COLOR]
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Samsung Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice       "MX Rev"
    #InputDevice    "Configured Mouse"
EndSection
```There, your xorg.conf file is ready. You backed up the previous one? Yes? Good. You can restart your computer now, but if you run into trouble (something went wrong in the xorg.conf file or udev rule, and you can't load xserver), then follow the guide below.

**-------------------- BEGIN if xserver wont start-------------------------**

Remove the udev rule and restore your xorg.conf:

```
$ sudo rm /etc/udev/rules.d/19-local.rules
$ sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```Or, if you think you just made a silly typo, you can use nano to edit it from command line:

```
$ sudo nano /etc/X11/xorg.conf
```or
```
$ sudo nano /etc/udev/rules.d/19-local.rules
```Then to start udev and xserver again, type

```
$ sudo /etc/init.d/udev restart
$ sudo /etc/init.d/gdm restart
```**-------------------- END if xserver wont start-------------------------**


5. Congrats, now you should have functionality for **all** the buttons. You can test this by using xev. Install it if you don't have it.

```
$ sudo apt-get install xev
```Then run it by typing xev. A window should open. Test all you mouse buttons on the screen. Your terminal should output something everytime you press a button. For example, if I pull the thumb-wheel towards myself, I get:

```
ButtonRelease event, serial 31, synthetic NO, window 0x3800001,
    root 0x52, subw 0x0, time 1207998740, (66,85), root:(1000,153),
    state 0x10, **button 17**, same_screen YES

```This means the button is mapped as mouse button 17.

[B]
-----------------------[/B][/SIZE][SIZE=2]** MX Revolution buttons**[/SIZE][SIZE=2]**---------------------------**

Here are all the button numbers, at least the ones I got:

_Top-buttons_
1: Left button
3: Right button
keycode 122: Search button

_Thumb-buttons_
8: "the button nearest to you"
9: "the button away from you

_Top-wheel_
4: Scroll-up
5: Scroll-down
6: Tilt-right
7: Tilt-left

_Thumb-wheel_
15: Pull
13: Push
17: Press
[/SIZE][SIZE=2]**-----------------------**[/SIZE][SIZE=2]** VX Revolution buttons**[/SIZE][SIZE=2][B]---------------------------

[/B][/SIZE][SIZE=2]_Top-buttons_
1: Left button
3: Right button

_Wheel_
2: Press
4: Scroll-up
5: Scroll-down
6: Tilt-right
7: Tilt-left

_Other buttons_
8: Big thumb button 
9: Small thumb button
13: Zoom slider +
14: Zoom slider -
Keycode 122: Search button
[/SIZE]     [SIZE=2]------------------------------------------------------------------------

Go ahead and map them as you like. It's great with Compiz (or Beryl). I mapped the thumbwheel to rotate the cube and the thumb buttons to rotate apps from one workspace to the other etc.
If you aren't using anything like Beryl and want to bind the buttons to keyboard shortcuts like "Alt+Tab", go look at [detyabozhye's guide]("http://ubuntuforums.org/showthread.php?t=219894"). Have a look at section 2 (part 1 and 3) where he shows you how to install and configure xvkbd and xbindkeys. This should help. I haven't tried it myself, so please let me know how it works out.

[/SIZE][SIZE=2][COLOR=Blue]detyabozhye's guide also shows how to install configure lomoco. It's a utility to get increased resolution for the laser, the full 800dpi for an MX Revolution. However, as of writing this lomoco does not have support for the MX Revolution. I don't about VX's status, but I highly doubt there is support for it either.[/COLOR][/SIZE]
[SIZE=2]  
[COLOR=DarkRed] Just remember that you might have to edit your udev rule if you plug in your RF receiver to a different USB port.[/COLOR] In that case, you have to use the cat command like in step 2 to find the device location and edit the udev rule, replacing the old location with the new one and restarting udev+xserver. 
Hope this helped.[/SIZE]


[SIZE=2]------------------------------------------------------------------------
**Optional tips and tricks:**[/SIZE]

**Search button-> mouse wheel click**
There is no mouse wheel click on the MX Revolution. One option is to bind it to the search button (below the top mouse wheel). There are several ways to do this, but using xkbset turns out to be the best approach. Thanks to **NobodySpecial** for bringing up xkbset and **knn** for polishing up the method.

1. Install xkbset:
```

sudo apt-get install xkbset
```2. Open the mousekeys config file for editing:
```

sudo gedit /usr/X11R6/lib/X11/xkb/compat/mousekeys
```3. Remove all text after the line "// Keypad actions" and before "// New Keysym Actions", and save the file. If you are unsure about what to remove, use [this example from knn]("http://www.ubuntuforums.org/attachment.php?attachmentid=22816&d=1168622608") as a reference.

4. Use the following command to map the search button to mouse button 2:
```
echo "keycode 122 = Pointer_Button2" >> ~/.Xmodmap
```5. Tell gconf to load the .Xmodmap at startup by giving these two commands:
```
gconftool-2 --list-type string --type list --set /desktop/gnome/peripherals/keyboard/general/known_file_list "[.Xmodmap]"
gconftool-2 --list-type string --type list --set /desktop/gnome/peripherals/keyboard/general/update_handlers "[.Xmodmap]"
```7. Finally, add "xkbset m" to your sessions so it begins on startup (System -> Preferences -> Sessions->Startup Programs).

8. Now restart X (CTRL+ALT+BACKSPACE) and try clicking a link in Firefox with the search button. If the link opens up in a new tab, it worked.



**Switch mouse wheel tilt functions**
By default, tilting the mouse wheel left in Firefox goes forwards and tilting it right goes backwards in your page history. This is counter-intuitive. You can switch the directions of the tilts by adding a line to you ~/.Xmodmap file:

```
gedit ~/.Xmodmap
```Add this line to the file:
```
pointer = 1 2 3 4 5 7 6 8 9 10 11 12 13 14 15 16 17 18 19 20
```Now restart X (CTRL+ALT+BACKSPACE).



**Mouse wheel tilt for horizontal scrolling**
This tip is used to switch the mouse wheel tilt function to horizontal scroll in Firefox. Thanks to **knn** for suggesting this tip.

1. Go to about:config by typing "about:config" in the URL field of Firefox.

2. Set mousewheel.horizscroll.withnokey.action "Value" field to 0. **NOTE**: If you've swapped the wheel tilt buttons as described in the "Switch mouse wheel tilt functions" tip above, the direction will be reversed. In this case, change mousewheel.horizscroll.withnokey.numlines "Value" to 1.


[COLOR=Blue]EDIT1: Fixed mouse tilts. Thanks **selari**.
EDIT2: Added the udev rule step.
EDIT3: Added note about VX and its button numbers. Thanks **Micha&#322;**.
EDIT4: Howto changed to include VX.
EDIT5: Added note about lomoco.
EDIT6: Works in Edgy.
EDIT7: Added search button-> mouse-wheel click bind. Thanks **MonkeyWrench32**
EDIT8: Added mouse wheel tilt switch.
EDIT9: Changed the search button-> mouse-wheel click bind method. Thanks **NobodySpecial** and **knn**.
EDIT10: Added "Mouse wheel tilt for horizontal scrolling" tip. Thanks **knn**.
EDIT11: A completely new way to do the howto with btnx.
[/COLOR]

---

### Post by selari on 2006-10-18
The buttons for the top wheel on my mouse are different than yours.  Clicking the wheel isn't a button, but just changes the locking mechanism inside the mouse.  Tilting the wheel to the left is 7 and to the right is 6.

---

### Post by daou on 2006-10-20
>  	The buttons for the top wheel on my mouse are different than yours. Clicking the wheel isn't a button, but just changes the locking mechanism inside the mouse. Tilting the wheel to the left is 7 and to the right is 6.

I forgot the tilt-buttons, I'll add them. And yes, you are right about the clicking. I mistook the click output on xev as button 7, when in fact I had tilted the wheel while pressing it. I'll fix this too.

A lot of other corrections are needed, this is the first time I've been able to edit the howto since I posted it. Figured out a bit afterwards (including the mistaken click-tilt thing).

---

### Post by daou on 2006-10-21
selari,

What did you do for the xorg.conf device section for the MX Revolution? Did you simply use a changing event number or did you make a udev? The udev method described as of now in the howto binds the MX Revolution USB receiver to a physical location, which means it can't be unplugged.

Or have you figured out something better?

---

### Post by webfootedchicken on 2006-10-23
Hey Daou,

Thanks for the guide - very much appreciated.

Xev reports all the same button config's as yours.

As I'm a Ubun00b - could you please advise how and what you have mapped your mouse buttons to?:oops: 

I can't for the life of me get the buttons to do anything. Ideally what I'd like to achieve:

Top-buttons
1: Left button = Single left click
3: Right button = Single right click
keycode 122: Search button = Open Firefox

Thumb-buttons
8: "the button nearest to you" = Double click
9: "the button away from you = Close app/Alt+F4

Top-wheel
4: Scroll-up = As is
5: Scroll-down = As is
6: Tilt-right = Scroll left
7: Tilt-left = Scroll right

Thumb-wheel
15: Pull = Minimize app
13: Push = Ctrl + Tab (Which will change active tab in Firefox)
17: Press = Open Nautilus home folder

Or am I completely dreaming, when I hope for this type of functionality? Are any of these do-able?:confused: 

BTW I'm not using XGL/Compiz.

Cheers again,

Web Footed Chicken

---

### Post by daou on 2006-10-23
webfootedchicken,

I'm glad the howto helped.
[URL="http://ubuntuforums.org/showthread.php?t=219894"]
detyabozhye's guide[/URL] shows how to assign functionality to the buttons once they are recognized. Have a look at section 2 (part 1 and 3, I don't believe the cruise control is meant for MX Revo.) where he shows you how to install and configure xvkbd and xbindkeys. This should help.

Beryl (Compiz) provides an easy way to map buttons to functions so I haven't tried this myself. I ran out of buttons after mapping mine to useful Beryl functions :rolleyes: so I haven't tried the xvkbd and xbindkeys yet.

But I would image it will work for the MX Revo as well. Just fill in your correct mouse button number in the "b:#" parts and change the keyboard shortcut it calls (in his example, ALT+RIGHT).

A quick fix for the search button->firefox: go to System->Preferences->Keyboard Shortcuts. In the dialog, click on the text next to "Launch web browser" and then click the search button. It should map the function to a button "0x7a" which is hexadecimal for 122. That was the keycode your search button had. Worked for me.

Let me know what happens. If the method works, I'll add it to the howto. If it doesn't, I'll see if I can make it work.

---

### Post by mdwuznik on 2006-10-23
Thanks for the guide.
If any of you is wishing to get a "smaller" Revolution VX - the same guide applies to you, with the only difference being the key numbering. 
So, for the VX:
button placement
1 left
2 wheel press
3 right 
4 wheel up
5 wheel down
6 wheel right
7 wheel left
8 big thumb button 
9 small thumb button
13 zoom slider +
14 zoom slider -

Binding to various beryl functionalities is a bliss.
Michal, playing with the new mouse...

---

### Post by daou on 2006-10-23
> Thanks for the guide.

You're most welcome.

> If any of you is wishing to get a "smaller" Revolution VX - the same guide applies to you, with the only difference being the key numbering. 

I'll add a note about this in the howto and add the button numbers for the VX . But first, could you tell what Vendor, Product, and Version ID you get for VX Revolution with the "cat /proc/bus/input/devices" command? Also the name, if it is something other than "Logitech USB Receiver".

Actually, if you would give me the whole output for VX, would be much appreciated.

---

### Post by mdwuznik on 2006-10-24
Sure, I'll post when I get back home. 
As for the numbers:
Vendor stays 046d, the rest I'll check. 
Logitech USB receiver stays the same, too.


Small update for the layout:
search button on VX is of course keycode 122.

As for my laptop - the udev rule is perfectly valid and working even if I turn off my mouse and/or remove the receiver, as long as I plug it back into the same USB socket (I may have misunderstood that it won't be that good when unplugging :)). No worries when booting, no issues with the touchpad, too (which is redundant information, but may be encouraging for the frightened - even if you screw up your Rev config, the touchpad may save you). 


I would underline that it's blahblah/input0 which is the real mouse.
blahblah/input1 is this (a bit weird) one-button keyboard being the search button.

On a VX switching between ratcheted and freewheel wheel is only manual (using a small lever underneath). No auto mode foreseen, but clicking the wheel is back normal :)


Cheers
Michal (sorry, my screen name here is just my usual login name, no fancy nickname)

---

### Post by mdwuznik on 2006-10-24
logitech revolution VX portion of /proc/bus/input/devices:


I: **Bus=0003 Vendor=046d Product=c518 Version=4204**
N: Name="Logitech USB Receiver"
P: Phys=**usb-0000:00:1d.1-1/input0**
S: Sysfs=/class/input/input7
H: **Handlers=mouse2 event4 ts2**<-This is the mouse
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0003 Vendor=046d Product=c518 Version=4204
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.1-1/input1
S: Sysfs=/class/input/input8
H: Handlers=kbd event5 <-and this is the search button
B: EV=f
B: KEY=c0002 400 0 0 1 f80 78000 6039fa d84157ad 8e0000 0 0 0
B: REL=40
B: ABS=1 0

---

### Post by daou on 2006-10-24
Michal (not 'ae', is it?),

Thanks for the VX info. I added all the necessary bits into the howto. It's an MX/VX Revolution howto now. Plus I clarified a few bits you pointed out, at least I think I did ;).

About the receiver being plugged in and out into the same port: apparently it's not a problem. However, when I was testing the MX in Windows XP and switched to receiver port to different one, and then back to the original one, the physical location had changed. Apparently if it gets recognized in a different port, it rearranges the physical locations somehow. Anyway, better safe than sorry and always keep it in the same port :D.

If you see anything else that needs cleaning, don't hesitate to point it out.

---

### Post by Nojatron on 2006-10-24
Is there anyway to swap the right and left wheel tilt? It's a bit annoying in firefox having it the other way around.

I know I could use xvkbd and xbindkeys but I remember there a few options in xorg.conf that could do the trick.

---

### Post by dsptech on 2006-10-25
Nice work with the how-to.
I was having issues with my xserver crashing on every other boot.
Your edit resolved that problem.
Would be nice if we could figure out how to increase the resolution now.

---

### Post by daou on 2006-10-25
> Is there anyway to swap the right and left wheel tilt? It's a bit annoying in firefox having it the other way around.

I know I could use xvkbd and xbindkeys but I remember there a few options in xorg.conf that could do the trick.

No other way that I'm aware of. The tweaks made to the input device section in xorg.conf probably won't allow whatever trick it was that you saw. I'll try looking into this.

> Nice work with the how-to.
I was having issues with my xserver crashing on every other boot.
Your edit resolved that problem.
Would be nice if we could figure out how to increase the resolution now.

Good to hear the howto helped. I've been trying to look into the lomoco utility that detyabozhye's guide mentioned (for added resolution). When I installed lomoco it simply recognized my Revo as an unsupported device (it did recognize my older optical one though). We might just have to wait for the developers to add support. We should probably inform them about the lack of support.

---

### Post by mdwuznik on 2006-10-28
Lomoco author ("They") asks to mail him the /proc/bus/input/devices and lsusb -v output, so we only need to mail him lsusb -v :)

For me it seems that Rev VX "boots" as an 800 dpi device, as it's so much faster and responsive comparing to the old 300 dpi mouse - as far as I know there's no resolution switching like G5 in the win drivers, so the Revolutions may just be one resolution - 800 dpi (IMHO, of course).

Cheers
Micha&#322;

---

### Post by daou on 2006-10-28
Micha&#322;,

Could you take care of sending the lsusb and /proc/.../devices to the developers of lomoco (for both the MX and VX Revolution) because you apparently got hold of them already?

I've attached the following:

mxrevo_devices : contains MX Revolution section of cat /proc/bus/input/devices 
mxrevo_lsusb: contains MX Revolution section of lsusb -v

---

### Post by mdwuznik on 2006-10-28
> **daou said:**
> Micha&#322;,


(for the sake of US-ASCII only guys let's stay with Michal, that doesn't hurt that much :) ). 

> **daou said:**
> 
Could you take care of sending the lsusb and /proc/.../devices to the developers of lomoco (for both the MX and VX Revolution) because you apparently got hold of them already?



Sure, if only I get a working email adress. The one I found is not promising, but I'll try anyway.


Michal

---

### Post by daou on 2006-10-30
> for the sake of US-ASCII only guys let's stay with Michal, that doesn't hurt that much
 :D
Michal,
I'll try subscribing to the lomoco dev. mailing list as well. Tell me if you run into to trouble sending the info. I'll take care of it then. I just want to avoid double posting the same issue there.

---

### Post by Lost Creation on 2006-11-17
Thanks for the very helpful HowTo. Have everything working as I'd like except this: **I want the "search" button on the mouse to work as a middle-mouse button.**

At a guess, I remaped keycode "122" as "Pointer_Button2" using Xmodmap. It looks like it took ("xmodmap -pk" prints "keycode 122 = Pointer_Button2") but it doesn't actually work as a middle mouse click.

Since all the existing guides work on the "map mouse click to keyboard shortcut" direction, I'm at a loss for going the other way.

Any ideas?

---

### Post by NobodySpecial on 2006-11-18
Lost Creation -

You need xkbset to make it work:
```
sudo apt-get install xkbset
```

Then assign it:
```
xmodmap -e "keycode 122 = Pointer_Button2"
xkbset m
```

Enjoy!  :-D 

Thanks to [hajk]("http://ubuntuforums.org/showpost.php?p=1357540&postcount=2")

---

### Post by TomPreuss on 2006-11-18
> **NobodySpecial said:**
> Lost Creation -

You need xkbset to make it work:
```
sudo apt-get install xkbset
```

Then assign it:
```
xmodmap -e "keycode 116 = Pointer_Button2"
xkbset m
```

Enjoy!  :-D 

Thanks to [hajk]("http://ubuntuforums.org/showpost.php?p=1357540&postcount=2")
It'll be keycode 122 (not 116) in the MX Revolution's case though.

---

### Post by Lost Creation on 2006-11-18
It works but it also disables my keyboard number pad, and it stops working when I restart. I need the number pad as much as I need the middle mouse button, any way to eat my cake and have it too?

---

### Post by jrickard on 2006-11-30
I have gone over this a dozen times.  It just doesn't work for me.  I have Ubuntu Edgy 686 installed on an HP media center desktop.  I just bought the Logitech MX Revolution keyboard and mouse.

The keyboard worked out of the box.  I couldn't believe it.  I didn't even reboot the machine.  Plugged the bluetooth adapter into the front of the machine, turned on the switch on the keyboard, and unplugged the old keyboard.  It works great.  There's a little slider on the side of the keyboard to allow you to change speaker volume.  Even that works.

Now the mouse.  I've done the events, changed the xorg.conf a half dozen times.  The mouse very much shows up in my /proc/devices/input  but whenever I enable it in xorg.conf, the system hangs on boot.  

To get back, I boot to a command line using the recover boot, copy the backup 
xorg.conf, and I'm back in business. 
:confused: 

Some data from lsusb
```

Bus 003 Device 004: ID 046d:c714 Logitech, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc714 
  bcdDevice           49.00
  iManufacturer           1 Logitech
  iProduct                2 Logitech BT Mini-Receiver
  iSerial                 3 00076170D513
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 RR49.00_B0057
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     301
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               2
Device Status:     0x0000
  (Bus Powered)

Bus 003 Device 002: ID 046d:0b04 Logitech, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0x0b04 
  bcdDevice           49.00
  iManufacturer           1 Logitech
  iProduct                2 Logitech BT Mini-Receiver
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             255

```

and from cat /proc/dev/input

```

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=03f0 Product=040c Version=0100
N: Name="HP EverestFBB"
P: Phys=usb-0000:00:1d.3-1/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=12000f
B: KEY=42c43b2 20d0400 0 0 1 c04 7c000 2639fa d8415faf 8e0040 0 0 0
B: REL=40
B: ABS=1 0
B: LED=1f00

I: Bus=0003 Vendor=046d Product=c713 Version=4900
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:1d.2-1.2/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c714 Version=4900
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:1d.2-1.3/input0
S: Sysfs=/class/input/input3
H: Handlers=kbd mouse0 event3 ts0 
B: EV=f
B: KEY=c0002 400 0 f ffff0001 f80 78000 6639fa d841d7ad 9e0000 0 0 0
B: REL=7cf
B: ABS=1 0

I: Bus=0011 Vendor=0002 Product=0005 Version=0000
N: Name="ImPS/2 Generic Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input4
H: Handlers=mouse1 event4 ts1 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103


```

---

### Post by jrickard on 2006-11-30
Err...belay my last.

I just tried something pretty high tech on this mouse thingy.  I plugged in the bluetooth adapter into a USB port and things are working much better.

The keyboard and mouse came quite separately packaged.  They each had a bluetooth adapter.  I just "*** U ME d" that I could just use one bluetooth adapter for the two of them.

Apparently not.  I plugged in the one for the mouse that I've been fooling with for six hours trying to get to work.  Voila.  It now does.  This with no changes to xorg, or really anything else.  

This 6.10 release is really quite good.

Jack Rickard

---

### Post by TomPreuss on 2006-12-04
> **Lost Creation said:**
> It works but it also disables my keyboard number pad, and it stops working when I restart. I need the number pad as much as I need the middle mouse button, any way to eat my cake and have it too?

I can duplicate this behavior as well.  My numpad stopped working too.

Does anyone have any other ideas?

---

### Post by MonkeyWrench32 on 2006-12-05
I just bought an MX Revolution today.  I have mapped the "Search" button for middle click and my numpad isn't working either.  Oy vey.

Edit:  What it does is turn the numpad into a mouse control.

---

### Post by daou on 2006-12-05
Sorry I haven't been around lately. Project after project.

About the search->middle mouse with xkbset. A quick search reveals what MonkeyWrench said already. It's an accessibility program that allows you to control the mouse with the keypad.

*from [http://packages.debian.org/unstable/x11/xkbset](http://packages.debian.org/unstable/x11/xkbset)*
>  1. MouseKeys
    MouseKeys is a system whereby the numeric keypad can be used to control
    the mouse pointer.

But there should be a button combo to turn mousekeys off.

*from [http://www.math.missouri.edu/~stephen/software/](http://www.math.missouri.edu/~stephen/software/)*
> Mouse Keys: The numerical key pad may be used as well as the mouse to move the cursor. To switch this on/off, press in this order (holding them down until you are done with the third key): Left SHIFT key, left ALT key, NUM-LOCK key. (Actually Mouse Keys is buggy with respect to acceleration: see bugfix-for-mousekeys.)

Try and see if this works. I'm currently not using xkbset.

EDIT: post a reply if it works. If it does, I'll add a note about it to the howto.

---

### Post by MonkeyWrench32 on 2006-12-05
> **daou said:**
> Sorry I haven't been around lately. Project after project.

About the search->middle mouse with xkbset. A quick search reveals what MonkeyWrench said already. It's an accessibility program that allows you to control the mouse with the keypad.

*from [http://packages.debian.org/unstable/x11/xkbset](http://packages.debian.org/unstable/x11/xkbset)*


But there should be a button combo to turn mousekeys off.

*from [http://www.math.missouri.edu/~stephen/software/](http://www.math.missouri.edu/~stephen/software/)*


Try and see if this works. I'm currently not using xkbset.

EDIT: post a reply if it works. If it does, I'll add a note about it to the howto.
I tried that keystroke combination three times and it did not disable it.  :(

EDIT: The command "xkbset m" turns on mousekeys.  If you turn off mousekeys by issuing a "xkbset -m", the search button no longer works.

For now, I have remapped the thumb-wheel press (17) to perform the middle mouse button click.  If anyone else is interested, copy and paste this into a terminal (or the run dialog):

```
xmodmap -e "pointer = 1 17 3 4 5 6 7 8 9 10 11 12 13 14 15 16 2 18 19 20"
```

---

### Post by daou on 2006-12-05
I did some digging around and I was able to get middle-mouse click functionality for the search button with a program called xke. It intercepts kernel events, allowing you to reroute them.

However, there is some sort of instability issue with it. Whenever I try to use the middle-click, gnome becomes somewhat unresponsive. For example, changing window focus sometimes stops working. Doesn't surprise me too much, I don't think the program was designed to be used like this.

If anyone wants to try their luck with it, ask me and I'll post as much as I remember about the installation and setup process.

---

### Post by daou on 2006-12-06
I can confirm the guide applies to Edgy as well.

---

### Post by bodhi.zazen on 2006-12-06
Nice How-to

This thread has been added to the UDSF wiki.

[Logitech_MX_Revolution](http://doc.gwos.org/index.php/Logitech_MX_Revolution)

---

### Post by daou on 2006-12-07
> **Nojatron said:**
> Is there anyway to swap the right and left wheel tilt? It's a bit annoying in firefox having it the other way around.


This was posted a while back. The solution comes from a tweak to the xmodmap that MonkeyWrench pointed out.
To switch the functionality of the top-wheel right and left tilt run the following command in your terminal:

```
xmodmap -e "pointer = 1 2 3 4 5 7 6 8 9 10 11 12 13 14 15 16 17 18 19 20"
```

Notice numbers 6 and 7 (tilt events) have switched places. This switches their functionality.

---

### Post by MonkeyWrench32 on 2006-12-08
I have figured out how to use the search button as the middle button!  Here's how you do it:

1. Download this compiled version of [mvmouse](http://ubuntuforums.org/attachment.php?attachmentid=5244&d=1136859260).  Special thanks to [audax321](http://ubuntuforums.org/member.php?u=11439).  It was compiled under Breezy but it works with Edgy just fine (and it should for Dapper as well).

2. Open the terminal, navigate to where you downloaded mvmouse.tar.gz, and issue these commands:
```
tar xvzf mvmouse.tar.gz
sudo mv mvmouse /usr/bin/
```

3. Install xbindkeys if you haven't already done so:
```
sudo aptitude install xbindkeys
```

4. Make an .xbindkeysrc file in your home directory:
```
cd ~
gedit .xbindkeysrc
```

5. Paste this into gedit:
```
"mvmouse +0 +0 2 &"
c:122
```

7. Now, press Alt+F2 and run "xbindkeys".

8. Finally, add "xbindkeys" to your sessions so it begins on startup (System -> Preferences -> Sessions).

daou, feel free to add this to the HOWTO (granted that I didn't mess anything up or forget something).  ;)

---

### Post by NobodySpecial on 2006-12-08
MonkeyWrench32 - you rock!!!  Thanks for posting the solution - it works perfectly.  Now we can all "have our cake and eat it too."  :o

For those who are interested, the source code is here: [http://hocwp.free.fr/movemouse.html]("http://hocwp.free.fr/movemouse.html")

---

### Post by MonkeyWrench32 on 2006-12-08
> **NobodySpecial said:**
> MonkeyWrench32 - you rock!!!  Thanks for posting the solution - it works perfectly.  Now we can all "have our cake and eat it too."  :o

For those who are interested, the source code is here: [http://hocwp.free.fr/movemouse.html]("http://hocwp.free.fr/movemouse.html")
:D

I'm glad that this worked out for someone else!  It's also great that I have finally configured my mouse to work exactly as I want it to.

---

### Post by daou on 2006-12-10
> daou, feel free to add this to the HOWTO (granted that I didn't mess anything up or forget something). 

Nice work MonkeyWrench! Simple, clear, and it works like a charm. I'll add it to the howto.

---

### Post by wizzkid on 2006-12-12
Hi,

I owned a VX Rev mouse and I am wondering if i can program/bind the mouse button without using Beryl or Compiz? i want to use all 7 buttons :)

Please advice!


Thanks!

---

### Post by tweedledee on 2006-12-12
> **webfootedchicken said:**
> I can't for the life of me get the buttons to do anything. Ideally what I'd like to achieve:

Top-buttons
1: Left button = Single left click
3: Right button = Single right click
keycode 122: Search button = Open Firefox

Thumb-buttons
8: "the button nearest to you" = Double click
9: "the button away from you = Close app/Alt+F4

Top-wheel
4: Scroll-up = As is
5: Scroll-down = As is
6: Tilt-right = Scroll left
7: Tilt-left = Scroll right

Thumb-wheel
15: Pull = Minimize app
13: Push = Ctrl + Tab (Which will change active tab in Firefox)
17: Press = Open Nautilus home folder

Or am I completely dreaming, when I hope for this type of functionality? Are any of these do-able?:confused: 

BTW I'm not using XGL/Compiz.

Cheers again,

Web Footed Chicken

Perhaps a bit late, but you can look here for possible solutions, especially the double-click functionality: [http://www.ubuntuforums.org/showthread.php?t=316441](http://www.ubuntuforums.org/showthread.php?t=316441)

---

### Post by glave on 2006-12-12
Has anyone figured out how to change the middle mouse button function?  Under Windows, the logitech drivers let you define it to what you want, but more importantly, they let you disable the flywheel shifting from freescroll to click, so you can just pick one and leave it and assign functions to the button.

---

### Post by glave on 2006-12-12
I got the middle mouse button to work!

Well, *I* didn't discover it, but I did find someone who did!

[http://andy.hillhome.org/blog/2006/09/27/logitech-mx-revolution-in-linux/](http://andy.hillhome.org/blog/2006/09/27/logitech-mx-revolution-in-linux/)


There is also a link to a small program that duplicates the logitech driver function of setting the mode of the scroll wheel from free to click, to manual, etc!!!

---

### Post by michalm on 2006-12-26
Another way to use the search button as a middle click is to edit the file /usr/share/apps/kxkb/ubuntu.xmodmap

All it does is maps keycode 122 to the button 2 of the mouse.

Issue the command:

```
sudo vi /usr/share/apps/kxkb/ubuntu.xmodmap
```
and add a line like this:

```
keycode 122 = Pointer_Button2
```

Restart X and that's it.

---

### Post by hockeysk8 on 2006-12-27
A lot of what is done in the above instructions is unnecessary.  Udev is not needed.  I have posted complete instructions at [http://rootsmith.ca/mxrev-linux.html]("http://rootsmith.ca/mxrev-linux.html") to get the MX Revolution running on Linux in a simpler fashion.

---

### Post by NobodySpecial on 2006-12-27
hockeysk8 - Got news for you, this guide is perfectly correct, it doesn't use udev.  You might want to read through it again . . . .

---

### Post by drdrewusaf on 2006-12-28
I'm not sure if everyone saw the links in this thread to the Andy Hill site, but on his site he has linked to a tool for the middle mouse button called Revoco.  Right now the writer (Edgar Toernig) of the tool's website is down...a router issue he hopes to have fixed by the end of this week.

Anyway, I have two other links to version 0.3 so you can use Revoco now while Edgar gets his site up and running.

[http://www.drewandnati.com/revoco-0.3.tar.gz](http://www.drewandnati.com/revoco-0.3.tar.gz)
[http://www.missingreality.com/revoco/revoco-0.3.tar.gz](http://www.missingreality.com/revoco/revoco-0.3.tar.gz)

**For updates you will need to go to his site:**

[http://goron.de/~froese/revoco/](http://goron.de/~froese/revoco/)

Here are some instructions on getting it to work.

First extract everything in any fashion you like to where ever you like.

Next, open a terminal and change dir to where ever you extracted everything.  Then type:
```
make
```

Then, make it executable:
```
chmod a+x revoco
```

Finally, run it as superuser:
```
sudo revoco
```

The usage instructions in the program are VERY self explanatory.  For the auto shift speed setting, just type a number.  I use 10.  Once you send a command, it will stay that way until you change it...that means reboots, log outs, the works...the setting will stay the same.  I hope this helps some people looking for some middle button action.

Keep an eye out for updates, Edgar says he's looking to find a way to monitor the battery too, like setpoint.


Drew

---

### Post by mdwuznik on 2007-01-08
Hi again guys, 
I just got an idea of a workaround for the Xserver to avoid failure in case of unplugged Rev mouse.  This would require creating two different xorg.confs and a wrapper script for X to swap the config file for the right one if the mouse is present or not when starting. Anone interested, or that's too fishy?

Michal, with enough will to test if someone else needs it :)

---

### Post by knn on 2007-01-11
> **Search button-> mouse wheel click**
There is no mouse wheel click on the MX Revolution. One option is to bind it to the search button (below the top mouse wheel). The next step, by **MonkeyWrench32**, shows you how to do this.

1. Download this compiled version of [mvmouse]("http://ubuntuforums.org/attachment.php?attachmentid=5244&d=1136859260"). Special thanks to audax321. It was compiled under Breezy but it works with Edgy just fine (and it should for Dapper as well).

2. Open the terminal, navigate to where you downloaded mvmouse.tar.gz, and issue these commands:
```

tar xvzf mvmouse.tar.gz sudo mv mvmouse /usr/bin/
```

3. Install xbindkeys if you haven't already done so:

```
sudo aptitude install xbindkeys
```

4. Make an .xbindkeysrc file in your home directory:

```
cd ~ gedit .xbindkeysrc
```

5. Paste this into gedit:

```
"mvmouse +0 +0 2 &" c:122
```

7. Now, press Alt+F2 and run "xbindkeys".

8. Finally, add "xbindkeys" to your sessions so it begins on startup (System -> Preferences -> Sessions).

That solution is not optimal. First, it lags a lot, second, it generates a key release event immediately after the keypress.
As a solution, I've written a small app using the sources of xbindkeys and mvmouse as a reference, that sits in the background, intercepts keycode 122 and fakes button events just like mvmouse. However, it doesn't lag and it disables key autorepeat for button 122 and generates appropriate button press and button release events, so you can also middle drag. I plan to integrate some other functionality into it, e.g. sending alt-left and alt-right events and maybe even some revoco functionality, but it's not high on my priority list right now.
Attached is the source.
Extract it and compile:
```

gcc -c mxrev.c -o mxrev.o
gcc mxrev.o -o mxrev -L/usr/X11R6/lib -lX11 -lXtst
sudo cp mxrev /usr/bin

```
Then add mxrev to your session startup

spread and enjoy!

---

### Post by MonkeyWrench32 on 2007-01-11
> **knn said:**
> That solution is not optimal. First, it lags a lot, second, it generates a key release event immediately after the keypress.
As a solution, I've written a small app using the sources of xbindkeys and mvmouse as a reference, that sits in the background, intercepts keycode 122 and fakes button events just like mvmouse. However, it doesn't lag and it disables key autorepeat for button 122 and generates appropriate button press and button release events, so you can also middle drag. I plan to integrate some other functionality into it, e.g. sending alt-left and alt-right events and maybe even some revoco functionality, but it's not high on my priority list right now.
Attached is the source.
Extract it and compile:
```

gcc -c mxrev.c -o mxrev.o
gcc mxrev.o -o mxrev -L/usr/X11R6/lib -lX11 -lXtst
sudo cp mxrev /usr/bin

```
Then add mxrev to your session startup

spread and enjoy!
Got an error on step two of the compilation directions:

/usr/bin/ld: cannot find -lXtst
collect2: ld returned 1 exit status

---

### Post by knn on 2007-01-11
> **MonkeyWrench32 said:**
> Got an error on step two of the compilation directions:

/usr/bin/ld: cannot find -lXtst
collect2: ld returned 1 exit status

you need:
libxtst-dev
libxtst6

---

### Post by MonkeyWrench32 on 2007-01-11
Oh wow, that works wonderfully!  Much better than my method!

Thanks a million!  :D

---

### Post by knn on 2007-01-11
> **MonkeyWrench32 said:**
> Oh wow, that works wonderfully!  Much better than my method!

Thanks a million!  :D

Unfortunately, it's not perfect. While the search button is pressed, my app has exclusive control of the keyboard, and no other application gets keyboard events. This means no shift/alt/control/super-middle drag (blender, beryl window resizing, etc.). I'll try to fix it.

---

### Post by knn on 2007-01-12
Turns out mousekeys CAN be configured.
Edit /usr/X11R6/lib/X11/xkb/compat/mousekeys and remove the interpret parts that are not bound to symbols (i.e. everythin before // New Keysym Actions). (I've attached mine). Then restart the X server. Add keycode 122 = Pointer_Button2 to .Xmodmap and load xmodmap ~/.Xmodmap and xkbset m on startup.

EDIT: for gnome, use this to enable xmodmap on startup:
> **tomchuk said:**
>  gnome-settings-daemon would be very happy to run your .Xmodmap for you on login, all you have to do is ask nicely:
```

gconftool-2 --list-type string --type list --set /desktop/gnome/peripherals/keyboard/general/known_file_list "[.Xmodmap]"
gconftool-2 --list-type string --type list --set /desktop/gnome/peripherals/keyboard/general/update_handlers "[.Xmodmap]"

```

Another thing missing from the howto:
To change the wheel tilt action in firefox to horizontal scrolling, go to about:config and set mousewheel.horizscroll.withnokey.action to 0. If you've swapped the wheel tilt buttons as described in the howto, the direction will be reversed, change mousewheel.horizscroll.withnokey.numlines to 1.

---

### Post by tweedledee on 2007-01-13
Not having this mouse, I'm not entirely clear on why this seems so complicated.  So without suggesting that anything above is wrong or uncessary, I suggest two possibly simpler solutions:

1) Regarding the "button release" event generated with xbindkeys, you can use "b:X & Release" to make the event generated only when you release the button to avoid that event generation interference.  Of course, that doesn't work well if you need to click-and-drag.

2) You may want to look at xte, a component of xautomation, in the repos.  It handles mouse and keyboard event generation quite smoothly, including the ability to make use of click and drag events, although you still need some other interface (xbindkeys, whatever) to actually trap the event.

---

### Post by knn on 2007-01-13
> **tweedledee said:**
> Not having this mouse, I'm not entirely clear on why this seems so complicated.  So without suggesting that anything above is wrong or uncessary, I suggest two possibly simpler solutions:

1) Regarding the "button release" event generated with xbindkeys, you can use "b:X & Release" to make the event generated only when you release the button to avoid that event generation interference.  Of course, that doesn't work well if you need to click-and-drag.

2) You may want to look at xte, a component of xautomation, in the repos.  It handles mouse and keyboard event generation quite smoothly, including the ability to make use of click and drag events, although you still need some other interface (xbindkeys, whatever) to actually trap the event.

1) It doesn't work with click and drag and the problem is that mvmouse has to be loaded from disk and run, which can lag a lot. Plus if you have a laptop and it spins down the drive to save power, it will take a second or two to spin up again. That's unacceptable for a mouse button.
Besides, my program did just that, but the problem was that while you kept the button pressed, no other program could get keyboard input. XBindkeys works in the same way (my program was based on it).

2) I've tried writing a program that reads /dev/input/event3 and sends mouse3 press and release events using the XTest extension, but for some reason it didn't work. A program named xke (mentioned in this thread) does the same, but I couldn't get it to work. If xte requires xbindkeys, it's not a solution, because it's going to be slow like mvmouse, and the keyboard will be unavailable while dragging.

mousekeys, on the other hand, is the ideal solution, because it's built into the server and completely transparent (while my program and xke are in fact ugly hacks). The only problem with it was the hidden configuration file.

---

### Post by tweedledee on 2007-01-13
> **knn said:**
> 1) It doesn't work with click and drag and the problem is that mvmouse has to be loaded from disk and run, which can lag a lot. Plus if you have a laptop and it spins down the drive to save power, it will take a second or two to spin up again. That's unacceptable for a mouse button.
Besides, my program did just that, but the problem was that while you kept the button pressed, no other program could get keyboard input. XBindkeys works in the same way (my program was based on it).

2) I've tried writing a program that reads /dev/input/event3 and sends mouse3 press and release events using the XTest extension, but for some reason it didn't work. A program named xke (mentioned in this thread) does the same, but I couldn't get it to work. If xte requires xbindkeys, it's not a solution, because it's going to be slow like mvmouse, and the keyboard will be unavailable while dragging.

mousekeys, on the other hand, is the ideal solution, because it's built into the server and completely transparent (while my program and xke are in fact ugly hacks). The only problem with it was the hidden configuration file.

xte makes use of the XTest extension better than any of a variety of other programs I've tried, so if you need that function I recommend it as an interface.  However, since it does require something else to actually trap (at least for the functions you're describing), it's a not a solution for you.  Sounds like mousekeys is the best way.  It's great we have so much control (and even have the option of ugly hacks!), but a shame that somtimes really elegant solutions are available but buried too deep to be common knowledge.

---

### Post by ronnieredd on 2007-01-17
> **daou said:**
> Micha&#322;,

Could you take care of sending the lsusb and /proc/.../devices to the developers of lomoco (for both the MX and VX Revolution) because you apparently got hold of them already?

I've attached the following:

mxrevo_devices : contains MX Revolution section of cat /proc/bus/input/devices 
mxrevo_lsusb: contains MX Revolution section of lsusb -v
btw; the command to get those into a text file would be something like:
cat /proc/bus/input/devices > /home/YOURDIRECTORYHERE/inputdevices.txt
lsusb -v > /home/YOURDIRECTORYHERE/lsusb.txt

---

### Post by drainman on 2007-01-26
I cant get my VX to work properly, its working as it should just that tilt and zoom doesnt work. in win it works so it cant be the mouse, xev doesnt get any respons at all when pushing tilt/zoom all the other things work as it should. 
question is is there anybody else that have this problem???

/Jonas

---

### Post by daou on 2007-01-27
I confirmed the mousekeys approach for the search button. I'll add it to the howto.

---

### Post by daou on 2007-01-27
> Another thing missing from the howto:
To change the wheel tilt action in firefox to horizontal scrolling, go to about:config and set mousewheel.horizscroll.withnokey.action to 0. If you've swapped the wheel tilt buttons as described in the howto, the direction will be reversed, change mousewheel.horizscroll.withnokey.numlines to 1.


I added this to the howto as well.

---

### Post by daou on 2007-01-27
> **drainman said:**
> I cant get my VX to work properly, its working as it should just that tilt and zoom doesnt work. in win it works so it cant be the mouse, xev doesnt get any respons at all when pushing tilt/zoom all the other things work as it should. 
question is is there anybody else that have this problem???

/Jonas

I can't say because I don't have a VX. You could try asking Michal by PM (Private Message). He owns a VX and has posted in this thread with the username mdwuznik.

---

### Post by drainman on 2007-01-29
Thanks for the reply are going mad (i want my buttons). I will pm him
/thanks Jonas

---

### Post by gehrehmee on 2007-01-31
It is possible to write udev rules to match a single vendor/model part for both the mouse and the keyboard. My Logitech Elite keyboard is one such beast (i.t's a keyboard, but with a mouse wheel).

First, detect and record whether we're dealing with a mouse or a keyboard:

BUS=="usb", SYSFS{bInterfaceClass}=="03", SYSFS{bInterfaceProtocol}=="00", ENV{ID_CLASS}="mouse"
BUS=="usb", SYSFS{bInterfaceClass}=="03", SYSFS{bInterfaceProtocol}=="01", ENV{ID_CLASS}="kbd"
BUS=="usb", SYSFS{bInterfaceClass}=="03", SYSFS{bInterfaceProtocol}=="02", ENV{ID_CLASS}="mouse"

Then, act appropriately based on that device type and the vendor/model information:

KERNEL=="event*", SYSFS{idVendor}=="046d", SYSFS{idProduct}=="c30a", ENV{ID_CLASS}=="mouse" SYMLINK+="input/event-logielite-scroll"
KERNEL=="event*", SYSFS{idVendor}=="046d", SYSFS{idProduct}=="c30a", ENV{ID_CLASS}=="kbd" SYMLINK+="input/event-logielite-keyboard"

---

### Post by Jeeks on 2007-01-31
Thank you the HOWTO, it was very helpful.

I used it to install m Revolution VX and I could detect all the buttons as you mentioned in the first post. I have a problem though, I am using kubuntu and I want to assign functions for all the buttons. The zoom+ and - I want to use to increase and decrease the master volume. The tilts I want as alt_left and alt_right as for the thumb buttons I would like them to work as pgup and pgdown.

I couldn't figure out all these from the HOWTO and a little help would be greatly appreciated.

Is there a way to use the search button to open a particular application?

Thanks

---

### Post by quatrecouleurs on 2007-02-01
Hello !

I just used for 2-3 months your faq, thx, works, but by me there is a problem :

Several times my pointer freezes on the screen... I just wonder why it does that ? Seems to be because the "hardware recognizing method" ... Perhaps ? I don't be very aware of how my ubuntu really works.

But I get my pointer fully working under Xorg 7.1,  just made this changes in my xorg.conf file :

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "evdev"
    Option         "SendCoreEvents" "true"
    Option         "CorePointer"
    Option         "Device" "/dev/input/event0"
    Option         "WHEELRelativeAxisButtons" "4 5"
    Option         "HWHEELRelativeAxisButtons" "6 7"
    Option         "Emulate3Buttons" "false"
    Option         "Buttons" "20"
EndSection

```
edit : LOL it does not work, the device had changed, I should expect hinhinhin

---

### Post by schaefer on 2007-02-02
I followed this guide a month or so ago and ended up getting everything set up properly, except for one small problem. It seems that when I don't have the wireless USB connection hooked into my computer, X crashes. This only happens on the bootup, quiting before I get to the GDM screen. After logging in, I can remove the connection ok though. Anyways, this is a problem as I am using a laptop, and can't have my mouse with me all the time. Any help anyone could furnish would be appreciated. Cheers.

---

### Post by knn on 2007-02-03
> **schaefer said:**
> I followed this guide a month or so ago and ended up getting everything set up properly, except for one small problem. It seems that when I don't have the wireless USB connection hooked into my computer, X crashes. This only happens on the bootup, quiting before I get to the GDM screen. After logging in, I can remove the connection ok though. Anyways, this is a problem as I am using a laptop, and can't have my mouse with me all the time. Any help anyone could furnish would be appreciated. Cheers.

If the Rev is your corepointer, X won't start if it's not available. You should set up the mousepad as the corepointer, and the Rev as a secondary device with SendCoreEvents. Just remove Option "CorePointer" and in the server layout:
    InputDevice       "MX Rev" "SendCoreEvents"
    InputDevice       "<whatever mousepad is called>" "CorePointer"

Hope this helps, it should work (the wacom eraser and pencil is set up like this I think, and it works even if you don't have one).

---

### Post by schaefer on 2007-02-03
Thanks knn, that did the trick nicely :-)

Edit:

One small problem arose. When I go to system->preferences->mouse, editing the settings now edits the touchpad's settings. Is there any way to change the sensitivity of the VX Revolution? Right now its a little too responsive for my tastes. Thanks.

---

### Post by knn on 2007-02-05
> **schaefer said:**
> Thanks knn, that did the trick nicely :-)

Edit:

One small problem arose. When I go to system->preferences->mouse, editing the settings now edits the touchpad's settings. Is there any way to change the sensitivity of the VX Revolution? Right now its a little too responsive for my tastes. Thanks.

Probably not in Gnome, if that setting doesn't affect both mice. Try to change resolution in xorg.conf: [http://ftp.x.org/pub/X11R6.9.0/doc/html/mouse5.html]("http://ftp.x.org/pub/X11R6.9.0/doc/html/mouse5.html")

---

### Post by chunger on 2007-02-07
Thanks for such a great howto, I was worried for a little bit that I wouldn't be able to get my new MX Rev. to work with all the fancy buttons on it.  I have it working almost exactly the way I'd like it to, but I ran into a little problem and was hoping someone could help me out.  

What I'd like to do is have the thumb wheel flip through my desktops (ctrl+alt+left, or ctrl+alt+right).  I have my .xbindkeysrc working with the page forward and backwards in nautilus and firefox, and added a couple of extra lines which I thought would give me the pager flip function, but alas, it didn't work. 

Here is what my .xbindkeysrc looks like:
> "/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9
"/usr/bin/xvkbd -xsendevent -text "\[Ctrl_L]\[Alt_L]\[Left]""
  m:0x0 + b:15
"/usr/bin/xvkbd -xsendevent -text "\[Ctrl_L]\[Alt_L]\[Right]""
  m:0x0 + b:13

From this thread, and xev I found out that the thumb wheel push and pull is button 13 and 15, but I'm guessing its the ctr+alt+right/left statement that I got wrong.  If anyone has any ideas, it would be appreciated.

Thanks in advance :)

---

### Post by daou on 2007-02-07
> What I'd like to do is have the thumb wheel flip through my desktops (alt+left, or alt+right). I have my .xbindkeysrc working with the page forward and backwards in nautilus and firefox, and added a couple of extra lines which I thought would give me the pager flip function, but alas, it didn't work. 

Make sure xbindkeys is running.

```
xbindkeys &
```

And check the .xbindkeysrc file. I would suspect it is case-sensitive... 

change your [left] to [Left] etc.  <--EDIT: the post doesn't capitalize the L. It's "Left". Probably did the same to your post.

And whenever you make changes to your .xbindkeysrc file, remember to either restart xbindkeys or restart X.

---

### Post by daou on 2007-02-07
> Several times my pointer freezes on the screen...

If you mean a quick freeze, about a second or so, then it's just a "feature" of the MX Revo. The MX sometimes goes to sleep to conserve power. It then checks every now and then to see if you are moving it, and it won't do anything until it does this check.

---

### Post by daou on 2007-02-07
> **Jeeks said:**
> Thank you the HOWTO, it was very helpful.

I used it to install m Revolution VX and I could detect all the buttons as you mentioned in the first post. I have a problem though, I am using kubuntu and I want to assign functions for all the buttons. The zoom+ and - I want to use to increase and decrease the master volume. The tilts I want as alt_left and alt_right as for the thumb buttons I would like them to work as pgup and pgdown.

I couldn't figure out all these from the HOWTO and a little help would be greatly appreciated.

Is there a way to use the search button to open a particular application?

Thanks


You can assign functions to the buttons with xbindkeys and xvkbd. Have a look at their manuals for the correct syntax. I did this with my Kubuntu a few days back.

First you need to make sure xbindkeys starts with Kubuntu:

```
cd ~/.kde/Autostart
ln -s /usr/bin/xbindkeys xbindkeys
```

This makes a symbolic link to xbindkeys in the Autostart folder. KDE runs everything in the autostart folder at startup. Or you could make a script file in there that starts xbindkeys and make it executable. The above method is easier though.

Then make a .xbindkeysrc file in your home directory:
```
kate ~/.xbindkeysrc
```

Then, to start a program like amarok with the search key, add these lines to the file:
```
"amarok"
c:122

```

To emulate an alt-left with a button, say button 15, add these to the file:
```
"xvkbd -xsendevent -text "\[Alt_L]\[Left]""
m:0x0 + b:15
```

The [left] is supposed to be Left, capital L.

And so on. If you want a volume change, you need to send an XF86VolUp or XF86VolDown event.

---

### Post by hoarycripple on 2007-02-07
Everything works properly after I followed this guide, but there is one thing I can't resolve.  If i use "xkbset m" to get the search button to middle click, it apparently dies after a few minutes and I have to keep typing this command into the command line to get it working again.  Anyone else have this issue?  Thanks.

---

### Post by daou on 2007-02-07
> **hoarycripple said:**
> Everything works properly after I followed this guide, but there is one thing I can't resolve.  If i use "xkbset m" to get the search button to middle click, it apparently dies after a few minutes and I have to keep typing this command into the command line to get it working again.  Anyone else have this issue?  Thanks.

Try and see if xkbset is throwing errors when it's running. This saves the output of xkbset in two files:

```
xkbset m 1> ~/xkbset_output 2> ~/xkbset_errors
```

They both go into your home folder. When xkbset dies, open the errors file and see if there is anything suspicious there. If there's nothing useful there, try looking through the output file for anything out of the ordinary.

---

### Post by hoarycripple on 2007-02-07
> **daou said:**
> Try and see if xkbset is throwing errors when it's running. This saves the output of xkbset in two files:

```
xkbset m 1> ~/xkbset_output 2> ~/xkbset_errors
```

They both go into your home folder. When xkbset dies, open the errors file and see if there is anything suspicious there. If there's nothing useful there, try looking through the output file for anything out of the ordinary.

I'm not sure that the program is actually crashing or what.  I get no output from xkbset.  But I left the computer alone for a while, came back, and sure enough, the middle-click is not working again.  This is very strange.  I will go back through this thread and see if I missed something, but I am pretty sure that I followed the directions properly.  Thank you.

---

### Post by knn on 2007-02-07
> **daou said:**
> Try and see if xkbset is throwing errors when it's running. This saves the output of xkbset in two files:

```
xkbset m 1> ~/xkbset_output 2> ~/xkbset_errors
```

They both go into your home folder. When xkbset dies, open the errors file and see if there is anything suspicious there. If there's nothing useful there, try looking through the output file for anything out of the ordinary.

xkbset only turns on mousekeys (and then quits), which is built into the server. I never had this problem. I'm not sure, but is there an auto-deactivating feature for a11y options that might be interfering here? I think windows can do that kind of thing.

---

### Post by hoarycripple on 2007-02-07
> **knn said:**
> xkbset only turns on mousekeys (and then quits), which is built into the server. I never had this problem. I'm not sure, but is there an auto-deactivating feature for a11y options that might be interfering here? I think windows can do that kind of thing.

I thought that xset might be interfering with things, so I removed my xset commands from the xinitrc, and still I get the same thing.  After a while, the middle-click stops working.  Any ideas at all would be appreciated.  Thank you.

---

### Post by chunger on 2007-02-08
> **daou said:**
> Make sure xbindkeys is running.

```
xbindkeys &
```

And check the .xbindkeysrc file. I would suspect it is case-sensitive... 

change your [left] to [Left] etc.  <--EDIT: the post doesn't capitalize the L. It's "Left". Probably did the same to your post.

And whenever you make changes to your .xbindkeysrc file, remember to either restart xbindkeys or restart X.

Hi Daou

I added xbindkeys to my startup in gnome sessions, which lets my side buttons work (buttons 8 and 9), but the thumb wheel is still a no go.  I've restarted X, tried (killall xbindkeys), and restarted with (xbindkeys &), also tried a complete system restart. 

My .xbindkeysrc has the left and right listed as 'Left' and 'Right' with the correct case in brackets [ ] (I guess the post somehow changed it to lower case).   What I did find that might be odd is that with my .xbindkeysrc as is, my thumbwheel ends up performing the same functions as buttons 8 and 9, like it doesn't see the [Ctrl] statement.

I appreciate your help... any other ideas?

Thanks

Here is my .xbindkeysrc again...
> "/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9
"/usr/bin/xvkbd -xsendevent -text "\[Ctrl_L]\[Alt_L]\[Left]""
  m:0x0 + b:15
"/usr/bin/xvkbd -xsendevent -text "\[Ctrl_L]\[Alt_L]\[Right]""
  m:0x0 + b:13

---

### Post by daou on 2007-02-08
> My .xbindkeysrc has the left and right listed as 'Left' and 'Right' with the correct case in brackets [ ] (I guess the post somehow changed it to lower case). What I did find that might be odd is that with my .xbindkeysrc as is, my thumbwheel ends up performing the same functions as buttons 8 and 9, like it doesn't see the [Ctrl] statement.

I'm not sure if it will help, but try replacing the ctrl and alt statements in case xvkbd has trouble with their keysyms. For example, change "\[Alt_L]" to "\A" and "\[Ctrl_L]" to "\C".

---

### Post by chunger on 2007-02-08
> **daou said:**
> I'm not sure if it will help, but try replacing the ctrl and alt statements in case xvkbd has trouble with their keysyms. For example, change "\[Alt_L]" to "\A" and "\[Ctrl_L]" to "\C".

Thanks for your input, but I still couldn't get it to work.  I've tried all sorts of variations of using the possible syntax for Control and Alt, from abbreviated 'Ctrl', to 'C' to 'Control', and all case combinations with and without the [brackets], not to mention using the "_L" or not.  I stopped and restarted xkeybinds every time I changed the .xkeybindsrc file, but I couldn't get the desired effect.  I guess I'll keep tinkering with it and see what else I can find.  Any other suggestions will be appreciated.

Thanks:)

---

### Post by hoarycripple on 2007-02-09
> **hoarycripple said:**
> Everything works properly after I followed this guide, but there is one thing I can't resolve.  If i use "xkbset m" to get the search button to middle click, it apparently dies after a few minutes and I have to keep typing this command into the command line to get it working again.  Anyone else have this issue?  Thanks.

I think I've found a solution to the problem.  I used xkbset-gui to set some parameters and then enable mousekeys.  Then saved the info to .xsession.  And so far mousekeys are working for me, without having to keep executing "xkbset m" in the command line.  The relevant bit of the .xsession:

```
 xkbset b r rate 500 33 perkeyrepeat \ 00ffffffdffffbbffadfffdfffdfe5efffffffffffffffffffffffffffffffff m 1 ma 160 40 30 30 \
 500 -a -st twokey latchlock -sl 300 -bo 300 f dumbbell -led \
 feature slowwarn slowpress slowaccept -slowreject -slowrelease \ 
bouncereject stickybeep -ov1 -ov2 groupswrap wrap 1 ignoregrouplock \
nullify -shift -lock -control -mod1 -mod2 -mod3 \
-mod4 -mod5 ignorelock -shift -lock -control -mod1 -mod2 -mod3 \
 -mod4 -mod5 & 
```

I don't know why exactly that works, but it does.  Thanks for the guide and the many excellent replies.

---

### Post by Jeeks on 2007-02-13
I used this guide to setup my VX a couple of weeks ago and it worked like a charm. I loved everything about it. For some reason I had to reformat my laptop and re install ubuntu. Immediately I rushed to this guide to configure the mouse. To my surprise this time X did not start at all. I tried and tried and re tried and nothing happened. What makes me amazed is that it worked before, why wouldn't it work again?

Ok, I don't know how but now things are back on track.

---

### Post by daou on 2007-02-14
I'm glad it worked (again). I just got to try the VX for the first time. A friend bought one yesterday. It's a really nice mouse for laptops. I would've bought one for my laptop, but I think one Rev mouse is enough candy for any person :wink: . Only thing missing is the switching between free scroll when pressing the middle mouse wheel. But it's really well thought out, like the USB receiver slot (which also turns off the device to save power when the receiver is put in).

Did your problems with Ubuntu have anything to do with upgrading to kernel 2.6.17-11? This happened to me. It was a 15 minute fix, had to reinstall the nvidia drivers.

---

### Post by wh0rd on 2007-02-14
This tutorial works up to when X Starts and GDM is displayed, so at the login screen the mouse is detected and works. After I start logging in the slash screen displays and the mouse freezes and remains that way until I unplug the USB dongle and plug it back in?

---

### Post by Capone on 2007-02-28
any idea how to make the search key to actually start a new google tab in firefox? My scroll key already supports clicking..

btw, my mouse is a VX

---

### Post by knn on 2007-03-01
Add this to .xbindkeysrc

```
"firefox http://www.google.com"
c:122
```

---

### Post by knn on 2007-04-03
Just a quick note for feisty users: the mousekeys configuration file is now located in /usr/share/X11/xkb/compat/

Edit: And to get rid of udev, I made a simple script (attached) that finds the event number assigned to the mouse and symlinks it to /dev/input/event9 (after removing /dev/input/event9). I've added it as an initscript before gdm, and it seems to work.
It's hardcoded to find the mx rev using the vendor and product ids, so if you want to use it with the vx rev, you'll have to modify those. You can find the id's in /proc/bus/input/devices (and in the first post)

To install it: copy the attachment to /etc/init.d/ and make it executable. Then you have to add an initscript for every runlevel that starts gdm. These are normally 2,3,4 and 5.
The directories for these runlevels are /etc/rc*x*.d , where x is the runlevel number. In these directories there should be a symlink called S*xx*gdm, where xx is a number (13 in my case). This is a symlink to the script that starts gdm. Find an unused number lower than 13 (in my case there was an S12something, S11something and S10something file, so I chose 09) and make a symlink to the mxrev.sh script in every directory containing Sxxgdm:
```

for i in 2 3 4 5; do
cd "/etc/rc$i.d"
ln -s ../init.d/mxrev.sh S09mxrev
done

```
replace 09 with the number you chose.

---

### Post by Church on 2007-04-20
I used this and other guides (whatever i have googled up) with good success on slackware-current using modular X aswell. 
at first i tried using main scroller as middle button via revoco's help .. but in mx revo mouse it just sucks, too easy to misclick/misscroll. and in mozilla based browsers easy to use middle click is essential. so i mapped search to mclick. only issue i've left with - as mouse is connected to KVM switch, after booting doze box aswell, logitech's software seems to change mouse behavior. i have to disconnect/reconnect mouse to restore search as middle (in doze i could set it only when i installed alongside official drivers [uberOptions xml hack]("http://www.mstarmetro.net/~rlowens/uberOptions/")). btw, if you haven't installed xkbset, you can switch mousekeys on/off with shift+kpdnumlock.
For my convenience i made package including revoco, xkbset, udev rules creating hiddev devices and install script that auto-edits mousekeys definition file and setts up Xmodmap related things for root & users (def. GID=100)

( [ ! -f /etc/X11/xkb/compat/mousekeys.orig ] && \
cd /etc/X11/xkb/compat && cp mousekeys mousekeys.orig && \
sed -i -e '/Keypad\ actions./,/New\ Keysym\ Actions/d' mousekeys )

( for USER in root $(grep ':[0-9]\{1,\}:100:' /etc/passwd|grep sh$|cut -d: -f1);do
bin/su $USER -c "gconftool-2 --owner=$USER --list-type string --type list --set \
/desktop/gnome/peripherals/keyboard/general/known_file_list '[.Xmodmap]'
gconftool-2 --owner=$USER --list-type string --type list --set \
/desktop/gnome/peripherals/keyboard/general/update_handlers '[.Xmodmap]'"
grep "keycode 122" $(grep ^$USER /etc/passwd|cut -d: -f6)/.Xmodmap >/dev/null 2>&1 && \
echo "$USER's ~/.Xmodmap already contains *keycode 122 = Pointer_Button2*" || \
echo "keycode 122 = Pointer_Button2" >> $(grep ^$USER /etc/passwd|cut -d: -f6)/.Xmodmap && \
chown $USER $(grep ^$USER /etc/passwd|cut -d: -f6)/.Xmodmap
done )

for xorg.conf all that i needed was
Section "InputDevice"
Identifier "Mouse1"
Driver     "evdev"
Option     "Phys" "usb-*/input0" # to use with whatever event #
Option      "Name" "Logitech USB Receiver"
Option      "HWHEELRelativeAxisButtons" "7 6" # to reverse horizontal tilt
EndSection

---

### Post by orren2002 on 2007-04-24
Hello

 Can someone explain how get mx revolution to work with Feisty

 Thanks in advance 

orren

---

### Post by TomPreuss on 2007-04-24
> **orren2002 said:**
> Hello

 Can someone explain how get mx revolution to work with Feisty

 Thanks in advance 

orren

Are the instructions in the first post not working for you?  What have you tried?  Are you getting any errors?

---

### Post by Nomearod on 2007-04-25
The how-to didn't worked :( 

After restart I didn't have X and had to change the x.org. :confused: 

I'm using Feisty Fawn and here's mine file where MX Revolution is listed:

> 
paulo@paulo-laptop:~$ cat /proc/bus/input/devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
H: Handlers=mouse0 event0 ts0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

[B]I: Bus=0003 Vendor=046d Product=c51a Version=0111
N: Name="Logitech USB Receiver"
P: Phys=_usb-0000:00:1d.1-1/input0_
S: Sysfs=/class/input/input2
H: Handlers=mouse1 event2 ts1 
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0003 Vendor=046d Product=c51a Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.1-1/input1
S: Sysfs=/class/input/input3
H: Handlers=kbd event3 
B: EV=f[/B]
B: KEY=7fff 2c3027 bf004440 0 0 1 f80 8807c000 667bfa d9415fed 8e0000 0 0 0
B: REL=40
B: ABS=1 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input4
H: Handlers=kbd event4 
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0007 Version=0000
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio3/input0
S: Sysfs=/class/input/input5
H: Handlers=mouse2 event5 ts2 
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=ACPI_FPB/button/input0
S: Sysfs=/class/input/input6
H: Handlers=kbd event6 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/class/input/input7
H: Handlers=kbd event7 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/class/input/input8
H: Handlers=event8 
B: EV=21
B: SW=1



The underlined part is what I copied to the udev config. file.

help? :confused:

---

### Post by KaMZaTa on 2007-04-25
for me dosn't work. Please help me!

---

### Post by orren2002 on 2007-04-26
hello 

Its don't work for me in Feisty 
this udev is that really necessary in Fiesty

---

### Post by Perrako on 2007-05-02
So, after struggling to figure out what the udev code was saying, I stumbled upon a bit of an issue. The reason the udev assignment works is that linux creates event0 through event9 no matter how many devices are plugged in. However, I have more than 10 devices, meaning event9 is occupied. The obvious fix would be to reassign the udev rule to event15, but event15 isn't by default created -- enough for each device over event9. How can I make linux create an event15 by default on boot?

---

### Post by coredix on 2007-05-19
hi,
this is my first nip from the ubuntu cup. And yes, i´m impressed :)

Thanks to this thread, i did figure out how to get my Revo fully featured in Feisty.

I´ve written a german howto for kubuntu 7.04 which is based on this one.

BIg thanks to daou and knn!

If somebody is interested in translating mine to help out those struggling Feisty users, who don´t know german - please feel free to do so.
My english is´nt good enough to turn it into something helpful, i  think.
You can read it --> [here]("http://mddn.net/node/14") (i´m mddn there)

coredix

---

### Post by knn on 2007-05-20
> **coredix said:**
> hi,
this is my first nip from the ubuntu cup. And yes, i´m impressed :)

Thanks to this thread, i did figure out how to get my Revo fully featured in Feisty.

I´ve written a german howto for kubuntu 7.04 which is based on this one.

BIg thanks to daou and knn!

If somebody is interested in translating mine to help out those struggling Feisty users, who don´t know german - please feel free to do so.
My english is´nt good enough to turn it into something helpful, i  think.
You can read it --> [here]("http://mddn.net/node/14") (i´m mddn there)

coredix

Nice work. Just a small correction: In this line:
```
eventname=$(cat /proc/bus/input/devices | grep "Vendor=046d Product=c51a" -A 4 | grep "Handlers=mouse" | sed "s/.*\(event.\).*/\1/")
```

You should replace "Vendor=046d Product=c51a" with whatever your mouse's product id is. (the vendor id should remain the same, since they're all Logitech, but you could use this for other mice as well. The product id is different for the vx revo). The product id's can be found in the first post, but you can also run
```
cat /proc/bus/input/devices
```
and check there (my Revo's version was different than the version posted in the first post, so I did not include a version check)

> So, after struggling to figure out what the udev code was saying, I stumbled upon a bit of an issue. The reason the udev assignment works is that linux creates event0 through event9 no matter how many devices are plugged in. However, I have more than 10 devices, meaning event9 is occupied. The obvious fix would be to reassign the udev rule to event15, but event15 isn't by default created -- enough for each device over event9. How can I make linux create an event15 by default on boot?

Perhaps you could try my simlink trick (previous post), and change event9 to event15 in it. You won't need udev at all then.

---

### Post by coredix on 2007-05-20
> **knn said:**
> Nice work. Just a small correction: In this line:
```
eventname=$(cat /proc/bus/input/devices | grep "Vendor=046d Product=c51a" -A 4 | grep "Handlers=mouse" | sed "s/.*\(event.\).*/\1/")
```

You should replace "Vendor=046d Product=c51a" with whatever your mouse's product id is. (the vendor id should remain the same, since they're all Logitech, but you could use this for other mice as well. The product id is different for the vx revo). The product id's can be found in the first post, but you can also run
```
cat /proc/bus/input/devices
```
and check there (my Revo's version was different than the version posted in the first post, so I did not include a version check)

Thx for the correction, there is a completely new version of my howto online now.
Pls take look [here]("http://mddn.net/node/14").


> **knn said:**
> 
Perhaps you could try my simlink trick (previous post), and change event9 to event15 in it. You won't need udev at all then.

I can confirm that. event15 works fine for me, no need for udev.

Some posts before there was a need for a quick taskselectionbox one can get with a mousebutton.
There is a simple way to put this function on the searchbutton. A description is in my howto near the end, 
Maybe someone can translate it and post it here ;)

coredix

---

### Post by okke on 2007-05-22
For me the VX Rev doesn't work in Feisty anymore.. The X won't start unless I remove the parts about the the VX in xorg.conf. Anyone else got the problem?

---

### Post by daou on 2007-05-23
Hi,

Sorry for not checking up on the thread and replying for a while. I've been very busy this spring hacking away at the Linux based Nokia 770 for a uni project. Now I'm working at an embedded solutions company doing Linux and electronics work. That should be incentive enough for anyone to learn some Linux ;)!

I just started working on a program today that reroutes events from the MX Revo through uinput back to X as keyboard events (or any events for that matter). Basically this means no more pulling hairs with evdev, udev, xorg.conf, xvkbd, xbindkeys, and mousekeys. I don't know about everyone else, but I got tired of it, especially after the Feisty upgrade.

Basic functionality is already working. My free time is quite limited, but once I get the program polished up enough, I'll post about it here for anyone interested.

---

### Post by daou on 2007-05-25
The first release of the program is done. I've posted instructions at the top of the how to. Let me know if there are any problems.

And I would appreciate it if a VX user could test the program. If it doesn't work, then someone with a VX needs to do some hexdumping on an event handler.

---

### Post by Mack1 on 2007-05-26
Hi Daou!

Man...someone finally comes up with this nifty program....getting your mousebuttons to
work decently is (stupidly enough) soo much work in (k)ubuntu...i couldn't believe it at first.

I own a logitech G5 mouse now, which is an excellent mouse aswell.

I've installed your program and it does well....nothing ;-)

im pretty sure this is due to the fact that my mouse sends out what you call rawcodes in
your program that i haven't configured yet.

Can you tell me how i can lookup what the rawcodes are for my mouse? (i think it's xev)

xev tells me this when i push my scrollwheel:

ButtonPress event, serial 31, synthetic NO, window 0x3e00001,
    root 0x137, subw 0x0, time 7753479, (120,113), root: (123,301),
    state 0x10, button 2, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0x3e00001,
    root 0x137, subw 0x0, time 7753646, (120,113), root: (123,301),
    state 0x210, button 2, same_screen YES

only thing i can imagine is the 'state 0x..." code that changes but i entered that in your config file, doesn't work.

I want to bind the keyboard 'L' key to pressing my mousewheel for in game usage.

Can i use xev's output (and what part) to make it work with your program you think?

I'm willing to test anything you want and givefeeback in order to make your program more universal.

I think (k)ubuntu needs this program bad as this is one the things that is withholding me from
ditching windows all together!

(k)ubuntu rocks!

---

### Post by daou on 2007-05-26
>  I own a logitech G5 mouse now, which is an excellent mouse aswell.

I've installed your program and it does well....nothing :wink:

im pretty sure this is due to the fact that my mouse sends out what you call rawcodes in
your program that i haven't configured yet.

Can you tell me how i can lookup what the rawcodes are for my mouse? (i think it's xev)
For the G5 the program would need a bit more than just the rawcode changes. I did, however, code some parts so that it could be used for other mice as well. This means that support for the G5 could possibly be added with little effort.

So if you (or anyone else for that matter) want support for a different mouse, I will need the following things:

1. The complete output of your /proc/bus/input/devices file.

```
$ cat /proc/bus/input/devices > ~/devices_output
```If you have multiple mice connected, please tell me which one of the sections refers to the mouse you want support for. From that file, I need to know the Vendor and Product IDs, and possibly the Handler line for each of the sections that refers to the mouse (MX and VX have two sections, one being simply for the search button). Most likely just sending the output will do fine.

2. This is the trickier bit and might take a little explaining. I need you to hexdump your event handler output. 
First, you need to find out the event name to look at. This can be found in the previously mentioned /proc/bus/input/devices file. You need to know the Vendor and Product ID for your mouse. If you don't know them, google them. If you still can't find them, look at the bottom of the post for additional instructions.

Here is the output for my mouse:

```
I: Bus=0003 Vendor=046d Product=c51a Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-4/input0
S: Sysfs=/class/input/input7
H: Handlers=mouse2 ts2 **event3** 
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

```The bolded part is the important bit. This is the event name you need for the next step.

3. Now starts the actual hexdumping. Run the following command, replacing "event3" with the event name you got in the previous step:

```
$ sudo cat /dev/input/event3 | hexdump
```Now you get lots of hexadecimal code running across your screen whenever you do something with your mouse. Now, for each button on your mouse, copy down exactly what happens. Try clicking a button several times until you are sure that a certain couple of lines refer to exactly *that* button.

For example, when I press and release the thumb mouse wheel on my MX Revo, I get the following 4 lines:

```
00029f0 7d62 4658 240d 0008 0001 011c 0001 0000
0002a00 7d62 4658 2412 0008 0000 0000 0000 0000
0002a10 7d63 4658 68d0 0005 0001 011c 0000 0000
0002a20 7d63 4658 68d4 0005 0000 0000 0000 0000

```The first and the third lines are important. Notice how they are almost the same. The first one is for pressing and the third one is for releasing the button. The rawcode is actually 4 bytes in that line. You can stop the program by pressing Ctrl-C so you don't lose track of which lines referred to a certain button. For each button, I would like something like this:

```

Thumb wheel press
00029f0 7d62 4658 240d 0008 0001 011c 0001 0000   press
0002a00 7d62 4658 2412 0008 0000 0000 0000 0000
0002a10 7d63 4658 68d0 0005 0001 011c 0000 0000  release
0002a20 7d63 4658 68d4 0005 0000 0000 0000 0000
```Some buttons only register a press event and no release. You will notice this when you only get two lines on hexdump, or that the lines always stay the same. This is very important information for me, otherwise the button won't work. This is the case for my top wheel tilt events. When this happens, I would like the following information:

```
Top wheel tilt left (no release event)
0000840 7fd7 4658 8545 000e 0002 0006 ffff ffff    press
0000850 7fd7 4658 8548 000e 0000 0000 0000 0000

```And that's pretty much it. Stick all the hexdumps with comments in a file and send them to me.

[B]
------------------- Can't find Vendor and Product ID? -----------------------[/B]
Run the following command:
```
$ ls /dev/input
```Now run 
```
$ sudo cat /dev/input/eventX | hexdump
```for each event listed by ls in that folder, replacing X with the different numbers. Once you see output when you move your mouse or press its buttons, you've found it. It might not be necessary at this point, but you can now look at the /proc/bus/input/devices and find the section with that event name in its handler. That section's Vendor and Product IDs are for your mouse.

>  I'm willing to test anything you want and givefeeback in order to make your program more universal.I hope the length of the post hasn't changed your mind ;). But on a more serious note, I'm glad you feel this way. The reason Linux and its distros are becoming such excellent pieces of software (or should I call them artwork), is because there are people with a passion to help and share to make it better. Try finding that on a Windows forum. Even theír hired staff won't help as much as the Linux community. I owe a lot to Linux and I'm glad to be able to give something back.

If someone feels confident coding C and is interested in supporting the program, I can give commit privileges to the SVN repository.

---

### Post by Mack1 on 2007-05-26
Hello there :-)

man....that's a long list lol.

Nah. im not at home but tomorrow i will be and will see if i can
send the infos you asked for.

Keep in mind that i am at the point that i can run and maintain my linux system now
but that i'm not a 26 year linux-veteran...i switched to linux (kubuntu) just
last year. So programming is a thing i cannot do for you, sorry :(

will let you know tomorrow!

ps: i'm glad you feal this way; i have the same fealings. the community fealing 
     hence 'we help eachother' is a warm fealing. indeed not much seen in the ms-world....

---

### Post by daou on 2007-05-26
Good news,

The program is ready to support other mice. If you want mouse support, just provide me with get the necessary info (/proc/bus/input/devices and hexdumps).

---

### Post by Mack1 on 2007-05-27
Hi again Daou,

I just sent you a private message with the information for my logitech G5 laser mouse.

Hopefully this is usefull to you!

I'm always willing to help, just let me know.

Hopefully your nifty program can work for my mouse aswell and help others
that use the G5!

Mack

ps: when i run sudo btnx i get:
      cat: /home/daou/events: No such file or directory
      shouldn't this be cat /home/[my login]/events?

---

### Post by daou on 2007-05-27
Thanks for the info,

btnx should now support G5. Please try it as soon as possible so I can confirm that it actually works.
Make sure to get the latest (0.02.1 at this time). And uninstall any previous btnx that you may have ("sudo make uninstall" before "make" and "make install").
When btnx starts, it should autodetect your mouse. In your case, it should detect the G5 and copy the default configuration file from /etc/btnx/defaults/default_config_g5 to /etc/btnx/btnx_config.
Notice that I commented out the button functions for the left and right mouse buttons and the mouse wheel. You probably don't want to send any extra events when using these buttons. 

If, however, you want some other functionality for the mouse wheel press other than the default action used by kubuntu, you can uncomment it and tell Xmodmap to map the mouse wheel press to some other event. You need to tell Xmodmap to remap the button so you won't get duplicate events. This is because btnx can't actually stop any events from taking place that X handles. It sniffs the same event handler that Xserver looks at.

>  ps: when i run sudo btnx i get:
      cat: /home/daou/events: No such file or directory
      shouldn't this be cat /home/[my login]/events?You are absolutely right (actually it should be /etc/btnx/events and owned by root because btnx can only be run by root). I noticed this already while browsing the code last night and fixed it in v0.02. It was a leftover from debugging and prevented the program from working at all on other people's computers.

---

### Post by Mack1 on 2007-05-27
man you're fast lol!

Excellent

Ok i'm very eagerly following everything to get the new version installed BUT...i get this error:

i type:  sudo make uninstall
i get back:

./scripts/uninstall.sh
make: execvp: ./scripts/uninstall.sh: Access denied
make: *** [uninstall] Error 127

Any ideas?


hardheaded as i am i just went trhough make, make install etc. btnx has restarted but has not copied the G5_config file to btnx_config.
just noticed this and wanted to let you know, maybe it is because of the above error i don't really know.

---

### Post by daou on 2007-05-27
>  i type:  sudo make uninstall
i get back:

./scripts/uninstall.sh
make: execvp: ./scripts/uninstall.sh: Access denied
make: *** [uninstall] Error 127Make sure you have execute privileges for the uninstall script. Do a 
"chmod a+x ./scripts/uninstall.sh" in the btnx source directory. It should be executable by default.

> hardheaded as i am i just went trhough make, make install etc. btnx has restarted but has not copied the G5_config file to btnx_config.
just noticed this and wanted to let you know, maybe it is because of the above error i don't really know.It might not have detected the G5 correctly... do a "cat /etc/btnx/btnx.log" and send me the output. Or just run "sudo ./btnx" in the btnx source directory. EDIT: this will dump any errors on the terminal output.

---

### Post by daou on 2007-05-27
> Make sure you have execute privileges for the uninstall script. Do a 
"chmod a+x ./scripts/uninstall.sh" in the btnx source directory. It should be executable by default.This was a bug in the makefile. It's fixed, just download the version 0.02.1 again, or run the chmod command.

---

### Post by Mack1 on 2007-05-27
> **daou said:**
> It might not have detected the G5 correctly... do a "cat /etc/btnx/btnx.log" and send me the output. Or just run "sudo ./btnx" in the btnx source directory.

Both actions do nothing.

cat /etc/btnx/btnx.log gives no errors but the file doesn't get updated and it's empty

sudo ./btnx gives:
Did not find additional event handlers.
No startup errors

What now?

Another thing: when i restart btnx when the config file has been updated it says in konsole:
Restarting MX Revolution mouse event rerouter btnx

argl...what's with that MX rev that's soooo great lol!


However:

You are now officially my hero :D

I've manually copied the G5 config file (see my previous post) to btnx_config and edited
the buttons/keystrokes.

I fire up my favorite game and voila! it works like a charm!

ok here it goes: (OK if working)

mouse wheel scroll up:        OK
mouse wheel scroll down:   OK
mouse wheel left scroll:      OK
mouse wheel right scroll:    OK
mouse left button:               NOT TESTED
mouse right button:            NOT TESTED

mouse wheel press :  NOT OK
(i assign that it should press the C button on my keyboard, it does it once but after that it
seems to act like a ctrl-v action..it sometimes remembers last entered keystrokes and once pressed
shows them...wierd)

thumb button:           NOT OK
Same as the mouse wheel press...somehow it seems to remember last entered keystrokes and copy-pastes them in konsole etc.

However....i wanted my mousebuttons to emulate keystrokes in some of my games just as the logitech driver in windows did.....and your nifty program does it!! it works excellently in the game i tested.

Thanks very much for this!

If you want me to help, again, let me know.

Mack

---

### Post by daou on 2007-05-27
> Both actions do nothing.

cat /etc/btnx/btnx.log gives no errors but the file doesn't get updated and it's empty

I hope I'm not wearing out your patience... the program detected the device but did not set it :mrgreen:. The bug is fixed now in 0.02.2

>  mouse wheel press :  NOT OK
(i assign that it should press the C button on my keyboard, it does it once but after that it
seems to act like a ctrl-v action..it sometimes remembers last entered keystrokes and once pressed
shows them...wierd)

thumb button:           NOT OK
Same as the mouse wheel press...somehow it seems to remember last entered keystrokes and copy-pastes them in konsole etc.

Can you send me the configurations you used for those buttons so I can check them.

---

### Post by daou on 2007-05-27
You can also use xev to look at what input is sent once you have configured a button. So if you set a button to press C, make sure xev sees the C and not extra modifier keys (ctrl, alt, etc).

---

### Post by daou on 2007-05-27
>  Another thing: when i restart btnx when the config file has been updated it says in konsole:
Restarting MX Revolution mouse event rerouter btnx

argl...what's with that MX rev that's soooo great lol!You'll know once you get one ;) (everything but the price). Theres still a lot of text sprinkled throughout the program that refers to btnx as a program for MX only. Obviously this has changed, so I'll fix them when I see them.

---

### Post by Mack1 on 2007-05-27
Hehe no i'm still here :D

I sent you the current settings file.

---

### Post by daou on 2007-05-27
>  # Thumb button
# Does an Alt+LeftMouseButton. Useful for dragging windows.
Button
rawcode =    0x01011300
type     =    0
keycode =    KEY_I
mod1    =    KEY_I
EndButtonThis part is wrong (same goes for the other parts). The mod keys are only for ctrl, alt, shift, and start. You can fix it by setting mod1 = NONE or removing the mod1 line altogether. Does this fix your problems?

---

### Post by Mack1 on 2007-05-27
hmm not really. in game it works fine most of the time but in konsole for instance (not that im going to be using these mousebuttons inthere) they act like copy-past somehow.

think it has something to do with the fact that x handles a few things itself also.

but i am so happy with the result so far ;-)

if you want translations in dutch or german i can help you aswell btw.

---

### Post by daou on 2007-05-27
Note that pressing the middle mouse button on a terminal (at least gnome-terminal) is the paste command.

Did you check xev to see what key events its sending when you press the buttons? I hope its not a serious issue.

But thanks a lot for helping add support for the G5 and ironing out the initial bugs. Your nickname is now in the SUPPORTED_MICE file ([http://svn.ollisalonen.com/btnx/trunk/SUPPORTED_MICE](http://svn.ollisalonen.com/btnx/trunk/SUPPORTED_MICE)). 
Actually your first post was the catalyst for adding support for multiple mice :D. 

I made a new thread last night in the tutorials and tips section for btnx. Once (and if ;)) it gets approved by the forum staff, all discussion of btnx will be moved there. It's getting a bit off topic in the MX Revolution howto.

Once the btnx thread is up, you can add howto's to the Dutch and German forums based on it if you want.

---

### Post by Mack1 on 2007-05-27
ahh yet another thing i've learned!! thanks.

Glad to have been helpfull. At the moment it's working just fine so i'm all happy :D

Secretly i hope btnx will be implemented in (k)ubuntu gutsy release....living without
those mousebuttons was the one thing holding me back from staying out of windows 95% 
of the time!

If you need me to do anything for you in the future just pm me.

yay!

;)

---

### Post by daou on 2007-05-27
btnx now supports VX Revolution. Got hold of a friend's VX and did the hexdumping.

Also a bug-fix in 0.2.3: pressing some buttons while moving the mouse resulted in the loss of those events. This was the case for MX's wheel left and right tilts. Not a problem anymore.

---

### Post by Mack1 on 2007-05-27
i've updated to 0.2.3 and everything works just fine.

you got my vote to get btnx in kubuntu gutsy as a standard once it comes out :-)

---

### Post by Bedpan.ca on 2007-05-27
I just bought an MX Revolution today, and I can't seem to get btnx to make any difference whatsoever... 
Maybe I'm doing something wrong...?

---

### Post by daou on 2007-05-28
All discussion relating to btnx has been moved to the [btnx thread]("http://ubuntuforums.org/showthread.php?p=2727025").

My replies to the posts above can be found there.

---

