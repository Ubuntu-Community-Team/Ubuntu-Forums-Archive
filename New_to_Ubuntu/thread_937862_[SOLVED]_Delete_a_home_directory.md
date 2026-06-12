---
title: "[SOLVED] Delete a home directory"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by nothingspecial on 2008-10-04
How do I delete a user entirely including their home directory.
As a previous victim of mass data loss,I want to get this exactly right.
Thanks

---

### Post by tuxxy on 2008-10-04
To delete th user account from terminal

```
sudo userdel -r username
```

Then to remove their /home

```
sudo rm -rf /home/username
```

---

### Post by Mulenmar on 2008-10-04
First, back up the data!

There's a User & Groups management tool in the System -> Administration menu. Load it, click Unlock, and put in your password. I'm pretty sure, if you're in the administrator group, that you can delete other users.

I don't know for sure if that deletes their directory as well, but if not you can sudo rmdir /home/*unluckuser* or something similar from Terminal.

---

### Post by nothingspecial on 2008-10-04
I added a child protection firefox extension to my wifes account. It means that the kids can`t visit any website without knowing the password. The trouble is that firefox will not accept that password even though I have reset it 3 times in my account.  Whatever I change the password to it won`t accept it.
 So firefox and thus her account is completely useless to her.
I have tried reinstalling firefox twice but to no avail.
 Luckily I only upgraded to hardy last night (clean install) so everything is backed up.
 I deleted her in the users and groups tab but it has no option to delete the home directory then I tried

```
sudo rm -rf ~/themissus
``` but that didn`t work.

```
sudo rm -rf /home/username
``` works thanks Tuxy 


I guess that ~/themissus tried to delete a directory in my home folder called themissus which dosen`t exist#-o anyway, thanks again.

---

