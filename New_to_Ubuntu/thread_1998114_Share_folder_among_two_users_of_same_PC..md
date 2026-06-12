---
title: "Share folder among two users of same PC."
date: 2012-06-06
forum: New to Ubuntu
---

### Post by vinodm on 2012-06-06
Hello Folks, 

How to share a folder to all the users in Ubuntu, Can I create some folder outside "home" folder and access it by all users ?

---

### Post by HermanAB on 2012-06-06
Make a directory and change the group to something that all users are members of such as 'users' and make it 'setuid' and 'setgid' (+s), so that all new files will aquire that user and group setting.

---

### Post by Morbius1 on 2012-06-06
**[1] Create a folder such as /home/Common**
```
sudo mkdir /home/Common
```**[2] Change permissions. This depends on what you mean by "shared":**
[COLOR=Blue]*This will allow all users to add to and delete any file but only be able to read and not write to someone else's files:*[/COLOR]
```
sudo chmod 0777 /home/Common
```[COLOR=Blue]*This will do the same thing as above but only the owner of the file can delete the file ( the "1" is a "sticky bit" ):*[/COLOR]
```
sudo chmod 1777 /home/Common
```[COLOR=Blue]*If you want the ability to actually write to another users files then things get more involved:*[/COLOR]
** Change the group of the folder to say for example, plugdev:
```
sudo chown :plugdev /home/Common
```** If your users are not members of the plugdev group they will need to be added:
```
sudo gpasswd -a morbius plugdev
```** Then you need to change the default umask so that files are added as 664 and not 644:

[COLOR=Blue]***NOTE**: The default umask is already at 002 if you are running 12.04 so this step is not required.*[/COLOR]
Edit /etc/profile as root:
```
gksu gedit /etc/profile
```Find the line at the bottom that references umask and change it to:
```
umask 002
```** Then change permissions of the shared folder:
```
sudo chmod 2775 /home/Common
```OR
```
sudo chmod 3775 /home/Common
```"2775" - All plugdev users will be able to add and delete all files and will have read/write access to all new files. The "2" is a setgid bit.
"3775" - All plugdev users will be able to add to but delete only their own files and have read/write acces to all new files. The "3" is a "sticky" (1) + "setgid" (2) =3.

---

