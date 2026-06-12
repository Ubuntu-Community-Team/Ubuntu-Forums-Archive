---
title: "Reinstall Ubuntu when using Grub"
date: 2014-01-08
forum: New to Ubuntu
---

### Post by tblom on 2014-01-08
Hi,

I have had a dual boot setup with Windows Vista and Ubuntu 11.04 for a couple of years, using grub.

For both Windows and Ubuntu, I have seperate partitions for the OS and the data.

Being a n00b, I never updated Ubuntu because this always imposes some problems, which might be easy to solve for experienced users, but not for a beginner.

Anyway now I would like to upgrade to the most recent Ubuntu version. I think the best way is to reinstall Ubuntu from scratch. However, I am worried that dual boot using grub will no longer work after this, or that other problems may arise.

Could anyone please give me a short simple step-by-step guide how to do this? Since I am a beginner, please do not assume that I know anything. Thanks in advance!

---

### Post by Mark Phelps on 2014-01-08
Sorry, don't have detailed links, but do have two pieces of advice I strongly urge you to follow:
1) Upgrading in dual-boot situations: If you have separate drives, then have the MS Windows drive disconnected whenever you do a Linux upgrade or install. This prevents the accidental overwriting of the Windows boot loader -- which will render it unbootable.  If you only have one drive, then download and install the Free version of Macrium Reflect to Windows, attach an external drive and do an image backup.  This way, if anything goes wrong with the Linux install or upgrade, you have a way of restoring the working, current version of MS Windows.
2) Upgrading Linux versions: I generally recommend against this -- unless you're going from one version to the very next.  In your case, you're going from an 11.x version to a 13.x version, and I don't believe you can do a direct one-step upgrade; instead, I think you have to upgrade again and again, from one version to the next.  So much has changed between 11.x and 13.x, that I would be very surprised if the eventual string of upgrades actually worked.  In this case, I would recommend a clean install of 13.x.  If you want to be able to restore 11.x if something goes wrong with the install of 13.x, then look into using RedoBackup -- a menu-based Linux backup tool.  You will have to go to their site, download the ISO image, and burn that to CD or USB stick.  You can't run it from inside Linux to do the backup.

---

### Post by tblom on 2014-01-08
Thank you for your reply.
Yes, indeed, I did mean a clean install, sorry if that was not clear.
I was just wondering how to do this without breaking the grub installation.

---

### Post by grahammechanical on 2014-01-08
Grub is always installed into the MBR (Master Boot Record) of the first hard disk (sda) whenever we install Ubuntu. Unless we direct Grub to be installed elsewhere. You need to choose the "Something Else" option and then tell the installer the partition where you want Ubuntu to be installed. Your concerns about Grub are not justified. Be more concerned about installing Ubuntu to use the entire disk as that will overwrite/remove Windows.

This link shows you some of the dialogs you will see:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

This link is a bit old but what you want to study is step 7-C Installation Type. Note the Change button. Having selected the partition you want Ubuntu to be installed into you click "change" and you see a dialog box. You need to select the partition to Use As Ext4 and then tick to format the partition and give it a mount point of / and then click OK. That will bring you back to the Installation Type (partitioning screen) and if you are happy that you are not going to install Ubuntu over Windows then click Install Now.

[http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/](http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/)

Do not forget to back up your data. And remember, up until the point we click "Install Now" we can back out by clicking "Cancel."

Regards.

---

### Post by Impavidus on 2014-01-08
If you don't like upgrading or reinstalling, I recommend you stick to LTS releases, like the current 12.04 or in the near future 14.04, which will be released in three months.

Upgrading to 12.04 would require 2 upgrades, via an unsupported version, which adds other complications, so a fresh install is best indeed. Grub will be reinstalled and Windows will be untouched, unless you accidentally install Ubuntu on the whole disk.

I have done some upgrades in the past (single boot 10.04&#8594;10.10&#8594;11.04&#8594;11.10&#8594;12.04; dual boot 6.06&#8594;8.04&#8594;10.04&#8594;12.04) and only that last upgrade gave a small network problem, which was easely solved with some help from here, so, in my experience, upgrades work. Of course, you could be less lucky. People claim upgrades either always work or never work.

---

