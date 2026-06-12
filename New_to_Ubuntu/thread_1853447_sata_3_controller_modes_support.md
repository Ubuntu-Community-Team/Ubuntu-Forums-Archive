---
title: "sata 3 controller modes support"
date: 2011-10-02
forum: New to Ubuntu
---

### Post by VChaman on 2011-10-02
HI everyone,

I'm currently selecting which motherboard I'll buy for my next Ubuntu desktop. I'm going after something with muscle, the likes of an Intel DQ67SW (for getting VT-x / VT-d support) with an Core I7-2600 ,16 gig of RAM, SATA 3 SSD & HDD, high end graphic card, USB 3 and so on. 

I noticed that recent boards offer SATA 3 controller with Legacy Mode as well as Native Mode.

I wonder if Ubuntu 11.04 64 bits edition, or any 64 bits kernel above 2.6.38 supports SATA 3 controller in Native Mode?

Many thanks

---

### Post by VChaman on 2011-10-02
Hi again, although I did some research before posting this thread, I  found a partial answer moments ago. 

Linux transparently supports both modes from some time, it's just a matter of setting on AHCI in the BIOS. So, I bet it's safe to assume that this works for SATA 3 controller also.

Anyone can confirm?

Thanks

---

### Post by VChaman on 2011-10-07
Ok, Natty is installed, everything is working just fine, SATA 3 included. Native mode support for SATA3. I made sure before starting the install that my BIOS setting enabled native mode for my SATA controllers.

---

