---
title: "Lubuntu 14.04 installation: GRUB problem"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by michael_freres on 2014-04-25
Hello,

I installed yesterday the last release of Lubuntu and when i restarted the computer i had a message that GRUB was not found.
So i tried to reinstall the lubuntu 12.10 version i had on CD.
I works, but now i have 2 version of lubuntu installed on the pc, 12.10 and the upgraded 14.01.
the grub file start the 12.10 version, but i want the pc starting automaticaly with the 14.01.
What can i do to change the grub priority?

thanks in advance

michael

---

### Post by WoodenWalker on 2014-04-25
This might be able to help you out some. [http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order](http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order)

---

### Post by michael_freres on 2014-04-25
thank you. I'm trying to install the grub customizer

---

### Post by oldfred on 2014-04-25
Can you boot into 14.04 from your 12.10 install's grub menu? It would be at the bottom.

If so you may need to do a full purge & reinstall or a dpkg update and then have a correct install of grub booting.

       sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

      
 # purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by michael_freres on 2014-04-25
i tried to do i like that, but it doesn't work. 
te command sudo apt-get purge grub grub-pc grub-common is not going to the end, see above.
...

michael@michael-B202:~$ sudo fdisk -l
[sudo] password for michael: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 têtes, 63 secteurs/piste, 14593 cylindres, total 234441648 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Identifiant de disque : 0x0008d0ca

Périphérique Amorçage  Début         Fin      Blocs    Id. Système
/dev/sda1   *        2048   102059543    51028748   83  Linux
/dev/sda2       102060030   234440703    66190337    5  Étendue
/dev/sda5       232366080   234440703     1037312   82  partition d'échange Linux / Solaris
/dev/sda6       173205504   203623760    15209128+  83  Linux
/dev/sda7       203624448   232364682    14370117+  83  Linux
/dev/sda8       102060032   173203455    35571712   83  Linux

Les entrées de la table de partitions ne sont pas dans l'ordre du disque

Disk /dev/sdb: 1000.2 GB, 1000204138496 bytes
255 têtes, 63 secteurs/piste, 121601 cylindres, total 1953523708 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Identifiant de disque : 0x885f5ddd

Périphérique Amorçage  Début         Fin      Blocs    Id. Système
/dev/sdb1            2048  1953520064   976759008+   c  W95 FAT32 (LBA)

Disque /dev/sdc : 1015 Mo, 1015021568 octets
12 têtes, 43 secteurs/piste, 3841 cylindres, total 1982464 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Identifiant de disque : 0x00000000

Périphérique Amorçage  Début         Fin      Blocs    Id. Système
/dev/sdc1             251     1982463      991106+   6  FAT16
michael@michael-B202:~$ sudo apt-get purge grub grub-pc grub-common
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires :
  libswscale-extra-2 linux-image-3.8.0-31-generic
  linux-image-extra-3.8.0-31-generic
Veuillez utiliser « apt-get autoremove » pour les supprimer.
Les paquets suivants seront ENLEVÉS :
  grub* grub-common* grub-pc* grub-pc-bin*
0 mis à jour, 0 nouvellement installés, 4 à enlever et 0 non mis à jour.
Après cette opération, 15,8 Mo d'espace disque seront libérés.
Souhaitez-vous continuer ? [O/n] n
Annulation.
michael@michael-B202:~$ sudo apt-get purge grub grub-pc grub-common
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires :
  libswscale-extra-2 linux-image-3.8.0-31-generic
  linux-image-extra-3.8.0-31-generic
Veuillez utiliser « apt-get autoremove » pour les supprimer.
Les paquets suivants seront ENLEVÉS :
  grub* grub-common* grub-pc* grub-pc-bin*
0 mis à jour, 0 nouvellement installés, 4 à enlever et 0 non mis à jour.
Après cette opération, 15,8 Mo d'espace disque seront libérés.
Souhaitez-vous continuer ? [O/n] O
Annulation.
michael@michael-B202:~$ sudo apt-get purge grub grub-pc grub-common
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires :
  libswscale-extra-2 linux-image-3.8.0-31-generic
  linux-image-extra-3.8.0-31-generic
