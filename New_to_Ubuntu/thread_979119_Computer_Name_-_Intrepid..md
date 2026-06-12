---
title: "Computer Name - Intrepid."
date: 2008-11-11
forum: New to Ubuntu
---

### Post by Roasted on 2008-11-11
How can I find it? And wherever I can find it, is it changable there?

---

### Post by Iowan on 2008-11-11
I presume you're talking about the hostname.  It's in /etc/hostname and can be changed, but be sure to change the entry in /etc/hosts as well (or **sudo** will complain).
[http://ubuntuforums.org/showthread.php?t=977968]("http://ubuntuforums.org/showthread.php?t=977968")

---

### Post by Axos on 2008-11-11
When I changed /etc/hostname last week, some sort of daemon creature updated /etc/hosts automatically. I was surprised! :)

---

### Post by Roasted on 2008-11-11
In previous versions of Ubuntu, I always went to system - admin - network and clicked on the general tab. But, this isn't the case in Intrepid... hence why I'm confused.

---

### Post by jmjohn on 2009-06-02
Is there a way to change the computer name as before with the GUI?  Where did Sytem -> Network go?

---

### Post by Celauran on 2009-06-02
> **jmjohn said:**
> Is there a way to change the computer name as before with the GUI?  Where did Sytem -> Network go?

System -> Administration -> Network -> General?

---

### Post by philinux on 2009-06-02
Install gnome-network-admin. It's not installed by default.

---

### Post by jmjohn on 2009-06-02
Thanks.

sudo apt-get install gnome-network-admin

Then, using the menus:
System -> Administration -> Network

And I can change the computer name via the GUI.

---

