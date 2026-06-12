---
title: "wireless can't used!! help please"
date: 2012-09-09
forum: New to Ubuntu
---

### Post by andy94 on 2012-09-09
I install my laptop with ubuntu 10.10 but i can't use the wireless ..
Any solution ?

---

### Post by roger_1960 on 2012-09-09
Hi

Have you tried searching these forums for similar problems with your type of PC and wireless card (whatever they are? - its hard to help with no information!).  Ubuntu 10.10 is in fact no longer supported (as of april).  If your PC is new, 10.10 may not have the right drivers.

---

### Post by kc1di on 2012-09-09
> **andy94 said:**
> I install my laptop with ubuntu 10.10 but i can't use the wireless ..
Any solution ?

We will need a little more information to be of much help.

what type of laptop? What Wireless card?

---

### Post by metilly on 2012-09-09
Try installing a different version of Ubuntu.  I've found that an earlier version of Ubuntu than the one I'm using will sometimes work and sometimes a later one.

A Compaq I was installing with a 9 or 10 version wouldn't even complete installation and rolling back to 8.04 was successful.  The Dell I'm having trouble with I'm fairly certain was giving me wireless network problems on 11.04 but 12.04 was up and running straight off.

---

### Post by shadedpixel on 2012-09-09
> **andy94 said:**
> I install my laptop with ubuntu 10.10 but i can't use the wireless ..
Any solution ?
Just as what everyone else has said, 10.10 is no longer supported. Try installing (or upgrading) to 12.04. Also could you paste the output of

```
sudo lsusb
```

and

```
sudo lspci
```

---

### Post by andy94 on 2012-09-09
thanks before for all
my laptop is A43SD
i don't know how to see my wireless type
i want to use ubuntu 10.10
can you help me with telling me where i can download the driver so my wireless can use ?

thank you

---

### Post by anewguy on 2012-09-10
From Asus's web site, it appears there are 3 possible adapters that might be in your laptop.  As shadedpixel suggested, before we can give you any further guidance, please run the following in a terminal window and post the results back here in a reply:

lspci

lsusb

lsmod


Each of those does the following:

lspci lists the hardware on the pci bus in your system.  The wireless will probably be in this list.  However, internally in some laptops the built-in wireless is actually connected to the usb bus. lsusb lists the hardware on the us busses from your system.  Finally, just as in Windows, a driver is required for the wireless - these drivers are in the form of modules for the Linux OS kernel.  lsmod lists the kernel modules that are currently loaded.  All of this information will allow us to determine what the adapter is and what needs to be done to get a driver working for you.

I also would like to stress going to a newer version of Ubuntu - preferably the newest long-term support release 12.04.  There are multiple reasons why I would suggest this, among them:
[LIST]
[*]your hardware is relatively new.  Older versions of Linux may not have the best support for your system.
[*]Many drivers have been added to Ubuntu since version 10.  This includes wireless drivers that previously had to be manually installed.  
[/LIST]

---

### Post by andy94 on 2012-09-11
I think u r right with ubuntu 10.10 was not supported my laptop because when i installed version 12.04 it's work great
now i can access wifi from my ubuntu
even i am not feel enough yet
but thanks all for your help...

---

