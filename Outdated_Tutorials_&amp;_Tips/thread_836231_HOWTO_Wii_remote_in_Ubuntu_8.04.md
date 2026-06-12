---
title: "HOWTO: Wii remote in Ubuntu 8.04"
date: 2008-06-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Rhubarb on 2008-06-21
[CENTER][SIZE="5"]**HOWTO: Wii remote in Ubuntu 8.04**[/SIZE][/CENTER]


[SIZE="4"]**Introduction:-**[/SIZE]

This howto should help you get a Wii remote working as a mouse / keyboard / joystick in 32bit or 64bit Ubuntu Hardy Heron 8.04
There is no compiling required, you only need to download a few packages, and configure a few text files.

I'd like to thank leffect for posting [http://ubuntuforums.org/showthread.php?t=535659](http://ubuntuforums.org/showthread.php?t=535659) and all the contributors too.
I'd also like to thank Cyborg_572 for clearing up a mouseemu related bug that used to effect this howto.
Hopefully I'll update [https://help.ubuntu.com/community/CWiiD](https://help.ubuntu.com/community/CWiiD) to reflect this howto as well.

Your computer must have a known working bluetooth adapter, a Wii remote.
An infra-red light source is required if you wish to use your Wii remote to behave like a mouse from an IR light source, such as the Wii sensor bar, some candles, an incandescent light, etc.
An IR LED pen is required if you wish to setup a whiteboard with your Wii remote.

