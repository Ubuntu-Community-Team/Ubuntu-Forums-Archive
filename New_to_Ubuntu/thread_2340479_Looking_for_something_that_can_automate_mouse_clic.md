---
title: "Looking for something that can automate mouse clicks in Firefox"
date: 2016-10-19
forum: New to Ubuntu
---

### Post by cptkludge on 2016-10-19
I am new to Linux and am trying it out to see if I can use it to replace windows (and speed up) my older Fujitsu T4210 
I have run XP since new but it seems to get slower and slower.
I have used a prog called Tiny Task to automate a series of mouse click in a loop of about one minute.
Is there anything in Linus that I can record the mouse clicks, save then than loop the recording?
Was going to use this with Firefox and Chrome but AFAICT, Chrome will not work on my 32 bit machine:( 
TIA:)
Joe

---

### Post by mastablasta on 2016-10-19
what kind of mouse click tasks? you can do most things in command line script running in background.
otherwsie is this somethign you are after?:
[SIZE=2]http://alternativeto.net/software/tinytask/?platform=linux
[/SIZE]

---

### Post by cptkludge on 2016-10-19
Thanks, I have looked at it. It may be powerful but I just want something that I can record what I have done (ala macro) thne have it loop endlessly. 
ie: LC a button, move to another location, LC, move to another location, LC, move to another location, LC,move to another location, LC,move to another location, LC,move to another location, LC. 
Then set this sequence to repeat endlessly or until interrupted. Macros seem to use keyboard and text input, whereas tinytask uses mouse location input
Thanks

---

### Post by arnomuhren-b on 2016-10-19
Probably the software package *Actiona* is something for you.
You can find it in the Ubuntu software center

---

### Post by vasa1 on 2016-10-20
> **arnomuhren-b said:**
> Probably the software package *Actiona* is something for you.
You can find it in the Ubuntu software center
Seems pretty powerful!

I've used xdotool to do something far more modest:```
#!/usr/bin/env bash
# hint: use "xdotool getmouselocation" to get values
xdotool mousemove --sync 1350 50 click 1 
sleep 0.3
xdotool mousemove --sync 1350 105 click 1
```

---

### Post by cptkludge on 2016-10-20
I'll check it out:)
Thanks

---

### Post by CantankRus on 2016-10-21
Here's a loop script using &#65532; **vasa1's** example.
```
#!/usr/bin/env bash
# hint: use "xdotool getmouselocation" to get values
## hold down Escape key to exit

while [ 1 ]; do
	sleep 0.3
	xdotool mousemove --sync 1350 50 click 1 
	sleep 0.3
	xdotool mousemove --sync 1350 105 click 1

## run "xinput" to get ID of your keyboard
## run "xinput --test <ID>" and hit Escape to check the Escape key is key[9] 
keypress=$(xinput --query-state [COLOR="#FF0000"]10[/COLOR] | grep -c "key\[9\]=down")
	if [ "$keypress" == "1"  ]
		then
		break
	fi		
done
exit 0
```
xinput will show your [COLOR="#FF0000"]keyboard ID[/COLOR]. Substitute your ID for [COLOR="#FF0000"]10[/COLOR] in the script.
eg
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] xinput**
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; DEXIN Tt eSPORTS BLACK Gaming mouse     	id=8	[slave  pointer  (2)]
&#9116;   &#8627; DEXIN Tt eSPORTS BLACK Gaming mouse     	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Wired Keyboard 600            	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Microsoft Wired Keyboard 600            	id=[COLOR="#FF0000"]10[/COLOR]	[slave  keyboard (3)]
```

This shows the result of running xinput --test [COLOR="#808080"]<ID>[/COLOR] and hitting Escape.
It will pick up the release of the Return key then shows the press and release of the Escape key[9]. 
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] xinput --test 10**
key release 36 
key press   9 
^[key release 9
```

Holding down Escape stops the script.

---

