---
title: "Ubuntu 13.10 installation aborted at the end"
date: 2013-12-17
forum: New to Ubuntu
---

### Post by to_agrawals on 2013-12-17
Hi all,
   I am a beginner on Ubuntu, trying to install on virtualbox created on Windows 8.1. machine. I am able to get through all the installation steps, thanks to extensive help available online. However, at the end, when I click on the RESTART NOW button, it just aborts and says 'Oracle VM virtualbox manager has stopped working. I have tried to get all the issues, log details and VM screenshot in an attachment, please help...!!

Thanks
Saurabh

---

### Post by jones quest on 2013-12-18
A few tips that might help.

First remove the cd image from virtualbox settings: 
Storage --> Controller: IDE, CD/DVD Drive: Remove disk from virtual drive
This way the virtualbox will actually try to boot from the finished installation.

Second, increase the amount of Video Memory. 12MB it really not enough for unity. Display: Video memory set to 128MB.

In fact you'll get a pretty bad experience of ubuntu (with unity) in a virtualbox without hardware acceleration. So that's step three.
In video settings, tick Features: Enable 3D Acceleration. The follow this guide: [http://www.typicaltips.com/2013/02/ubuntu-lags-in-virtualbox-solution.html](http://www.typicaltips.com/2013/02/ubuntu-lags-in-virtualbox-solution.html)

3D acceleration with virtualbox doesn't work with all video cards (virtualbox will abort with an error). In which case your better of trying ubuntu with another desktop environment. Disable 3D acceleration in virtualbox settings and install a lightweight desktop environment (like xfce) or install another flavor of ubuntu (xubuntu = xfce+ubuntu).

---

