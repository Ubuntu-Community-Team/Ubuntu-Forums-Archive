---
title: "Upgraded from Lubuntu 16.10 to 18.04 now VNC won't connect"
date: 2020-01-08
forum: New to Ubuntu
---

### Post by ianmanning on 2020-01-08
I was using a RealVNC client on my Windows 10 machine to connect to my Lubuntu 16.10 machine. I have now installed Lubuntu 18.04, with the same VNC setup as I had in the 16.10 config, but now my VNC client says "Failed to connect" when I try to connect on port 5900.

These are the commands I use to start VNC:
```
/usr/bin/x11vnc -xkb -auth /var/run/lightdm/root/:0 -noxrecord -noxfixes -noxdamage -forever -bg -rfbport 5900

tightvncserver :1
```

I originally ran them from a bash prompt, and they ran successfully. I've also tried putting them in my autostart.

Is the above method no longer valid for Lubuntu 18.04?

---

### Post by ianmanning on 2020-01-09
One step forward, two steps back...
So I tried an alternative approach:  I followed the instructions here to install an alternative VNC server solution, using xfce4:
[FONT=Arial][[COLOR=#663366]https://linuxconfig.org/vnc-server-on-ubuntu-18-04-bionic-beaver-linux[/COLOR]]("https://linuxconfig.org/vnc-server-on-ubuntu-18-04-bionic-beaver-linux")

I was then able to connect from my Windows VNC client, but found that I was unable to run synaptic package manager from the GUI (presumably because VNC is giving me a shell with no root access?). However I was able to run it from a command line using 
```
sudo synaptic
```

I then made a few changes to /etc/fstab to mount my internal drives, and smb.conf to create some smb shares,  and rebooted. Now I have two problems:

(1) The console (default Gnome desktop for Lubuntu 18) does not respond to my keyboard or mouse

(2) A VNC session is unable to install new packages - this happens:
```
sudo apt-get install lame
E: Could not open lock file /var/lib/dpkg/lock-frontend - open (2: No such file or directory)
E: Unable to acquire the dpkg frontend lock
```[/FONT]```
[FONT=Arial]/var/lib/dpkg/lock-frontend, are you root?[/FONT]
```
I get the same error when I try to run synaptic.

Any idea how I can fix these two problems?

---

### Post by CelticWarrior on 2020-01-09
The error message says it all. There's some process, updates running in the background probably, locking it.
Just wait or reboot.

---

### Post by ianmanning on 2020-01-09
I rebooted and got the same error
???

---

### Post by guiverc on 2020-01-10
```
E: Could not open lock file /var/lib/dpkg/lock-frontend - open (2: No such file or directory)Check the [COLOR=#000000][FONT=&amp]/var/lib/dpkg/ directory exists.
```

There are a few things I don't understand, 
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
> The console (default Gnome desktop for Lubuntu 18) does not respond to my keyboard or mouse

There is no Lubuntu 18 as it only has primary *year.month* releases (Ubuntu Core 18 for IoT is a specialist release using *year* format). Default Gnome desktop?  Lubuntu uses LXDE not Gnome.  16.10 was only tested to upgrade to 17.04 (ie. next bump; only LTS to LTS also gets tested; so 16.04 to 18.04, or 17.10 to 18.04)... The result is I've stayed away from this one.[/FONT][/COLOR]

---

### Post by ianmanning on 2020-01-10
Sorry - I'm new to Ubuntu. My distro is 18.04.3 Bionic Beaver LTS (LXDE).
I use the default UI installed with this - from what you're saying this is LXDE

---

### Post by Autodave on 2020-01-10
Let's back up a moment: you upgraded from 16.10 to 18.04?  That could be the problem since you skipped 17.04 and 17.10 in the process.  Some one higher on the pay scale might have to jump in here.

---

### Post by Al_Klein on 2020-01-11
@ ianmanning:  Your thread got me to rethinking - I also couldn't get any VNC running in 18.04.3, so I tried synaptic, and installed tightvncserver, then used your shell script (in a file) to start it.  IT STARTED!  (Gave it the password, etc.)  Then went back to my Win box and tried connecting TightVNC client to it and, Voila!, it worked.  So thank you, and maybe try that yourself.  Synaptic should work - I did the whole thing from the Win box, I'm typing this from the Win box ... I just don't get key repeat, which I think is a setting in the client ... I have to check that.  (UltraVNC viewer allows repeat characters.  Problem solved.)

---

### Post by ianmanning on 2020-01-13
> **Al_Klein said:**
> @ ianmanning:  Your thread got me to rethinking - I also couldn't get any VNC running in 18.04.3, so I tried synaptic, and installed tightvncserver, then uses your shell script (in a file) to start it.  IT STARTED!  (Gave it the password, etc.)  Then went back to my Win box and tried connecting TightVNC client to it and, Voila!, it worked.  So thank you, and maybe try that yourself.  Synaptic should work - I did the whole thing from the Win box, I'm typing this from the Win box ... I just don't get key repeat, which I think is a setting in the client ... I have to check that.  (UltraVNC viewer allows repeat characters.  Problem solved.)
Hmmm...that's weird. You seem to have done exactly what I did (installed tightVNCserver from Synaptic, then ran the script). I wonder why on earth my Windows client won't connect???

Incidentally I didn't actually upgrade from 16.10 to 18.04.3 - it was a clean install of 18.04.3 on a machine that was previously running 16.10 (I wiped the OS partition)

---

