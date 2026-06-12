---
title: "logitech M-UAG120 7-button usb mouse problem"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by crps on 2008-09-13
I have a logitech M-UAG120 7-button usb mouse and Ubuntu 8.04. 

The 3D wheel is like a traditional mouse scrolling wheel but that has also lateral switches, left and right.
[http://211.78.161.57/res/gdsale/st_pic/0378/st-378909-1.jpg](http://211.78.161.57/res/gdsale/st_pic/0378/st-378909-1.jpg) 

The problem is that both left and right scrolling wheel buttons generate no outcome in xev so i don't know how to continue in the xorg.conf.

The other buttons work fine.

Help is greatly appreciated.

---

### Post by phidia on 2008-09-14
Take a look at the many button mouse wiki [here]("https://help.ubuntu.com/community/ManyButtonsMouseHowto") and hopefully that will provide the answer for you.

---

### Post by crps on 2008-09-14
thanks for the reply phidia, that tutorial would be very helpful in the next step, that is after I manage to find all the buttons numbers. I've tried xev and imwheel so far but still, the horizontal scroll buttons generate no outcome.

---

### Post by phidia on 2008-09-14
I think you're going about this the wrong way. If i don't have an xorg.conf or have the wrong one for my hardware I won't see any x events either.

Just try setting up xorg.conf for a many button mouse per the guide. Your xorg.conf is where it all starts.

From man xev:
> DESCRIPTION
       Xev creates a window and then asks the X server to send it events when&#8208;
       ever  anything  happens to the window (such as it being moved, resized,
       typed in, clicked in, etc.).  You can also attach  it  to  an  existing
       window.   It  is  useful  for seeing what causes events to occur and to
       display the information that they contain; it is essentially  a  debug&#8208;
       ging and development tool, and should not be needed in normal usage.
 
If xev is checking the xserver for those events it can't get any if your xorg.conf isn't configured correctly.

---

### Post by cmoman on 2008-09-17
I'll be interested to see how you get on.
I've got exactly the same mouse and I've played around a little with editing the xorg.conf
```
Option "Buttons" "7"
``` and watching the xorg.log but so far xev and imwheel have yielded little result.

---

### Post by blackyfreud on 2010-10-21
I know this is an old thread, but I just had the same problem (using crunchbang - based on ubuntu) ... I managed to get the vertical left and right scrolling going with the following xorg.conf entry for the V100 Optical Logitech Mouse (M-UAG120)

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"Logitech USB Optical Mouse"
	Option		"Buttons" "8"
	Option		"ZAxisMapping" "4 5"
	Option		"ButtonMapping" "1 2 3 6 7 8 4 5"
	Option		"Emulate3Buttons" "no"
EndSection

```

Hope it's of use to someone.

---

