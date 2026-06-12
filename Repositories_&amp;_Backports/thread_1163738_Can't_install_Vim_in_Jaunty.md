---
title: "Can't install Vim in Jaunty"
date: 2009-05-19
forum: Repositories &amp; Backports
---

### Post by aliov_85 on 2009-05-19
I'm trying to install Vim with no success. I've ruby(1.8.6) on rails(2.3.2) already installed.

But when I try to install "vim-gnome" through Synaptic, I get the following:

> 

vim-gnome:
  Depends: libruby1.8 (>=1.8.7.72) but 1.8.6.111-2ubuntu1 is to be installed


Can anyone help me to solve this installation problem please?

Regards
Ali

---

### Post by stroyan on 2009-05-21
You should be able to install the newer libruby1.8.
Apt-get should just pull it when you install vim-gnome.
Have a look at your apt sources and see if they really match jaunty.
You can check the available versions with apt-cache-
apt-cache show libruby1.8
Look at the "Version" line, which should be "Version: 1.8.7.72-3".

---

