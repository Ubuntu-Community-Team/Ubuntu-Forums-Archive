---
title: "not recognizing USB devices after new ram"
date: 2014-02-17
forum: New to Ubuntu
---

### Post by ndunkz on 2014-02-17
Having a couple issues - 

Im running multiple GPU's with Ubuntu, and they required more ram than I had initially installed.  Im very unfamiliar with Bios and Linux command line, so plz be patient..

I shut down the system, then placed two corsair 4 gb ram cards in staggered position, complimenting the already implemented 2x2 of the same make. Went to boot the system and it wouldnt get to boot screen.  Trying a few things, I then removed the new ram (after a hard reset), and rebooted - this time it got me up to the purple boot selection screen, I selected Ubuntu, not recovery mode or older versions, and it booted up ok. Then, after seeing that I could get away with trying the ram in and removing it, I tried to put the two in again, thinking I might have missed the 'click' on one side.  When I booted after this, it opened saying there was a corrupted OS, it would boot from back up, and not to shut down.  I let it all boot up - then once it did I got to the home screen with user login, but I cant login.  Keyboard, mouse, or Wifi receiver all running off USB arent showing or being recognized.  

At the moment I'm running a memtest86 - but Im really hoping someone might be able to shed a little light on this?  

Greatly appreciate any help at all..

Thanks in advance

---

### Post by ndunkz on 2014-02-17
I figured it out in Bios - who knows why but there is a setting called [COLOR=#333333][FONT=Helvetica Neue] [/FONT][/COLOR]IOMMU Controller that needs to be enabled 

Thanks

---

