---
title: "Sharing printer"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Sydius on 2008-05-26
I am sharing a printer (with sharing enabled in the administration/printing).  I checked the box under server settings to share local printers, and I made sure sharing is enabled for the specific printer as well.  Yet, another computer, also using Ubuntu (8.04 for both), can't see the printer.  Any advice?

---

### Post by iaculallad on 2008-05-26
> **Sydius said:**
> I am sharing a printer (with sharing enabled in the administration/printing).  I checked the box under server settings to share local printers, and I made sure sharing is enabled for the specific printer as well.  Yet, another computer, also using Ubuntu (8.04 for both), can't see the printer.  Any advice?

You could follow-up with this [thread]("http://ubuntuforums.org/showthread.php?p=163882") for sharing the CUPS printer.

---

### Post by sam_delta on 2008-05-26
try, in the client  ubuntu machine, go into system>administration>printing then select on "show printers shared by other systems", ,then try to click on "new printer" in the top menu ,  and let it search

sam

---

### Post by perce on 2008-05-26
After doing what sam_delta saied, if it still doesn't work, you can try restarting CUPS on both machines. I don't know if it is strictly needed, but for me it helped. To restart CUPS:

```

sudo /etc/init.d/cupsys stop

```

followed by 

```

sudo /etc/init.d/cupsys start

```

or just a reboot.

---

