---
title: "Uninstall kubuntu"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by jrw690 on 2008-10-06
I have installed kubuntu on my laptop and ubuntu on my desktop pc.  I prefer ubuntu and want to install it on my laptop, but the laptop will not boot with the unbutu cd, it goes directly to the kubuntu operating sysem.  Is there any way to uninstall kubuntu and then install ubuntu?

---

### Post by tuxxy on 2008-10-06
Yes you could install GNOME then remove KDE to leave you with essentially Ubuntu.

To install GNOME you would need ubuntu-desktop pavkage and also gdm.

```
sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
sudo /etc/init.d/gdm start
```

Now to [remove KDE ]("http://www.psychocats.net/ubuntu/puregnome.php")

---

### Post by jrw690 on 2008-10-10
Thank you.

---

