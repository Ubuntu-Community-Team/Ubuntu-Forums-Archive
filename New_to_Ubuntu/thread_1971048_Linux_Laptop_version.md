---
title: "Linux Laptop version?"
date: 2012-05-02
forum: New to Ubuntu
---

### Post by KdHBuntu on 2012-05-02
When you go to download linux, it is ubuntu desktop, but I heard somewhere there is ubuntu laptop for lower end laptops. Is this true?

---

### Post by jerome1232 on 2012-05-02
Kind of.


Ubuntu Desktop isn't what your thinking, it's just the standard version with Unity as the Desktop Environment, You need at least 1 GB of ram to really use it with satisfactory performance.


For systems that aren't so powerful we have Xubuntu, which uses xfce as the desktop environment, and Lubuntu, which uses LXDE for it's desktop environment.

Lubuntu is lighter than Xubuntu which is lighter than Ubuntu.

What are the specs for your laptop? I run Ubuntu Desktop on my netbook (1 GB ram, has a weak atom processor) and it runs fairly fast.

---

### Post by KdHBuntu on 2012-05-02
> **jerome1232 said:**
> Kind of.


Ubuntu Desktop isn't what your thinking, it's just the standard version with Unity as the Desktop Environment, You need at least 1 GB of ram to really use it with satisfactory performance.


For systems that aren't so powerful we have Xubuntu, which uses xfce as the desktop environment, and Lubuntu, which uses LXDE for it's desktop environment.

Lubuntu is lighter than Xubuntu which is lighter than Ubuntu.

What are the specs for your laptop? I run Ubuntu Desktop on my netbook (1 GB ram, has a weak atom processor) and it runs fairly fast.

[http://reviews.cnet.com/laptops/lenovo-thinkpad-x100e/4507-3121_7-33960160.html](http://reviews.cnet.com/laptops/lenovo-thinkpad-x100e/4507-3121_7-33960160.html)
These are my specs. Its a lenovo thinkpad x100e. Everything is fine but the dash home is fairly laggy for me :(. Mabey its because im using wubi and not a partition? (Btw im on windows 7)

---

### Post by jerome1232 on 2012-05-02
Have you installed ATI proprietary drivers? Click the cog in top right, System Settings->Additional drivers. They may help. Wubi does impact performance a bit, mostly reading/writing to/from disk will eat a lot more cpu than with a standard install.


If Unity is just to slow for you, you can try the other environments out without re-installing, open a terminal (ctrl+alt+t) and....

To try gnome-shell (I would first recommend trying this, it's a smaller install since it shares almost everything in common with unity, is similar to Unity, and as I understand it, is slightly lighter than Unity)
```
sudo apt-get install gnome-shell
```


for Xubuntu
```
sudo apt-get install xubuntu-desktop
```

for Lubuntu
```
sudo apt-get install lubuntu-desktop
```

another option is kde, or kubuntu
```
sudo apt-get install kubuntu-desktop
```


To swap between installed sessions you click the gear symbol at the login screen and select the appopriate session.

---

