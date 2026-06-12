---
title: "I messed up"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by gulmer on 2011-09-20
I need help getting my ubuntu desktop back. I was going to install a new video card and I couldn't get into ubuntu, so I put the old card in and removed the nvidia driver that got installed. The new card still would not load ubuntu,so I installed the old card back and now ubuntu is not recognising the old card. I blew it this time, wife will be ****ed. What can I do to get ubuntu back?

---

### Post by Paqman on 2011-09-20
First things first, check that the card is properly seated in the slot and that you've connected up anything it needs (such as power if it's that sort of card).

What sort of card is it? Does it need drivers? If so, what does Additional Drivers show?

---

### Post by gulmer on 2011-09-20
> **Paqman said:**
> First things first, check that the card is properly seated in the slot and that you've connected up anything it needs (such as power if it's that sort of card).

What sort of card is it? Does it need drivers? If so, what does Additional Drivers show?

OK, I got the old card to work and I'm on the desktop again after getting up a screen that gave me a choice of logging in normal mode or recovery mode,not sure how I got that screen up, but I went into recovery and told ubuntu to fix anything broken, then went into safe graphics mode and installed the nvidia driver and all is back. I would still like to get the new card working,which is a ATI Radeon HD5570 and the old card is a GeForce 7200GS. Upgrading can be a bitch. How can I get ubuntu to recognise the ATI card and get me to my desktop to install the correct drivers for it?

---

### Post by gulmer on 2011-09-20
Maybe I should restate my problem. How can I go from a Nvidia video card to a ATI video card? Looks like with a Nvidia driver installed, Ubuntu will not bring up my desktop with the ATI card in place of the Nvidia card, what do I do to get this solved so I can use the new ATI card?

---

### Post by Paqman on 2011-09-20
You can boot up into recovery mode again (if your Grub menu is hidden you need to press a key to get it to show, shift I think?) and from there you can uninstall the old Nvidia driver:
```
jockey-text --list
```
Check which one is showing as enabled and in use then do:
```
jockey-text -d *name_of_driver*
```

That will clear out your old Nvidia driver. You can also install the new ATI driver the same way, except use:
```
jockey-text -e *name_of_driver*
```
...instead. Jockey is just another name for the Additional Drivers tool you use on the desktop.

---

