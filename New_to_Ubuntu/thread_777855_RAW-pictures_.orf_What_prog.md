---
title: "RAW-pictures *.orf What prog?"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by mormor on 2008-05-01
Hi. I take alot of pictures, usually in RAW-format, as I have a olympus e-400 DSLR The format I'm stuck with is *.orf Any idea what prog I can use for ubuntu (heron) that can work this format?

system/administration/synaptics paccage manager:

Search for dcraw, and you will find several plugins for gimp and some standalone converters atleast. Hope this might help somebody else: )

---

### Post by SunnyRabbiera on 2008-05-01
hmm, well you can try the gimp that usually works with a lot of formats.

---

### Post by mormor on 2008-05-01
Gimps doesnt understand the format. : / Wich is a shame, couse I need a photoshoplike program to edit the pics in:P Is a reson I shoot in raw tbh: )

---

### Post by SunnyRabbiera on 2008-05-01
well if its an obscure proprietary format we might not be able to cover you, was there a program you used in windows to read these files?

---

### Post by mormor on 2008-05-01
photoshop did the trick for me. Its not really an obscure format, as its the standard raw format for olympus dslr

---

### Post by SunnyRabbiera on 2008-05-01
yes, but its still a proprietary format... and we might not be able to cover it
but apparently there is a way to get the gimp to work with this format, read this topic:
[look]("http://ubuntuforums.org/showthread.php?t=182155")
It may help you, it may not.

---

### Post by mormor on 2008-05-01
Thnx: )

---

### Post by SunnyRabbiera on 2008-05-01
did it work?

---

### Post by mormor on 2008-05-01
Yep. Now all I need to do is to learn to use gimp like I used to know photoshop. (feels good using free software legal:P )

It reads the *.orf well. Made a fast little solved and explenation in first post. Can repeat it here.

Solved:

system/administration/synaptics paccage manager:

Search for dcraw, and you will find several plugins for gimp and some standalone converters atleast. Hope this might help somebody else: )

---

### Post by SunnyRabbiera on 2008-05-01
well if you have a legal copy of photoshop laying around you may be able to run it in WINE depending on your version of it.

---

### Post by PrimaryMaster on 2008-11-22
IMPORTANT

I apologize if this has been mentioned before. 

You have to use Synaptic Package Manager to install gimp-dcraw to make Gimp work with ORF files. If you use Add/Remove software instead and type dcraw in the search box, it will find Raw Studio which also happens to include dcraw. BUT that dcraw is NOT the plugin for Gimp. 

If you want Gimp to work with ORF files you need to install from Synaptic Package Manager, the gimp-dcraw file. Please acknowledge. 

My kindest regards to all the helpful guys out there!

---

