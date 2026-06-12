---
title: "[SOLVED] how do i grant user rights?"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by versemelk on 2008-05-27
hi,

i run a linux dual-boot on a MBP 2nd gen. in order to get my wifi working i had to install the mad wifi drivers. so far so good. to work out a little bug i need to change a line in a certain file (> Finally, the MadWifi driver will prevent you from resuming after suspend-to-ram. To fix this, edit /etc/default/acpi-support and add the ath_pci driver to the MODULES variable, like so:

# ...
MODULES="ath_pci"

# ...


a-ok, but when i try to save it says i don't have the permissions necessary to save the file. any help? have searched on a few keywords but it's a little vague to me.

thanks.

---

### Post by drs305 on 2008-05-27
> **versemelk said:**
> hi,

i run a linux dual-boot on a MBP 2nd gen. in order to get my wifi working i had to install the mad wifi drivers. so far so good. to work out a little bug i need to change a line in a certain file (

a-ok, but when i try to save it says i don't have the permissions necessary to save the file. any help? have searched on a few keywords but it's a little vague to me.

thanks.

Open the file with the following command:
```
gksudo gedit /etc/default/acpi-support
```
The file is owned by root so you must temporarily assume root privileges to modify it.

Added: it is a good idea to back up any of these files first. You can do so with:
```
sudo cp /etc/default/acpi-support /etc/default/acpi-support.bak
```

---

### Post by issih on 2008-05-27
Essentially you (the user) do not own the file you are trying to modify. Consequently you are not allowed to modify it. You can look at it, but not save any changes you try and make.

In order to change things, you need to be someone else, someone with the authority to make these kind of (potentially dangerous) changes. You need to be a super user (root user).

In ubuntu you achieve this with the sudo command (sudo stands for "super user do" or something like that). Any command that complains about permissions probably needs sudo putting before it.

In your case, assuming you opened gedit (Text Editor) to manipulate the file in question, you instead want to launch gedit as the root user.

To do this open a terminal then type "gksudo gedit"

the gksudo is a separate command better suited for launching gui based apps, sudo on its own is intended for console applications.

You will be asked for your password (which is simply your login password) and then gedit will open. Now simply make the changes as before, but this time, as you are impersonating a super user (and therefore claiming you know what you are doing :)) you will be able to save the changes.

Hope that helps.

---

### Post by versemelk on 2008-05-27
thanks! both of you!

problem solved! i'll read up on some terminal tutorials ;) might come in handy!

---

