---
title: "grub 2 dual boot two linux OS"
date: 2013-06-21
forum: New to Ubuntu
---

### Post by ubunt72 on 2013-06-21
This is probably a dumb question or an easy one.   But, hopefully, someone who has utilized a dual-boot setup will know but I need help understanding.  :-(

So, please be patient and I hope my description make some sense.   Please correct me and explain if something I state can be clarified easier.

I have Ubuntu installed and it boots up fine.   I have other partitions and on one, I want to install Debian sid.  As this will be an experimental OS, there's a possiblity for problems and I read that when you install binary drivers, you can hose your system - this includes dist-upgrade (upgrading everything, kernel included).   So, my idea was to have Ubuntu's bootloader be the main grub 2 and have it boot any subsequent OS installs.   Does that make sense?

Else, I believe the typical routine would be to install grub in MBR each time so that the *next* OS's grub would handle bootloading duties.   Is that right?

I think my options (if I want the Ubuntu's grub - which would already be installed in MBR, right) are as follows:
1) install Debian sid - but don't install grub at all - then run 'update-grub' in a terminal console
2) install grub in /boot or /  - not sure about that
3) install grub in MBR and then I would have to configure grub - if I wanted - OR run grub-install in Ubuntu to 're-install' grub to MBR.   
(sudo grub-install /dev/sdb) - I have Windows in the ist partition so I am wondering whether Win7 is untouched - i.e. the Windows bootloader is uneffected.)

I googled 'grub 2' + dual boot  etc etc. and read countless grub 2 tutorials, how to repair grub, how to update etc but I am still confused.   :-{

I do have Windows 7 in a partition but I hope whatever I do, it is untouched.   It's booting normally so I hope I don't do anything to upset that.   It shouldn't be a problem.   I think the main thing is making sure that both linux operating systems boot properly.   I have done typical installs in the past and I often get the Grub 15 error.   That's why I am posting this.   I am posting it in the beginner section because I feel like a beginner each time I have to deal with grub (2).   LOL!   Please help.

---

### Post by oldfred on 2013-06-21
If you get a grub 15 error that is from grub legacy, not grub2. And Ubuntu has used grub2 since 9.10.

I multi-boot but do have multiple hard drives and several flash drives. Each MBR boots a different install, but my larger sdc drive has many Linux installs. My main working install is usually the one I use to boot everything else, but sometimes I just install to another drive. 

Best to install grub somewhere as Ubuntu's grub2's os-prober uses the grub.cfg or other similar files from other installs as its primary source of boot info. Otherwise it trys to create a default boot of a kernel.
Ubuntu does not offer to not install grub2's boot loader, but you can just install it to the same partition as your install or the partition boot sector - PBR, more as a throw away to never be used. Never install grub2 to any NTFS partition PBR as that will damage Windows. Windows has more boot code in the PBR, but grub does not normally use the PBR.

When you start to get multiple installs it can be a bit of work as you have to run sudo update grub on the other install, then boot Ubuntu and run its sudo update-grub to find the update in the other install.

If other installs are Debian based you can avoid the double update with manual entries that boot a partition not a specific kernel.

See section on boot stanza to boot partition.
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

---

### Post by ubunt72 on 2013-06-22
> Best to install grub somewhere as Ubuntu's grub2's os-prober uses the  grub.cfg or other similar files from other installs as its primary  source of boot info.
Where?!? :)

I have something like this:
  	 	 	 	   sdb1 nfs
 sdb2 ext4 – ubuntu – 100.95 GB

 sdb3 ext4  - sid – 50.63 GB  

 sdb4 extended  
 sdb5 linux swap – 8 gb
 sdb6 ext4 – 38.29  - debian ?   

sdb3 and sdb6 are available for installs

Windows and Ubuntu boot up normally.   Ubuntu is kept up to date and is 13.04.

So, if I install a new copy of Debian sid in sdb3, where do I install grub when it comes to that part of the installation?   To that PBR?   sdb3?

---

### Post by oldfred on 2013-06-22
Installing grub to the PBR of sdb3 would work.

Grub2 does remember where it installed so best to have it somewhere not otherwise used.

       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

---

