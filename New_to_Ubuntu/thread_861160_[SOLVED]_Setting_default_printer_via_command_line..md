---
title: "[SOLVED] Setting default printer via command line."
date: 2008-07-16
forum: New to Ubuntu
---

### Post by hovzio on 2008-07-16
Hi, I've been playing around with ssh lately (having an absolute BLAST!!!) and I've been trying to use the lpr command on the remote machine. Then I get an error message no default printer. **How do I set the default pr.** I know how to list all available printers etc. and I've looked at the man pages for lpr but I haven't found anything. Is this set up in some .rc file or setting a variable in .bashrc? I'm positive the printer works and I know how to set it with a gui but I dont really feel like forwarding X under ssh just to specify a default printer. [B]The printer works fine when using a gui (gedit, firefox, ....). Why is this?
[/B]
I've looked around the web and the forums without any solid results, any direction or help would be very appreciated. Better yet, any tips on how one could go about figuring this out on ones own? (OS internal, not any websites, books etc. Please note I have looked into the lpr man pages and tried the locate command to find any file associated with "printer", ".rc" etc.) I found some python scripts for the printer but I have no prior experience with python. (I can't imagine a printer config file in python :) but who knows.)

Thanks for any help

---

### Post by brian_p on 2008-07-16
> **hovzio said:**
> Hi, I've been playing around with ssh lately (having an absolute BLAST!!!) and I've been trying to use the lpr command on the remote machine. Then I get an error message no default printer. **How do I set the default pr.** 

On the remote machine:

Edit /etc/cups/printers.conf. Change <Printer blahblahblah> to 
<DefaultPrinter blahblahblah>.

I imagine you could also use lpoptions.

---

### Post by hovzio on 2008-07-16
> **brian_p said:**
> On the remote machine:

Edit /etc/cups/printers.conf. Change <Printer blahblahblah> to 
<DefaultPrinter blahblahblah>.

I imagine you could also use lpoptions.

Hi thanks, for starters I managed a workaround:

```
lpr -P printer_that_is_to_be_used file

```

It works just fine but I still would like to figure this out. I gave a few stabs at /etc/cups/printer.conf. I've tried various combinations but I cannot get lpstat -p to list a default printer. Here goes:
```


# Printer configuration file for CUPS v1.3.2
# Written by cupsd on 2008-07-16 16:56
<Printer Deskjet_D2400_series>
Info HP Deskjet D2400 series
DeviceURI hp:/usb/Deskjet_D2400_series?serial=TH73J122RV04Y7
State Idle
StateTime 1216220190
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>     


```

First I tried modifying the last line and have tried:

```
</Printer Printer Deskjet_D2400_series>
</Printer Deskjet_D2400_series>
</Printer hp:/usb/Deskjet_D2400_series?serial=TH73J122RV04Y7>
</Printer hp:/usb/Deskjet_D2400_series?serial>

```

I assume I'm just making a simple mistake but I've tried more than the above listed options...whats funny is that my printer is listed at the top of this file. Like I said I have a workaround but for the sake of administration and know how I would like to figure this out. The above is taken from my 7.10 xubuntu laptop, on my hardy machine it differs a little but the basics seem the same. Thanks for the help, really appreciate it.

---

### Post by brian_p on 2008-07-16
> **hovzio said:**
> 

I gave a few stabs at /etc/cups/printer.conf. I've tried various combinations but I cannot get lpstat -p to list a default printer. Here goes:

```


# Printer configuration file for CUPS v1.3.2
# Written by cupsd on 2008-07-16 16:56
<Printer Deskjet_D2400_series>
Info HP Deskjet D2400 series
DeviceURI hp:/usb/Deskjet_D2400_series?serial=TH73J122RV04Y7   


```



```
<Printer Deskjet_D2400_series>
```

becomes

```
<DefaultPrinter Deskjet_D2400_series>
```

And restart cupsd.

---

### Post by hovzio on 2008-07-16
> **brian_p said:**
> ```
<Printer Deskjet_D2400_series>
```

becomes

```
<DefaultPrinter Deskjet_D2400_series>
```

And restart cupsd.

Hi, would this be the correct code.
```

sudo /etc/init.d/cupsd restart
```

Thank you for the replies. Sorry but I'm really not sure if the above is correct. I assume so but being that I just formated another box due to "experimentational sudo usage" I'd like to play it safe. Thanks


Edit: well, I decided to just go for it and it worked perfectly. The above command for restarting cups is wrong thoe. Goes as follows:

 sudo /etc/init.d/cupsys restart

Thank you, this really helps me out a bunch.

---

