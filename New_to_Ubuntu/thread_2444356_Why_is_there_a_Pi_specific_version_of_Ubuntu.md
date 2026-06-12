---
title: "Why is there a Pi specific version of Ubuntu?"
date: 2020-05-29
forum: New to Ubuntu
---

### Post by smartaland on 2020-05-29
Coming from the perspective of "normal" machines (i.e. consumer  desktops/laptops) you can just download the x86-64 and it will work on  the machine regardless of the particular components (so long as the  processor architecture matches).
  The Pi (to my non-expert eyes) is an ARM machine, so why is there a  specific build for the Pi when it still targets ARM architecture?
  Thanks!

---

### Post by mastablasta on 2020-05-29
because you can modify the kernel to suit specific board, which makes it more efficient on the reosurces.

with x86 or amd64 - you don't know how the PC will be built, what hardware will be used. but with pi you know exactly which hardware it will be used on.

with opensource you can make your own respin or version. and respin is juts one of such tools you could use. or you can also build form scratch.

---

### Post by guiverc on 2020-05-29
FYI:  I just saw this on [https://askubuntu.com/questions/1244821/why-is-there-a-pi-specific-version-of-ubuntu-and-we-cant-just-install-regular]("https://askubuntu.com/questions/1244821/why-is-there-a-pi-specific-version-of-ubuntu-and-we-cant-just-install-regular?noredirect=1#comment2098679_1244821")

---

### Post by grahammechanical on 2020-05-29
ARM does not make computer chips. It designs them for whoever is willing to supply a specification and pay the price. Apple Corp have made great use of ARM designs. It follows that versions of Ubuntu have to be compiled to run on a specifically designed architecture. Provided the design has not been copyrighted to prevent anyone from producing their own software to run on that particular design.

Regards.

---

### Post by coffeecat on 2020-05-29
> **guiverc said:**
> FYI:  I just saw this on [https://askubuntu.com/questions/1244821/why-is-there-a-pi-specific-version-of-ubuntu-and-we-cant-just-install-regular]("https://askubuntu.com/questions/1244821/why-is-there-a-pi-specific-version-of-ubuntu-and-we-cant-just-install-regular?noredirect=1#comment2098679_1244821")

@guiverc, thanks for providing that link. Interesting that the OP of that askubuntu question (which precedes the OP here) is surprised that the identical question has been asked here. 

@Geesh_SO, if you are reading this, no there is no automation that re-posts askubuntu questions here. Indeed, we take a dim view of copy-pastes, which is why I have now closed this thread. 

Anyone wishing to follow further discussion has the link to the askubuntu page. Thanks to all for your interest.

---

