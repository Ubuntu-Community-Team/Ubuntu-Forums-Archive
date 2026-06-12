---
title: "wxPython no Menubar"
date: 2012-10-13
forum: Programming Talk
---

### Post by wd40bomber7 on 2012-10-13
Any interface created with wxPython shows up without a menubar.

Yes I've seen the thread
[http://ubuntuforums.org/showthread.php?t=2004101](http://ubuntuforums.org/showthread.php?t=2004101)

but none of the solutions presented there worked for me. 

My setup:
Downloaded a clean Ubuntu 12.04 Desktop 64 bit iso, used a usb drive to install it to my computer.
Ran 
sudo apt-get update
sudo apt-get install python-wxgtk2.8
sudo apt-get upgrade
python myapp.py

That's it. I haven't even taken the time to finish setting up ubuntu. Oh yeah, I did try restarting a few times. 

I did try the solutions presented in the other thread to no avail.
Anyone have any ideas?

Edit: Forgot to mention the strangest thing. "sudo python myapp.py" works perfectly. It shows a menubar and everything. Why would that work? So confused.
Edit2: More information

The main change I could think of that happens when running a command with sudo is permissions so using lsof I found that when my python program is run with/without sudo they seem to open different libraries. That doesn't make any sense to me because I'd think a program would either need a library or it wouldn't, but nonetheless they did.

The files opened by "sudo python myapp.py" that were not opened by "python myapp.py" were:
/root/.cache/dconf/user
/root/.config/dconf/user
The files opened by "python myapp.py" that were not opened by "sudo python myapp.py" were:
/lib/x86_64-linux-gnu/libdbus-1.so.3.5.8
/lib/x86_64-linux-gnu/libudev.so.0.13.0
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
/usr/lib/x86_64-linux-gnu/gio/modules/libgvfsdbus.so
/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/engines/libmurrine.so
/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
/usr/lib/x86_64-linux-gnu/gtk-2.0/modules/libcanberra-gtk-module.so
/usr/lib/x86_64-linux-gnu/gvfs/libgvfscommon.so
/usr/lib/x86_64-linux-gnu/libatk-1.0.so.0.20409.1
/usr/lib/x86_64-linux-gnu/libcairo.so.2.11000.2
/usr/lib/x86_64-linux-gnu/libcanberra.so.0.2.5
/usr/lib/x86_64-linux-gnu/libcanberra-gtk.so.0.1.8
/usr/lib/x86_64-linux-gnu/libdbusmenu-glib.so.4.0.13
/usr/lib/x86_64-linux-gnu/libdbusmenu-gtk.so.4.0.13


As you can see there are several things that list "menu" in them. Perhaps one of them is responsible? This bug is driving my crazy...

---

