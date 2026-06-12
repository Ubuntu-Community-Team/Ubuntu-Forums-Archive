---
title: "How to make your back and forward buttons work (The real solution)"
date: 2006-06-08
forum: Outdated Tutorials &amp; Tips
---

### Post by mindwarp on 2006-06-08
This will let you actually make your back and forward buttons work on your intellimouse microsoft mice.  There is another article on here, but involves kludgy xmodmap and other confusing steps.  This is a much simpler solution:

**Step 1:**
Change to the directory where the xorg.conf file is located (this file controls your display)
```
cd /etc/X11/
```

**Step 2:**
Edit the file.  In order to edit the file, you will need root permissions which you can aquire through use of the "sudo" command
```
sudo gedit xorg.conf
```

**Step 3:**
Find the location in the file that has your current mouse configuration.  You can go to search -> "Configured Mouse" and you should see a mouse configuration and it probably says a line like "Option "Device" "/dev/input/mice"".  Highlight the section, and replace it with this
```

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "ButtonMapping" "1 2 3 6 7"
EndSection

```

**Tested working with Dapper 6.06 on Jun 8th 2006, using a Intellimouse Explorer USB mouse.**  Please email changes to [email]thisdying_nospam_dream@gmail.com[/email]

---

### Post by nomail on 2006-06-10
Doesn't work for me....](*,) 
using Microsoft IntelliMouse Explorer 3.0A USB

----

edited:
sorry, it works with firefox. But sadly not with Opera....back to imwheel for me

---

### Post by mindwarp on 2006-06-10
Yes this only works with browsers that use the forward and back buttons in their standard configuration.

---

### Post by Angellis_ater on 2006-06-10
When I tried it and restarted X it all crashed. Fortunately enough I JUST learned how to undo changes to the xorg.conf

---

### Post by mindwarp on 2006-06-10
Post your /var/log/ file with xorg in the name here so we can see why it crashes, these changes will 100% not crash X unless there is a bug with the config parsing.  Also list the model / connection type of your mouse.

---

### Post by Visceral Monkey on 2006-06-10
Yea, this doesnt work for me either.

---

### Post by edwing on 2006-06-10
After much fiddling, this worked for me (you will get to install imwheel via apt):

/etc/X11/xorg.conf

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Emulate3Buttons"       "false"
        Option          "Buttons"               "11"
        Option          "ZAxisMapping"          "4 5"
        Option          "Resolution" "100"
EndSection

```

/etc/X11/imwheel/startup.conf

```

IMWHEEL_START=1
IMWHEEL_PARAMS="-k -b "0089""

```

/etc/X11/imwheel/imwheelrc

```

"^firefox$"
None, Thumb1, Alt_L|Left
None, Thumb2, Alt_L|Right

```

/etc/X11/Xsession.d/60imwheel_start-imwheel

```

# Starts the imwheel process.
. /etc/X11/imwheel/startup.conf
if [ "$IMWHEEL_START" = "1" ]; then
        /usr/bin/imwheel ${IMWHEEL_PARAMS}
fi

