---
title: "Modifying Live Image to boot to external monitor"
date: 2016-02-28
forum: New to Ubuntu
---

### Post by wikilor on 2016-02-28
Hi everyone, I have a problem with an old laptop, it has a broken screen and due to the fact that it is still relatively new I would like to re-purpose it. The only problem I encounter is that it doesn't switch automatically to the external screen output, making it impossible to see or configure anything (keyboard shortcuts don't work). Now what I would like to know is:

-what config should I modify in the live image file (prior to loading it in the usb) to switch to the external hdmi/vga output ?
So that when it first boot I can see what I'm doing in the screen.
Thanks in advance Wikilor :).

Laptop conditions:

The laptop has been torn apart, and is now a bare bone motherboard (the broken screen has been removed).

Laptop specs:

Pavillion DV6 3102sl pentium P6100 4GB ram ATI mobility radeon 5470 512mb GDDR5

---

### Post by DuckHook on 2016-03-01
Yours is one of those "challenges". It's great for people who want to take on the challenge for the sake of the challenge itself, but you have to be fully aware of how difficult things will be.

From your description, the system BIOS may be set to output only to the laptop screen. I am not aware of any Ubuntu boot parameter that can be set to output to a different monitor without having the first monitor from which to view the system BIOS.

Some BIOSes default to mirrored output if it detects an external monitor. Have you tried simply running a LiveUSB/DVD session with an external monitor attached? If nothing shows, then I'm afraid you may need to change a BIOS setting, and I don't know how to do that without an initially functioning Laptop screen. Other contributors may be more helpful.

BTW, I applaud your desire to repurpose what amounts to a bare laptop MB/CPU. Just be aware that you are setting yourself a high hurdle. If you succeed, it should be very interesting what you end up doing with it.

---

### Post by DuckHook on 2016-03-01
<sigh>... brain cramp.

Postscript:

Most laptops have a function key combo that will toggle from internal to external output. All I had to do was check my old laptops to see this. The key combo varies from brand to brand, so you will have to look at your keyboard/users manual or google to find yours. On my old Dells, it's <Fn>+<F8>. Yours will likely differ. You can even try them all in series to see which one works. In the event that your laptop does not have this option, I'm out of ideas, but practically every laptop does, so it should be an easy fix.

---

