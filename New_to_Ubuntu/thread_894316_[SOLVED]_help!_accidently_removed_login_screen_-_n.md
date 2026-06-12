---
title: "[SOLVED] help! accidently removed login screen - now cannot access desktop"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by LTFC2020 on 2008-08-19
I tried KDE but decided I prefer gnome so removed it using sudo apt etc
I also found some instructions to remove the Kbuntu boot splash screen (I wished I hadn't)
I typed them into the terminal (sorry cannot remember exactly what it was and the details are lost on the computer)
luckily I have another laptop to ask this question or I'd be really up the creek without a paddle
The result of the above is that after loading the ubuntu log in screen does not appear - instead it looks like the terminal (the whole screen)
I type in my user name and password - then its says something about ubuntu not having warranty etc and then

richard@richard-laptop: $

what do I have to type here to get ubuntu to run i.e. access my desktop?

what do I have to do to get the original login screen back?

any help appreciated

---

### Post by BTMark on 2008-08-19
Hey,

I had a similar issue moving from GNOME to KDE, at the terminal prompt try

```
sudo startx
```

---

### Post by LTFC2020 on 2008-08-19
ok thanks
it says I'm running the session as a security user and I lost all my settings but at least I have the desktop
do you know what to do next?

---

### Post by LTFC2020 on 2008-08-19
I apparently need to set up GDM does anyone know how to do this?

---

### Post by BTMark on 2008-08-19
Hmm... I'd try (from a terminal)

```
sudo dpkg-reconfigure gdm
```If that comes back with an error, try:

```
sudo apt-get install gdm
```

---

### Post by LTFC2020 on 2008-08-19
I tried /etc/init.d/gdm restart

but get the message that gnome is not starting as it is not the default display manager

system ==> admin --> login window results in a message about GDM not running

ARGH!!

---

### Post by BTMark on 2008-08-19
> **LTFC2020 said:**
> I tried /etc/init.d/gdm restart

but get the message that gnome is not starting as it is not the default display manager

system ==> admin --> login window results in a message about GDM not running

ARGH!!

From that, it seems that you must run this into the terminal ```

sudo dpkg-reconfigure gdm
```

I did this when I had to switch back from KDE and had KDM as the default manager.

---

### Post by LTFC2020 on 2008-08-19
mark
I tried sudo dpkg reconfigure and its says changes will take effect when current x session ends
however there is no restart button where it is normally found
and the terminal also says:
invoke-rc.d: intiscript gdm action "reload" failed

---

### Post by BTMark on 2008-08-19
If you can't find the buttons to reboot, open up a terminal and type in

```
sudo reboot
```

---

### Post by BTMark on 2008-08-19
For that "invoke-rc.d: initscript gdm action "reload" failed" error you are receiving, this solution worked for another user who had a similar issue to yours, for the post:

[http://sudan.ubuntuforums.com/showpost.php?p=4354674&postcount=5](http://sudan.ubuntuforums.com/showpost.php?p=4354674&postcount=5)


Edit: The whole thread can be found here: [http://sudan.ubuntuforums.com/showthread.php?t=700234](http://sudan.ubuntuforums.com/showthread.php?t=700234)

---

### Post by LTFC2020 on 2008-08-19
thanks mark
I did a manual reboot i.e. held the off button down, and when it reloaded everything seemed fine
I ran the reconfig gdm again to make sure and restarted it and still ok
cheers:grin:

---

### Post by philinux on 2008-08-19
If you want to find out what you did in the terminal.

Go to your home folder, show hidden files and open .bash_history

Very useful.

---

### Post by BTMark on 2008-08-19
Good! Am glad to hear your problem is solved. Be sure to mark your thread as [SOLVED]! (Believed this option is found under "Thread Tools" at the top of this thread)

---

### Post by LTFC2020 on 2008-08-19
good call
I normally do that but forgot this time

---

