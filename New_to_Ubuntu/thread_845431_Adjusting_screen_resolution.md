---
title: "Adjusting screen resolution?"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by cinohpa on 2008-06-30
So, I managed to get the proper nvidia driver installed on my machine and I went into applications>other>graphics and screens and in there I selected "Model:lcd panel 1680 x 1050" as that is what my screens native resolution is. Underneath where is says "resolution" I cannot find a 1680 x 1050 option and so my display doesn't look right. What should I do about that to make it match my native? 

Also does the refresh rate matter really?

thanks.

(using hardy btw.)

---

### Post by sayakb on 2008-06-30
At a terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And try again.

---

### Post by cinohpa on 2008-06-30
eh that doesn't really help. That just unmounts my nvidia driver and puts me back where I started which doesn't really give me any resources to try anything new.

Is there anything else I can do? I'm trying to understand why I can choose the right lcd type but then ubuntu can't supply me a resolution to match that.

---

### Post by sayakb on 2008-06-30
Did you reboot after doing that?

---

### Post by philinux on 2008-06-30
sudo dpkg-reconfigure -phigh xserver-xorg

Does not work in hardy, xorg.conf is now a stub file with no resolution data, on a clean install.

Without the -phigh it only configures mouse and keyboard.

---

### Post by sayakb on 2008-06-30
Didn't know tht.. :(

---

### Post by philinux on 2008-06-30
Yep found this out soon as Hardy got installed on my new machine back in Early April.

[http://ubuntuforums.org/showthread.php?t=750305](http://ubuntuforums.org/showthread.php?t=750305)

Some good info here too.

---

