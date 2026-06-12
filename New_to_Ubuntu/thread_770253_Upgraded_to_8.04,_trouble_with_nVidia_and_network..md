---
title: "Upgraded to 8.04, trouble with nVidia and network..."
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Sarteck on 2008-04-27
I tried to upgrade to Kubuntu 8.04 today, had a bucketfull of problems.  The first was some problem with hal or dbus or something like that, and I had to remove then re-install it to get it working (and couldn't do it with apt, for some reason).  This was hard to do or even figure out, as I was also having trouble getting my network back up and getting the xserver to start.

Ell, I finally got the first problem sorted out, but the other two not so much...  I uninstalled Envy (which I had used to install my nVidia driver last time) and installed EnvyNG (envyng-qt, as was recommended for Kubuntu users).  Installation of it went fine, and running it to re-install the driver went fine.  I restarted the computer, but was only able to log into a console screen.  The screen flickered several times, as if it was trying to load, but each time went back to the console login.

So, I logged in at the console, and typed "startx".  Got "(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!"  Went in, changed "nvidia" to "nv" in the xorg.conf file just so I could at least get this far and plead for help.

Then the network trouble started...  I -think- I got it all sorted out, except that I have to manually set a DNS server after manually enabling the wirless card.  :/  Will definitely want to fix that later, but it's not too important at the moment.

Anyways, if you can help at all with the nVidia problem, I'd greatly appreciate it.  I'm sitting here typing in a 640x480 resolution, and it's too reminiscent of the mid `90's.  XD  Thanks in advance.



P.S., I'm no Linux guru--I in fact know very little about the system--so if you'll want me to provide logs or anything, please tell me where I can find them. :)

---

### Post by PmDematagoda on 2008-04-27
How did you install the Nvidia driver in the first place(before the upgrade)?

---

### Post by Sarteck on 2008-04-27
Well, in Feisty I installed from the files at the nVidia site, but Gutsy seemed to throw up when I upgraded to it, so I got -it- to work by using Envy.



Also, isn't```
sudo dpkg-reconfigure xserver-xorg
```supposed to let me specify info about my monitor and stuff?  It's just asking about my mouse and keyboard, writing, and exiting.  Doesn't ask about driver, monitor size, resolution, or anything...  I swear I remember messing with it back when I upgraded to Gutsy, and it DID ask for those things.  >.<

---

### Post by PmDematagoda on 2008-04-27
Since the kernel was upgraded you will have to reinstall the Nvidia driver, you may either use the manual method, Envy or nvidia-glx-new to achieve that.

After installation, run:-
```
sudo nvidia-xconfig
```
and then try starting the X-Server.

---

### Post by Sarteck on 2008-04-27
Not quite sure how I did it... but it works now.  O.o

I read your reply, and was going to say "I already did that," because I honestly did.  XD  But I figured I'd give it one more shot...  I logged out, stopped KDM, used envyng -t to REMOVE the driver, then used the script downloaded from nVidia to install.

It was giving me a whole bunch of errors, something about not being able to do something because some files were left by previous installations or some crap like that, so I of course knew it wasn't going to work...

...Well, I was wrong, thankfully.  Heh.

---

