---
title: "Connect to Remote Desktop on Ubuntu using Xming on Windows fails"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by tnek on 2008-10-19
Hi,

I have followed this guide: [http://ubuntuguide.org/wiki/Ubuntu:Hardy#Howto_Install_and_use_Xming_for_Windows](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Howto_Install_and_use_Xming_for_Windows)

But I can't seem to connect and get the log in screen. I use XLaunch and choose "One Window", "Open session via XDMCP", Write the correct IP-address at "Connect to host" and I leave "Indirect connextion" unchecked (but the same result happens when I check it too), and choose "Clipboard" on the next step of the wizard. Last I click Finish to start Xming.

I get an empty grey screen (as the default Xorg screen, except there is no terminal window) and I seemingly can't do anything. The guide says I should get the log in screen, but I don't. All help appreciated!

---

### Post by conrad.warmbold on 2008-11-12
Same issue here attempting to connect from Windows XP to Ubuntu 8.10.

---

### Post by 451422 on 2008-12-16
Does anyone check this stuff before releasing it to the public.  You're not the only one.  Ditto.  I have the same issue.

---

### Post by starcannon on 2008-12-16
use tightvnc on both xp and ubuntu and you'll be fine.

---

### Post by tnek on 2008-12-18
Thanks for your suggestion Starcannon. If I change the settings in Ubuntu so that I'm able to connect using tightvnc than I have to be logged in first on the Ubuntu machine, or no connection will be accepted. Do you mean to not use the built in VNC-server (even uninstall it?), install a tightvnc server and then try it?

If the above works it's at least a way to connect remotely. But it's hardly comparable to running X remotely as it for example can't handle multiple simulteneous users (please correct me if I'm wrong on that one, but I don't think I am).

And lastly. If following the instructions in Ubuntu guide does not work. Does that mean there is a problem with some packages and we should file a bug report? Or does it simple mean the guide is wrong and should be changed?

---

### Post by grognut on 2009-11-04
Hi,

I'm trying to run remote xwindows and after trying Xming for a while and not getting anywhere I tried the following

Run-> cmd to get a dos box.
locate plink, then
<path to plink>plink -X <IPaddress of remote machine> <program to run> eg nautilus

This then request user and password.
You may get a few errors in the dos box then up pops nautilus and then a desktop.
Can't work out how to get a bash command yet though.

Found this at [http://the.earth.li/~sgtatham/putty/0.58/htmldoc/Chapter7.html]("http://the.earth.li/~sgtatham/putty/0.58/htmldoc/Chapter7.html")

Hope is helps.

Cheers

---