Veuillez utiliser « apt-get autoremove » pour les supprimer.
Les paquets suivants seront ENLEVÉS :
  grub* grub-common* grub-pc* grub-pc-bin*
0 mis à jour, 0 nouvellement installés, 4 à enlever et 0 non mis à jour.
Après cette opération, 15,8 Mo d'espace disque seront libérés.
Souhaitez-vous continuer ? [O/n] 
Annulation.
michael@michael-B202:~$ sudo apt-get purge grub grub-pc grub-common
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires :
  libswscale-extra-2 linux-image-3.8.0-31-generic
  linux-image-extra-3.8.0-31-generic
Veuillez utiliser « apt-get autoremove » pour les supprimer.
Les paquets suivants seront ENLEVÉS :
  grub* grub-common* grub-pc* grub-pc-bin*
0 mis à jour, 0 nouvellement installés, 4 à enlever et 0 non mis à jour.
Après cette opération, 15,8 Mo d'espace disque seront libérés.
Souhaitez-vous continuer ? [O/n] O 
Annulation.
michael@michael-B202:~$

---

### Post by oldfred on 2014-04-25
Afraid my French was in High School in 1960, so not very good now. :)

If you have uninstalled grub, do not reboot without reinstalling it.

---

### Post by michael_freres on 2014-04-25
and my english is very bad, so it will be difficult to make me anderstand.
another question. How can i go in "superuser" ('superutilisateur')?

---

### Post by oldfred on 2014-04-25
Super user is just sudo. And you issued the command with sudo.
Do you have working Internet as the reinstall needs that to download the new grub packages.

       [http://xkcd.com/149/](http://xkcd.com/149/)

Above has never worked for me.

---

### Post by michael_freres on 2014-04-25
:-)
ok i have restarted the pc and the grub menu is still the same, so i think, nothing is wrong.
i think the systems goes on internet to load a new package, but i'm not sure...
i have on the pc different os
Ubuntu
xubuntu
lubuntu 12.10
lubuntu 14.04
but i need juste the partition with lubuntu 14.04. Perhaps is it easier to erase the other OS and to clear the different patition?...

---

### Post by oldfred on 2014-04-25
Before deleting partitions you need to know that 14.04's version of grub is the one booting from the MBR of the hard drive.

Are you directly booting into 14.04, or is the first menu item one of the other installs?

---

### Post by michael_freres on 2014-04-26
yes thats the problem, the system is booting on Lubuntu 12.10 because it's the first item. I want to boot on the lubuntu 14.04 version. 
what is the MDR of the hard disk?

---

### Post by michael_freres on 2014-04-26
the only data i want to save is the email on thunderbird. thunderbird gives not the possibility to save data in another folder... How can i save my emails on another harddisk?

---

### Post by oldfred on 2014-04-26
I use a shared partition for both Tbird and Firefox. I also converted firefox in both windows & ubuntu from 2 to 3 to 3.5. I
Start Thunderbird & shut down. In place, homefolder, (change view setting check to show hidden files), scroll down to .mozilla-thunder
on my system:

For Thunderbird, please press Alt+F2 and run ubuntu-bug thunderbird. 

/home/fred/.mozilla-thunderbird

It should contain a profile file and a directory xxxxxx.default
You can copy the entire default directory from one computer to another. If the name or path is different you can edit the profile with the correct entry. I also copy my shared to my portable and back when I travel without any problem.

