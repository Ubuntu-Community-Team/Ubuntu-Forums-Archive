---
title: "Howto: Gnomeboyadvance, A GTK2 Front-end for Visualboyadvance"
date: 2005-10-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Technoviking on 2005-10-27
Gnomeboyadvance is a great GTK2 front-end for Visualboyadvance.

1. Get files:
```
wget -c http://mikesplanet.net/deb/gnomeboyadvance_0.4-1~breezy_all.deb
```

2. Install visualboyadvance:
```
sudo apt-get install visualboyadvance
```

3. Install Files:
```
sudo dpkg -i gnomeboyadvance_0.4-1~breezy_all.deb
```

4. Restart Gnome Panel:
```
killall gnome-panel
```

Let me know if you have any problems,
Mike

---

### Post by kazuya on 2005-11-02
Installation was successful, however, I cannot load ROMs or get them to play.
Is there some guide or readme for gnomeboyadvance? Are there some configuring I need to do to make it work. Like change the permissions of the visualboyadvance executable. Or is there a particular visualboyadvance version that it works with?

---

### Post by Sniffer on 2005-11-02
Sorry for the question...

But do you have the GBA BIOS??

---

### Post by Odice on 2006-03-18
It installs but dont load any roms, a segment fault problem i shown. when you define a roms folder

---

### Post by btnheazy03 on 2006-04-20
[QUOTE=Odice]It installs but dont load any roms, a segment fault problem i shown. when you define a roms folder[/QUOTE]
I get the same error

---

### Post by mp3guy on 2006-05-02
[QUOTE=Odice]It installs but dont load any roms, a segment fault problem i shown. when you define a roms folder[/QUOTE]
Yep, same here too

---

### Post by CorePoint on 2006-05-02
Works perfect for me! Thank you for this cool Tipp.

---

### Post by FentonJT on 2006-05-02
Nice work, keep it up! :)

---

### Post by mp3guy on 2006-05-03
For people having trouble with it freezing etc, download this;

```

http://prdownload.berlios.de/gnomeboyadvance/gnomeboyadvance_0.4-1ubuntu1_all.deb

```

and install it instead of the deb mike provided, then just to be safe, enter in the rom dirs manually, don't browse, just type them in.

---

### Post by finferflu on 2006-11-17
> **mp3guy said:**
> For people having trouble with it freezing etc, download this;

```

http://prdownload.berlios.de/gnomeboyadvance/gnomeboyadvance_0.4-1ubuntu1_all.deb

```

and install it instead of the deb mike provided, then just to be safe, enter in the rom dirs manually, don't browse, just type them in.


That package is not working for me:
```
~$ sudo dpkg -i gnomeboyadvance_0.4-1ubuntu1_all.deb 
dpkg-deb: `gnomeboyadvance_0.4-1ubuntu1_all.deb' is not a debian format archive
dpkg: error processing gnomeboyadvance_0.4-1ubuntu1_all.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 gnomeboyadvance_0.4-1ubuntu1_all.deb

```

Any clue?

Thanks

---

### Post by spyke01 on 2006-11-17
For those needing a guide or howto check out: [http://www.mameworld.net/easyemu/vboyadvtut.htm](http://www.mameworld.net/easyemu/vboyadvtut.htm)

---

### Post by finferflu on 2006-11-17
Am I wrong or that guide is for Windows only?

---

### Post by spyke01 on 2006-11-19
The keys are the same however, since there was nothing on how to save or load a state in the readme files or on the forums

---

### Post by finferflu on 2006-11-20
Yep, but that's a bit too far for me, since I can't find a way to install it. Once installed, *then* I will need to know how to run it...

---

