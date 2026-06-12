---
title: "HOWTO: Solve default sound mixer settings problems"
date: 2005-08-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Copter on 2005-08-08
hi!

**Problem :** when restarting the system / KDE sound mixer settings are messed up. ones saved from previous session arent loaded.

**Intro :** first i would like to say that im quite new to linux (1 month) and this is my first howto. i was trying to solve this problem for a long time (posted it [here](http://ubuntuforums.org/showthread.php?t=52713)). i finally did it and decided to share the solution with other people.

**Thanks :** goes to heimo and cutOff

**General sound settings :** using as default ALSA (0.9.7) with two soundcards:

1) onboard ATI IXP AC97
2) PCI Soundblaster Audigy Player (EMU10K1) (default)

[here](http://ubuntuforums.org/showthread.php?t=27186) is great HOWTO about solving two soundcard problems // issues.

**Solution :**

first set mixer settings as you want them to be
```

alsamixer -c1
```-c1 because i use my 2nd soundcard as default (-c0 is the 1st one). if you have one soundcard you can run without -c1 setting

save your settings (using sudo to enter root mode)
```

sudo alsactl store
``` 
create KDE autostart script
```

nano ~/.kde/Autostart/mysound.sh
```and write there
```

sleep 5
alsactl restore -f /var/lib/alsa/asound.state -F
```click F3 (to save) and F2 to exit.

why 'sleep 5' (it waits 5 seconds before restoring mixer settings)? on my system without this command mixer values were overwriten by some other process. for me it was essential. sleep value can be changed if it doesnt work.

after that you have to change file access permission (i think it would work without this step)
```

chmod 755 ~/.kde/Autostart/mysound.sh
```thats all :D now everytime KDE starts it loads previous sound mixer settings.

i hope it will help

copter :]

---

### Post by pkoufalas on 2005-08-21
Thanks Copter. This problem was driving me mad. I use gnome.

Your howto gave me the insight, and I solved it a bit differently.

I changed the settings using the gnome-volume-control applet and/or the alsamixer console tool (I think I mucked around with both).

Then,

sudo alsactl store

to write the changes to the /var/lib/alsa/asound.conf file was all I needed to do.

ALSA is started on boot. I had a look at the /etc/init.d/alsa script. I also had a look at the /etc/default/alsa configuration script. It looks like the defaults were the problem...on shutdown, the default config for ALSA is *not* to write changes to asound.conf. I didn't confirm it by changing the parameter (can't recall the name, but it's the first one) but it should always save the current sound configuration on shutdown if this parameter is changed accordingly.

---

### Post by Servus on 2005-10-09
thanks a lot!!
It worked!
:D

---

### Post by Copter on 2005-10-23
[QUOTE=Servus]thanks a lot!!
It worked!
:D[/QUOTE]
im glad i could help ;)

copter :]

---

