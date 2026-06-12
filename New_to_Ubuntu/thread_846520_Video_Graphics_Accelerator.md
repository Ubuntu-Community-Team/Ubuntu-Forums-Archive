---
title: "Video Graphics Accelerator"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by parakeets11 on 2008-07-01
I have just managed to install a updated graphics driver for linux and at first it had issues.  It asked me to configure and set the driver and monitor.  I chose a Generic Monitor 1680x1050 widescreen and the Nvidia Gefore 8 series driver (I have a Gefore 8600 GTS, yes I know, uber fail).  It would mever boot so I restarted it and then I could log in.  But when i went to enable the graphics Acelerator, it would go back and ask me to configure the drivers again, back to where I started.  I new to Linux, second or third day using it, and I am just LOST.  Is there a way to roll back drivers or something, back to where it was when i first installed Ubuntu?

---

### Post by Hospadar on 2008-07-01
how are you installing/enabling the drivers?

---

### Post by parakeets11 on 2008-07-01
Through System>Administration>Hardware Drivers and i check that box, on restart, it starts the cycle over again.

---

### Post by mbsullivan on 2008-07-01
Hi parakeets11,

I have neither an nvidia card nor do I use the Gnome WM, so I'm not sure I can be of much help, I'm afraid.

Have you looked at the nvidia community documentation [here]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")? It's not updated for Hardy, but perhaps it may still be useful.

I believe that the normal way to install the drivers is to install the nvidia-glx package along with the linux-restricted-modules package for your kernel, and then run nvidia-xconfig.

I'm loathe to give you the exact commands for this, since I'm not 100% sure about the process, but my guess is it would look something like the following:

```
sudo -s
aptitude install nvidia-glx nvidia-xconfig nvidia-settings linux-restricted-modules linux-restricted-modules-`uname -r`

```

Then restart X (using CTRL+ALT+BACKSPACE) and run:

```
sudo nvidia-xconfig
```

Mike

---

### Post by parakeets11 on 2008-07-01
Well, it worked, but then failed when I tried to enable it.  So i give up.
I want to wipe that partition and reinstall, how do I do this?  Do I just install over it and it wipes it for me?

---

### Post by mbsullivan on 2008-07-03
> Well, it worked, but then failed when I tried to enable it. So i give up.


What failed when you tried to enable what? You shouldn't have to enable your graphics drivers, per se...

> I want to wipe that partition and reinstall, how do I do this? Do I just install over it and it wipes it for me?

You can reformat a partition in the installer, or you could boot to a [gparted]("http://gparted.sourceforge.net/") CD and reformat there. Which partition are you talking about, though? The one containing all ubuntu files, or did you separate your /boot and /home partitions (or something)?

Mike

---

