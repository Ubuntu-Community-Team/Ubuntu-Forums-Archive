---
title: "Will there ever be a official snap/firefox fix issued?"
date: 2022-12-11
forum: New to Ubuntu
---

### Post by Butthead on 2022-12-11
Just nosey.  And the ACPI error deluge seen at bootup after upgrading to 22.04 Jammy?

Don't want to screw stuff up trying to fix things myself, and whats posted online usually doesn't work.

Thanks!

---

### Post by VMC on 2022-12-11
I'm not sure what your comments have to due with Firefox or Snap.
I remove run Firefox snap free without issue.

---

### Post by Butthead on 2022-12-12
I'd like to get firefox (snap or oherwise) to run after doing the 22.04 upgrade.

Since you sound like you know what you are doing, do you have any suggestions?

---

### Post by VMC on 2022-12-13
What happens when you run Firefox? If nothing or you know its not installed, then ```
sudo apt install firefox
``` shuld install it. Not sure your situation regarding Firefox. 
Here's what it should look like:
> $ sudo apt install firefox
[sudo] password for user 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  snapd
The following NEW packages will be installed:
  firefox snapd
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 23.8 MB of archives.
After this operation, 102 MB of additional disk space will be used.
Do you want to continue? [Y/n] 


---

### Post by Butthead on 2022-12-13
It gave me (apt install firefox) an error message, if I recall.   I have firefox installed, it just doesn't want to run.

Anyway, thanks for your assistance.  It appears to be working now that I installed the snapd store. :guitar:

---

### Post by grahammechanical on 2022-12-14
>  It appears to be working now that I installed the snapd store. 

Does anyone want an explanation? In Ubuntu 22.04 Firefox is a Snap packaged application. Remove snapd and snap applications will not work. For the record the deb packaged version of Firefox cannot be install by a simple apt command in 22.04. It has now become more complicated.

> If you run apt install firefox on Ubuntu 22.04 it will NOT  install a .deb version as before. Instead, Ubuntu includes a  transitionary package that (re)installs the Firefox Snap.

I got that quote from OMG! Ubuntu. The page also explains how to install the deb version of Firefox in 22.04. 

[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

Regards

---

### Post by Butthead on 2022-12-14
Thanks for all the good info! :cool:

---

### Post by AR_Kozz on 2023-01-13
That transition package has crossed a hard red line for me. 

Unbeknownst to the super user and without explicit permission, it diverts the package request to an entirely different system? 

Maybe there are other examples and I was slow to notice, but now that it has my attention, I think it's completely unacceptable. Tell the user it's not on apt, give them the command to get it from snap, that's all that should happen.

---