```

---

### Post by mindwarp on 2006-06-10
The whole point of this is as long as you have a microsoft intellimouse explorer USB and use firefox, imwheel isn't needed.  The other thread already covers the imwheel method, no need to regurgitate it here.

---

### Post by Visceral Monkey on 2006-06-10
I stand corrected, this *does* work for me now. Thanks!

---

### Post by nomail on 2006-06-12
mindwarp could you explain what exactly this line does? Just curious;) 
```
Option      "ButtonMapping" "1 2 3 6 7"
```

---

### Post by gibson on 2006-06-12
Worked for me.

Thanks dude, a really neat and tidy solution!

---

### Post by Somenoob on 2006-06-12
Works perfectly here.

thanks,

---

### Post by aktiwers on 2006-06-12
Somehow didnt work on my mouse. Just made it unable to do much. Thanks anyways :)

---

### Post by CyberRaven on 2006-06-12
Worked like a charm with my Logitech Cordless Optical Mouse (which is part of the Logitech UltraX Cordless Media Desktop).

Lots easier than my earlier solution with xmodmap and stuff!
So, thanks!

---

### Post by David Valentine on 2006-06-28
Also worked for me.  Thanks for the elegant HowTo!

---

### Post by NT4usB on 2006-06-28
We'll try this out on a Mx310 tonight. Looks to be a ton easier than the other howto.
btw, any idea how to change the scroll wheel from the default 6 lines or whatever it is, to scroll a page at a time?
I'm wearing my scroll wheel out browsing these forums!

---

### Post by BluDragon on 2006-06-28
[QUOTE=nomail]mindwarp could you explain what exactly this line does? Just curious;) 
```
Option      "ButtonMapping" "1 2 3 6 7"
```[/QUOTE]

I believe that that's the magic line which adds support for your left and right buttons. 1 is left click, 2 right click, 3 mouse wheel/button, 6 left side button, 7 right side button. Don't quote me on this though as I am just talking out of my ***.

---

### Post by jsma on 2006-06-29
[QUOTE=BluDragon]I believe that that's the magic line which adds support for your left and right buttons. 1 is left click, 2 right click, 3 mouse wheel/button, 6 left side button, 7 right side button. Don't quote me on this though as I am just talking out of my ***.[/QUOTE]
I asked about ButtonMapping on the xorg mailing list (btw, I think it's intended for developers only...there doesn't appear to be a user forum...so my newbie-ness barged right in the middle of their developer discussions :blush: ). Anyway, one person replied:
"xev and other X applications see the logical buttons. They expect 1 to be select, 2 to be paste, 3 to be context menu, 4 scroll up, 5 down, 6 left, 7 right."
So, I think I get some of it finally. ButtonMapping maps physical buttons on the mouse to logical buttons. The places from left to right are the physical buttons and the numbers in those places are the logical buttons. To be more clear, to get standard right-handed mouse configuration we use:
```
"ButtonMapping" "1 2 3 6 7"
```
This makes button '1'(the button under your index finger if you're right-handed) map to the 'select' action and button '3'(the button under your middle finger) map to the 'context menu' action. So, this means to get left-handed mouse configuration we simply switch:
```
"ButtonMapping" "3 2 1 6 7"
```
I just tested it and this is exactly what happens. I was also told that the PS/2 driver we're using only has fields for 5 physical buttons, so any numbers after "1 2 3 6 7 ..." wouldn't mean anything (may cause problems even, haven't tried). This is also why xev never sees any action from my tilt-wheel. If I wanted to be crazy (and usually I do, just not in this case) I could map the wheel to forward/back with ```
"ButtonMapping" "1 2 3 4 5"
```

So I don't know what kind of can of worms would be opened by using evdev driver (which apparently I have to use to get the tilt wheel working on my mouse). The examples I've seen using evdev cut out any ButtonMapping arguments. My back/forward buttons are working perfectly with the solution at the top of this thread, so I'm hesitant to go breaking things.

---

### Post by mgmiller on 2006-07-03
This is just what I was looking for.  I used to use the imwheel solution in Hoary, but didn't like the complexity of it and didn't bother in Breezy.  Once Dapper came along, I noticed the back and forward buttons weren't mapped to anything anymore, like they used to be in the stock hoary and breezy installs.  Anyway, I have system that was a clean install of Breezy, that was updated to Dapper and am using a Microsoft Intellimouse Optical 1.1A USB mouse (black model) and this worked perfectly after logging out and restarting x.  I think it would be a good idea to tell your system that this is an edited xorg.conf, so it updates itself properly in the future.  From a terminal run     sudo dpkg-reconfigure -phigh xserver-xorg

This info is from the xorg.conf file itself and the instructions have changed a bit since Breezy.  I have found if you don't do this, then if you try to update video cards, drivers, etc, the system balks at the commands to update the file and you have to keep editing it manually.

Thanks for a great little tip.  (IMO Dapper really should do this kind of hardware detection by default)

---

### Post by bocmaxima on 2006-07-03
Weird, this worked for me the first time I did it, but on my new install it doesnt.. : /

---

### Post by s3ppel on 2006-07-06
Thx for the Howto. I got my Razer Diamondback to work with just a few modifications:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option          "Buttons"               "7"
        Option          "Resolution"            "1600"
	Option		"ZAxisMapping"		"4 5"
	Option		"ButtonMapping"		"1 2 3 6 7"
	Option		"Emulate3Buttons"	"true"
EndSection

---

### Post by Glueeater on 2006-07-07
Works flawlessly with my Logitech G5.

---

### Post by DarkDancer on 2006-07-07
Worked for me with my logitch mx-310. Thanks I have been missing the back and forward buttons... ;)

---

### Post by handy on 2006-07-15
I used it on Breezy & it works for me perfectly on Dapper!! :KS 

Mouse:  IntelliMouse Explorer, no version #'s written on it, had it for years, probably the first one.  I'm running it on USB.

---

### Post by PingunZ on 2006-07-15
The first of the mouse-howto's that worked for me ;)

TY :KS 

Grtz PingunZ

---

### Post by jabooty on 2006-11-01
Maybe you guys can give me a little insight here.  

I got a HP mouse (cheapo at walmart), and it's a 5-button wheel job.

However, xev shows what I would expect buttons 6 and 7 as 8 and 9 (there are no buttons that will register as 6 and 7).  These buttons aren't on the side of the mouse, like normal 6 & 7 buttons would be, but are on top of the mouse, right behind the wheel.  Not that that makes any difference.

I tried editing my xorg.conf, and this is what I did, but nothing seems to work.  Can you please look it over and see if I just plain screwed up something?

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons" "9"
	Option		"ButtonMapping" "1 2 3 9 8"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```

Yes, I intended to make 9 before 8.  It just makes sense to me to have the "top" button be the "back" button.

---

