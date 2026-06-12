---
title: "Problem configuring Wine"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by Dibbling Dave on 2008-11-30
I am trying to configure wine to run internet explorer. Problem is the main window does not let me click (or see) the OK button. See Picture
[IMG]http://space.davethould.fastmail.fm/public/Screenshot-Default%20-%20Wine%20desktop-1.png[/IMG]
I have uninstalled and reinstalled Wine using the add/remove under applications and am now stuck for ideas. Dave.

---

### Post by Efros on 2008-11-30
Are you just running winecfg from the terminal?

---

### Post by Dibbling Dave on 2008-11-30
No, I have tried that. I'm running wine from the Applications list

---

### Post by Efros on 2008-11-30
If I run winecfg from terminal I don't get the desktop that you have, the window is on its own. I think you may have "Emulate a virtual desktop" enabled on the graphics tab of the winecfg applet. If that is the case uncheck it and tab 5 times, this will take you to the OK button even if you can't see it, then hit return.

---

### Post by Dibbling Dave on 2008-11-30
That did the trick, I can now see the whole of the applet. I will have a go at configuring ie now. Thanks.

---

### Post by Efros on 2008-11-30
You're welcome! Glad it worked out.

---

### Post by Dibbling Dave on 2008-11-30
I have an internet explorer window but cannot seem to get anything in it.
[IMG]http://space.davethould.fastmail.fm/public/Screenshot-Wine%20Internet%20Explorer.png[/IMG]
What am I doing wrong?

---

### Post by Keen101 on 2008-11-30
I'm not an expert when it comes to wine. But, if you really want internet explorer, then try **ie4linux**. I used ie4linux once, and it installed ie6 just fine.

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by Dibbling Dave on 2008-11-30
Thanks I need internet explorer for web developing. I will give ie4linux a try. Dave.

That worked, I shall give Wine another go another day.

---

### Post by Efros on 2008-11-30
You should perhaps look at a virtual machine of XP within Ubuntu.

---

### Post by w4ett on 2008-11-30
Another option is Crossover Linux Standard...you can try it for free:

[http://www.codeweavers.com/products/cxlinux/download_trial/](http://www.codeweavers.com/products/cxlinux/download_trial/)

---

