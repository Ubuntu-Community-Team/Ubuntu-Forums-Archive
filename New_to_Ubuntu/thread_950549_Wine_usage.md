---
title: "Wine usage"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by melrokz on 2008-10-17
I've recently installed wine on ubuntu and was trying to install some software like winamp, avg and adobe reader and they do not work as expected. Will someone please tell me how to use wine productively? Or, is wine incompatible with some windows software?

---

### Post by shifty_powers on 2008-10-17
why were you trying to install avg? there is a natove linux version. as for adobe reader, there are plenty of pdf readers on linux, and iirc even a linux version of adobe reader.

something like xmms is a very good clone of winamp...

[http://en.wikipedia.org/wiki/XMMS](http://en.wikipedia.org/wiki/XMMS)

---

### Post by Sarmacid on 2008-10-17
Wine does not run every program flawlessly, it works in most cases, but in some it doesn't work as expected. As the last post suggest, you should look for linux native versions of the programs you're using.

To run something in wine, usually just

```
wine yourprogram.exe
```

If it doesn't work as expected, you can always configure wine with

```
winecfg
```

---

### Post by LowSky on 2008-10-17
Adobe Reader is availible for linux, you need the Medibuntu repos I think or I can be installed from the source code, but its availible.

Plenty of options for a good multimedia player already exist, just look through Add/Remove under Applications for some choices.

And AVG is worthless on Linux, you dont really need virus protection as nothing can install without you saying its okay, but if its for a computer that is on a local Windows file sharing network then ClamAV is in Add/Remove (or Synaptic) which works great.

---

### Post by Northsider on 2008-10-17
> **melrokz said:**
> I've recently installed wine on ubuntu and was trying to install some software like winamp, avg and adobe reader and they do not work as expected. Will someone please tell me how to use wine productively? Or, is wine incompatible with some windows software?

One question: Why are you using linux if you just want to use windows apps?:confused:

I would *highly* suggest using native linux apps, such as VLC, Banshee, or Amarok for music instead of winamp; a native version of AVG; and a native linux pdf (which work WAY faster than Adobe's bloatware!) reader like KPDF.

If all you want to do is use windows apps, then use windows.  If you genuinely need a windows program to work in linux, consult the wineHQ apps database.  You can find tips and tricks to get common programs to work, or read if it works at all.  It's really a crapshoot with wine if you ask me.

---

