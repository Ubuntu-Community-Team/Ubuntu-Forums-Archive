---
title: "why does firefox close on this website?"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by woodley42 on 2008-07-27
Whenever i try to go to [www.autotrader.com](www.autotrader.com) and select any of the search criteria (distance, price etc) firefox closes.

It occasionally does it on other sites like you tube but very sporadically.  For autotrader it's every time.

Anyone have any idea why this is and how to fix it?

Thanks

---

### Post by woodley42 on 2008-07-27
sorry its [www.autotrader.co.uk](www.autotrader.co.uk) not .com

---

### Post by ingeva on 2008-07-27
> **woodley42 said:**
> sorry its [www.autotrader.co.uk]("http://www.autotrader.co.uk") not .com

All it does for me is to ask for a valid UK postcode. Tried various numbers but I have no idea.

It might be useful to know what Ubuntu/FireFox versions you are using?

---

### Post by kerry_s on 2008-07-27
worked fine for me.

---

### Post by woodley42 on 2008-07-27
8.04.1 i think. I only installed Hardy Heron a few weeks ago so whatever the latest version is.  Firefox is whatever was bundled with it.

After filling in the postcode (use cv4 7al) and selecting for a distance or whatever it then crashes.

---

### Post by Joeb454 on 2008-07-27
Can you try opening a terminal (Applications &#8594; Accessories &#8594; Terminal) and running firefox from there, then post back any errors when firefox crashes.

To run firefox, simply enter ```
firefox
```

---

### Post by Troll_the_Great on 2008-07-27
I tried the link and I don't have any problems with the web site.Might be a firefox issue...

---

### Post by lswb on 2008-07-27
It may be related to flash content on the web site. The ver 10 beta 2 non-free flash player is causing firefox to crash on certain flash content. From firefox menu select Tools/Addons and see which version you are running. To see if it is the problem you can temporarily disable or uninstall it and try the site that causes crashes.

---

### Post by stevoo on 2008-07-27
Most probably flash problem.
That is what is causing the crashes.
Try removing flash and reinstalling it.
Or download the official one from adobe and install it.
If you need a how to post and will help

---

### Post by kaibob on 2008-07-27
I'm running stock Hardy Ubuntu, and the UK site works fine for me. 

To troubleshoot this issue, I would first disable Flash to see if that helps. You can do this by going to *Tools > Add-ons > Plugins*. You may also want to disable extensions, which can cause Firefox to crash.

If all else fails, you can create a new profile. To do this, enter "firefox -ProfileManager" in a terminal window.

[http://support.mozilla.com/en-US/kb/Managing+profiles](http://support.mozilla.com/en-US/kb/Managing+profiles)

If Firefox runs properly with the new profile, you can copy over your bookmark and any other user files and, after a test period, delete the old profile.

---

### Post by woodley42 on 2008-07-27
Thanks guys thats great.  The flash version is Shockwave Flash 10.0.0 d525.
Disabling it means i can now search for a new car :)

Only problem now is youtube and other sites dont work.  Somebody offered some info on how to install the adobe flash version which doesnt suffer this problem.  If you wouldnt mind posting it in terms a computer illiterate person can understand i'd be very grateful.

Or point me towards a post that has it already. Ive searched and most of the posts with instructions are beyond me with only a few weeks worth of ubuntu experience.

---

### Post by gjoellee on 2008-07-27
no problem for me...
:guitar:

---

### Post by stmiller on 2008-07-27
Flash is the culprit, not firefox. It is a constant complaint of flash in Linux. Version 10 beta crashes less now... :)

---

### Post by lswb on 2008-07-27
You can install adobe flash version 9 something from the repositories, (enable universe/multiverse/restricted, not sure which exactly is required) or, you can google and try to find version 10.0 b218. The ver 10 b525 is the one that causes crashes, ( I believe these numbers are the month and day of month of the release; Feb 18 and May 25) Probably best to uninstall the current version via synaptic first, if it shows up as being installed in synaptic. 

IIRC selecting it from synaptic or apt-get still gets a download from Adobe, but with the advantave of having the package manager keep track of the installation.

---

### Post by Merk42 on 2008-07-28
I've had Firefox crash on me on sites with Flash.  I have flash 9.0 r124 and the error was ```
Gtk:ERROR:(/build/buildd/gtk+2.0-2.12.9/gtk/gtkplug.c:182):gtk_plug_set_is_child: assertion failed: (!GTK_WIDGET (plug)->parent)
Aborted
```

Anyone know how to fix that?

---

### Post by woodley42 on 2008-07-28
i tried to uninstall using synaptic and got this error message when i opened it:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



What does this mean and how can i sort it out?

Thnaks

---

### Post by perlluver on 2008-07-28
> **woodley42 said:**
> i tried to uninstall using synaptic and got this error message when i opened it:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



What does this mean and how can i sort it out?

Thnaks

Go to apllications>accescories>terminal.  And type in ```
sudo dpkg --configure -a
```.  That should sort it out.

---

### Post by woodley42 on 2008-07-28
thanks

---

