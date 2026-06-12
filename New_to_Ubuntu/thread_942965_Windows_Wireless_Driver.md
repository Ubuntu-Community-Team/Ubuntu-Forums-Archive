---
title: "Windows Wireless Driver"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by donaldshelton on 2008-10-09
I followed the directions on using windows wireless drivers.  

However, my driver has the .sys extension instead of the .inf

I get the error "invalid .inf file"

I use Vista, and am trying to use Ubuntu.

Thanks

---

### Post by Big_Kahunaca on 2008-10-09
What type of wireless card are you using?

"lspci" and look for Network Controller, post the results.

---

### Post by donaldshelton on 2008-10-09
Atheros AR5007EG Wireless Network Adapter #2

Thanks

:popcorn:

---

### Post by Big_Kahunaca on 2008-10-09
Give this a try...

[http://ubuntuforums.org/showthread.php?t=512828]("http://ubuntuforums.org/showthread.php?t=512828")

---

### Post by carml on 2008-12-03
Search on Google this driver and try itWireless_Atheros_V5.3.0.67_XP_XB63_XB62(WHQL),it worked for me,and it has a .inf file;).
Let us now if it helped you.

---

### Post by s.fox on 2008-12-03
If you have no luck you could try using the windows driver via ndiswrapper.  This, I found is a little tricky and should be a last resort.

---

### Post by Michael.Godawski on 2008-12-03
Here is a how-to if you need it dealing with ndiswrapper:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[http://lxer.com/module/newswire/view/46385/](http://lxer.com/module/newswire/view/46385/)

---

