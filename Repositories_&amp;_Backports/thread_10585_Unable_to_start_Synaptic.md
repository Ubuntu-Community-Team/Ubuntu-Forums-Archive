---
title: "Unable to start Synaptic"
date: 2005-01-09
forum: Repositories &amp; Backports
---

### Post by Loonux on 2005-01-09
Whenever i select the synaptic package manager from the menu at the top i am prompted for my root password, which i enter, then get the following error:

Failed to run /usr/sbin/synaptic as user root:
 Child terminated with 1 status

im new to ubuntu so dont really know what to do to sort this. any help appreciated.

thanks

---

### Post by tiiim on 2005-01-09
[QUOTE=Loonux]Whenever i select the synaptic package manager from the menu at the top i am prompted for my root password, which i enter, then get the following error:

Failed to run /usr/sbin/synaptic as user root:
 Child terminated with 1 status

im new to ubuntu so dont really know what to do to sort this. any help appreciated.

thanks[/QUOTE]
 did create the password in installation?

If not you can run:

sudo apt-get install [package] 

in a terminal

or you can open a root terminal up and change your password

passwd [username] (i think)

Your root password should be your password which you made in the installation program.

Not worry in mean time to update your computer

sudo apt-get update
sudo apt-get upgrade


if you ask for password and it still does not work do that then root terminal. but let us know did you create the password in installation.

---

### Post by Suzan on 2005-01-09
What password did you use? You have to enter your USER-password, not your root-password (if you have set one).

---

### Post by danip on 2005-01-11
yes your user password

---

