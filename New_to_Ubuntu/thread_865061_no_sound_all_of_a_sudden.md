---
title: "no sound all of a sudden"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-20
after a upgrade my sound disappeared,i have an hda intel sound card.if that helps,but no sound no fun:(
unusually i get sound on games but not music or any thing else.
rick i am also getting an error when i play an mp3:failed to connect stream:invalid argument.

---

### Post by dexter.deepak on 2008-07-20
even i had the same problem in the past and i had to reinstall the alsa drivers..
just give them execute permissions 
```
sudo chmod 777 alsa_1.sh
sudo chmod 777 alsa_2.sh
```
and run the first one:
```
sudo sh ./alsa_1.sh
```
reboot your system and then try the second one:
```
sudo sh ./alsa_2.sh
```
hope that works !!

---

### Post by rixtr66 on 2008-07-20
when i run your commands i get no such program,i downloaded the alsa files 
and the first one downloaded abunch of files i dont know what to do with,
the second one wouldnt download,what do i do with the files???
rick

---

### Post by dexter.deepak on 2008-07-20
this is strange !!
i myself just downloaded the stuff and everything works fine !!
but here's an alternative..
this is the alsa_1.sh:
```
#!/bin/sh
#Thanks to Ubuntu forum user, 'syxbit'
#install necessary stuff
apt-get install build-essential ncurses-dev gettext
apt-get install linux-headers-`uname -r`

echo "downloading alsa packages..."
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2

echo "extracting alsa packages..."
tar -xjf alsa-driver*.tar.bz2
tar -xjf alsa-lib*.tar.bz2
tar -xjf alsa-utils*.tar.bz2
rm alsa*.tar.bz2

echo "setting up alsa for compilation"
mkdir -p /usr/src/alsa
mv alsa-* /usr/src/alsa

#alsa-driver
cd /usr/src/alsa/alsa-driver*
./configure --with-cards=hda-intel --prefix=/usr
make
make install

#alsa-lib
cd /usr/src/alsa/alsa-lib*
./configure --prefix=/usr
make
make install

#alsa-utils
cd /usr/src/alsa/alsa-utils*
./configure --prefix=/usr
make
make install

echo "now reboot your machine, and run alsa_2"

```
this is the alsa_2.sh
```
#!/bin/sh
#for after reboot
cp -v /lib/modules/2.6.2*/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.2*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
cp -v /usr/src/alsa/alsa-driver*/modules/* /lib/modules/2.6.2*/kernel/sound/
depmod -a
#end of alsa_2

```

simply copy and paste these scripts to your favourite text editor, and save them with the names alsa_1.sh and alsa_2.sh respectively.
suppose we save them on your desktop.
execute these commands:
```

cd Desktop
sudo chmod a+x alsa_1.sh
sudo chmod a+x alsa_2.sh
sudo ./alsa_1.sh

```
reboot your system and then run the second one :
```
cd Desktop
sudo ./alsa_2.sh

```
then reboot.

---

### Post by rixtr66 on 2008-07-20
ok i ran through all the commands and they were successfull,but i still 
have the same problem although i can play them through vlc but none of the others,i dont understand this problem because it worked great before the update,thanx for the help,any other ideas?
rick

---

### Post by dexter.deepak on 2008-07-20
do you hear the login sound ?
before trying the above codes were you able to play songs through vlc ?
is the problem limited to mp3 files ?
open up your player through terminal like:
```
amarok
```
or
```
audacious
```
you will get some error messages in the terminal itself..post them here.

---

### Post by rixtr66 on 2008-07-20
i was able to play mp3s through vlc before i put in your codes,
everythingb plays but theres no sound,i can hear my login though,
im wondering if i have to instal the drivers for my sound card,
wich i dont know how to do.
amarok plays but with no sound.

---

### Post by dexter.deepak on 2008-07-21
run the player through  the terminal as suggested in my previous post and post any errors here.
are you trying other players too ??

also goto system -> prefernces-> sound and try all the other drivers listed in the "devices" tab..hope you get some output through other drivers.

if all these dont work..there is one awkward method..
since all the downloaded packages go to /var/cache/apt/archives , you can go there, right-click "arrange icons-> by modification date" , look for the latest entries...probably they are the updates.
note down the package names, and see if they are anyhow linked to "sound",just uninstall them, either through synaptic or apt-get.

---

### Post by t0p on 2008-07-21
My audio on vids also vanished after an update.  This fixed it: [http://ubuntuforums.org/showthread.php?p=4928900]("http://ubuntuforums.org/showthread.php?p=4928900")

---

### Post by perce on 2008-07-21
I had the same sound card, and the same problem. I solved it by opening
system > preferences > sound > devices and setting all first 4 entries to ALSA.

---

### Post by Deedlit on 2008-07-21
Thanks to everyone who posted here. I had a problem with my sound disappearing, and all these posts REALLY helped.

---

### Post by woodybrando on 2008-12-18
Hi all,
The first script ran fine and told me to reboot. So I rebooted and ran the second script which gave me this error:

```


loveruby@loveruby:~/Desktop$ sudo ./alsa_2.sh 
`/lib/modules/2.6.27-7-generic/kernel/sound/pci/hda/snd-hda-intel.ko' -> `/lib/modules/2.6.2*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko'
cp: cannot create regular file `/lib/modules/2.6.2*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko': No such file or directory
cp: cannot stat `/usr/src/alsa/alsa-driver*/modules/*': No such file or directory
cp: omitting directory `/lib/modules/2.6.27-7-generic/kernel/sound/'



```

I'm running intrepid ibex, on a macbookpro 2,2 with 2.6.27-9-generic linux kernel. (which I'm guessing is the reason for the error.) Anyone know how I can fix this?
thanks,
jayson

---

### Post by Doulpe on 2009-01-04
I had the exact same problem with the above user the first commands work then when i try sudo ./alsa_2.sh i get a error and no such file or directory

---

### Post by fluxbuntu_user on 2009-02-19
I am having the same problem as the person above me. I can run the first script and reboot but after that I get an error stating that it cannot find the directories/files. Has anybody come across a solution for this yet?

---

