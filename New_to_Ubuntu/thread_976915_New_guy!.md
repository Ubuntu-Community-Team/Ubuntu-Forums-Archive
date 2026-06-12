---
title: "New guy!"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by Whisp3r on 2008-11-09
Good evening.

My name is Whisp3r, and I am brand new to Linux. I tried a couple variations of Linux, and have ended up landing with Kubuntu. I enjoy KDE 4.1, and the flavor of Ubuntu, so here I am.

I have a few questions; I will try not to sound like an idiot, as I plan to make a trip to the local book store and pick up a Ubuntu book which to read while I'm bored at work. :)

How do I tell:
1) My computer's stats (similar to my computer properties in Windowz (IE, RAM/Processor/etc).
2) How do I tell how much hard disk space I have left?

Thank you much, and I look forward to working with you all. :)

-Whisp3r.

P.S. Please don't mock me too hard! :)

---

### Post by AmbiguousOutlier on 2008-11-09
Click System > Adminstration > Synaptic Package Manager.

Within the Synaptic Package Manager click the search button and type "gnome-device-manager"

Click the first entry and select “Mark for installation” Then click “Apply” on the toolbar. This will tell you about your computer stats and just click on   places > computer, on the bottom you'll see you available disk space.

---

### Post by AmbiguousOutlier on 2008-11-09
or you can install screenlets, I think there's a vista style widget that shows your disk space.

---

### Post by drs305 on 2008-11-09
> **Whisp3r said:**
> 
2) How do I tell how much hard disk space I have left?


Or for partition usage/space you can run this in terminal:
```
df -Th
```

You will find there are lots of ways of doing things in linux.

Welcome to the (K)ubuntu forums!

---

### Post by SuperSonic4 on 2008-11-09
> **RhysGM said:**
> Click System > Adminstration > Synaptic Package Manager.

Within the Synaptic Package Manager click the search button and type "gnome-device-manager"

Click the first entry and select “Mark for installation” Then click “Apply” on the toolbar. This will tell you about your computer stats and just click on   places > computer, on the bottom you'll see you available disk space.

The OP has kubuntu ;)

KMenu -> System -> Adept Package Manger.

Your computer's stats can be found using a few methods, install superkaramba so you can install widgets more easily:

```
sudo apt-get install superkaramba
```

You can get widgets such as this Oxygen system monitor: [[COLOR="Red"]http://kde-look.org/content/show.php/Oxygen+System+Monitor?content=86664[/COLOR]]("Clicky").
Download and open with superkaramba

2. Filelight is considered and excellent tool for this
```
sudo apt-get install filelight
```

---

### Post by Whisp3r on 2008-11-09
Holy cow. That was a quick response.

Thank you all so very, very much.

---

### Post by grotto on 2008-11-09
Ksysguard will show you your memory usage, apps running in memory, cpu usage.

---

