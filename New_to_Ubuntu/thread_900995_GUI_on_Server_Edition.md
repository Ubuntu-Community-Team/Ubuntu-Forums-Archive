---
title: "GUI on Server Edition"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by _neS on 2008-08-25
hi guys,

Is there a GUI in Server Edition of UBUNTU?
If there is, how can i apply it in my pc?

Thanks.

---

### Post by gaspard.leon on 2008-08-26
short: 
```
sudo apt-get install gnome-desktop-environment
```


long:
You need to install one of the GNOME, KDE or XFCE desktop environments using aptitude.

I suggest the GNOME one because it's the best supported, although XFCE is very light...

I'm not sure what you're trying to achieve however, if you're looking to use the server as a multi-role server/workstation, or if you're just trying to find a management interface or some such.

---

### Post by zeronothing on 2008-08-26
Their is really no set gui for server edition. your best bet is to install whatever destkop you would like. This could be xubuntu, ubuntu, kubuntu desktop on top of the server edition. in order to do this just enter in the command at the server commandline. of course you have to login under the commandline interface and do:

sudo apt-get install "which ever desktop"-desktop

Ex. sudo apt-get install ubuntu-desktop

This will install the ubuntu gui on top of the server install. I would recommend using the xubuntu because it requires less system resourses. If you just need an interface to the server edition because you not to familiar with commandline. try looking at the "Webmin" project. Its a web base frontend to the server edition. It allows you to controll the system through your web browser. check it out [[COLOR="Blue"]here[/COLOR]]("http://www.webmin.com/"), have fun..

---

### Post by _neS on 2008-08-26
thanks guys.. it really help..

---

