---
title: "Server 11.04 Install questions"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by durendel on 2011-10-03
I'm trying a fresh install of Server 11.04 on a Lenovo desktop. Eventually this will be moved to a VM if I can get it to work.

I'm trying to make do the LAMP install and getting errors. I'm doing it from a DVD from the image I downloaded here. I select LAMP but get errors on the Apache server install.

I also tried to install the telnet daemon but it doesn't work either. I tried this:

sudo apt-get install telnetd

However the response I get is:

[I]Reading package lists ... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package telnetd[/I]

How can I validate the Apache Server installation? Is there something I'm doing wrong with the telnetd?

Thanks from a newbie

---

### Post by Dangertux on 2011-10-03
Did you do 

```

sudo apt-get update

```

Prior to attempting to install it : also you may have to install the following package to get it

```

sudo apt-get install openbsd-inetd

```

Hope that works for you.

On a side note you should use SSH instead (more secure, more functional etc etc)

```

sudo apt-get install openssh-server

```

---

### Post by durendel on 2011-10-03
Thanks I'll try this. I don't really need SSH since this is a pretty secure network already.

---