For the Ubuntu Intrepid Ibex 8.10 Wii remote guide, follow the following link:
[http://ubuntuforums.org/showthread.php?t=993376](http://ubuntuforums.org/showthread.php?t=993376)


[SIZE="4"]**Install Packages:-**[/SIZE]
Bring up a terminal (Applications --> Accessories --> Terminal), and install these packages:
```
sudo aptitude install wminput wmgui lswm
```

Now we need to find the bluetooth device address of your Wii remote, this will allow you to connect to your Wii remote faster in future, and will let you know if your system can connect to your Wii remote via bluetooth.
Press buttons 1 + 2 on your Wii remote
Then in a terminal, type in:
```
lswm
```
If you don't see something that looks like 00:1F:32:95:EF:B0 then keep on running lswm / pressing buttons 1 + 2 on your Wii remote until you do.
Please note down the number that lswm returns (that looks similar to 00:1F:32:95:EF:B0), this is your Wii remote bluetooth device address.


[SIZE="4"]**Check to see if all the capabilities of your Wii Remote (and extra controllers) work:-**[/SIZE]
Start up wmgui, Applications --> Accessories --> Wmgui
wmgui is an easy application that's good to use for simple diagnostics.


[SIZE="4"]**Allow your Wii remote to be a keyboard / mouse / joystick:-**[/SIZE]
Unless you want to run **sudo modprobe uinput** every time you start Ubuntu, it's recommend you make it automatically run upon Ubuntu start up.
```
gksudo gedit /etc/modules
```
Add this line at the end of the file:
```
uinput
```
So the whole file should look exactly like this:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
uinput
```
You may restart your computer for the settings to take effect, or if you're impatient and want to play with your Wii remote now (without having to restart your computer) you can run this:
```
sudo modprobe uinput
```


[SIZE="4"]**Using your Wii remote as a mouse using acceleration data:-**[/SIZE]
If you want to use your Wii remote as a mouse by tilting your Wii remote, then press buttons 1 + 2 on your Wii remote and from a terminal run this:
```
wminput 00:1F:32:95:EF:B0
```
Please use your bluetooth device address for your Wii remote.


[SIZE="4"]**Using your Wii remote as a mouse using an Infra-red light source:-**[/SIZE]
There's a configuration file that you must first edit before this is possible.
From a terminal, type this in:
```
gksudo gedit /etc/cwiid/wminput/ir_ptr
```
Find these lines:
```
Plugin.ir_ptr.X	= ~ABS_X
Plugin.ir_ptr.Y	= ~ABS_Y
```
and replace it with:
```
Plugin.ir_ptr.X	= ABS_X
Plugin.ir_ptr.Y	= ABS_Y
```

To get your Wii remote to track IR light sources, press buttons 1 + 2 on your Wii remote and from a terminal run this:
```
wminput -c ir_ptr 00:1F:32:95:EF:B0
```
Please use your bluetooth device address for your Wii remote.


[SIZE="4"]**Swapping default left and right mouse buttons:-**[/SIZE]
If you prefer the left mouse button to be button B (the trigger) on your Wii remote, and the right mouse button to be button A on your Wii remote, then from a terminal run this:
```
gksudo gedit /etc/cwiid/wminput/buttons
```
Find these lines:
```
Wiimote.A		= BTN_LEFT
Wiimote.B		= BTN_RIGHT
```
and replace it with:
```
Wiimote.A		= BTN_RIGHT
Wiimote.B		= BTN_LEFT
```

[SIZE="4"][B]
Using your Wii remote and IR LED pen as a whiteboard:-[/B][/SIZE]
If you wish to use your Wii remote and an IR LED pen to make up a cheap touch screen / interactive whiteboard, then download and install the appropriate package from here:
[http://code.google.com/p/linux-whiteboard/downloads/list](http://code.google.com/p/linux-whiteboard/downloads/list)
Once installed, you can find the Wiimote Whiteboard application in Applications --> Accessories --> Wiimote Whiteboard.


[SIZE="4"]**Using your Wii remote for watching DVDs, Elisa media center, etc:-**[/SIZE]
I've setup on my system 2 icons in my gnome panel that I can click on if I want to connect to my Wii Remote and use it's IR light tracking ability as a mouse, and the other to turn off the wminput daemon that I started on the other icon.
Right click on an empty part of the Gnome panel and select "Add to Panel...", then "Custom Application Launcher" then press the "+Add" button
Type in a name for it, for the command, use this:
```
wminput -d -c ir_ptr 00:1F:32:95:EF:B0
```
Select a nice icon for it if you wish, then press close.
To create another icon to kill all running wminput processes, do the same as above, but for the command use this:
```
killall wminput
```

The advantage of using these two icons to run wminput, is that you can turn off your Wii remote (by pressing and holding the power button on your Wii remote) when you start watching a DVD / listening to music to save battery power, then if you wish to start using your Wii remote again, simply press buttons 1 + 2 on your Wii remote and Ubuntu will automatically connect to your Wii remote again as before without having to pick up a keyboard or mouse to do so.
I have attached two icons to this post that I have created myself that you may use for this.


[SIZE="4"]**Remapping the buttons / axis on your Wii remote / classic controller / nunchuck:-**[/SIZE]
All the files you would want to change and experiment with are located in /etc/cwiid/wminput/
A list of all possible axis / keyboard / mouse / joystick / gamepad / steering wheel buttons you can bind your Wiimote to: [http://abstrakraft.org/cwiid/browser/trunk/wminput/action_enum.txt](http://abstrakraft.org/cwiid/browser/trunk/wminput/action_enum.txt)


If I've left anything out let me know, I'll endeavor to keep this updated.

***Updated 24-Jun-2008:** Cyborg_572 has found that mouseemu isn't required which fixes up a bug that did affect this howto.
***Updated 6-Aug-2008:** leffect has kindly donated the icons attached for us all to use and share - under a "Creative Commons Attribution-Share Alike" license, which essentially means you can use them wherever you like, but if you do, or you change them, let other people have them too.
***Updated 29-Nov-2008:** Added link to Toshibawarrior's Ubuntu 8.10 Wii remote guide.
***Updated 30-Nov-2008:** Changed the auto startup line for the uinput module from /etc/rc.local to a much more appropriate place for modules in /etc/modules

---

### Post by Toshibawarrior on 2008-06-22
Rhubarb you are my hero! Thanks so much for this How-To...I read it and it seems to be easy enough...I just have two little questions before tampering with my Wiimote and my "current flawlessly working keyboard+mouse configuration"...

If I download all these packages and make these configurations...will my Wiimote still work on my Wii?...I know the configs are on Ubuntu, and the Wiimote is not supposed to be changed in any way, but I want to make 100% sure...

And, if I follow this How-To, will my keyboard+mouse combo will suffer any changes, other than the specified on your How-To (the one about the mouse dying when you type on the keyboard)? (BTW I have an integrated touchpad on my laptop (as all of them do, and an external USB wireless mouse...will they be changed?...or it's configs?)

Thank you so much for this! :popcorn::)

I also posted this message on the old Wiimote thread...;)

BTW this How-To is great, very complete and easy-to-follow...;)Keep up the good work;)!

---

### Post by heddleston on 2008-06-22
you, good sir, are phenomenal. thank you. ill be doing this tonight after work!

---

### Post by TrashmanL on 2008-06-22
> **Rhubarb said:**
> 
All the files you would want to change and experiment with are located in /etc/cwiid/wminput/
A list of all possible axis / keyboard / mouse / joystick / gamepad / steering wheel buttons you can bind your Wiimote to: [http://abstrakraft.org/cwiid/browser/trunk/wminput/action_enum.txt](http://abstrakraft.org/cwiid/browser/trunk/wminput/action_enum.txt)


I followed the steps and got my Wii remote working. I tested it with WMgui and all buttons worked fine. However, when I edit /etc/cwiid/wminput/buttons and I used the list from the URL above to try an remap the buttons, nothing worked! It seems only BTN_RIGHT, BTN_LEFT and REL_X and REL_Y work. I can map any Wii button to BTN_RIGHT or BTN_LEFT, but nothing else works (Including the the keys that are in the default buttons file). What could be wrong?

---

### Post by TrashmanL on 2008-06-22
> **Rhubarb said:**
> 

The advantage of using these two icons to run wminput, is that you can turn off your Wii remote (by pressing and holding the power button on your Wii remote) when you start watching a DVD / listening to music to save battery power, then if you wish to start using your Wii remote again, simply press buttons 1 + 2 on your Wii remote and Ubuntu will automatically connect to your Wii remote again as before without having to pick up a keyboard or mouse to do so.
I have attached two icons to this post that I have created myself that you may use for this.




OK, I made the two icons and put them on the panel. I can click on the green icon and my remote connects, then click on the red and it disconnects. 

The way you worded this part makes it seem like this will magically make Ubuntu automatically connect if I press 1+2 and disconnect if I press the power button. I didn't think this would happen, and it didn't. Is there a way (i.e. something else I have to do) to get Ubuntu to automatically recognize these button presses?

---

### Post by TrashmanL on 2008-06-22
Answered my own questions on automatically disconnect/reconnect. The -d option makes it stay in memory so you can connect/disconnect. Aha!

I still can't get all the button maps to work, though.

---

### Post by TrashmanL on 2008-06-22
Sorry for so many posts... I'm having fun with this tonight. I just found out, it's not necessary to specify your bluetooth address. wminput will use hci_inquiry to find an active bluetooth device and pick the first one. My panel button is now simply wminput -d and it works fine.

---

### Post by Rhubarb on 2008-06-22
**Toshibawarrior:** Your Wiimote should still work on your Wii just fine.
While I don't own a Wii myself, I could possibly be wrong here - but I have not heard of anyone having problems with using their wiimote on Ubuntu and their Wii.
Your keyboard+mouse combo will not suffer any changes (you must fix up the bug I described in my howto).  I have tested this on 3 different Ubuntu 8.04 computers - 2 64bit Desktops and 1 32bit Laptop.  Everything works fine.

**TrashmanL:** True it's not necessary to specify your bluetooth address, but it does allow Ubuntu to connect to your wiimote a lot faster.
[COLOR="Red"]Thanks for pointing out the problem with binding buttons using **wminput** / **wminput -c acc_ptr**.  I didn't realise that there's a bug with this.
Binding different buttons does work fine when you use: **wminput -c ir_ptr** or **wminput -c buttons**
I will experiment a bit and update my howto accordingly.[/COLOR]

***Updated 6-Aug-2008:** Attached are my original icons you may all use, they are under a "Creative Commons Attribution-Share Alike" license, which essentially means you can use them wherever you like, but if you do, or you change them, let other people have them too.

---

### Post by TrashmanL on 2008-06-23
My last post of the night, I swear...

Confirmed. Just some more info to narrow down. The buttons did map correctly with ir_ptr and buttons used directly. Not only did acc_ptr not work, but nunchuk_acc_ptr did not work, either. As a test, I tried to put 

Plugin.acc.X	= REL_X
Plugin.acc.Y	= REL_Y

in buttons directly. wminput -c buttons no longer worked to remap the buttons. This tells me the bug happens whenever REL_X and/or REL_Y are called (as opposed to being in the include statement - but I suppose that was obvious in that ir_ptr worked).

You probably already though of this, but just in case you didn't, I figured I'd share my observations.

---

### Post by Rhubarb on 2008-06-23
[COLOR="Red"]I've come to a similar conclusion TrashmanL.
It seems to me whenever **REL_X** or **REL_Y** is called it becomes impossible to map keyboard buttons to other wiimote buttons.

Interestingly this functions exactly like a joystick (it appears as a joystick and works in google earth), and the buttons work fine:
```
Plugin.acc.X	= ABS_X
Plugin.acc.Y	= ABS_Y
```

When you include mouse buttons, rather than just behaving as a joystick, it actually behaves as a joystick and a mouse simultaneously (the buttons work fine here too):
```
Plugin.acc.X	= ABS_X
Plugin.acc.Y	= ABS_Y
Wiimote.B	= BTN_LEFT
```

But when ever you call **REL_**X or **REL_Y**, only mouse buttons can be bound, no extra keyboard bindings can be made:
```
Plugin.acc.X	= REL_X
Plugin.acc.Y	= REL_Y
```

A little clue of why this happens is found here:
[http://abstrakraft.org/cwiid/wiki/wminput](http://abstrakraft.org/cwiid/wiki/wminput)
> An event device is always created. A mouse device is created if REL_X, REL_Y, and BTN_LEFT symbols are mapped (~ABS_X and ~ABS_Y effectively map REL_X and REL_Y, respectively). A joystick device is created if ABS_X is mapped.

So it seems when a mouse device is created the buttons don't work, and when a joystick device is created (even though it can control the mouse cursor - I'm a bit confused here) the buttons do work.

This possibly can be proven by (I'm a bit confused here)
```
Plugin.acc.X	= ~ABS_X
Plugin.acc.Y	= ~ABS_Y
```
Using the above configuration, I was unable to move the mouse pointer (it doesn't fuction as a joystick either), none of the buttons worked except for the buttons I bound to left and right mouse click.


I haven't compiled the latest development version CWiid to test any further.

If anyone here knows how to fix this bug please let me know.[/COLOR]

---

### Post by Toshibawarrior on 2008-06-23
So which of the above configurations you mentioned works good? the ABS_X/Y one?...

I still haven't got the time to play with this, but I will later on today...I don't know if I might encounter problems...

Anyways, thanks for your replies, and I hope someone can explain to me what's the difference between REL_X/Y and ABS_X/Y...:)

---

### Post by Rhubarb on 2008-06-23
[COLOR="Red"]> **Toshibawarrior said:**
> So which of the above configurations you mentioned works good? the ABS_X/Y one?

ABS_X/Y is used in ir_ptr (infra red tracking) as well as joystick, everything works perfectly here.

REL_X/Y is used in acceleration data from your Wii remote (tilt your Wii remote and your mouse cursor will move too), this is the one where you are unable to bind keyboard keys to your Wii remote - only mouse buttons can be bound to your Wii remote in this case.[/COLOR]

---

### Post by Toshibawarrior on 2008-06-23
Oh, I get it now...I'm gonna start playing with this right now. I'll let you know how it turns out.

Just in case it doesn't work, is there a way to uninstall this packages and dependencies without damaging other configurations?...like using:

sudo aptitude remove cwiid....?or something along these lines?...;)

---

### Post by Toshibawarrior on 2008-06-23
YEAH! It's working! I still have to tamper with button mapping, but at least the "WiiMote as a mouse" thing works...a little shaky though. I'm gonna map some buttons to see how it goes! ;):p

---

### Post by Toshibawarrior on 2008-06-23
OK, this will sound extremely stupid...but I did it! And when I saw my WiiMote acting as a multimedia pc remote (for moving between songs, next, prev, play/pause, etc...) a tear came out of my eye...I'm so freaking amazed at how many things Ubuntu can do...

I deeply thank you for all your help Rhubarb...I'll keep playing with my WiiMote's settings to see if I can find anything about the key binding problems...

i just have one last question (I'm very new to this, I was on the DarkSide of Windows for over 10 years)...How can I make my Nunchuk's joystick work?...the C and Z buttons work great, but they joystick is dead...I tried to modify the /etc/cwiid/wminput/nunchuk_acc_ptr, but nothing works...

If anyone can help me, please do! ;):p:)

---

### Post by paulderol on 2008-06-23
okay, this all looks good, and i'm in. can i bind the zoom functions to the up/down axis on the d-pad either in the wiimote setup or in the zoom configuration? and you did confirm that doing this does nothing internally to the wiimote, correct?

gonna try it out later today...

---

### Post by Toshibawarrior on 2008-06-23
paulderol, it does not chang anything on the wiimote, I confirmed it myself. However, as for the zoom functions, you should check [here]("http://abstrakraft.org/cwiid/browser...ction_enum.txt")...it has tons of button/key bindings, and you might find your zoom options there. Check it out and us know.

Don't worry about your wiimote, he'll be fine! ;)

---

### Post by Toshibawarrior on 2008-06-23
Ok, so I keep messing around with my wiimote, and I wanted to know...Does the nunchuk has cursor movement in CwiiD?...Whenever i have it plugged into the wiimote the cursor shakes a little bit...sometimes a lot. And I wanted to know if the nunchuk has cursor control via IR like the wiimote? if it does, please let me know how to disable it...;)...

I still can't find how to make the nunchuk's joystick work...

And btw, I'm sorry for so many consecutive posts...:(

---

### Post by paulderol on 2008-06-23
i think the nunchuck produces some accelerometer information, does it not? wouldn't that then be pushed through as extraneous mouse inputs that X is having difficulty translating? 

and thanks for the link, that looks like it'll do me just fine, now it's just for stealing a wiimote from a friend to try it out.

---

### Post by Toshibawarrior on 2008-06-23
Well I've been toying with the nunchuk's configurations, and it does produce accelerometer info/data, I still don't know how deactivate it...I needed the Z and C buttons for using CTRL and ALT to activate the Compiz Cube...but everytime I point both the wiimote and the nunchuk at the sensor bar, the cursor goes berserk with shaking...

I hope there's a workaround to this. 

And as far as I've read, the nunchuk's joystick is not recognized by CWiiD...as it doesn't show anywhere on the wminput files...the only joysticks there are the ones on the classic controller...:(...

---

### Post by Cyborg_572 on 2008-06-23
Instead of installing mousemu, I use the command "sudo modprobe uinput" before running wminput for the first time after a reboot. It seems to work. Also using this, the buttons seem to be mapping to keyboard buttons using the accelerometer as a pointer. I haven't edited any configuration files since intalling the packages originally.

---

### Post by Toshibawarrior on 2008-06-23
Now that Cyborg mentions that...I can actually use my - and + buttons to go to the previous and/or next song, the Home button as Play/Pause, 1 and 2 for volume up and down, and so on, while my wiimote acts as a pointer by using the ABS_X and ABS_Y options on /etc/cwiid/wminput/ir_ptr... I did it following this how-to...weird...I can map any button or key and still use the wiimote's pointer to control the mouse cursor...:confused::confused::confused:

Did it work like that to anyone else?...Or is it just the way it's supposed to work and I'm stupid?.........8-[:-s8-[

---

### Post by Cyborg_572 on 2008-06-23
Toshibawarrior: That's what people have been saying. Keyboard mappings work fine using ABS_X, and don't work when using REL_X.
I have them working with both though, and the only difference between my setup and the one described here is using "sudo modprobe uinput" instead of installing mousemu, as far as I can tell

---

### Post by Toshibawarrior on 2008-06-23
Oh, ok, sorry about that. I guess I'm just stupid then. Anyways, I didn't even tried using the REL_X/Y thing...I went straight to ABS_X/Y...

For a minute there I thought that no key/button mappings worked while using the wiimote as a mouse...I guess they were just talking about the REL thing...sorry...:(

I feel stupid...I'm just a noob at Linux, and let alone using wiimotes as mouses...](*,) ...but I guess you guys noticed this already...:(

Anyways...I hope I can get the hang of this...I used to be one of the best "technicians" among my friends for Windows...what a waste of my life...now that I've seen the light, I'm never ever going back. So I'm back at learning the basics from the ground up...

---

### Post by TrashmanL on 2008-06-23
OK. Lots of things to go over. I'm having a hard time keep track of who's who, so if the "you" applies to you, then it means you. If it doesn't, then that you is not you. :lol:

What are you using as an infrared source when using ir_ptr? Short of turning my Wii on and using its bar, I don't have one. I've tried using an incandescent light bulb as suggested, but it didn't work for me.

This is why I'm stuck using acc_ptr. 
The difference between ABS and REL is this. When using the IR pointer, ABS works, because where you point it determines the actual mouse POSITION (the absolute position). When using the acceleration data, however, you need to use REL (relative position) because the way you tilt the WiiMote will determine where the mouse MOVES relative to its current position. If I was to use ABS with acc_ptr, I'd have to keep moving the WiiMote to keep it in a certain position, or else it would jump to a corner or the center. Thus, I HAVE to use REL or it would be near impossible to control the mouse.

Again, if you can use IR and therefore the ABS fucntions, you can map all buttons. However, if you cannot, like me, and need to use REL functions, an apparent bug makes it impossible to map keyboard functions to the other buttons.

On to the other issue, the nunchuk joystick. There are commands for using it, but they're hidden. I think they're hidden because they don't work yet. If you open the file /usr/share/doc/wminput/wminput.list it has the list of available commands. This is identical to the options found in the config files, with two additional commands.

Nunchuk.Stick.X
Nunchuk.Stick.Y

However, if I try to set these to either set (ABS or REL), my mouse pointer immediately jumps to the lower right hand corner of my screen and I can no longer move it away from there.

This tells me that nunchuk joystick functions are in the works, but not yet functional.

As far as nunchuk/IR stuff. The nunchuk uses no IR at all. Only acceleration data, which is purely how you hold the nunchuk. So yes, it does have cursor movement, but no, it's not based on IR. That being said, I'm somewhat surprised it would cause your cursor to move, as I thought you'd have to use wminput -c nunchuk_acc_ptr for it to affect your mouse.

I would also suggest using the WMGUI utility to test your nunchuk. Run it, go to the "settings" menu, then select extension data. This will then activate the "Nunchuk" section, and you can move your nunchuk around and see how the data changes. You can also see the difference between it and the "IR" section.

---

### Post by Rhubarb on 2008-06-24
> **paulderol said:**
> ... can i bind the zoom functions to the up/down axis on the d-pad either in the wiimote setup or in the zoom configuration? and you did confirm that doing this does nothing internally to the wiimote, correct?

It changes nothing in your wiimote, - go and have some fun with it in Ubuntu now!

To make your wiimote zoom in / zoom out:
```
gedit /etc/cwiid/wminput/buttons
```
Then change the keybindings for Wiimote.Up and Down to look like this:
```
Wiimote.Up	= KEY_F6
Wiimote.Down	= KEY_F7
```
By doing this, you've bound F6 and F7 to your up and down buttons on your wiimote.
Then it's just a matter of going into Compiz Config Settings Manager
(**sudo aptitude install compizconfig-settings-manager** if you haven't already got it installed) and binding F6 and F7 to zoom in and zoom out.

---

### Post by Rhubarb on 2008-06-24
I have updated the howto to reflect Cyborg_572's wonderful help in resolving the problem of not being able to bind keyboard keys to your wiimote while using REL_X and REL_Y accelerometer input.

For those who followed my howto before 24th June 2008 and have this problem, this can be easily resolved:


Get rid of mouseemu, this is the cause of the problem:
```
sudo aptitude remove mouseemu
```
When prompted respond with **y** to remove the mouseemu package (there may be another library that mouseemu used, just press **y** and it might remove this extra library too).
Alternatively you can just go into Synaptic package manager and remove the **mouseemu** package that way.


Unless you want to run **sudo modprobe uinput** every time you start Ubuntu, it's recommend you make it automatically run upon Ubuntu start up.
```
gksudo gedit /etc/rc.local
```
Insert this line before **exit 0**:
```
modprobe uinput
```
So the whole file should look exactly like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

modprobe uinput

exit 0
```
You may restart your computer for the settings to take effect, or if you're impatient and want to play with your Wii remote now (without having to restart your computer) you can run this:
```
sudo modprobe uinput
```


Now you should have full functionality of you wiimote no matter what tracking mode it's in.  :D

---

### Post by Toshibawarrior on 2008-06-24
> **Rhubarb said:**
> I have updated the howto to reflect Cyborg_572's wonderful help in resolving the problem of not being able to bind keyboard keys to your wiimote while using REL_X and REL_Y accelerometer input.

For those who followed my howto before 24th June 2008 and have this problem, this can be easily resolved:


Get rid of mouseemu, this is the cause of the problem:
```
sudo aptitude remove mouseemu
```
When prompted respond with **y** to remove the mouseemu package (there may be another library that mouseemu used, just press **y** and it might remove this extra library too).
Alternatively you can just go into Synaptic package manager and remove the **mouseemu** package that way.


Unless you want to run **sudo modprobe uinput** every time you start Ubuntu, it's recommend you make it automatically run upon Ubuntu start up.
```
gksudo gedit /etc/rc.local
```
Insert this line before **exit 0**:
```
modprobe uinput
```
So the whole file should look exactly like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

modprobe uinput

exit 0
```
You may restart your computer for the settings to take effect, or if you're impatient and want to play with your Wii remote now (without having to restart your computer) you can run this:
```
sudo modprobe uinput
```


Now you should have full functionality of you wiimote no matter what tracking mode it's in.  :D

:)GREAT!...I re-read everything and now i get it...I'm sorry to ask obvious or already answered questions...

As for me, I'll keep using the ABS (IR tracking)...since I don't what difference there is between ABS and REL...(I believe REL doesn't use IR? I'm on the dark on this).

Anyways, ABS has worked for me, and I have my wiimote running smoothly...with a Nyko wireless sensor-bar...not the one connected to the Wii.

So if anyone can tell me the advantages of REL please do. ;) If I'm not mistaken REL uses the wiimote as a joystick, without IR ... but I may be wrong...Rhubarb is the one who can actually throw some light my way on this.

---

### Post by Toshibawarrior on 2008-06-24
If I use the uinput thing on the script...will my two icons (turning wminput on and off like you said on your how-to) still work? Or will i have to change something else on the icons' config?...

I know that I'll need to add the uinput thing to the startup processes and stuff, but is there something else?...:popcorn:

---

### Post by Rhubarb on 2008-06-24
> **Toshibawarrior said:**
> If I use the uinput thing on the script...will my two icons (turning wminput on and off like you said on your how-to) still work? Or will i have to change something else on the icons' config?...
I know that I'll need to add the uinput thing to the startup processes and stuff, but is there something else?...:popcorn:
Yes, everything will still work perfectly (well, actually even better than before if you where using REL_X/Y), and there's nothing more to do to make it work.

The REL_X/Y is good if you don't have a sensor bar / IR source.  Basically, just tilt your wiimote and the cursor goes in that direction (REL_X/Y can really only be used with accelerometers only - no IR, but as stated in my last sentance here, it's possible to use ABS_X/Y with the accelerometers).
Just try it yourself by running:
```
wminput
```

If you're feeling a little adventurous, it's possible to use ABS_X/Y with the accelerometers - this way your mouse cursor centres in the middle of the screen when your wiimote is horizontal.

---

### Post by Toshibawarrior on 2008-06-24
Ah, i see. So if i take mouseemu out, I'll still be able to use the ABS setting?...

I'm gonna start playing with the REL setting now...I'll let you know...

---

### Post by Toshibawarrior on 2008-06-24
Ok, so I added sudo modprobe uinput to the sessions startup processes manager...and it does nothing...

If I run it from a terminal it does nothing also!...It's not working for me...did I do something wrong?

Edit: all the buttons work...however the cursor remains still...no movement at all...

I changed BS to REL on /etc/cwiid/wminput/ir_ptr...was that it?

---

### Post by Cyborg_572 on 2008-06-24
> **Toshibawarrior said:**
> Ok, so I added sudo modprobe uinput to the sessions startup processes manager...and it does nothing...

If I run it from a terminal it does nothing also!...It's not working for me...did I do something wrong?

Edit: all the buttons work...however the cursor remains still...no movement at all...

I changed BS to REL on /etc/cwiid/wminput/ir_ptr...was that it?
sudo modprobe uinput doesn't give any output back to the console. If you removed mousemu, and the wii remote is working in any way at all, then sudo modprobe uinput is working. 

if you're using ir_ptr, it should be ABS if you're using acc_ptr, it should be REL

---

### Post by Rhubarb on 2008-06-24
> **Toshibawarrior said:**
> Ok, so I added sudo modprobe uinput to the sessions startup processes manager...and it does nothing...

If I run it from a terminal it does nothing also!...It's not working for me...did I do something wrong?

Edit: all the buttons work...however the cursor remains still...no movement at all...

I changed BS to REL on /etc/cwiid/wminput/ir_ptr...was that it?
Ok, well, when you run sudo modprobe uinput, getting nothing back is exactly what you want.  - It shows that it's working fine with no errors.

The next problem I see you've done is to edit the ir_ptr file.  Please leave this file alone.  For reference it should look like this:
```
#ir_ptr

include buttons

Plugin.ir_ptr.X	= ABS_X
Plugin.ir_ptr.Y	= ABS_Y
```

If you wish to try out the accelerometer mouse pointer use for the wiimote, **TYPE THIS IN**:
```
wminput
```
When running **wminput** by itself, it by default runs:
wminput -c default
and default is actually a link to acc_ptr (which if you read the contents of acc_ptr, it uses REL_X/Y)

Here is what acc_ptr looks like:
```
#acc_ptr

include buttons

Plugin.acc.X	= REL_X
Plugin.acc.Y	= REL_Y
```
You'll notice that in acc_ptr it references Plugin.**acc**.X
where as ir_ptr references Plugin.**ir_ptr**.X
This is the main difference between IR and acceleration tracking.
The REL_X/Y is different to ABS_X/Y because REL = relative tracking (similar to a mouse), and ABS = absolute tracking (similar to a joystick).

If you want to experiment, it'd be best to create your own file, ie test, and put it in /etc/cwiid/wminput/
Then to run it, just run: wminput -c test


> **Cyborg_572 said:**
> if you're using ir_ptr, it should be ABS if you're using acc_ptr, it should be REL
It is also possible to use ABS when using acc_ptr too - though it's nothing too useful.

---

### Post by Toshibawarrior on 2008-06-24
SUCCESS!!! REL works over here...kinda hard to control it that way. I think i might stick to this setup because that way I can economize the sensor bar's batteries for when they're really needed. It's great though!

;) Thanks for all you help! Keep this thread alive! :p

---

### Post by Rhubarb on 2008-06-24
> **Toshibawarrior said:**
> SUCCESS!!! REL works over here...kinda hard to control it that way...
Yes it is a little hard to control, but when you've got no sources of IR light it's the next best option to use.

You may prefer holding the wiimote in both hands sideways.
Edit your acc_ptr file so it looks like this and try it out:
```
#acc_ptr

include buttons

Plugin.acc.X	= REL_Y
Plugin.acc.Y	= REL_X
```
**note:** I've changed the X and Y axis around.

---

### Post by TrashmanL on 2008-06-24
Woo-hoo! It works! Completely and totally now. Sorry I overlooked your post, Cyborg! It may be my imagination, but it even seems like it's a little easier to move the pointer now, too.

---

### Post by TrashmanL on 2008-06-24
I'll just note that the modprobe fix did not fix the Nunchuk.stick settings.

---

### Post by TrashmanL on 2008-06-24
I don't know what's wrong with me. Now that I can use my WiiMote on my laptop, I've gone mad crazy with power. Anyway, I found another "bug" or perhaps this was on purpose. I made a file with the following lines in it:

Plugin.nunchuk_acc.X	= REL_HWHEEL
Plugin.nunchuk_acc.Y	= REL_WHEEL

Plugin.acc.X	= REL_X
Plugin.acc.Y	= REL_Y

The idea is, that I'd use my WiiMote as a pointer and the nunchuk to scroll. Unfortunately, you can't use both Plugin.nunchuk_acc AND Plugin.acc Apparently, Plugin.acc is dominant, as no matter what order I put it in, that works and the nunchuk doesn't.

This seems like a horrible idea, I suppose. And indeed, when I only had REL_HWHEEL AND REL_WHEEL alone and working, my screen went crazy, 'cause the slightest movement in my nunchuk switched desktops on me. My idea is, ideally, when this is developed more, there'd be more tweaks you could do, such as setting thresholds. It would only scroll when you tilted it at least so far. Then it could be used for a lot of different things.

---

### Post by Rhubarb on 2008-06-24
I don't have a nunchuck here (only a wiimote and a classic controller), but there are a few tricks that you might be able to do to get scrolling working a bit nicer:


You can bind scrolling to your wiimote's D-Pad (or maybe the joystick on your nunchuck):
```
Wiimote.Dpad.X = REL_HWHEEL
Wiimote.Dpad.Y = REL_WHEEL
```
You'll notice here that you can't press and hold down on the D-Pad to scroll, you have to press it repetitively.


If you want to increase the dead zone so you don't start scrolling at the slightest movement:
```
Plugin.acc.X	= REL_HWHEEL
Plugin.acc.Y	= REL_WHEEL
Plugin.acc.X_Scale = 0.3
Plugin.acc.Y_Scale = 0.3
```
As you'll find out by doing the above, it still scrolls very fast indeed.  - But the dead zone is increased, so it's not quite as bad.


If you wish to use your wiimote as an ABS joystick:
```
Wiimote.A	= BTN_THUMB
Wiimote.B	= BTN_TRIGGER
Plugin.acc.Roll		= ABS_X
Plugin.acc.Roll_Scale	= 2.0
Plugin.acc.Pitch	= -ABS_Y
Plugin.acc.Pitch_Scale	= 2.0
```
If you have mouse buttons bound then it will also control your mouse cursor.  If you have no mouse buttons bound (and use keyboard / joystick buttons only), then it will appear to Ubuntu as being a joystick that works in google earth / other apps that want joysticks.

---

### Post by paulderol on 2008-06-25
as it turns out, you can map the +/- buttons directly to zoom in/out!

oh yeah, this is sweet indeed.

a question--

is anyone else having small issues with ir tracking? as in, i'm  getting a weird effect wherein the pointer won't move all the way to the corners of the screen at all times, is this because the ir lights aren't set up as well as they should be or is it an issue with tracking it at varying levels of sensitivity and speed? i may just switch to accellerometer input, as it is a little more forgiving of my twitchy hands, but yeah, either way, everybody here is awesome, and this thing rules.

---

### Post by TrashmanL on 2008-06-25
Thanks again, Rhubarb. I was unaware of the Pitch/Roll and Scale settings. I'll have to play around with those now. What documentation can those be found in?

I do wish that in increasing the dead zone, the scroll speed could be slowed down, too.

---

### Post by Nxion on 2008-06-26
This might seem like a stupid question but how does the Wiimote  work with a machine, IR?, Bluetooth?.

---

### Post by Rhubarb on 2008-06-27
> **Nxion said:**
> This might seem like a stupid question but how does the Wiimote  work with a machine, IR?, Bluetooth?.
The wiimote communicates to your machine via Bluetooth.


paulderol:-
> i'm getting a weird effect wherein the pointer won't move all the way to the corners of the screen at all times
The IR tracking in your wiimote can only report back what it sees.
The wiimote has a 45° field of view.
If it can't track to the corners of your screen, then you may need to place more IR lights around where you'll point your wiimote in.
When in IR tracking mode, it ONLY tracks via IR, there is no accelerometer input at all.
Another common problem is if your IR sources are too bright / too many reflective surfaces around.  Remember your wiimote can only track 4 sources of IR at a time.
If you want to see what your wiimote can see, Applications --> Accessories --> Wmgui, connect to your wiimote, then Settings --> IR Data
For good tracking your wiimote should be always able to see at minimum one (maximum of 4) clear IR spot(s) at a time for where ever you want to be able to swing your wiimote around in.


TrashmanL:-
> I was unaware of the Pitch/Roll and Scale settings. I'll have to play around with those now. What documentation can those be found in?
Well to be honest I found the Pitch/Roll settings from here:-
[http://ubuntuforums.org/showpost.php?p=4228575&postcount=98](http://ubuntuforums.org/showpost.php?p=4228575&postcount=98)
(Thanks segalion).  I'm unsure where segalion got that info from.
It might be hidden away somewhere on CWiid's site:
[http://abstrakraft.org/cwiid/](http://abstrakraft.org/cwiid/) (there seems to be a problem with their site atm)

---

### Post by madu on 2008-06-27
Wow.. this is awesome!
Got a few questions.. would be great if somebody can enlighten me.

1) Can I just buy a Wii remote only and get this to work?
2) If I only want Wii remote to function as the mouse, apart from the bluetooth adapter, what else do I need? Why do I need an infrared light source? Can somebody please tell me what this exactly is and what it does and used for?
What is the difference between "Using your Wii remote as a mouse using acceleration data" and "Using your Wii remote as a mouse using an Infra-red light source"..?

Thanks a lot.

Cheers!

---

### Post by drjonze on 2008-06-27
> **madu said:**
> Wow.. this is awesome!
Got a few questions.. would be great if somebody can enlighten me.

1) Can I just buy a Wii remote only and get this to work?
2) If I only want Wii remote to function as the mouse, apart from the bluetooth adapter, what else do I need? Why do I need an infrared light source? Can somebody please tell me what this exactly is and what it does and used for?
What is the difference between "Using your Wii remote as a mouse using acceleration data" and "Using your Wii remote as a mouse using an Infra-red light source"..?

Thanks a lot.

Cheers!

1) Yes, you can just buy a wiimote, you don't need a Wii

2) If you use the wiimote as a mouse with acceleration data, you have to tilt it to to move the cursor around. It uses the motion sensors to work. If you are just doing this, you don't need an infra-red light source. If you want to use your wiimote as a remote control for your computer (its much the same as using it as a mouse) you need the IR light. It uses the light as a point of reference for movement. You can use the sensor that comes with a Wii (or buy a wireless sensor bar, you don't need a Wii with this option, they are about $15) as an IR light or you can actually just use a candle. A flame is an infra red light source.

---

### Post by madu on 2008-06-27
> **drjonze said:**
> 1) Yes, you can just buy a wiimote, you don't need a Wii

2) If you use the wiimote as a mouse with acceleration data, you have to tilt it to to move the cursor around. It uses the motion sensors to work. If you are just doing this, you don't need an infra-red light source. If you want to use your wiimote as a remote control for your computer (its much the same as using it as a mouse) you need the IR light. It uses the light as a point of reference for movement. You can use the sensor that comes with a Wii (or buy a wireless sensor bar, you don't need a Wii with this option, they are about $15) as an IR light or you can actually just use a candle. A flame is an infra red light source.

Thanks a lot drjonze.
I guess I will try this with the accelerator. Using it with tilting should be the fun part :)

Thanks again mate.

---

### Post by Toshibawarrior on 2008-06-27
madu, using your wiimote with acceleration data is fun, but hard to master. On the plus side, you don't ned anything except the Bluetooth adapter and the wii remote. On the other hand, using it with infra-red light sources, makes it easier to handle, but then you'll need to buy an IR LED or Wireless Wii Sensor Bar...:(

Anyways, this is the most fun you'll have while using ubuntu! :):):):p:p:p

Rock on dude!

---

### Post by madu on 2008-06-27
> **Toshibawarrior said:**
> madu, using your wiimote with acceleration data is fun, but hard to master. On the plus side, you don't ned anything except the Bluetooth adapter and the wii remote. On the other hand, using it with infra-red light sources, makes it easier to handle, but then you'll need to buy an IR LED or Wireless Wii Sensor Bar...:(

Anyways, this is the most fun you'll have while using ubuntu! :):):):p:p:p

Rock on dude!

Hey thanks a lot Toshibawarrior!

Is it really hard to control the mouse with the acceleration?
I mean there wont be much fun with I'm just going it as the mouse, will there?

Actually I'm using a Dell laptop and it has an in-built bluetooth adapter. I can check for bluetooth devices with *hidtool scan* and even make a connection with my mobile, but I can't seem to get to transfer files or anything. I was wondering whether I need to check further before buying a Wii-mote.

Can somebody please tell me if using with acceleration is difficult?

Thank you guys.

---

### Post by madu on 2008-06-28
Hi,

I just got a Wiimote and it works!!
man this is really nice! although it cant replace the mouse.. well that wasn't the case anyway.. this is just fun!

BTW, I'm wondering about a couple of things.

If I buy a Wii sensor bar, do I need a seperate light source too?
And what additional advantages do I have with using the Sensor bar over the accelerometer?

One last thing, is there anyway I can log the WMINPUT acceleration data on the console? rather than in the WMGUI?

Thanks a lot guys! this is really awesome!

---

### Post by Toshibawarrior on 2008-06-28
Hey madu, good to know it worked for you. If you buy a Wii Sensor Bar (preferably wireless, since the other one just connects to the Wii) you won't need any more IR light sources...Although some people want to have more than 2 IR (which is basically what the Sensor Bar has, and build their own ones with 4 IR LED (which is the most IR lights the wiimote will recognize at the same time. This is done for the wiimote to have better movement and control. 

Anyways, with 2 IR LEDs (the sensor bar you buy at GameStop, remember to go ireless otherwise you won't have where to connect the sensor bar) is more than enough for most users, like me. 

The pros of using a sensor bar are: you get better handling of the cursor, since it'll work almost like your Wii, no need to tilt or twist the wiimote, just point n' click. And that's basically it...
The cons are: that you'll need to buy batteries for your sensor bar and that you'll need to find a place for it while using it, I use a Toshiba laptop and I found that the best place for the sensor bar is on front of the PC, near the touchpad...

And as for accelerometer mode, it rock...it's a little weird to get used to it, but you'll master it in no time ;)

Anyways, if you have more questions, just let us know...:p:)

---

### Post by madu on 2008-06-28
> **Toshibawarrior said:**
> Hey madu, good to know it worked for you. If you buy a Wii Sensor Bar (preferably wireless, since the other one just connects to the Wii) you won't need any more IR light sources...Although some people want to have more than 2 IR (which is basically what the Sensor Bar has, and build their own ones with 4 IR LED (which is the most IR lights the wiimote will recognize at the same time. This is done for the wiimote to have better movement and control. 

Anyways, with 2 IR LEDs (the sensor bar you buy at GameStop, remember to go ireless otherwise you won't have where to connect the sensor bar) is more than enough for most users, like me. 

The pros of using a sensor bar are: you get better handling of the cursor, since it'll work almost like your Wii, no need to tilt or twist the wiimote, just point n' click. And that's basically it...
The cons are: that you'll need to buy batteries for your sensor bar and that you'll need to find a place for it while using it, I use a Toshiba laptop and I found that the best place for the sensor bar is on front of the PC, near the touchpad...

And as for accelerometer mode, it rock...it's a little weird to get used to it, but you'll master it in no time ;)

Anyways, if you have more questions, just let us know...:p:)

Hey thanks buddy!
had no idea what the sensor bar did.
Are you using the sensor bar for navigation? do you feel much better handling (of the pointer) compared to the accelerator method?
Also how to map the left & right d-pad buttons? and how to map the middle button of the mouse (opening tabs in Firefox) ?

Thanks for the help mate. cheers!

---

### Post by Toshibawarrior on 2008-06-28
Well I'm using the acceleration mode to economize batteries on my sensor bar, but I like the IR mode better...it's easier for me, but i mastered both modes ;):p.

Write this into a terminal:

```
gksudo gedit /etc/cwiid/wminput/buttons

```

and then follow the link that Rhubarb provided to map out the buttons...the link he posted on the How-To has a long list of compatible commands to map on the wiimote's buttons.

Here's the link and the part of the How-To...

> Remapping the buttons / axis on your Wii remote / classic controller / nunchuck:-
All the files you would want to change and experiment with are located in /etc/cwiid/wminput/
A list of all possible axis / keyboard / mouse / joystick / gamepad / steering wheel buttons you can bind your Wiimote to: [http://abstrakraft.org/cwiid/browser...ction_enum.txt](http://abstrakraft.org/cwiid/browser...ction_enum.txt)


---

### Post by madu on 2008-06-28
> **Toshibawarrior said:**
> Well I'm using the acceleration mode to economize batteries on my sensor bar, but I like the IR mode better...it's easier for me, but i mastered both modes ;):p.

Write this into a terminal:

```
gksudo gedit /etc/cwiid/wminput/buttons

```

and then follow the link that Rhubarb provided to map out the buttons...the link he posted on the How-To has a long list of compatible commands to map on the wiimote's buttons.

Here's the link and the part of the How-To...

Thanks for that mate.
I mapped the d_pad X & Y (up & down) buttons. I want to know the mapping names of the Left & Right buttons of the d_pad.

Cheers.

---

### Post by Toshibawarrior on 2008-06-28
Wiimote.Left
Wiimote.Right

Those are the d-pad's left and right names...Hope this helps!:popcorn::)

Here's my /etc/cwiid/wminput/buttons configuration:

```
#buttons

Wiimote.A		= BTN_RIGHT
Wiimote.B		= BTN_LEFT
Wiimote.Up		= KEY_UP
Wiimote.Down	= KEY_DOWN
[B][I]Wiimote.Left	= KEY_LEFT
Wiimote.Right	= KEY_RIGHT[/I][/B]
Wiimote.Minus	= KEY_PREVIOUSSONG
Wiimote.Plus	= KEY_NEXTSONG
Wiimote.Home	= KEY_PLAYPAUSE
Wiimote.1		= KEY_VOLUMEUP
Wiimote.2		= KEY_VOLUMEDOWN

Nunchuk.C		= KEY_LEFTALT
Nunchuk.Z		= KEY_LEFTCTRL

Classic.Up		= KEY_UP
Classic.Down	= KEY_DOWN
Classic.Left	= KEY_LEFT
Classic.Right	= KEY_RIGHT
Classic.Minus	= KEY_BACK
Classic.Plus	= KEY_FORWARD
Classic.Home	= KEY_HOME
Classic.A		= BTN_LEFT
Classic.B		= BTN_RIGHT
#Classic.X		= 
#Classic.Y		= 
#Classic.ZL		= 
#Classic.ZR		= 
#Classic.L		= 
#Classic.R		= 
```

---

### Post by madu on 2008-06-28
> **Toshibawarrior said:**
> Wiimote.Left
Wiimote.Right

Those are the d-pad's left and right names...Hope this helps!:popcorn::)

Here's my /etc/cwiid/wminput/buttons configuration:

```
#buttons

Wiimote.A		= BTN_RIGHT
Wiimote.B		= BTN_LEFT
Wiimote.Up		= KEY_UP
Wiimote.Down	= KEY_DOWN
[B][I]Wiimote.Left	= KEY_LEFT
Wiimote.Right	= KEY_RIGHT[/I][/B]
Wiimote.Minus	= KEY_PREVIOUSSONG
Wiimote.Plus	= KEY_NEXTSONG
Wiimote.Home	= KEY_PLAYPAUSE
Wiimote.1		= KEY_VOLUMEUP
Wiimote.2		= KEY_VOLUMEDOWN

Nunchuk.C		= KEY_LEFTALT
Nunchuk.Z		= KEY_LEFTCTRL

Classic.Up		= KEY_UP
Classic.Down	= KEY_DOWN
Classic.Left	= KEY_LEFT
Classic.Right	= KEY_RIGHT
Classic.Minus	= KEY_BACK
Classic.Plus	= KEY_FORWARD
Classic.Home	= KEY_HOME
Classic.A		= BTN_LEFT
Classic.B		= BTN_RIGHT
#Classic.X		= 
#Classic.Y		= 
#Classic.ZL		= 
#Classic.ZR		= 
#Classic.L		= 
#Classic.R		= 
```

Hey thanks a lot for that ToshibaW.

BTW, how did you find the keys like KEY_VOLUMEUP, KEY_NEXTSONG?
Do you define them somewhere?

Thanks a lot mate.

---

### Post by Nxion on 2008-06-29
So If I wanted to use this as a mouse w/ a IR sensor, will any IR receiver from the store work with it. I tried using it with the acceleration data but it was a little annoying.

---

### Post by madu on 2008-06-29
> **Rhubarb said:**
> I don't have a nunchuck here (only a wiimote and a classic controller), but there are a few tricks that you might be able to do to get scrolling working a bit nicer:


You can bind scrolling to your wiimote's D-Pad (or maybe the joystick on your nunchuck):
```
Wiimote.Dpad.X = REL_HWHEEL
Wiimote.Dpad.Y = REL_WHEEL
```
You'll notice here that you can't press and hold down on the D-Pad to scroll, you have to press it repetitively.


If you want to increase the dead zone so you don't start scrolling at the slightest movement:
```
Plugin.acc.X	= REL_HWHEEL
Plugin.acc.Y	= REL_WHEEL
Plugin.acc.X_Scale = 0.3
Plugin.acc.Y_Scale = 0.3
```
As you'll find out by doing the above, it still scrolls very fast indeed.  - But the dead zone is increased, so it's not quite as bad.


If you wish to use your wiimote as an ABS joystick:
```
Wiimote.A	= BTN_THUMB
Wiimote.B	= BTN_TRIGGER
Plugin.acc.Roll		= ABS_X
Plugin.acc.Roll_Scale	= 2.0
Plugin.acc.Pitch	= -ABS_Y
Plugin.acc.Pitch_Scale	= 2.0
```
If you have mouse buttons bound then it will also control your mouse cursor.  If you have no mouse buttons bound (and use keyboard / joystick buttons only), then it will appear to Ubuntu as being a joystick that works in google earth / other apps that want joysticks.

I have a pretty confusing terms here.

What is the difference between > REL_WHEEL and using > KEY_UP&DOWN?

And the what is the difference between > Dpad.X and > Wiimote.Left&Right?

Thanks for all the great work guys!

---

### Post by Rhubarb on 2008-06-29
> **Nxion said:**
> So If I wanted to use this as a mouse w/ a IR sensor, will any IR receiver from the store work with it. I tried using it with the acceleration data but it was a little annoying.
Ok, first of all, a Wii sensor bar is not actually a sensor, it's actually just a rod with a bunch of IR lights at each end.
Any IR **emitter** should work fine, preferably at around 940nm in wavelength.  - You can try with any remote control (tracking won't be that good - because the IR LED in a remote control flashes), an incandescent light bulb or a candle.  Pretty much anything that gives a nice constant IR source that's not too bright (incandescent light bulbs can be too bright) should work fine.


**madu:-**
REL_WHEEL can give (mouse) scroll up and scroll down values.
So when using **Wiimote.Dpad.Y = REL_WHEEL** scrolling up will go to to the up button on the Dpad, and scrolling down will go to the down button on the Dpad.
KEY_UP&DOWN is used if you want to bind **ONE** button / key to it.
as REL_WHEEL is not **a** button / key (it actually can report scroll up and scroll down), you can not bind it it to just one button on your Wiimote (hence you need to bind it to Wiimote.Dpad.Y or any axis you wish.

If you don't quite understand, it's perhaps best if you tried binding it yourself, and experimenting to see what happens.

Hopefully I've explained this well enough, it's a bit difficult for me to explain this concept clearly.
Some good reading: [http://en.wikipedia.org/wiki/Infra_red](http://en.wikipedia.org/wiki/Infra_red)

---

### Post by Toshibawarrior on 2008-06-29
> **madu said:**
> Hey thanks a lot for that ToshibaW.

BTW, how did you find the keys like KEY_VOLUMEUP, KEY_NEXTSONG?
Do you define them somewhere?

Thanks a lot mate.

madu, go check this link --> [http://abstrakraft.org/cwiid/browser...ction_enum.txt]("http://abstrakraft.org/cwiid/browser...ction_enum.txt") There's all you need to know about which key/button bindings you can make with you wiimote and classic controller (optional).

I've asked a lot of stupid questions in this How-To but thanks to Rhubarb and the others I can understand this thing very good now. So I can actually be of assistance if anyone needs me ;). I hope this link helps madu, it has tons of key/button bindings that'll help you do all sorts of cool things with your wiimote! BTW the "NEXTSONG, PLAYPAUSE, and PREVIOUSSONG bindings are absolutely awesome!!! especially if you're a music-junkie like me :p!

NOTE: The link is dead right now...the page is going through some Python errors or at least that's what they say. When i click on it, it gives me a weird "OperationalError" and some bizarre Python error logs...Anyways, Rhubarb provided the same link on his How-To...you'll have to wait until they fix the page...:(

2nd NOTE: Now that i think of it, I don't know if the NEXTSONG,PREVIOUSSONG, PLAYPAUSE, VOLUMEUP, VOLUMEDOWN, etc key bindings are usable on any computer. They appear on the list of key/button bindings on the CWiiD webpage (the link above), but my laptop has these controls as part of the keyboard. My laptop has something like a Media Remote but stuck to the keyboard...with those functions (volume, play, pause, etcetcetc) so as Rhubarb said you should experiment with different bindings to see which one works for you ;). I hope those bindings work for any laptop/desktop, because they're uber cool :p!!!

---

### Post by madu on 2008-06-29
Dear Rhubarb and ToshibaW.
Thank you very much for the information guys. I think I got it now Rhubarb.
Yes ToshibaW, the link gives me an OperationalError too.
I got my Volume up and down working.. like you my Dell laptop also has volume/play/stop etc., buttons. Maybe thats why it works.. Interested in knowing other ones...

Rhubarb, do you have any idea how to get the Acc./Pitch/Rll values out of the Wminput? Without being able to see in Wmgui, anyway I can output them to console, .txt? 
I had a look at the wminput.wmgui sources but they are too complicated for me.

For example like this (for Windows): [http://carl.kenner.googlepages.com/glovepie](http://carl.kenner.googlepages.com/glovepie)

Thanks for all the help guys!

BTW anybody tried the touch screen thing?
I'm going ot make a IR pen this weekend and try it out.. cant wait.. :)

---

### Post by Toshibawarrior on 2008-06-29
You're welcome madu! 

And no, I haven't played with the touchscreen thing...I don't have an IR pen yet...Maybe I should make one too ;)!

---

### Post by Rhubarb on 2008-06-29
The volume/play/stop etc wiimote bindings will work on any computer / laptop regardless of if you have those keys on your keyboard / laptop or not.

I'm not aware of any ways to get pitch / roll / X or Y data to your console (and hence into a txt file).  If you're handy with some Python or C, you should be able to do it yourself somehow.
May I ask why you want to have these values in a text file?

I've made up an IR LED pen myself, and it works flawlessly.  Once you've made up the IR LED pen, it's all very easy to get going with it :)
You can draw with GIMP, play cards in Solitaire, pretty much anything you want ;)
Try out Phun when you've got your whiteboard working too (it's a 2D physics simulator fun app to play around with):
[http://phun.cs.umu.se/wiki/Download](http://phun.cs.umu.se/wiki/Download)

---

### Post by madu on 2008-06-29
Thanks for the Rhubarb.
I haven't got anything special in mind.. but was thinking certain angle+key combinations to do things.. I mean this thing opens up a heck of possibilities... I wish Wiimote had more buttons :)

Thanks for all the input guys...
Can't wait to get my IR pen done..

P.S: Rhubarb I noticed in an earlier post you said that accelerator method cannot do keyboard binding (only IR method)? But I can get every key binded as in the ../winput/buttons config. And I'm only doing the accelerator method? Did I miss something?

Thank you.

---

### Post by Toshibawarrior on 2008-06-29
> **madu said:**
> Thanks for the Rhubarb.
I haven't got anything special in mind.. but was thinking certain angle+key combinations to do things.. I mean this thing opens up a heck of possibilities... I wish Wiimote had more buttons :)

Thanks for all the input guys...
Can't wait to get my IR pen done..

P.S: Rhubarb I noticed in an earlier post you said that accelerator method cannot do keyboard binding (only IR method)? But I can get every key binded as in the ../winput/buttons config. And I'm only doing the accelerator method? Did I miss something?

Thank you.

The wiimote would technically have more buttons with a Wii Classic Controller attached...now that's awesome. 

And about the key binding problem on REL (accelerometer0 it got fixed with the removal of "mouseemu"...Cyborg made that discovery and Rhubarb corrected his awesome How-To with this info. ;):p

The Classic Controller opens up tons of more possibilities ..You'd have to buy one to see for yourself. It has two joysticks, tons of buttons and an extra D-Pad...;):)

---

### Post by Rhubarb on 2008-06-29
If you wish for more buttons on the wiimote, then it is possible to bind Alt / Ctrl / Meta (Super) / Numlock buttons to your wiimote.
Which means with some tweaking to gnome / programs you use you can get significantly more accessible buttons on your wiimote than what the wiimote offers.

As Toshibawarrior said above, accelerator method input does now work with keyboard binding, I had updated my main post to reflect this.  I will make this more clear on other posts I have made.  - You won't experience any problems with this.

> **Toshibawarrior said:**
> The Classic Controller opens up tons of more possibilities ..You'd have to buy one to see for yourself. It has two joysticks, tons of buttons and an extra D-Pad...;):)
For some reason I can't get the two joysticks working on two different bindings / same bindings simultaneously.
I can bind one or the other, but not both.  - I may have to investigate this further.

---

### Post by madu on 2008-06-29
Ah nice.
Thanks guys.
Classic controller is pretty impressive but it is wired right? having both Wiimote and classic kinda clutter it up. but still.. looks interesting now you mention it :)
Thanks a lot guys!

---

### Post by Rhubarb on 2008-06-29
> **madu said:**
> Classic controller is pretty impressive but it is wired right?
Yes there is a wire going from the classic controller to the wiimote, it's not too annoying really.  I use the classic controller to play smc (Secret Maryo Chronicles) :D

---

### Post by lunarcloud on 2008-06-29
Is there any way to map the nunchuk stick axis to up down left right? I'm trying to get it to work well with half life, but ABS_X/Y sets itself to the first joystick device AND the mouse. I would like ir to be mouse and nunchuk stick to be a joystick, but that wouldn't matter if I could set the axis to keys.

---

### Post by Rhubarb on 2008-06-29
> **zarquad said:**
> ...ABS_X/Y sets itself to the first joystick device AND the mouse...
When you bind mouse buttons on the wiimote / nunchuck, your joystick also becomes a mouse.  If you **don't** wish for the mouse to be created as well, make sure there are **no** mouse buttons bound in /etc/cwiid/wminput/buttons
As far as I know, it is not possible to bind 2 forms of analogue input (IR and nunchuck, nunchuck and acc on wiimote, etc) simultaneously.
While I don't have a nunchuck here to test with, I don't think it's possible to bind up/down/left/right to the accelerometer in the nunchuck.
It is however possible to bind up/down/left/right to the D-pad on the wiimote / classic controller.
I'm hoping these issues will be fixed up in cwiid soon.  (Perhaps I should file a bug to the people that develop cwiid).

---

### Post by Nxion on 2008-06-30
> **Nxion said:**
> So If I wanted to use this as a mouse w/ a IR sensor, will any IR receiver from the store work with it. I tried using it with the acceleration data but it was a little annoying.

Any one?

---

### Post by Rhubarb on 2008-06-30
> **Rhubarb said:**
> Ok, first of all, a Wii sensor bar is not actually a sensor, it's actually just a rod with a bunch of IR lights at each end.
Any IR **emitter** should work fine, preferably at around 940nm in wavelength.  - You can try with any remote control (tracking won't be that good - because the IR LED in a remote control flashes), an incandescent light bulb or a candle.  Pretty much anything that gives a nice constant IR source that's not too bright (incandescent light bulbs can be too bright) should work fine.
So long as you understand that they're not actually IR sensor bars / IR receivers (the wii sensor bar is just a marketing term, it's far far from the truth of what it actually is).  If you can buy these, they should work fine for you.

---

### Post by madu on 2008-06-30
I dont get how Wiimote can track the changes from an IR LED and how the program can map the X/Y  on the screen.
I'm going to make a sensor bar myself. Just wondering is there an optimal way of placing the LEDs? I mean rather than placing them together in a line (side-by-side), what if I place for LED's on the sides of the monitor? would there be any difference?

Cheers!

---

### Post by Rhubarb on 2008-06-30
There is an IR camera at the end of the wiimote.  It can see up to 4 point sources of IR light at a time.
If you wish to see what your wiimote can see, load up Wmgui:-
Applications --> Accessories --> Wmgui
Then, Settings --> IR Data
Then just wave a remote control / candle in front of it.

The wiimote must be able to see at least 1 IR light source at a time if you wish it to move the mouse cursor.
So where you place the IR LEDs is up to you, it depends haw far you wish to be able to swing your wiimote around and still expect mouse tracking, and how far away from the screen you'll be.
Remember the IR camera inside the wiimote only has about a 45° field of view.

You can place an IR LED at each of the 4 corners of your screen if you wish (this is similar to what I'll be making sometime soon).

---

### Post by Toshibawarrior on 2008-06-30
> **Rhubarb said:**
> 
You can place an IR LED at each of the 4 corners of your screen if you wish (this is similar to what I'll be making sometime soon).

Great idea. Sounds good...although I  really don't want anything stuck to my laptop. I'll figure out a way to make some sort of removable frame or something :(.

;)

---

### Post by madu on 2008-06-30
> **Rhubarb said:**
> There is an IR camera at the end of the wiimote.  It can see up to 4 point sources of IR light at a time.
If you wish to see what your wiimote can see, load up Wmgui:-
Applications --> Accessories --> Wmgui
Then, Settings --> IR Data
Then just wave a remote control / candle in front of it.

The wiimote must be able to see at least 1 IR light source at a time if you wish it to move the mouse cursor.
So where you place the IR LEDs is up to you, it depends haw far you wish to be able to swing your wiimote around and still expect mouse tracking, and how far away from the screen you'll be.
Remember the IR camera inside the wiimote only has about a 45° field of view.

You can place an IR LED at each of the 4 corners of your screen if you wish (this is similar to what I'll be making sometime soon).

Thanks Rhubarb.
I tried with two LED's at the bottom of my monitor and seems the range is limited and I can't cover the whole screen. I'm thinking 4-pairs at the sides.
But I'm wondering whether Wiimote (or wminput) can work that way.
For example, I have 4 LEDs around the screen; one on top, one on left, right and bottom. Suppose Wiimote can see all for LEDs at one time, and then I turn the Wiimote to the right-top direction, such that the left and bottom LED's are now out of range on the Wiimote angle. In this case, will the flow (mouse movement) be maintained? or the program will reset to track the right & top LEDs? or it doesn't matter?

It's kinda difficult to explain. But I think you get what I'm asking.

Thanks!

---

### Post by Rhubarb on 2008-07-02
madu, please read my previous posts a bit more closely - it's all in there.
So long as your wiimote can see at least 1 IR LED, it will work.
Your wiimote must not be able to see more than 4 IR LEDs at a time.
You may be better off placing your IR LEDs at each corner of your screen, top right, top left, bottom right, bottom left.  This will give you more swinging freedom on your wiimote than IR LEDs placed top, bottom, left and right.
Also, the IR LEDs don't necessarily have to be near your screen, they just have to be somewhere where you'd like to be able to swing your wiimote around in.

---

### Post by TrashmanL on 2008-07-04
> **Rhubarb said:**
> I don't think it's possible to bind up/down/left/right to the accelerometer in the nunchuck.
It is however possible to bind up/down/left/right to the D-pad on the wiimote 

I don't know if you meant the keys up/down/left/right or mouse directions. FYI I was able to control the mouse w/nunchuk acc, but I could not assign the wiimote acc to anything  else at the same time

---

### Post by Rhubarb on 2008-07-04
> **TrashmanL said:**
> I don't know if you meant the keys up/down/left/right or mouse directions. FYI I was able to control the mouse w/nunchuk acc, but I could not assign the wiimote acc to anything  else at the same time
Ahhh ok, I was referring to keys.  But I do think it's possible now to bind the nunchuck / wiimote acc to the cursor keys on your keyboard.  There's a nice program in the Ubuntu repos called **joy2key**.
There is a nice howto to get joy2key working nicely (because the wiimote / nunchuck is actually detected as a joystick (and sometimes also a mouse), it should be possible to translate joystick movement into keyboard key pressing.
[http://ubuntuforums.org/showthread.php?t=646564](http://ubuntuforums.org/showthread.php?t=646564)

---

### Post by Nxion on 2008-07-06
Can someone please tell me if any IR reciver that I buy will let me use the wii remote as a mouse?

---

### Post by madu on 2008-07-07
> **Nxion said:**
> Can someone please tell me if any IR reciver that I buy will let me use the wii remote as a mouse?

what you need is an IR source.
So as long as you the device has IR emitters it should be fine. Thats why even candles work. But having a good IR LEDs will prbably aid in good tracking...

---

### Post by madu on 2008-07-07
> **Rhubarb said:**
> madu, please read my previous posts a bit more closely - it's all in there.
So long as your wiimote can see at least 1 IR LED, it will work.
Your wiimote must not be able to see more than 4 IR LEDs at a time.
You may be better off placing your IR LEDs at each corner of your screen, top right, top left, bottom right, bottom left.  This will give you more swinging freedom on your wiimote than IR LEDs placed top, bottom, left and right.
Also, the IR LEDs don't necessarily have to be near your screen, they just have to be somewhere where you'd like to be able to swing your wiimote around in.


Thanks Rhubarb.
I made the IR sensors over the weekend and tried having  them around my monitor. But unfortunately it wasn't very succesful. I placed 4 IR LEDs in the four sides/corners. This depends on how and where you use it, but I tried with the same position as I would normally use my mouse and it was not usable. Becasue of the small distance from the Wiimote to monitor, Wiimote couldnt see all 4 LEDs at the same time. Probably it can only see one LED. so when I want to move the cursor around to corners, Wiimote tracking changed from one LED to the next. and everytime it sees a new LED (and lose the sight of the last LED) the mouse pointer resets back and starts. So you can't get a continuous motion.

Ofcourse this depends on your monitor size and how you handle the Wiimote. After some moving around I found the best place for the LED's is the bottom of the monitor. Still can't cover the complete monitor but gives a fairly good area. Angled the LED's so that they face the Wiimote. I'm not sure if its just me, but are the IR LEDs supposed to illuminate like normal LEDs? because the IR LEDs I got just faintly illuminate and they also have a range of about 45 degrees. 

All in all, it was a pretty interesting thing. Tried the whiteboard too. and like I said, with an IR LED of 45 degree range, pretty difficult to get it working. Still working on that..

Finally want to thank you guys for helping out.

Cheers!

---

### Post by dc2447 on 2008-07-07
So this works great.

So what stops the wiimote being paired with the Ubuntu machine when you want to use the Wii?

I can't test this as my Wii is having it's laser cleaned.

---

### Post by Toshibawarrior on 2008-07-07
Apparently the Wii-mote is instantly possessed by the Wii console as soon as it turns on. My wii-mote stops working with my laptop as soon as the Wii becomes active...

I haven't found a way to stop this...:(:(

---

### Post by Holmen on 2008-07-07
Love the guide, its perfect.

But - How do I map my Nunchuk joystick to WASD keys so that I can use them in, say ETQW?

---

### Post by Rhubarb on 2008-07-08
madu, thanks for your investigations, I don't think I fully understood what you where saying before, but now I understand.
I just tested it with 2 IR LEDs, and you're right, seeing 1 LED is ok, seeing 2 LEDs is ok, but when one LED goes out of its field of view, the mouse cursor resets back to its previous position.
This does pose quite a big problem, the only way I can think to resolve this issue is to either submit a patch to wminput to fix this bug, or to space out your IR LEDs so at most your wiimote will only be able to see one IR LED at a time (there will be brief positions where your wiimote won't be able to see any IR LEDs).
IR LEDs don't appear to give off much light because they're Infra-Red (it's light that your eyes can't pickup very well) [http://en.wikipedia.org/wiki/Infra_red](http://en.wikipedia.org/wiki/Infra_red)
My whiteboard IR pen actually has an IR LED poking out the side of it, so the IR LED directly faces the wiimote (rather than having to reflect off the monitor)


dc2447, I don't know, I don't own a Wii console myself, you'll have to experiment ;)

Toshibawarrior, as I don't own a Wii console myself, I could be very wrong, but there's a button inside the battery compartment of your wiimote that may tell your wiimote to prefer to pair with Ubuntu rather than your Wii console.  As always you may have to experiment a bit to work this out.

Holmen, it may be possible to use a program in the Ubuntu repositories called joy2key (translates joystick movement which is what the wiimote reports back, into keyboard buttons).
Alternatively you could compile wminput's extra plugins:
[http://kyrlian.free.fr/binaries/cwiid/latest/](http://kyrlian.free.fr/binaries/cwiid/latest/)

---

### Post by madu on 2008-07-08
> **Rhubarb said:**
> ]

Thats a neat IR pen mate. My IR LED doesn't illuminate as much. Actually it doesn't illuminate at all.. I can see it working if I switch off all lights and see it very closely.. it's same as a remote control IR.. maybe I need to find a better one..

Thanks for that link for the plugin.. any idea what the ir_fps is doing?

Cheers!

---

### Post by Rhubarb on 2008-07-09
madu you probably don't need a better IR LED, the whole point of infra-red is that you can't see it.  It can only been seen easily using a digital camera (like on your phone or webcam), or using wmgui (Settings --> IR Data) which shows you what your wiimote can see.
The digital camera that took the pictures of my IR LED pen appears to filter out a lot of IR light, so better to try with a cheap camera like in a typical mobile phone.

I haven't tried out ir_fps yet, I may try it if I buy a nunchuck in future.
For some (brief) details about it:
[http://kyrlian.free.fr/binaries/cwiid/latest/howto](http://kyrlian.free.fr/binaries/cwiid/latest/howto)

---

### Post by madu on 2008-07-09
> **Rhubarb said:**
> madu you probably don't need a better IR LED, the whole point of infra-red is that you can't see it.  It can only been seen easily using a digital camera (like on your phone or webcam), or using wmgui (Settings --> IR Data) which shows you what your wiimote can see.
The digital camera that took the pictures of my IR LED pen appears to filter out a lot of IR light, so better to try with a cheap camera like in a typical mobile phone.

I haven't tried out ir_fps yet, I may try it if I buy a nunchuck in future.
For some (brief) details about it:
[http://kyrlian.free.fr/binaries/cwiid/latest/howto](http://kyrlian.free.fr/binaries/cwiid/latest/howto)


Thanks mate.
I think I need to first have a proper solid place to mount the Wiimote to do the calibration.

---

### Post by Rhubarb on 2008-07-09
If you've got a camera tripod, you can attach your wiimote to it with some rubber bands.  It's probably not a good long term solution, but good if you just want to impress your friends :D

---

### Post by madu on 2008-07-09
LOL.. yeah a tripod would work.. I dont have a tripod and unfortunately don't have the space to work with a tripod around there... :) probably fix it on my wall with something...

---

### Post by bodaciousllama on 2008-07-11
someone posted that they could use the nunchuk joystick as a mouse; how?

I looked at joy2key and the other joystick mapping programs, but the problem is that the nunchuk doesnt show up as /dev/js0

any ideas?

---

### Post by Rhubarb on 2008-07-11
While I don't have a nunchuck to test this out, you should be able to get your nunchuck working as a mouse.
Make sure in your /etc/cwiid/wminput/buttons you have:
```
Nunchuk.C		= BTN_LEFT
Nunchuk.Z		= BTN_RIGHT
```
Then connect to your wiimote using nunchuck_acc_ptr:
```
wminput -c nunchuck_acc_ptr
```

---

### Post by Toshibawarrior on 2008-07-12
> **Rhubarb said:**
> 
Then connect to your wiimote using nunchuck_acc_ptr:
```
wminput -c nunchuck_acc_ptr
```
:-k...:-s...:???:
I definitely have to try this...While I haven't been able to mess around with my wiimote on Ubuntu these past few days, I think I might be able to play with it some more today...I will try this nunchuk thingy, since i really want my joystick to control the cursor...but I see it kinda "impossible"...But thanks for the input Rhubarb! :);)

---

### Post by whyette on 2008-07-16
I'm currently browsing the internet and using my Hardy Machine with my infrared keychain light that I rigged up today. It works fantastically with the help of the Wii Whiteboard app that was in the link. Thanks for the awesome links!! I'm a proud owner of a laptop with a touch screen! For about 50 bucks!

EDIT: Has anyone else had any success with this use of the wiimote?

---

### Post by Rhubarb on 2008-07-16
Yes the wii whiteboard app is really nice isn't it?  <3

I just discovered another good wiimote application similar to CWiid (which is what this howto uses), it's called XWii.
[http://www.resplect.com/xwii/](http://www.resplect.com/xwii/)
I've had a quick play around with it already, the IR tracking is poor, and I dare say the accelerometer tracking is also a little poor.
But having said that, it allows you to bind multiple key combinations to buttons / actions / bumps.
You can even bind executables and bash scripts to it  <-- Which I just love, it's great!

So I think XWii makes a nice complement to CWiid, perhaps I may write up a little howto to get XWii up and running some day.

---

### Post by oodlesOfmoodles on 2008-07-18
Hey guys!

Thanks for the great How-To!

I got a wiimote today and got it up and running within minutes.

I'm sure this has been asked before but:

Is it possible to map the nunchuck analog stick to KEY_UP KEY_DOWN KEY_LEFT and KEY_RIGHT?

(I'm thinkin FPS's)

Thanks again!

---

### Post by Rhubarb on 2008-07-22
> **oodlesOfmoodles said:**
> Is it possible to map the nunchuck analog stick to KEY_UP KEY_DOWN KEY_LEFT and KEY_RIGHT?
Yes this is possible, but may be a little tricky to setup.
There are two ways in which this may work for you:

**joy2key** can translate joystick movements into key presses (I'm not sure how easy this is to get up and going)

**[XWii]("http://www.resplect.com/xwii/")** is an alternative to CWiid (which is what this tutorial uses), in some cases it's worse, and in others far better.

As I don't have the nunchuck myself I can't say exactly how this would be done (I'm thinking of getting one soon).

Personally I'd tend to lean towards using XWii, as it's very good once it's up and working (yes, there are some annoyances with it), it allows you to bind axis to keys, allows you to bind multiple keys to buttons, and allows you to bind programs and bash scripts to buttons.

I can help you if you need some with XWii.

---

### Post by qwerdy on 2008-07-23
Cool, i see the XWII developer finally had some time to add the daemon function to it :D. Thats the only thing that hold me back on using cwiid on my mythbox.

---

### Post by secros on 2008-07-26
I'd like to get the -d flag working with my setup here, but wminput doesn't like it.  When I try to use -d, it reports back the following  

"invalid option --d"

What can I do to get this thing always looking for my WiiMote so that I don't have to run the battery down when I'm not using it?

Thanks a lot.  I am more of a reader than a poster, so I'll be interested in seeing the responses.

Thanks again.

---

### Post by Rhubarb on 2008-07-27
> **secros said:**
> I'd like to get the -d flag working with my setup here, but wminput doesn't like it.  When I try to use -d, it reports back the following  

"invalid option --d"
Could you please post the output of:
```
wminput -v
```
Ideally it should say: **CWiid Version 0.6.00**
Are you running Ubuntu 8.04?  What version of Ubuntu are you running?

---

### Post by secros on 2008-07-27
Wow.  Thanks for the prompt response.  My ubuntu version is:

```
~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

```

The output for wminput -v is:

```
~$ wminput -v
wminput: invalid option -- v

```

The only valid modifiers I see come from the help command and are:

```
~$ wminput -help
usage:wminput [-h] [-w] [-c config] [bdaddr]

```

I should tell you that everything works fine when i use wminput, but I don't want to have to type in "wminput" everytime I want to connect or reconnect.

Thanks.

---

### Post by secros on 2008-07-27
I guess I could contribute something, so if anyone is using a MythTV with VLC as the MythVideo player with their WiiMote, I wrote up a myth config file to use with CWiid.  Feel free to use it.  Since I don't get in the nuts and bolts much, and am not yet tired of documentation, it is, of course, nicely documented.  Enjoy and thanks for the help.  

```
#mythtv setup

Wiimote.A	= KEY_P			#myth = play/pause	vlc = play/pause
Wiimote.B	= KEY_ESC		#myth = back		vlc = back to myth (end video/next in playlist)
Wiimote.Up	= KEY_UP		#myth = nav up		vlc = skip ahead 10 minutes
Wiimote.Down	= KEY_DOWN		#myth = nav down	vlc = skip back 10 minutes
Wiimote.Left	= KEY_LEFT		#myth = nav left	vlc = skip back 30 seconds
Wiimote.Right	= KEY_RIGHT		#myth = nav right	vlc = skip ahead 30 seconds
Wiimote.Minus	= KEY_LEFTBRACE		#myth = decrease vol	vlc = decrease volume
Wiimote.Plus	= KEY_RIGHTBRACE	#myth = increase vol	vlc = increase volume
Wiimote.Home	= KEY_BACKSLASH		#myth = mute		vlc = mute
Wiimote.1	= KEY_SPACE		#myth = select		vlc = subtitle toggle
Wiimote.2	= KEY_W			#myth = asp rat toggle	vlc = asp rat toggle

```

Note:  You need to go into the VLC interface prefs to change the hotkeys to agree with the key assignments.  Hope someone can use this, it's pretty functional for me.

---

### Post by secros on 2008-07-29
so, neither "wminput -v" nor "wminput -d" work.  any help would be appreciated, my info is in the few previous posts.  thanks.

---

### Post by Sebastian12 on 2008-07-29
How are you able to tell if your computer has a bluetooth adapter?

If you don't, how do you acquire one?

---

### Post by Helios1276 on 2008-07-29
Nice work, now my Wii remote will actually get some use ..

---

### Post by qwerdy on 2008-07-30
> **secros said:**
> so, neither "wminput -v" nor "wminput -d" work.  any help would be appreciated, my info is in the few previous posts.  thanks.

Then you probably dont have the latest version 0.6.00

Try with the latest one, or try out [XWII]("http://www.resplect.com/xwii/")

---

### Post by Rhubarb on 2008-07-30
> **Sebastian12 said:**
> How are you able to tell if your computer has a bluetooth adapter?

If you don't, how do you acquire one?
You should see a bluetooth icon come up in the top-right corner of your screen if you have bluetooth.
If you want a bluetooth adapter, just buy a cheap usb bluetooth adapter (some really cheap ones work, some may not work).

---

### Post by cruckin on 2008-08-01
um i know this is rather odd but i think this would be extremly cool if i could get my wii mote to work for some of my emulators anywho...
i dont believe i have a bluetooth pick up in my computer im assuming they are cheap but wondering if i could try this
i have a wireless keyboard and mouse that is connected by a small like usb pick up its from hp and is there a way for me to get it to pick up my wii mote???
I also have a wireless pci card...if that would work???

---

### Post by Rhubarb on 2008-08-02
> **cruckin said:**
> um i know this is rather odd but i think this would be extremly cool if i could get my wii mote to work for some of my emulators anywho...
i dont believe i have a bluetooth pick up in my computer im assuming they are cheap but wondering if i could try this
i have a wireless keyboard and mouse that is connected by a small like usb pick up its from hp and is there a way for me to get it to pick up my wii mote???
I also have a wireless pci card...if that would work???
You can get your wii remote working with your emulators in Ubuntu.
I doubt your hp usb pickup is actually bluetooth.
Check to see if there's the bluetooth logo on it:
[IMG]http://www.kirya.net/wp-content/uploads/2007/07/bluetooth_logo.png[/IMG]
Also check your panel too see if there's the bluetooth loge in there.
Your wireless pci card is for wireless LAN / internet, it's not bluetooth.

Bluetooth usb plug-ins can be bought for AU$10 here, most should just work when you plug it in (check the gnome panel - top right corner in Ubuntu - a bluetooth icon should pop up when your computer is bluetooth enabled).

---

### Post by cruckin on 2008-08-03
> **Rhubarb said:**
> You can get your wii remote working with your emulators in Ubuntu.
I doubt your hp usb pickup is actually bluetooth.
Check to see if there's the bluetooth logo on it:
[IMG]http://www.kirya.net/wp-content/uploads/2007/07/bluetooth_logo.png[/IMG]
Also check your panel too see if there's the bluetooth loge in there.
Your wireless pci card is for wireless LAN / internet, it's not bluetooth.

Bluetooth usb plug-ins can be bought for AU$10 here, most should just work when you plug it in (check the gnome panel - top right corner in Ubuntu - a bluetooth icon should pop up when your computer is bluetooth enabled).

thank ya sir
i figured most of those were stupid questions but i figured id see if there was  any way before i went out and payed that hefty figure for a bluetooth adapter :P

---

### Post by deathvalleyjoker on 2008-08-03
So i read through the first few pages and saw nothing on the IR receiver. Does anyone use an IR receiver , and if so, is it a single reciever like on a tv, or does it have the two end like the Wii does? 

not sure if i am wording that correctly or not but hopfully you understand what i mean. next question would be where can i buy one? 

sorry if this has already been answered, but like i said, after the first 5 pages or so, nothing about it has been said.

---

### Post by Rhubarb on 2008-08-03
> **deathvalleyjoker said:**
> So i read through the first few pages and saw nothing on the IR receiver. Does anyone use an IR receiver , and if so, is it a single reciever like on a tv, or does it have the two end like the Wii does? 

not sure if i am wording that correctly or not but hopfully you understand what i mean. next question would be where can i buy one?
You're after an IR transmitter (your wiimote is actually the reciever), you only need 1 emitter for it to work.
I don't know where you can buy them from, I just made it up myself with an IR LED, a switch, and a AA battery.

If you want to test your wiimote, try using a candle / cigarette lighter / incandescent light bulb.  Your wiimote should be able to track one of those fine.

---

### Post by deathvalleyjoker on 2008-08-03
> **Rhubarb said:**
> You're after an IR transmitter (your wiimote is actually the reciever), you only need 1 emitter for it to work.
I don't know where you can buy them from, I just made it up myself with an IR LED, a switch, and a AA battery.

If you want to test your wiimote, try using a candle / cigarette lighter / incandescent light bulb.  Your wiimote should be able to track one of those fine.

Rhubarb: thanks for the correction. after re-reading what i wrote, i see i mixed them up.

I thought i remember reading, when the wii first came out, that the sensor bar was only two lights and from that, the wiimote could triangulate where it is at. And that is how it is able to know where you are pointing. But if u say u have it working with just one transmitter, well then ill see if radio shack has one, and give it a whirl. Thanks

---

### Post by Rhubarb on 2008-08-03
> **deathvalleyjoker said:**
> Rhubarb: thanks for the correction. after re-reading what i wrote, i see i mixed them up.

I thought i remember reading, when the wii first came out, that the sensor bar was only two lights and from that, the wiimote could triangulate where it is at. And that is how it is able to know where you are pointing. But if u say u have it working with just one transmitter, well then ill see if radio shack has one, and give it a whirl. Thanks
When using your wiimote with your wii, it needs to see two IR lights.
But, when using your wiimote with this howto in Ubuntu, you only need one IR light (it works really well from just 1 IR light).
Have fun!

---

### Post by leffect on 2008-08-05
I've not looked at Wiimote stuff since Feisty, and wow, it's got a lot easier! Thanks, Rhubarb, for posting the new howto, and I hope you do get a chance to clean up my wiki page for the new version (it's probably worth keeping the old version around as an appendix, for those strange people who're still using an older version of Ubuntu though, I think) - the install instructions seem to be up to date, but the ones for actually using it are a little out.

Anyway. I've created some alternative icons for the Wiimote stuff, as I felt your ones didn't really fit in with my theme - they were a bit too loud, so I've made some slightly subtler ones.

Everyone, feel free to use them. I'm putting them under "Creative Commons Attribution-Share Alike" license, which essentially means you can use them wherever you like, but if you do, or you change them, let other people have them too.

I made the white one first, but on a more or less white toolbar, it didn't show up, so I darkened it a bit. That works quite nicely with the default theme colours. The inverted one, I'm using for the "killall wminput", where you used the red one, but I also did red and green icons as well, in case people have got used to them or prefer them! Hope they're useful.

---

### Post by leffect on 2008-08-05
Sorry to double post, but I noticed that the green one was a bit too pale, so here's a darker version.

---

### Post by Rhubarb on 2008-08-05
Lovely, thanks leffect :)
I've added your nice icons to my main tutorial.
I should update the wiki page, but I don't quite have time to do it at the moment.

If you have time leffect (or others here), by all means you may update it with my tutorial for Ubuntu Hardy.
The wiki can be found here: [https://help.ubuntu.com/community/CWiiD](https://help.ubuntu.com/community/CWiiD)

---

### Post by leffect on 2008-08-06
Glad you like them, Rhubarb! I've updated the Wiki page somewhat. It's now got instructions, split by version, for using the Wiimote as a mouse - both tilting and IR, but I've not added the additional controllers part, or the details on config files. I've not played with that myself yet, so I don't feel ready to write documentation on it! It also could use some proofreading, and checking, but I think it's pretty accurate!

---

### Post by Toshibawarrior on 2008-08-07
Darn! After I had my Wiimote working great I had a major need to format my pc and make a clean install of Hardy, and I copied lots of things, except the configurations files for this How-To I'll have to start from scratch again. Although I can paste the "Functions"I mapped to the buttons, if I can find where I posted them in this How-To...

Anyways, this has nothing to do with you guys, but I wanted to tell someone...LOL! :)

---

### Post by sl4sher on 2008-08-08
I'm having a problem with wminput thinking that my screen is about 200x200 pixels. The pointer will move and get to the edge of that box but won't move any further. Does anyone know if it's possible to provide the actual display size?

---

### Post by BLTicklemonster on 2008-08-08
So, if you have a wii guitar and frets on fire, would this allow you to use the guitar instead of the keyboard to play frets on fire?

---

### Post by leffect on 2008-08-08
BLT: Yes, I believe it would allow that. I've not actually tried it myself, but the technical side should work fine, and I think I've seen a mention somewhere of someone doing it.

If you do, and you get it working, it might be worth adding the config file you use to the howto, or to the wiki page as well! Though I imagine it will simply be a case of mapping the buttons on the guitar to the appropriate keys.

---

### Post by Toshibawarrior on 2008-08-08
I'm dtill kind of a noob with all of this, but leffect is right. I believe it's just a matter of mapping buttons, just like you do with a Classic Controller to play an emulator. I'm gonna try all this as soon as I get my "Wiimote-on-Ubuntu-mojo" going again :p And when I manage to install everything again ;)!

---

### Post by leffect on 2008-08-08
I've got a computer at home hooked up to the same TV the Wii's plugged into, so the sensor bar's conveniently on top of it, but until recently it's been running Feisty, but earlier this week, I upgraded it to Hairy, via Gusty, using the update manager gui. I was really impressed that I managed it without rebooting once (uptime's now about 135 days  \o/ )

Anyway, now that I've got that up to date, I can start using the new version of CWiid as discussed in this tutorial, so I'm going to give all this stuff a more serious try! I don't have a Guitar Hero guitar yet though, so that's going to have to wait, but apparently I'll be getting one for my birthday in a month or so!

I shall report back over the weekend, when I've seen how it goes!

---

### Post by Toshibawarrior on 2008-08-08
> **leffect said:**
> I've got a computer at home hooked up to the same TV the Wii's plugged into, so the sensor bar's conveniently on top of it, but until recently it's been running Feisty, but earlier this week, I upgraded it to Hairy, via Gusty, using the update manager gui. I was really impressed that I managed it without rebooting once (uptime's now about 135 days  \o/ )

Anyway, now that I've got that up to date, I can start using the new version of CWiid as discussed in this tutorial, so I'm going to give all this stuff a more serious try! I don't have a Guitar Hero guitar yet though, so that's going to have to wait, but apparently I'll be getting one for my birthday in a month or so!

I shall report back over the weekend, when I've seen how it goes!

Yeah let us know how it goes for you. As for the guitar hero guitar, I don't have one yet neither...they're too pricey...

I may get one when Rock Band ll comes out...now that's a hot wii-game...although probably due to hardware differences the PS3 and X360 version will be better...just like any other "port-to-every-systm-game"...

Anyways, hope you get all of this working good ;)!

---

### Post by BLTicklemonster on 2008-08-08
Oh I was just asking, because I think that would be cool. I don't have any infrared thingies on my computer, so I won't be trying it. Shame the wii sensor bar won't just plug in, lol.

---

### Post by Toshibawarrior on 2008-08-08
> **BLTicklemonster said:**
> Oh I was just asking, because I think that would be cool. I don't have any infrared thingies on my computer, so I won't be trying it. Shame the wii sensor bar won't just plug in, lol.

You can get a "Wireless Wii Sensor Bar" for $20 at GameStop...Or you can build one yourself like Rhubarb and others here have done...

Besides, you can use the wiimote with the non-infrared thingy...in accelerometer mode...

Anyways, this is uber cool!:popcorn:

---

### Post by leffect on 2008-08-08
You never know, they might leave the graphics at the level the slowest system can cope with, so the PS3 gets Wii style graphics! 

OK, probably not... But the Wii version of Godfather had new style controls, but still the same graphics as the PS2 version. Was still fun though!

I'll post to let you all know how the Wiimote thing goes. Probably tomorrow, although I'm not going to set up anything too clever, at least at first!

I threw together an IR light to use with my laptop as well... It was just a USB cable with the (non USB A plug) end cut off, and a resistor and IR LED soldered to the power lines. I stuck a bit of heat shrink over the components as well to make it neat. I played around with resistor values a bit, trying to get a decent range without damaging anything... In the end went for a fairly low resistance (can't remember what I used in the end - sorry), so the LED's very bright (slightly longer range than the sensor bar, I think) but the resistor does get a bit hot... Might use 2 LEDs in series next time, and perhaps 2 resistors to spread the heat out a bit!

You can also use a light bulb, but they tend not to be in as convenient a place, and they're not as good as LEDs. Check WMInput with the camera data on - you can see what the Wiimote's picking up from the black dots on the camera view.

---

### Post by BLTicklemonster on 2008-08-08
> **Toshibawarrior said:**
> You can get a "Wireless Wii Sensor Bar" for $20 at GameStop...Or you can build one yourself like Rhubarb and others here have done...

Besides, you can use the wiimote with the non-infrared thingy...in accelerometer mode...

Anyways, this is uber cool!:popcorn:

Oh, I actually have an extra sensor bar besides the one already hooked to the wii. I just meant it would be cool if I could use it on the computer, lol.

---

### Post by Toshibawarrior on 2008-08-08
> **BLTicklemonster said:**
> Oh, I actually have an extra sensor bar besides the one already hooked to the wii. I just meant it would be cool if I could use it on the computer, lol.

Ooooooh! I get it...we sould find a way to cut the cord on the bar and solder it to a USB tip...might be cool. And then we could sell them in the Cnonical Store as "Ubuntu Sensor Bars"! LOL!

---

### Post by dim333 on 2008-08-08
join the banning game everyone

---

### Post by leffect on 2008-08-09
> **Toshibawarrior said:**
> Ooooooh! I get it...we sould find a way to cut the cord on the bar and solder it to a USB tip...might be cool. And then we could sell them in the Cnonical Store as "Ubuntu Sensor Bars"! LOL!

That would actually be very easy, I think! IIRC, the Wii Sensor bars are 5V, so it would probably work! I'm tempted, except I don't really want to slice up my sensor bar!

Hardest part would be finding which wire's which in the cable, but plugging it into the Wii would make that easy enough. I wonder if it's possible to buy new "official" sensor bars... Or I could look into getting a wireless one, I suppose... And putting a USB plug on the end would mean I could just plug it into the media server behind the TV, and not have to worry about whether the Wii's on. I don't think I could mount a sensor bar on the top of my laptop though - it'd get in the way of the clip for opening it!

I said I'd update as to how my Wiimote adventures were going... I've run into a bit of a snag. The install worked fine, lswm and WMGUI work fine, so I can see the wiimotes, I can connect to the with wmgui and see the outputs - that's all fine - but when I try to run wminput, it says "unable to open uinput", and this is despite me having done the "sudo modprobe uinput". I think it's because I'm being awkward - I upgraded from Feisty to Hardy earlier this week, but I didn't want to reboot 'cos of all the stuff I've got running on the server, so I'm afraid that might be what's causing it not to work as I'll probably still be using the old kernal.

Does anyone have any thoughts on this, perhaps a way to prod it appropriately without rebooting?

Thanks!

---

### Post by davidw89 on 2008-08-09
Could someone link me to a USB bundle that will work with wiiremote and ubuntu?

thanks

preferably from dealextreme?

---

### Post by Toshibawarrior on 2008-08-09
> **leffect said:**
> That would actually be very easy, I think! IIRC, the Wii Sensor bars are 5V, so it would probably work! I'm tempted, except I don't really want to slice up my sensor bar!

Hardest part would be finding which wire's which in the cable, but plugging it into the Wii would make that easy enough. I wonder if it's possible to buy new "official" sensor bars... Or I could look into getting a wireless one, I suppose... And putting a USB plug on the end would mean I could just plug it into the media server behind the TV, and not have to worry about whether the Wii's on. I don't think I could mount a sensor bar on the top of my laptop though - it'd get in the way of the clip for opening it!

I said I'd update as to how my Wiimote adventures were going... I've run into a bit of a snag. The install worked fine, lswm and WMGUI work fine, so I can see the wiimotes, I can connect to the with wmgui and see the outputs - that's all fine - but when I try to run wminput, it says "unable to open uinput", and this is despite me having done the "sudo modprobe uinput". I think it's because I'm being awkward - I upgraded from Feisty to Hardy earlier this week, but I didn't want to reboot 'cos of all the stuff I've got running on the server, so I'm afraid that might be what's causing it not to work as I'll probably still be using the old kernal.

Does anyone have any thoughts on this, perhaps a way to prod it appropriately without rebooting?

Thanks!

[_You can buy official wii sensor bars!!!_]("http://store.nintendo.com/webapp/wcs/stores/servlet/ProductDisplay?productId=117713&currency=USD&catalogId=10001&tranId=0&lastAction=setCurr&storeId=10001&languageId=-1&categoryId=62707&ddkey=http:SetCurrencyPreference") Enjoy! LOL!

It would really be cool to do that and have it custom-made for computers. *sigh* techonlogy rocks!

davidw89, if you mean a USB sensor bar, it doesn't exist yet...at least I've never seen one...sorry.

---

### Post by davidw89 on 2008-08-09
No USB dongle (bluetooth) for my desktop computer to connect to the wi i remote. I don't want to sensor cuz i can use the nunchuck to control.

---

### Post by Rhubarb on 2008-08-10
> **BLTicklemonster said:**
> So, if you have a wii guitar and frets on fire, would this allow you to use the guitar instead of the keyboard to play frets on fire?
The wii guitar actually appears to the wiimote (and hence wminput) to be a wii classic controller.
Check this post out for the correct bindings for it:
[http://pennsylvania.ubuntuforums.com/showpost.php?p=3839705&postcount=65](http://pennsylvania.ubuntuforums.com/showpost.php?p=3839705&postcount=65)


If you wire up a USB powered sensor bar, and you're not sure if you've got the correct polarity, just plug it in and test it.
There's no danger of breaking anything if it's plugged in the wrong way, because an LED is a diode, it'll only emit light if it's hooked up correctly.  If hooked up incorrectly, no current passes, nothing will light up, and no harm is done.


If you're wanting to select the correct resistors for your LEDs, there is a simple formula you can use to derive the best value (and wattage) resistor (I can't remember off-hand what it is now - it's 4am here).
It just uses ohm's law which is simple enough to calculate.


davidw89, the only (easy) way to connect your wiimote to your computer is via bluetooth.  There's no avoiding that unless you know how to program microcontrollers and know about high speed i^2c buses.
So, get a bluetooth USB dongle, it's the only real way to connect your wiimote with your computer.

---

### Post by Toshibawarrior on 2008-08-10
Darn! Now I really want a Wii Wireless Guitar, but they're too expensive...there's a Nyko one that looks like a Telecaster for $40 on GameStop, but even that is too expensive for me right now.

Thanks to BLTicklemonster I discovered FretsOnFire...I heard of it before, but neevr got around to play with it. IT'S FUN!!! :)

---

### Post by leffect on 2008-08-10
I've had a bit of a look around with Google, and it appears that the Wii sensor bar runs on 7.3V, so connecting it to a USB plug probably won't work! Shame really, I was hoping to be able to connect the sensor bar to the computer behind the TV, meaning I wouldn't have to have the Wii on all the time for the "mouse" to work. Oh well! Guess I'll have to either make my own USB powered one, or put up with leaving the Wii on. 

After much deliberating, I finally decided I'd have to reboot the server (goodbye 136 day uptime!), but that fixed everything - I think all the problems I'd been having were due to running essentially a 8.04 OS, but with a 7.04 kernal. Now the Wiimotes link up happily, and seem to work exactly as I'd want.

So, the next thing I did was have a bit of a monkey around with the config files. I wanted to link the 1 and 2 buttons to space and f, so I could easily pause/play and fullscreen in mplayer. That was trivial to do, thanks to the list linked to upthread - I just put the appropriate keys in the config file and it just worked (tm!).

Slightly harder was getting the + and - buttons to flick between desktops (ie, rotate the cube). I didn't want to lose the ctrl+alt+arrow functions for flipping and I couldn't see a way with the current config files to tie a Wiimote button to multiple keys. However, I did notice that CCSM allows you to assign a keyboard shortcut, a mouse shortcut or both to an event, so I set it to use nice high mouse buttons (Button8 and Button9, neither of which my mouse has!) to the flip cube options. Sadly, the obvious options from the control list (BTN_8 and BTN_9) didn't work, but after a bit of experimenting, I discovered that BTN_BACK and BTN_EXTRA mapped to CCSM's Button8 and Button9. So, with the following config file:

```
Wiimote.A		= BTN_LEFT
Wiimote.B		= BTN_RIGHT
Wiimote.Up		= KEY_UP
Wiimote.Down	= KEY_DOWN
Wiimote.Left	= KEY_LEFT
Wiimote.Right	= KEY_RIGHT
Wiimote.Minus	= BTN_BACK
Wiimote.Plus	= BTN_EXTRA
Wiimote.Home	= KEY_HOME
Wiimote.1		= KEY_SPACE
Wiimote.2		= KEY_F
```

I can now pause/play, fullscreen and flip the cube all from the Wiimote!

The next stage is to decide what else I'm likely to want to do, and which buttons should do it! I think mpc next and mpc pause are going to be the next most important!

Also, I'm going to have a shot at getting wminput to switch config files as well. This would be easy enough with a bash script, killing wminput and reloading it with a different config, but ideally, I'd like to do it without having to reconnect the Wiimote.

Thanks for the advice about resistors and whatnot, Rhubarb, but I do know what I'm doing there (degree in Electronic Engineering!), I just got a bit carried away with the brightness! I shall probably knock another one up with 2 or 3 LEDs later when I get round to it.

---

### Post by Rhubarb on 2008-08-11
> **leffect said:**
> Also, I'm going to have a shot at getting wminput to switch config files as well. This would be easy enough with a bash script, killing wminput and reloading it with a different config, but ideally, I'd like to do it without having to reconnect the Wiimote.

Thanks for the advice about resistors and whatnot, Rhubarb, but I do know what I'm doing there (degree in Electronic Engineering!), I just got a bit carried away with the brightness! I shall probably knock another one up with 2 or 3 LEDs later when I get round to it.
If you can't get wminput to switch config files without having to reconnect you wiimote (at worst you just have to press buttons 1 + 2 to reconnect automatically - so long as you tell wminput to be in daemon mode), Then I recommend you try XWii.
XWii allows you to change configuration files on the fly quite easily.
Unfortunately there's a few non-elegant parts to XWii, and IR tracking isn't as good.
I'd recommend you try out XWii, it's quite easy to setup and learn, and does not conflict with CWiid / wminput (just don't run them simultaneously).
[**XWii website**]("http://www.resplect.com/xwii/")

I've only got a diploma in electronics here, not quite a degree like you have leffect.  But we're talking about simple electronics stuff here anyway :D
It's good to play around with electronics and Linux stuff, makes for a very powerful combination.  Customised nicely :D

---

### Post by davidw89 on 2008-08-11
Hi guys!
I have just bought this:
[http://www.dealextreme.com/details.dx/sku.754](http://www.dealextreme.com/details.dx/sku.754)

When i get it, i will see if i can get it working. In addition to Wii Remote, does nunchuck and the class controller work? Is it useful in controller HTPC?

---

### Post by Rhubarb on 2008-08-11
> **davidw89 said:**
> Hi guys!
I have just bought this:
[http://www.dealextreme.com/details.dx/sku.754](http://www.dealextreme.com/details.dx/sku.754)

When i get it, i will see if i can get it working. In addition to Wii Remote, does nunchuck and the class controller work? Is it useful in controller HTPC?
That USB bluetooth dongle looks very similar to one that I bought, works fine, just plug it in and you have bluetooth in ubuntu!

The nunchuck and classic controller work fine in ubuntu, just look in /etc/cwiid/wminput for examples you can use.
Examples such as:
/etc/cwiid/wminput/gamepad and /etc/cwiid/wminput/nunchuck_acc_ptr

I don't have a nunchuck myself, but I do have the classic controller, it's great with games like smc (super maryo chonicles), and extreme tux racer.

---

### Post by Toshibawarrior on 2008-08-11
Ok, so I want to share today :)

A little info first...

I use my nunchuk's Z and C buttons as CTRL and ALT and then move my wiimote for rotating the cube.

And I set up my Classic Controller to play SMC (Secret Maryo Chronicles) (thanks a lot to Rhubarb for mentioning this game, I never heard of it before, and it ROCKS!)

So I'll post my buttons config for anyone who wants to copy it and avoid the pain of choosing KEY_SOMETHING ... 

As I stated before on this thread, I use the wiimote's buttons mostly as a media remote...reference to my previous posts.

Anyways if you want to use my configuration, just delete everything on the "buttons" file and paste my configuration.

For any more info just ask me. I thought of this as a good way of sharing, since I don't know much about deep configrations...:)

Enjoy! (If you want)

```
#buttons

Wiimote.A               = BTN_RIGHT
Wiimote.B               = BTN_LEFT
Wiimote.Up              = KEY_UP
Wiimote.Down    = KEY_DOWN
Wiimote.Left    = KEY_LEFT
Wiimote.Right   = KEY_RIGHT
Wiimote.Minus   = KEY_PREVIOUSSONG
Wiimote.Plus    = KEY_NEXTSONG
Wiimote.Home    = KEY_PLAYPAUSE
Wiimote.1               = KEY_VOLUMEUP
Wiimote.2               = KEY_VOLUMEDOWN

Nunchuk.C               = KEY_LEFTALT
Nunchuk.Z               = KEY_LEFTCTRL

Classic.Up              = KEY_UP
Classic.Down    = KEY_DOWN
Classic.Left    = KEY_LEFT
Classic.Right   = KEY_RIGHT
Classic.Minus   = KEY_BACK
Classic.Plus    = KEY_FORWARD
Classic.Home    = KEY_ESC
Classic.A               = KEY_LEFTCTRL 
Classic.B               = KEY_LEFTALT
Classic.X              = KEY_3
Classic.Y              = KEY_SPACE
Classic.ZL             = KEY_4
#Classic.ZR             = 
#Classic.L              = 
#Classic.R              =

```

Edit: I forgot to uncomment some of the Classic Controller buttons...Now it's supposed to work well ;)!

---

### Post by Toshibawarrior on 2008-08-12
I think I found a bug. If you uncomment (remove the # on the /etc/cwiid/wminput/buttons file) on any button without an assigned KEY_ wminput won't start. I had to learn this the hard way. Keep all unassigned buttons of the wiimote, nunchuk, or classic controllers commented (with the # before the button).

---

### Post by speed32219 on 2008-08-19
I have been using Ubunut 7.1 edgy for a backend video server for Xbmc.  I just intalled 8.4 hardy to check out Xbmc so I can watch 720P and 1080i/p in a native mode.  I've been using my wireless mouse/keyboard, but would rather a remote.

I have a Wii so this is great news.  I just ordered a Bluetooth/USB device? 

 I also have the wireless Wii bar so will I be able to use that with the Wii remotes and Bluetooth also?

---

### Post by leffect on 2008-08-20
Yes. The sensor bar is just a set of IR LEDs, so it doesn't make any difference to the Wiimote whether you're using an official sensor bar, the wireless one, some LEDs you put together yourself or a couple of candles.

Have you had much luck playing 720/1080p video under Linux? I've tried a couple of computers (2GHz dual core laptop with onboard Intel video and 2GHz single core desktop with nVidia Quadro FX 540) and they both struggle playing 720p mkv files. They can, just, but there's no way they'd be able to play anything higher res than that!

---

### Post by dmiller40 on 2008-08-30
I have read through this post and it doesnt seem any1 but me is have a problem getting it set up. I got wminput wmgui lswm installed, I have a bluetooth working and the icon in the panel.

When i push 1+2 on the wiimote and enter lswm in the terminal, i get "NO Bluetooth interface found" My wiimote has all 4 lights blinking before i enter lswm, but i get the same message everytime.

thanks
dm

---

### Post by Toshibawarrior on 2008-08-30
Hmmm...weird...Try to turn off any other bluetooth devices that might be accessing the link at the same time the wiimote does. Try restarting the computer. And if this doesn't work try to unplug the bluetooth USB dongle (if it is a dongle, or deactivate if it's integrated...).

And, try to use any bluetooth device, like a cellphone, mouse or pocketpc, and check if they're currently working.

Let me know if this doesn't work. I's the best i can think of...

I've read that some laptops/desktops with integrated bluetooth like to play rough with Ubuntu and need to be configured for certain protocols/services...

Just let me know if it still doesn't work after all this.

---

### Post by dmiller40 on 2008-08-30
I have rebooted, I turned off any other bt devices so that ubuntu has the only bt turned on. I unplugged and plugged back in. Activated wiimote entered lswm and get the same

"Put Wiimotes in discoverable mode now (press 1+2)...
No Bluetooth interface found"

dm

---

### Post by Toshibawarrior on 2008-08-30
Even weirder...

Try to run Wmgui...And connect your wiimote (pressing 1+2 when it prompt you to)...You'll have to go to File > Connect, and check if it works there...if not...

Try to run lswm several times and pressing 1+2 several times like the tutorial says in case of malfunctioning. Also try to move the bt dongle from one USB port to another...I've never came across such a weird message on lswm...

You could also try to uninstall all the packages and re-install them with the bt dongle unplugged...or plugged if you already did the afore mentioned...



Let me know what happens.;)

---

### Post by dmiller40 on 2008-08-30
I've tried using wmgui file->connect and no luck. Also done multiple lswm (1+2) several times. I've been working on this since last night so i've probably tried 20 times.

I'll swich usb ports and see what happens, if nothing then i'll try and reinstall.

thanks
dm

---

### Post by Toshibawarrior on 2008-08-30
I know how frustrating it can be...I've gone through that with tons of programs. So let me know how it turns out...;)!

---

### Post by dmiller40 on 2008-08-30
I've uninstalled and reinstalled twice, once w/ the bt in once with it out. Still same message in lswm.

I think i may have stubled apon a problem. hciconfig returns
hci0: Type USB
BD Adress: ...
UP RUNNING PSCAN ISCAN
RX bytes:979 acl:0 sco:0 events:27 errors:0
TX bytes:359 acl:0 sco:0 commands:27 errors:0

but...
hcitool scan returns
Device is not available: No such device

what does this mean?
thanks
dm

---

### Post by Toshibawarrior on 2008-08-30
Apparently your device is not recognized by hcitool...apparently it's not recognized by Ubuntu either, and that's why lswm and Wmgui don't recognize it either...

Your other bt devices work okay?...

---

### Post by Toshibawarrior on 2008-08-30
You might find some useful info about hcitool [_here_]("http://ubuntuforums.org/showthread.php?t=898423&highlight=hcitool+scan"). I'm not familiar with hcitool...but check that link out. You may need to search Synaptic for bluetooth apps.

You're using Ubuntu Hardy, right?

---

### Post by Toshibawarrior on 2008-08-30
Okay, I found something...hcitool works fine here on my laptop...It recognizes my bt dongle. For some reason yours is not being recognized by the computer. Which is weird if you've already used it before, and it shows up on the gnome-panel. 

Right-click the bluetooth icon on the panel and click preferences. On the first tab click on "Other devices can connect", on the second tab click the "Input Service" checkbox, if it's not already marked. And on the third tab click on "Select class of device automatically".

Reboot, retry the lswm, wmgui and other tasks...and post back what you get.

Hope this helped.

---

### Post by dmiller40 on 2008-08-30
Ubuntu recognizes it, when i plug it it it says a bt device found. the bt icon is at the top, and when i search for bt devices w/ my phone i see it.

```
dmiller@hometheater:~$ lsusb
Bus 002 Device 002: ID 8086:1120 Intel Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0a5c:2035 Broadcom Corp. BCM2035 Bluetooth
Bus 001 Device 001: ID 0000:0000  
dmiller@hometheater:~$ hciconfig
hci0:	Type: USB
	BD Address: 00:00:00:00:00:00 ACL MTU: 377:10 SCO MTU: 16:0
	UP RUNNING PSCAN ISCAN 
	RX bytes:701 acl:0 sco:0 events:23 errors:0
	TX bytes:344 acl:0 sco:0 commands:23 errors:0
```

lsusb see's it, hciconfig see's it and says its running. Looks like im off on a bluetooth problem hunt though.

dm

---

### Post by Toshibawarrior on 2008-08-30
Man, that's very strange...I really can't figure out what it could be...:(...

Maybe Rhubarb will think of something else. I really can't find anything else on the subject. As far as my bt devices go, they connect swiftly...including my wiimotes...:'(

I'm sorry but I really can't help you further than I've done already. I'm sorry if i wasn't of assistance (which i think I wasn't, since you haven't solve your problem.)

Anyways, let me know if something new pops up...Maybe it'll give me another clue.

---

### Post by dmiller40 on 2008-08-30
I changed 1 setting in the bt properties and I'm rebooting now. I haven't ever plugged this bt in before so it wasn't working before this. I only use this machine as a media center so didn't have a need for bt. 

Until the awesome idea to use your wiimote as a remote ;-)

dm

---

### Post by dmiller40 on 2008-08-30
Ok so i was looking up how to setup bluetooth from [here]("https://help.ubuntu.com/community/BluetoothSetup")and at the hcitool dev i get all zeroes.

I've removed and installed bluez-utils and still get all zeroes.

dm

---

### Post by dmiller40 on 2008-08-30
Ok, so i have another usb bt i use with xp. Windows didn't support the one was using, i had to use their driver which sucked. Any way i swapped the bt and it found the wiimote. So yeah and damnit.

I guess having the wiimote is more important so i'll use it. And hopefully figure out what is wrong with the other later.

thanks for you help
dm

ps: i may be hitting you back to help map the keys. I only want to use it as a keyboard.

---

### Post by dmiller40 on 2008-08-31
YEAH!!! I got it working with acceleration. So... 2 questions. 

1. How do i turn off acceleration data, as i only want to use the buttons. Don't need mouse functionality. 

2. Can i just add a session and give it the command "wminput 00:A2:36..." so all i have to do is hit the (1+2) at startup?

thanks for your help
dm

---

### Post by leffect on 2008-08-31
OK. If you don't want the mouse to be controlled by the Wiimote, load wminput like this:

```

wminput -d -c buttons

```

This tells wminput to use the buttons config file which contains the keyboard mappings you've been setting up, but no mouse mappings. Normally when you run

```

wminput -d -c ir_ptr

```

it loads the ir_ptr (or acc_ptr if you use that instead) config file, which tells it to use the pointing (or accelerometers) for moving the mouse, and also loads the buttons config file as well. Just loading buttons removes the mouse config.

Oh, and in answer to your second question, the -d in the commands I listed daemonises wminput so it runs in the background waiting for you to connect the wiimote, and if you disconnect it (by pressing the power button on the wiimote) it'll stay in the background, so you can reconnect by pressing 1+2 again. If you know the address of the wiimote you're using, you can put that in the command too, which makes connection quicker. I use:  

```

wminput -d -c ir_ptr 00:19:1D:A8:44:AB

```

but you'd want:

```

wminput -d -c buttons 00:19:1D:A8:44:AB

```

(and of course change the address to the one for your wiimote)

---

### Post by dmiller40 on 2008-08-31
Awesome, so to make sure i'm getting it strait. When i run wminput w/ the -d command i only have to run it once? even if i reboot or do i need to put that command as a startup session?

thanks
dm

---

### Post by leffect on 2008-08-31
You have to run it each time you reboot, unless you put it in your session start.

I suspect if you run it from inside the gui, and then restart X (ie, ctrl alt bksp, or logout) then you'll have to run it again as well, but I'm not certain.

If you're planning to use it a lot, then I'd stick it in the session start, but if you're only planning to use it occasionally (or use the Wiimote for other things as well!) then you can stick an icon on one of your panels to start it, and another to kill it. The instructions (and the icons I made for this!) are on the first post of this thread.

---

### Post by monsterman199 on 2008-08-31
how do Install the plugins for cwiid for fps games?(from hear [http://kyrlian.free.fr/binaries/cwiid/latest/](http://kyrlian.free.fr/binaries/cwiid/latest/) ) the instructions don't make any since

---

### Post by Toshibawarrior on 2008-09-01
Guys, I don't know if you're getting annoyed by entering the command for changing button configuration each time...I know I have...So I put together this little script which does the "sudo gedit /etc/cwiid/wminput/buttons" almost automatically...Just double-click the script enter your password upon request, and presto! you're in the table to change button configs!...

I know this is a pretty simple script, but it's esier than having to enter the command each time you need to change something.

I thought I'd share this for making your lives, as well as mine, easier. ;)

**Note** This script uses "gedit" if you don't have it installed then this script won't work! ;)

Hope you guys like it!

---

### Post by Toshibawarrior on 2008-09-01
> **monsterman199 said:**
> how do Install the plugins for cwiid for fps games?(from hear [http://kyrlian.free.fr/binaries/cwiid/latest/](http://kyrlian.free.fr/binaries/cwiid/latest/) ) the instructions don't make any since

You have to compile both cwiid and those plugins...and you're right...the instructions make no sense. Probably a more experienced user will understand them.

---

### Post by Rhubarb on 2008-09-02
Simple script there Toshibawarrior :)
When using the super user in a gui app, it's best to use gksu instead of sudo (there's a few reasons why, but it's a good practice to get into).

So, I'd recommend to change it from this:
```
#!/bin/bash
sudo gedit /etc/cwiid/wminput/buttons/

```

To this:
```
#!/bin/bash
gksu gedit /etc/cwiid/wminput/buttons
```

To install the cwiid plugin for FPS games (it's not very descriptive in what it actually does), you'd need to compile cwiid and those extra plugins yourself.
There's a few things I have to do here at the moment, I may be able to compile it for Ubuntu 8.04 in 32 and 64bit deb packages (or maybe I should setup my own PPA repository) for those that want it (given it's actually useful - I play many FPS games myself).

So stay tuned ;)

---

### Post by Toshibawarrior on 2008-09-02
You're totally right! I completely forgot about the gksu/gksudo/sudo/su differences...I already fixed it with "gksu" although for some reason my favorite is "gksudo" ;)

Thnks for pointing that out! :)

I posted the corrected script here and on my previous post too ;)!

---

### Post by Rhubarb on 2008-09-03
> **monsterman199 said:**
> how do Install the plugins for cwiid for fps games?(from hear [http://kyrlian.free.fr/binaries/cwiid/latest/](http://kyrlian.free.fr/binaries/cwiid/latest/) ) the instructions don't make any since

Had a bit of fun today trying to compile cwiid with the extra fps plugins :)
It compiled nicely, the plugins work fine, and it all works beautifully.

I've made up a nice deb package for Ubuntu 8.04 32bit and 64bit.
Please note that I'm still learning how to make up deb packages, so it's not perfect (no menu entries in the applications menu for wmgui, and I don't know how to specify what dependencies my package requires).

Before installing, please remove any existing cwiid packages you've installed previously:
```
sudo aptitude remove libcwiid1-dev lswm python-cwiid transfermii transfermii-gui wmgui wminput
```

For some reason my package does require one cwiid dependency, make sure this is installed:
```
sudo aptitude install libcwiid1
```

To install my deb package, download the correct one for your platform, the double click on it, then click on the "install package" button.

The extra plugins work especially well with a nunchuck, to use it:
```
wminput -c fps_config
```
Happy fragging! :D

---

### Post by Angel_OD on 2008-09-13
Hi

Anyone have any ideas why my mouse pointer is not moving 
with IR tracking?
The IR is working in wmgui.


Edit: Aah nvm, I edited the wrong file.
I edited the conf file in :/etc/cwiid/wminput
when i needed to edit the file in :/usr/local/etc/cwiid/wminput

---

### Post by cewan on 2008-09-22
> **Angel_OD said:**
> Hi

Anyone have any ideas why my mouse pointer is not moving 
with IR tracking?
The IR is working in wmgui.


Edit: Aah nvm, I edited the wrong file.
I edited the conf file in :/etc/cwiid/wminput
when i needed to edit the file in :/usr/local/etc/cwiid/wminput

I have the same problem you mentioned above. My mouse pointer is not working with IR tracking. It works fine in wmgui. How can I fix this?

Mouse moves when using the acceleration thing. But it fails to move when using:
sudo wminput -c /etc/cwiid/wminput/ir_ptr 00:1E:35:55:D8:B5

I am running Gutsy 7.10. I dont have any config files under /usr/local/etc/cwiid/wminput, they are under: /etc/cwiid/wminput.

Grateful for any input/help :-)

---

### Post by deigote on 2008-10-07
Hello everybody.

Maybe it's a stupid question, but i'll take the risk :D. What doy you need to configure in your IR receiver? Any IR receiver will do the job? Cause I have a USB TV Card (with IR) working, but I don't have a remote control for it (I lost it :$). Not sure how to test that its IR receiver is working...

Everything else works great for me. Thanks a lot!

---

### Post by leffect on 2008-10-08
The IR for the Wiimote is not the same sort of IR as used by TV remotes. The sensor bar has IR sources at each end and the Wiimote has an IR camera which detects the sensor bar, allowing it to work out where you're pointing it.

I'm afraid I've not so much answered your question as told you you're asking the wrong question, but I hope it helps none the less!

---

### Post by Rhubarb on 2008-10-08
Technically a remote control can act as a source of IR light for a wiimote.
It won't do much good because the remote actually flashes like crazy, meaning the wiimote has difficulty locking on to it.

As leffect stated, you need 1 or 2 **sources** of IR, the wii "sensor" bar is not a sensor at all, it's just a pole with 2 IR lights at either end.

You can use a candle, sometimes an incandescent light bulb works, or you could buy a "sensor" bar, or make up an IR light source yourself with a cheap IR LED and a battery.

I hope I haven't confused you more :P

---

### Post by ethana2 on 2008-10-09
I just bought a wiimote just to use as a mouse with my new ubuntu dell, and getting it to work was about trivial, but there are three problems I'm having:

1. The X axis for the cursor is the wrong one from the accelerometer, making it unusable as a mouse
2. The latency isn't that great
3. It's not sensitive enough to use easily

How do I change my wminput configuration to fix these issues?  I'm thinking the latency thing could be due to dead zones or something..

---

### Post by ethana2 on 2008-10-10
It seems I may have overestimated the wiimote's hardware.
I have ordered an $8 AA powered emitter bar, it should be here in 2 to 5 days.

---

### Post by leffect on 2008-10-10
I take it from your second post that you meant that you were using it in "tilt" mode, rather than sensor bar mode? And so, from that, that by "wrong axis" you meant that you had to twist it (like a key) rather than turn it left and right?

If that's correct, then yes, that's pretty much what you have to do if you don't have a sensor bar, as the Wiimote can't detect left and right panning without one. While you're waiting for your sensor bar to arrive, however, you could try running it with the ir config file and pointing it at any light bulbs you've got nearby to see the difference.

Using IR instead of tilting will probably fix your latency and accuracy issues as well. To be honest, I wouldn't want to use the Wiimote as a replacement for a mouse full time, however for controlling a media server or running a presentation, it's fine.

Hope that helps, give me a shout if you want to know more!

---

### Post by markp1989 on 2008-10-18
i have ordered a wii remote just to test this

---

### Post by Toshibawarrior on 2008-10-18
And you won't regret it! This is very fun and useful! Let us know when you get your wiimote!

---

### Post by Perk on 2008-10-19
My wiimote works perfectly with Ubuntu, although there are a few problems when I try to use it for zsnes. I think it's just a matter of fiddling with the buttons config file. But, has anyone tested using two wiimotes at once for games? That would be neat.

---

### Post by markp1989 on 2008-10-23
> **Toshibawarrior said:**
> And you won't regret it! This is very fun and useful! Let us know when you get your wiimote!

just arrived to day, works excellent, 

one question, currently to move left or right, i have to turn the remote, rather then paning left. if i were it get an ir  source , and put it by my monitor it would work better?

---

### Post by Toshibawarrior on 2008-10-23
If you use the accelerometer on the wiimote the only way to move the cursor left or right is by twisting it.

If you get an IR source you'll be able to pan the cursor by moving the wiimote up/down/left/right and so on. 

IR mode is better for some people and it's kinda easier to get used to it. ACC mode is kinda trickier but you won't need anything besides the bluetooth adapter and the wiimote.

:popcorn:

---

### Post by markp1989 on 2008-10-23
> **Toshibawarrior said:**
> If you use the accelerometer on the wiimote the only way to move the cursor left or right is by twisting it.

If you get an IR source you'll be able to pan the cursor by moving the wiimote up/down/left/right and so on. 

IR mode is better for some people and it's kinda easier to get used to it. ACC mode is kinda trickier but you won't need anything besides the bluetooth adapter and the wiimote.

:popcorn:

ok, for the IR source, can i just use some IR leds, or do i have 2 buy the strip that the wii uses?

edit: tested using it my IR sky remote, tad jumpy, because its sending pulses, but it worked. i just ordered some IR Leds, that i will put in a row across the bottom of the my monitor

---

### Post by Toshibawarrior on 2008-10-23
Yep, you can use about any IR source...some will work better than others...

There are tons of posts about this topic on the course of this thread...read back a little and you'll learn a lot.

---

### Post by markp1989 on 2008-10-23
> **Toshibawarrior said:**
> Yep, you can use about any IR source...some will work better than others...

There are tons of posts about this topic on the course of this thread...read back a little and you'll learn a lot.

Thanks, I ordered a batch of 50 IR leds, for £3.70 that run at 1.5v so they are easy to power, and i have enough so if i mess up  i dont have 2 order any


based on user exprience, is it  better to have the IR leds above or below the screen?

---

### Post by Rhubarb on 2008-10-27
> **Perk said:**
> ... has anyone tested using two wiimotes at once for games? That would be neat.
I haven't tried 2 wiimotes yet (don't have 2 to try it out in), but if I do, I'll report back here.
It's probably best in this situation (easier and cheaper) to use a wiimote + nunchuck, rather than 2 wiimotes.


> **markp1989 said:**
> ... based on user exprience, is it  better to have the IR leds above or below the screen?
I find having only 1 IR LED is best (it doesn't require any more than 1 IR LED).
I prefer the IR LED to be just below the screen, but really it doesn't matter where you put it.
The IR LED could be placed anywhere, even away from the screen.
You place it where you are comfortable in pointing the wiimote at.
As you may well have 49 spare IR LEDs then, you really should consider making up a IR LED pen.  Which essentially gives you a really cheap touchscreen.

My IR LED pen consists of a AA battery, a momentary push button, an IR LED, an ex-highlighter, wire, rubber chair leg stopper, and some swearing was involved in getting it all together.
The software to get it working is easy, just grab it here: [http://code.google.com/p/linux-whiteboard/downloads/list](http://code.google.com/p/linux-whiteboard/downloads/list)

A close-up of my IR LED pen:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=76968&d=1215569727[/IMG]
Wiimote and IR LED pen:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=76969&d=1215569727[/IMG]

---

### Post by DayZno1 on 2008-11-02
> **cewan said:**
> I have the same problem you mentioned above. My mouse pointer is not working with IR tracking. It works fine in wmgui. How can I fix this?


Same Problem here. Have you been able to fix this?

Accelerate works fine on my linuxmce (gutsy), Buttons as well. But no IR tracking, I tried with a candle. However, it shows in wmgui, about 1 px in size but it is there and moving.

And I think I have a wiimote knock-off, not the real thing.

I appreciate any help.. Thank you guys for all the good work!

DayZ

---

### Post by leffect on 2008-11-02
Just to check the obvious things first... Are you using the IR config file? 

As it says in the first post in this topic, you need to edit /etc/cwiid/wminput/ir_ptr and replace

Plugin.ir_ptr.X	= ~ABS_X
Plugin.ir_ptr.Y	= ~ABS_Y

with 

Plugin.ir_ptr.X	= ABS_X
Plugin.ir_ptr.Y	= ABS_Y

and then load wminput with wminput -c ir_ptr 00:1F:32:95:EF:B0

---

### Post by DayZno1 on 2008-11-02
Hey leffect,

thanks for the quick response. 

Yes, all is as described in the Howto. Changing buttons works as well, so I think I am editing the correct files.

LinuxMCE is based on Kubuntu, just in case this is worth mentioning. 
Also, I have not adjusted any userrights yet, so I start with a "sudo". 

DayZ

---

### Post by Rhubarb on 2008-11-05
It seems that in Ubuntu Intrepid Ibex (8.10) my wiimote won't work properly.
wmgui and lswm can see my wiimote fine, but wminput doesn't work.
I'm pretty sure this is to do with uinput and the new xorg.
I'll have to dig around some more to find out how to get the wiimote working again soon.

If you have to have your wiimote(s) working in Ubuntu, I recommend you keep Hardy Heron installed (8.04), and don't upgrade to Intrepid Ibex (8.10) until a solution is found (unless you want to help find the solution of course).

---

### Post by Toshibawarrior on 2008-11-07
Yup, I've been sniffing here and there, and the new xorg is a pain in the back end. Synaptics touchpads are also harder to configure now. Back in Hardy I could even make my touchpad scroll like an iPod (circular motion) but with the new xorg that's harder to do now.

With wiimotes I believe it'll be the same. Probably uinput needs an update to work with the new xorg and the new file where "input" devices settings are stored (I read about it but I forgot how it's called).

---

### Post by Toshibawarrior on 2008-11-09
Hey Rhubarb- I found out that the new Xorg uses something called **xinput** to communicate with keyboards and mouses....maybe that stupid xnput is killing uinput...I guess...

I've been reading back and forth and apparently Xorg has no power over input devices now and xinput took the cookie jar...I dunno, maybe we need to experiment a little...:o

---

### Post by sneakersupplier on 2008-11-09
good site: [Air Jordan Shoes](http://www.sneakersupplier.com)

---

### Post by Ditch64 on 2008-11-11
the only problem im running into is that the IR thing isnt working, i tried having my friend hold up 2 lighters and nothing happend, the buttons work fine, and the tilt works fine when i set it to tilt, but it just doesnt work with the IR.. any ideas?

---

### Post by Rhubarb on 2008-11-11
> **Ditch64 said:**
> the only problem im running into is that the IR thing isnt working, i tried having my friend hold up 2 lighters and nothing happend, the buttons work fine, and the tilt works fine when i set it to tilt, but it just doesnt work with the IR.. any ideas?

Use wmgui to see if your wiimote can see IR sources.
Applications --> Accessories --> wmgui
Then go to File --> connect
follow what it says.
Then go to Settings --> IR Data
You should be able to see what the wiimote camera can see (at most 4 IR sources).

Then make sure you followed my tutorial correctly, specifically, the following:-


There's a configuration file that you must first edit before this is possible.
From a terminal, type this in:
```
gksudo gedit /etc/cwiid/wminput/ir_ptr
```

Find these lines:
```
Plugin.ir_ptr.X	= ~ABS_X
Plugin.ir_ptr.Y	= ~ABS_Y
```

and replace it with:
```
Plugin.ir_ptr.X	= ABS_X
Plugin.ir_ptr.Y	= ABS_Y
```

To get your Wii remote to track IR light sources, press buttons 1 + 2 on your Wii remote and from a terminal run this:
```
wminput -c ir_ptr
```

---

### Post by cta16 on 2008-11-11
> **Toshibawarrior said:**
> Back in Hardy I could even make my touchpad scroll like an iPod (circular motion) but with the new xorg that's harder to do now.

Can you give me a link to a tutorial for that?

EDIT:Nevermind, googled it and found out how to tweak Xorg. I always thought Macs had special hardware that would detect two and three finger gestures but I learned something new today =D

---

### Post by pierreski on 2008-11-12
Just fyi, **wmgui and wminput wiimote connectivity seems to be broken for me as well in Intrepid (8.10)**. They both worked fine in Hardy (8.04), but now appear to be non-functional. I can see my wiimote with lswm, but unfortunately neither program can establish a connection to the remote! :(

anybody up for squashing some bugs...?

---

### Post by Rhubarb on 2008-11-12
**wmgui** works fine for me in intrepid.

After some playing around, I just (literally 20s ago) worked out how to get **wminput** working using its accelerometers and IR as mouse input (as tested on my 32bit Intrepid install with all updates applied - will test on 64bit Intrepid sometime over the next few weeks):-

Make sure you've got all the relevant packages installed:
```
sudo aptitude install libcwiid1 lswm python-cwiid wmgui
```

Then load the uinput kernel module (you'll need to run this every time you boot up Intrepid):
```
sudo modprobe uinput
```

This is the weird bit, for some reason you have to run wminput as root, rather than (as previously, non-root):
```
sudo wminput
```

Then it all works! :D

I need further testing to verify that it works properly on 32 and 64bit, as well as extra extensions, like nun-chuck and the classic controller.

Then I'll update this guide to reflect the changes, so it supports both Hardy and Intrepid.
Oh, and binding mouse and keyboard buttons also works nicely too.

I'm so happy I got this working :D

---

### Post by tiyakusa on 2008-11-12
> **Rhubarb said:**
> **wmgui** works fine for me in intrepid.

After some playing around, I just (literally 20s ago) worked out how to get **wminput** working using its accelerometers and IR as mouse input (as tested on my 32bit Intrepid install with all updates applied - will test on 64bit Intrepid sometime over the next few weeks):-

Make sure you've got all the relevant packages installed:
```
sudo aptitude install libcwiid1 lswm python-cwiid wmgui
```

Then load the uinput kernel module (you'll need to run this every time you boot up Intrepid):
```
sudo modprobe uinput
```

This is the weird bit, for some reason you have to run wminput as root, rather than (as previously, non-root):
```
sudo wminput
```

Then it all works! :D

I need further testing to verify that it works properly on 32 and 64bit, as well as extra extensions, like nun-chuck and the classic controller.

Then I'll update this guide to reflect the changes, so it supports both Hardy and Intrepid.
Oh, and binding mouse and keyboard buttons also works nicely too.

I'm so happy I got this working :D

I just tried your solution, but it does not work at all:
I always get this message:
```
 Socket connect error (control channel)
unable to connect 
```

Any workaround...?

---

### Post by Toshibawarrior on 2008-11-12
Hmmm...weird...First make sure your Intrepid install is completely up-to-date. Then try to reinstall the packages needed to use the wiimote:

```
sudo aptitude remove libcwiid1 lswm python-cwiid wmgui wminput

```

Then restart the computer and go to a terminal again and type:

```
sudo aptitude install libcwiid1 lswm python-cwiid wmgui wminput
```

Now follow this section of Rhubarb's original tutorial as it'll work for Intrepid too.

> 
Allow your Wii remote to be a keyboard / mouse / joystick:-
Unless you want to run sudo modprobe uinput every time you start Ubuntu, it's recommend you make it automatically run upon Ubuntu start up.
Code:

gksudo gedit /etc/rc.local

Insert this line before exit 0:
Code:

modprobe uinput

So the whole file should look exactly like this:
Code:

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

modprobe uinput

exit 0

You may restart your computer for the settings to take effect,

Once you're done restart the computer again.

Once it boots up again run:

```
gksudo wminput <your wiimote's bluetooth address here>

```

And check if it works.

If somehow that doesn't work try reconnecting your bluetooth adapter to another USB port...if it is a USB dongle...

Let me know if it works for ya. :popcorn:

---

### Post by Rhubarb on 2008-11-12
I've got some more good news:

I've managed to compile the wii whiteboard application successfully:
[http://code.google.com/p/linux-whiteboard/](http://code.google.com/p/linux-whiteboard/)

You can't just install the deb files there, because it wants to see libbluetooth2 rather than libbluetooth3 that's provided with Intrepid.
So after compiling it, it seems to work fine.
It does seem to freeze up after ~ 1 minute of use, but I'm not sure if it's a genuine problem, or just a problem because I'm using a remote control to test it (which flickers an awful lot).

I'll have access to my 64bit Intrepid install in a few day's time, so I can test my wiimote there, and will be able to test the wii whiteboard out more properly too.

I still recommend people stick with Hardy if they're not confident in getting their wiimotes working for the time being.
After further testing, I'll release an update to my guide here.
I can't foresee any major problems getting wiimotes working fully as before in Intrepid for those more technically inclined at the moment.

It's all good news so far :D

---

### Post by yumeona on 2008-11-20
Hi, just a couple of questions:

Does XWii support mouse scrolling? What options are allowed in MOUSECLICK? 

Also, are gestures already possible with wiimote on linux?

Thanks. :)

---

### Post by Rhubarb on 2008-11-20
> **yumeona said:**
> Hi, just a couple of questions:

Does XWii support mouse scrolling? What options are allowed in MOUSECLICK? 

Also, are gestures already possible with wiimote on linux?

Thanks. :)

I haven't played with XWii for some time, but from the best of my memory:-
XWii would support mouse scrolling, it's just mouse button 4 and mouse button 5.
I'm not sure what you mean by what options are allowed in MOUSECLICK - you can bind a mouse click to any button / gesture on the wiimote.

I haven't done much research into gestures on linux, having said that, if you are using cwiid (like in my tutorial) and make the wiimote act as a mouse, then it should well be possible to find an application that supports mouse gestures.  Then it should work.

I know a fair bit about text input, and alternative input stuff.
So if you like I can look it up for you (if someone else doesn't beat me to it first).
Just bear in mind that I'll probably be rather busy during the upcoming months, so I may not be able to give a prompt response.

Cheers, Rhubarb

---

### Post by Toshibawarrior on 2008-11-20
Well, in other news, I managed to destroy my Ubuntu install and lost my everything...music, photos, videos, data, and Ubuntu in general, thanks to openSUSE I made a mistake in the partitioner and it took over my 3 partitions and destroyed them...so I'm back to 0 with WiiMote-On-Ubuntu....

Luckily I have my button config and other stuff safe on an external HDD but I'll need to reinstall everything back.

I also wanted to check if this trick was possible in other Linux distros...I'll check that later on today...:)

---

### Post by yumeona on 2008-11-20
> **Rhubarb said:**
> I haven't played with XWii for some time, but from the best of my memory:-
XWii would support mouse scrolling, it's just mouse button 4 and mouse button 5.
I'm not sure what you mean by what options are allowed in MOUSECLICK - you can bind a mouse click to any button / gesture on the wiimote.



Thanks! That was just what I needed. Sorry if that was a little vague, what I mean was that I don't know what to put in "mouseclick", I only know "MOUSECLICK 3" for the left mouse button and "MOUSECLICK 1" for the right mouse button. I was wondering if there were any other like mouse scroll or something, which you just answered. :)

Edit: I was referring to the config profiles in XWII, btw. 

> 
I haven't done much research into gestures on linux, having said that, if you are using cwiid (like in my tutorial) and make the wiimote act as a mouse, then it should well be possible to find an application that supports mouse gestures.  Then it should work.

I know a fair bit about text input, and alternative input stuff.
So if you like I can look it up for you (if someone else doesn't beat me to it first).
Just bear in mind that I'll probably be rather busy during the upcoming months, so I may not be able to give a prompt response.


Actually, I need the gestures to control a UI similar to Elisa Media Center. I'm trying to study the cwiid API, but I'm a little bit lost in it. If you could point me to something that may help me that would be great, but it's okay if you're busy. Thanks a lot. :)

---

### Post by iztok.jeras on 2008-11-23
I have no success in making wiimote work on intrepid. On Hardy it works fine.

I tested it on an AMD 64 system and the bluetooth driver seems to crash.
On an 32bit (Asus Eee Box, Acer Aspire One) I was not able to connect to the remote, It seems that it receives a device ID, but is not able to connect to it.

I do not have any other bluetooth devices to test with, but it seems that the problem might be with the bluetooth stack.

I was able to get the wiimote ID (i have yet to check if it is not from a random phone around) a few times, but was never able to connect or to get any further.

IzI

---

### Post by Trebaruna on 2008-11-24
> **Toshibawarrior said:**
> 
Once it boots up again run:

```
gksudo wminput <your wiimote's bluetooth address here>

```And check if it works.
I think you probably mean
```
sudo wminput <your wiimote's bluetooth address here>

```instead.
Remember, this is not a graphical command, so there's not need for graphical wrappers.

Also, rhubarb: is there a specific reason you do not setup wminput as a daemon at startup in your howto? This would eliminate the need for manual intervention to get the Wii remote working. 

Lastly: last night I got it up and running in intrepid x86. Haven't gotten around to the IR functionality yet, will report when I do. It might be interesting to report I did have some initial Bluetooth difficulties: after initial detection by lswm it refused to acknowledge my bluetooth adapter, even after some un- and replugging. After reboot it worked fine.

---

### Post by Rhubarb on 2008-11-25
> **Trebaruna said:**
> Also, rhubarb: is there a specific reason you do not setup wminput as a daemon at startup in your howto? This would eliminate the need for manual intervention to get the Wii remote working.

Good point, there's no reason why you couldn't add wminput to start up automatically.  The reason why I didn't include it to my howto, was because I hadn't thought of that (thanks by the way), and it'll probably cause problems if you wish to play on your Wii while your computer is on.
- Not that I have a Wii myself, but others probably do.

> **Trebaruna said:**
> Lastly: last night I got it up and running in intrepid x86. Haven't gotten around to the IR functionality yet, will report when I do. It might be interesting to report I did have some initial Bluetooth difficulties: after initial detection by lswm it refused to acknowledge my bluetooth adapter, even after some un- and replugging. After reboot it worked fine.

Thanks for the info, I was a bit confused initially with Intrepid too (and still am a bit).
I haven't narrowed down exactly what problems were the cause of it (could've been old packages that were fixed in updates, rebooting, or me not issuing a sudo wminput rather than just a wminput).

I'll have an opportunity to verify this further in the upcoming weeks.

Thanks again Trebaruna for the ideas and info.
I might compile an intrepid update to this guide sometime (unless someone else is nice enough to beat me to it) ;)

---

### Post by Toshibawarrior on 2008-11-25
I could make a guide for you Rhubarb...Just let me know if I should make it on another thread, or just add it here. :)!

Let me know! :popcorn:

---

### Post by micha137 on 2008-11-25
Hi Toshibawarrior,

I would love to find the guide you mentioned here!

@ all, 
I am also struggeling with getting the Wiimote to work as mouse in intrepid. (In my new Dell mini9 on hardy it worked almost out of the box without IR tracking though). 
In Itrepid on my three other systems (two desktops and one notebook) I just got my office Desktop to run wminput partially successful - the IR tracking is still not functional - will work on the other two systems this evening.

In my case too there was some trouble regarding the bluetooth usb-stick. One stick only worked up to the point of extracting the Wiimote adress information but wouldn't connect(MSI). I borrowed another one from a friend(Belkin F8TO12xx1) and that one connected.

In some older postings I found advice to edit some config files to turn the IR-Tracking on, but I couln't find the files to edit on my Intrpid desktop.
Can someone give me some advice on where to find the relevant config files now and what to change ?

I would love to use the Wiimote for my presentations(I am physics lecturer), but just using the accelerometers I don't have sufficient control over the mouse position to use it with confidence.

Since Christmas is homing in it would be really cool to light a candle during the lecture to allow for cursor positioning....

regards
   micha137

---

### Post by Toshibawarrior on 2008-11-25
Hi micha137, the guide I mentioned is still under construction. I might be able to finish it by tomorrow so stay tuned! :popcorn:!

---

### Post by daberger on 2008-11-26
should this work for 8.10 to?

cuz i tried it on it but it couldnt find any packages.
and if it doesnt is there a cwiid for 8.10?

---

### Post by Toshibawarrior on 2008-11-26
I made a new thread with a guide about using the Wiimote in Intrepid. But I made it last night and 14 hours later it's still un der moderating I guess...It's still not up. I did use some snippets from Rhubarb's guide, so I really hope that doesn't pose a problem because I gave credit to him for that.

So let's see if my guide gets posted and I'll send you a link. **Stay tuned!**

---

### Post by micha137 on 2008-11-26
Hi there,
just got wminput with IR positioning up and going for all three of my intrepid systems: 8-)).

Basically I followed Rhubarbs and Toshibawarriors how-to's. Many thanks to Down Under and to the guy in front of his notebook!

(I wouldn't be able to post a tutorial -like info because there was a lot of trial and error and some aparently erratic behaviour of my systems during the process of cutting through the jungle...besides-the systems behaved differntly for no reason apparent to me e.g. the dell notebook needed the "sudo modprobe uinput" thing and sometimes needed a bluetooth reset to partially function again once in a while, the desktop worked right out of the box and didn't even need the modprobe command ?!?)

Some comments from my side: 

1.) some bluetooth sticks just won't work with wmgui or wminput. The one I spent hours with (unsuccessfully) correctly received the bluetooth adress
and the info that the device is a wiiremote but just stubbornly didn't connect. 
Just got me a new one in an electronics shop and that one did it. It was a HAMA ( lsusb -> Broadcom Corp. BCM2210 Bluetooth) that connected. So if you can get the address of the wiimote but can't sucessfully connect with wmgui chances are your Bluetooth stick won't do. You might borrow other ones and check again.

2.) In Hardy I could run wminput as normal user whereas in intrepid only wmgui could be run successfully as non-sudo, wminput had to be called as sudo. 

3.) Without editing the ir_ptr file, ir-navigation was only partially functional. I could just move the mouse in  a rectangular subsection of the screen. Removing the "~" in the file (in folder etc/cwiid/wminput )did the job as pointed out in a recent posting by rhubarb or was it toshibawarrior...
A chrismas-candle is a perfect IR-source btw.

4.) There is a problem remaining (for me) though. In order to be able to run wminput as non-sudo and not to be forced to open a terminal and put in the keyword on request - according to the info popping up on "man wminput" I supposedly have to add the line:  
KERNEL=="uinput", MODE="0666"
to some *.rules file and that I should consult my sytem-info on which file to put this line in. Frankly - I had a look at some of the rules files and have no idea on where I am supposed to insert this line. Since these rules seem to be important to the workings of my system I don't really feel inclined to go for trial and error...
I would greatly appreciate help in this point from you ubuntu experts.

Anyhow - this last minor problem won't keep me from using the wiimote for all my future presentations.

Regards
  micha137

---

### Post by Toshibawarrior on 2008-11-26
Hello all! 

I thought you would be interested in knowing that my guide is up and running!

[HERE'S THE LINK TO MY GUIDE!]("http://ubuntuforums.org/showthread.php?t=993376&highlight=wii+remote")

Please keep in mind that I used an outline similar to Rhubarb's guide and I also used some parts of his guide, but my guide is directly aimed for Intrepid users...

If you have any questions about Intrepid+wiimote post them on my guide...if you have questions about Hardy+wiimote post them here, just to have a clean and organized look and info in both guides.

So feel free to ask questions, give suggestions, ask for advice, and anything else! I'll do my best to keep my guide up-to-date and to help everyone out!

:popcorn:!

---

### Post by micha137 on 2008-11-26
Hi Toshibawarrior!

Great tutorial. Would have saved me a lot of time if I could have started with your tutorial.

@all
As to the point of having to run wminput as sudo in Intrepid. The following steps fixed that on my system so that it can be called now as non-root in Intrepid:

1.)  
create a file in /etc/udev/rules.d
somewhat along the lines suggested by clockware in [http://sudan.ubuntuforums.com/showthread.php?t=535659&page=12](http://sudan.ubuntuforums.com/showthread.php?t=535659&page=12)
I named it "50-cwiid.input.rules" and included the single line:

KERNEL=="uinput", MODE="0666"

to make uinput accessible to any user (can alternatively be done a bit safer by assigning access only to a special group).

2.)
Then from a Terminal type: "sudo /etc/init.d/udev restart"

then I could call wminput successfully as normal user.


regards
  micha137

---

### Post by Toshibawarrior on 2008-11-26
Thanks for the info! Would you mind posting that on my guide's thread?

As soon as I personally test that I'll add it to my guide officially. Thanks for sharing!

---

### Post by t0ksik on 2008-12-10
Intrepid does not automatically give the admin group access to uinput.  Change your uinput settings to include the admin group and you can run wminput without needing root access.

---

### Post by Toshibawarrior on 2008-12-11
This might sound weird, but I like root privileges requests. That way I know that **wminput** started and it's doing something. But that's just me anyways...

For the record: when you guys have questions, suggestions or requests about Intrepid Wiimoting go post them on my guide -->[http://ubuntuforums.org/showthread.php?t=993376&highlight=wii+remote]("http://ubuntuforums.org/showthread.php?t=993376&highlight=wii+remote").

That way we can keep both guides with info relevant to each version.

---

### Post by dhruv_1884 on 2009-01-03
Hi Guys,

I cant seem to get the mouse scroll to work, any tips on how i could do so, or if it is even possible to do so?

regards
dhruv_1884

---

### Post by Meson on 2009-01-10
> **Rhubarb said:**
> 
[SIZE="4"]**Using your Wii remote as a mouse using acceleration data:-**[/SIZE]
If you want to use your Wii remote as a mouse by tilting your Wii remote, then press buttons 1 + 2 on your Wii remote and from a terminal run this:
```
wminput 00:1F:32:95:EF:B0
```
Please use your bluetooth device address for your Wii remote.


You should mention that you need to setup uinput for normal users.  The manpage for wminput explains how to do this by creating a udev rule.  Alternatively you can just SUID the wminput command.

---

### Post by Toshibawarrior on 2009-01-10
> **Meson said:**
> You should mention that you need to setup uinput for normal users.  The manpage for wminput explains how to do this by creating a udev rule.  Alternatively you can just SUID the wminput command.

As far as i know/tested this step is only needed in Intrepid Ibex...Check out[ my guide for Intrepid Ibex Wiimoting!]("http://ubuntuforums.org/showpost.php?p=6251695&postcount=1") ;)

In this guide you'll find the steps for Hardy Heron and on my guide you'll find the steps for Intrepid Ibex. Make sure to check my whole guide's thread since some people have mentioned some very nice observations and suggestions!

:guitar: Rock on!

---

### Post by xxKillBillxx on 2009-01-30
Hi, I'm having problems in getting the D-Pad working. When I get to the part where I put in "sudo wminput" Only the accelerometer and the A and B buttons work. I can't get any of the other buttons to work. Any help is appreciated.

---

### Post by jbulmer08 on 2009-02-17
Iv got this working great :) got next song pause previouse song even eject working. Thank you :guitar: rock on and keep up the good work. 5 gold stars :KS:KS:KS:KS:KS

---

### Post by drjonze on 2009-04-05
I've followed this guide and had no issues using my wimote as an IR remote in Hardy, Intrepid and now Jaunty. Thank you Rhubarb!

---

### Post by B4RR13N705 on 2009-04-05
Hi, i was looking to do this some of this days, then i red your tutorial, and i get convnced, i will buy a wii remote controller! Good job dude! very useful tutorial! thanx a lot!

---

### Post by Rhubarb on 2009-04-19
Thanks B4RR13N705, drjonze, and jbulmer08 :D

xxKillBillxx:  I haven't had much time recently to play around with the wiimote recently, so I'm a bit out-of-touch with it all.

I do know (as drjonze had said above) that the wiimote does work nicely in Jaunty, which is great news :)

As always, have fun everyone with your wiimote and ubuntu ;)

---

### Post by smith99 on 2009-04-29
Hi,

Here are some tips for wii remote in ubuntu.


Type in a name for it, for the command, use this

gksudo wminput -d -c ir_ptr [your wiimote's bluetooth address here]
  

For IR mode. If you want to use ACC (accelerometer mode) the command should be

gksudo wminput [your wiimote's bluetooth address here]
  
The gksudo is important because if you use sudo only you won’t see any prompt to type in your password, and in Intrepid it IS necessary to be root to activate wminput.

---

### Post by krul on 2009-05-23
Great topic!

However, after installing fresh Jaunty I am not able to run wminput without sudo, I get:

```

$ wminput
unable to open uinput

```I did change the udev rules with:
sudo sh -c 'echo "KERNEL==\"uinput\", GROUP=\"admin\"" > /etc/udev/rules.d/50-cwiid-input.rules'

And my user is in the admin group.

Anyone an idea?

---

### Post by andho on 2009-06-27
Hey,
I got my wiimote to work with wminput with the accelerometer. But the thing is my nunchuk is not getting detected. In wmgui it says no extension.

Is there any other way to check if my nunchuk is detected like, i don't know input probing or something.

I also tried the wiimote on windows and glovepie, and it only detected the nunchuk only if i was pressing a button on the nunchuk when i ran the script.
If i ran the script without pressing a button on the nunchuk then the nunchuk input is not detected.
Then problem on glovepie was the Joystick could not be calibrated.

So i'm looking for a solution on linux.
It would be great if you could help me

Thanks

---

### Post by RJ12 on 2009-07-27
Also is there a way to use the nunchuck stick as a mouse or wiimote dpad as a mouse I dont have a sensor bar and dont like the accl. thing

---

### Post by Jexel on 2009-08-17
Is anyone having problems with key bindings? I'm trying to bind the directional keys on the wiimote to wasd, however this doesn't seem to work. Has anybody managed to get this to work?

---

### Post by Boondoklife on 2009-09-07
Hey I wrote a little script that I use to enable and disable my wiimote connection, feel free to use it in your How-To.

In the attachment is a png of a wiimote and the script:

```

#!/bin/bash
# Small script that is used to connect and disconnect the wiimote from system
# requires zenity to be installed on system


if [ `pidof wminput` ]; then
 echo stopping wminput
 gksudo sleep 0.001 #this line to so the gksudo is in effect before the timer is called
 (for ((i=0;i<=100;i+=1)); do echo $i; sleep 0.03; done) | zenity --progress --auto-close --width 350 --text="Stopping the WiiMote interface"
 gksudo "killall -9 wminput"
else
 echo starting wminput
 gksudo sleep 0.001 #this line to so the gksudo is in effect before the timer is called
 gksudo /usr/bin/wminput &
 (for ((i=0;i<=100;i+=1)); do echo $i; sleep 0.08; done) | zenity --progress --auto-close --width 350 --text="Press 1+2 on the WiiMote Now"
fi

```

---

### Post by skotos on 2009-09-15
> **krul said:**
> ...after installing fresh Jaunty I am not able to run wminput without sudo, I get:

```

$ wminput
unable to open uinput

```I did change the udev rules with:
sudo sh -c 'echo "KERNEL==\"uinput\", GROUP=\"admin\"" > /etc/udev/rules.d/50-cwiid-input.rules'

And my user is in the admin group.

Anyone an idea?
Got the same problem, but yet no idea...

---

### Post by Boondoklife on 2009-09-15
Here is a version that doesn't prompt you for elevated rights:
```
#!/bin/bash
# Small script that is used to connect and disconnect the wiimote from system
# requires zenity to be installed on system
if [ `pidof wminput` ]; then
 echo stopping wminput
 (for ((i=0;i<=100;i+=1)); do echo $i; sleep 0.03; done) | zenity --progress --auto-close --width 350 --text="Stopping the WiiMote interface"
 killall -9 wminput
else
 echo starting wminput
 zenity --info --text="Press the 1 and 2 buttons at the same time on the WiiMote\nthen click ok."
 /usr/bin/wminput &
 (for ((i=0;i<=100;i+=1)); do echo $i; sleep 0.08; done) | zenity --progress --auto-close --width 350 --text="Connecting to the WiiMote"
fi
```You will need to add the following to your udev rules to get it to work:
/etc/udev/rules.d/uinput.rules
```
KERNEL=="uinput", MODE="0666"
```

---

### Post by CRAY-4 on 2009-10-03
how about fps games?
I tried playin quake live and the mouse(controlled by ir) goes crazy if you dont keep it inside of a small area

---

### Post by Kozar on 2009-10-07
I can't get past this error code

```

~$ sudo modprobe uinput
~$ wminput -c ir_ptr 00:1E:35:73:E6:76
unable to open uinput
~$ 


```

---

### Post by Boondoklife on 2009-10-08
> **Kozar said:**
> I can't get past this error code

```

~$ sudo modprobe uinput
~$ wminput -c ir_ptr 00:1E:35:73:E6:76
unable to open uinput
~$ 


```
Have you tried throwing a sudo infront of it? By default you need admin rights to use that module.

---

### Post by kevinguillorytraining on 2009-10-09
You are  good. I'll check it after finishing my work. Thanks

---

### Post by Kozar on 2009-10-09
Thanks Boondoklife it works perfectly now!

---

### Post by Boondoklife on 2009-10-09
You can add the udev rule i posted and then you would not have to do the sudo.

---

### Post by the_joey_o on 2009-10-10
I'm having trouble getting my computer to recognise any bluetooth device, including my wiimote. I have a usb bluetooth device that appears to be working. When I plug it in, I get the bluetooth symbol in my device tray. The usb bluetooth device also works in my other laptop that runs Windows Vista, although I had to download a driver from bluesoleil.com to make it work. I downloaded and installed an ubuntu version of the software from bluesoleil, but when I try to open the program, nothing happens. I'm running Jaunty on an old Gateway tablet. Any help would be great.

---

### Post by Boondoklife on 2009-10-10
i've never used the software that you are mentioning, but instead why not just try to send a file to a phone or something to see if that works.

---

### Post by the_joey_o on 2009-10-10
> **Boondoklife said:**
> i've never used the software that you are mentioning, but instead why not just try to send a file to a phone or something to see if that works.

I've tried, but it can't find my phone. No Bluetooth device will show up no matter what I do. I know that my wiimote and phone work with Bluetooth, because I can get them to interface with my laptop that runs Windows Vista via Bluetooth.

---

### Post by Boondoklife on 2009-10-11
> **the_joey_o said:**
> I've tried, but it can't find my phone. No Bluetooth device will show up no matter what I do. I know that my wiimote and phone work with Bluetooth, because I can get them to interface with my laptop that runs Windows Vista via Bluetooth.
Sounds like your bluetooth adapter may not work with ubuntu, what is the make and model? Have you looked online to see if there are any reports either way of its compatibility?

You might want to start a new thread as you wont get much related exposure in this one.

---

### Post by the_joey_o on 2009-10-11
That's one of my suspicions as well, but why would Ubuntu recognize it as a Bluetooth enabling device if it wasn't compatible?

I started a [new thread]("http://ubuntuforums.org/showthread.php?p=8088133#post8088133") to continue this discussion. Thanks.

---

### Post by drizzo4shizzo on 2009-10-17
> **skotos said:**
> Got the same problem, but yet no idea...

Try loading the uinput module.

sudo modprobe uinput

you will have to do this on every reboot, or you can just add uinput to /etc/modules.conf for it to be loaded automatically

---

### Post by gibdogg on 2009-11-03
> **Kozar said:**
> I can't get past this error code

```

~$ sudo modprobe uinput
~$ wminput -c ir_ptr 00:1E:35:73:E6:76
unable to open uinput
~$ 


```

I confirm I have the same problem, and yes I have added the rules file to /etc/udev/rules.d
It works if I run sudo wminput but this isn't exactly convenient.

Any ideas? Seems like a few people have this issue...

Thanks

---

### Post by Boondoklife on 2009-11-03
Post what you put in the rules file and the name of the file, also have you rebooted since you added the rule?

---

### Post by tqft on 2009-11-04
You can restart udev once you have updated the rules with

sudo /etc/init.d/udev restart

Rebooting the machine is generally cleaner and safer but not always practical for testing

---

### Post by Rhubarb on 2009-11-22
> **tqft said:**
> You can restart udev once you have updated the rules with

sudo /etc/init.d/udev restart

Rebooting the machine is generally cleaner and safer but not always practical for testing
Thanks tqft :)

That is indeed a smarter way of doing things.
Another way of achieving the same result would be:
```
sudo service udev restart
```

... some day I'll see if the wiimote needs any special configuration for Ubuntu Karmic.  But now I'm in too much of a lazy mood :P

---

### Post by Gidskid on 2009-12-25
I have a glovepie script and want to know if i can convert it to a Cwiid Config File? It requires 2 wiimotes which is another complication. 



Thanks


G

---

### Post by thelethargarian on 2009-12-28
I have read through most of this thread, but I can not find out how to use the D-pad to move the cursor smoothly when you hold it. I find that using the ir and sensor bar mode isn't completely accurate for small buttons, so I would like to be able to use the D-pad once I get in the range with the ir mode.

I've tried
```

Wiimote.Dpad.X    = REL_X
Wiimote.Dpad.Y    = -REL_Y

```, but that just moves one pixel per button press.

Thanks,
thelethargarian

---

### Post by thelethargarian on 2010-01-09
Nobody knows?

---

### Post by acatak on 2010-10-20
old thread, i know but will it work on 10.10?

---

### Post by emoguitarist06 on 2010-11-04
> **acatak said:**
> old thread, i know but will it work on 10.10?

Bump

will it? :)

---

### Post by ibanezguy19 on 2010-12-18
i want to assign the buttons on the wiimote to keyboard combinations(like CTRL+C).  How would I go about doing this?

---

### Post by inate on 2011-03-21
Help, I'm stuck at the wminput 00:1A:1A:10:6C:0D part when I type this in it tells 
unable to open uinput
:confused:

---

### Post by hfxdesign on 2011-04-25
For now, ignore the uinput error, it starts it up (i checked the code). It's just a dev error, they forgot to check if the file exists before executing, I'm new to c++ but have had design experience in other languages, so I'm trying to find a workaround, the closest thing I've come to for newer ubuntu is removing "/dev/input/uinput" from the list. I'll keep looking into this. For those of you having compile errors, I had them too, they are due to missing headers in some of the files. Do some research on it and edit the .hpp files that are throwing errors and add the includes (most are stdio.h and stdint.h) until you get it compiled.

UPDATE: I fixed the uinput error, here's how:

1. Open the uinput.cpp file in your source folder
2. Find this statement near the top of the file:
```
if ((fd = open(uinput_filename[i], O_WRONLY | O_NDELAY)) >= 0)
        {
          break;
        }
      else
        {
          std::cout << "Error: " << uinput_filename[i] << ": " << strerror(errno) << std::endl;

```
3. Change to this:
```
if ((fd = open(uinput_filename[i], O_WRONLY | O_NDELAY)) >= 0)
        {
          std::cout<< "uinput (" << uinput_filename[i] << ") started" <<std::endl;
          break;
        }
      else if ( i >= 2 )
        {
          std::cout << "Error: " << uinput_filename[i] << ": " << strerror(errno) << std::endl;

```

That will fix the error messages, just a little bit of debugging.

---

