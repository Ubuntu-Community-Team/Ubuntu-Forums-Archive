---
title: "[SOLVED] Unable to open usb disk in live cd"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by unknown user on 2008-12-02
[FONT="Tahoma"]I am running from the live disk (Live Session User) and I have created a new user (Unknown) as that way I can log in and access all my old files (home/unknown). My plan was to copy the home folder, re-install ubuntu 8.10 and then drop my old (unknown) folder in the new system.

However, when I log in as unknown, I am unable to access any of the usb pens and can not copy my home folder. Does anyone know how I could allow access to the usb drives so I can copy my home folder onto a safe drive so I can re-install my system?[/FONT]

---

### Post by Kinetic777 on 2008-12-02
Sometime in linux, if a usb memory card is formated under a different user account, other users will not be able to write to it. This is because you need thew privileges to access it. If there is no data on the usb device, you can easily just re-format it, that will switch the privileges to you. Alternatively, in terminal if im correct you can type **gksudo nautilus "pathtodevice**"

---

### Post by unknown user on 2008-12-03
[FONT="Tahoma"]Thanks for this. I cleared of all my data on the flash pen and was ready to format, then I rebooted the system and set up the second account again. This time when I put the flash pen in I was asked to enter the password for the account and then after putting it in I could access it all OK.[/FONT]

---

