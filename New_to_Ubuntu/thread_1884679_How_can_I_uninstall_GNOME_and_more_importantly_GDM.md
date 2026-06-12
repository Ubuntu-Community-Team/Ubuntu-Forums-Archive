---
title: "How can I uninstall GNOME and more importantly GDM?"
date: 2011-11-21
forum: New to Ubuntu
---

### Post by venom104 on 2011-11-21
I've been looking on the internet for a way to uninstall gnome and GDM. I've found a bunch of commands that will uninstall GNOME, but I have to sort though them to find and keep programs that I use. I haven't found anything that will uninstall GDM though.

So, I guess my question here is

1)How can I get the GDM daemon to stop running ([http://www.flickr.com/photos/venom104/6379759025/](http://www.flickr.com/photos/venom104/6379759025/) ) and how do I uninstall it?
2)If I don't use GNOME, is it safe to uninstall the gnome shell? What about Unity? What's the best way to uninstall gnome/unity?

I'm running Ubuntu 11.10 and I am using the KDE plasma desktop.

---

### Post by Harry.k on 2011-11-21
just open synaptic, enter the search term as 'gnome' and remove the packages individually.

---

### Post by venom104 on 2011-11-21
> **Harry.k said:**
> just open synaptic, enter the search term as 'gnome' and remove the packages individually.


Correct me if I am wrong but isn't synaptic not installed on 11.10 ubuntu OSes? IF not, how would I do that in KDE, i don't see it in the control center.

---

### Post by lolpenguin on 2011-11-22
> **venom104 said:**
> Correct me if I am wrong but isn't synaptic not installed on 11.10 ubuntu OSes? IF not, how would I do that in KDE, i don't see it in the control center.
Run in a terminal:
```
sudo apt-get install synaptic
```
**recommended method**
Use Harry.k's method. It is safer than manual method.
**Manual method**
For safety, launch a tty using Ctrl+Alt+F1 (or F2 - F6), and login.
To kill GDM:
```
sudo service gdm stop
```
To remove all GNOME components (firstly make sure none of them are running):
```
sudo apt-get remove ubuntu-desktop
```
This will uninstall ALL of GNOME and Unity. If you also want all program settings, configuration, etc. remove run this instead:
```
sudo apt-get purge ubuntu-desktop
```
After this run
```
sudo dpkg-reconfigure kdm
``` and set the default display manager as KDM and reboot with
```
sudo reboot
```

---

### Post by raja.genupula on 2011-11-22
Hi man do you want to remove ubuntu-desktop and run with KDE then use this command by opening your terminal.

(apt-cache depends ubuntu-desktop; apt-cache depends kde-desktop; apt-cache depends kde-desktop) | cut -d ':' -f 2 | tr -d [:blank:] | sort | uniq -u | tr [:space:] ' ' | xargs sudo apt-get -y purge
this worked for me. I am sure that gonna help you. 
All the best.

---

### Post by mastablasta on 2011-11-22
see here on how to remove and get pure KDE (kubuntu): [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
 
As iknow some porgrammes use Gnome (or GTK) even in KDE. so wouldn't removing all Gnome mess them up.

---

### Post by xboxbman on 2011-11-22
> **mastablasta said:**
> see here on how to remove and get pure KDE (kubuntu): [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
 
As iknow some porgrammes use Gnome (or GTK) even in KDE. so wouldn't removing all Gnome mess them up.

I've been trying to follow the instructions in that link, but it does not seem to find some of the files in the repos.  I've tried a number of different sources, but to no avail.

---

### Post by lolpenguin on 2011-11-23
Is your oneiric/main source active? If so run```
sudo apt-get update
```

---

