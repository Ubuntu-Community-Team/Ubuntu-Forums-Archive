---
title: "Manually install latest nvidia driver"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by hermes0710 on 2008-04-29
Hi all,
  I faced problems of blank screens when booting to Gutsy after installing manually the latest drivers from nvidia's site. Has anybody tried to do this in hardy heron? Is there any tutorial on how to manually install the latest nvidia drivers in ubuntu?

---

### Post by alienexplorers on 2008-04-29
I use Envy to load my drivers.  It's a lot easier to do it this way.  No playing with files.  Just start it and let it run.

---

### Post by hermes0710 on 2008-04-29
> **alienexplorers said:**
> I use Envy to load my drivers.  It's a lot easier to do it this way.  No playing with files.  Just start it and let it run.

Thank you, I will try that home. I visited envy's home page but no reference to hh8.04, is it working??? (I really dont want to mess up nvidia...)

---

### Post by hermes0710 on 2008-04-29
Never mind, I found the reference (EnvyNG). Thanx again, I'll come back if anything goes wrong.

---

### Post by pedro_orange on 2008-04-29
> **hermes0710 said:**
> Never mind, I found the reference (EnvyNG). Thanx again, I'll come back if anything goes wrong.

I wouldn't recommend installing nvidia drivers from the site unless you know what you're doing.

If you can; use Restricted Driver Manager.
If you can't use that; use Envy.
If you can't use either; then install manually, following a guide.

---

### Post by hermes0710 on 2008-04-29
Hi pedro, I actually want to have the latest drivers because i am facing some problems with the video rendering. I keep seeing horizontal lines in any video and its kind of disturbing. I want to try the latest drivers so i would use envy but since my box hosts 8.04 i have to use envyng.

Any warnings?

---

### Post by pedro_orange on 2008-04-29
I'm not sure if Envy works for Hardy yet.
I'm sure it will do soon enough, either way.

If you download it from the site; save it someplace you can remember. Like your home dir.
Logout.
Ctrl+Alt+F1 (So you're in Terminal)

If you're using Gnome (Like the pros do!)
sudo /etc/init.d/gdm stop

Else if you're a KDE man:
sudo /etc/init.d/kdm stop

Then you run the driver shell script..I think it's something like:

sh nvidia-driver-name-thingie-a-mjigg-foobar.run

You'll then need to edit your xorg.conf to have the correct stats in. Like screen res etc.

Good luck

---

### Post by hermes0710 on 2008-04-29
> **pedro_orange said:**
> I'm not sure if Envy works for Hardy yet.
I'm sure it will do soon enough, either way.

If you download it from the site; save it someplace you can remember. Like your home dir.
Logout.
Ctrl+Alt+F1 (So you're in Terminal)

If you're using Gnome (Like the pros do!)
sudo /etc/init.d/gdm stop

Else if you're a KDE man:
sudo /etc/init.d/kdm stop

Then you run the driver shell script..I think it's something like:

sh nvidia-driver-name-thingie-a-mjigg-foobar.run

You'll then need to edit your xorg.conf to have the correct stats in. Like screen res etc.

Good luck

Thanx, i'll come back to you later this evening (if i have a working screen :lolflag: )

---

### Post by Nepherte on 2008-04-29
Envy works on hardy. I found it in the repositories.

---

### Post by pedro_orange on 2008-04-29
> **Nepherte said:**
> Envy works on hardy. I found it in the repositories.

Smashing. I was just booting up my laptop to check to see if it was there.

```
pedro@pedro-laptop:~$ apt-cache search envy
alsa-tools-gui - GUI based ALSA utilities for the specific hardware
envyng-core - install the ATI or the NVIDIA driver
envyng-gtk - intall the ATI or NVIDIA driver
envyng-qt - install the ATI or NVIDIA driver
```

They're also in Synaptic.
Could give it a go if you wanted to.

---

### Post by hermes0710 on 2008-04-30
I installed it and it works fine! Thank you all for your replies

---