More info:
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Profile_Manager](http://kb.mozillazine.org/Profile_Manager)

When you start computer BIOS checks what hardware you have and jumps to MBR to continue to boot.
Applies to all MBR systems, but grub does not use PBR or partition boot sector like Windows does.
 Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

If you can boot into 14.04 run this:
      
 sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive like sda, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by michael_freres on 2014-04-28
thank you very much, i have saved the mail archives.
but i also fund an old virus on my extern harddisk, his name is .trash-1000. Is it possible to earse it?

I tried 
 sudo dpkg-reconfigure grub-pc
but i have some problems... i think the system is not right installed on my pc.
michael@michael-B202:~$ 
michael@michael-B202:~$ sudo dpkg-reconfigure grub-pc
[sudo] password for michael: 
/usr/sbin/dpkg-reconfigure: grub-pc est cassé ou partiellement installé
michael@michael-B202:~$ 

I will trie to erase all the harddisk and to reinstall lubuntu 14.04!
just one little thing, on lubuntu i didn't succeed to install the codec for the video/DVD player "Gnome MPlayer" so I can only read my dvd's on Ubuntu 10 with VLC. I succeeded to install the codec for VLC on Ubuntu 10...


thank for your help
michael

---

### Post by sudodus on 2014-04-28
**.trash-1000** is the trashcan (which is quite useful). Don't wipe it :-)

---

### Post by oldfred on 2014-04-28
I do not know with Lubuntu whether all the restricted extras are installed or not. 
Did you check to install them?

       Media howto: 
[http://ubuntuforums.org/showthread.php?t=2179777](http://ubuntuforums.org/showthread.php?t=2179777)
Older Ubuntu versions may not have new install-css.sh
[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)
(make sure to install/upgrade the libdvdread4 package first)
sudo apt-get install libdvdread4
new libdvdread 4 is already in 13.10
The new libdvdread4 has an updated install-css.sh that will install libdvdcss2 from a videolan repo
[https://launchpad.net/ubuntu/+source/libdvdread](https://launchpad.net/ubuntu/+source/libdvdread)
Medibuntu discontinued April 2013
[https://launchpad.net/medibuntu/+announcement/11219](https://launchpad.net/medibuntu/+announcement/11219)
[http://gauvain.pocentek.net/node/61](http://gauvain.pocentek.net/node/61)

You normally just empty trash. But if you have reinstalled, I do not know if your trash container would then have trash that is not seen by new install?

---

### Post by michael_freres on 2014-05-02
what's a trashcan?...

---

### Post by michael_freres on 2014-05-02
Hello Oldfred,

I'm back :-)
I read the [https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/) and I followed the instruction :
installing 
sudo apt-get install lubuntu-restricted-extras

abd after that 
 sudo /usr/share/doc/libdvdread4/install-css.sh

the pc installed something and after that i tried to start "GnomeMPlayer" or "VLC" but I can't read a DVD and I didn't understand why. 
Did I miss something?

---

### Post by oldfred on 2014-05-02
With Ubuntu you can configure whether trash can is on desktop or not. I see with Unity it is at bottom on Unity. But with your version I am not sure.

I have seen other threads with issues on DVDs, but I do not read them. If above instructions do not work and search of forum does not find useful info, start a new thread with that issue and post what you have already done.

I find the best way to search forum is to use Google.
 But using google is often better than the forums search function.
Just append site:ubuntuforums.org to your search term

---

### Post by michael_freres on 2014-05-02
It works! I don't know why, but it works.
with MPlayer it doesn't work, but with vlc it works. In vlc i had to select /dev/dvd instead of /dev/dvd1 ... and the system is running the dvd.
Every time i close vlc and open it again, the system propose me to open /dev/dvd1. 
but i'm happy it works, so i can reinstall all my PC and erase all the different version of linux. I will install only lubuntu 14.04.
thanks for your help!

---

### Post by sudodus on 2014-05-02
> **michael_freres said:**
> what's a trashcan?...

When you delete a file using the file browser, it is usually set to put it in a special directory, instead of deleting it. This special directory is called the Trashcan or Wastepaper Basket. Once in a while you can view that directory and decide whether you want to delete the file completely by removing it from the Trashcan, or maybe making the Trashcan empty (by removing all files). You can often view the Trashcan from your file browser.

-o-

Edit: If you think that the problem in your title and first post is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED :-)

---

### Post by michael_freres on 2014-05-02
ok thanks for helping

---

