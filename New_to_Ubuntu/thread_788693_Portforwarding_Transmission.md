---
title: "Portforwarding Transmission"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by Cephaus on 2008-05-10
[IMG]http://img210.imageshack.us/img210/7676/omgizzvn4.png[/IMG]

Im pretty sure I have the right port open, but It still says port closed

halppppp

---

### Post by Xiong Chiamiov on 2008-05-10
When you look in the transmission settings, what port does it say it's using?  It better be 12825.  That said, you should also forward UDP as well.  And if you run ifconfig, does it say your address is 192.168.1.104?

---

### Post by Cephaus on 2008-05-10
No, it says that it is 192.168.1.105

So I changed it and it still says its still closed

---

### Post by eriqjaffe on 2008-05-10
At the risk of stating the obvious, you're saving the settings on the router before you check in Transmission, right?

---

### Post by Cephaus on 2008-05-10
yes

---

### Post by Cephaus on 2008-05-10
anyone?

---

### Post by FuturePilot on 2008-05-10
Have you started a torrent? If you have UPnP enabled on your router it will automatically open the port when you load a torrent.

---

### Post by Xiong Chiamiov on 2008-05-10
I noticed that sometimes it would take a while for settings on my WRT54GL to save, or occasionally, they wouldn't seem to ever take effect.  But now I'm running dd-wrt and lovin' it.

---

