---
title: "&quot;No screens found&quot;"
date: 2013-07-02
forum: New to Ubuntu
---

### Post by sal55 on 2013-07-02
Using Ubuntu 12.04 under VirtualBox on Windows 7. Worked well for a day or so, now it's starting to fall apart!

On booting (ie. starting Ubuntu under VirtualBox), it either hangs indefinitely, or goes into console mode.

When it hangs, I can press keys and they are echoed on an otherwise blank screen, but nothing else happens (not even with ^C or ^Z).

In console mode, the main error is "No screens found" when it tries to start X. The same if I type 'startx'. If I try and run a graphics application, it says "Cannot open display".

There is a file /etc/X11/xorg.conf. What else is it missing to come up with the above message?

xorg.conf:
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

---

### Post by sal55 on 2013-07-02
> **sal55 said:**
> Using Ubuntu 12.04 under VirtualBox on Windows 7....

In console mode, the main error is "No screens found"

I should have just done a search for that error. Another thread suggests doing this:

sudo dpkg-reconfigure xserver-xorg

which sort of worked (after installing xserver-xorg) and typing startx. But I
don't know if it will fix the hanging problem or if it will work every time. This
system is very fragile!

---

