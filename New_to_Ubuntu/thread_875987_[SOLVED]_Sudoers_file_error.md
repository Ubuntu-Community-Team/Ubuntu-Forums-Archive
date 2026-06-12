---
title: "[SOLVED] Sudoers file error"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by waterrr on 2008-07-31
Hi all,
Ive placed a auto-extracting folder into my /tmp folder and in terminal I

```
cd /tmp
su user2
sudo apt-get install ....
```

the ...'s are lines for the things I was installing and when I try to run the sudo apt-get install command I get the error

```
user2 is not in the sudoers file. This incident will be reported.
```

how can I fix this? or what's wrong?

---

### Post by eightmillion on 2008-07-31
Go to System>Administration>Users and Groups. Click on unlock and enter your password. Click on user2 and then click the properties button. Under the "User Priveleges" tab, check "Administer the system".

---

### Post by aysiu on 2008-07-31
That'll work.

Since you seem pretty comfortable with the terminal, you can also do ```
sudo adduser *user2* admin
```

---

### Post by nbayiha on 2008-07-31
You got two possibility right here.

First try this:

If you have another user with (sudo right), log in with this user and do 
```
sudo visudo
```
and edit sudoers normally , or add this user add2 in the admin group .
Secondly 
If no one else has sudo right, so reset the computer and in the beginning, get in Grub and start in single user mode (the mode where you get the console), and from there add user2 to admin . 
```
sudo adduser user2 admin
```
or visudo.

---

### Post by Twexcom on 2008-10-31
Here is how to edit the sudoers file manually: [http://www.kompulsa.com/it/linuxtips.php#sudofile](http://www.kompulsa.com/it/linuxtips.php#sudofile)

---

