---
title: "Ubuntu 12.04 and Canon MP620b"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by livewire94 on 2012-04-30
Has anyone been able to install the Canon Mp620b printer on Ubuntu 12.04?  If so, how did you do it?

I goto add printer and nothing shows up.  I have the printer setup on my home network wireless.  I also tried using USB to my printer and it doesn't see it.

I tried a script file I found online but it was outdated and didn't work correctly.

Thanks.

---

### Post by jtarin on 2012-04-30
[Here's ]("https://help.ubuntu.com/community/HardwareSupportComponentsPrintersCanonPrintersCanonMP620") Ubuntu documentation on that particular printer.

---

### Post by livewire94 on 2012-04-30
Thanks for the reply but that seems to be an old documentation.  

After spending hours on this proplem, I finally got it to work.

I followed instructions on this site  [http://rackerua.com/2011/05/mp-620-630-debian-based-univeral-installer/](http://rackerua.com/2011/05/mp-620-630-debian-based-univeral-installer/)

It actually installed the printer automatically after 10min.  Closed everything up and tried to print a test page and it would give some weird status errors.  So I went back into the printer properties and changed the driver Make and Model to Canon PIXMA MP620 - CUPS+Gutenprint v5.2.8-pre1

Now I can print.  :)   Prints slower than it would in Windows but at least it prints.  

If everything else works and is stable, I won't need to use Windows.:KS

---

### Post by jtarin on 2012-04-30
> Thanks for the reply but that seems to be an _old_ documentation. I wasn't aware that your model was _new_? I'm happy to see you got it working.

---

### Post by joshiii on 2012-05-02
The Canon Cnijfilter drivers appear to be not working on 12.04 (and if one more person tells me how to install those I get aggressive.)

Currently there seem to be two other drivers that make the printer work.

* PIXMA MP620 - CUPS+Gutenprint v5.2.8-pre1 (make sure to set the resolution to 600dpi, that might speed up the printing, the automatic selection of paper source wasn't working either for me.)
* and [turboprint]("http://www.turboprint.info/") - it is not free but definitly worth the money

thank you for pointing that out livewire but if you use the guttenprint drivers, you won't need to follow any of the instructions installing the broken canon drivers.

---

### Post by ratcheer on 2012-05-02
Thanks for the tip, @joshiii. I have tried that before, and I got the same result today that I got before, "The printer is busy".

However, There are many ways to express the address of the printer and I am not sure which form to use. I tried "ipps://192.168.1.123/ipp/", getting the above result. How do you specify your printer to the Add Printer dialog?

Tim

---

### Post by jtarin on 2012-05-02
192.168.1.123  Will do.

---

### Post by livewire94 on 2012-05-05
> **ratcheer said:**
> Thanks for the tip, @joshiii. I have tried that before, and I got the same result today that I got before, "The printer is busy".

However, There are many ways to express the address of the printer and I am not sure which form to use. I tried "ipps://192.168.1.123/ipp/", getting the above result. How do you specify your printer to the Add Printer dialog?

Tim

The printer won't show up unless you install the drivers from that site I posted earlier.  Canon uses bjnp:// then ip address.

Weird.  I can print web sites and text documents.  I can scan.  But I cannot print from shotwell or any photo software.  

Appears to still be broken.  I will have to print pictures from my Windows laptop for now until this is resolved.  Any Ideas?

---

