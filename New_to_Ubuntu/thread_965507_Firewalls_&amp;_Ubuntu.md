---
title: "Firewalls &amp; Ubuntu"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Sailorcancer on 2008-10-31
I'm not all that knowledgeable about Linux and I'm learning a little each day.

I noticed that there are some firewall programs in the add/remove section and I was wondering if I should install one of them?

I know that everyone says that Linux is ultra safe and that firewall/antivirus/spyware protection is not really needed.  Due to the fact that there are not that many out there, and the ones that are pretty much are "jokes".  

So should I just skip the firewall, or should I get one?  And if I get one which one will be good?

---

### Post by Sarmacid on 2008-10-31
You don't really need a firewall, unless you're running some services.

If you plan on setting one up, try iptables, it comes installed by default but is command line only. Check out these links to learn more about it
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

There is also a front end for iptables called firestarter, to install it run ```
sudo apt-get install firestarter
```

---

### Post by Sailorcancer on 2008-10-31
So firestarter is like a GUI for the built in firewall?

---

### Post by Sarmacid on 2008-10-31
> **Sailorcancer said:**
> So firestarter is like a GUI for the built in firewall?

Exactly

---

### Post by gandaran on 2008-10-31
I would recommend gufw, its a lot easier to setup
for ubuntu 8.10 it's in the repos, for 8.04 download here [http://gufw.tuxfamily.org/](http://gufw.tuxfamily.org/)

---

