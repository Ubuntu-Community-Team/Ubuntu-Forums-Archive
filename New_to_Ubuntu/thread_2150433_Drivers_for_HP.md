---
title: "Drivers for HP"
date: 2013-06-01
forum: New to Ubuntu
---

### Post by saikiransunny on 2013-06-01
I recently moved on from windows to ubuntu. I lost all the default drivers(coolsense and others). Are there any ways to regain them?
Any web sites(links)?
Thanks in advance.

---

### Post by 3rdalbum on 2013-06-01
No, Windows stuff doesn't work in Linux and vice-versa.

Does your hardware work? If so, you have all the drivers you need.

---

### Post by Feathers McGraw on 2013-06-01
Hi saikiransunny,

Trying to understand why you need the software... as 3rdalbum said the windows program won't work, but there may be equivalents for Ubuntu. I just googled it, and this is what HP Coolsense apparently does:


1) "Automatic detection system uses the motion sensor in your notebook PC to sense where your PC is being used and automatically adjust the cooling".

All laptops run the fan at higher speeds when the temperature increases inside the laptop, regardless of how much the laptop is being moved around. Not sure why how much you're moving the laptop around makes any difference to how much cooling you need.


2) "HP Thermal Assistant software allows you to specify your cooling preferences (maximum cooling, quiet or optimized performance) and automatically shifts into that mode when you're mobile."

Again, temperature control is automatic. There are fan control programs on Ubuntu [(see here)]("http://askubuntu.com/questions/22108/how-to-control-fan-speed?rq=1") but I wouldn't go tinkering unless there's something wrong.

Is your laptop overheating?

Feathers

---

### Post by saikiransunny on 2013-06-02
yes, it is over heating.

---

### Post by mastablasta on 2013-06-03
what are the system specs then? do you have AMD or nvidia GPU? if so you need to install additional drivers.

---

### Post by Feathers McGraw on 2013-06-03
My HP laptop is also prone to overheating.

Partly it is due to bad hardware design, the fans on a load of their laptops catch a load of dust and effectively make a draught excluder in front of the vent. Not helpful, especially as to clean the fan properly you'd have to disassemble the entire laptop (the fan is the last thing you get to).

If you have an AMD graphics card then try the solution I posted in this thread (post no.4), basically you need to use a different driver for the card and it won't throw off so much heat:

[http://ubuntuforums.org/showthread.php?t=2118419](http://ubuntuforums.org/showthread.php?t=2118419)

Has worked very well for me and seems to have worked equally well for others.

Feathers

---

### Post by Mark Phelps on 2013-06-03
What make and model PC are you using? IF it's a laptop, and it's a recent one that utilizes switchable graphics, you will have some work ahead of you -- as that doesn't work well in Linux.

---

