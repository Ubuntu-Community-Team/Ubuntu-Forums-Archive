---
title: "[SOLVED] Failed uninstall of nvidia restricted drivers"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by NaF on 2008-05-16
I tried setting up visual effects, and it's required me to install those restricted drivers. At the time, those drivers made my screen flicker like crazy (loose dvi cable :oops: ), so I set it uninstall them again. That failed, but it still required me to reboot (?). Now I'm stuck with half installed nvidia drivers that's blocking any kind of use of synaptic. Just how am I suppose to remove those drivers correctly, so I can put them in again and install other stuff?

---

### Post by EXCiD3 on 2008-05-16
What is the error message from synaptic? Try opening synaptic and choosing "Fix broken packages" from the menu.

---

### Post by Sef on 2008-05-16
Did you use Synaptic to install them?  If not, how did you install them?

---

### Post by NaF on 2008-05-16
> **EXCiD3 said:**
> What is the error message from synaptic? Try opening synaptic and choosing "Fix broken packages" from the menu.

E: nvidia-glx-new: subprocess post-removal script returned error exit status 2
Did try the fix broken packaged thing, got the same message

> **Sef said:**
> Did you use Synaptic to install them?  If not, how did you install them?

No I just tried adding the appearance stuff, and it popped up a box that says "enable restricted drivers" - and I removed it from the system - hardware driver section.

---

### Post by nicedude on 2008-05-16
Either use envyng program from the repositories or get the driver from nvidia's website and install yourself. This is the best 2 ways in my opinion of using your Nvidia card with up to date drivers.

COMMAND TO INSTALL ENVYNG
sudo apt-get install envyng envyng-gtk

this will install envyng and its GUI frontend with the -gtk 

to run it just put following in a terminal

envyng-gtk   

then use it to install your nvidia driver for you, thats all it is for and it works pretty well.

also you should uninstall the nvidia drivers installed earlier

sudo synaptic 

this will open the synaptic package manger once in there just search for nvidia and select the ones you installed for uninstallation

GOOD LUCK & feel free to PM me if you need more help I will be around a couple more hours so I can answer you pretty quick ( Click my name and choose send private message :-) )

---

### Post by EXCiD3 on 2008-05-16
Here is information on fixing your synaptic problem: [http://www.debian-administration.org/articles/251](http://www.debian-administration.org/articles/251)

It looks like you just need to comment out "-e" or "set -e" from the removal scripts that are blocking synaptic from functioning. Follow the pages instructions to locate scripts, then edit them with nano and try again. Then you can work out your nvidia problem. With synaptic broken, trying to use envy to install your nvidia drive will do absolutely no good until synaptic is fixed because envy will not be able to download packages it needs, in fact you probably cant even download and install envy with synaptic broken.

---

### Post by NaF on 2008-05-16
> **nicedude said:**
> Either use envyng program from the repositories or get the driver from nvidia's website and install yourself. This is the best 2 ways in my opinion of using your Nvidia card with up to date drivers.

COMMAND TO INSTALL ENVYNG
sudo apt-get install envyng envyng-gtk

this will install envyng and its GUI frontend with the -gtk 

to run it just put following in a terminal

envyng-gtk   

then use it to install your nvidia driver for you, thats all it is for and it works pretty well.

also you should uninstall the nvidia drivers installed earlier

sudo synaptic 

this will open the synaptic package manger once in there just search for nvidia and select the ones you installed for uninstallation

GOOD LUCK & feel free to PM me if you need more help I will be around a couple more hours so I can answer you pretty quick ( Click my name and choose send private message :-) )

I couldn't install envyng-gtk and really couldn't uninstall the nvidia drivers, but I could REINSTALL :D, so it's all working now. Thanks:) synaptic - nvidia (the one with red background and a cross if it failed uninstall) - reinstall packagde. That did it for me at least.

> **EXCiD3 said:**
> Here is information on fixing your synaptic problem: [http://www.debian-administration.org/articles/251](http://www.debian-administration.org/articles/251)

It looks like you just need to comment out "-e" or "set -e" from the removal scripts that are blocking synaptic from functioning. Follow the pages instructions to locate scripts, then edit them with nano and try again. Then you can work out your nvidia problem. With synaptic broken, trying to use envy to install your nvidia drive will do absolutely no good until synaptic is fixed because envy will not be able to download packages it needs, in fact you probably cant even download and install envy with synaptic broken.

:confused: please note where I put the thread "absolute beginner" I seriously don't understand a word you're saying :oops:

---

### Post by EXCiD3 on 2008-05-16
haha, sorry for the techincal jargon. can you post the entire output of the synaptic error? we can use this to narrow down the synaptic problem and get that fixed first. once that is out of the way we can get your nvidia issue solved.

---

### Post by nicedude on 2008-05-16
sorry didn't see he said synaptic was broken as well. can you use aptitude with synaptic broken? I just would like to know as I have never broken my synaptic ( Knock on Wood ).

---

### Post by EXCiD3 on 2008-05-16
Synaptic is a graphical interface for aptitude. In his case its aptitude that is broken. If aptitude is broken then you wont be able to use Synaptic since it uses aptitude to do the stuff behind the scenes. Sometimes the Fix Broken Packages works in synaptic but this is one of the cases where it cant unfortunately.

---

