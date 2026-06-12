---
title: "Black square around the screen"
date: 2020-03-27
forum: New to Ubuntu
---

### Post by maorvnkl12 on 2020-03-27
Hello all, 
I'm New to Linux im using Lubuntu ,
I have a problem with my screen, i have a Black square around the screen( top,left and right) its like the resolution is not correct but i checked and my resolution is on max, this is how the operating system need to look like?
(I checked "additional drivers" and i have nothing to install there).

---

### Post by CelticWarrior on 2020-03-29
Welcome.

"Resolution is on max" (whatever you mean by this) doesn't mean it is the correct native resolution for your monitor.

---

### Post by Impavidus on 2020-03-29
Also, what kind of connection do you have between computer and monitor? As you use Lubuntu, I guess you have a somewhat older system. The old analogue connections may require some tweaking using the monitor settings.

And no, there isn't supposed to be a black bar around the screen.

---

### Post by grahammechanical on 2020-03-30
There is a fallback video mode that loads if we don't have the correct video driver or the video driver does not load. That fallback video mode puts a black boarder around the screen (if I remember correctly). Icons and stuff seem overly large as well.

Proprietary video drivers often drop support for older video cards. And older proprietary video drivers not work with the latest Linux kernels. This happened to me. So, I stopped using the proprietary video driver and I find that the open source video driver called Nouveau works fine with my older Nvidia card.

Regards

---

### Post by mörgæs on 2020-03-31
We need a hardware description. Please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it onto the command line, run it and post lshw.txt in CODE tags.

---

