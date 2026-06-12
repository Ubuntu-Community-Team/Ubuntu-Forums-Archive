---
title: "Fresh install - Ubuntu Server 14.0.4 on USB - new user not sudo"
date: 2015-12-20
forum: New to Ubuntu
---

### Post by diskothreat on 2015-12-20
Hello :)

I just installed Ubuntu Server 14.0.4 using a USB drive with unetbootin.  I created the ability to root and a username which I thought would have admin privileges.

I have two problems:
GRUB did not install on the right drive (it installed on the USB drive which was the /dev/sda.  Even with expert install, I wasn't able to install it on the /dev/sdb which housed my actual primary partition that I created).  In order to rectify that situation, I had to use a sudo command and found out that I am not in the sudoer's file.

I am hearing I cannot root because I did try that login as well as with su.

For some reason, I'm not finding any helpful verbage in my searches.

Is there a straightforward way to rectify these two issues?
1. add my main and only username to the sudoer's file
2. move/reinstall my GRUB to boot from my hard disk on /dev/sdb?

Respectfully,
Disko

---

### Post by buzzingrobot on 2015-12-20
The installer will install on the drive it has identified as /dev/sda, unless you tell it otherwise.

---

### Post by diskothreat on 2015-12-21
What was odd is that during the Expert set up, I did try to specify the other drive.  I'm sensing a deeper issue but I'm not quite sure what it is. Would the user account I was creating not come with an automatic sudo access?  Should I rerun the install without enabling the root with a password?

---

