---
title: "not all updates can be installed"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by al.adab on 2013-03-09
hello,

i'm getting the following message from Update Manager:

[I]Not all Updates can be installed
Run a partial upgrade, to install as many updates as possible.

This can be caused by:
* A previous upgrade which didn't complete
* Problems with some of the installed software
* Inofficial software packages not provided by Ubuntu
* Normal changes of a pre-release version of Ubuntu[/I]

Tried to apply some of the solutions given at [http://ubuntuforums.org/archive/index.php/t-1550455.html](http://ubuntuforums.org/archive/index.php/t-1550455.html) but none worked. 

Do I need to rectify this or should I just ignore it? thanks

---

### Post by sudodus on 2013-03-09
Which version of Xubuntu are you running (12.04 LTS or 12.10 or ...)?

Which command(s) or program did you use to perform the update/upgrade?

Do you have any Personal Package Archive (*PPA*)?

---

### Post by al.adab on 2013-03-09
thanks sudodus. Here it goes: 

*Which version of Xubuntu are you running (12.04 LTS or 12.10 or ...)?*: 12.04 Precise

*Which command(s) or program did you use to perform the update/upgrade?*: i usually use sudo apt-get upgrade unless I'm prompted to update (orange icon on taskbar). I think the last time I upgraded I used the latter, though I'm not entirely sure, sorry. 

*Do you have any Personal Package Archive (PPA)?*: plz see screenshot in attachment.

---

### Post by sudodus on 2013-03-09
> **al.adab said:**
> thanks sudodus. Here it goes: 

*Which version of Xubuntu are you running (12.04 LTS or 12.10 or ...)?*: 12.04 Precise

*Which command(s) or program did you use to perform the update/upgrade?*: i usually use sudo apt-get upgrade unless I'm prompted to update (orange icon on taskbar). I think the last time I upgraded I used the latter, though I'm not entirely sure, sorry. 

*Do you have any Personal Package Archive (PPA)?*: plz see screenshot in attachment.

Precise should be quite stable now. I'm using it without problems, but I have only a couple of PPAs. I suggest that you try the commands in the following list, originally posted by *oldfred*. Use sudo for all the commands.

```
# This will reinstall if not current. (from my chroot procedure which does not have sudo on every line,
# so use the sudo -i first).
 
#if not chroot use: sudo -i

#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean

#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a

```

---

### Post by al.adab on 2013-03-09
thanks! I think *apt-get dist-upgrade* did the trick :)

---

