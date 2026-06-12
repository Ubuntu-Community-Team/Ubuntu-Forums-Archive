---
title: "How to install drivers in Ubuntu?"
date: 2008-05-03
forum: Philippine Team
---

### Post by SHENGTON on 2008-05-03
Hello to Ubuntu Experts!

I have here 3 drivers for my motherboard --> Sound driver, LAN Adapter driver and the Chipset driver

The problem I have to install it using Terminal commands. I don't know the commands and how to use it. Hope you guys can help me.

Thanks and God bless!

---

### Post by loell on 2008-05-03
you don't need them :)

if ubuntu  supports your hardware, ubuntu will load the proper driver for you.

---

### Post by lixx on 2008-05-03
hmm weird ^^ dpat d ka na magiinstall ng mga drivers kc may drivers na
ang linux kernel para sa hardware mo, kung supported nga lng. ndi
ko pa naencounter mag install ng drivers manually sa terminal. pag
insert ng drivers manually sa system, oo. gagawin mo lng sudo modprobe <driver>, tas maiinsert na xa. btw, sa windows pla, drivers ang tawag. sa linux, mas appropriate ang term na "modules".

---

### Post by Aearenda on 2008-05-03
loell is right, if those drivers came with the motherboard, then the good news is you don't need them for Ubuntu - they will be Windows drivers.

---

### Post by SHENGTON on 2008-05-03
I guess the drivers that are already installed in are generic I guess. Correct me I'm wrong Ubuntu experts.

---

### Post by other guy on 2008-05-03
In Ubuntu Linux, it works or it don't. You can do things if the need is there. All the work is done for you while installing the operating system. If a part does not work as you expect. Then you can do somethings to fix it. If the hardware operates as you want, then no need to worry.

You can of course fine tune with various methods if you like. The magic is. If it works, hey your up and running. Move on to the fun stuff.

Keep in mind. Linux detects the hardware. Not the brand name of the parts you bought.
:)

---

### Post by loell on 2008-05-03
something like that.



P.S: stop addressing us as ubuntu experts, shy kami :lolflag:

---

### Post by Script Warlock on 2008-05-03
sa natandaan ko lang some firmware from xp transfer ko to ubuntu para sa genius vivid 3xe na scanner para gumana. actually its not an installation its just a copy paste..the rest provided na sa ubuntu

---

### Post by SHENGTON on 2008-05-03
Ahh ok, thanks for the quick reply guys. One more question, the drivers that already provided by Ubuntu are generics or not?

---

### Post by Aearenda on 2008-05-03
The point is, on Windows they are unnecessarily specific!

---

### Post by SHENGTON on 2008-05-03
What do you mean about the "unnecessary specific"?

---

### Post by Aearenda on 2008-05-03
Sometimes on Windows you have to load the drivers from a specific manufacturer, even though a perfectly good driver from another manufacturer who uses the same hardware chipset is present. The good side: you know (or hope) they have got their quirks sorted out. The bad side: endless driver installation after installing Windows. With Ubuntu, it is a joy NOT to have to install drivers after a reinstall (with the exception of proprietary stuff like Nvidia).

---

### Post by loell on 2008-05-03
you might wanna define what generic meant for you, in linux theres two kinds of drivers closed source and open source drivers

closed source drivers are generally provided by the vendor in binary format, some hardware vendors develop  open source drivers and some develop by exceptional coders.

---

### Post by saipu on 2008-05-03
Linux drivers are based on chipsets NOT manufacturer. Don't care what mobo manufacturer or soundcard manufacturer you use, as long as the chipset driver is supported it will works in linux! :)

---

### Post by adredz on 2008-05-03
> **SHENGTON said:**
> Ahh ok, thanks for the quick reply guys. One more question, the drivers that already provided by Ubuntu are generics or not?

if we talk about modules/drivers for a certain brand with different models, i think they are..eg. ATI video cards come with different models but they all have the same module. i came to this assumption for a fact that not all video card models work with the module provided by the manufacturers (ATI/NVIDIA) for linux. some models are very old for that module and some are too new. if you're lucky and your video card doesn't work out of the box :), then you have to tweak some the config things in your system.

---

### Post by SHENGTON on 2008-05-03
Ahh ok, thanks guys! :) Very informative.

---

