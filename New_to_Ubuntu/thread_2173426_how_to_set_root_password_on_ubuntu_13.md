---
title: "how to set root password on ubuntu 13"
date: 2013-09-09
forum: New to Ubuntu
---

### Post by siso3 on 2013-09-09
1, i am absolutely new to linux...have just installed ubuntu 13.... been prompted to provide root password everytime i try downloading anything or accessing my hard drives....tried to decipher from old threads but failed...can someone give me step by step guide fro ubuntu 13.
2. Also i tried to access my external hard drive which is otherwise password locked (WESTERN DIGITAL)...and failed...otherwise other pen drives are accessible.

3. Lastly in the welcome screen i get three options to log on but cant figure out where to set up log in main user / guest user acct...i have already logged in to Ubuntu 1 BUt THAT email and password doesnt work for remote log in...i m completely confused ,... some one help

harsh

---

### Post by ajgreeny on 2013-09-09
[LIST=1]
[*]The password you are being asked for is not the root password but your own user password which you set at installation and now use to login to the OS, all the info about this is detailed at [Ubuntu: RootSudo]("https://help.ubuntu.com/community/RootSudo")
[*]I can't help with encryption; I've never used it.
[*]Not sure about this, but if you just enter your user password and don't touch the user option I think the system will default to the your first user, ie the one set up at installation and therefore the one with sudo rights when needed.
[/LIST]
PS: What do you mean exactly by "remote log in" ?

---

### Post by deadflowr on 2013-09-09
Are you logging in as guest?

I ask because, beyond the need for a password when downloading and installing programs, the default user you created wouldn't need to enter a password to access external drives, as those permissions are yours from the outset.

When you installed Ubuntu, you created a first user. That first user has admin rights. It's password is in all respects, a pseudo-root password.

---

