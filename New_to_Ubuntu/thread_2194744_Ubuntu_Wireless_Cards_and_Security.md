---
title: "Ubuntu Wireless Cards and Security"
date: 2013-12-20
forum: New to Ubuntu
---

### Post by g.137.314.789 on 2013-12-20
Hi:

Can people send you emails with spyware that can infiltrate your Ubuntu  system?

Also, is there a usb wireless card I can buy from a regular big box store like Target or Best Buy that will work Ubuntu 12.04?

---

### Post by PaulBx on 2013-12-20
They can send you emails but the malware or viruses won't run, if I'm not mistaken. That's one of the nice things about Linux - you don't always need to be cleaning your system or burning hardware resources running virus checkers and spybot cleaners and registry cleaners.

Why do people want to go with 12.04 when 13.10 is available? Maybe I'm ignorant of some factors in this choice, but it seems you are more likely to have drivers in a later version. As to devices, the best you can do is search the forum for what works, make a list, and then go to the store and try to find something in or close to what is in your list (see also any available hardware compatibility lists). Unfortunately, the chipset is what matters, and hardware vendors have a bad habit of changing chipsets without changing product model numbers, so it is a bit of a crap shoot. But my philosophy has always been to just go ahead and gamble. You are not actually risking much; hardware is cheap, after all. What's expensive is investing piles of your time messing with software.

It's a bit different from the Windows world where almost every piece of hardware is guaranteed to work (that's what hardware manufacturers test against). But I would put up with this minor inconvenience to eliminate all the other BS you have to put up with in the Windows world.

---

### Post by Impavidus on 2013-12-20
Yes, people can send you spyware and yes, it can infiltrate your system, but only if the malware has been designed for Linux (which is very rare, but possible) and you activate it yourself. Unless of course it manages to use a security hole in your email program or web browser, which is why we keep them always updated. Malware is not a big risk, but you have to pay attention. Have a look at the security subforum for some more information.

You can search the internet to find out whether other people have had success on Ubuntu with the wireless cards you consider buying. Sometimes you can return the hardware to the store if it doesn't work with your computer. I don't know about the stores you mentioned, they're foreign to me.

Right now, it doesn't really matter whether you install 12.04 or 13.10. Usually I recommend LTS releases, but in this case there won't be any more intermediate releases before the next LTS, and not having the hassle of the intermediate upgrades is the primary reason to stick to LTS releases.

---

### Post by kurt18947 on 2013-12-20
> **g.137.314.789 said:**
> Hi:

Can people send you emails with spyware that can infiltrate your Ubuntu  system?

Also, is there a usb wireless card I can buy from a regular big box store like Target or Best Buy that will work Ubuntu 12.04?

Wireless adapters and linux are a bit of a tricky topic and you're wise to ask before buying.  One adapter that seems well regarded and available is Netgear's WNA1100.  The only glitch I recall with that adapter is some people needing to turn off hardware encryption when connecting to a WPA / WPA2 router.  I have that adapter and haven't had a problem with leaving hardware encryption on its default enabled setting.  Just because one Netgear adapter works doesn't mean all Netgear adapters work.  Some Netgear devices are very difficult or impossible to get to work with linux.  I've had excellent success with Realtek RTL8192SU chipset based devices.  I have a Trendnet TEW-649UB adapter based on the RTL8192 chipset that is plug 'n' play on 12.04 through 13.10.  I believe Tenda makes an inexpensive RTL8192SU based adapter as well but I'm not certain about the model.  RealTek 8192SU devices have one possible glitch.  When I put a machine in suspend then resume it, the wifi adapter doesn't wake up.  Unplug then plug back in and it works.  There's a simple fix for that.  The web site wikidevi.com has information about chipsets and devices built with them.

Manufacturers have a disconcerting habit re wifi adapters, they change chipsets and there's often no easy way to tell.  I used to recommend Dlink DWA-131 as plug 'n' play because I had one and it was - it was a twin to the TrendNet TEW-649UB.  A few weeks or months later someone bought one and it didn't work.  Turns out Dlink switched chipsets to a chip that wasn't plug 'n' play and didn't change the model #.  The only way to tell was to read the data tag on the device; the one that didn't work was a DWA-131 Rev. B or similar.

---

