---
title: "Failure to start firestarter?"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-05-15
Hi folks, 

I did a boot under verbose mode, during which the following popped up (along with some other stuff, but that's OK):

```

stopping firestarter firewall...successful
starting firestarter firewall...fail!

```

Is this something to be concerned about? Or is it because I've previously run firestarter and had it do its configuration everything is OK and I have some modicum of protection? 

Thanks, 

-'Mage

---

### Post by bodhi.zazen on 2008-05-15
Well, a few things ...

First your firewall is iptables. To see your settings :

```
sudo iptables -L
```

Firestarter is a gui front end to configure iptables.

You can try opening firestarter in a terminal :

```
gksu firestarter
``` and see if it gives any further error messages.

Otherwise I suggest you look into ufw. ufw is a command line interface to iptables configuration and is both more sophisticated and easy to use.

[UFW (Uncomplicated Firewall)]("https://help.ubuntu.com/8.04/serverguide/C/firewall.html")

[Howto:  Use, setup, and Take advantage of the New Ubuntu Uncomplicated Firewall UFW]("http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html")

---

### Post by UnWarierMage224 on 2008-05-15
Ah I see. 

Thanks!

-'Mage

---

