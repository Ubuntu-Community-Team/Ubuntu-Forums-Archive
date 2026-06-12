---
title: "Epson Driver Install &quot;Failed to satisfy all dependencies&quot;"
date: 2014-05-23
forum: New to Ubuntu
---

### Post by Drowz0r on 2014-05-23
Hello all

Having trouble installing some Epson Printer Drivers.

Freshly downloaded from the Epson website, the XP-212 model.

I had the exact same problem installing the drivers on Bodhi linux however the solution was simple. On Bodhi, I attempted to install the drivers and it gave me a huge list of unmet dependencies. It offered to install these dependencies and I opted for that... it installed them, then installed the driver and works fine.

I attempted to install the drivers on Ubuntu and it came up with the same dependency error and offered to "repair" the problem but all it did was seemingly reverse the install. It didn't install the dependencies or give me a list of them for me to install myself as far as I could see... but then the software updater popped up and installed about half a meg of stuff, so I attempted to run the driver installer again but the same error of unmet dependencies appears and now with the message "Failed to satisfy all dependencies (broken cache)". Broken Cache wasn't there before.

I have tried:

```
sudo apt-get update
```

I have tried rebooting

I have tried marking the .deb as executable.

Drivers won't install :(

---

### Post by Vladlenin5000 on 2014-05-23
Are you sure XP-212 isn't already supported? We don't install drivers for any of our Epson printers and we have plenty.

Now, if you really need the Epson driver, it should just work. Assuming you downloaded the correct version (32 or 64-bit) from this page [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=PT&CN2=&DSCMI=22523&DSCCHK=a86333b2d76e3c6372657171525d2e0902e3c9e1](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=PT&CN2=&DSCMI=22523&DSCCHK=a86333b2d76e3c6372657171525d2e0902e3c9e1) , the "full feature" (the "generic" should be exactly the same already included in Ubuntu), how did you (tried to) install it? Software Center, Synaptic...?...

Anyway, you have a new problem now that requires fixing before any other attempt. Try ```
sudo dpkg --configure -a
``` then, to avoid pending installations ```
sudo apt-get install -f
``` an finally you should then do ```
sudo apt-get update
``` followed by ```
sudo apt-get dist-upgrade
```

---

### Post by Drowz0r on 2014-05-23
Oh, look at that... I did a quick Interslice search on what you said and apparently you can just go into "printers" and add it.

Splendid. Thanks.

---

### Post by Vladlenin5000 on 2014-05-23
That's exactly what I meant. Glad it works for you. It certainly does for us because the printers only work with the generic driver anyway ;)
Newer models like your have the "full feature" option which should - I think - give you the same eye candy the Windows version has.
Now, I'm curious about what dependencies such driver might require. A huge list according to you and that is really puzzling.

---

### Post by Drowz0r on 2014-05-23
Yeah I wish I had written it down, probably around A4 size list if you had to print it... on Bodhi it said "unmet dependencies...." then that big ol' list.

Bodhi is really lightweight though so... it seemingly needs dependencies installed before you use anything, in my experience...

---

### Post by Vladlenin5000 on 2014-05-23
Indeed. Bodhi uses the Enlightment window manager which is ultra-light hence stripped down a notch.

---

### Post by kilha on 2014-05-27
So I am having similar problem.
Ubuntu 14.04 (64) fresh install.
Plug USB printer.
Go to "printing"
Click "add printer"
The system correctly detects USB printer Epson XP-200
Select it and click "forward".
System suggests download driver 201204w (or something like that).
Select this option then click "forward".
System takes some time, then asks me for adm password in order to install. After that takes a lot of time then the aplication hangs and stop responding.

Forced close "add printer aplication". Started all over again with same results.

Tried  dloading the driver (.deb) from [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=17707&DSCCHK=7eb2b95601a4a0a65adc04e65e3667e0c9dda153](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=17707&DSCCHK=7eb2b95601a4a0a65adc04e65e3667e0c9dda153) and install with GDebi and got the "Failed to satisfy all dependencies" error (no list of dependencies thou).

Any ideas?

---

### Post by kilha on 2014-05-27
Forgot to mention printer worked just fine with previous Ubuntu 12.04 (32).

---

