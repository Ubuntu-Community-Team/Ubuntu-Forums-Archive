---
title: "Reset Baytrail Tablet BIOS to Default from Terminal"
date: 2017-10-31
forum: New to Ubuntu
---

### Post by byteman2 on 2017-10-31
Hi
I've installed 17.10 Cinnamon onto my Baytrail Z3735F Atom Android Tablet. Well it worked almost fine except for an annoying refresh rate problem.
Problem was not present in the Bios screens previously, but after installing this version on Ubuntu it was also flickering in the BIOS so, in order to solve the refresh rate problem, I've changed some settings in the BIOS related to the active display, which were probably disabling the tablet screen and putting the picture on some other display, and eventually I don't have any image. 

Luckily I've had teamviewer remote desktop on the tablet so I can reach the OS from my other computers. :D I feel like I've cut the brunch I was sitting on but I haven't lost connection with the Mars Rover. :D

I've found these set of commands somewhere else, 

```
[COLOR=#111111][FONT=Consolas]modprobe nvram
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]dd if=/dev/zero of=/dev/nvram[/FONT][/COLOR]
```

but I get this error :

modprobe: ERROR: could not insert 'nvram': Operation not permitted

Is there any command to reset the BIOS to default values from Linux terminal?

---

### Post by mörgæs on 2017-10-31
Hi, welcome to the fora.

If you edit the title and change it to a more informative one there is a better chance that you will get an answer.

---

