---
title: "[SOLVED] Using a Projector"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by donaldshelton on 2008-10-30
I have a VGA LCD projector that I would like to hook up to my laptop and present Impress files to my classes.

I have both Ubuntu 8.10 and Kubuntu 8.04 on my laptop.

I hook up the laptop to the projector, then I boot it up.  The boot up process shows up on the screen, but when the main desktop shows up on the laptop screen, the projector screen goes blank.

I have gone to preferences and screen resolution, thinking that changing the resolution would help.   It doesn't.  I press "detect displays" and I still get nothing.

Am I missing a package that would help me solve this?

You guyz are awesome!!!

Thanks

Don
:guitar:

---

### Post by LowSky on 2008-10-30
the laptop should ahve a button that has a two square boxes  drawn on it(usually a F button) that when pressed with athe Fn button it will switch monitors...try that

---

### Post by rustutzman on 2008-10-30
Most times you have to hold the fn key and tap f7 or another f-key to toggle the laptop between display modes.

Russ

---

### Post by vanadium on 2008-10-30
It very much depends on your particular graphics card. For me currently (yes, it changes with each Ubuntu release), the screen is displayed simultaneously on the laptop and the projector. If the beamer does not support the resolution, it only displays part of the screen. I can fix that by lowering the resolution. Latest kernel (2.6.24-21) upgrade: I could not anymore change the resolution. I reverted back to 19 because of this. I have an ATI X600 Mobility Radeon card (just saw on the release notes of Intrepid that that one is not supported in the new drivers, so there is hope : sarcasm:)

Just to tell you that anyones mileage can vary. This is one area where Linux continues to be trouble. Indeed, in your case, it might work by switching the displays with the appropriate key combination on your keyboard (vendor dependent).

Anyway, it would be good to post the specs of your graphics card.

---

### Post by donaldshelton on 2008-10-30
How do I get the graphics card specs?  I have the device manager, but I don't know how to identify the card.  thanks

---

