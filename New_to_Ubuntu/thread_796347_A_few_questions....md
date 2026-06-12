---
title: "A few questions..."
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Tom--d on 2008-05-16
How do I have more than on conky running? {Solved}

How do I find out how much RAM my graphics card has? (in the terminal)

I have no sound in flash in firefox? Why? {Solved}

thanks,
Tom

---

### Post by Tom--d on 2008-05-16
anyone??

---

### Post by Tom--d on 2008-05-16
??

---

### Post by shifty_powers on 2008-05-16
try

```
sudo dmidecode | more
```

for the second question ;)

---

### Post by erginemr on 2008-05-16
For two conky setups:
[http://ubuntuforums.org/showthread.php?t=300742](http://ubuntuforums.org/showthread.php?t=300742)
[http://ubuntuforums.org/showthread.php?t=281865&page=202](http://ubuntuforums.org/showthread.php?t=281865&page=202)

---

### Post by erginemr on 2008-05-16
For Firefox Flash sound issue, installing the following package may help:
```
sudo aptitude install libflashsupport
```
which supposedly fixes Flash sound problems in PulseAudio sound system.

---

### Post by Tom--d on 2008-05-16
It showed my bios, cpu an ram. No Graphics card :(

---

### Post by erginemr on 2008-05-17
I guess you are looking for a way to show the RAM of your video card (GPU) **on conky**. I have no direct answer to that but the following site packs a plethora of conky setups. A sub-search there for video RAM may yield some useful information:
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

Otherwise, for general tools to get info about your graphics card, I can only think of these:
1. If you are an NVidia user, which shows up as the outcome of the following terminal command:
```
lspci | grep -i vga
```
Then, you can install nvidia-settings from Synaptic or with:
```
sudo aptitude install nvidia-settings
```
and have access to more information regarding the details of your video card (first screenshot)

2. The tool **hardinfo** gives general diagnostics for your hardware,but surprisingly reports my video card RAM wrong. You may want to give it a shot, anyway (second screenshot):
```
sudo aptitude install hardinfo
```
```
Alt+F2 -> hardinfo
```

Take care. :)

PS. I wonder if you could solve the sound problem in Flash.

---

### Post by hyper_ch on 2008-05-17
it is also adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

Furthermore it's also advices for unrelated questions to open individual threads.

---

### Post by Tom--d on 2008-05-17
Will do next time. Just couldn't think of a title for it. 

I don't have Nidvia, I have an Intel graphics card.

Hardinfo reports my RAM as 256mb, but when I had virtualbox, it reported I have 128mb.

And when I look up my model on the internet, it says 300mb (around) but that includes the system ram as well.

---

### Post by Xiong Chiamiov on 2008-05-17
> **Tom--d said:**
> Will do next time. Just couldn't think of a title for it. 

I don't have Nidvia, I have an Intel graphics card.

Hardinfo reports my RAM as 256mb, but when I had virtualbox, it reported I have 128mb.

And when I look up my model on the internet, it says 300mb (around) but that includes the system ram as well.
As we discussed [here]("http://ubuntuforums.org/showthread.php?t=797287#5"), you can actually edit the title for this thread now.  I've found good titles can bring in better help.

---

