---
title: "login does not work"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by firefox791 on 2008-07-03
Help!

I've just installed Ubuntu 8.04 (Hardy Heron??), and the installation worked fine. 

But when i try to login after Restarting after the Installation, I get a funny Problem:

-i hear the drums - sound (the one signalising you've reached the login screen) and
-the login screen appears
-i enter the CORRECT username and password i chose during installation
-i hear the sound that accompanies the loading desktop and the screen turns beige-oragneish color

so far that's fine, and thats what should happen. but then suddenly, i hear the first sound again and I'm back at the login, and i never get to see more than the monochromatic orange-beige screen :(

please help me! what on earth have i done wrong?

Some more info:

i have 2 Partitions on my primary slave IDE drive, one 45GB ext2 for the / directory, one 5GB swap partition.

i can log in GNOME-recovery session (or fail-safe ?)

I'm new to ubuntu.

~fox

---

### Post by niyonk on 2008-07-03
yap, try fail-safe (like safe mode in WinLand)
Then, tell us the results :)

Note: fail safe will not load any settings other than the default ones

---

### Post by firefox791 on 2008-07-03
Fail safe works like it should, but since its not an everyday session that you should use for everyday business, i just wanted to ask how to fix this

the results: everything works normally.

---

### Post by firefox791 on 2008-07-03
someone please help!

---

### Post by firefox791 on 2008-07-05
Help!

---

### Post by zakirs on 2008-07-05
try installing other window manager if u have good net speed and see if it works .. this is just anoobish solution 
but u can try

---

### Post by firefox791 on 2008-07-05
What do you mean by another window manager? like XFCE or KDE?

~fox

---

### Post by knockonankur on 2008-07-11
I'm having the same problem..........
plz neone help me with a solution to this problem..

---

### Post by markbuntu on 2008-07-11
If you are having this problem but you can get in with gnome safe mode then you need to look in your log files for error messages concerning gdm or some missing file, etc.

You can find these in System/Administration/System Log.
Look in the auth.log, and and syslog first. If these logs are not shown you can get them with file/open.
I had this problem months ago when I first installed Ubuntu and it turned out to be a few missing apps that gdm called to verify login.

You can also try to get around this by changing the Login Window Preferences/Security to enable timed or automatic login. Automatic login can be a bad experience if something goes wrong with your default login session settings so I do not reccomend that. With timed login you get a chance to get to safe mode.

---

### Post by rogier.de.groot on 2008-07-11
Sounds like something is crashing Gnome as it's starting up.
Could you try to do a regular boot-up & logon? Then, after it crashes, use alt-f1 (or maybe ctrl-f1, I never can remember) to get to a text-mode shell. Login to that, and consult some of the logs in /var/log too try and figure out what's crashing Gnome.
Alternatively, if you have an internet connection you could try something like "sudo apt-get install kubuntu-desktop" (from that same text mode shell) to install the full KDE environment and try with that.

---

