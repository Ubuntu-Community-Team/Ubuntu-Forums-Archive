---
title: "How To Save /Home To USB?"
date: 2012-11-19
forum: New to Ubuntu
---

### Post by ssands10 on 2012-11-19
I upgraded to 12.x version on my netbook and it takes a long time to load to login screen, when I enter my password it "failed to load Ubuntu client". I can get to a terminal. Based on other forum comments, I need to save my /home to a USB and do a fresh install. How do I copy my /home to a USB? Thank you.

---

### Post by oldfred on 2012-11-19
Did you have multiple users?

Do you see your current /home in terminal?

Have you run full updates from terminal?

This is to copy to a separate partition but uses same commands.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)


Updates if you want to try anthing after a # is comment do not type:
       
 #if not chroot use: 

sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# fix Broken packages -f 
sudo apt-get -f install
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

---

### Post by fibercut on 2012-11-19
If you want to just save your home and do a fresh install do this..

(1)Log in as root if you cannot mount the usb as your self.
(2)cd /home

(3)tar -pcvf whatever_u_want.tar.gz /your_dir
   tar The compression program
   the -p Preserves the permissions
   the c creates
   the v stands for verbose
   the f stands for file(s)

i.e. root#cd /home   
     root#tar -pxvf peter.tar.gz /peter
     root#cp -r peter.tar.gz /path_to_usb/usb
     ***reinstall as you planned***
     ***login to new install***
     root#cd /path_to_usb/usb/
     root#cp -r peter.tar.gz /home
     root#cd /home
     root#rm -rf peter
     root#tar -xvf peter.tar.gz (This will crate dir "peter")
     root#cd peter/
     root# all done.....

This is all assuming your path to your home dir is /home

If this all works for you and you use this method vs. the other suggested method message me when you have your new install up and running and I will give you the steps to backing up your home dir once a week or month or etc to either a back up partition or network drive or ftp site. I lost a drive once and lost a lot of info so I back my home dir up once a week.

---

### Post by fibercut on 2012-11-19
Meant to type i.e. root#cd /home   
     root#tar -pcvf peter.tar.gz /peter
     
not
i.e. root#cd /home   
     root#tar -pxvf peter.tar.gz /peter

> **fibercut said:**
> If you want to just save your home and do a fresh install do this..

(1)Log in as root if you cannot mount the usb as your self.
(2)cd /home

(3)tar -pcvf whatever_u_want.tar.gz /your_dir
   tar The compression program
   the -p Preserves the permissions
   the c creates
   the v stands for verbose
   the f stands for file(s)

i.e. root#cd /home   
     root#tar -pxvf peter.tar.gz /peter
     root#cp -r peter.tar.gz /path_to_usb/usb
     ***reinstall as you planned***
     ***login to new install***
     root#cd /path_to_usb/usb/
     root#cp -r peter.tar.gz /home
     root#cd /home
     root#rm -rf peter
     root#tar -xvf peter.tar.gz (This will crate dir "peter")
     root#cd peter/
     root# all done.....

This is all assuming your path to your home dir is /home

If this all works for you and you use this method vs. the other suggested method message me when you have your new install up and running and I will give you the steps to backing up your home dir once a week or month or etc to either a back up partition or network drive or ftp site. I lost a drive once and lost a lot of info so I back my home dir up once a week.

---

