---
title: "Ubuntu 11.04 hangs on startup where its shows ubuntu....."
date: 2011-04-01
forum: Philippine Team
---

### Post by gtechmyk on 2011-04-01
Guys need help. can not find solution for this one. d ko magamit desktop unit ko. inupgrade ko yng ubuntu 10.10 na nakainstall sa dekstop unit ko to ubuntu 11.04... succesfull nmn yng uprgade hanggang sa magrestart cya. tpos un na. nung nsa splash screen na where it shows ubuntu ..... ala na naghang na. hanggang dun na lang ayaw na magpatuloy. kahit irestart ko ganun pa din. still it stocks on the splash screen where it shows ubuntu ..... ano po ba dpat ko gawin. is der a way to go back to ubuntu 10.10..

---

### Post by Script Warlock on 2011-04-01
na try mo ba muna sa live cd or usb ang machine mo before installing or upgrading to 11.04? better reinstall na lang kesa mag downgrade mas malaki trabaho. or drop to shell during boot at tingnan ang mga sablay sa /var/log

you can use 
less
grep
tail
more
cat var/log/boot.log

huwag kalimutan nasa beta stage pa lang ang 11.04.

---

### Post by gtechmyk on 2011-04-01
i think der is something wrong with my display driver. i was able to access the command line by pressing ctrl+alt+F1.. i tried gnome-panel but no luck its says Gtk-WARNING **: cannot open display. den i tried sudo gedit /boot/grub/menu.lst -samething no luck once again it says Gtk-WARNING **:cannot open display. still no find solution but at-least now i know whats causing the problem.for sure its my video card thats making the plymouth loads unnecessarily. 

my video card is NVIDIA GeForce FX5500 256Mb. if u guys find solutions just tell me that would be a big help.

---

### Post by Script Warlock on 2011-04-01
try mo na muna tingnan ang /var/log kung ano talaga ang problema possible din yung hardware try mo din palitan ang vc kung may spare pa.

---

### Post by gtechmyk on 2011-04-01
i'm trying to install driver for my NVIDIA GeForce FX5500 using sudo apt-get install linux-restricted-modules-generic but it shows 
Encounter a section with no package: header
Problem with mergelist /var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en 
sir sa tingin nyo po ano mali kc ganito din yng lumalabas pag ginagamit ko yng sudo apt-get update. hay 11.04 beta version sakit sa ulo bkt ba kc naisipan ko iupgrade yng desktop unit ko from 10.10 to 11.04. d ko na 2loy magamit. hanggang splash screen na lang.

---

### Post by Script Warlock on 2011-04-01
huwag kang aasa sa beta di pa yan stable.

---

### Post by zeroseven0183 on 2011-04-01
Do you think similar ang problem na naencounter mo dito? [http://ubuntuforums.org/showthread.php?t=1679457](http://ubuntuforums.org/showthread.php?t=1679457)

If you can boot to recovery mode and follow the instructions mentioned in post#2.

---

### Post by gtechmyk on 2011-04-03
problem solved. thanks po sir sa mga help and suggestions. was so lucky i was able to boot on recovery mode den i chose the failxsafe graphics mode. den i was able to fix everything. now everything is working good. thanks po uli mga sir..

---

