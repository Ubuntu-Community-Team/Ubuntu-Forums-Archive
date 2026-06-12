---
title: "LibreOffice slowness issue"
date: 2014-07-07
forum: New to Ubuntu
---

### Post by ian49 on 2014-07-07
Having previously been using OpenOffice on Ubuntu 10.04 without any problems whatsoever for a number of years I recently started using Ubuntu 14.04 along with LibreOffice.

I'm now at the point where I'm seriously considering getting rid of LibreOffice as every few minutes it seems to go into a sleep state... I click on a cell in a spreadsheet (I use Calc most of the time), nothing happens for about 10 - 20 seconds, then the screen greys, then there's another long pause and then finally I can input some data. The laptop I'm using has 2Gb of memory, a capable CPU and everything else runs relatively fast. I've tried tweaking the LibreOffice memory settings as advised elsewhere but it made no difference. I've also noticed a lag of a second or two for the various menus to display... all in all it feels sluggish.

Since I use Calc for several hours each day I can't really tolerate this constant having to wait in order to input data. Am I the only one having this problem and if not is there a setting or something I can adjust to improve things? If not, is OpenOffice available for 14.04?

Thanks in advance for any input.

---

### Post by vasa1 on 2014-07-07
Hi,

I now have to use LibreOffice Calc extensively. I've noticed what you've noticed plus a bit more. My laptop is a Dell 1545 Inspiron with 4GB RAM and a Core2Duo processor. However, it has integrated graphics which I understand means that there's no gpu and that gpu requirements are met by the CPU (???). My OS is Lubuntu 14.04. (I didn't have to use Calc extensively before and so won't comment about performance on earlier Lubuntu versions.)

Just in case anyone asks, I don't use any form of compositing and the window manager is the default, Openbox.

I've reached some sort of understanding with the monster: I seem to need to use just the one font and font size. (Bolding stuff is okay.) If I change the font to my choice (after importing stuff or whatever), **I need to save the file, completely exit LibreOffice and reopen the file**. Then everything is snappy. Otherwise, each step lags making Calc unusable.

I keep a CPU usage monitor/indicator visible. On my system, Calc's sluggishness correlates perfectly with higher CPU usage.

In addition to what you reported, I also see navigation, scrolling, and screen redrawing problems when I have the same spreadsheet open in two windows. I have no solution for that :(

I have gnumeric as well and that seems much quicker but I'm too used to Calc to switch.

If you do switch to OpenOffice Calc and find it's consistently snappier, please post back :)

BTW, no charts, no macros, no JRE.

---

### Post by monkeybrain20122 on 2014-07-07
I don't think your problem is typical. LO runs fast here.
Maybe try upgrade LO [https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)

---

### Post by vasa1 on 2014-07-07
Re. OpenOffice for Ubuntu ... I don't think it's in the Software Center. You'll need to get it "direct": [http://www.openoffice.org/download/](http://www.openoffice.org/download/)

If you need help, the forum is excellent: [https://forum.openoffice.org/en/forum/faq.php?sid=b2f34c887fdd95312a08d31f6ce2d756](https://forum.openoffice.org/en/forum/faq.php?sid=b2f34c887fdd95312a08d31f6ce2d756). I was using OpenOffice Calc when on Windows and got a lot of help from the volunteers there :)

All the best.

PS: also see [http://www.openoffice.org/download/common/instructions.html#linux-preinstall](http://www.openoffice.org/download/common/instructions.html#linux-preinstall)

---

### Post by sandyd on 2014-07-07
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/462487](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/462487)

---

### Post by vasa1 on 2014-07-08
> **sandyd said:**
> [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/462487](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/462487)Yes, I had posted about that here: [http://nabble.documentfoundation.org/Marching-ants-Calc-Xorg-CPU-usage-Ubuntu-td3996853.html](http://nabble.documentfoundation.org/Marching-ants-Calc-Xorg-CPU-usage-Ubuntu-td3996853.html)

But the present problems don't seem to involve the marching ants. In any case, I've turned off anti-aliasing.

I'll give Calc a try again :)

---

### Post by vasa1 on 2014-07-08
Turning off anti-aliasing seems to have improved things! Now, I can have two windows open and scroll happily in each. And even have a different font size.

@Sandyd, thanks for the reminder :)

I hope OP (original poster) tries this: it's under Tools, Options, View, Use anti-aliasing. That's ticked by default. So I unticked it.

---

### Post by ian49 on 2014-07-14
Just to feedback that my own problem appears to have been related to compiz rather than LibreOffice itself as since switching to metacity I've not had the lockups/slowness occur. I've only done that a few hours ago though so hopefully I'm not jumping the gun in suggesting the problem has gone away.

---

