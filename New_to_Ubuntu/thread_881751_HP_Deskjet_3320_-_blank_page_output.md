---
title: "HP Deskjet 3320 - blank page output"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by sharad.sharma on 2008-08-06
I set up a dual boot (Windows XP and Ubuntu 8.04) to switch to Ubuntu.
My HP deskjet 3320 printer outputs a blank page when I try to print a test page or from OpenOffice.
The USB printer is detected by the system when I connect but it gives a blank output.
I tried the recommended drivers from foomatic and then downloaded the PPD file as well but the problem persists.
The printer prints normally from Windows XP.
Please help

---

### Post by phidia on 2008-08-06
Try installing the hplip package, if it isn't already installed, and set up your printer from that.

---

### Post by sharad.sharma on 2008-08-07
hplip was installed already..That didn't help
Any other solution/check?

---

### Post by ramjet_1953 on 2008-08-07
If it isn't already installed, install the Python QT3 bindings.

Type this in a terminal:

```
sudo apt-get install python-qt3
```

Next, run the HP Setup utility.

```
sudo hp-setup
```

A window should open and guide you through the setup.

After a test page has printed, run this command, to view all of the functions of HPLIP.

```
hp-toolbox
```

Regards,
Roger :cool:

---

### Post by sharad.sharma on 2008-08-07
Thanks Roger.. Printer working fine now :)

---

