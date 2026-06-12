---
title: "rm command to remove default plymouth"
date: 2014-02-04
forum: New to Ubuntu
---

### Post by rburkartjo on 2014-02-04
still messing around with splash screen. somehow i selected a splash and cant delete it. the splash wont stop loading even if i select another one. tks

---

### Post by rburkartjo on 2014-02-04
or a fix might be to remove the plymouth .config file if there is one. but cant seem to find.

---

### Post by rburkartjo on 2014-02-04
and to make matter more confusing if i run 

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

### Post by rburkartjo on 2014-02-04
and chose any of the above options i can change only the shutdown splash screen. the startup screen keeps using the one that is not on the list and i thought i had deleted. weird.

---

### Post by rburkartjo on 2014-02-04
this is what i have to undo i think to fix. no idea how to do. looks like i need to edit the default plymouth

linux-is-sexy
modification of the awesome plymouth theme made by n3cr0-0 and props to Andre "Osku" Schmidt for supply the scripts to mod and also to zechman1138 for his modd of the space-sunrise "earth-sunrise"

/********************************************/
/ installation                               /
/********************************************/
Then extract the contents of the zip INT2MIL-Ubuntu-10.04-Eng to your home or Desktop folder, then open a terminal and run this (firstly navigate to the folder where you extracted it using a terminal; if you extracted it on your Desktop, that would be: cd ~/Desktop):

sudo cp -R linux-is-sexy/ /lib/plymouth/themes/
sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/linux-is-sexy/linsex.plymouth 100
sudo update-alternatives --config default.plymouth  #here, choose the number of the theme you want to use then hit enter
sudo update-initramfs -u

---

### Post by rburkartjo on 2014-02-04
no big deal just want to figure it out so if it happens again i can fix

---

### Post by rburkartjo on 2014-02-05
fixed it by just messing around. which is not a good answer. will mark this thread as closed when i can explain what i did. or at least duplicate.

---

### Post by rburkartjo on 2014-02-09
okay figured out how to do but complicated

to change the boot screen so that the startup and shutdown splash screen are the SAME
run
sudo update-alternatives --config default.plymouth
[sudo] password for ray: 
There are 9 choices for the alternative default.plymouth (providing /lib/plymouth/themes/default.plymouth).

  Selection    Path                                                       Priority   Status
------------------------------------------------------------
  0            /lib/plymouth/themes/lubuntu-logo/lubuntu-logo.plymouth     150       auto mode
  1            /lib/plymouth/themes/fade-in/fade-in.plymouth               10        manual mode
  2            /lib/plymouth/themes/glow/glow.plymouth                     10        manual mode
* 3            /lib/plymouth/themes/linux-is-sexy/linsex.plymouth          100       manual mode
  4            /lib/plymouth/themes/lubuntu-logo/lubuntu-logo.plymouth     150       manual mode
  5            /lib/plymouth/themes/solar/solar.plymouth                   10        manual mode
  6            /lib/plymouth/themes/space-sunrise/space-sunrise.plymouth   100       manual mode
  7            /lib/plymouth/themes/spinfinity/spinfinity.plymouth         10        manual mode
  8            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth       100       manual mode
  9            /lib/plymouth/themes/xubuntu-logo/xubuntu-logo.plymouth     150       manual mode

Press enter to keep the current choice[*], or type selection number: 

select the number you want
then run in terminal
sudo mount -o remount,exec /tmp
then run in terminal
sudo update-initramfs -u
and wait until the prompt comes back

sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.11.0-17-generic
ray@ray-Latitude-D630:~$ 

now both of the splash screen will be the same

if you now go back and run the first command
sudo update-alternatives --config default.plymouth

and select whatever number the shutdown splash screen will change to that and the startup splash will not change

---

