---
title: "Running/Installing  ubuntu on PC with low RAM"
date: 2007-02-07
forum: Outdated Tutorials &amp; Tips
---

### Post by ambuj123 on 2007-02-07
[SIZE="6"]
Installing Ubuntu 6.10 on old computers low on Ram
[/SIZE]
I had been using Linux on my thinkpad for over 2 years now , it isnt a piece of marvel just a modest configuration Pentium M 1.4 GHz , 256 MB Ram and a 40 GB HDD with a slow cdrom drive(hey my original DVD drive got damaged had to use the cheap stuff from market),i had used all sort of Linux distributions from from Fedora Core's to Kubuntu to Linspire to OpenSuse none of the distribution gave me any sort of problem during installation or running . However Ubuntu Linux 6.10 installation and Live CD mode really provided a lot of headaches to me , i had installed Ubuntu 6.06 earlier which installed and ran in Live CD mode quiet flawlessly but on running the latest Ubuntu Distro i was shell shocked the Live CD took more than 10 minutes to just load on my PC not to mention on clicking the install button there was a further 10 - 15 minutes coffee break for me . Now these times may seem absurd to you but it's true coupled with low ram , slow cd drive and apparently Ubuntu not using my swap drive made this a hellish experience .




So i started to find some solution to my problem it was quiet apparent that during ubuntu Linux live cd mode it wasnnullt using my swap partition for storing information and was using temporary swap partition and ram only which was the main cause for the UN-responsiveness . Now if i somehow switched on the swap partition it would really make this installation a lot quicker.

Here is how i did this : -

Method 1:
Boot from the Live CD normally and allow ubuntu to load the full gnome desktop enviornment . Now after the Gnome has loaded fully press Control + F1 which will take you to the console .

Now if you have swap partition on a drive say /dev/hda5 type this

sudo swapon /dev/hda5

This would activated the swap partition which then could be used by the Live CD .

To see if the partition turned up correctly issue command sudo swapon -s

Also if you donnullt have a swap partition i would recommend that you create one by launching the fdisk utility also try having some unpartitioned space for use during the installer since the manual editing of the partition table in ubuntu during installation tends to crash the installer over 80% of times i had numerous hang up during installation of ubuntu.

Now go back to the graphical mode by pressing Ctrl + F7 and continue with the installation process.

Method 2:
This is quiet similar to Method 1 but the unwanted wait for Ubuntu to get loaded can be avoided , also if for some reason ubuntu freezes after loading the graphical enviornment or is just way too slow even to load the graphical enviornment . Put the Ubuntu CD in the drive boot the computer now when the Grub Boot menu is show press F6 to edit the boot options and add line single at the end of the boot parameters .

Now boot the edited menu item , this would boot the ubuntu system into the console quiet quickly now do the following steps : -

Now if you have swap partition on a drive say /dev/hda5 type this sudo swapon /dev/hda5

This would activated the swap partition which then could be used by the Live CD .

To see if the partition turned up correctly issue command
sudo swapon -s

Also if you donnullt have a swap partition i would recommend that you create one by launching the fdisk utility also try having some unpartitioned space for use during the installer since the manual editing of the partition table in ubuntu during installation tends to crash the installer over 80% of times i had numerous hang up during installation of ubuntu.

now at the console type : startx

this would take you to the graphical Gnome enviornment and if all went fine it should work at a usable speed. Now go to System - > Administration -> Install and follow the instructions to install the Ubuntu System on to the hard drive .

Now after installation is complete remove the CD from the drive re-boot the computer now at the grub menu press e and remove single from the boot parameter boot the ubuntu system.

After ubuntu is loaded type sudo gedit /boot/grub/grub.conf and remove all reference to single from the configuration file. and reboot the computer your ubuntu should be configured to be used on this computer now.

by Ambuj Varshney
([http://linuxondesktop.blogspot.com]("http://linuxondesktop.blogspot.com"))

---

### Post by frodon on 2007-02-08
Well, why not just use the alternate CD which use a light installer without loading GNOME, it is made for this purpose as well.

**Anyone who read this, if you have an old computer use the alternate CD it is made for that.**

---

### Post by maxamillion on 2007-02-08
and possibly take a look at Xubuntu or Fluxbuntu ... might yield more desired results.

---

### Post by ambuj123 on 2007-02-08
Hello 
well alternative cd's might just work. But in countries like india where bandwidth is costly first you download 700 MB of stuff in over 28 hours from the internet then find out that it wont work well because you have low ram then just download 700 Mb stuff more it's just too time taking and costly (we are charged per mb download here around 0.01 Cents ) so it maybe  usefull for those who dont have a very good net connection or has no net connection and only live CD.

If alternate cd works you are always welcome to use them.

:)

---

### Post by frodon on 2007-02-08
Yes it works and it is not alternative cd's but "The Official Alternate install CD" ;), it is because it uses another light installer (the one used at the time for warty, hoary and breezy) that it is recommended for old computers.
[http://se.releases.ubuntu.com/6.06/](http://se.releases.ubuntu.com/6.06/)

But obviously once you have downloaded the wrong ISO image and don't want to download another image then your tip is useful :KS

---

### Post by javaTard on 2007-02-17
I should have known better. I am installing Ubuntu for a family friend on an old system and could not get 6.10 to boot as gnome was bombing out. Of course it has very little ram, and thank goodness I had an old 5.10 disk in my CD case. 5.10 of course loaded like a champ!

---

