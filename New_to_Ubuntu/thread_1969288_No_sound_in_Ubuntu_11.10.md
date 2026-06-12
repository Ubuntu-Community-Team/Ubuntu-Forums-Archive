---
title: "No sound in Ubuntu 11.10"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by joeyfixit on 2012-04-29
Did some recommended updates today, restarted and no sound at all.

As per another thread I tried:

sudo /sbin/alsa force-reload

in the terminal and the response is:

Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).

Which I thought was strange.

alsamixer provides no options - "no such file or directory".

Suggestions?

Does anyone know of a recent update that removes/replaces alsa?

---

### Post by daslinkard on 2012-04-30
Are you using gnome or unity?  I have seen were users have not been able to get sound to work in gnome but were able to get it to work in Unity....just switching between the two.

---

### Post by daslinkard on 2012-04-30
It looks like you might be able to open a terminal and do the following commands:

```
sudo apt-get remove --purge alsa-base
```

```
sudo apt-get remove --purge pulseaudio
```

```
sudo apt-get clean && sudo apt-get autoremove
```

```
 sudo apt-get install alsa-base 
```

```
sudo apt-get install pulseaudio
```

Then restart your PC....if your sound icon goes away after rebooting try the following command:

```
sudo aptitude ubuntu-desktop
```

---

