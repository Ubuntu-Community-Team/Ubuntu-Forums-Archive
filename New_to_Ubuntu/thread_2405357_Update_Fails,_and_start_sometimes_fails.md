---
title: "Update Fails, and start sometimes fails"
date: 2018-11-04
forum: New to Ubuntu
---

### Post by cybervigilante on 2018-11-04
When I try to run an update I get this message " The repository 'http://download.opensuse.org/repositories/home:/selmf/xUbuntu_17.10  Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default."

How do I fix this or doesn't it matter? Is xUbunutu different from Ubuntu?

The reason I wanted to upgrade then dist-upgrade is I sometimes get an error message that ubuntu 18.04 didn't start properly but it disappears when I click "details." How can I see the error so I can post it here?

---

### Post by Autodave on 2018-11-06
Ubuntu, Xubuntu, Lubuntu and many others all run the same kernel, so the only real differences are the desktops that each use. Ubuntu is the heaviest (uses the most resources) of those three, Lubuntu is the lightest. Xubuntu falls in the middle and is what I use on all of my machines (9 of them).

I have found that upgrades from one release to the next release very often do not go well. Or don't go at all.  I always do a clean install and only use the LTS releases.  17.10 is no longer supported and that may be the reason for your current problem.  I would suggest that you download a 18.04 release and install it.  PLEASE make sure that you backup everything to an external source first!

---

### Post by mehrdadsami on 2018-11-06
about the first error you received "is not signed " .. this problem is for this reason that you should first add gpg key from opensuse to your machine and then update repository . 
About the second problem i have to say that every distro such as ubuntu , xubutu or lubuntu just can update to top version of itself ... and also is better you install LTS version such as 18.04 ... i suggest you remove the your linux and clean install LTS version of ubuntu or xubuntu or lubuntu , whatever you like ..

---

