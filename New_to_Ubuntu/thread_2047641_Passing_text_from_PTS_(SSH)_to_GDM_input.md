---
title: "Passing text from PTS (SSH) to GDM input"
date: 2012-08-25
forum: New to Ubuntu
---

### Post by dohzer on 2012-08-25
So this isn't really an Ubuntu question, more a generic GNOME/Linux one.

Is there a way to pass text from a random terminal to the GNOME Display Manager? Currently I'm logged into a BeagleBone development board's PTS via SSH over Ethernet, and I also have an LCD displaying the GNOME GUI awaiting a password.

I don't have a keyboard plugged into the device, and the LCD is a touch screen, but I'm wondering if I can somehow 'echo' the text typed into the SSH shell into the 'password' bar of the GUI so I can log in.

I've mucked around passing commands from one TTY to another (e.g. 'echo blah > tty1'), but I'm not sure if it's possibly to do it in this case.

---

### Post by dohzer on 2012-08-25
I notice if I read from the /dev/input/mouse0 file I can output the touch screen data, and when I plug in a keyboard there are two other files in the /dev/input directory (event2 and event3).

Could I write data to these files to pass it on to the GUI as a keyboard command?

---

### Post by dohzer on 2012-08-25
I've figured it out.
Someone on another forum suggested I install [xdotool]("http://www.semicomplete.com/projects/xdotool/") which then just needed me to use 'export DISPLAY:=0' to allow it to work properly.

Now I can send text and key presses (and mouse commands, etc) to the GUI from the SSH shell.:D :D :D

---

