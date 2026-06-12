---
title: "upgrade question"
date: 2015-10-19
forum: New to Ubuntu
---

### Post by rburkartjo on 2015-10-19
running 14.04 and want to upgrade to 15.04 then 15.10-when comes out. 14.10 is at end of life so can i still upgrade to 14.10 the 15.04 without problems/tks

---

### Post by rburkartjo on 2015-10-19
spm wont let me do. update manager just shows 15.04 and wont let me upgrade

---

### Post by rburkartjo on 2015-10-19
get this output
do apt-get upgrade && sudo apt-get dist-upgrade
  248  sudo update-manager -d
  249  history
  250  sudo apt-get upgrade && sudo apt-get dist-upgrade
  251  sudo update-manager -d
  252  sudo -i
  253  history
ray@nightmare:~$ sudo -i
[sudo] password for ray: 
root@nightmare:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@nightmare:~# update-manager -d
Checking for a new Ubuntu release
WARNING:root:file 'utopic.tar.gz.gpg' missing
                  248  sudo update-manager -d            
  249  history
  250  sudo apt-get upgrade && sudo apt-get dist-upgrade
  251  sudo update-manager -d
  252  sudo -i
  253  history
ray@nightmare:~$ sudo -i
[sudo] password for ray: 
root@nightmare:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@nightmare:~# update-manager -d
Checking for a new Ubuntu release
WARNING:root:file 'utopic.tar.gz.gpg' missing

---

### Post by rburkartjo on 2015-10-19
[sudo] password for ray: 
root@nightmare:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@nightmare:~# update-manager -d
Checking for a new Ubuntu release
WARNING:root:file 'utopic.tar.gz.gpg' missing

---

### Post by grahammechanical on 2015-10-19
End of life means more than not receiving security fixes. It also means that the repositories are first closed and then archived and moved to another location. The URLs of the repositories are no longer accurate.

It is technically possible to upgrade to 14.10 and then immediately upgrade to 15.04. You will need to edit the URLs in the sources.list file. But first I would advise reverting to an open source video driver and reverting the OS to a default state as far as possible.

This wiki page explains End of Life upgrades.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Regards

---

### Post by Geoffrey_Arndt on 2015-10-19
You're making this complicated.   Just download the latest beta (Ubuntu Wily Werewolf 15.10).    Burn it to DVD or USB Flash-stick media.    Install it from the media to overlay (replace) you current 14.04 version (after securing/obtaining all your important data).    Then, when the next LTS comes out in April (16.04), you can do the online upgrade and it will work if you have only the standard repos enabled, and haven't radically customized Wily.

---

### Post by rburkartjo on 2015-10-21
tks had to do this. change software sources to default then upgrade. note there is no 14.10 so just went directly to 15.04.

---

### Post by gonzalo-vc on 2015-10-23
Question: to upgrade things inside Ubuntu without jumping to the next version cause wanting to stay with LTS, we use only apt-get update && upgrade.
Can we use dist-upgrade to upgrade "more things" like kernel and Libreoffice, for instance? Or does dist-upgrade always make the version jump forward?
Thanks!

---

### Post by mcduck on 2015-10-25
*apt-get dist-upgrade* doesn't jump to next version. It's just a slightly more powerful version of normal *apt-get upgrade*. *upgrade* can only replace an existing installed package with a new version, while *dist-upgrade* can add new packages or remove existing ones if the upgrade requires that. 

So, *dist-upgrade* won't give you any different versions of software compared to *upgrade*, it's still pulling things from the same repositories.

The command to actually update to next release version is *do-release-upgrade* (although manually editing your sources.lst to point to new version's repositories and then running a dist-upgrade would also get you to next release version. But the *do-release-upgrade* command does some checks, disables PPA repositories and other things to make sure the upgrade goes smoothly.

---

