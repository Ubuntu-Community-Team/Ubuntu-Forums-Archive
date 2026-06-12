---
title: "[SOLVED] Stellarium question"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by loyaleagle on 2008-11-16
Hello everyone,

I just installed stellarium and when I go into the program, my screen go crazy. (To the point I can make anything out, including them menus. The only way out is to push the power button and reboot)

I have an ATI Radeon card and use the proprietary driver without nay issues. Everything works great. Is it an issue with Stellarium?


Thanks....

---

### Post by Cresho on 2008-11-16
disable compiz

---

### Post by jpkotta on 2008-11-16
Try it in windowed mode.
```
stellarium --full-screen no
```

---

### Post by loyaleagle on 2008-11-17
Worked great..... Full screen still flickers, but in window mode all is well.
Thanks for the suggestion!

---

### Post by NoWayBill on 2008-11-18
Personally I prefer Kstars to Stellarium.

---

### Post by texasjim on 2009-01-14
> **jpkotta said:**
> Try it in windowed mode.
```
stellarium --full-screen no
```

Good workaround, fixed me right up. The problem seems to be related to the graphics card, I had a 1G intel with an ATI 7500 card, stellarium worked fulscreen OOTB. Now, with a 1.8G intel and a lesser video card (ATI 7200) in vesa mode, it needs the 'full-screen no', or in the stellarium config file 'fullscreen false'.

 Jim):P

---

