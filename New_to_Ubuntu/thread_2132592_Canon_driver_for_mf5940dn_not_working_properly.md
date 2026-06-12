---
title: "Canon driver for mf5940dn not working properly"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by jordiland on 2013-04-05
Hi, I have a network of 3 computers in Ubuntu 12.04 64-bit and a PC with Windows. My new printer is Canon MF5940DN. Canon Europe offers a variety of drivers based on the CQUE for this printer in Linux but I have several problems:
- in general printing is possible for example from openoffice but not possible from firefox or pdf, etc.
- not any computer is able to scan.
- the installation guide of cque says that when you double click or even if you run the ./setup from the terminal a tuturial should open, but it has never happened. Normally I have had to find the ppd and paste it in the ppd's directory.

I've called the canon costumer department and guess what they've said: "ubuntu is suposed to be oriented to people expert in informatics, so there's no sense we give support in this cases so we are no trained for that, I'm sorry, YOU SHOULD BETTER CONTACT TO UBUNTU COSTUMER DEPARTMENT ...."  !!! :)

i've setup the different DEB drivers, this one for example:
[http://www.canon-europe.com/Support/Consumer_Products/products/Fax__Multifunctionals/Laser/LaserBase_MF_series/i-SENSYS_MF5940dn.aspx?DLtcmuri=tcm:13-1003199&page=1&type=download](http://www.canon-europe.com/Support/Consumer_Products/products/Fax__Multifunctionals/Laser/LaserBase_MF_series/i-SENSYS_MF5940dn.aspx?DLtcmuri=tcm:13-1003199&page=1&type=download)

Can any one help me?
thank you.

---

### Post by pdc on 2013-04-05
so you have issues:

1) printing is possible for example from openoffice but not possible from firefox or pdf, etc.
2) not any computer is able to scan.
3) a tuturial should open, but it has never happened

1) so from here 

[http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/Laser/LaserBase_MF_series/i-SENSYS_MF5940dn.aspx?type=download&page=1](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/Laser/LaserBase_MF_series/i-SENSYS_MF5940dn.aspx?type=download&page=1)

one finds a 64bit debian package from Canon for the CQE driver; I note it is packaged as a .deb package so I assume it was can be/was installed by gdebi installer so the 

> [COLOR="#FF0000"]sudo dpkg -l | grep cqe[/COLOR] ......should hopefully show a CQE driver installed?

.........there is a CQE thumbnail 

2) from  here [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)

it is likely that sane should recognise the scanner: if we test with several command

> sane-find-scanner
> scanimage -L

if you can post back what you get please

it often seems a "permissions" issue

[https://help.ubuntu.com/community/ScanningHowTo#A.22No_device_available.22_-_what_to_do.3F](https://help.ubuntu.com/community/ScanningHowTo#A.22No_device_available.22_-_what_to_do.3F)

and 

[http://www.tuxradar.com/answers/412](http://www.tuxradar.com/answers/412)

3) [http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/Laser/LaserBase_MF_series/i-SENSYS_MF5940dn.aspx?type=download&page=1](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/Laser/LaserBase_MF_series/i-SENSYS_MF5940dn.aspx?type=download&page=1)

there are several guides here; aimed mainly at windows and mac but there are network advice guides if one needs that

---

