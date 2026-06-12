---
title: "Hibernate is missing"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by Frankiewizard on 2012-05-23
Running 12.04 UbuntU on a Toshiba Qosmio G20. When I go into System Settings > Power > When lid is closed - in the menu there is 'Suspend' - 'Do nothing' in black & 'Hibernate' in gray. That means I don't have acces to it. I am sure that there is something I am missing here.

& if there was 'Hibernate'is it a good thing for the hard disk / computer?

Cheers

---

### Post by carl4926 on 2012-05-23
I only use suspend

---

### Post by Revolutionary101 on 2012-05-23
> **Frankiewizard said:**
> Running 12.04 UbuntU on a Toshiba Qosmio G20. When I go into System Settings > Power > When lid is closed - in the menu there is 'Suspend' - 'Do nothing' in black & 'Hibernate' in gray. That means I don't have acces to it. I am sure that there is something I am missing here.

& if there was 'Hibernate'is it a good thing for the hard disk / computer?

Cheers


My guess is that you installed Ubuntu via Wubi (You installed it without creating a separate partition and just installed it inside Windows). In Wubi hibernate is not supported. Here is a little information about Wubi:

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

If you did not install via Wubi, I don't exactly know why it would be doing this.

As for benefits of using hibernate vs suspend, hibernate writes all RAM data to the HDD and essentially turns off the computer. This will save the state that the computer is in until you turn it back on. Suspend does the same thing but keeps the memory in RAM (uses small amount of energy to keep the RAM powered). Suspend will return to the original state because the computer is not turned off per say. Hibernate has a slower wake up time because the computer has to read the data from the HDD back into RAM. The benefit that hibernate has over suspend is that it uses no energy, suspend uses a tiny bit to keep the RAM data.

---

### Post by bcbc on 2012-05-23
Hibernate is disabled by default in 12.04 for all installs. It doesn't have anything to do with wubi ;)

Here is how to enable it: [http://askubuntu.com/questions/94754/how-to-enable-hibernation-in-12-04](http://askubuntu.com/questions/94754/how-to-enable-hibernation-in-12-04)

PS of course if you have a wubi install, then you don't need to bother as it won't work :)

---

### Post by Frankiewizard on 2012-11-05
I do not use wubi I am on a double boot.

---

### Post by sinnadyr on 2012-11-09
> **carl4926 said:**
> I only use suspend
Wow, really helpful! Thank you very much, that really solved my hibernation issue =D

---

