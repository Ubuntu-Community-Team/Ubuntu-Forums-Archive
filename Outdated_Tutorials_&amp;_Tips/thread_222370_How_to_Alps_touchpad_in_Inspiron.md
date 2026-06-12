---
title: "How to: Alps touchpad in Inspiron"
date: 2006-07-24
forum: Outdated Tutorials &amp; Tips
---

### Post by the_blue_pill on 2006-07-24
Prologue: I actually posted this message before, but since people remained clueless on some points already addressed here I thought it might be more useful in the howto collection. Enjoy.  
======================
I know there are several dozens of Howtos for touchpad woes but I thought one more wouldn't hurt. But seriously, to get mine working I had to make use of several of those guides, which generally were on specific details, such as how to turn off tapping etc. I thought a more general version for the Alps touchpad I'm using could be helpful. The guide is admittedly  a 'bit' long but that's because I felt people would fare better if they knew the reasons for tweaking this parameter or that. I'm not an expert though, so feel free to correct or add to this guide. For the record, I have an Inspiron 8600 and running breezy. Here goes:

**-------Preliminary checks: Know thy enemy**
First off, check if the evdev module is available and loaded.
Type:
```
lsmod |less
```
and scroll down to see if evdev is there. 

Next, look in the 'devices' file with your favourite text editor 
```
vi /proc/bus/input/devices
``` 
to see if your touchpad is detected correctly, you should find several related lines like:
I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse1 event2 ts1
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003
As you can see, the touchpad is correctly identified here. Write down the handlers line, we'll use this information later.
As an additional tidbit, the serial and USB mice should show different handlers, e.g. for mine:
I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="PS/2 Mouse"
P: Phys=isa0060/serio1/input1
H: Handlers=mouse0 event1 ts0 
...
I: Bus=0003 Vendor=0d62 Product=a100 Version=0300
N: Name="Darfon USB Optical Mouse"
P: Phys=usb-0000:00:1d.0-1/input0
H: Handlers=mouse2 event4 ts2 
Sadly, the additional devices are handled somewhat arbitrarily, and this causes problems as I'll refer to later on.

