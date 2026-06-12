---
title: "Keeping the SynPS/2 Synaptics TouchPad disabled"
date: 2014-10-31
forum: New to Ubuntu
---

### Post by tuxbonewits.com on 2014-10-31
**There is not much to not love about Ubuntu 14.04.1 LTS Trusty Tahr OS**.  
I have been using it since 20141004. Currently dealing with an anoyance and would like a bit of help.

Firstly, My data;
HP Pavillion g7 - 2269wm
AMD Quad-Core A8-4500M Accelerated Processor
17.3" diagonal HD+ BrightView LED Display
Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7640G]
Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
500 GB HDD
DVD A DS8A9SH
6144MB DDR3 SDRAM
DVD Optical Drive

I have tried every fix I can find in the forums and nothing seem to be permanent. 
[COLOR=#ff0000]The prob is keeping the SynPS/2 Synaptics TouchPad disabled.[/COLOR]

I have tried the simple; [COLOR=#0000ff]System Settings -> Mouse & Touchpad -> switch OFF[/COLOR].  It works for a while.

I have tried in the terminal[COLOR=#0000ff] xinput set-prop xx "Device Enabled" 0[/COLOR], where xx= device id.  It works for a while.

I have tried the [COLOR=#8b4513]startup option to disable[/COLOR] it via the app, where this text is inserted; [COLOR=#0000ff]xinput set-prop xx "Device Enabled" 0[/COLOR] where xx= device id
This sorta works for a while. They all sorta work for a while. 

[COLOR=#8b4513]I have noticed that the device ID seems to change now and then[/COLOR]. 
So, I fix the script and it is disabled again for a while. 

[COLOR=#8b4513] I have also noticed that if my screen goes off (it is set for 30 minutes) that apon awakening, the touchpad is enabled again.[/COLOR]

OK, so unsure if this is two probs or if that are related.

Thanks in advance for your assistance.
[EMAIL="tux@bonewits.com"]tux@bonewits.com[/EMAIL]
69 years old and still a noob

---

### Post by JeQhdMD on 2014-11-01
Many laptops (including my Acer Timeline) allow the touchpad to be turned off/on via keyboard combo keys.   On my Acer it's the Fn (Function) key + F7.   Repeating the steps acts as a toggle (on/off, off/on).   Is there a similar combo on your laptop?   Perhaps the user manual has info?

---

### Post by tuxbonewits.com on 2014-11-02
Thanks for the reply
fn+F7 turns "caret browsing" on and off
It is apparently the only fn+func key combo I have :)

WRONG

also fn+F11 does full screen on and off

---

### Post by JeQhdMD on 2014-11-04
OK, per the HP website, your model of hp laptop has a touchpad "off/on" key.   It seems to be located just above the top edge of the touchpad . . . but maybe your specific model is different.  Anyway - - check it out and see if that works.

---

### Post by sudodus on 2014-11-04
I use the following simple bash function ***touchpad-toggle***. It has worked for me in many different laptops.

```
function touchpad-toggle {

# toggle synaptic touchpad on/off

# get current state
SYNSTATE=$(synclient -l | grep TouchpadOff | awk '{ print $3 }')

# change to other state
if [ $SYNSTATE = 0 ]; then
    synclient touchpadoff=1
    echo "touchpad OFF"
elif [ $SYNSTATE = 1 ]; then
    synclient touchpadoff=0
    echo "touchpad ON"
else
    echo "Couldn't get touchpad status from synclient"
    exit 1
fi
}
```

You can use it in many ways. I add the following text to the end of the file **/etc/bash.bashrc**

```
sudo nano /etc/bash.bashrc
```

```
alias and touchpad-toggle
---------------------------

# Appended to /etc/bash.bashrc

alias TT='touchpad-toggle'

###

function touchpad-toggle {

# toggle synaptic touchpad on/off

# get current state
SYNSTATE=$(synclient -l | grep TouchpadOff | awk '{ print $3 }')

# change to other state
if [ $SYNSTATE = 0 ]; then
    synclient touchpadoff=1
    echo "touchpad OFF"
elif [ $SYNSTATE = 1 ]; then
    synclient touchpadoff=0
    echo "touchpad ON"
else
    echo "Couldn't get touchpad status from synclient"
    exit 1
fi
}

####

alias TT
```

and then I can use ***TT*** to toggle the touchpad on/off from a terminal window. If you want to have it switched off all the time, you can simply use

```
synclient touchpadoff=1
```

in an executable file in your ***autostart***

---

### Post by tuxbonewits.com on 2014-11-05
[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1841810_1.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1841810") 				 				 					 						 	[**[COLOR=#000000]JeQhdMD[/COLOR]**]("http://ubuntuforums.org/member.php?u=1841810")

Thanks for the reply.
Indeed it has this function, IF you are using Win8
Does not work with Ubuntu :(

---

### Post by tuxbonewits.com on 2014-11-05
[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1499021_3.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1499021") 				 				 					 						 	[**[COLOR=#C61919][B]sudodus**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1499021")
Thanks for the reply.

I have already created a script to set the touch pad off at startup.
Touchpad is always off at startup, but; 
somewhere during the day, several times on some days;
 it flips back on. Sometimes it is after the screen blanks. 
Sometimes after awaking. How can I expect another script to work?

The ID seems to change randomly. If I re-write the startup script with the new ID
it works for a day or two and then it is back to fun and games.

This is the result of [COLOR=blue]xinput list today;
[/COLOR]&#9121; Virtual core pointer                                    id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad            id=14    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                          id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard            id=5    [slave  keyboard (3)]
    &#8627; Power Button                                   id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                       id=7    [slave  keyboard (3)]
    &#8627; Power Button                                  id=8    [slave  keyboard (3)]
    &#8627; UVC Camera (046d:0804)                 id=9    [slave  keyboard (3)]
    &#8627; HP Truevision HD                            id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard           id=13    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                             id=15    [slave  keyboard (3)]
    &#8627; HP Wireless hotkeys       

When I started this thread SynPS/2 Synaptics TouchPad was id=12
**While trying to align the above columns, it did it again!**
Somehow I don't think another script will work any better, but;
Thank you for your advise.

I think the question is why does the ID change randomly?
And why does the switch change itself randomly?
This time when it flipped the touchpad back on;
the ID did not change!

---

### Post by tuxbonewits.com on 2014-11-05
[**[COLOR=#C61919][B]sudodus**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1499021")

This is my current startup script
**xinput set-prop 14 "Device Enabled" 0**

I will try the script you posted **synclient touchpadoff=1** 
and let you know how it goes.

Thank you

---

### Post by sudodus on 2014-11-05
> the question is why does the ID change randomly

I don't know the answer to that question, or if is normal. I'm looking forward to your result with

```
synclient touchpadoff=1
```

See this link for more details

[https://help.ubuntu.com/community/SynapticsTouchpad/ShortcutKey](https://help.ubuntu.com/community/SynapticsTouchpad/ShortcutKey)

---

### Post by tuxbonewits.com on 2014-11-08
sudodus

We're on day 3 of the expirment using **synclient touchpadoff=1**

in the startup script
and all seems to be working 
the way one's hopes it will work.

Thank you again for your wise input.
I will close this thread.
Thbanks again to all who responded!

---

### Post by sudodus on 2014-11-08
I'm glad it works for you :-)

It is enough that you marked this thread as SOLVED. We need not close it.

---

