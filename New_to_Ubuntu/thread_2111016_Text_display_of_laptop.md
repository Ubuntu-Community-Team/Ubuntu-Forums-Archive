---
title: "Text display of laptop"
date: 2013-01-31
forum: New to Ubuntu
---

### Post by nns2006 on 2013-01-31
Hello,
Yesterday,I instaled KDE desktop from synaptic and later uninstalled it. BUt after the uninstallation the text on my laptop looks thin and broken type. 
Please see the attachment for text before and after installation.

What should I do?

Thank you

Nitya

---

### Post by nns2006 on 2013-02-01
*bump*

---

### Post by nns2006 on 2013-02-02
I have the same problem as asked in this thread. [http://ubuntuforums.org/showthread.php?t=2083802&highlight=font+ubuntu](http://ubuntuforums.org/showthread.php?t=2083802&highlight=font+ubuntu)

---

### Post by sudodus on 2013-02-02
Try this way: Get ***Ubuntu Tweak*** according to this link (via tualatrix)

[http://ubuntu-tweak.com/downloads/](http://ubuntu-tweak.com/downloads/)

Select the third tab, 'Adjustments' or something similar (I don't use the English version)

and 'Font'. Here you should be able to tweak hinting and type of 'smooting of the edges' (or something similar, I don't use the English version).

Maybe this will help.

(I found this way in Ubuntu with Unity, there are other menus in other desktop environments, for example Lubuntu).

---

### Post by nns2006 on 2013-02-02
I solved it by deleting the hidden setting folders in "home". now I get my text displayed corectly on laptop.

Thank you for the reply though.

---

### Post by varunendra on 2013-02-03
Looks like I'm late in the party, so would just make a quick comment for those who may come here having similar problems

Laptop (or any LCD/TFT) screens work best at some particular resolution (or an exact factor of it) specific to them. Usually the recommended resolution for these screens is the largest one they support, but you can lower it to another set which is an exact factor of that one. Deviation from this resolution may cause 'hazy' or distorted display, unless the text or object size is very large.

For example, the typical resolution recommended for a 15" widescreen laptop is **1366 x 768** (aspect ratio 16:9)

However, nitya, the second attachment in your post seems normal, suggesting it was not a resolution problem. Most probably a system default font change. Although it could be fixed by what sudodus suggested, you should also have been able to fix it by just resetting the 'Theme' in "System Settings > Appearance". But what you did instead -> **nns2006 said:**
> I solved it by deleting the hidden setting folders in "home".
..was not a bad call either, but should ba a last resort :).

---

### Post by Nwwmac on 2013-02-03
> **nns2006 said:**
> I solved it by deleting the hidden setting folders in "home". now I get my text displayed corectly on laptop.

Thank you for the reply though.

I don't see a .settings folder, but I do have .fontconfig. 

Is that what you deleted?

---

### Post by nns2006 on 2013-08-18
Sorry for being sleepy for so many days :D By deleting "setting" folder, I mean deleting the hidden folder in home. You can see then by pressing Ctrl+H . Then you can selectively delete if necessary. However, changing font and antialiasing also works.

---