Open up the xorg log file:
```
vi /var/log/Xorg.0.log
```
and see if the synaptics driver is loaded. In mine, I see:
(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
        compiled for 4.2.0, module version = 1.0.0
        Module class: XFree86 XInput Driver
        ABI class: XFree86 XInput driver, version 0.3

Normally, there should be no problem with these preliminary checks. If there is, refer to the following discussion for possible solutions:

[http://web.telia.com/~u89404340/touchpad/trouble-shooting.txt](http://web.telia.com/~u89404340/touchpad/trouble-shooting.txt)


**----------------Delving into xorg.conf: The beast within**
Almost every parameter related to the touchpad performance is (or will be. once you're done) has to be in /etc/X11/xorg.conf
Make sure that you backup this file before doing anything! It's very easy to lose track of the different blocks, lines and entries and screw the file so badly that your X session won't start! Experience speaks here...
Anyway once you've backed it up, open up your xorg.conf
```
sudo vim /etc/X11/xorg.conf
```

You should first find an entry of Section "InputDevice" with driver "synaptics". This is where we make most of our changes. If this is the first time you're editing this section, you'll see the default settings. In mine I see the following lines:

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Looks short and elegant. Except that (surprise, surprise!) it doesn't work. My edited version is below. I'll try to explain in detail what the changes mean.
Section "InputDevice"
        Identifier      "Alps Touchpad"
        Driver          "synaptics"
        Option          "AlwaysCore"
        Option          "Protocol"              "event"
	Option          "Device"                "/dev/input/event2"
        Option "LeftEdge" "120"
        Option "RightEdge" "910"
        Option "TopEdge" "120"
        Option "BottomEdge" "650"
        Option "FingerLow" "10"
        Option "FingerHigh" "15"
        Option "MaxTapTime" "300"
        Option "MaxTapMove" "110"
        Option "ClickTime" "0"
        Option "VertScrollDelta" "10"
        Option "HorizScrollDelta" "0"
        Option "MinSpeed" "0.45"
	Option "MaxSpeed" "0.95"
        Option "AccelFactor" "0.015"
	Option "EdgeMotionMinSpeed" "40"
        Option "EdgeMotionMaxSpeed" "40"
        Option "UpDownScrolling" "1"
        Option "CircularScrolling" "0"
        Option "CircScrollDelta" "0.1"
        Option "CircScrollTrigger" "2"
        Option "SHMConfig" "false"
EndSection



 
First line under the InputDevice header is the identifier. Don't bother much about it - it doesn't matter what it says BUT it should be exactly the same as what is written towards the end of the file, in the Section "ServerLayout". So if you name your touchpad 'foopad' in the section above you should change it to that in the ServerLayout section too. Thus mine has the following line:
Section "ServerLayout"
       ... 
       InputDevice     "Alps Touchpad"
EndSection

The second line is the driver to be used. That's fine too. Some people have recommended to include the line
Load "synaptics" 
in the Section "Module" upstairs but mine works happily without it.

The next three lines are the most diabolical of all, and in general information available in the net is vague or worse, contradictory. Suffice to say that in my configuration, these three lines have to be EXACTLY what I posted here or the touchpad won't work. On a brighter note, if you get these three lines to work correctly, the rest is really easy and victory shall be yours. So if my configuration doesn't work straight out of the post for you, you'll need to play with them, i.e. edit xorg.conf then restart x (ctrl-alt-backspace). Repeat, rinse, next cycle and so on. To see if the touchpad configuration communicates successfully with the operating system, edit the option 
  Option "MaxTapTime" "300"
to
  Option "MaxTapTime" "0"
This will disable tap-to-click if linux is at all aware of your changes. And yes that is how you disable tapping, but if your other parameters are optimized, you really don't need to disable this feature. Read on.

Simply put I don't know what the "AlwaysCore" option means. You can try to sort it out from this link:

[http://www.tldp.net/HOWTO/Wacom-Tablet-HOWTO-5.html](http://www.tldp.net/HOWTO/Wacom-Tablet-HOWTO-5.html)

Scroll down to 5.12 Device Modes extension and see if you can make some sense out of it.
 
The protocol option refers to the method used by the kernel to cope with the input. Ideally, auto-dev should take care of everything but it doesn't. So I set it to 'event' 

The Device option should point to the handler for the touchpad. Recall that these handlers are reported in the /proc/bus/input/devices file
Mine had event2 as the handler so that's what ended up in my xorg.conf 
Though I haven't tried, it is mentioned that one could also use the other handler(s) e.g. 'mouse1' for this line.


**---------------- Optimizing parameters: The coup de grace**
Hopefully, now linux is aware that you're trying to do something with the touchpad and is reacting to it. Don't let the plethora of following options intimidate you: many are not essential and you'll be pleasantly surprised to see that you can actually teach your touchpad some neat tricks. Mine didn't support scrolling under windows for example and now it does!

For in depth explanation of the parameters, refer to

[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)
[http://www.tctwest.net/~mlewis00/XF86Config-4.synaptics](http://www.tctwest.net/~mlewis00/XF86Config-4.synaptics)

I'll just cover the basics. The left,right, bottom and top edge parameters - as you might guess - set the coordinates for the corners of the touchpad. More importantly, these determine where the edges and therefore edge events, such as scrolling, start. For instance when I declared the right edge of the touchpad as 840, the scroll region occupied almost a third of the pad, and I had to expand the right edge to above 900 for comfortable motion.

The infernal: " selecting and tapping by mistake while moving the cursor " problem is embedded in the MaxTapMove option. It means the maximum amount of movement 'noise' that is allowed when a tap is detected. Setting this lower will preclude tapping when there is motion.

The tap-and-drag functionality can be enabled by the MaxTapTime parameter. You might have noticed that when you attempt to drag something, your finger lingers on the pad, so a higher time is required to allow the detection of the second 'drag' tap.
 
VertScroll  and HorizScroll delta are self explanatory. If scrolling is enabled, for instance by: Option "UpDownScrolling" "1", these determine the scrolling distance while your finger is sliding down the pad. 

The MinSpeed, MaxSpeed and AccelFactor work in cohort to determine the speed of your pointer. Adjust these to your liking.

The EdgeMotion speed options dictate the rate of effects that occur when you're at the edge. e.g. when you drag an icon across the screen and you reach an edge, the icon will appear to 'jump'. The higher the parameter value, the bigger that jump is.

Finally the option:  Option "SHMConfig". Supposedly the effect of this is to toggle userspace configuration through an interface such as ksynaptics. It didn't work for me but you might give it a shot and set it to 'true'


**---------------------The glitch: A parting shot**
Well it wouldn't be linux if everything just worked would it? As I mentioned before, when you plug in a usb mouse, linux nicely assigns new handlers to it and your event numbers remain intact. When you plug it out, the entry is deleted as can be seen from the devices file. Now, when you boot your linux kernel WITH the usb mouse plugged in, linux decides to assign the portable usb mouse the first event number for an inexplicable reason, thus changing the event numbers. So the handlers for the touchpad in my example become mouse1, event3 and so on. Why a detachable device is given priority over a permanently fixed touchpad is beyond my comprehension. Worse, the entry doesn't disappear when you unplug the usb mouse, or even when you restart X! You have to restart linux get rid of the entry.

Fortunately there is a workaround. Just keep your mouse unplugged while booting and attach it only after you get to the login. That way everything works proper.

-----------


So that's it. It's really sad that a treatise is needed to get something as elementary as a touchpad to work but I guess that's how it goes. Hopefully dapper has better handling.

---

