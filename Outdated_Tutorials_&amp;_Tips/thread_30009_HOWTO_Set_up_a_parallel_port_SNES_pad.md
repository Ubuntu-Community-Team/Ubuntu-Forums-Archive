---
title: "HOWTO: Set up a parallel port SNES pad"
date: 2005-04-26
forum: Outdated Tutorials &amp; Tips
---

### Post by NTolerance on 2005-04-26
This guide is for the few of us who like to play SNES games with a real SNES controller.  If you're one of these people, you've followed the various online guides available and have wired up an SNES pad with a parallel port adapter.  There are guides available that explain how to set up one of these pads with older Linux kernels, but some stuff was changed in the 2.6.10 kernel that made previous procedures quit working.  I have done some experimenting and have found a way to make them work with the 2.6.10 kernel that is used by Ubuntu Hoary. 

First, open up your favorite text editor and paste this to create a shell script that will enable our pad:

```
#!/bin/sh
modprobe -r lp
modprobe gamecon map=0,1,0,0,0,0
modprobe gamecon gc=0,1
```

Save it as a filename of your choice.  I will use the name "snespad".  

We need make our shell script executable:

```
chmod +x snespad
```

Copy this shell script to your /bin directory:

```
sudo cp snespad /bin
```

You will now be able to run this script and enable your SNES pad.  It should be recognized in your window manager's GUI config util, if it has one.  I'm running KDE and I can see the controller inputs in the Control Center.  It should also now work in ZSNES.  Please note that this script will unload the "lp" module, which I think has something to do with printer support.  I don't use a parallel port printer, but if you do, you may need to run

```
sudo modprobe lp
```

to re-enable printer support.

If you'd like to have your system execute the script on startup to have your pad always ready to go, copy the script to your /etc/init.d directory:

```
sudo cp /bin/snespad /etc/init.d/snespad
```

Make a link to the runlevel 2 startup (Ubuntu default):

```
sudo ln -s /etc/init.d/snespad /etc/rc2.d/S99snespad
```

Now your SNES pad should work all the time without the need to manually run the script.

---

### Post by Devarien on 2006-07-19
I followed your instructions, but whenever I run ZSNES after initializing the pads, my kernel panics.  This also happens when I run jstest from the Debian joystick package.  Both ZSNES and SNES9x run fine when the joystick is not initialized.  Any suggestions?

-Devarien

---

### Post by arus on 2006-08-05
Hi!

I'm having the same problem... :(
Is there any solution????

Bye

---

### Post by NTolerance on 2006-08-17
Holy crap, I didn't think anyone used my guide.  Apparently something has changed in the newer kernels that breaks this.  I suspect it's one of these two commands that is the culprit:

```
modprobe gamecon map=0,1,0,0,0,0
modprobe gamecon gc=0,1
```

Unfortunately, since I wrote this guide I have sold my old PC that had a parallel port, so I can't test any fixes for you guys.  I did find some more detailed info about this here:

[http://www.tolaris.com/snes-to-parallel/](http://www.tolaris.com/snes-to-parallel/)

Apparently the whole script process that I described above isn't actually necessary to make the SNES pad persistant after a reboot, so forget all that.  This line in /etc/modules would take care of that:

```
modprobe gamecon gc=0,1
```

Again, what probably needs to be tweaked is this:

```
modprobe gamecon map=0,1,0,0,0,0
modprobe gamecon gc=0,1
```

Here's an explanation of that from the above link:

> This will disable lp printing to the parallel port, then load the gamecon joystick driver and tell it to create joystick devices for all five controllers. To use fewer controllers, replace the five 1's with 0's according to the controller wiring order for the "Linux" pinout above. 

---

