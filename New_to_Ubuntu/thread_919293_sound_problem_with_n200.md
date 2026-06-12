---
title: "sound problem with n200"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by ivh90 on 2008-09-13
hey there 

i ve just bought a lenovo n200 and installed ubuntu 8.04 
everything works like magic except the sound i just cant make it work although i checked some threads about it but i didnt know how to use the terminal ( since this is my first time i use linux) 

can somebody guide me step by step and maybe i get the sound working ? 

another problem is hibernate ... my laptop doesnt wake up :)  what can i do about it ???? 

please help

---

### Post by rraj.be on 2008-09-13
> **ivh90 said:**
> 
everything works like magic except the sound i just cant make it work although i checked some threads about it but i didnt know how to use the terminal ( since this is my first time i use linux) 

can somebody guide me step by step and maybe i get the sound working ? 


A warm welcome to Ubuntu my dear friend.

In ubuntu you need to install Audio codes separately for playing sounds like Mp3 or videos like .Vob etc.

To install that go the following in men

```
System --> Administration --> Synaptic package manage
```r

in that select the all ```
Gstreamer packages
``` and right click on it and select 

```
Mark For Install.
```

Click apply at the top

And regarding Terminal, its similar to your command line in windows.

All you need is experience and some command in mind to work fine.

You can get many help online regarding the using terminal.

---

### Post by lio_013 on 2008-09-19
i had this problem befor 
u need to add a simple line in a text file
```

sudo nano /etc/modprobe.d/alsa-base

```
then enter your password and hit enter 
a text file will open go to the end and paste the following
```

options snd-hda-intel model=lenovo

```
 then Ctrl+X to save and quit then restart ur laptop and enjoy:guitar:

---

