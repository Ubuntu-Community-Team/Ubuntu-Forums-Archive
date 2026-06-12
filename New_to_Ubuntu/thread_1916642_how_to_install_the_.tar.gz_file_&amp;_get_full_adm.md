---
title: "how to install the .tar.gz file &amp; get full administrative right"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by csejunker on 2012-01-28
whenever i try to install the tar.gz file i can do no more than extracting using terminal.
as in some thread written read the readme file for instruction .  while executing the instructions like "make install" it slams me with insufficient administrative  right.
how to get full "administrative right" to do anything u want

---

### Post by snowpine on 2012-01-28
Welcome to the forums! But you need to slow down and give us more information... what is "the tar.gz file"?

Here is a basic introduction to "how to get administrative rights in Ubuntu": [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

For example:

```
sudo make install
```

If you tell us more about the application you're trying to install, and where you got it, we can give you specific advice. :)

---

### Post by lechien73 on 2012-01-28
Hi and welcome to the forums,

Depending on what you want to install - and where - you could try:

```
sudo make install
```

Enter your password, when prompted - and note that your password won't be displayed as you type.

"sudo" gives you administrative capabilities, see this page for more information: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

EDIT: @snowpine - snap :D

---

### Post by Lars Noodén on 2012-01-28
There should be a file called 'README' or 'INSTALL' which will contain the build instructions.

However, first make sure that the program is not already available in the package repositories.  It is infinitely easier and more manageable to use Synaptic or the Software Center.

If and only if the package is not available via the Ubuntu repositories, then you can try building from source.  Even then, it's best to [build a .deb package](http://tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/) and go via the package manager.

---

