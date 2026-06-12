---
title: "visual effects. mobility radeon 9200 driver"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by ajfriend on 2008-07-28
Hi,

I'm new to Ubuntu and I was trying to enable the visual desktop effects in 8.04, but I get an error message saying "Desktop effects could not be enabled" when I switch my visual effects setting from None to Normal or Extra.

From what I can figure out, it looks like I need to install some sort of restricted driver for my graphics card, which is an ATI Mobility Radeon 9200, but I have no idea how to do that. Can anyone help me out?

Thanks a lot,
AJ

---

### Post by kool_kat_os on 2008-07-28
System > Administration > Hardware

---

### Post by ajfriend on 2008-07-28
Yeah, I go to System > Administration > Hardware Drivers, but nothing shows up on the list. On the top, it says, "No proprietary drivers are in use on this system."

Am I just missing something really obvious?

---

### Post by kool_kat_os on 2008-07-28
hmm...thats strange...maybe try downloading a driver from ATI's website?

I know they have driver's for linux...but i dont know if that will fix it....

---

### Post by Ryadt on 2008-07-28
Can you post the output of ```
lshw -C Display
```

---

### Post by ajfriend on 2008-07-28
This is what i get from running lshw -C Display:

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Radeon RV250 [Mobility FireGL 9000]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
       configuration: latency=128 mingnt=8

---

### Post by Rocket2DMn on 2008-07-28
Your card does not support the restricted fglrx driver, so please don't even try with them.  Here is how you can enable compiz with cards using the open source drivers - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by kool_kat_os on 2008-07-28
> **Rocket2DMn said:**
> Your card does not support the restricted fglrx driver, so please don't even try with them.  Here is how you can enable compiz with cards using the open source drivers - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

hmmm...i didnt even know about that :)

---

### Post by ajfriend on 2008-07-28
> **Rocket2DMn said:**
> Your card does not support the restricted fglrx driver, so please don't even try with them.  Here is how you can enable compiz with cards using the open source drivers - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

Thanks a lot, that seemed to work perfectly.

---

