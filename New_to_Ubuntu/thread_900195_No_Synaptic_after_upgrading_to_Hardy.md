---
title: "No Synaptic after upgrading to Hardy"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by fliegenderrobert on 2008-08-25
Hi Ubuntu Forum,
I'm new in the forum and have encountered som problems with the last update to 8.04.01 from friday 22nd Aug 2008 which might be of interest for you as well.
After having run the laste update my synaptic is completely gone.
As soon as I try to start "sudo synaptic" I get the attached message window.

The complete folder in root /synaptic has been gone.

An uninstall synaptic and install synaptic does not help. Still the same.

Trying to edit the sources.list comes up with the following message,
---
helmut@addy:/etc/apt$ sudo gedit sources.list

(gedit:7289): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: No such file or directory
Benutzerspezifisches GNOME-Konfigurationsverzeichnis »/root/.gnome2/« konnte nicht angelegt werden: No such file or directory
helmut@addy:/etc/apt$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy
helmut@addy:/etc/apt$ sudo dpkg-reconfigure synaptic
helmut@addy:/etc/apt$ sudo dpkg-reconfigure update-manager
/usr/sbin/dpkg-reconfigure: update-manager ist kaputt oder nicht komplett installiert
---
Has anyone ot you an idea what had happened and what I can do to resolve the problem?

I even thought of re-installing the system but I have now idea how to install it over the existing one.

Maybe I've choosen the wrong category. If it is so please redirect me as appropriate.

I appreciate your help and assistance. Thank you very much.

fligenderrobert

---

### Post by gn2 on 2008-08-25
Have you tried opening a terminal and immediately typing: ```
sudo apt-get install synaptic
```

---

### Post by fliegenderrobert on 2008-08-25
Hi gn2
Yes I have tried this command. The terminal reply is that nothing is installed because synaptic is up to date.
Nothing has changed.

Brgds

---

### Post by halitech on 2008-08-25
if you go to System - Administration - Synaptic Package manager, is it there and if so, does it run?

---

### Post by fliegenderrobert on 2008-08-25
Hi Halitech,
Yes it is there. I'm asked for the password and then the error message which I have attached to my original post appears.
Brgds

---

### Post by halitech on 2008-08-25
try this in the terminal
```
sudo mkdir /root/.synaptic
```

---

### Post by fliegenderrobert on 2008-08-25
@halitech
this is the terminals output
---
helmut@addy:~$ sudo mkdir /root/.synaptic
[sudo] password for helmut: 
mkdir: kann Verzeichnis &#8222;/root/.synaptic&#8220; nicht anlegen: No such file or directory
---
I think it is because root is not recognised?
Brgds

---

### Post by halitech on 2008-08-25
stranger and stranger

okay, open Nautilus and browse to the file system and see if the root folder even exists

---

### Post by fliegenderrobert on 2008-08-25
There is no root folder. I tried the following in a terminal
---
helmut@addy:/$ sudo ls -a /root
ls: Zugriff auf /root nicht möglich: No such file or directory
---

---

### Post by halitech on 2008-08-25
ouch, thats not good at all :(

I'm not sure but we might be looking at a reinstall here. :(  do  you have a usb flash drive or a cd burner so you can back up your important data?

---

### Post by fliegenderrobert on 2008-08-25
I have a clean installation of my son Samsung X20 laptop and had a quick look.
I could find the root folder there. Now I used sudo mkdir root and sudo mkdir /root/.synaptic and it worked. I can open synaptic now.
Because it was started from the terminal I could see an output message
---
helmut@addy:/$ sudo synaptic

(synaptic:6300): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed
---
Besides that in the laptops root folder are some more files like
.bashrc, .gconfd, .gnome2_private, .rnd, .wapi, .gconf, .gnome2 and .profile

Do you think it is wise to copy and paste them into my system or shall I just try an uninstall of Synaptic by itself and then again an install?

It looks like that gnome desktop itself is missing some setting files or even directories. I have no idea how to solve that.

---

### Post by halitech on 2008-08-25
I'll be honest I'm not sure. Might work or might not but worth a shot. I'm trying to remember if there is a repair option when booting from the cd that might let us save the install without having to reinstall...

---

### Post by fliegenderrobert on 2008-08-25
After searching for gconf in synaptic I re-installed gconf and now are the following folders back in root again
.gconfd, .gnome2_private, .gconf, .gnome2 and .synaptic

The .profile contains setting related to bashrc. So I will try an re-install of the shell as well and see what will happen.

---

### Post by fliegenderrobert on 2008-08-25
I could cp .bashrc and .profile. .wapi was admitted. Obviously it is a directory and needs another command which I have to lookup first.

---

