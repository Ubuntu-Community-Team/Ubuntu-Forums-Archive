---
title: "[SOLVED] Can only access Sudo by hitting ESC at Startup"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by maninsitu on 2008-10-21
I can only access Sudo at startup by hitting the Escape key and selecting recovery mode.

I found this out after much research on how to add users. I had done a clean install over Gutsy and Windows XP. Established myself as the first user during the install and provided a password for the root. When at the desktop and trying to use the graphical interface for adding users, I was not able to have the system authenticate my password. I tried both my user password and the root password.

After reading how to add users in Sudo, I tried doing it in terminal - it didn't work. I then read somewhere how to restart, hit esc just before Ubuntu loads and select recovery and sure enough on the bottom of the screen a terminal session started and I was able to succesfully add a user.

Now I have the same problem with the update manager. Help...I have tried apt-get in Sudo to no avail!!!:(

---

### Post by pytheas22 on 2008-10-21
Ubuntu doesn't have a root password because the root account doesn't really exist.  When the installer asks you for a password, it's asking you for the password for the first user of the system.  By default, this user gets administrator privileges, meaning that she can use sudo.  But this is not the root account.

Are you positive that the password that you're entering is correct and that you're a member of the 'admin' group (type 'groups' at a command line and it will tell you which groups you belong to)?  It's possible that your administrator privileges were removed somehow, which is why you can't sudo.

Also, are you sure that you can't use sudo from the command line?  If you type 'sudo -s' and enter your password when prompted, does it reject the password repeatedly?  Note that you don't actually see anything on the screen when you're typing your password; perhaps this is where you're getting hung up?

---

### Post by maninsitu on 2008-11-09
> **pytheas22 said:**
> Ubuntu doesn't have a root password because the root account doesn't really exist.  When the installer asks you for a password, it's asking you for the password for the first user of the system.  By default, this user gets administrator privileges, meaning that she can use sudo.  But this is not the root account.

Are you positive that the password that you're entering is correct and that you're a member of the 'admin' group (type 'groups' at a command line and it will tell you which groups you belong to)?  It's possible that your administrator privileges were removed somehow, which is why you can't sudo.

Also, are you sure that you can't use sudo from the command line?  If you type 'sudo -s' and enter your password when prompted, does it reject the password repeatedly?  Note that you don't actually see anything on the screen when you're typing your password; perhaps this is where you're getting hung up?

Typing SU in Terminal took care of it. My sudo password was different than my User password strange!? Anyways, I have now updated to Intrepid and that took care of the passwords etc. Thanks for your help! :D

---

