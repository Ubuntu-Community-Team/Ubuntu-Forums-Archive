---
title: "[SOLVED] huge mistake doesnt let me open terminal! noooo!"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by jsf_pp on 2008-11-10
it seems i made a huge mistake when installing ePSXe. now i cant open terminal!!

it launchs a message like this:

Could not launch application
Failed to change to directory '/home/julio' (Permission denied)

now, even my keyboard seems to be working wrongly cuz some characters changed their old keys to appear.

[ like when i press the nine key + shift it writes "(" and not the usual ")" which is now under zero key + shift ]

why is this happening ?
can i go back in time like, lets say, half an hour ago?? 

thanks! 

PD: about the keyb, im from southamerica, thats why i have that configuration.

---

### Post by echo.whoami on 2008-11-10
Press alt-f2 and then write /usr/bin/gnome-terminal.

Does the terminal open?

---

### Post by jsf_pp on 2008-11-10
i did it but no. not at all. after i press run nothing happens.

damn! now i realize firefox is different became diferent! this forum, as an example, looks like this...

damn x2 : i tried to take a screenshot and i cant!!! not even pressing the IMP PNT PET SYS key.

damn x3 : theres no appliaction workin!! only the ones are already opened... that means if i disconect from the internet right now i wont be able to do it anymore... and i'll die. :biggrin:

noooooo!
thanks anyway for trying.

---

### Post by jamesrl on 2008-11-10
hmmm... Permission denied is a weird error message, that's usually easily correctable (it just means it thinks you are some other user who doesn't have access to your home directory).

Can you try pressing Alt-F2 and then
```
gksudo gnome-terminal
```

It will try opening the terminal as root user (and prompt you for your password).

---

### Post by jsf_pp on 2008-11-10
> **jamesrl said:**
> hmmm... Permission denied is a weird error message, that's usually easily correctable (it just means it thinks you are some other user who doesn't have access to your home directory).

Can you try pressing Alt-F2 and then
```
gksudo gnome-terminal
```

It will try opening the terminal as root user (and prompt you for your password).

ok. i did it. and again, nohing happens after i press run. im starting to worry about it.

---

### Post by jamesrl on 2008-11-10
First, do you know exactly what you did wrong?  Did you type commands like 'chmod -R 000 /home/julio'?

I would try rebooting, but have a plan of what to do first.

If everything's not fixed upon rebooting (e.g., you can login but can't start any new programs like right now or you can't login as your normal user.), I would try either booting into single user mode to try fixing everything (equivalent to logging in as root), or boot from a live cd.

To boot from single user mode, just select from the grub menu "recovery mode" (equivalent to "single-user mode").  Hopefully you will be able to get back on the internet from one of these modes (or from a live cd), as well as diagnose your problem better.

---

### Post by jamesrl on 2008-11-10
Also have you tried other terminal programs:
like running
```
xterm
```

---

### Post by ajgreeny on 2008-11-10
What about Ctrl+Alt+F1 and simply reversing what you did to install the emulator, or am I just too simple.  I have no idea how you install it or what it is, but this is just a thought you may have overlooked.

---

### Post by jsf_pp on 2008-11-10
hi, im back. yes, like i said my firefox out of the blue stopped working and when i closed it down i wasnt able to open it any more.

ok, so, without internet and your help im like a hopeless and sad n00b here. so, i reboot it.

everything went ok til the user & password screen shown up cuz after i inserted my user and my pass the system told me i wasnt able of...no permisions... blablabla.

i went to the left/down corner of that screen several times trying to get in anyhow, and after a while i realized that the last option was the only one to go in. yes, that one is fail terminal (or sth like that).

but in there, well, let me be honest with you guys, IM LIKE TOTALLY LOST! for real. when i was a lil boy i had to use a lot of DOS cuz i have ever had bad experiences with guindows since the very first beginning so thanks to that i achieved to apply the dir command and some programs like firefox writing 

sudo firefox

which must be the most obvious thing to you, but for me its like way new stuff.

anyway. as i couldnt connect my laptop to the internet under terminal i went to my cds case in order to get my pretty 7.10 ubuntu disk.

and here i am. under a live CD of gutsy.

now, please help me. i'll be here till i (actually, you guys...)fix it.7

thanks!

---

