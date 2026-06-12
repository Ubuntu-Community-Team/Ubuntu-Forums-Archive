---
title: "Trouble with Nvidia Accelerated Graphics Driver"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by Great Blue Heron on 2008-05-07
Hi,

I recently installed Ubuntu 8.04 AMD64 as dual boot with Windows XP. I am new to linux.

My problem is with the Nvidia Accelerated Graphics Driver that is under  Hardware Drivers. I selected the check mark to enable the driver. It installed itself and then said I needed to restart my computer. When the computer restarted, the screen when blank after the Ubuntu flash screen. I could here the drums playing in the background but I could not see anything. 

I booted into Widows XP and did a Google search and found that I need to press Ctrl+Alt+F1 and then type in: ```
sudo dpkg-reconfigure -phigh xserver-xorg 
```

That worked and I was able to see the Ubuntu login screen and log in successfully. Under Hardwar Drivers it shows that the Nvidia Accelerated Graphics Driver is not selected.

I have dual monitors that I would like to set to Span Mode and I would also like to enable Visual Effects. I don't know where to go from here. Please Help!

System Specs:
Motherboard: ASUS M3A32-MVP Deluxe Wifi
CPU: AMD Athlon 64 X2 6400+
Video Card: Nvidia EVGA 8800 GT Superclocked
Hard Drive: 500 GB Samsung
RAM: 4 GB

---

### Post by philinux on 2008-05-07
If the default install failed then I'd use envy.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Great Blue Heron on 2008-05-07
Philinux,

No luck. I let EnvyNG automatically select the driver and it did the same as before. The screen went blank right after the Ubuntu splash screen. 

I looked at the instructions in the FAQ to get back to open source drivers. I had to press Crtl+Alt+F1 and type in: ```
envyng --uninstall-all
```

Now I'm back to where I was before.

Got anymore ideas?

---

### Post by philinux on 2008-05-07
What have you got under system>admin>Hardware Drivers

---

### Post by Great Blue Heron on 2008-05-08
Hey Phil,

I attached a screenshot of Hardware Drivers.

---

