---
title: "Transfer user accounts from one distro to other."
date: 2008-09-11
forum: New to Ubuntu
---

### Post by zwygart on 2008-09-11
Hi everybody,

I am running 6.10 on my desktop and XP. Logically I want to upgrade to 8.04. Is this possible to do dist-upgrade from a iso on the USB key? (I don't have Internet on this computer). If I have to make a fresh install, is there a way to copy all the user accounts (8) from the old to the fresh install? Please tell me how I don't want to make all the setup again. Is there a way to transfer the programs? I think I have to reinstall them.

For the user account /home it will be easy I think, but for the passwords and desktop configuration I don't know how.

Thanks for any answer.

N.B: How to connect a printer? It works on XP, but on ubuntu I don't know which program I have to install or where I have to set it. 

The first question is more important at the moment. The second I will do some research later.

---

### Post by dioltas on 2008-09-11
To transfer your user accounts there are some files that you need to copy from your new system.
The whole /home/ directory should be copied as this contains the user's personal application settings and all their personal files.

The passwd file contains user account information. The shadow file contains all user's encrypted passwords. The group file contains information about what groups user's belong. Therefore it is nessecary to copy all these as well. They are all in /etc/

So the files you need to copy to the new system are:

/home/ (entire directory)
/etc/passwd
/etc/shadow
/etc/group

If you copy those files, all your user accounts and user settings should be intact.
[[COLOR="Blue"]Here's a guide to doing it.[/COLOR]]("http://www.cyberciti.biz/faq/howto-move-migrate-user-accounts-old-to-new-server/")

---

### Post by dioltas on 2008-09-11
Also an easy way to backup all your installed applications is to use dpkg to get a list of all installed programs. Then on your new system you can import the list and automatically install them. You'll need to connect the other computer to the internet for this bit though.
[[COLOR="Blue"]Here's another guide for that [/COLOR]]("http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html"), just follow the instructions for debian.

Just re-read your post. CUPS is what controls printers in linux usually. It should be installed by default along with a load of drivers.

To go to the CUPS setup page, go here:  [[COLOR="Blue"]http://127.0.0.1:631[/COLOR]]("http://127.0.0.1:631"). Click add printer and follow the steps. Type whatever name, location, and description you want. And select the model of your printer as the driver. Then your done and hopefully it'll work! I've had trouble with printers in the past myself :)


Having said all that, I'm fairly sure you should be able to install the ubuntu upgrade over the 6.10 system without losing your data. I havn't done it before myself so I cant say for definite. I'd say backup those files anyway just in case!

---

