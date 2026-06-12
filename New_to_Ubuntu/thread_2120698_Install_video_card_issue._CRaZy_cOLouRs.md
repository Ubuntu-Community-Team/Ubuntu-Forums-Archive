---
title: "Install video card issue. CRaZy cOLouRs?"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by waxcan on 2013-02-27
So I'm trying to install the latest Ubuntu 64bit on my win7 box, dual boot.

[IMG]http://yfrog.com/scaled/landing/612/hhsunm.jpg[/IMG]
I runs this [ATI HD6450 graphics card]("http://www.ebay.com.au/itm/HIS-ATI-HD6450-1GB-HDMI-HTPC-Silent-Video-Graphics-Card-/290831458624?pt=AU_Components&hash=item43b6e7e140&_uhb=1#ht_14713wt_1037").

I rebooted from a DVD to install (tried two discs) and the colours went mad. I also plugged in one monitor into the original integrated graphics VGA port, but it received no input.

I'm using UNetbootin to try to install Ubuntu off a USB now, but its still downloading as I write.

Any ideas? I'll unplug the card if I have too, but I would want Ubuntu to support it as I'll swap between OSes (till I get a handle on terminal)

Works normal on Windows.

Drivers?
Ta
waxcan

---

### Post by Mark Phelps on 2013-02-27
Ubuntu 12.10 has default Radeon drivers that should work fine with that video card -- so, the display is confusing.

If this is a desktop, try booting the install DVD with only one monitor connected and seeing if you get a readable display.

Also, is the Radeon the only video chip you have in the PC, or do you also have other graphics chips -- like onboard Intel, for example?

---

### Post by waxcan on 2013-02-27
Thanks, I'll check shortly.
I have an integrated graphics -- "business and gaming graphics" -- which has a VGA port that's not issuing any signals to the monitors since I installed the new card.
Hope this works!

---

### Post by waxcan on 2013-03-03
Hi guys, no luck disconnecting either of the monitors, or running them in the old VGA slot.
I could disconnect the video card, but then perhaps I'll face the same problem when I run the OS.

---

### Post by darkcrimson on 2013-03-03
I would disconnect the card, run through your integrated VGA, and install first. Then, after the install is complete, plug in the card.

---

