---
title: "Browser window is cut in half (Chrome)"
date: 2013-09-06
forum: New to Ubuntu
---

### Post by gabmuks on 2013-09-06
Hello and good day.

I don't understand why I can only see one half to on quarter of my browser window. It has been getting worse over the last six months.
Makes it really difficult to do anything on line when I can only view
a small portion of a web page at a time.
Does anyone know how to fix this??
Also I am unable to close most offline applications (like ubuntu tweak) because there is no longer a "Close" box on the screen.
I have to "Restart" Ubuntu just to close a program.

This all happened about six months ago after some Ubuntu updates.
Does anyone know how to fix these problems?

---

### Post by bkline on 2013-09-06
This sounds an awful lot like the problems we ran into with xfce, described here:

[http://ubuntuforums.org/showthread.php?t=1765417](http://ubuntuforums.org/showthread.php?t=1765417)

There are some workarounds included in the thread.  Good luck!

---

### Post by gabmuks on 2013-09-06
When this problem first started, I was able to hold down left mouse button and drag the screen to a larger size.
After while that was no longer possible. The screen has continued to shrink. There is also no "Min/Max/Close" bar at the top of the browser window like there used to be.
I have tried re-installing Chrome. That had no effect on the problem at all. Have tried Firefox but that makes it worse because I have to "Restart" Ubuntu just to close FIrefox.
It's like Ubuntu thinks I am using an IPhone screen instead of my desktop PC.

---

### Post by Frogs Hair on 2013-09-06
Checking the zoom may be worth while if you haven't already but , the text would be extremely large if the the zoom was set high enough to cut the page in half. If you re-install without removing the old configuration file the problem won't go away.


To do this open the home folder and press Ctrl + H to show hidden folders . Locate the .config file and delete the Google Chrome file. When Chrome is re-installed there will be a new configuration file and this will hopefully solve the problem.

---

### Post by gabmuks on 2013-09-06
> **bkline said:**
> This sounds an awful lot like the problems we ran into with xfce, described here:

[http://ubuntuforums.org/showthread.php?t=1765417](http://ubuntuforums.org/showthread.php?t=1765417)

There are some workarounds included in the thread.  Good luck!


THANKS!!!

That worked great!!

Alt f2 and then:  [COLOR=#000000][I]xfwm4 --replace

Now I was able to drag the window to full screen.
Also have a Min/Max/Close bar on top again.

Hope I can remember this fix.

Thanks again.[/I][/COLOR]

---

### Post by Jonathan Precise on 2013-09-06
> **gabmuks said:**
> THANKS!!!

That worked great!!

Alt f2 and then:  [COLOR=#000000][I]xfwm4 --replace
[/I]
Now I was able to drag the window to full screen.
Also have a Min/Max/Close bar on top again.

Hope I can remember this fix.

Thanks again.[/COLOR]

Please add this to your start-up programs. Then mark it as solved.

---

### Post by Besmir_Zekaj on 2013-09-06
Hi,

1. Uinstall Google Chrome
2. Install it.
3. The issue must be fixed.

Zekaj Developer

---

### Post by gabmuks on 2013-09-06
Thanks for telling me to mark solved.

How can I add this to my start-up programs?

---

