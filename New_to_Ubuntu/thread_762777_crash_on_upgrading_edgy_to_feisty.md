---
title: "crash on upgrading edgy to feisty"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by weemikey on 2008-04-22
A while back I upgraded Dapper to Edgy with no problems so yesterday decided to upgrade to Feisty.
Edited  /etc/apt/sources.list and changed 'edgy' to 'feisty'.
Updated source list:
*sudo apt-get update*
Upgraded:
*sudo apt-get dist-upgrade*
Several hours later:
[I]sudo apt-get -f install
sudo dpkg --configure -a[/I]

At this point I rebooted and got this:

[I]Busy Box v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
/bin/sh: can't access tty; job control turned off
(initramfs)_ [/I] (blinking underscore)


As I am relatively unaware of linux commands I was reluctant to mess around with any of them.
HELP!
What do I do now?  All reasonable suggestions accepted.
I have a Dell Dimension (4 years old) with 40Gb HDD.
Should I just suck all my data off the HDD and start from scratch?  Sounds rather primitive.
Mikey

---

### Post by ace007 on 2008-04-22
EDIT: I realized the problem is a little deeper than what I anticipated.  My suggestion was useless.

I did find numerous sources that say the way you upgraded was not reccomended and required a lot of debugging to get it fixed again.  You are always better off using the upgrade button from the update manager.  

read the comments near the bottom of this page ...
[http://onlyubuntu.blogspot.com/2007/03/upgrade-ubuntu-610-edgy-eft-to-ubuntu.html](http://onlyubuntu.blogspot.com/2007/03/upgrade-ubuntu-610-edgy-eft-to-ubuntu.html)

---

### Post by hums07 on 2008-04-22
Had you waited some days, you would ve been able to upgrade from Dapper to Hardy. If I were you, I would save my data and do a clean install. Sorry if this does not help.

@ace007
It is not an "official" way but it works.

---

