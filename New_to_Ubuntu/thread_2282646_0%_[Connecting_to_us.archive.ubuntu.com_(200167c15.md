---
title: "0% [Connecting to us.archive.ubuntu.com (2001:67c:1562::14)] - Install not happening"
date: 2015-06-15
forum: New to Ubuntu
---

### Post by deepak29 on 2015-06-15
Please help. I am not able to install anything from the us.archive.ubuntu.com site.

Installation gets stuck with the following error. I am able to ping us.archive.ubuntu.com though.

0% [Connecting to us.archive.ubuntu.com (2001:67c:1562::14)]



Here is the full log.

```
 sudo apt-get install vim-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libbonoboui2-0 libbonoboui2-common libgnomecanvas2-0 libgnomecanvas2-common
  libgnomeui-0 libgnomeui-common libruby1.9.1 libyaml-0-2 ruby ruby1.9.1
  vim-gui-common vim-runtime
Suggested packages:
  ri ruby-dev ruby1.9.1-examples ri1.9.1 graphviz ruby1.9.1-dev ruby-switch
  cscope vim-doc ttf-dejavu
The following NEW packages will be installed:
  libbonoboui2-0 libbonoboui2-common libgnomecanvas2-0 libgnomecanvas2-common
  libgnomeui-0 libgnomeui-common libruby1.9.1 libyaml-0-2 ruby ruby1.9.1
  vim-gnome vim-gui-common vim-runtime
0 upgraded, 13 newly installed, 0 to remove and 223 not upgraded.
Need to get 9,264 kB of archives.
After this operation, 43.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
0% [Connecting to us.archive.ubuntu.com (2001:67c:1562::16)]


```

Thank you,
Deepak

---

### Post by sandyd on 2015-06-15
Sometimes, the Ubuntu mirrors are not reachable over IPv6.

Run the following
```

sudo nano /etc/gai.conf

```
Scroll with arrow keys down to where it says
```

#precedence ::ffff:0:0/96  100
```
and remove the comment (#)

Press control+x to save, and you should be on your way.

---

### Post by deepak29 on 2015-06-15
Still not working - I tried the above and also restarted ubuntu - still gets the same error

---

### Post by wildmanne39 on 2015-06-15
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by deepak29 on 2015-06-15
> **deepak29 said:**
> Still not working - I tried the above and also restarted ubuntu - still gets the same error

I just switched from my wired connection to my wifi connection and it started working - weird. :)

Thanks for your help.
Deepak

---

