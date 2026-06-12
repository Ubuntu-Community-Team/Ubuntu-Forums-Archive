---
title: "[SOLVED] Mute system beep"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by WitchCraft on 2008-10-07
Hi!

I've a question: 

I've muted sound, but when I use gedit and press up or down key at the top or bottom of a document, you hear this annoying BEEP. 

Additionally, when I start gdm: beep
And when I type "shutdown -h now": BEEP !


How can you switch of this infernal beeping?
I'm using gedit during lectures to take notes, and sometimes I restart during lectures (for example when it is boring, and I installed something).

Why does it beep anyway, when sound is muted?

So far I've muted all channels in volume control... but that doesn't stop the infernal !BEEP!ing...

---

### Post by arkticcool on 2008-10-07
Go to **System > Preferences > Sound** and then go to the system beep tab and disable it.

---

### Post by Dacker on 2008-10-07
what i know is that the Beebing sign is not related any way with or by the operating system, because this sound is the system sound which is built in with the motherboard and the only way to shut it down is that you get rid of the connector from the motherboard that's what i was doing while practicing in DOS on my pc........

wait for the others to benefit you more

---

### Post by NeoTaoistTechnoPagan on 2008-10-07
Yeah, this is a little annoying to some people - myself included.

This is handled by the pcspkr module and can be easily blacklisted.

Check to make sure the pcspkr mod is running (which is probably is)
```
lsmod | grep pcspkr
```
you will see output like this```
pcspkr                  4224  0
```

try this```
 sudo nano /etc/modprobe.d/blacklist
```
go to the end of the file, at the bottom enter this
```
#blacklist pc speaker to get rid of annoying beeps
blacklist pcspkr
```

Hit <ctrl> and <x> to save it. Now when you reboot the pc speaker module will not be loaded.

If that is too drastic for you and you just want to get rid of it for this instance, not every time you use your system, try```
sudo modprobe -r pcspkr
```

---

### Post by iaculallad on 2008-10-07
To permanently remove beep, add it to the blacklist module:

```
gksudo gedit /etc/modprobe.d/blacklist
```

then add:

> blacklist pcspkr

at the last part of the file. Save and Close and do a Ctrl+Alt+Backspace.

---

### Post by tarps87 on 2008-10-07
> **Dacker said:**
> what i know is that the Beebing sign is not related any way with or by the operating system, because this sound is the system sound which is built in with the motherboard and the only way to shut it down is that you get rid of the connector from the motherboard that's what i was doing while practicing in DOS on my pc........

wait for the others to benefit you more

The speaker is build into/onto the moth motherboard but it can be controlled by the bios or the OS so you do not need to disconnect it.
In gnome go to System->Preferences->Sound and disable system beep on the system beep tab. This usually works, if it doesn't you can black list it like previously suggested.
In KDE the blacklist method will also work.
Edit you can make the file .inputrc in your home directory
E.g. Gnome(Ubuntu):```
gedit ~/.inputrc
```
KDE(Kubuntu):```
kate ~/.inputrc
```
and add the line
For no beep:
set bell-style none
For visual beep:
set bell-style visible
(This is per user, for all users use the file /etc/inputrc)

---

### Post by WitchCraft on 2008-10-07
For temporarely disable beeps when X is running:
```

xset b off

```

For permanently disable gnome-terminal beep:
```

gnome-terminal->Edit->CurrentProfile->General --> untick "Terminal bell"

```


To permanently disable gnome-console & gedit beep:
```

System->Preferences->Sound->SystemBeep
untick "Enable system beep"

```


The following does not work: "setx -b" to ~/.bashrc:
```

echo "setx -b" >> ~/.bashrc

```

But you can System->Administration->LoginWindow->Accessibility
There login screen ready is ticked, but has selected "none".
Select a sound, then untick "Login screen ready", and no more beep at gdm startup.

Now I still get the beep when I type too much backspace in gdm, and when I do shutdown -r now
Blacklisting does not do that job, and inputrc does not seem to have any effect...

The option -q for quiet does not seem to exist in shutdown

---

### Post by WitchCraft on 2008-10-07
I wanna change the source to add -q.
Where do i find the source for sbin/shutdown ?

Oh, already answered:
[http://ubuntuforums.org/showthread.php?t=721850](http://ubuntuforums.org/showthread.php?t=721850)

apt-get source sysvinit
apt-get build-dep sysvinit

---

