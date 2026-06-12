---
title: "show icons for all installed software"
date: 2014-05-19
forum: New to Ubuntu
---

### Post by errolgreer on 2014-05-19
The bar at the left can only show some apps. How do I get a screen or list of apps to display all of the installed programs?

---

### Post by grahammechanical on 2014-05-19
That depends on which version of Ubuntu or its flavours you are using. If it is Ubuntu 12.04, 13.10 or 14.04 then click the Ubuntu icon on top of the Launcher or press Super+A. Super is the key with the flying windows on it. You can click Installed show nn more results. 

If you hold down the Super key an overlay will appear on the screen that lists keyboard shortcuts.

Regards.

---

### Post by monkeybrain20122 on 2014-05-19
Press super + A or click the Ubuntu icon on the top of the launcher bar and go to Applications. You can see them listed by category if you then click "filter" on the upper right side.

---

### Post by deadflowr on 2014-05-20
> **errolgreer said:**
> The bar at the left can only show some apps. How do I get a screen or list of apps to display all of the installed programs?

You can place ALL your apps on the launcher.
As long as the apps are in the share/applications folders in /usr and /home/user/.local folders.
```
/usr/share/applications
/home/username/.local/share/applications

```
I think if you built apps and use the /usr/local directory, they, too, might get listed as well.
Though I'm not sure.
But +1 to super+A, the second field usually shows Installed, which you can toggle to view all.
They'll be listed alphabetically.

---

### Post by errolgreer on 2014-05-25
Thank you all! Problem solved!

---

