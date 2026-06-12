---
title: "Problem to start GUI"
date: 2011-09-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by zaurus on 2011-09-13
Hello

I upgraded from 10.10 throu 11.04 to 11.10.
Boot process stops at "checking Power states"
I can switch to another screen and login to the command line.
Starting X as normal user gives a lot of errors.
Starting X as a root bring ups some GUI and propopse to restart session to save changes. After restarting I am again on command line.

Does anybody know where should I start to solve this issue?

KR

---

### Post by tista on 2011-09-13
> **zaurus said:**
> Hello

I upgraded from 10.10 throu 11.04 to 11.10.
Boot process stops at "checking Power states"
I can switch to another screen and login to the command line.
Starting X as normal user gives a lot of errors.
Starting X as a root bring ups some GUI and propopse to restart session to save changes. After restarting I am again on command line.

Does anybody know where should I start to solve this issue?

KR

Hi zaurus. ;)

OK... I'm afraid that you had not complete the installation process on oneiric, yeah sometimes oneiric couldn't resolve that "half-baked" upgrading...

so you log in VT, run "sudo apt-get update" and then "sudo apt-get upgrade".

please give it a try! :P

cheers.

---

### Post by zaurus on 2011-09-17
Thanks for help but it did not help.

---

### Post by dino99 on 2011-09-17
which graphic driver is installed ?

---

### Post by garvinrick4 on 2011-09-17
> I upgraded from 10.10 throu 11.04 to 11.10.
Boot process stops at "checking Power states"You most likely have both gdm and lightdm installed oneiric uses lightdm now.
ctrl/alt/F1
log in
sudo dpkg-reconfigure lightdm
Use tab and arrows to toggle with and choose lightdm
sudo stop gdm
sudo start lightdm
or 
sudo /etc/init.d/lightdm restart

#Might have to reboot after dpkg-reconfigure lightdm (I cannot quite remember it was a few months back)


## Used gdm thru 11.04.

---

