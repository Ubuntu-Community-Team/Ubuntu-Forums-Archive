---
title: "Making the Switch !"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by jameswhite15 on 2008-10-29
Looking to move from Ubuntu to Windows few questions:

1) Is VirtualBox safe ( If something were to go wrong could I recover my files and if so how easy/hard would this be )

2) Will it be possible to move files between XP which I hope to install on VirtualBox and Ubuntu.

3) Once its up and running I want to uninstall my previous copy of windows, how do you do this lol..

4) Currently on my laptop Ubuntu is installed on one HDD and XP on the other and I want to move Ubuntu onto the main drive. Should I just be able to put it on a flash drive and copy it over ?

Sorry about all the questions but I can't really afford to screw this up and lose any files. 

Thanks :)

---

### Post by tompickles on 2008-10-29
1 ~ VirtualBox has always worked for me. It is just a virtual machine, so yes, it is safe.
2 ~ Depending on networking setup of the virtual machine, i guess you can share files like samba. As far as Im aware, you are basically like sticking an extra machine onto you LAN, so probable, but not the easiest I don't think.
3 ~ Uninstall windows?! I take it you mean the one on your hdd, and you wanna expand ubuntu to take up the whole space? I think though please someone help me out here - you basically just expand the partition using gparted on the live cd over the top of the windows one, and then edit GRUB to remove the windows boot.
4 ~ Not sure....

Please someone help me out here! Please be aware that the vm will not run as fast as the native XP install.

---

