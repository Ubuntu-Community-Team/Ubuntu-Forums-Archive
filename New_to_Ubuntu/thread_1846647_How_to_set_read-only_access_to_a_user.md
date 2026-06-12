---
title: "How to set read-only access to a user"
date: 2011-09-19
forum: New to Ubuntu
---

### Post by whiteleech on 2011-09-19
Hi there,
 
I'm trying to set up read-only access for a user. I've just set up ubuntu on a VPS, installed vsftpd, created two users, disabled ssh access and set their home directories to the same thing and restricted them both to only that directory. Is there a way I can allow User1 to have read/write permissions on the ftp and User2 to have read-only permissions?
 
Cheers!

---

### Post by Lisiano on 2011-09-19
You can set the permissions to 744 which means Owner (User1) can both Read, Write and Execute while group members and everyone else (User2) can only Read. (To execute make it 755)
Can be done by issuing this command inside the directory
```
chmod 744 -R ./
```
Do note that this is a bit dangerous if you run it from the wrong directory so I recommend that you substitute ./ with the full path to the directory.
Also to make User1 the owner and set User1 as the group use this
```
chown User1:User1 -R ./
```
Again I recommend you set it to the full path instead of ./

---

### Post by P05TMAN on 2011-09-19
> **whiteleech said:**
> Hi there,
 
I'm trying to set up read-only access for a user. I've just set up ubuntu on a VPS, installed vsftpd, created two users, disabled ssh access and set their home directories to the same thing and restricted them both to only that directory. Is there a way I can allow User1 to have read/write permissions on the ftp and User2 to have read-only permissions?
 
Cheers!

Anyone, correct me if I'm wrong, but I think that you would have to set up two separate groups for each user, then set permissions to the directory for each group.

---

### Post by P05TMAN on 2011-09-19
> **Lisiano said:**
> You can set the permissions to 744 which means Owner (User1) can both Read, Write and Execute while group members and everyone else (User2) can only Read. (To execute make it 755)
Can be done by issuing this command inside the directory
```
chmod 744 -R ./
```Do note that this is a bit dangerous if you run it from the wrong directory so I recommend that you substitute ./ with the full path to the directory.
Also to make User1 the owner and set User1 as the group use this
```
chown User1:User1 -R ./
```Again I recommend you set it to the full path instead of ./

+1

I was making it too difficult. Thanks for the tutorial & I apologize.

---

### Post by whiteleech on 2011-09-19
Thanks for the reply!
 
Ok I've changed the permissions (chmod 744 -R /home/user1), changed user2's group to user1 (usermod -g user1 user2) and then set user1 as owner (chown user1:user1 -R /home/user1)
 
Also, under /etc/passwd I changed (manually inserted which may be the problem?):
 
user1:x:1003:1003:,,,:/home/user1:/etc/ftponly
user2:x:1004:1003:,,,:/home/user1:/etc/ftponly
 
to 
 
user1:x:1003:1003:,,,:/home/user1:/etc/ftponly
user2:x:**1003**:1003:,,,:/home/user1:/etc/ftponly
 
 
.. but when I log in to the ftp as user2 I can delete files. Have I gone wrong somewhere in the above?
 
 
Cheers
 
 
ps :x = : x

---

### Post by Lisiano on 2011-09-20
You just stated what you did wrong, files are owned as UID and GID, User and Group ID, you changed User2 so that he has User1s UID, thus he can delete/modify files, also if you set it up as 744 (rwxr--r--) then you don't need to make them from the same group. If you don't want some other users (Say User3) to read the files, then you can instead of adding User2 to User1s personal group (He can then read files that you want only User1 to see), you can create a group with both of them (Cool_peeps) and assign the permissions as 740(rwxr-----)
To create a group and add both of them to the group
```
sudo addgroup cool_peeps
sudo adduser user1 cool_peeps
sudo adduser user2 cool_peeps
```
Now change back user2 (Manually) to his own UID and GID
Now just chmod the files so they are owned by User1 and the group Cool_peeps
```
sudo chmod user1:cool_peeps -R /home/user1
```
Also, I forgot to mention, without the execution bit (x) you can't execute NOR open folders. So the recommended would be to set 750, allowing User1 to read/write/execute, User 2 to read/execute and everyone else to just plainly look at the /home/user1 folder and wonder what is in it.
So, do this on directories (Including the home)
```
sudo chmod 750 -R /home/user1
```
This on files that you don't want User2 to execute (Read as run programs/scripts)
```
sudo chmod 740 /home/user/Cool_program
```

Note: I used sudo above since I'm assuming the OP is running as his own user (Say user whiteleech) and since whiteleech can't modify files he owns, he has to call upon sudo or to constantly relogin as User1 or User2. If the OP is using user1 then sudo can be easily omitted.

Note 2: If you want to go another road (Which is probably a bit more friendly than numbers) then you can use r(ead),w(rite),e(xecute) but to do that you need to write it a bit differently. To add/remove a permission you need to specify who you add/remove the permission to u(ser), g(roup), a(ll). The syntax is easy first who then a plus (add) or minus (remove) and the permission. For example to make a file not executable by User2
```
sudo chmod g-x
```
If you want to read more on the permissions and how to use chmod, read the man pages.

---

