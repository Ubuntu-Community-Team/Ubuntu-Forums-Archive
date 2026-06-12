---
title: "Torrent Client with abillity to Auto Shutdown"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by ConcreteDonkey on 2008-05-10
Hello,

I am wondering if there is a torrent client available that I can use that will automatically shut down my PC once all of my torrents have finished downloading, as I run my PC through the night and I don't want to leave it on all the time.

Thanks

---

### Post by vanadium on 2008-05-10
Under Linux, you can always use the poweroff command to shut down the system on a sheduled time. This command will gracefully terminate all running processes (and a bit less gracefully if the process refuses to shut down voluntary ;)

---

### Post by ConcreteDonkey on 2008-05-10
> **vanadium said:**
> Under Linux, you can always use the poweroff command to shut down the system on a sheduled time. This command will gracefully terminate all running processes (and a bit less gracefully if the process refuses to shut down voluntary ;)

Thanks for the suggestion although if I do set a certain time this will mean, for example if for whatever reason the speed drops the computer may shut down before it is fully complete. I'm looking for a solution that is in the program itself, I know there is utorrent which I can run with wine but I'm not sure if wine will be able to shut down the computer.

---

### Post by knowmonger on 2008-08-21
badboy, dude I confirmed it using the latest uTorrent. It doesn't actually shut down the computer. It just quits itself. Does Azureus have this feature ? 

P.S: If I get a positive answer in any of my tryouts, I'll report here.

---

### Post by knowmonger on 2008-08-21
Bah I searched everywhere. There just isn't any software which does this feature. Well, Azureus actually does do this but through a plugin and see Azureus changed to "Vuze" recently. So, obviously things have changed. But I'm still on the look out.

---

### Post by netlaptop on 2008-08-23
1+ for this feature.

It would be greate if a torrent client (for Linux) gets a function like do command x then y then ... after complete zz tasks. And we can type the command ourself.

Internet bill is ok (unlimited bandwith), but the bill of energy is nightmare for me.

---

### Post by durand on 2008-08-23
I made a python script to do this. The reason why this isn't a feature in most clients is that you need root privileges to shutdown the computer.

_[SIZE="5"]Step 1: Get Deluge 1.0[/SIZE]_
For this script, you need to use [deluge]("http://deluge-torrent.org/") 1.0, which you can get [_here_]("http://ubuntuforums.org/showthread.php?t=837683") or from the [deluge website]("http://deluge-torrent.org/"). You _cannot_ use deluge 0.5 or below. The way deluge works is that there is a daemon which runs in the background and a clients. 
There are currently 3 UI's for deluge:

* Graphical using GTK - You can access this by running deluge -u gtk in a terminal

* WebUI - Accessed through a web browser. You need to start it first by running deluge -u web

* Console - Accessed in a terminal using deluge -u null. This is what the script uses.

For this script to work, get your torrents working with the GUI or WebUI and setup torrent queueing to pause torrents after a certain ratio.

Since root access is needed to shutdown, this script also needs to run as root.

_[SIZE="5"]Step 2: Check that deluge works with root[/SIZE]_
In a terminal, type:
```
sudo -i
```
then your user password. This changes to a root shell.

Now check that deluge -u null can connect to deluged, the daemon:
```
deluge -u null
```
When you get the deluge prompt, type info and press enter. You should get your currently running torrents. If not, type:
```
connect localhost
```
Replace localhost with the ip address of your daemon if it's not on the same computer. Then:
```
info
``` should give you your torrents.

_[SIZE="5"]Step 3: Run the script[/SIZE]_
Finally, get the script.

```
nano -w delugecheck.py
```

Copy and paste this into the terminal.
[PHP]## If all torrents are paused, then the script quits.

# Time to wait between checks in seconds
interval = 60

import os, time
total = 999
done = 0

while done < total:
    info = os.popen('echo info | deluge -u null | grep Status').read()
    total = info.count('Status')
    done = info.count('Paused')
    print "%s in %s complete" %(done,total)
    time.sleep(interval)
[/PHP]
Press Ctrl+X, then Y, then Enter.
Then run the script, telling your computer to shutdown when the script terminates.

```
python delugecheck.py; echo halt | deluge -u null;shutdown -h now
```
If you want to check that it works correctly, replace "shutdown -h now" with "echo Done" and then pause all the torrents with the Deluge GUI. Hopefully, the script will stop and Done will show on the terminal.

---

### Post by devansh.j2007 on 2011-07-24
Well as this is asked for ubuntu all variants the answer is yes(now after a several years) **_[COLOR="Red"]Ktorrent[/COLOR]_**:KS now has the ability to autoshutdown when all torrents are downloaded! I use ubuntu 10.04 lucid and i hv also installed kubuntu desktop on it. my GNOME also handles Ktorrent pretty well and it shuts down my machine! after downloading everything! even it provides all good features like when seeding finishes or a particular download finishes!:popcorn::D

---

