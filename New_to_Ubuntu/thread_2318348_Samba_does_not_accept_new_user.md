---
title: "Samba does not accept new user"
date: 2016-03-25
forum: New to Ubuntu
---

### Post by Alexander_Tsarev on 2016-03-25
I try to configure a samba share with dedicated user. This user should not be able to login, and is only used to access the share.
So, do the following:
Create the user
sudo adduser sr
Enter simple password
Add it to samba
sudo smbpasswd -a sr
Enter the same password
Enable the user (I guess it is not necessary)
sudo smbpasswd -e sr
Create the folder to share /storage/rsh and assign permissions
sudo chown sr:sr /storage/rsh
sudo chmod -R 755 /storage/rsh
Add the records to /etc/samba/smb.conf
[rsh]
   path = /storage/rsh
Restart samba
sudo service smbd restart

When I try to connect to this share using any client (from Android, Windows and even Nautilus on the same computer) it keeps asking me user and password, and does not accept what enter.

Interestingly, if I add myself (existing user) as a samba user, and try to connect using this account, the share becomes accessible and works well (I have read permissions).
sudo smbpasswd -a at
sudo service smbd restart

I do not understand what can be the difference between me (at) and the new user I create (sr) so that the last one does not work in samba.

---

### Post by bab1 on 2016-03-25
It all looks correct.  Have you tried configuring the share a little bit more?  You can test the share access by adding "valid users = sr" to limit the share access to only that user.  What do you get from this command```
sudo pdbedit -L
```...that should show all the *Samba* users.  Have you tried changing the password of the user "sr"?

---

### Post by Alexander_Tsarev on 2016-03-27
The pdbedit command gives me this:
at:1000:Alexander Tsarev
sr:1002:
Which looks correct.

I have just tried to change the password with
sudo passwd sr
sudo smbpasswd -a sr
sudo service smbd restart
No changes. The "sr" user cannot access the share, while "at" can. The shared folder is owned by "sr" with 755 permissions.
I also tried to create few more users and added them to samba. They also cannot access the share.

If I add "valid users = sr" to smb.conf, "sr" still cannot access, but also "at" cannot. What may be important is that trying to use "sr" (or any other new user) credentials I get the user/password request again and again on the client, while "at" just gets the access error on the share. This ensures me that the problem happens during the authentication.

Any ideas? I start to think that I have a broken Samba installation.

---

### Post by Alexander_Tsarev on 2016-03-27
Few more points on this problem...
If I add "force user = at", I can access the share using any user, which is expectable.
Using "sr", I can see the list of shares on the server. So, it obviously authenticates "sr" on this level, but not on the share level.
If I enter a wrong password, it does not let me see the list of shares, which looks right for me.

---

### Post by Alexander_Tsarev on 2016-03-27
Actually, the symptoms look the same as if the folder permissions do not let "sr" read from it. But what can be a problem there if the folder is 755 (and even owned by "sr")?

---

### Post by Alexander_Tsarev on 2016-03-27
OK, it looks the whole problem has to do with the fact that /storage is actually another HDD. If I share any folder on the main HDD - it works.

---

### Post by Alexander_Tsarev on 2016-03-27
Answering my own question, I hope it will help somebody...
The folder I tried to share (/storage/rsh) is on RAID, which is mounted at boot time to /storage folder.
The /storage folder had 700 permissions. I have no idea why it affected the share, which is /storage/rsh and is set to 755 permissions, but when I changed /storage permissions also to 755 the problem was fixed. The share works well now.
It all worked for "at" user because the /storage is owned by it, so "at" had access even with 700 permissions.

---

