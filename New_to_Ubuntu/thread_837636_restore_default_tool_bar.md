---
title: "restore default tool bar?"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by pcrussell50 on 2008-06-22
somehow, i've made my toolbar, [the grey bar at the top], custom.  i want to restore it to default, the way it is on a fresh install.  i've spent a good deal of time trying to do this, but...no luck.  i'm about to reinstall hardy here just to get it back to "stock".  somebody ssstop me!

-peter

---

### Post by chenqinbo5 on 2008-06-22
do drop by to [www.shop-foco.com](www.shop-foco.com) <http://www.shop-foco.com>  look through the articles there. With information on anything from getting the  cheapest shoes, you'll find something that helps you save a lot of money.
-- 
the cheapeast shoes
[www.shop-foco.com](www.shop-foco.com)
<msn:shop-foco@hotmail.com>
E-mail:shopfoco@gmail.com
Thank you for your E-mail and your order

---

### Post by N.N. on 2008-06-22
You should be able to reset all panels by deleting the "panel" folder, which is located in the "apps" subdirectory in the hidden ".gconf" folder located in your home directory. To do this graphically, open your home directory in nautilus (the graphical file manager), press CTRL+H to reveal hidden files, open the directory called ".gconf", navigate to the subdirectory called "apps", and delete the directory therein called "panel".

An easier way to go about this is to issue the following command in a terminal: ```
rm -r ~/.gconf/apps/panel
```

EDIT: Having done that, you should restart gnome-panel by issuing the following command in a terminal: ```
killall gnome-panel
```

---

### Post by pcrussell50 on 2008-06-22
worked like a charm...after a system restart!  thanks have been left!

-peter

---

### Post by Jim_in_Omaha on 2008-08-11
Mine changed on me for some reason. Everything was moved to the left on both the top and bottom panels. Thanks for this post, fixed it like new.

---

