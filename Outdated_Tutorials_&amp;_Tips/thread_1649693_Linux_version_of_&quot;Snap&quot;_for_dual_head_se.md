---
title: "Linux version of &quot;Snap&quot; for dual head setups"
date: 2010-12-20
forum: Outdated Tutorials &amp; Tips
---

### Post by iverasp on 2010-12-20
Hi,

I found a set of commands for use with compiz to resize the  current active window to cover half the screen from left or from right  (equivalent to "Snap" in Win7) on this webpage: [http://www.clickonf5.org/linux/use-aero-snap-windows7-feature-ubuntu/6956](http://www.clickonf5.org/linux/use-aero-snap-windows7-feature-ubuntu/6956)

However,  on my dual head setup this would not work as X handles both the screens  as one and TwinView (for those using nvidia cards) takes care of  telling GNOME which display to maximize the current window on etc (as  far as I understand it. I could be wrong).

This bash script finds  the location of the mouse pointer and moves the active window to that  display, taking the argument "right" to move it to the right half of the  screen and with none arguments moves it to the left side of the screen. It needs to be modified if the displays are not of the same  resolution. The Edge Binding solution with compiz (from the link above)  is of no use as, again, X handles both screens as one. Instead use  keyboard shortcuts. Execute the script with the argument "right" (i.e.  "/usr/sbin/windows_arrange right") to move the window to the right side  of the screen and without any arguments for the left side of the screen.

You would also need wmctrl and xdotool so from a terminal type:
sudo apt-get install wmctrl xdotool

Make a script by pasting the following code:
```
#!/bin/bash
DISP_WIDTH=1920
HALF=$(($DISP_WIDTH/2))
X_POS=`xdotool getmouselocation | cut -f 2 -d ':' | cut -f 1 -d 'y'`

if [[ "$X_POS" -le "$DISP_WIDTH" ]]; then
  X_ZERO=0
else
  X_ZERO=$DISP_WIDTH
fi

if [[ "$1" = "right" ]]; then
  X_ZERO=$(($X_ZERO + $HALF))
fi

wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$X_ZERO,0,$HALF,-1
```sudo gedit /usr/sbin/windows_arrange
Paste the above code
Change the value of DISP_WIDTH to your setup (the horizontal resolution of one of your displays)
Save and exit gedit
sudo chmod +x /usr/sbin/windows_arrange

---

