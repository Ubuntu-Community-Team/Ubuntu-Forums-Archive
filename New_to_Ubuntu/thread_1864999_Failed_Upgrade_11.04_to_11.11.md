---
title: "Failed Upgrade 11.04 to 11.11"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by Slownis on 2011-10-19
I started the upgrade and walked away.  An hour or so later the power went out, so I'm not really sure where the process was intereupted, or if it finished.
 
If I allow normal boot, it gets to a black screen directly after the 'UBUNTU' with the 5 dots under it.
 
If I hold down the shift key, and choose the recovery mode, I get to a screen that has some options, but mouse and keyboard no longer work.
 
If I try recovery mode of prior linux kernels, it gets to:  init:  plymout-stop pre-start process (1177) terminated with status 1.
 
any ideas?

---

### Post by peperomia on 2011-10-19
[LEFT]If no one has any other advice, you could boot from a live cd or usb to recover your data (if you didn't back it up somewhere before you tried to upgrade) and then reinstall. 
[/LEFT]

---

### Post by forestG on 2011-10-19
Try to see if you can access one of the tty's by pressing ctrl+alt+F1...F6. if you can log in and write sudo dpkg-reconfigure -a and then  sudo apt-get install ubuntu-desktop. 

Mind that the first command is dpkg-reconfigure. reconfigure is not an option of the command dpkg. If you cannot log in in normal Ubuntu (I cannot ) try to log in to Ubuntu 2d. If you do not like it you can try to install gnome 3 by writing sudo apt-get install gnome.

---

### Post by Slownis on 2011-10-20
I got it working with a live USB for 11.10. I backed up my files to another drive and then I used the option to install/replace the 10.4 installation and it preserved my home directory files. Now I'm logging into Unity 2d - My computers a bit old and the SIS display adapter it has is not supported for 3d graphics. I'm going to give Unity a try but if I can't get used to it I'll go back to gnome.
 
One problem I am having is getting Samba working again - I use this computer as a file server. I make backups of my other windows computers to it, as well as media storage.  The is a 2nd drive (not the drive Ubuntu is on) and it is formatted NTFS, and I can't seem to get the samba shares working on it again.
 
I think under Natty I had to add a line to the samba config file that allowed setting up shares under a different user, but I can't find the command now.

---

