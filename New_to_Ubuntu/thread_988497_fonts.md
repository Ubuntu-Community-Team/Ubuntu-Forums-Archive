---
title: "fonts"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-11-20
can someone tell me some fonts that really look good?

---

### Post by kestrel1 on 2008-11-20
Do a search in Google, you should find loads.

---

### Post by Cope57 on 2008-11-20
[_Enable Smooth fonts on Ubuntu Linux_]("http://www.howtogeek.com/howto/ubuntu/enable-smooth-fonts-on-ubuntu-linux/")

---

### Post by DaveyG on 2008-11-20
Try something like this:

> sudo apt-get install msttcorefonts

Fixes those ugly fonts...

---

### Post by Cope57 on 2008-11-20
You could use your existing fonts and try this.

First, enable **Sub_p_ixel smoothing (LCDs)** in the **System > Preference > Appearance** then the **Fonts** TAB in the control panel.
Then click **D_e_tails** and make the **R_e_solution:** [**96**] dots per inch.
Full Hinting helps also.
That should enhance your existing fonts.

But if you are determined to install more fonts, try here.

[_76 Fun fonts_]("http://thelinuxbox.org/?p=26")

[_300+ Easily Installed Free Fonts for Ubuntu_]("http://ubuntu.wordpress.com/2007/05/21/300-easily-installed-free-fonts-for-ubuntu/")

**Summary**
If you want to get all 300 fonts in one go, use the following command:
```
$sudo apt-get install ttf-gentium ttf-dustin ttf-georgewilliams ttf-sjfonts sun-java6-fonts ttf-larabie-deco ttf-larabie-straight ttf-larabie-uncommon
```

But if this is not enough of your font fetish...

[_Six Thousand Seven Hundred Sixty Fonts_]("http://thelinuxbox.org/?page_id=3#fonts")


If all else fails... [TRY HERE](http://letmegooglethatforyou.com/?q=fonts)

---

