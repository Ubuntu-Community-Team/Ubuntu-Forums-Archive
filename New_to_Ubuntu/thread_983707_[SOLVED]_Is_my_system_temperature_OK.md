---
title: "[SOLVED] Is my system temperature OK"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by sonu 1807 on 2008-11-16
I have AMD Tutorian 64 X2 processor with 1 GB Ram . I have compiz-fusion enabled. Righ now I am running Abiword, firefox, swiftweasel, frostwire.I use EVDO usb device for internet and that too is connected.The system monitor  says that I am using 37% of RAM. The room temperature is about 27 C. Now when i type sensors in terminal i get this-:
k8temp-pci-00c3s 
Adapter: PCI adapter
Core0 Temp:  +56.0°C                                    
Core1 Temp:  +59.0°C  

I want to know is this OK or my computer is getting hot? I am using 32-bit hardy

---

### Post by boblemur on 2008-11-16
yeh that should be fine, most are rated for about 70 degree's ur bios should cut the power to the core if its too hot, to save it from overheating...


the higher the temp the less stable ur core will be... however 50 degree's is definatly a healthy opperating tmp

---

### Post by cl0ckwork on 2008-11-16
thats normal temperature for AMD chips under load, no worries.
AMD always tend to run a little hotter than Intel, but they get the work done a lot better IMO

---

### Post by sonu 1807 on 2008-11-16
Thanks... Now I am happy :)... I have noticed that the fan does not work overtime as it did when I was using vista is it because ubuntu is easier on processor

---

### Post by sonu 1807 on 2008-11-16
Thanks... Now I am happy :)... I have noticed that the fan does not work overtime as it did when I was using vista... is it because ubuntu is easier on processor

---

### Post by Skripka on 2008-11-16
It depends on the thermal rating of your CPU.


My AMD6400+ is a 125W chip.  It has a MAX temp of 65C.  For example 65W Intel chips have a max temp near 100C (IIRC).

It depends on your specific chip and its thermal rating.

---

### Post by boblemur on 2008-11-16
hell yeah it is... ubuntu is very nice :) iv got mine down to 100mb of ram and almost completly idle :)

openbox ftw :P

---

### Post by sonu 1807 on 2008-11-16
How I can find thermal rating of my chip?

---

### Post by Skripka on 2008-11-16
> **sonu 1807 said:**
> How I can find thermal rating of my chip?

What model chip is it?   Turion you say?  From what I've read Turions have a 35W thermal power-which means you're very safe.

Scroll down to Turion:

[http://www.cpu-world.com/info/id/AMD-Mobile_K8-identification.html](http://www.cpu-world.com/info/id/AMD-Mobile_K8-identification.html)

---

### Post by boblemur on 2008-11-16
read this for more info:


[http://www.amd.com/us-en/assets/content_type/white_papers_and_tech_docs/43373.pdf](http://www.amd.com/us-en/assets/content_type/white_papers_and_tech_docs/43373.pdf)

but ur chip appear to be happy at upto almost 100 degrees

although i wouldnt let it get that hot if i were you...just in case :P

but that document has all the details

---

### Post by oldsoundguy on 2008-11-16
the temps reported in the posts are fine.

Just remember the hotter the ambient around a chip, the hotter the interior of the case.  
I ran a hyper-threaded intel 3.06 for a while and it would LITERALLY heat the house in the wintertime.. lots of noisy fans in order to keep the temps in the box down.  To no avail as the capacitors on the power rails sat right next to the processor on that MSI board and eventually those capacitors got cooked and the board became, as the saying goes, TOAST!

---

### Post by sonu 1807 on 2008-11-16
even if I am using it for hours and using multiple applications ... it does not rise beyond 75. i just checked it by opening picasa and some other applications too simulataneously.... so it seems fine:)... Now one more thing how can I mark this post as solved... i tried but am not finding any clue for that... sorry I know this is silly...

---

### Post by boblemur on 2008-11-16
just above in thread tools... should be solved if i recall correctly...

---

### Post by sonu 1807 on 2008-11-16
OK I marked it as solved :)....  ubuntu forum rocks!!:guitar:

---

