---
title: "Restricted access in opt/lampp/htdocs"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by stookin on 2012-04-17
Hello guys

I just installed LAMPP (or XAMPP for Linux) and I want to create and edit files in "opt/lampp/htdocs"

However to edit/delete/move files is restricted in this directory.

How do I solve this problem?

---

### Post by Lars Noodén on 2012-04-17
Probably the easiest way to solve it is to remove /opt/lampp and try again using the Ubuntu package manager.  If you persist in trying without the package manager, you will have several packages redundant with what is already installed and will also have to manually do security updates.  If you choose to go ahead and use Ubuntu's package manager (either via Synaptic or via the Software Center) then it will automatically take care of dependencies and keep you up to date with patches and security upgrades.

With the standard LAMP setup (via the package manager) your files will be in /var/www.  If you are the only user on that machine, then it is enough that you change ownership of the directory and files to your own account.

```

sudo chown -R stookin /var/www

```

You'll find Apache, MySQL and PHP in the package manager.   Perl is already installed by default.

---

### Post by stookin on 2012-04-17
sorry I solved it using:
sudo chmod 777 /opt/lampp/htdocs

---

### Post by stookin on 2012-04-17
> **Lars Noodén said:**
> Probably the easiest way to solve it is to remove /opt/lampp and try again using the Ubuntu package manager.  If you persist in trying without the package manager, you will have several packages redundant with what is already installed and will also have to manually do security updates.  If you choose to go ahead and use Ubuntu's package manager (either via Synaptic or via the Software Center) then it will automatically take care of dependencies and keep you up to date with patches and security upgrades.

With the standard LAMP setup (via the package manager) your files will be in /var/www.  If you are the only user on that machine, then it is enough that you change ownership of the directory and files to your own account.

```

sudo chown -R stookin /var/www

```

ah thank you, read your answer a little late

---

