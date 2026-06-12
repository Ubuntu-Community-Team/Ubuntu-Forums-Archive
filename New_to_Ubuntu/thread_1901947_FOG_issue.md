---
title: "FOG issue"
date: 2011-12-29
forum: New to Ubuntu
---

### Post by je171 on 2011-12-29
Hello all,
 
I just joined this forum in my search for troubleshooting answers and figured I'd make a post while I continue looking.  I just installed 64 bit Ubuntu Server 11.10, as well as the latest version of FOG (trying to set up PXE Boot Imaging at my Internship).
 
I am at the point of the install of FOG where I need to edit the config.php files for mysql and fog, to enter the password info.  When I type 
gksu gedit /var/ww/fog/commons/config.php  I am prompted for a password (even though I am on the admin account).  The install never had me set a root password, so I don't know the password to use for the elevation prompt...is there a default root password for Ubuntu Server 11.10 in 64 bit?
 
Thanks!
 
Jeremy

---

### Post by Sempa on 2011-12-29
I could be all wrong, but I think gksu is not asking for your root password but rather for the password to your admin account!

---

### Post by je171 on 2011-12-29
I did type in my admin account password, it won't accept it.  The only 2 passwords I had to enter during the install were the admin account password, and the mysql password.  It will not accept either of them.  I even tested by going to user accounts to try and change the password, to see if I was typing the admin password right.  And I am.

---

### Post by Sempa on 2011-12-29
Okay, what if you try using sudo instead of gksu?

---

### Post by grahammechanical on 2011-12-29
Perhaps you do not understand how passwords work in Ubuntu. Here is a link:

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

When you installed you were surely asked to set up a user account and a password for it? I am sure you were asked to give a user name and a password. That is the password that is required.

In Ubuntu even though we are set up with administrator privileges we are not actually the administrator until we try to do something that requires administrator privileges. Then we enter our log-in password and we become the administrator for the duration of that task. Then we revert back to being a standard user. This is a more secure way of working that Ubuntu applies.

With the command gksu gedit you are loading the Gedit editor and giving it administrator powers. This mean you can edit system files that normally are protected from being edited or deleted as it may break the system. This is why you are asked for a password. It is your log-in password, believe me.

When you close that session of Gedit the editor will then become a standard user's editor unable to edit system files.

This way of working may seem strange but it means that you do not have to log in as root and then for security log out and log back in a standard user. It also means that someone cannot take over your session and have administrator privileges.

By the way, when you type in the password it will not be echoed/printed on the screen for security reasons but it will still entered into the system.

Regards.

---

### Post by je171 on 2011-12-29
I tried sudo and su as well.  It won't take the admin login password for ANY elevation prompt.  I made this all on VMware with an .iso so I'll just delete and try a reinstall, using "password" for all the passwords.  And just change them later.  We'll see if I run into the same issue.

---

