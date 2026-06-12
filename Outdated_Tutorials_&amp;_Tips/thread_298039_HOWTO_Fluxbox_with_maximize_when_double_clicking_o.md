---
title: "HOWTO: Fluxbox with maximize when double clicking on Windows Title Bar"
date: 2006-11-12
forum: Outdated Tutorials &amp; Tips
---

### Post by patrick295767 on 2006-11-12
Howto Make dblclick titlebar maximize
====================================
  
  
Hi, 
 
I made a deb for this purpose
(You can download the deb there [here]("http://patrick295767.sitesled.com/miniram/dblclickfluxbox_1.0rc2-1_i386.deb") )
  
  
   

So, the installation steps are :
```

cd /tmp
wget http://patrick295767.sitesled.com/miniram/startfluxbox 
wget http://patrick295767.sitesled.com/miniram/dblclickfluxbox_1.0rc2-1_i386.deb
sudo su
rm -rf  /usr/bin/fluxbox   #to make sure you have it right
dpkg -i dblclickfluxbox_1.0rc2-1_i386.deb
cp -a /usr/local/share/fluxbox/ /usr/share/
ln -s /usr/local/bin/fluxbox /usr/bin/fluxbox
mv /tmp/startfluxbox   /usr/bin/startfluxbox
chmod uog=rx  /usr/bin/startfluxbox
```

and create the file     /usr/share/xsessions/dcfluxbox.desktop     containing:
```
[Desktop Entry]
Encoding=UTF-8
Name=Fluxbox
Comment=Highly configurable and low resource X11 Window manager
Exec=/usr/bin/startfluxbox
Terminal=False
TryExec=/usr/bin/startfluxbox
Type=Application

[Window Manager]
SessionManaged=true

```
The new xsession dcfluxbox has the maximize dblclicktitlebar function.

Enjoy !!

Double click on the title bar, makes the window un-/ maximized


---
(I am missing some styles but it works fine, I will try to make soon a deb with more of them included)
 
:KS 
 
 ---------
my lsb_release:
[I]lsb_release -a
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.1 LTS
Release:        6.06
Codename:       dapper[/I]

---

