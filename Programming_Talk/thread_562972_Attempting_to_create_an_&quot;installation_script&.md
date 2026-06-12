---
title: "Attempting to create an &quot;installation script&quot;"
date: 2007-09-29
forum: Programming Talk
---

### Post by Incursis on 2007-09-29
Hello, I am trying to create an "installation script" on Kubuntu 7.04 that would install all the required programs I need. Its not so much an actual script but more of a batch process.

I am setting this up because I am trying to simplify my post-ubuntu-installation by having all my programs downloaded and installed automatically using the terminal without much user interaction.

I have attached my batch script here:
```
#Remove programs
sudo apt-get remove akregator amarok hplip kaffeine karm kate kexi klipper kmag kmail kmousetool knotes konversation konqueror kontact kpdf kppp kwalletmanager

#Add new repository
echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

#Copy fonts
mkdir /home/jon/.fonts
sudo cp /media/sda5/Setup/Linux/Fonts/*.* /home/jon/.fonts/
sudo fc-cache -f

#Install ATI drivers
sudo apt-get update
sudo dpkg -i '/media/sda5/Setup/Linux/ATI Mobility Radeon Drivers/xorg-driver-fglrx_8.40.4-1_i386.deb'
sudo dpkg -i '/media/sda5/Setup/Linux/ATI Mobility Radeon Drivers/xorg-driver-fglrx-dev_8.40.4-1_i386.deb'
sudo dpkg -i '/media/sda5/Setup/Linux/ATI Mobility Radeon Drivers/fglrx-kernel-source_8.40.4-1_i386.deb'
sudo dpkg -i '/media/sda5/Setup/Linux/ATI Mobility Radeon Drivers/fglrx-amdcccle_8.40.4-1_i386.deb'
aticonfig --initial

#Install Real Player
sudo dpkg -i '/media/sda5/Setup/Linux/Real Player/realplayer_10.0.8-0.1_i386.deb'

#Install programs
sudo apt-get update
sudo apt-get install acroread acroread-escript dolphin filezilla firefox gstreamer0.10-gnomevfs kedit ksynaptics ktemperature mozilla-plugin-vlc mozilla-thunderbird putty quodlibet sun-java6-jdk sun-java6-jre sun-java6-plugin vlc wine

#Install printer drivers
sudo apt-get update
sudo apt-get install alien libxml1 libpng12-0 libpng12-dev libgtk1.2 libgtk1.2-common
mkdir canon 
cd canon
tar -xvzf '/media/sda5/Setup/Linux/Canon iP1600/iP2200_Linux_260.tar.gz'
sudo alien cnijfilter-common-2.60-1.i386.rpm cnijfilter-ip2200-2.60-1.i386.rpm
sudo dpkg -i *.deb
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
sudo ln -s /usr/lib/libpng.so /usr/lib/libpng.so.3
sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1
sudo ldconfig
sudo /etc/init.d/cupsys restart

#Install avast antivirus
sudo apt-get update
sudo dpkg -i '/media/sda5/Setup/Linux/avast Antivirus/avast4workstation_1.0.8-2_i386.deb'
cd /usr/lib/avast4workstation/share/avast/desktop
sudo ./install-desktop-entries.sh install

#Distribution upgrade
sudo apt-get dist-upgrade

#Post-installation process
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```

I tried pasting all that into a terminal window but I get errors and lots of it gets skipped and the terminal ends up pointing to the wrong directory.

It is a custom install using wubi and I have an NTFS partition which is mounted and readable as well as an active wireless connection to get files from.

I was wondering if there is something wrong with my code. I suspect that it may be a problem with the commented lines causing problems with the terminal as well as the cd commands needing a return carriage. Still I am unsure as to what the problem may be.

---

### Post by walkerk on 2007-09-29
why not make a sh file?

```
gedit install.sh
```

insert into file
```

#!/bin/bash

#Remove programs
sudo apt-get remove akregator amarok hplip kaffeine karm kate kexi klipper kmag kmail kmousetool knotes konversation konqueror kontact kpdf kppp kwalletmanager

#Add new repository
echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

#Copy fonts
mkdir /home/jon/.fonts
sudo cp /media/sda5/Setup/Linux/Fonts/*.* /home/jon/.fonts/
sudo fc-cache -f

#Install ATI drivers
sudo apt-get update
sudo dpkg -i '/media/sda5/Setup/Linux/ATI Mobility Radeon Drivers/xorg-driver-fglrx_8.40.4-1_i386.deb'
sudo dpkg -i '/media/sda5/Setup/Linux/ATI Mobility Radeon Drivers/xorg-driver-fglrx-dev_8.40.4-1_i386.deb'
sudo dpkg -i '/media/sda5/Setup/Linux/ATI Mobility Radeon Drivers/fglrx-kernel-source_8.40.4-1_i386.deb'
sudo dpkg -i '/media/sda5/Setup/Linux/ATI Mobility Radeon Drivers/fglrx-amdcccle_8.40.4-1_i386.deb'
aticonfig --initial

#Install Real Player
sudo dpkg -i '/media/sda5/Setup/Linux/Real Player/realplayer_10.0.8-0.1_i386.deb'

#Install programs
sudo apt-get update
sudo apt-get install acroread acroread-escript dolphin filezilla firefox gstreamer0.10-gnomevfs kedit ksynaptics ktemperature mozilla-plugin-vlc mozilla-thunderbird putty quodlibet sun-java6-jdk sun-java6-jre sun-java6-plugin vlc wine

#Install printer drivers
sudo apt-get update
sudo apt-get install alien libxml1 libpng12-0 libpng12-dev libgtk1.2 libgtk1.2-common
mkdir canon 
cd canon
tar -xvzf '/media/sda5/Setup/Linux/Canon iP1600/iP2200_Linux_260.tar.gz'
sudo alien cnijfilter-common-2.60-1.i386.rpm cnijfilter-ip2200-2.60-1.i386.rpm
sudo dpkg -i *.deb
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
sudo ln -s /usr/lib/libpng.so /usr/lib/libpng.so.3
sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1
sudo ldconfig
sudo /etc/init.d/cupsys restart

#Install avast antivirus
sudo apt-get update
sudo dpkg -i '/media/sda5/Setup/Linux/avast Antivirus/avast4workstation_1.0.8-2_i386.deb'
cd /usr/lib/avast4workstation/share/avast/desktop
sudo ./install-desktop-entries.sh install

#Distribution upgrade
sudo apt-get dist-upgrade

#Post-installation process
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

```

make it executable
```
chmod +x install.sh
```

now run it
```
./install.sh
```

---

### Post by Incursis on 2007-09-29
It didn't work. Something was missing, I think the error said something about needing a component to execute or compile the script. Oh well it doesn't really matter anymore. I just installed manually and I figured out what messes up the script if I add everything into the terminal.

Thanks for your help.

---

### Post by venik212 on 2007-10-03
That's really too bad, since I am in the same situation: each time there is a new version, I have to reinstall a lot of various programs.  I would love to be able to just unleash a script that will do all of that.  Ideally, Kubuntu should log my installation choices, and create a script that I could update as things change.

---

