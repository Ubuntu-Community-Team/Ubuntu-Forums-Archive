---
title: "disk drives not mounting regualrly"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by rajeshkhetan@vnrvjiet.inf on 2008-10-04
hiiii

i use both xp and also ubuntu 8.04. my disk drives are mounted in half of the ocations and is not mounted on other half of the ocations. can anyone tell me why it happens and why the settings are different in different boots????? why sometime something is visible and sometimes something is not visible(disks)???? also when am creating a new user, the user is being created. but when i close the user and group and check it(by relogin or going to user/groups), the user wont be available.

---

### Post by kd420 on 2008-10-06
You need to be more specific. If you're dual booting Windows/Ubuntu, Windows won't see ext3 filesystems (the default format for Ubuntu). If you want to open a NTFS partition (your Window's one etc.) in Ubuntu, it has to be mounted. Go to Places and select the drive, it should mount itself. 

Also, what do you mean by close the user and group? When you create it from another user, can you log out and login with the new user? Does it give you an error about the login name etc?

Try the command:

id <username you created>

and see if it shows the user there.

---

