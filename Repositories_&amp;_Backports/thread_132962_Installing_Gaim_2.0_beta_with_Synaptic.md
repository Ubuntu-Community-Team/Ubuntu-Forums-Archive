---
title: "Installing Gaim 2.0 beta with Synaptic?"
date: 2006-02-19
forum: Repositories &amp; Backports
---

### Post by yootje on 2006-02-19
Is it possible to install Gaim 2.0 beta 2 via apt-get? If no, how can I do it?

---

### Post by Harold P on 2006-02-19
I think you can, but you have to change the repositiories, though.

I don't know how to do that. Maybe searching around on the forums could help.

---

### Post by Kimm on 2006-02-19
you can use my build

[http://users.domaindlx.com/LinuxHoster/gaim_2.0.0beta2-1_i386.deb](http://users.domaindlx.com/LinuxHoster/gaim_2.0.0beta2-1_i386.deb)

```
dpkg -i gaim_2.0.0beta2-1_i386.deb
```

Mind the bandwith, its not excelent... its a free host

---

### Post by vassie on 2006-02-19
[quote=Kimm]you can use my build

[http://users.domaindlx.com/LinuxHoster/gaim_2.0.0beta2-1_i386.deb]("http://users.domaindlx.com/LinuxHoster/gaim_2.0.0beta2-1_i386.deb")

```
dpkg -i gaim_2.0.0beta2-1_i386.deb
``` 
Mind the bandwith, its not excelent... its a free host[/quote]

Here is a mirror

[http://195.153.177.76/uploads/ben/linux/ubuntu/gaim_2.0.0beta2-1_i386.deb]("http://195.153.177.76/uploads/ben/linux/ubuntu/gaim_2.0.0beta2-1_i386.deb")

Ben

---

### Post by Kimm on 2006-02-19
Great! Thanks :D

---

### Post by chill on 2006-02-22
how can I get GAIM 2 to run on AMD 64 box?

thanks,

---

### Post by eyelessfade on 2006-02-24
[QUOTE=chill]how can I get GAIM 2 to run on AMD 64 box?

thanks,[/QUOTE]

First hit on google:
[http://www.dissociatedpress.net/?p=130]("http://www.dissociatedpress.net/?p=130")

---

### Post by firepol on 2006-03-20
sudo dpkg -i gaim_2.0.0beta2-1_i386.deb
(Reading database ... 82437 files and directories currently installed.)
Unpacking gaim (from gaim_2.0.0beta2-1_i386.deb) ...
dpkg: error processing gaim_2.0.0beta2-1_i386.deb (--install):
 trying to overwrite `/usr/share/applications/gaim.desktop', which is also in package gaim-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 gaim_2.0.0beta2-1_i386.deb


I renamed the gaim.desktop to gaim.desktop.back... it gives me the same problem.

I uninstalled gaim. Same problem. How do you install the deb provided in this thread??

---

### Post by WoS on 2006-03-29
Remove gaim-data package then try again ;)
It worked for me ....

---

### Post by Sonique on 2006-04-01
that works, thanks

```
sudo apt-get remove gaim-data
```

---

