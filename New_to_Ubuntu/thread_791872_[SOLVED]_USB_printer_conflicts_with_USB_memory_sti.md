---
title: "[SOLVED] USB printer conflicts with USB memory stick"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-05-12
My Brother MFC-240c, won't scan. And it's brscan driver (or something) made my PQI 1 gig USB memory stick fail. The memory won't mount, so it's useless.

So this morning, I uninstalled the Brother software and tried to reinstall it using Synaptic.

XSane says "no device found"

and I already added the 

#brother
SYSFS{idVendor}=="04f9",MODE="666",GROUP="scanner"
LABEL="libsane_rules_end"

to /etc/udev/rules.d/45-libsane.rules

on reboot, XSane says: "no device found"

anybody know what to do?

---

### Post by timcredible on 2008-05-12
an easy solution is to replace that printer with an hp printer/scanner.  there's no setup involved for hp printer/scanners except plug it in.  i've connected about 8 hp printer/scanners to linux machines, they all worked great.  however, having said that, i would still recommend checking linuxprinting.org before buying anything.

---

### Post by Mark_in_Hollywood on 2008-05-12
I've somewhat solved this problem by reinstalling the brother scanner driver.

I can't get a handle on the fax portion, but CUPS shows the printer, the brfax and a pdf-printer. Maybe that's good enough for now.

thanks, community

---

