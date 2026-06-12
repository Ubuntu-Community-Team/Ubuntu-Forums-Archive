---
title: "accounting software for lubuntu"
date: 2015-04-21
forum: New to Ubuntu
---

### Post by Cristian1969 on 2015-04-21
HI
I need an software accounting for lubuntu for my limited company. I haved in ubuntu manager, very good software. I need somethint similary for lubuntu. There is somebody can help me?

---

### Post by Impavidus on 2015-04-21
Everything that can be installed on Ubuntu can also be installed, in the same way, on Lubuntu.

(One catch, sometimes you need an awful lot of new dependencies, but that's mostly an issue when moving to/from Kubuntu.)

---

### Post by Vladlenin5000 on 2015-04-21
Hi and welcome.

The software available in the repositories is the same. The one you're looking for is probably [Manager - Accounting software]("https://apps.ubuntu.com/cat/applications/manager-accounting/") (up xUbuntu 14.04). So...

- If you have **Lubuntu 14.04** you can install it from the Lubuntu Software Center, searching by "manager-accounting" or in terminal ```
sudo apt-get install manager-accounting
```

- If you have **Lubuntu 14.10** or **15.04** then you can download the deb file from [http://www.manager.io/desktop/download/](http://www.manager.io/desktop/download/) (just click download under Ubuntu), and open it with the default option.

---

### Post by ajgreeny on 2015-04-21
**sudo apt-get install manager-accounting** does not work in 14.04; that package is not in the repos.

Your link to the .deb file suggests it will install OK but in my Xubuntu 14.04 it requires a lot of dependencies, most of which are mono packages and libs.

---

### Post by Vladlenin5000 on 2015-04-21
Installed fine on Ubuntu 15.04.
It should be in the repos: [https://apps.ubuntu.com/cat/applications/manager-accounting/](https://apps.ubuntu.com/cat/applications/manager-accounting/)

---

### Post by ajgreeny on 2015-04-21
That link does not say it is in the repos.
It is just a download page for the .deb package.

---

### Post by Vladlenin5000 on 2015-04-21
It actually says it is, in both 12.04 and 14.04 (and no surprise, a professional software being only available for LTS).
The button "Available on the Software Centre" is merely a call for "apt://manager-accounting"...

If it isn't installing in your xUbuntu 14.04 then probably you have something wrong in your sources list.

---

### Post by corbin.loftis on 2015-04-21
I have used Grisbi and GNUcash in the past. Both work well and are free.

---

### Post by ajgreeny on 2015-04-22
> **Vladlenin5000 said:**
> It actually says it is, in both 12.04 and 14.04 (and no surprise, a professional software being only available for LTS).
The button "Available on the Software Centre" is merely a call for "apt://manager-accounting"...

If it isn't installing in your xUbuntu 14.04 then probably you have something wrong in your sources list.
Nothing wrong with them, but I never use software-centre as I prefer synaptic.  Perhaps it needs software-centre, which I am just about to try.

Yes, indeed, I have just searched with SC and it does appear in that.
I have to admit that I was not aware that certain packages are available in one but not the other; I must remember that.  However, the terminal **apt-get** command does not work; I tried that before and got the normal error for non-found package.

---

### Post by vasa1 on 2015-04-22
> **ajgreeny said:**
> ...
Perhaps it needs software-centre, which I am just about to try.

Yes, indeed, I have just searched with SC and it does appear in that.
I have to admit that I was not aware that certain packages are available in one but not the other; I must remember that. ...
I had a somewhat [similar experience]("http://askubuntu.com/questions/192705/whats-the-difference-in-content-between-the-ubuntu-and-lubuntu-software-centers") sometime ago: software in USC wasn't in Lubuntu's SC (unlike Xubuntu and Ubuntu Mate which have the same SC as Ubuntu).

---

### Post by dino99 on 2015-04-22
Manager-accounting is a third app, not referenced into ubuntu's archives. 
But you can find 'postbooks-updater' from the ubuntu's archive:
A full-featured, fully-integrated business management system, the core of the award winning xTuple ERP Suite. Built with the open source PostgreSQL
database and the open source Qt framework for C++, it provides the ultimate in power and flexibility for a range of businesses and industries of any size.

---

### Post by HermanAB on 2015-04-22
There is also SQLLedger, which is a full featured program, not gratis, but not expensive either.

---

### Post by carlexpc on 2015-04-23
Install Gnucash, and it's available in the Ubuntu repository.

---

