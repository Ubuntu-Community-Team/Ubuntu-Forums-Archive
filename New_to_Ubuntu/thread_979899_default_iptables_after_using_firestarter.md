---
title: "default iptables after using firestarter"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by myddewji13 on 2008-11-12
Hi,

Ive been using firestarter for awhile now and after messing around with the settings I am unable to print to my networked printer unless i disable the firewall (even after allowing incoming/outgoing connections on appropriate ports etc..). The printing seems to work with a fresh install of ubuntu (on my moms laptop) with no problems whatsoever. So how do i revert to the default iptables config?

---

### Post by alpage2 on 2008-11-12
One approach which will be good for learning more about iptable firewalls will be to uninstall firestarter and roll your own firewall with the help of this tutorial:

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Alan

---

### Post by myddewji13 on 2008-11-12
so let me get this straight...short of a clean install there is not way for me to get a default iptables?!?!

---

### Post by brian_p on 2008-11-13
> **myddewji13 said:**
> so let me get this straight...short of a clean install there is not way for me to get a default iptables?!?!

Not at all!

```
apt-get remove --purge firestarter
```

Check iptables rules. After a reboot may be wise.

```
sudo -L iptables
```

How's that?

---

### Post by hyper_ch on 2008-11-13
> **myddewji13 said:**
> so let me get this straight...short of a clean install there is not way for me to get a default iptables?!?!
There is... just delete all rules in iptables... that's the default setting and it's a good one.

---

### Post by alpage2 on 2008-11-13
> **hyper_ch said:**
> There is... just delete all rules in iptables... that's the default setting and it's a good one.

Let's just be clear what is meant by the 'default iptables' that you want to return to. By default, in a fresh installation, no packet filtering rules have been set. Yes, it can't block any communication, but that is because you have no firewall!

It is easily done at the command line. Once you have removed firestarter, type:

sudo iptables -L

will list all the current packet filtering rules. It might give you a clue as to how firestarter was causing problems. Follow with:

sudo iptables -F

which will flush all the packet filtering rules.

List the rules again, and see the difference.

Take a look at the link provided in the first reply in this thread - it will show you how to apply your own simple firewall rules, which should not interfere with what you want to do.

Alan

---

