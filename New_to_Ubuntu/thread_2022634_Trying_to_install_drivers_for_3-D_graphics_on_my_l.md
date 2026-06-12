---
title: "Trying to install drivers for 3-D graphics on my laptop, help!"
date: 2012-07-11
forum: New to Ubuntu
---

### Post by JakeConnors on 2012-07-11
I have a Lenovo ThinkPad 400 (2767) running ubuntu 12.04 LTS currently. I have tried several times to find graphics card drivers for my computer and along the way made several mistakes and screwed up some things which I do not completely understand (/usr/lib/ stuff etc.) 

Here is the output of lspci | grep VGA:

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV620 [Mobility Radeon HD 3400 Series]

glxinfo:

name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

glxgears: (same as above)

Thank you for your help!

---

### Post by Redblade20XX on 2012-07-11
Take a look here : [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

Hopefully it helps!

- Red

---

### Post by JakeConnors on 2012-07-11
Hi, thank you for pointing me to that. I followed the instructions, and first removed my old fglrx, then replaced it and reconfigured. Unfortunately for some reason fglrxinfo still displays error messages. Do you have any more ideas? Is there anything I could post that would help you figure out what is going on here?

Thanks again!

---

### Post by JakeConnors on 2012-07-11
I also forgot to mention, but I need something that also has openGL support, as I'd like to be able to play minecraft using this laptop as well. Regardless, at this point no 3-D graphics work though.

---

### Post by QIII on 2012-07-11
Many users have problems with hybrid Intel/ATI graphics.

I'm on the train home from work and typing on my cell phone.  If I have a chance later tonight I'll try to post some links that may help.

For now, read through the wiki in my signature.  Somewhere in there I included a link to a forum post from someone who had gotten his system to work.

---

