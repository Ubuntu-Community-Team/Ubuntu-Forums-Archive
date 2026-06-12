---
title: "wget, Server and package removal"
date: 2011-11-13
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2011-11-13
Using the [following]("http://www.cherokee-project.com/doc/basics_installation_easy-install.html"):

wget [http://cherokee-project.com/install](http://cherokee-project.com/install) && python install

I installed the Cherokee server. I want to remove it and see it also install python, which I **don't** want to remove. 

By the bye: the GNU WGET manual has no mention of how to remove packages (software, applications) that it installed.

---

### Post by Cyclane on 2011-11-13
wget is used to download the install script after that it uses python to install cherokee.

run the following command and try again:
> sudo apt-get build-dep cherokee

---

### Post by Mark_in_Hollywood on 2011-11-13
This is how to remove or uninstall? I ran 

sudo apt-get build-dep cherokee

and it wants to install another 27 meg

---

### Post by Cyclane on 2011-11-13
> **Mark_in_Hollywood said:**
> This is how to remove or uninstall? I ran 

sudo apt-get build-dep cherokee

and it wants to install another 27 meg

Pardon me, I misunderstood you. I though you where trying to install cherokee.

Uninstalling programs can be difficult if not installed with a package manager. I'm sorry but I cannot help you with this.

---

