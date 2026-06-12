---
title: "Connect VirtualBox to internet"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by tentel on 2008-05-06
I've been trying to figure out how to do this, but I'm stumped.


From what I've read in the User Manual, I should have it set to NAT, and PCnet-FAST III.

I've done that, but I have no idea what to do next.

I am pretty illiterate when it comes to networks.


By the way, I am running XP as a guest inside of Hardy Heron, and I'm using VirtualBox 1.6 Puel, not OSE, so I haven't installed anything from synaptics.



Thanks for the help
-Tim

---

### Post by 1875 on 2008-05-06
Works out of the (virtual)box for me.

---

### Post by mlentink on 2008-05-06
> **1875 said:**
> Works out of the (virtual)box for me.

As it does for me. I run 1.5.6. with NAT and that PCnet-Fast pseudo adapter, and it works. Weird.

---

### Post by Oldsoldier2003 on 2008-05-06
> **tentel said:**
> I've been trying to figure out how to do this, but I'm stumped.


From what I've read in the User Manual, I should have it set to NAT, and PCnet-FAST III.

I've done that, but I have no idea what to do next.

I am pretty illiterate when it comes to networks.


By the way, I am running XP as a guest inside of Hardy Heron, and I'm using VirtualBox 1.6 Puel, not OSE, so I haven't installed anything from synaptics.



Thanks for the help
-Tim

let vbox handle the networking, dont try to set it up unless you absoulutely need to. By default vbox will share the hosts connection.

use nat and the defualt adapter vb sets up,make sure you have enable network adapter and cable plugged in ticked.

---

### Post by tentel on 2008-05-06
> **Oldsoldier2003 said:**
> let vbox handle the networking, dont try to set it up unless you absoulutely need to. By default vbox will share the hosts connection.

use nat and the defualt adapter vb sets up,make sure you have enable network adapter and cable plugged in ticked.

Okay, so that check out.  it all seems to be set up.

Is there anything I have to do inside of XP?

-Tim

---

### Post by Oldsoldier2003 on 2008-05-06
> **tentel said:**
> Okay, so that check out.  it all seems to be set up.

Is there anything I have to do inside of XP?

-Tim

no it should autodetect. if youve changed anything in xps settings change it back to dhcp/automatic

edit: oh and if you get new hardware detected... use the vbox drivers- dont try to install any new drivers from the internet or anything. XP will find them and install them from the vbox guest additions iso if its mounted.

---

### Post by tentel on 2008-05-06
How do I make sure it is on DHCP/Automatic?


-Tim

---

### Post by tentel on 2008-05-06
Would I be better off using an older version of VirtualBox?

I wonder if that could be the problem?

I think that I read that 1.6 was a bit buggy with Hardy.


-Tim

---

### Post by SlappyPappy on 2008-05-06
Just do the connection wizard and go LAN. You don't have to change any settings. It piggybacks on the host connection.

---

### Post by dark_harmonics on 2008-05-06
It cant be said enough in this thread to LEAVE DEFAULTS. I think it uses NAT (never had to check really) and forwards traffic seamlessly. If you have that working the only other thing i would do is to install the guest additions. Makes everything roll together smoother.

---

