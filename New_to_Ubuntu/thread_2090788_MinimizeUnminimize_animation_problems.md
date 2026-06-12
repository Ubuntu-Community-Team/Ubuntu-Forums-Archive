---
title: "Minimize/Unminimize animation problems"
date: 2012-12-03
forum: New to Ubuntu
---

### Post by newtrino on 2012-12-03
Hi,
I'm on Ubuntu 12.10, Core i5, Nvidia GTX 550 Ti, 8GB Ram and I have a problem.
Whenever I minimize a windows, the animation starts but the window in the animation has no contents, so basically, the contents of the window vanishes and the border of the window follows the animation.
Not only that but sometimes when unminimizing windows, the animations work fine, but the window contents will be black, and the only way to rectify is to minimize (animation works) and then unminimize again. After that the animation stops working properly again.

It's really bizarre and I can't figure it out. Any help would be appreciated.
Thanks

---

### Post by dannyboy79 on 2012-12-03
which nvidia drifver are you using?

---

### Post by newtrino on 2012-12-03
Thanks for the response.
nvidia experimental 310 i think it's called.

---

### Post by dannyboy79 on 2012-12-03
are you using compiz? have you tried different nvidia drivers?

---

### Post by newtrino on 2012-12-04
Sorry for the late reply, 
Yes I am using compiz and I have tried different drivers, the animation worked ok with the open source driver, but everything was horrible, slow and laggy.

---

### Post by newtrino on 2012-12-05
Anyone any ideas?

---

### Post by monkeybrain2012 on 2012-12-05
Does this bug report describe your situation? If so you should add an "affect me too", though don't know when it will be fixed (it affects both 12.04 and 12.10)

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/729979](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/729979)

---

### Post by newtrino on 2012-12-05
Not really, mine is more when minimizing windows, then opening them before the minimize animation completes. I think I will just do a fresh install of 12.10 as I'm dual booting at the moment, and I want to get rid of windows ^^

---

### Post by newtrino on 2012-12-05
Ok even after a fresh install the problem persists. This leads me to think it's a compiz nvidia clash or something. It kind of looks like the content of the window minimizes faster than the border if that helps anyone.

---

### Post by dannyboy79 on 2012-12-06
sorry, not sure what to suggest.

---

### Post by Lamo_nksp on 2012-12-08
ccsm >> unity plugin >> switcher tab >> uncheck "shown minimized windows in switcher"
(optional) ccsm >> disable workarounds OR ccsm >> workarounds >> uncheck "keep previws of minimized windows"
Optional step fixes maximized windows, at least worked for me.
Ubuntu 12.10 x64, Nvidia GTX 275, proprietary drivers 310.14, compiz+unity

---

### Post by newtrino on 2012-12-09
> **Lamo_nksp said:**
> ccsm >> unity plugin >> switcher tab >> uncheck "shown minimized windows in switcher"
(optional) ccsm >> disable workarounds OR ccsm >> workarounds >> uncheck "keep previws of minimized windows"
Optional step fixes maximized windows, at least worked for me.
Ubuntu 12.10 x64, Nvidia GTX 275, proprietary drivers 310.14, compiz+unity

I could kiss you!
Thank you! It worked :)

---

