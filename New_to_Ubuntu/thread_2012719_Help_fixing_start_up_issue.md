---
title: "Help fixing start up issue"
date: 2012-06-29
forum: New to Ubuntu
---

### Post by SlayeroftheDarkForest on 2012-06-29
Okay so a while back In had upgraded to Ubuntu w/ Linux 13.0.0-generic and I used it for a little while, and one day I turned it off and when i went to turn it back on, it wont load anymore that was back in December, so I got a new computer, so now I want to reload my ubuntu os computer but it would go pass the 
the old computer is a lenovo 3000 n200
PulseAudio configured for per-user sessions 
saned disabled;edit /etc/default/saned
what can I do to fix this?
yes i tried burning a new ubuntu disk and I wanna try logging in by pressing alt+crtl+f2 but I cannot remember for the life of me the actual username and password for the account I had on it

I can go into the 
root drop
root@DFi :~# 


So I want to know how to make it load and run again but with out loosing my personal files

---

### Post by sudodus on 2012-06-29
Hi and Welcome to the Ubuntu Forums :-)

I suggest that you read this link 'How to reset your password in Ubuntu'
[[COLOR="Red"]_http://www.psychocats.net/ubuntu/resetpassword_[/COLOR]]("http://www.psychocats.net/ubuntu/resetpassword")

You can find the user names (normally the same as the home directory names, so when logged in as root, try the following command ```
ls /home
```
You can also look at all the user IDs with the following command
```
cat /etc/passwd
``` but there will be many IDs automatically generated for some purpose, and there are only a few of them that are actually users IDs for logging in.

---

### Post by SlayeroftheDarkForest on 2012-06-29
okay thank you, i got my info back, i tried to fallow these steps 

[SIZE="3"][COLOR="DarkRed"]I'm also getting this after upgrade from 11.04 to 11.10 - in order to get it to boot I had to force use of the 2.6.x kernel instead of the v3 kernel that 11.10 seems to want to use by default. I did this by editing /boot/grub/grub.cfg - not a great solution but it's a stopgap until I figure out why it's not booting with the v3 kernel and fix it.

For some reason I cannot use by USB keyboard with GRUB2 to select previous kernel from the boot menu, hence editing the grub.cfg.

edit: Exact steps I took to solve this problem:

(1) Press Ctrl+Alt+F2 as boot starts to get a login prompt. Log in.

(2) Navigate to /etc/default/

(3) Edit the grub settings: sudo vi grub

(4) Set GRUB_DEFAULT=2>2

(5) Set GRUB_TIMEOUT=10

(6) Save the file and run: update-grub

(7) Reboot.

Note, the GRUB_DEFAULT value is the 3rd sub-menu item in the 3rd submenu (counts from 0), which for me is the boot option for the latest 2.6 kernel. If you have a new install yours might not have the 2.6 kernel available, or it may be in a different place, but I hope this helps someone.
[/COLOR][/SIZE]


but i was stupidly unable to fallow  step 4 my system still gets stuck at at that, so now I am wondering if their is any way to just install over the old Ubuntu? Can I do it from the root, or is their a working way to get to the log in screen? again thank you


super-n00b

---

### Post by sudodus on 2012-06-29
> **SlayeroftheDarkForest said:**
> okay thank you, i got my info back, i tried to fallow these steps 

Have you backed up your personal data to another drive?
> 
[COLOR="DarkRed"]I'm also getting this after upgrade from 11.04 to 11.10 - in order to get it to boot I had to force use of the 2.6.x kernel instead of the v3 kernel that 11.10 seems to want to use by default. I did this by editing /boot/grub/grub.cfg - not a great solution but it's a stopgap until I figure out why it's not booting with the v3 kernel and fix it.

For some reason I cannot use by USB keyboard with GRUB2 to select previous kernel from the boot menu, hence editing the grub.cfg.

edit: Exact steps I took to solve this problem:

(1) Press Ctrl+Alt+F2 as boot starts to get a login prompt. Log in.

(2) Navigate to /etc/default/

(3) Edit the grub settings: sudo vi grub

(4) Set GRUB_DEFAULT=2>2

(5) Set GRUB_TIMEOUT=10

(6) Save the file and run: update-grub

(7) Reboot.

Note, the GRUB_DEFAULT value is the 3rd sub-menu item in the 3rd submenu (counts from 0), which for me is the boot option for the latest 2.6 kernel. If you have a new install yours might not have the 2.6 kernel available, or it may be in a different place, but I hope this helps someone.
[/COLOR]

Have a look at the following link for 'grub 2 basics'
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1195275_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275")
> 

but i was stupidly unable to fallow  step 4 my system still gets stuck at at that, so now I am wondering if their is any way to just install over the old Ubuntu? Can I do it from the root, or is their a working way to get to the log in screen? again thank you

super-n00b
Yes, there are several ways to install a new [KLX]ubuntu over the old one.

I suggest that (after you have a good backup), you boot from a CD or USB drive (for example an Ubuntu install drive) and run ***gparted*** to edit your partitions. Maybe it is enough to reformat the Ubuntu partition.

If you post the output of ```
sudo fdisk -lu
``` it will be easier to give advice.

---

