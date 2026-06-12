---
title: "Canon printers under Hardy"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by CitizenJohnJohn on 2008-05-07
Hardy broke printing for me with my Canon LBP 3360. 

The printer driver package delivered by Canon's support site - UFR_II_Printer_Driver_for_Linux_Driver150v - didn't work because the dependencies wouldn't resolve. I went round in circles for a while installing old libraries which the installer would then replace with new ones and then complain it couldn't find the old ones!

I'd managed to dig through the package and find a PPD for my printer but that wasn't enough. I was getting the cups-missing-filter message that often implies a problem with AppArmor, but in my case the problem was genuinely that a filter - pstoufr2cpca - was missing.

A bit more digging turned up the existence of a newer version of the driver - UFR_II_PrinterDriver_for_Linux_Driver_v160 - which Canon takes you to if you are looking for more recent printers like the MF 4150.

I downloaded it from here:

[http://support-au.canon.com.au/contents/AU/EN/0100093001.html](http://support-au.canon.com.au/contents/AU/EN/0100093001.html)

Unpack the tarball, install the two .debs and - voila! - I can print again.

I hope this helps anyone else who's having problems with Hardy and printing.

Cheers

John

---

### Post by amorangi on 2008-06-07
I had the same problem. Unfortunately the drivers linked to above didn't help for my LBP-5000, but I eventually found 1.60 here which works for Hardy. [http://software.canon-europe.com/software/0028622.asp](http://software.canon-europe.com/software/0028622.asp)

---

### Post by Kartagis on 2008-07-02
Hi,

I installed the two .deb files on [http://support-au.canon.com.au/contents/AU/EN/0100093001.html](http://support-au.canon.com.au/contents/AU/EN/0100093001.html), and then our network printer started complaining about paper size. So I have to remove those and install a new driver I found on Canon's another site.

Regards,

---

