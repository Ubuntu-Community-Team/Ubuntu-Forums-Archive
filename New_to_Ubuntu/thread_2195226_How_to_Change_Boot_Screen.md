---
title: "How to Change Boot Screen"
date: 2013-12-23
forum: New to Ubuntu
---

### Post by Rick St. George on 2013-12-23
Tried to modify file in plymouth themes that points to the pic file to be loaded, to change it to another pic to be loaded. 

But admin access is apparently not high enough to modify the file.

Any suggestions? Running Xubuntu 11.10

Rick

---

### Post by claracc on 2013-12-23
xubuntu 11.10 has reached its end of life support. It means you are taking security risks, since you are not going to receive any security update. Also the repositories from which you can install software has been removed from the server.

I suggest to install a supported release as 12.04, 13.04, 13.10 and then you can try plymouth manager: [http://www.ubuntugeek.com/plymouth-manager-simple-tool-to-change-splash-screen-themes.html](http://www.ubuntugeek.com/plymouth-manager-simple-tool-to-change-splash-screen-themes.html) in order to change the screen.

---

### Post by Rick St. George on 2013-12-26
That just changes the theme, not the boot screen picture.

I have several systems, and would like to change the boot picture on all of them. 
ubuntu-studio 12.04 precise (laptop)
 xubuntu 11.10 (tried to upgrade due to video problems - will not boot, screen keeps going in and out)
Xubuntu 13.10
ubuntu-studio (desktop)

I must not have "administrator" access like I thought on these machines.  
How can one change/modify files?

Any suggestions?

---

### Post by yoreei.grigorov on 2013-12-26
The easiest way is to open /etc/default/grub and change GRUB_BACKGROUND so that it points to your background picture

---

### Post by Rick St. George on 2013-12-26
Thanks yoreei - but as mentioned, I don't have permission to change a file. 
How do I do that? Superuser? is that what SUDO means?
Sorry to be such a Newbie, should buy a book and read it.

---

### Post by rburkartjo on 2013-12-28
open terminal and run this command then you will be able to edit
sudo gedit /etc/default/grub 
after you run the command it will ask you for you password. enter
note the picture you want to use needs to be in your home folder
here is a copy of mine
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=-1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_BACKGROUND="/home/ray/8ukijh.jpeg"
 note the last line and you must use the quotes
save changes and while in the terminal type  sudo update-grub .
that should do it

---

### Post by Rick St. George on 2014-01-14
Worked ... Problem Solved 

Thanks
Rick

---

### Post by sahabcse on 2014-01-22
THis steps helped me lot. Thanks rburkartjo

---

