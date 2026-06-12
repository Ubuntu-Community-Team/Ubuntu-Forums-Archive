---
title: "[SOLVED] Xserver Stopped Working After Kernel Update"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by seagullplayer77 on 2008-05-28
So here's my problem: 

Update manager came up with a sizeable load of updates (almost 60 MB of files), so I naturally hit the update button and let the updates install. Among the updates was a new kernel image, which I also installed. I rebooted the system because update manager required one, and I booted into the new kernel without a glitch--everything worked the way it had in the old kernel. I installed Wine via Synaptic (not sure if that's significant, but I figured I'd include it anyway, just in case it was) and then I put my laptop in Suspend. 

Now here, there be dragons. Suspend always worked flawlessly in the old kernel, but in the new one, I couldn't wake the machine up. The mouse wouldn't do it, keyboard wouldn't do it, and I couldn't even Ctrl+Alt+F1 into a shell. I ended up having to a hard reset, and when I tried booting into the new kernel (and the older one, for that matter), I got hit with an error message right before the GDM screen should've showed up. I don't have the exact text, but it said something along the lines of "X could not start due to an internal error. Contact your system administrator to get it fixed. Until you fix the problem, the graphical display will be disabled. Once fixed, please restart GDM." Then, it dropped me into a command shell, from which I had complete functionality--I just couldn't get to my desktop.

I tried booting in recovery mode and doing an Xfix, but I got hit with another error about X not being able to access a file because the file system was read-only. Anyway, I'm starting to get that funny feeling in my stomach that you get when you're starting to feel absolutely screwed over, and I'd really appreciate some help here! Please, guys--I'm not in the mood to reinstall my Ubuntu, especially after I just finished getting everything working. 

Help!!

P.S. Probably should've mentioned this sooner, but I'm running Ubuntu Studio 8.04 AMD64, and both of the kernels I have are realtime.

---

### Post by seagullplayer77 on 2008-05-28
I tried running an apt-get to see if I could reinstall nvidia-glx, but I got hit with more errors there--/var/lib/dpkg was listed as read-only, along with a number of other folders. I tried to mess with the permissions, but that didn't do any good at all. Could the kernel update have messed with file permissions too?

Please--I'm desparate for some help here.

---

### Post by quelx on 2008-05-28
make a backup of your **xorg.conf** file ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.20080528
```

and try ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by seagullplayer77 on 2008-05-28
Another desparate bump

---

### Post by seagullplayer77 on 2008-05-28
All right, I'll give that a try right now...And if you could, quelx, please keep helpin' me out if this doesn't work! I'd appreciate it more than you could imagine.

---

### Post by seagullplayer77 on 2008-05-28
I think God just fixed it, because I did a reboot out of Vista (that's where I started the thread) and all of a sudden, X was working again--and in the new kernel, too. 

Anyway, is there any way to see what was causing the problem without trying to reboot again? I'm not doubting my machine, but, well...let's just say I'm kinda reluctant to reboot it again :-). Any ideas?

---

### Post by iaculallad on 2008-05-28
> **seagullplayer77 said:**
> I think God just fixed it, because I did a reboot out of Vista (that's where I started the thread) and all of a sudden, X was working again--and in the new kernel, too. 

Anyway, is there any way to see what was causing the problem without trying to reboot again? I'm not doubting my machine, but, well...let's just say I'm kinda reluctant to reboot it again :-). Any ideas?

To view logs on your X Server, you could try this on your terminal:

Code:

```
cat /var/log/Xorg.0.log
```

---

### Post by quelx on 2008-05-28
Praised be his name

Have a look at **/var/log/Xorg.0.log*** (copy them to your desktop because they get overwritten after each reboot) ```
cp /var/log/Xorg* ~/Desktop/
```

Lines with **EE** in the fron are critical errors that stop X11 from loading, those are the ones to look at closely.  **WW** lines are generally informational warnings and not show stoppers.

---

### Post by seagullplayer77 on 2008-05-28
Indeed. Amazing what a quick prayer and some faith can accomplish.

In any case, was able to reboot safely into both kernels without any hitches at all, although I did notice one thing: I can resume a session after I suspend. I used to be able to suspend/resume all the time, and it worked flawlessly without any special procedures before the kernel update. While it's not a major issue (not as big as losing X!), it would be nice if I could get it sorted out.

Should I mark this thread as solved and start a new one for the suspend/resume issue, or should I just keep using this one? Kinda new to forums in general, so I'm not sure what the accepted thing would be...

Anyway, thanks for the help!

Btw, not sure if there's any significance to these lines, but there were only three problematic lines I could see in the Xorg.0.log file. Here they are:

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) NVIDIA: No matching Device section for instance (BusID PCI:0:1:3) found
(WW) Configured Mouse: No Device specified, looking for one...

My wireless mouse works just fine, as does my touchpad, and I'm not concerned about the fonts, but I figured I would mention those lines anyway, just in case.

---