### Post by jsf_pp on 2008-11-10
> **jamesrl said:**
> First, do you know exactly what you did wrong?  Did you type commands like 'chmod -R 000 /home/julio'?

I would try rebooting, but have a plan of what to do first.

If everything's not fixed upon rebooting (e.g., you can login but can't start any new programs like right now or you can't login as your normal user.), I would try either booting into single user mode to try fixing everything (equivalent to logging in as root), or boot from a live cd.

To boot from single user mode, just select from the grub menu "recovery mode" (equivalent to "single-user mode").  Hopefully you will be able to get back on the internet from one of these modes (or from a live cd), as well as diagnose your problem better.

yes, i remember myself stupidly writing sth like chmod in terminal several hours ago.

let me search the HOWTO i was following to install that satanic ePSX

---

### Post by jsf_pp on 2008-11-10
i find it. its this one [http://ubuntuforums.org/showthread.php?t=95835](http://ubuntuforums.org/showthread.php?t=95835)
and yes, there are a few chmod 777 and some 666 too.

is that bad?
PD: it was till that line, the chmod one, that everything went wrong.

heeeeelp!:confused:

---

### Post by jsf_pp on 2008-11-10
desperately im begging for help. ](*,)

---

### Post by night_fox on 2008-11-10
chmod 666 bla

gives a file read and write permissions for everyone

chmod 777 bla

gives a file read write and execute permissions for everyone.

how do you know everything went wrong then? Did it give you an error message? Can you post it?

To find out what you did you could look at your bash history file. You can do this from the live CD, just mount the right partition of your hard disk in "Computer" then find your home directory (home/<INSERT USER NAME HERE>).

Press Ctrl-H to display hidden files

Find a file call .bash_history.

From single user mode/recovery mode:
```

cd /home/<USER NAME>

cat .bash_history | more
```

---

### Post by jsf_pp on 2008-11-10
> **night_fox said:**
> chmod 666 bla

gives a file read and write permissions for everyone

chmod 777 bla

gives a file read write and execute permissions for everyone.

how do you know everything went wrong then? Did it give you an error message? Can you post it?

To find out what you did you could look at your bash history file. You can do this from the live CD, just mount the right partition of your hard disk in "Computer" then find your home directory (home/<INSERT USER NAME HERE>).

Press Ctrl-H to display hidden files

Find a file call .bash_history.

From single user mode/recovery mode:
```
 
cd /home/<USER NAME>

cat .bash_history | more
```

ok i did both. but none of em works, look:

both screenshots attached...

---

### Post by night_fox on 2008-11-10
I take it your still using the live cd? Whats with the mentally big titlebars? Did you get bored?

BTW cd /home takes you the home directory on the live CD, and cd /julio takes you to a directory "julio" in the directory "/". "cd julio" is what you wanted but it wouldn't have worked because it is the live CD's file system and not your real home directory.

From the terminal on the live CD (I'm sorry that the commands I gave you didn't take into account your crazy file system (My home was in exactly the same place until a while back))

Here are some commands that will work:

```

cd /media/disk/home/julio       # disk has to be mounted
sudo gedit .bash_history        # dont change anything

Failing that:

cd /media/disk/home
ls -l julio
ls -l julio/.bash_history

```

those last 2 command lists everything about files.

---

### Post by night_fox on 2008-11-10
BTW I see you were trying to log in as root. On ubuntu your meant to use 

sudo <COMMAND> to run <COMMAND> as root but there is an equivalent.

---

### Post by jsf_pp on 2008-11-10
yes, im still using the live CD.
no, i didnt get bored, its just a common bug on gutsy im not goin to fix cuz... its the live CD. so **** the elephant titlebars

hahahha

anyway, im still dying here.

i did what you said and this happened:

the .bash_history file was completely empty!!!
this is gettin worse....

hey, but thanks for the help dude!

PD: i tried to upload the .bash_history file almost in every site i know, even as an attachment to this thread but its seems to be impossible.

---

### Post by jsf_pp on 2008-11-10
> **night_fox said:**
> BTW I see you were trying to log in as root. On ubuntu your meant to use 

sudo <COMMAND> to run <COMMAND> as root but there is an equivalent.

yes, now, about that, I WAS BORED so i did try everything (i dont know that much anyway, so its not like im goin to fix the whole thing writin su and my pass, but,... well, hope is the last you should lose..)

