---
title: "duplicate desktop icons"
date: 2012-11-08
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-11-08
running xubuntu 12.10. if i go to settings manager/desktop/icons and click on removable devices it shows up twice on my desktop. that is my other partition and any cd i put in will have the icons displayed twice. however if i click on show home or trash on one set of icons appear. dont know why the aforementioned is duplicated. any ideas how to fix

---

### Post by rburkartjo on 2012-11-08
here is link showing problem has anyone found a fix 

[https://bugs.launchpad.net/ubuntu/+source/xfce4/+bug/1044896](https://bugs.launchpad.net/ubuntu/+source/xfce4/+bug/1044896)

---

### Post by verymadpip on 2012-11-08
There's a bunch of us waiting for a fix, which is in the pipeline I think.  There appear to be 2 issues; one for the desktop & one for Thunar which are being handled separately

If you go into settings editor > xfce desktop > icons > style & then edit the value from 2 to 1 & then back to 2 again that will temporarily solve the issue.  I have to open Thunar twice for it to take effect in the side pane.  This will, however, reset itself on the next boot.

---

### Post by rburkartjo on 2012-11-08
ver tks for the info thought it might be just me until i found the bug report.

---

### Post by rburkartjo on 2012-11-17
just updating has anyone found a fix yet?

---

### Post by verymadpip on 2012-11-21
You could try:
[http://ubuntuforums.org/showthread.php?t=2079661](http://ubuntuforums.org/showthread.php?t=2079661) post #10.

For me Thunar has sorted itself out, desktop remains the same.  The F5 thing worked sometimes so I continued with the settings editor business for a while.

I ran into a couple of other unrelated problems (I think) that were pretty much deal breakers so I reverted the problem machine to 12.04.  I may just go with LTS releases on it.

---

### Post by rburkartjo on 2012-11-21
very tks for that f5 tip. works great! i have to use it every time if login or reboot to get the to get rid of the double icons. will be glad when this is finally fixed.

---

### Post by Elfy on 2012-11-21
I don't have this anymore - I have proposed repo's enabled, fixes landed there during the week in there.

---

### Post by COMECON on 2012-11-21
It's a known bug, look at [Xubuntu 12.10 release announcement](http://xubuntu.org/news/12-10-release/).

---

### Post by rburkartjo on 2012-11-21
el so do i just havent gotten yet. tks for the info

---

### Post by verymadpip on 2012-11-21
Elfy, I am afeared of the proposed repo :)

---

### Post by Elfy on 2012-11-22
> **verymadpip said:**
> Elfy, I am afeared of the proposed repo :)

Well then notmuch I can do about that ... 

However - if you want to see these fixes

Enable proposed

Update

Upgrade only the thunar and xfdesktop

Disable proposed

Update

It'll be fine, no issues here, I've had proposed enabled for almost 7 months with 12.10 [s]Cross fingers and hope for the best :p [/s]

or wait :)

---

### Post by verymadpip on 2012-11-22
Thanks Elfy, I didn't think of that.

The fear came from reading the "warning" thing about proposed & possible partial upgrades yada yada yada.
I swear I'm getting more stupid over time - no need to confirm that for me by the way :)

---

