---
title: "&quot;cannot load library&quot;"
date: 2011-12-07
forum: New to Ubuntu
---

### Post by corncob on 2011-12-07
My Canon pixma mp640 network (ethernet cable to router) works fine on 10.04 but I can't get it to work on 11.10 installed in the same computer.  The driver (cnijfilter-) is installed and it appears to be recognized but just tells me print job aborted --cannot load library.  What library is it talking about and what can I do?  Also, I've never been able to scan (xsane, simple scan) into the computer although my wife does it wirelessly from her windows computer.

---

### Post by bluexrider on 2011-12-07
different kernels between 10.04 and 11.10 did you look for a newer driver as this may be your issue

---

### Post by bluexrider on 2011-12-07
looks this thread is marked solved. may have some useful info 

[http://ubuntuforums.org/showthread.php?t=1313945](http://ubuntuforums.org/showthread.php?t=1313945)

---

### Post by corncob on 2011-12-08
> **bluexrider said:**
> looks this thread is marked solved. may have some useful info 

[http://ubuntuforums.org/showthread.php?t=1313945](http://ubuntuforums.org/showthread.php?t=1313945)

Thanks!  It looks like I have a lot of reading to do.

---

### Post by ussher on 2012-01-09
Any luck fixing it?  I have the exact same issue.

The linked thread starts by talking about "Karmic Koala"  which was a much older release than 11.10.

---

### Post by corncob on 2012-01-10
Everything is working now including the scanner.  It seems that I had selected it as 'printer' and not 'network printer'.  Although there is a workaround involving the option '--force-architecture' (or something like that) it seems that the driver only works on 32 bit Ubuntu.

---

### Post by pacharanero on 2012-11-25
Hi, just thought I'd post a possible solution to this problem.

I struggled for a while with the "cannot load library" error, which suddenly started a few days ago. Before this I had been printing without problems. Setup is: Xubuntu 12.04 64bit and a Canon MP560 Pixma via WiFi.

(I had a variety of weird errors suddenly start on the same day, this was the day I experimented with a session in Gnome Classic. I think the Gnome session must have changed a few settings in various config files which knobbed up my printing, among other things - such as my font rendering etc)

Reinstallation of CUPS, the cnij printer drivers, and deleting and reinstalling the printer made no difference at all.

The printer could be installed using the printer manager, it was auto-detected.

But it was not visible using lpstat -v, which gave the error "unable to unlock gnome-keyring" or something similar.

**Solution**: sudo gedit this file */etc/xdg/[I]autostart*/*gnome*-*keyring*-pkcs11.desktop[/I]

there is a line: "OnlyShowIn=GNOME;Unity;" - this needs to be edited to add on "XFCE" (or LXDE, etc depending on the environment you're using) so it reads: "OnlyShowIn=GNOME;Unity;XFCE". I think this is just another setting that my "trial" of Gnome knobbed up.

Now lpstat -v returned
[I]device for Canon-MP560: cnijnet:/00-1E-8F-52-39-8A
device for PDF: cups-pdf:/[/I]

but printing still wouldn't work.

Following advice in the Ubuntu print troubleshooter thingy I edited the Server settings in the Printer Manager (Applications > System > Printing to run the Manager, then the Server menu > Settings)

**I enabled the option "Publish shared printers connected to this system"**

And it now works. Embarrassingly simple.


/pacharanero

---