---

### Post by night_fox on 2008-11-10
Hi again, you appear to have changed the permissions of your home directory.

I think all directories might have to have execute permissions, so to reclaim your home folder you will need to do:

```
cd /media/disk/home
chmod 755 julio
```

now find the bash history file.

---

### Post by jamesrl on 2008-11-10
So from one of your screen shots it seems the permissions in your home directory do not give you access to change into that directory (eXecute).

So what you have to do, is from the live cd type 
```
sudo chmod -R a+X /media/disk/home/julio
```

This gives all users (the a) adds (the +) eXecute permission to all users (+X) for all directories and already executable files, in all the original  directory and its subdirectories.  (the -R)

EDIT: Seems like I was beaten to the reply.

---

### Post by jsf_pp on 2008-11-10
```
ubuntu@ubuntu:~$ cd /media/disk/home
ubuntu@ubuntu:/media/disk/home$ chmod 755 julio
chmod: changing permissions of `julio': Operation not permitted
ubuntu@ubuntu:/media/disk/home$ 

```

nope. but thanks for staying w/ me bro!

---

### Post by night_fox on 2008-11-10
Heres how the permissions work. This is the first column when you do ls -l:

drwxrwxrwx

the d means this is a directory. Not really a permission
the rwx stands for read write and execute.
the first  rwx means the owner's permissions
the second rwx means the group's permissions
the third belongs to everyone else
These can all be changed very simply from nautilus file manager (provided you have the permissions)

so -rwxr-xr-x means the owner can read write and execute the file, the group and everyone else can read and execute the file but cannot change it.
The rwx flags here are actually a group of binary digits, for instance

r-x = 101

which in decimal is 5.

so 755 corresponds to those permissions I gave you (I copied them from my own computer) and dont worry I tested every command I've given you on my own laptop!

---

### Post by night_fox on 2008-11-10
My apologies mate, do sudo and then that chmod command

---

### Post by night_fox on 2008-11-10
something that might be useful:
> man <COMMAND> brings up the manual page for <COMMAND>

exit it by pressing "q"

---

### Post by jsf_pp on 2008-11-10
> **jamesrl said:**
> So from one of your screen shots it seems the permissions in your home directory do not give you access to change into that directory (eXecute).

So what you have to do, is from the live cd type 
```
sudo chmod -R a+X /media/disk/home/julio
```

This gives all users (the a) adds (the +) eXecute permission to all users (+X) for all directories and already executable files, in all the original  directory and its subdirectories.  (the -R)

EDIT: Seems like I was beaten to the reply.

thanks man! i was able to open the fuc.king file!!!

and this is whats inside:

```
sudo pppoeconf
exit
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install compizconfig-settings-manager
exit
sudo gedit /etc/modprobe.d/alsa-base
sudo pppoe
sudo pppoeconf
sudo nautilus
sudo 
sudo vim/emacs/gedit/nano gdm.conf, chocolate
sudo vim/emacs/gedit/nano gdm.conf
sudo vim/emacs/gedit/nano file.txt
chocolate
sudo aptitude install wifi-radar
sudo vim/emacs/gedit/gdm.conf
sudo gedit gdm.conf
lsb_release -a
sudo
sudo -k
sudo -u
?
dir
cd escritorio
escritorio
cd: escritorio
cd..
subir
agt
-agt
apt-get
super vaca?
sudo -u julio
man sudo
sebfqknsaçf
sudo -a
sudo -a julio
lnhfgñwqja
sudo -k julio
sudo
sudo -K
sudo -k
echo "julio ALL=(ALL) ALL" >> etc/sudoers
echo julio ALL
sudo gedit /etc/gdm/gdm.conf
sudo -k j
gnome-sudoku
gnome-blackjack
gnome
gnome-
gnome-666
gnome-pics
gnome-varios
gnome-music
gnome-sistema de archivos
gnome-dictionary
gnome-sudoku
exit
sudo fdisk-l
sudo fdisk -l
gksudo gedit
sudo apt-get install alien
uname -a
sudo apt-get install flashplugin-nonfree
sudo nautilus
sudo apt-get wine
gconftool-2 -s -t string /apps/gnome-session/options/splash_image /home/julio/Escritorio/Pics/epic pics/epic boobs.jpg
gconftool-2 -s -t string /apps/gnome-session/options/splash_image /home/julio/Escritorio/Pics/epic_pics/epic_boobs.jpg
chocolate
sudo initn0
sudo init 0
sudo reboot
sudo poweroff
sudo init 0
sudo init 6
sudo init 0
suddo init 0
sudo init 0
sudo shutdown -h 13:30 "server is going down for maintenance"
sudo init 0
sudo init 6
sudo init 0
sudo poweroff
sudo init 0
sudo init 6
sudo poweroff
sudo reboot
sudo poweroff
sudo reboot
sudo poweroff
sudo power off
sudo poweroff
sudo reboot
sudo poweroff
sudo reboot
sudo poweroff
setupwfc
/home/julio/Escritorio/setupwfc
sudo poweroff
sudo pweroff
sudo poweroff
chocolarte
chocolarte
sudo poweroff chocolate
sudo rebooy
sudo reboot
sudo poweroff
chocolate
sudo poweroff
sudo reboot
sudo poweroff
sudo poeroff
sudo poweroff
sudo reboot
sudo poweroff
/home/julio/galaxium_0.7.4.1.tar.gz
sudo /home/julio/galaxium_0.7.4.1.tar.gz
miau
mother russia
'/home/julio/crossover_pro_7.0.0-1_i386.tar.gz' 
sudo reboot
sudo poweroff
cd /usr/share/fonts/
sudo chmod 755 myfonts
sudo poweroff
sudo shutdown -h 18:00
sudo poweroff
sudo gedit /etc/apt/sources.list
sudo poweroff
sudo apt-get -f install
sudo apt-get install emesene
sudo sed -i.bak 's/09607671-1C32-421F-A6A6-CBFAA51AB5F4/CFE80F9D-180F-4399-82AB-413F33A1FA11/g' /usr/share/emesene/emesenelib/XmlTemplates.py
sudo shutdown -h 1:20
$ sudo apt-get install supertux 
$ sudo apt-get upgrade 
sudo apt-get upgrade 
sudo poweroff
sudo reboot
sudo poweroff
sudo
sudo poeroff
sudo poweroff
sudo eboot
d
sudo Reboot
sudo init 07
init
sudo init0
sudo ini 0
sudo init 0
apt-get install gsplash
su
sudo poweoff
sudo init 0
sudo dpkg --configure -a
sudo init 0
sudo shutdown -h 02:20
sudo init 0
sudo init 6
su
sudo init 0
su
sudo init 0
sumo inti
sudo init 0
SUDO INIT 0
chocolate
sudo init 0
sudo
sudo init 0
init 0
sudo init 0
sudo init0
sudo init 0
aptitude install openoffice.org
su
ta1.- ¿Por qué para Do Santos el terminar con la dependencia del comercio exterior es insuficiente para terminar con las relaciones de Dependencia?
2.- Señale las causas del déficit de balanza de pagos en el ISI o "la nueva dependencia"
3.- Haga 3 críticas a las teorías desarrollistas.
Estas son las 3 preguntas para economía. Eso por ahora...no esperen pronto mi parte del trabajo de ayudantía, la **** oficina está llena de gente como nunca... (quiero mi computadooooooooooorrr )
Saludos!
.
ta1.- ¿Por qué para Do Santos el terminar con la dependencia del comercio exterior es insuficiente para terminar con las relaciones de Dependencia?
2.- Señale las causas del déficit de balanza de pagos en el ISI o "la nueva dependencia"
3.- Haga 3 críticas a las teorías desarrollistas.
Estas son las 3 preguntas para economía. Eso por ahora...no esperen pronto mi parte del trabajo de ayudantía, la **** oficina está llena de gente como nunca... (quiero mi computadooooooooooorrr )
Saludos!
ta1.- ¿Por qué para Do Santos el terminar con la dependencia del comercio exterior es insuficiente para terminar con las relaciones de Dependencia?
2.- Señale las causas del déficit de balanza de pagos en el ISI o "la nueva dependencia"
3.- Haga 3 críticas a las teorías desarrollistas.
Estas son las 3 preguntas para economía. Eso por ahora...no esperen pronto mi parte del trabajo de ayudantía, la **** oficina está llena de gente como nunca... (quiero mi computadooooooooooorrr )
Saludos!
tar zxvf <OO0_3.0.0_LinuxIntel_install_wJRE_es.tatar zxvf <filename.tar.gz>.
tar zxvf <OOo_3.0.0_LinuxIntel_install_wJRE_es.tar.gz>
tar zxvf OOo_3.0.0_LinuxIntel_install_wJRE_es.tar.gz
/tmp/OOo_3.0.0_LinuxIntel_install_wJRE_es.tar.gz
su
tar zxvf /tmp/OOo_3.0.0_LinuxIntel_install_wJRE_es.tar.gz
5tar zxvf /tmp/OOo_3.0.0_LinuxIntel_install_wJRE_es.tar.gztar zxvf /tmp/OOo_3.0.0_LinuxIntel_install_wJRE_es.tar.gztar zxvf /tmp/OOo_3.0.0_LinuxIntel_install_wJRE_es.tar.gztar zxvf /tmp/OOo_3.0.0_LinuxIntel_install_wJRE_es.tar.gztar zxvf /tmp/OOo_3.0.0_LinuxIntel_install_wJRE_es.tar.gztar zxvf /tmp/OOo_3.0.0_LinuxIntel_install_wJRE_es.tar.gztar zxvf /tmp/OOo_3.0.0_LinuxIntel_install_wJRE_es.tar.gztar zxvf /tmp/OOo_3.0.0_LinuxIntel_install_wJRE_es.tar.gztar zxvf /tmp/OOo_3.0.0_LinuxIntel_install_wJRE_es.tar.gztar zxvf /tmp/OOo_3.0.0_LinuxIntel_install_wJRE_es.tar.gztar zxvf /tmp/OOo_3.0.0_LinuxIntel_install_wJRE_es.tar.gztar zxvf /tmp/OOo_3.0.0_LinuxIntel_install_wJRE_es.tar.gztar zxvf /tmp/OOo_3.0.0_LinuxIntel_install_wJRE_es.tar.gztar zxvf /tmp/OOo_3.0.0_LinuxIntel_install_wJRE_es.tar.gztar zxvf /tmp/OOo_3.0.0_LinuxIntel_install_wJRE_es.tar.gztar zxvf /tmp/OOo_3.0.0_LinuxIntel_install_wJRE_es.tar.gztar zxvf /tmp/OOo_3.0.0_LinuxIntel_in
tar zxvf /tmp/OOo_3.0.0_LinuxIntel_install_wJRE_es.tar.gz
sudo init hola, soy un clon. es obvio no? y la razon es simple: me da una verguenza enorme ventilar esto con la cant de post y años que llevo en el sitio.
sudo init 0
su
sudo apt-get install libartsc0 libasound2 libatk1.0-0 libaudiofile0 libbinio1c2 libc6 libcairo2 libcomerr2 libcurl3-gnutls libesd-alsa0 libflac7 libfontconfig1 libgcc1 libglade2-0 libglib2.0-0 libgnutls12 libgtk2.0-0 libid3-3.8.3c2a libidn11 libkrb53 liblircclient0 libmodplug0c2 libmpcdec3 libmusicbrainz4c2a libogg0 libpango1.0-0 libresid-builder0c2a libsamplerate0 libsidplay1 libsidplay2 libsndfile1 libstdc++6 libtag1c2a libvorbis0a libvorbisfile3 libx11-6 libxcursor1 libxext6 libxfixes3 libxi6 libxinerama1 libxml2 libxrandr2 libxrender1 zlib1g libglade2-dev
sudo apt-get install libartsc0 libasound2 libatk1.0-0 libaudiofile0 libbinio1c2 libc6 libcairo2 libcomerr2 libcurl3-gnutls libesd-alsa0 libfontconfig1 libgcc1 libglade2-0 libglib2.0-0 libgnutls12 libgtk2.0-0 libid3-3.8.3c2a libidn11 libkrb53 liblircclient0 libmodplug0c2 libmpcdec3 libmusicbrainz4c2a libogg0 libpango1.0-0 libresid-builder0c2a libsamplerate0 libsidplay1 libsidplay2 libsndfile1 libstdc++6 libtag1c2a libvorbis0a libvorbisfile3 libx11-6 libxcursor1 libxext6 libxfixes3 libxi6 libxinerama1 libxml2 libxrandr2 libxrender1 zlib1g libglade2-dev
sudo apt-get install libartsc0 libasound2 libatk1.0-0 libaudiofile0 libbinio1c2 libc6 libcairo2 libcomerr2 libcurl3-gnutls libesd-alsa0 libfontconfig1 libgcc1 libglade2-0 libglib2.0-0 libgtk2.0-0 libid3-3.8.3c2a libidn11 libkrb53 liblircclient0 libmodplug0c2 libmpcdec3 libmusicbrainz4c2a libogg0 libpango1.0-0 libresid-builder0c2a libsamplerate0 libsidplay1 libsidplay2 libsndfile1 libstdc++6 libtag1c2a libvorbis0a libvorbisfile3 libx11-6 libxcursor1 libxext6 libxfixes3 libxi6 libxinerama1 libxml2 libxrandr2 libxrender1 zlib1g libglade2-dev
sudo apt-cache policy libjack0
udo apt-get install libartsc0 libasound2 libatk1.0-0 libaudiofile0 libc6 libcairo2 libcomerr2 libcurl3-gnutls libesd-alsa0 libflac7 libfontconfig1 libgcc1 libglade2-0 libglib2.0-0 libgnutls12 libgtk2.0-0 libid3-3.8.3c2a libidn11 libkrb53 liblircclient0 libmodplug0c2 libmpcdec3 libmusicbrainz4c2a libogg0 libpango1.0-0 libsidplay1 libsndfile1 libstdc++6 libtag1c2a libvorbis0a libvorbisfile3 libx11-6 libxcursor1 libxext6 libxfixes3 libxi6 libxinerama1 libxml2 libxrandr2 libxrender1 zlib1g
sudo apt-get install libartsc0 libasound2 libatk1.0-0 libaudiofile0 libc6 libcairo2 libcomerr2 libcurl3-gnutls libesd-alsa0 libflac7 libfontconfig1 libgcc1 libglade2-0 libglib2.0-0 libgnutls12 libgtk2.0-0 libid3-3.8.3c2a libidn11 libkrb53 liblircclient0 libmodplug0c2 libmpcdec3 libmusicbrainz4c2a libogg0 libpango1.0-0 libsidplay1 libsndfile1 libstdc++6 libtag1c2a libvorbis0a libvorbisfile3 libx11-6 libxcursor1 libxext6 libxfixes3 libxi6 libxinerama1 libxml2 libxrandr2 libxrender1 zlib1g
ok
bye
sudo apt-get install audacity
sudo init 0
top
rrr
sudo apt-get install lame liblame0
sudo apt-get install openoffice.org
sudo gedit /etc/apt/sources.list.d/openoffice.list
cd DEBS
cd home
cd julio
/home/julio/OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz
su 
'/home/julio/OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz' 
'/home/julio/Escritorio/OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz' 
'/home/julio/Escritorio/OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz' cd DEBS
'/home/julio/Escritorio/OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz' 
cd DEBS7
cd DEBS
sudo poweroff
sudo reboot
sudo poweroff
sudo reboot
sudo rebooy
sudo rebot
sudo reboot
sudo init 0
sudo poweroff
sudo init 0
sudo apt-get remove openoffice*.*
tar -zxvf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz
tar -zxvf 'OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz'
tar -zxvf '/home/julio/Desktop/OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz'
cd OOO300_m9_native_packed-1_en-US.9358/DEBS/
sudo dpkg -i *.deb
cd desktop-integration
sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb
sudo aptitude install gnome-splashscreen-manager
sudo poweroff
sudo init 0
gksu nautilus
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.org
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure -phigh xserver-xorg
lspci | grep VGA
sudo gedit /etc/X11/xorg.conf
uname -m
sudo apt-get update
wget -q -O - https://dl.google.com/linux/linux_signing_key.pub | sudo apt-key add  -
gksu gedit /etc/apt/sources.list
su
gpg --keyserver hkp://subkeys.pgp.net --recv-keys A040830F7FAC5991
gpg --export --armor A040830F7FAC5991 | sudo apt-key add -
sudo apt-get update
sudo aptitude update
sudo apt-get install gnome-device-manager
sudo apt-get install gnome device manager
sudo apt-get install gnomedevicemanager
sudo apt-get install gnome.device.manager
sudo poweroff
gksu nautilus
sudo apt-get install zsnes
```

any clue?
cuz till znes everything worked just fine. it wasnt till i tried to intall that diabolic epsxe that everything went wrong...

---

### Post by night_fox on 2008-11-10
That should have done it, and now you can probably reboot into your hard disk. BOOM. Well done!

---

### Post by jsf_pp on 2008-11-10
> **night_fox said:**
> That should have done it, and now you can probably reboot into your hard disk. BOOM. Well done!

yes!
we did it!
im back again on my normal enviroment!
hell yeah!
thanks y'all guys!

i really appreciate what you have done here.

this is another solved thread and it'll be tagged like that right now.

thanks thanks thanks!:guitar:

---

### Post by jamesrl on 2008-11-10
I didn't seem to see any evidence of the offending command in your .bash_history (which sort of makes some sense; if you removed permissions to your home directory .bash_history might not have been able to access its history file to record that).

However, if rebooting didn't fix everything, you should check and see what your / looks like (if booting live cd that is /mnt/disk/)
You should have permissions like:
```

