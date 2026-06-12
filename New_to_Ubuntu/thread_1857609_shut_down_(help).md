---
title: "shut down (help)"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by wolfman21 on 2011-10-10
hello i am new to Ubuntu and am having a problem when i turn off my computer the internet light indicates that the is still going,just like if i was on the internet but the computer is off. any help or explication would be a big help 

thanks

---

### Post by Lisiano on 2011-10-10
If your PC fully shuts down (Fans stop, HDDs stop, no LEDs are blinking and [if laptop] screen is off) then the network LEDs don't really show anything. It just means that there is a cable connected and it is connected to a router/another PC. So no need to be alarmed.

---

### Post by Lisiano on 2011-10-10
I'll reply to the PM here instead
> may i ask why it only dose it with Ubuntu ? :)
Simple my dear Watson. AFAIK Windows by default does everything how it pleases, disregarding the BIOS while Linux respects what you set up in your BIOS, you probably have "Allow wake from network" or the like set there. If you don't explicitly tell Windows to allow WoL, it'll just turn it off, same for Linux but it respects what you set (Or the manufacturer) in the BIOS.
So if you really don't like the light, either mechanically turn off your PC (Pull the plug) or turn off WoL in the BIOS.

---

### Post by wolfman21 on 2011-10-10
thank you....:)

---

