---
title: "gksudo nautilus problem"
date: 2014-09-28
forum: New to Ubuntu
---

### Post by czgirb on 2014-09-28
As title ...
```
czgirb@czgirb-Compaq-Presario-CQ40-Notebook-PC:~$ gksudo nautilus
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:2703): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.config/user-dirs.dirs


(nautilus:2703): GLib-CRITICAL **: Source ID 168 was not found when attempting to remove it

(nautilus:2703): GLib-CRITICAL **: Source ID 169 was not found when attempting to remove it

(nautilus:2703): GLib-CRITICAL **: Source ID 170 was not found when attempting to remove it
czgirb@czgirb-Compaq-Presario-CQ40-Notebook-PC:~$ 
```

How to solve it?

---

### Post by Frogs Hair on 2014-09-28
Try the following because the gksu package is no longer a default package, so make sure it is installed . Some applications use gksu as a dependency ```
sudo apt-get install gksu 
```

---

### Post by czgirb on 2014-09-28
> **Frogs Hair said:**
> Try the following because the gksu package is no longer a default package, so make sure it is installed . Some applications use gksu as a dependency ```
sudo apt-get install gksu 
```
As required
```
czgirb@ubuntu:~$ sudo apt-get install gksu
[sudo] password for czgirb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gksu is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
czgirb@ubuntu:~$ 

```

---

### Post by czgirb on 2014-09-28
Just tried ...
```
czgirb@ubuntu:~$ gksu nautilus
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
(nautilus:5970): GLib-CRITICAL **: Source ID 98 was not found when attempting to remove it
(nautilus:5970): GLib-CRITICAL **: Source ID 99 was not found when attempting to remove it
(nautilus:5970): GLib-CRITICAL **: Source ID 100 was not found when attempting to remove it


czgirb@ubuntu:~$ gksudo nautilus
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
** (nautilus:6079): WARNING **: Hit unhandled case g-io-error-quark:26 in nautilus_report_error_renaming_file
** (nautilus:6079): WARNING **: Hit unhandled case g-io-error-quark:26 in nautilus_report_error_renaming_file
(nautilus:6079): GLib-CRITICAL **: Source ID 105 was not found when attempting to remove it
(nautilus:6079): GLib-CRITICAL **: Source ID 107 was not found when attempting to remove it


czgirb@ubuntu:~$ sudo -H nautilus
[sudo] password for czgirb: 
(nautilus:6192): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
(nautilus:6192): GLib-CRITICAL **: Source ID 98 was not found when attempting to remove it
(nautilus:6192): GLib-CRITICAL **: Source ID 99 was not found when attempting to remove it
(nautilus:6192): GLib-CRITICAL **: Source ID 100 was not found when attempting to remove it


czgirb@ubuntu:~$ sudo -i nautilus
(nautilus:6204): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
(nautilus:6204): GLib-CRITICAL **: Source ID 98 was not found when attempting to remove it
(nautilus:6204): GLib-CRITICAL **: Source ID 99 was not found when attempting to remove it
(nautilus:6204): GLib-CRITICAL **: Source ID 100 was not found when attempting to remove it
czgirb@ubuntu:~$ 

```

---

### Post by Frogs Hair on 2014-09-28
Two alternatives gksu or gksudo are included in this post reporting the same error, but it is from 13..04.I haven't seen this error on any installation so far.
[http://askubuntu.com/questions/331938/sudo-nautilus-command-is-not-working-properly-in-ubuntu-13-04](http://askubuntu.com/questions/331938/sudo-nautilus-command-is-not-working-properly-in-ubuntu-13-04)

```
sudo -H nautilus
``````
sudo -i nautilus
```

---

### Post by czgirb on 2014-09-28
Tried already, Sir ...

---

### Post by mc4man on 2014-09-28
Well you could simply - 
alt+F2
gksudo nautilus

For the most part those warnings can be ignored. The 1st. one is from nautilus-share package being installed & sharing not set up 
The rest don't mean too much
(- for some reason here it's clean when I do, whether it's from some mods I've made to 14.04 or happenstance don't know. I generally use alt+F2 anyway
Ex.
> doug@doug-Y510P:~$ gksudo nautilus
Initializing nautilus-dropbox 1.6.2
Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension
doug@doug-Y510P:~$
And on another 14.04 install
> ~$ gksudo nautilus
Initializing nautilus-open-terminal extension
doug@doug-Y510P:~$ 

---

### Post by czgirb on 2014-09-28
OK ... thank you **mc4man**!

---

