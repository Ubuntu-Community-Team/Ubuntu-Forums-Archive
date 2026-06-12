---
title: "Low Graphics Mode"
date: 2012-12-02
forum: New to Ubuntu
---

### Post by daniell59 on 2012-12-02
I just installed a different video card. When I booted into Ubuntu, I got the following error message.

Ubuntu is running in low graphics mode.
The following error was encountered. You may have to update your configuration to solve this.

EE No supported AMD display adapters were found.
EE No devices detected

Ubuntu 10.04 64

Any assistance will be appreciated.

---

### Post by Yougo on 2012-12-02
With installed, you mean you also installed the drivers, or did you just swap out the card?

what video card did you swap with what?

if you were using non-standard drivers for the first one, and you swap the card out with a completely different one, Ubuntu is going to be confused and go to safe graphics mode. in that case you need to remove the old drivers and if needed, install the drivers for the new card

---

### Post by daniell59 on 2012-12-02
> **Yougo said:**
> With installed, you mean you also installed the drivers, or did you just swap out the card?

what video card did you swap with what?

if you were using non-standard drivers for the first one, and you swap the card out with a completely different one, Ubuntu is going to be confused and go to safe graphics mode. in that case you need to remove the old drivers and if needed, install the drivers for the new card

My previous card malfunctioned. I swapped it with a different PCI Express card. I did not install any drivers.

---

### Post by Yougo on 2012-12-02
i'm not on ubuntu 10.04, so i have to guess the menu structure. i believe somewhere  under System, there is "Additional drivers". start that app.

it can be a bit slow to start as it checks your whole system. when it opens, you can see if it still uses the drivers for your old card, and if it offers new drivers.

uninstalling drivers for your old card may already help.

also, since you are using 64 bit, it could be there are no 64 bit drivers for your card, but only 32 bit. in that case there may be a way to make them work, but i don't know how...

---

### Post by Yougo on 2012-12-03
So... did you get any further?

If you solved your problem, please be kind and briefly explain how you solved it, and mark the thread as [Solved].

If not, you can post here again and people may help you out...

---

