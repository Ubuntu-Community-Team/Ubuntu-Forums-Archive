---
title: "HOWTO: Sony PS3 Bluetooth Remote to control Amarok(or Kaffeine)"
date: 2009-01-05
forum: Outdated Tutorials &amp; Tips
---

### Post by aws910 on 2009-01-05
HOWTO: Sony PS3 Bluetooth Remote to control Amarok(or Kaffeine)

Requirements:
*Ubuntu (developed and tested under Ubuntu 8.10 Intrepid Ibex)
*Bluetooth
*Sony Bluetooth Playstation3 BD Remote

Steps:

1a. Install the required applications:
From a terminal(accessed via "Applications -> Accessories -> Terminal"), execute:
```
sudo apt-get install bluez-utils python-bluez
```

1b. Install Amarok.
It's a wonderful audio player.  If you don't use it, you should.  To install, from a terminal:
```
sudo apt-get install amarok
```

2. Enable HIDD:
At terminal, run:
```
sudo nano /etc/default/bluetooth
```
scroll to the line:
HIDD_ENABLED=0
and change it to:
HIDD_ENABLED=1
If the line doesn't exist, add "HIDD_ENABLED=1" at the end of the file.  Save the file and close it by pressing ctrl+x, then y to save your changes.

3. Get your remote's address:
Open a terminal, hold the START and ENTER keys on the remote, and type:
```
hcitool scan
```
The output should be something like this:
Scanning ...
xx:xx:xx:xx:xx:xx	BD Remote Control
"xx:xx:xx:xx:xx:xx" will be the address of your remote, note it.
If, at this point, "hcitool scan" yields no result, check the batteries in the remote and try again.

4. Pair your machine with the remote:
From the terminal, hold the START and ENTER keys on the remote and execute:
```
sudo hidd --connect xx:xx:xx:xx:xx:xx
```
(where xx:xx:xx:xx:xx:xx is the address you got in the last step)
To verify your remote is paired with your machine, execute:
```
hidd --show
```
Your remote should be listed.

5. Open Amarok - in gnome it's under "applications -> sound and video".  If you can't find it, you can run "amarok" from terminal.  If it's your first time opening it, you may need to perform some setup.

6. Download the attached script, "sonybd-amarok.py".  From the directory you downloaded the script to, hold the START and ENTER keys on the remote and execute it in a terminal:```
./sonybd-amarok.py
```If it says it's connected, and doesn't give an error, you can minimize this window.

If all is well and I didn't miss anything, you should be able to manipulate amarok at this point.  The only keys currently supported are:
Display: Toggles playlist on/off
Next: Next track
Prev: Previous Track
Play: Begin playback
Stop: Stop playback
Pause: Pause
Up arrow: Volume up
Down arrow: Volume down

If it doesn't work, post here and I'll help.  

---
more info:

When I started mapping functions to buttons, it wasn't apparent to me what each key should do - I just mapped the functions I needed.  If anyone would like to take a look at [this page]("http://amarok.kde.org/wiki/Script-Writing_HowTo_1.4") and help me out with some ideas as to which button should do what, I'd appreciate it.

The script currently works with Amarok 1.4, which is what apt-get gave me.  This may need to be revised when amarok 2 lands in the repo.

The program uses DCOP to interface with Amarok.  According to [this KDE page]("http://docs.kde.org/kde3/en/kdewebdev/kommander/dcop-interface.html"), all KDE applications support DCOP(to a certain extent), so Kubuntu users will benefit most from the script.  Kaffiene(a superb video player) also works with DCOP, and I may write a script to control it as well.  If I get enough response, maybe I'll write a script that does even more, or write this into a wiki page.

---
References:
[http://amarok.kde.org/wiki/DCOP_Functions](http://amarok.kde.org/wiki/DCOP_Functions)
[http://ps3mods.blogspot.com/2007/03/blu-ray-disc-remote-and-linux.html](http://ps3mods.blogspot.com/2007/03/blu-ray-disc-remote-and-linux.html)
[http://amarok.kde.org/wiki/Script-Writing_HowTo_1.4](http://amarok.kde.org/wiki/Script-Writing_HowTo_1.4)
[http://docs.kde.org/kde3/en/kdewebdev/kommander/dcop-interface.html](http://docs.kde.org/kde3/en/kdewebdev/kommander/dcop-interface.html)
[http://ps3mods.blogspot.com/2007/03/bd-remote-for-linux-update.html](http://ps3mods.blogspot.com/2007/03/bd-remote-for-linux-update.html)

---

