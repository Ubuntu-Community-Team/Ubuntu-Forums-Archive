---
title: "Big fat bug in lightdm"
date: 2011-09-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by CaptainMark on 2011-09-06
Went to change my password today and decided to use the option in the gnome-control ouser options to reset my password on next login, right, DO NOT USE IT! Your password basically gets stripped away and now I can't login. There is no option to remake it in lightdm, awesome

---

### Post by lucazade on 2011-09-06
> **CaptainMark said:**
> Went to change my password today and decided to use the option in the gnome-control ouser options to reset my password on next login, right, DO NOT USE IT! Your password basically gets stripped away and now I can't login. There is no option to remake it in lightdm, awesome

awesome.. thanks for heads up.
have you tried in recovery mode to set up a new pwd?
```
sudo passwd your-user-name
```

---

### Post by jbicha on 2011-09-06
I wasn't able to reproduce your bug but I guess I misread what you were describing. I changed my password with user accounts, logged out, and was able to log back in with the new password just fine.

[Here]("https://help.ubuntu.com/11.04/ubuntu-help/user-forgottenpassword.html")'s the advanced guide to fixing your password.

---

### Post by 3rdalbum on 2011-09-06
> **jbicha said:**
> I am definitely **not** able to reproduce your bug. I changed my password with user accounts, logged out, and was able to log back in with the new password just fine.

CaptainMark is talking about an option to "reset your password on next login". This option must use something specific to GDM that's not available in LightDM.

This bug has been reported already; it's LP 821771 ([https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/821771](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/821771)). I subscribed to it as I can reproduce the problem.

---

### Post by jbicha on 2011-09-07
Yes it's definitely reproducible. Sorry I didn't read the initial post closely enough.

---

### Post by mc4man on 2011-09-07
Cannot really speak for the OP but that option is available, using only lightdm here.
(though I'd be inclined to set it then & there

---

### Post by 3rdalbum on 2011-09-07
> **mc4man said:**
> Cannot really speak for the OP but that option is available, using only lightdm here.
(though I'd be inclined to set it then & there

Yeah, the option is available, but it doesn't work unless you're using GDM. Most Ubuntu users will stick with the default lightdm.

---

### Post by CaptainMark on 2011-09-07
yeah this is a major problem, try not to think about think about us using ubuntu but a new home user who decides that he/she wants to change a password, this is an absolute showstopper for them,

---

### Post by Mr. Picklesworth on 2011-09-07
I have some other bug reports filed on that settings panel (and, generally, its interaction with lightdm). It's terrifying to me in its current state. Needs lots of love, if anyone can spare some :)

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/821761](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/821761)
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/821759](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/821759)
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/821765](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/821765)
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/821766](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/821766)

Some of this work actually fits upstream, but I reported these bugs in Ubuntu because they're regressions for us. In short, this settings panel as it stands in Ubuntu murders kittens on a regular basis, and if we release this way it'll go on to torturing unicorns.

---

### Post by CaptainMark on 2011-09-08
ive confirmed 3/4 of these, but the one about the password manager being too strict, whilst i agree, is based on opinion, it seems the password manager has been completely overlooked when blending in gnome3 to ubuntu's new interface

---

