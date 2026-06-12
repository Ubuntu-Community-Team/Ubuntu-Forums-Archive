---
title: "cannot unlock any more!"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by plntbrt on 2008-10-25
hi,
I have done a mess. With the "users settings" I have disabled my only non-root user to administer the system. So when I try to "unlock" something I get an error message: "could not authenticate, an unexpected error has occurred"
HELP!!!

---

### Post by dracayr on 2008-10-25
try to execute 

gksudo users-admin

in a terminal. this opens the user settings with root rights. I don't know what exactly is meant with "administer the system", so I don't know if you can use sudo or gksudo. can you?

ok, I took a look at the /etc/sudoers file and I guess that the "administer the System" option puts a user into the "admin" group. So, boot up in recovery mode, choose the option "root prompt", and enter 

usermod -a -G admin yourUserName

then reboot.

dracayr

---

### Post by plntbrt on 2008-10-25
I tried, but if I use the password for "root" I get a "wrong password" message (but I am absolutely certain about the root password). If I try with the user's password an error message says that "sudo" does not allow me to run the program...:confused:

---

### Post by shifty_powers on 2008-10-25
try:

[http://www.ubuntux.org/how-to-change-the-root-password-in-ubuntu](http://www.ubuntux.org/how-to-change-the-root-password-in-ubuntu)

---

### Post by jerome1232 on 2008-10-25
You need to boot into recovery mode (mash esc while the computer is starting) and select recovery mode from the grub menu, then you'll select drop to root shell, since root has no password in Ubuntu (it's disabled excepy for recovery mode) you'll be dropped to a root shell. Now enter that command dracayr gave you to put yourself back in the admin group.

Enabling the root account is _not_ supported in Ubuntu and can actually break things so follow that tut shifty_powers gave you at your own risk. We aren't even supposed to be linking that stuff here.

---

### Post by plntbrt on 2008-10-25
HI,
I tried the
usermod -a -G admin yourUserName
option and it worked :)
thank you!!

---

