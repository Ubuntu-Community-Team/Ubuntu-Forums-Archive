---
title: "ubuntu Lubuntu problem"
date: 2013-10-10
forum: New to Ubuntu
---

### Post by The Frenchman on 2013-10-10
I've been happily using Ubuntu 12.04LTS for about a year.After not using my netbook for several weeks I logged on and started an update.after it finished problems started to develop.I lost dash on my own account (although it was still present in the guest account)then more problems popped up I lost several keys (that included several used in passwords) I had to use the on-screen keyboard to log on.I was given some advice on the forum and opened a terminal and ran unity but this only restored limited use of desktop that promptly reverted to the non working mode. The lost keys would work now and again but normally went missing after 10 minutes or so.I got a friend to mail me a copy of Lubuntu which went well for 10 minutes then I started losing keys again.Could there be a virus involved?

---

### Post by david98 on 2013-10-10
This will not solve your problem. But could you not back up all your personal data. [COLOR=#333333][FONT=UbuntuRegular] I would recommend a complete reinstallation, because getting to the bottom of your problems is quite hard to accomplish.[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]To make things not too hard you can remember all the packages you installed via apt/dpkg by using
$ dpkg --get-selections "*" > package.list
then save that file somewhere save, reinstall, and restore the package selection.
$ sudo dpkg --set-selections < package.list
$ sudo apt-get -u dselect-upgrade
The restore your the data you backuped before and you should be good to go.


[/FONT][/COLOR]

---

### Post by The Frenchman on 2013-10-11
Thats seems a good idea.....except.Because the keys I have lost form part of my password I can't authenticate with the administrator's password any changes updates/ upgrades.Is there a  terminal command I can run that will get rid of the need for passwords until I get rid of this problem.I did run Clam last night and found 7 threats (a couple of worms) I've quarantined/ deleted them but after reboot I still have the same problems

---

