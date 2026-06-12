---
title: "How to adjust Brightness and contrast on desktop?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by adnansanni on 2008-04-29
Is there any software or way to adjust Brightness and contrast on desktop? If I reduce the brightness then visibility become more clear and nice, I had to reduce that on windows. My laptop is Asus A6F. It hasn't ati or nvidia. Probably used Intel 945 graphics chip set and I'm using Ubuntu Hardy Heron.

---

### Post by adnansanni on 2008-04-30
Any help?

---

### Post by ism. on 2008-04-30
not 100% sure what you mean. If you go to system>preference the drop down list has options for screen resolution and appearance.  Is that what you mean?

---

### Post by master5o1 on 2008-04-30
right click on the Gnome panel and click Add to panel... then select the Brightness app. This applet is like the Volume Control applet and uses a slider to control the brightness.

---

### Post by mc4man on 2008-04-30
there is a built in gamma correction, xgamma. It's based on 1.000 as current setting which you can raise or lower rgb together or individually. You can freely experiment as settings will revert upon reboot unless added to xorg.conf
usage in xgamma --help

---

### Post by adnansanni on 2008-04-30
Thanks guys for your all reply.

@ism, I checked system>preference> screen resolution, there isn't control for adjust the contrast or brightness.

@master5o1, actually I'm not talking about LCD brightness. I want to control contrast and brightness of default driver.

@mc3man, is there any thing for contrast like xgamma? Thanks for the tip for xgamma.

---

### Post by mc4man on 2008-04-30
> is there any thing for contrast like xgamma
ck. here - haven't used (have crt)
[http://ddccontrol.sourceforge.net/](http://ddccontrol.sourceforge.net/)
doc. [http://ddccontrol.sourceforge.net/doc/0.4/](http://ddccontrol.sourceforge.net/doc/0.4/)

Slightly Ot - in regards to calibrating displays for photo, video or just because  - another tool and reading
[http://www.pcbypaul.com/software/monica.html](http://www.pcbypaul.com/software/monica.html)
[http://www.normankoren.com/makingfineprints1A.html](http://www.normankoren.com/makingfineprints1A.html)

---

