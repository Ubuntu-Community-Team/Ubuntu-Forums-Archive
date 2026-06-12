---
title: "How do I create a new user with root access?"
date: 2013-05-23
forum: New to Ubuntu
---

### Post by GumpTron on 2013-05-23
Today I got myself in a bit of trouble...

Created a new a user account, gave it Admin privileges, and then deleted the account I had when first installing the OS. I thought I was safe... I thought all i needed to do was change from a standard user to admin....it wasn't really my fault i mean, im a windos junk. Low and behold the new account was unable to run a single sudo command. I gasped! But I was able to fix it in terminal with the help of some very nice vatos, shout out to ubuntu on irc.

So, how exactly does one create a new user account with all the rooty goodness?



Ubuntu 13.04 with Xubuntu.

---

### Post by newb85 on 2013-05-23
What password did you use when attempting to sudo?  What error message did you get? 

A new administrator user should be automatically added to the sudoers file, but if for some reason it wasn't, you should be able to edit the file from a Live session.

---

### Post by p-dh on 2013-05-23
If you delete the default administrator account (or change its privileges), you can return admin goodness by rebooting to a prompt. You can get to this prompt by choosing "Recovery" from GRUB and then the "root" option from the n-curses screen. Once you have a prompt, remount the root drive with the following command (so that any changes you make will be written):
> mount rw -o remount /
Then simply readd the account to the admin and sudo accounts:
> adduser <user> admin sudo
eg. adduser usericreated admin sudo
You can use the useradd command, but it's easy to really screw everything up if you're not paying attention.
BTW, you can create a new user - and grant admin privileges with the following
> adduser <newuser>
adduser <newuser> admin sudo

Peace,
Paul :cool:

---

### Post by newb85 on 2013-05-23
I've done a little testing.  On my 13.04 system, adding a user set as Adminstrator successfully adds them to the group "admin", thus granting them sudo privileges.  However, sudo will not accept an empty password.  No password, no sudo.

If you set your new user up without a password, you do not need to drop to root or boot a Live session.  You simply need to open "User Accounts" and give your user a password.  Then sudo away to your heart's content.

---

### Post by deadflowr on 2013-05-23
> **GumpTron said:**
> Today I got myself in a bit of trouble...

Created a new a user account, gave it Admin privileges, and then deleted the account I had when first installing the OS. I thought I was safe... I thought all i needed to do was change from a standard user to admin....it wasn't really my fault i mean, im a windos junk. Low and behold the new account was unable to run a single sudo command. I gasped! But I was able to fix it in terminal with the help of some very nice vatos, shout out to ubuntu on irc.

So, how exactly does one create a new user account with all the rooty goodness?



Ubuntu 13.04 with Xubuntu.

It seems you jumped the gun.
You should have
1 mae new user
2 log out and into new user
3 test new user
4 fix or whatnot
5 finally remove old user when new user is working right.

It's truly amazing how things fail when you outright assume they'll run right as rain.

---

### Post by GumpTron on 2013-05-24
every poster has given helpful info so thank you to everybody.

deadlfowr thank you the most same for you p-dh

---

