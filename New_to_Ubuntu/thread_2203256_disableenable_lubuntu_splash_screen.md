---
title: "disable/enable lubuntu splash screen"
date: 2014-02-02
forum: New to Ubuntu
---

### Post by rburkartjo on 2014-02-02
what would be the command to disable the lubuntu splash screen. and again what would be the command to re-enable. i found this
command
sudo mv /etc/init/plymouth-splash.conf /etc/init/plymouth-splash.conf.disabled

however not sure this is what i want. might also want to enable it again.
tks

---

### Post by sudodus on 2014-02-03
Do you want a black screen or do you want a text screen showing what is happening during boot and shutdown, or something else?

---

### Post by rburkartjo on 2014-02-04
su think i have figured it out. please correct me if i am wrong.

if  i want a text mode in the splash screen all i have to is  change this item in the grub menu
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT=""

and if i want to change the splash screen i can use this command and change it to anything i have in the plymouth themes folder

sudo update-alternatives --config default.plymouth
[sudo] password for ray: 
There are 8 choices for the alternative default.plymouth (providing /lib/plymouth/themes/default.plymouth).

  Selection    Path                                                       Priority   Status
------------------------------------------------------------
  0            /lib/plymouth/themes/lubuntu-logo/lubuntu-logo.plymouth     150       auto mode
  1            /lib/plymouth/themes/fade-in/fade-in.plymouth               10        manual mode
  2            /lib/plymouth/themes/glow/glow.plymouth                     10        manual mode
  3            /lib/plymouth/themes/lubuntu-logo/lubuntu-logo.plymouth     150       manual mode
  4            /lib/plymouth/themes/solar/solar.plymouth                   10        manual mode
* 5            /lib/plymouth/themes/space-sunrise/space-sunrise.plymouth   100       manual mode
  6            /lib/plymouth/themes/spinfinity/spinfinity.plymouth         10        manual mode
  7            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth       100       manual mode
  8            /lib/plymouth/themes/xubuntu-logo/xubuntu-logo.plymouth     150       manual mode

Press enter to keep the current choice[*], or type selection number:

---

### Post by sudodus on 2014-02-04
I think you are right, and you can always try. Things should be fairly easy to reset.

---

