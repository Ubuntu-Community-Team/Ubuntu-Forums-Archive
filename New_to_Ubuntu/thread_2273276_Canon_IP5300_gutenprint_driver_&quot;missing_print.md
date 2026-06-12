---
title: "Canon IP5300 gutenprint driver &quot;missing print filter&quot;"
date: 2015-04-11
forum: New to Ubuntu
---

### Post by workshop99 on 2015-04-11
I'm new to Ubuntu. Installed  14.04.02.  Installed printer using settings, printers.  It found the printer and gutenprint driver.  Installed and tried to print test page.  Printing starts  but stops and printer pop-up shows "There is a missing print filter for printer...".  If I wait long enough the test page sometimes slowly prints.
Help will be gratefully received!

---

### Post by pdc on 2015-04-11
if you can open a terminal please: if you hold down three keys: the control and the alt and the t keys all at once ...............

.............and then if you paste the command below into the terminal .......... and again paste needs 3 fingers: shift and control and the v keys ........unlike most programmes that just use the control and v keys .....................

```
dpkg -l | grep cups
```

......... next skill is to highlight all the answer using your mouse and the cursor; and then copy the results you have highlighted ........ using 3 keys: this time shift and control and c keys ............

............then if you can paste the result back here: if possible if you click on the hash-tag symbol that is in the middle line above and paste the result in there ........ that helps everyone ..........

____

---

### Post by workshop99 on 2015-04-12
Thanks for your reply, pdc; hope this is what you asked for:

dpkg -l | grep cup
ii  bluez-cups                                            4.101-0ubuntu13.1                                   amd64        Bluetooth printer driver for CUPS
ii  cups                                                  1.7.2-0ubuntu1.5                                    amd64        Common UNIX Printing System(tm) - PPD/driver support, web interface
ii  cups-browsed                                          1.0.52-0ubuntu1.4                                   amd64        OpenPrinting CUPS Filters - cups-browsed
ii  cups-bsd                                              1.7.2-0ubuntu1.5                                    amd64        Common UNIX Printing System(tm) - BSD commands
ii  cups-client                                           1.7.2-0ubuntu1.5                                    amd64        Common UNIX Printing System(tm) - client programs (SysV)
ii  cups-common                                           1.7.2-0ubuntu1.5                                    all          Common UNIX Printing System(tm) - common files
ii  cups-core-drivers                                     1.7.2-0ubuntu1.5                                    amd64        Common UNIX Printing System(tm) - PPD-less printing
ii  cups-daemon                                           1.7.2-0ubuntu1.5                                    amd64        Common UNIX Printing System(tm) - daemon
ii  cups-filters                                          1.0.52-0ubuntu1.4                                   amd64        OpenPrinting CUPS Filters - Main Package
ii  cups-filters-core-drivers                             1.0.52-0ubuntu1.4                                   amd64        OpenPrinting CUPS Filters - PPD-less printing
ii  cups-pk-helper                                        0.2.5-0ubuntu1                                      amd64        PolicyKit helper to configure cups with fine-grained privileges
ii  cups-ppdc                                             1.7.2-0ubuntu1.5                                    amd64        Common UNIX Printing System(tm) - PPD manipulation utilities
ii  cups-server-common                                    1.7.2-0ubuntu1.5                                    all          Common UNIX Printing System(tm) - server common files
ii  libcups2:amd64                                        1.7.2-0ubuntu1.5                                    amd64        Common UNIX Printing System(tm) - Core library
ii  libcupscgi1:amd64                                     1.7.2-0ubuntu1.5                                    amd64        Common UNIX Printing System(tm) - CGI library
ii  libcupsfilters1:amd64                                 1.0.52-0ubuntu1.4                                   amd64        OpenPrinting CUPS Filters - Shared library
ii  libcupsimage2:amd64                                   1.7.2-0ubuntu1.5                                    amd64        Common UNIX Printing System(tm) - Raster image library
ii  libcupsmime1:amd64                                    1.7.2-0ubuntu1.5                                    amd64        Common UNIX Printing System(tm) - MIME library
ii  libcupsppdc1:amd64                                    1.7.2-0ubuntu1.5                                    amd64        Common UNIX Printing System(tm) - PPD manipulation library
ii  printer-driver-hpcups                                 3.14.3-0ubuntu3.2                                   amd64        HP Linux Printing and Imaging - CUPS Raster driver (hpcups)
ii  python-cups                                           1.9.66-0ubuntu2                                     amd64        Python bindings for CUPS
ii  python-cupshelpers                                    1.4.3+20140219-0ubuntu2.6                           all          Python modules for printer configuration with CUPS

---

### Post by pdc on 2015-04-12
thanks; you seem to have all the packages installed that are needed; some folks have found they don't have all the cups packages installed that they need; I am not sure how that happens;

I would be tempted to delete your existing printer entry from the PRINTERS menu; and ADD a new menu and see if it goes any better this time ............ gutenprint should support your printer ........

---

### Post by workshop99 on 2015-04-12
Thanks, pdc.
I have tried deleting it and adding it several times. There's a choice of three drivers:
CUPS+Gutenprint v5.2.7
CUPS+Gutenprint v5.2.7 simplified
CUPS+Gutenprint v5.2.10-pre2
I've tried them all - same result - the job appears in the print queue and hangs when about 1.3 per cent complete.
The printers is old - perhaps I might have to buy a new one if I want to use Ubuntu.
Thanks again

---

### Post by pdc on 2015-04-12
thanks; 

.......... new printers do seem to be a small cost these days; if one buys the basic; the cumulative ink cost is the running cost; 

if you feel like spending a few minutes on this [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems) it aims to logically work through printing problems

______________

this section [https://wiki.ubuntu.com/DebuggingPrintingProblems#Getting_the_data_which_would_go_to_the_printer](https://wiki.ubuntu.com/DebuggingPrintingProblems#Getting_the_data_which_would_go_to_the_printer) describes how one intercepts the data that is being sent to the printer; that in your case seems to go wrong; 

one would then get the computer to save the information as a file; that it is attempting to send to the printer; and send that file to the bug report folks to work out what is the issue; 

if you want to do that, I can offer to interpret the steps in the above file for you;

---

### Post by workshop99 on 2015-04-12
Thanks,pdc, but that would be putting you and the bug report folks to trouble that seems hardly worth it for a printer that is 8 years old - and I couldn't ask them to assign it any priority.
For 70 pounds sterling I can buy a new HP All-in-one (with Linux driver) which would be a significant improvement on the Canon - tomorrow!
But I really appreciate your offer.

---

### Post by pdc on 2015-04-12
great! enjoy a new printer

---

