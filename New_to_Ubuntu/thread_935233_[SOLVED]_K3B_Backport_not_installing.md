---
title: "[SOLVED] K3B Backport not installing"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by HellNoire on 2008-10-01
So I'm running an update and everything updates, save K3B which is greyed out under Ubuntu 8.04.1

Does that mean it's already installed? Or what's the story?

[IMG]http://img27.picoodle.com/img/img27/3/10/1/f_ScreenshotUm_980a974.png[/IMG]

That's a screenshot of the update manager, hopefully someone could help me out.

---

### Post by fooman on 2008-10-01
try installing in a terminal...type or copy/paste the following commands,  one at a time:

```
sudo apt-get update

sudo apt-get install k3b
```

post back with any errors.

---

### Post by cariboo on 2008-10-01
Sometimes a program will not update if there is a dependency missing. You have to remember that packages in the backports repository are not official Ubuntu packages, as they are not included as part of the LTS version that you are probably using.

Jim

---

### Post by silverglade00 on 2008-10-01
I have this same issue and I pretty much decided that it is because I have the medibuntu k3b installed. They have the same version as the backports one, so it may just be a matter of it not "wanting" to install the same version twice.

---

### Post by HellNoire on 2008-10-01
That did it, Fooman. Thanks.

---

