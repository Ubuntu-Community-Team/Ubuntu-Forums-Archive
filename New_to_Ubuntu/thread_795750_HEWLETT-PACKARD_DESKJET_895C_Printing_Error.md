---
title: "HEWLETT-PACKARD DESKJET 895C Printing Error"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by julieclaymore on 2008-05-15
Ubuntu Hardy Heron, HEWLETT-PACKARD DESKJET 895Cxi printer, using recommended HP Deskjet 895C driver, it has worked flawlessly with previous releases of Ubuntu, but with Hardy Heron it is not always printing pages correctly, often stopping mid-print and blinking the  paper light and showing in **messages**:
```

usblp0: Disabling reads from problematic bidirectional printer

```

in **user.log**:
```

prnt/backend/hp.c 561: ERROR 1009 media-empty-error; will retry in 30 seconds...

```

The printer stops with this error and the print job remains in the printer panel icon and with a reboot it still shows with an error and shows the long length of time between reboots as an error.

There is no stuck or missing paper in the tray but this problem persists. The test page prints out but anything else stops mid-print with multi-page prints and there is no option to continue the print job, only stop it.

Why is this happening in Hardy Heron and how do I resolve it, please?

---

### Post by julieclaymore on 2008-05-15
I haven't solved this so I still need help **please** but what I  noticed was...

When I print a document with success and try to print a second job it will fail and give the error I mentioned, followed by the printer paper light blinking... so I press the power button on the printer to turn off the printer then I go into CUPS [http://127.0.0.1:631](http://127.0.0.1:631) and JOBS and cancel the current stuck job and print out the other document I had to print out... this seems to allow another document for printing, but the issue crops up again after this and I have to repeat....

how do I solve this please so I don't have to go into CUPS every time this fails???

---

### Post by phidia on 2008-05-15
You could search for the most recent driver for that printer [here]("http://openprinting.org/printer_list.cgi") and/or check out what the linuxprinting site has to say about your printer.

---

