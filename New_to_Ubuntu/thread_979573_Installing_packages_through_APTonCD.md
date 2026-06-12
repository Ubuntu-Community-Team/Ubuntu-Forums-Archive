---
title: "Installing packages through APTonCD"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by bilol on 2008-11-12
Hi friends,
I am very new to Ubuntu. I have two machines say ‘X’, and ‘Y’ in two different places. In both X and Y ,I installed Ubuntu 8.04. The X is connected to internet but Y is not. I installed so many packages in X using apt-get through internet connection.
 Is it possible to install and run all those packages(stored in X) in  Y with the help of [apt-on-cd]("http://aptoncd.sourceforge.net/") feature of ubuntu?
Please clarify.
Thanks in advance…..

---

### Post by XxX_VLAD_XxX on 2008-11-12
I have the same problem, plus the computer with no connection has a ATI Saphire X1550  with 512 MB  and I can't Download the drivers.

How can I create the aptOnCd

---

### Post by Skripka on 2008-11-12
I posted this once, and it got eaten by the forums.....

APTonCD is in Add/Remove programs, download it and use it--easy as that :)

---

### Post by jenkinbr on 2008-11-12
I have to use this program all the time.

On the online machine, run:
```
sudo apt-get install aptoncd
```
Then, run aptoncd and click on create CD/DVD
Provided you have not run ```
sudo apt-get clean
``` or a similar command, all the packages you have installed on the online computer should show up in white. Make sure that all of these are selected, and then click 'create'.
It will go through the process of creating the ISO file, and then you will be given the option of burning it to CD.

PS.  If aptoncd doesn't work for you, this wiki article may help:
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)
I use it once a week and it works like a charm, provided you save all the files in the correct locations.  To get the proper upgrade packages, I reccomend downloading repositories for *, *-updates, and *-security where '*' is your distribution codename, i.e. hardy, intrepid, etc.  This method works nicely alongside synaptics ability to generate download scripts for marked packages.

---

