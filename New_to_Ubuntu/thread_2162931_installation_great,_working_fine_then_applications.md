---
title: "installation great, working fine then applications will not open"
date: 2013-07-16
forum: New to Ubuntu
---

### Post by arranskye on 2013-07-16
Pc has WD. HDD 320GB running win 7 plus SSD drive 128GB running win 7 & Ubuntu . Installation on SDD drive went fine. Ext 4 plus swap, home and windows, folders. along side win 7.  Boot menu fine offering dev/sda1 windows on 320GB drive
dev/sdb1 windows on SSD drive and Ubuntu on ext 4.  All boot correctly.

Installed wireless printer, wireless adapter, updates and a few utilities from the software centre all operating ok.
Kernel is 3.8.0-26. When problems started I tried using kernel 3.8.0-19 but problems continued. Tried recovery mode in both kernels and tried and failed to run in low graphics mode.  Tried all the other recovery options but problems remained. IE   Applications open but do not operate. can only close applications using the icon in the panel. clicking on Firefox does not open but offers a dropdown box "open in new tab/window" etc. It then opens but struggles to open web pages.

I was unable to select any options in "low graphic mode" so left it at the default option to run. nothing happened until i shut down and got this:                    GNU GRUB version 2.00_13 Ubuntu U3
                                         Recordfail  load video, GFX mode $ linux_gfx_mode
                           insmod GZ10   insmod  part_msdos      insmod ext2    set root= 'hd1,msdos8' 

This appears to indicate a graphics problem however the screen is working as normal, no lines, flashes or fragmenting.
Dont know why ext 2 would cause a problem  All systems 64 bit and ram 4GB Intel G41 chipset intergrated graphics.
Please can anyone help.  thanks

---

### Post by dino99 on 2013-07-16
into a terminal, run:

sudo rm /etc/X11/xorg.*
sudo apt-get install --reinstall dkms build-essential linux-image  xserver-xorg-video-intel
sudo dpkg-reconfigure -phigh -a
(can take a while, be patient)

after logging out/in, if you still have a graphic issue (low mode), then glance at .xsession-errors (inside your /home, ctrl+h to unhide it) to find some usefull warnings/errors

note: to avoid writing error(s), better to copy/paste to the terminal

---

### Post by arranskye on 2013-07-16
hi dino,  Thanks for your response.  Before I received/read it a couple of things happened. Dont really know how or why but on shutting down a session I ended up in a difference session as a guest user. The wallpaper was different from my user account. Anyway this guest user a/c tested workin ok. Went back into my user account and it was still inoperable. Looked in disks and saw the SSD drive was not mounted.  Remounted, restarted but no improvement.
Dont understand this because I thought Ubuntu would not boot at all if the disk was not mounted.

Anyway played around with user accounts until i managed to open a new administration a/c to allow me to delete my original a/c.  All now working fine except I get a system error just after boot up, and also on every bootup a text box appears asking me to authenticate the wireless adapter and I dont know how to stop it popping up.

Followed your instructions and iv'e attached the output but sorry I dont know how to contain it in an expanding box so I have sent as attachements.   it would appear that the problems were is some way related to user accounts???  I will just continue to use the Pc as usual until I hear from you.  Again many thanks

---

