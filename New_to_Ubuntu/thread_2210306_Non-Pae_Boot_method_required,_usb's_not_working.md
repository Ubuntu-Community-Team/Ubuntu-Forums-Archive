---
title: "Non-Pae Boot method required, usb's not working"
date: 2014-03-10
forum: New to Ubuntu
---

### Post by sun7 on 2014-03-10
Hi

I need to install xubuntu 13.10 onto my laptop. Pae required error comes up. Edited boot config of iso and placed it onto a pen drive. Now all usb ports are not functioning. Any ideas on how to install 13.10 without having to download 12.04 non pae version?

Sun7

---

### Post by sudodus on 2014-03-10
Welcome to the Ubuntu Forums,

There is the One Button Installer, which can install Xubuntu in computers with Pentium M and Celeron M CPUs without a PAE flag. But it requires USB or eSATA (not CD/DVD). I am working with a new installer (via CD) and there is a Lubuntu 13.10 installation available, but no Xubuntu.

There is also the possibility to get the daily build of the next version, 14.04 LTS. It has a boot option, **forcepae**, to override that problem. So you can try that version, but beware, it is not released yet, and may break several times before the release in April.

-o-

So there are alternatives. (The easiest one would be via USB.) Since you are a newcomer, I don't want to suggest experimental methods, that might be scary. Maybe the best alternative is to wait until the release of Xubuntu 14.04 LTS in April.

If you are willing to take the hard disk out of the computer and connect it to another computer, it will be possible to install the current Xubuntu without big problems, and then put it back into the laptop without PAE flag.

-o-

Finally, if you would be satisfied with *the current long time support version of Xubuntu, version 12.04 LTS*, you can get it with a non-pae kernel, install it and run it without problems. And when 14.04 LTS arrives, you can upgrade directly from 12.04 to 14.04. Or some other flavour or re-spin of Ubuntu 12.04 with long time support ...

---

### Post by sun7 on 2014-03-10
Hi Sudodus

Thanks for the welcoming and the succinct info. My colleague and I have been working on this issue for 3 days straight, and he is quite versed with Linux and is a competent programmer and IT technician, so by all means, please suggest the experimental methods as they would be welcomed gladly. 

Sun7

---

### Post by sudodus on 2014-03-10
Do you want the version under development Trusty Tahr, to become Xubuntu 14.04 LTS? Download it via the testing tracker

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds)

Or do you want Xubuntu 13.10? Learn to use the One Button Installer and use it to install Xubuntu 13.10 from a tarball.

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

[http://ubuntuforums.org/showthread.php?t=2172971](http://ubuntuforums.org/showthread.php?t=2172971)

and ask for help here at the Ubuntu Forums until you succeed!

Good luck :-)

---

