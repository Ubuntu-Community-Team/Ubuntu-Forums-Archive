---
title: "Ubuntu 12.04 How to install USB-&gt;Parallel Printer"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by vikev on 2013-04-28
Hi. I have been trying for a while to install a parallel printer using Parallel to USB cable and  share it with CUPS. I read quite a lot threads on the net but I didn't find a solution to my problem.

I read about CUPS the following thing:
```

[COLOR=#000000][FONT=sans-serif]If you are using a USB->Parallel adapter, you'll want to do the following:[/FONT][/COLOR]
[LIST]
[*]Add your printer by selecting a different connection type (since usb and parallel will not be listed)
[*]Edit the file [COLOR=#006400][FONT=monospace]**/etc/cups/printers.conf**[/FONT][/COLOR]
[*]Change the DeviceID line to read: [FONT=monospace]DeviceID = parallel:/dev/usb/lp0[/FONT]
[*]...actually, it looks like the proper line is now: [FONT=monospace]DeviceURI parallel:/dev/usb/lp0[/FONT]
[/LIST]

```

However I do not know if the printer is mounted at all and if it is what is its address.

There is no /dev/usb on my server.

I would appreciate it if somebody who has dealt with this problem helps me as I am new to Linux and I am completely lost at the moment.

Thank you in advance.

---

### Post by gordintoronto on 2013-04-28
It's quite possible that someone could provide better help if you identified the devices. "I have a Gazorks 4000 printer attached to a Mubly 1234 USB to parallel adapter, and this has worked in Windows Vista in the past."

When everything is hooked up and turned on, if you run Printing and select "Add" does the printer appear?

---

### Post by vikev on 2013-04-30
After several plug/unplugs it appeared as /dev/usb/lp0 and it is up and running. Thanks :)

---

