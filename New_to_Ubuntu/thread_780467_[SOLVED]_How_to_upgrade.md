---
title: "[SOLVED] How to upgrade"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by phoenix_abhi on 2008-05-03
One rare doubt !

I have two pcs are running Ubuntu. I had installed both as 7.04 fiesty. My internet enabled pc detected and upgraded to gutsy and later to Hardy

Now I am connected my other pc is to the net foer last few days, but except for some updates I have not found any upgradabvle info from fiesty to Gutsy to Hardy

How will I upgrade my machine without downloading a ISO. I meant any otherway to upgrade like getting upgrade from the site ?

Thanks    :)

---

### Post by aysiu on 2008-05-03
Maybe this will help?
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by phoenix_abhi on 2008-05-04
Sorry Aysiu. That didnot help. But I found one and upgraded. Here it is. It may help others too


Manual upgrades to Feisty

Please note - this method is less reliable. If you use this method, you MUST be prepared to fix problems manually, such as packages being unexpectedly removed, apt crashing unexpectedly, etc. It is highly recommended that you use the automatic upgrade instructions on FeistyUpgrades instead.

   1.

      Make sure that you have the packages "ubuntu-minimal" and "ubuntu-standard" installed, regardless of whether you're using Ubuntu, Kubuntu, Xubuntu or Edubuntu:
          *

            Example:

              sudo apt-get install ubuntu-minimal ubuntu-standard 

   2.

      The appropriate desktop package for your version of Ubuntu must also be installed. They are "ubuntu-desktop" for Ubuntu, "kubuntu-desktop" for Kubuntu, "xubuntu-desktop" for Xubuntu, and "edubuntu-desktop" for Edubuntu:
          *

            Example:

            For Ubuntu

              sudo apt-get install ubuntu-desktop 

            For Kubuntu

              sudo apt-get install kubuntu-desktop 

            For Xubuntu

              sudo apt-get install xubuntu-desktop 

            For Edubuntu

              sudo apt-get install edubuntu-desktop 

   3.

      Edit your /etc/apt/sources.list as root. Change every occurrence of edgy to feisty. It is also recommended that you remove or disable any extra repository that may have been added besides the Ubuntu repositories.
          *

            Long route: Use your preferred editor. If you have a CD-ROM line in your file, then remove it.

            For Ubuntu.

              gksudo gedit /etc/apt/sources.list 

            For Kubuntu.

              kdesu kate /etc/apt/sources.list 

            For Xubuntu.

              gksudo mousepad /etc/apt/sources.list 

            In any terminal program.

              sudo nano /etc/apt/sources.list
              sudo vi /etc/apt/sources.list 

          *

            Shortcut:

              sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list 

            NOTE: This might not remove old CD-ROM lines. Manual inspection is suggested after running this command. (see Long Route)
   4.

      If you have the alternate install CD, you can save bandwidth by loading the CD into your CD-ROM drive and using:
          *

              sudo apt-cdrom add 

   5.

      Perform the upgrade:
          *

              sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get dist-upgrade 

            OR, You can also use Aptitude:

              sudo aptitude update && sudo aptitude dist-upgrade && sudo aptitude dist-upgrade 

            NOTE: The first run of dist-upgrade will upgrade everything except for upstart. After this a second dist-upgrade will finish the upgrade.
   6.

      Just to be totally sure that everything is installed properly, run these commands:
          *

              sudo apt-get update && sudo apt-get dist-upgrade
              sudo apt-get -f install
              sudo dpkg --configure -a 

            Running dist-upgrade again is done to ensure that no packages are left to install or upgrade. In some cases, certain packages fail to install even after running dist-upgrade the second time.
   7.

      Reboot in order to effect all changes. (kernel upgrades, upstart, etc...)

Notes

    *

      If run a manual upgrade and you have apache2 and php5 installed, make sure to start apache before the upgrade (/etc/init.d/apache2 start). See bug [WWW] bug #95325 for details.
    *

      If you do not have the admin group on your system (e.g. because you upgraded all the way back from warty) it will be added during the upgrade. Make sure to add your sudo user(s) to it.
    *

      If you have pango-libthai installed, remove it before the upgrade
    *

      You may want to run /usr/lib/python2.5/site-packages/DistUpgrade/apt-autoinst-fixup.py (from the update-manager package) also to fix a common problem with the automatically installed information

---

### Post by the8thstar on 2008-05-04
If I were you, and if your hard disk allowed, I would create a specific /home partition with the liveCD, move the current /home directory contents to that new partition.

Then I would destroy the current / partition with the liveCD and move straight to installing Hardy Heron there.

I can post more info if you want to do it that way.

---

### Post by phoenix_abhi on 2008-05-04
Are u talking about installing hardy from a live cd. I have only fiesty with me

---

