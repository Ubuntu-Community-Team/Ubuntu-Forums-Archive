---
title: "Nvidia GE Force4 MX4000 cannot work"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by zenholy on 2008-06-06
I have replaced the old graphic card with this nvidia ge force4 mx 4000 for my Pentium III processor 751 MHZ 384 MB RAM XP 2002 SP2.
However it seems it is not working...when I want to fix the web cam it wouldn't work..when I play games it wouldn't work.  When I click the properties of the computer and general...it doesn't show I have NVidia?

Can someone help?   Thanks

---

### Post by mgranet on 2008-06-06
You should install the nvidia-glx package.

And post the output of ```
lspci 
```

---

### Post by bumanie on 2008-06-06
I think the mx4000 needs a nvidia legacy driver not nvidia-glx. Nvidia glx started a bit later; with the mx5200 - or there-abouts. When I had a mx4000, on feisty it installed OK via restricted drivers, but on gutsy, could only install via console and stopping gdm. Have a new computer now therefore I can't tell you whether hardware drivers works or not, but it should. If not you may have to use the console installation method which can be a bit of a pain as it has to be reinstalled with each kernel update.

---

### Post by davidsrsb on 2008-06-06
The MX4000 dates back to 2003, so the nvidia-glx-legacy is the best bet to try. This was a DirectX7 generation chip

---

### Post by zenholy on 2008-06-06
Thanks for the suggestions.  How and where do I get the nvidia-glx driver ? Thanks

---

### Post by davidsrsb on 2008-06-08
Look in the standard repositories using Synaptic for
nvidia-glx-legacy
This should be in multiverse
The MX family aremore of a GeForce2 chip than a "4" - marketing
I don't thing the nvidia-glx is the right driver, though I could be wrong. Nvidia documentation on which chip needs which driver is poor

---

### Post by alienexplorers on 2008-06-08
You could use ENVY to load your driver.  Select manual install and then select the last one in the list of 3 drivers.  ENVY can be found in the repositories.

---