### Post by pdc on 2014-05-27
assuming you downloaded the file [COLOR="#008000"]epson-inkjet-printer-201204w_1.0.0-1lsb3.2_amd64.deb[/COLOR] and saved it to your [COLOR="#0000FF"]Downloads[/COLOR] directory;

I wonder if you attempt an install from the terminal, if you can get a much more detailed error message; (eg wondering if libtiff4 is an issue; as it has been withdrawn recently)

so the commands would be 

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]sudo dpkg -i epson-inkjet-printer-201204w_1.0.0-1lsb3.2_amd64.deb[/COLOR]

I am just wondering if that will catch a printout of the problem(s); and if you could paste them back here

---

### Post by kilha on 2014-05-27
Yes i try with the 201204w first and then with the 1.4.0 and both gave me the same:

:~/Downloads$ sudo dpkg -i epson-inkjet-printer-201204w_1.0.0-1lsb3.2_amd64.deb

(Reading database ... 175188 files and directories currently installed.)
Preparing to unpack epson-inkjet-printer-201204w_1.0.0-1lsb3.2_amd64.deb ...
Unpacking epson-inkjet-printer-201204w (1.0.0-1lsb3.2) over (1.0.0-1lsb3.2) ...
cups stop/waiting
cups start/running, process 3861
dpkg: dependency problems prevent configuration of epson-inkjet-printer-201204w:
 epson-inkjet-printer-201204w depends on lsb (>= 3.2); however:
  Package lsb is not configured yet.

dpkg: error processing package epson-inkjet-printer-201204w (--install):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Errors were encountered while processing:
 epson-inkjet-printer-201204w

---

### Post by pdc on 2014-05-27
what does 

> [COLOR="#FF0000"]dpkg -l | grep lsb[/COLOR] give; if you copy this command; and **paste** it into a terminal; if you can copy and paste back the result please

---

### Post by kilha on 2014-05-28
"~/Downloads$ dpkg -l|grep lsb
iU  epson-inkjet-printer-201204w                          1.0.0-1lsb3.2                                       amd64        Epson XP-20/XP-101/XP-200/XP-201 Series - Epson Inkjet Printer Driver
rc  epson-inkjet-printer-escpr                            1.4.0-1lsb3.2                                       amd64        Epson Inkjet Printer Driver (ESC/P-R) for Linux
iU  lsb                                                   4.1+Debian11ubuntu6                                 all          Linux Standard Base 4.1 support package
ii  lsb-base                                              4.1+Debian11ubuntu6                                 all          Linux Standard Base 4.1 init script functionality
iU  lsb-core                                              4.1+Debian11ubuntu6                                 amd64        Linux Standard Base 4.1 core support package
iU  lsb-cxx                                               4.1+Debian11ubuntu6                                 amd64        Linux Standard Base 4.1 C++ support package
iU  lsb-desktop                                           4.1+Debian11ubuntu6                                 amd64        Linux Standard Base 4.1 Desktop support package
iU  lsb-graphics                                          4.1+Debian11ubuntu6                                 amd64        Linux Standard Base 4.1 graphics support package
iU  lsb-invalid-mta                                       4.1+Debian11ubuntu6                                 all          Linux Standard Base sendmail dummy
iU  lsb-languages                                         4.1+Debian11ubuntu6                                 amd64        Linux Standard Base 4.1 Runtime Languages package
iU  lsb-multimedia                                        4.1+Debian11ubuntu6                                 amd64        Linux Standard Base 4.1 Multimedia package
iU  lsb-printing                                          4.1+Debian11ubuntu6                                 amd64        Linux Standard Base 4.1 Printing package
ii  lsb-release                                           4.1+Debian11ubuntu6                                 all          Linux Standard Base version reporting utility
iU  lsb-security                                          4.1+Debian11ubuntu6                                 amd64        Linux Standard Base 4.1 Security package
"

---

### Post by kilha on 2014-05-28
Ok guys, thank you for your attention. I solved the problem... unusually it is necessary to install the scan driver BEFORE install the print driver. I tryed that and things now work perfectly.
So the order is:
1)install iscan-data_1.28.0-2_all.deb
2)install printer the normal "add printer" way
3)install iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb
4)install wireless driver iscan-network-nt_1.1.1-1_amd64 (witch I did yet wireless still not working)

---

