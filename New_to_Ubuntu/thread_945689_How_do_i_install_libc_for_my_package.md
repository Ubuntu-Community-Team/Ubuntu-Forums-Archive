---
title: "How do i install libc for my package?"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by Christopher on 2008-10-12
I can't install the latest nvidia drivers from nvidia cause its tell me "You do not appear to have libc header files installed on your system. Please install your distributions libcdevelopment package"  Can someone tell me how to this from a command promt. Thank you in advance. :)


Im using Ubuntu 8.04.1 64bit  with the newest kernel. This is a fresh install and all updated.

---

### Post by schauerlich on 2008-10-12
Does ```
sudo apt-get install libc
``` work?

---

### Post by Christopher on 2008-10-12
> **EDavidBurg said:**
> Does ```
sudo apt-get install libc
``` work?

I went under Synaptic Package Manager and installed "build Essentials" and all is now good for my drivers.


Question #2: How do i get a program that will run my video cards fans at 100% for linux?

Thank you in advance.

---

### Post by Christopher on 2008-10-12
> **Christopher said:**
> I went under Synaptic Package Manager and installed "build Essentials" and all is now good for my drivers.


Question #2: How do i get a program that will run my video cards fans at 100% for linux?

Thank you in advance.

Anyone?

---

### Post by durand on 2008-10-12
Why would you want to? Nvidia automatically changes the fan speed to suit the temperature.

---

### Post by Christopher on 2008-10-12
> **durand said:**
> Why would you want to? Nvidia automatically changes the fan speed to suit the temperature.

I want my fans running at 100%, I want my temps to stay low. Nvidia fans speeds are at 37% by default & i do not beleive they adjust as the temps go up. I was playing crisis in Vista and my cards were smoking hot. I installed riva tuner and all is good. just looking for a program that linux will do the same thing.

---

### Post by durand on 2008-10-12
> **Christopher said:**
> I want my fans running at 100%

Yes, you said that in your previous post. My question is why? It's a pointless waste of energy.

---

### Post by Christopher on 2008-10-12
> **durand said:**
> Yes, you said that in your previous post. My question is why? It's a pointless waste of energy.


Maybe to YOU its a pointless waste, but to ALOT of others its not.

---

