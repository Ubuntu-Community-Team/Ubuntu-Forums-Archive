---
title: "Installing a downloaded package"
date: 2014-01-27
forum: New to Ubuntu
---

### Post by richard30 on 2014-01-27
I've downloaded a package called pyme_0.8.1+clean.orig.tar.gz for Ubuntu Server (Lucid). I don't have the foggiest idea how to install this package. Being the Server edition, I only have the command line.

Thanks.

---

### Post by jones quest on 2014-01-27
The package your trying to install is presumably called python-pyme in ubuntu. You can install this using the package manager:
sudo apt-get install python-pyme

or 

You can manually install the downloaded file by first opening the archive:
tar -zxvf pyme_0.8.1+clean.orig.tar.gz
Then look inside the folder created for the makefile, readme, install, setup files etc.

The usual way to install programs manuall if it's a source file is to first build and install (specific instructions are usually contained in the readme file):
make && sudo make install
If it's a pre-build binary then you might not need to do anything else, or you might have to configure the program with setup or install or some other file... It really depends on the program your installing.

---

### Post by Bucky Ball on 2014-01-27
Welcome. Be advised that support ended for 10.04 LTS (Lucid Lynx) in April last year so moving to the latest LTS and an upgrade to the next (14.04 LTS) this April (if you want to) might be your best course of action. The LTS (long-term support) releases now have five years support. 

The easiest way to install, as suggested, is from the repositories with this:

sudo apt-get install python-pyme

... but you might have no luck as support has ended. As well as regular updates, this also means you will not get security updates so being online with this machine is not great.

Are you new to Ubuntu?

---

### Post by aysiu on 2014-01-27
> **Bucky Ball said:**
> Welcome. Be advised that support ended for 10.04 LTS (Lucid Lynx) in April last year so moving to the latest LTS and an upgrade to the next (14.04 LTS) this April (if you want to) might be your best course of action. The LTS (long-term support) releases now have five years support.  The OP is using the server edition, which is still supported for another year, even though the desktop edition lost support last year:
[http://fridge.ubuntu.com/2013/05/10/ubuntu-10-04-lucid-lynx-desktop-end-of-life-reached-on-may-9-2013/](http://fridge.ubuntu.com/2013/05/10/ubuntu-10-04-lucid-lynx-desktop-end-of-life-reached-on-may-9-2013/)

Still, your advice is good. There is already a solid LTS release to upgrade to right now--12.04.3.

---

### Post by Bucky Ball on 2014-01-27
> **aysiu said:**
> The OP is using the server edition, which is still supported for another year, even though the desktop edition lost support last year ...

My mistake, of course! Apologies. Getting late here, I should go to bed. ;)

---

