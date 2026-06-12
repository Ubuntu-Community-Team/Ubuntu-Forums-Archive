---
title: "AMD Radeon HD 6450"
date: 2013-06-26
forum: New to Ubuntu
---

### Post by DarthSidious on 2013-06-26
I have a Dell XPS8300 with a AMD Radeon HD 6450 video card.  I use to be able to run Ubuntu after adding NoModeSet to the grub, however this no longer works (13.04).  I switched to Linux Mint which worked fine until it's new release in late May.  I have tried many things that people have suggested, but not have worked.  I would really like to get Ubuntu back with my current hardware, however, I have no become desperate enough (I have been running Windows all month) to buy a video card.  I don't game, but I do use Google Earth alot.  I would like to stick around a $125 price range..if thats possible.  Does anyone have any suggestion to what I can do to either get Linux to work with my current video card or what type of video card I should buy?

Thanks,

Lord Sidious
May the Force Not be with You

---

### Post by mastablasta on 2013-06-27
install proprietary drivers.

also saying it doens't work really isn't helpful and doesn't mean anything.: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

any error messages? what happens when it stops working? how is it installed (single OS on disk, dual boot side by side, wubi?)

---

### Post by coffeecat on 2013-06-27
> **DarthSidious said:**
> I have a Dell XPS8300 with a AMD Radeon HD 6450 video card.  I use to be able to run Ubuntu after adding NoModeSet to the grub, however this no longer works (13.04).

Which video driver were you using? I'm posting from a machine with a Radeon HD 6450 card using Ubuntu 13.04 and the open source driver. I don't need to use nomodeset in grub and it works well for me, including Google Earth. If you don't game, you don't need the proprietary driver and the default open source one should be just fine. If you are using the proprietary driver, I suggest you uninstall it and see how you get on with the open source one.

---

### Post by DarthSidious on 2013-06-30
Sorry it has take me so long to repond, but its a long weekend up here in Canada:).

My problem has been solved, though I'm not sure why.  After a clean install, it would boot up with a black screen as I described in my first post.  There were no error messages.  I rebooted, but hit Alt-F2, & selected Advanced boot options, generic kernal.  It booted up without any problems.  I can now boot up normally.  I have no explanation for this.  It works, so I'm reluctant to go messing around with it.  Thanks for you help guys.

Darth Sidious

---