ls
drwxr-xr-x   2 root root  4096 2008-11-03 00:21 bin
drwxr-xr-x   3 root root  4096 2008-11-06 01:12 boot
lrwxrwxrwx   1 root root    11 2008-11-02 23:59 cdrom -> media/cdrom
drwxr-xr-x  15 root root 14420 2008-11-10 21:12 dev
drwxr-xr-x 148 root root 12288 2008-11-10 21:13 etc
drwxr-xr-x   4 root root  4096 2008-11-03 23:17 home
lrwxrwxrwx   1 root root    32 2008-11-03 00:09 initrd.img -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  15 root root  4096 2008-11-03 01:49 lib
drwxr-xr-x   4 root root  4096 2008-11-03 01:48 lib32
lrwxrwxrwx   1 root root     4 2008-11-03 00:00 lib64 -> /lib
drwx------   2 root root 16384 2008-11-02 23:59 lost+found
drwxr-xr-x   4 root root  4096 2008-11-10 21:13 media
drwxr-xr-x   3 root root  4096 2008-11-03 01:43 mnt
drwxr-xr-x   3 root root  4096 2008-11-03 13:44 opt
dr-xr-xr-x 156 root root     0 2008-11-10 21:12 proc
drwxr-xr-x  11 root root  4096 2008-11-08 15:27 root
drwxr-xr-x   2 root root  4096 2008-11-03 00:21 sbin
drwxr-xr-x   2 root root  4096 2008-10-29 17:04 srv
drwxr-xr-x  12 root root     0 2008-11-10 21:12 sys
drwxrwxrwt  12 root root  4096 2008-11-10 21:30 tmp
drwxr-xr-x  12 root root  4096 2008-11-03 00:18 usr
drwxr-xr-x  15 root root  4096 2008-10-29 17:28 var
lrwxrwxrwx   1 root root    29 2008-11-03 00:09 vmlinuz -> boot/vmlinuz-2.6.27-7-generic

```
If you don't have the x in all three sets of all the directories (for everything but lost+found and tmp), that means you can't get into them, and should run 
```

sudo chmod -R a+X /

``` You should also check that commands within your bin directories (e.g. /bin/ /sbin/ /usr/bin /usr/sbin ) all have execute priveleges as well.  You can go into any specific directory, first look and if you don't see 3 x in the permissions, I would run:
```

sudo chmod a+x *

```
note with a lower case x (to set specific files not just directories) and no -R.

EDIT: Guess I'm too slow yet again.

---

### Post by Egi_Power on 2008-11-10
> now, even my keyboard seems to be working wrongly cuz some characters changed their old keys to appear.

[ like when i press the nine key + shift it writes "(" and not the usual ")" which is now under zero key + shift ]

why is this happening ?
can i go back in time like, lets say, half an hour ago??

thanks!

PD: about the keyb, im from southamerica, thats why i have that configuration.

If you have problems with the keyboard, you can set it up in the Keyboard Preferences on the Layouts tab. I use hungarian and swedish keyboard layout also, the "(" and ")" [and all other symbols] are not on the same button as on the US layout. Sometimes I forget I changed the layout, then I'm surprised why I can't log in on websites.

Anyway happy you solved your problem.

Take it easy.

---

