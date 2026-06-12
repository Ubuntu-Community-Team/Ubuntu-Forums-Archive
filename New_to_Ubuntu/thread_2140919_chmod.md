---
title: "chmod"
date: 2013-05-01
forum: New to Ubuntu
---

### Post by Peter1981 on 2013-05-01
Hi,

I have a shared folder. It is /home/HDD0/main/.
Everybody makes his/her own folder in this share.
So it looks like  /home/HDD0/main/user 1 ... user n.
I'd like to change the access to their share as they just can write it and browse it and not to execute any file they put into their share.
I used sudo chmod 666 /home/HDD0/main and in this case I have the erros - Access denied on file. Drive not found.
If I set it to 755 everything is working fine. Nobody can write/delete any other user folder/file but they can execute and I don't want this.
 Samba conf is at this share

comment = Samba server
path = /home/HDD0/main/
read only = no
browsable = yes
guest ok = no
writable = yes
valid users = user 1 ... user n

What can be the problem?

Thank you

Peter

---

### Post by clearski on 2013-05-01
> **Peter1981 said:**
> Hi,

I have a shared folder. It is /home/HDD0/main/.
Everybody makes his/her own folder in this share.
So it looks like  /home/HDD0/main/user 1 ... user n.
I'd like to change the access to their share as they just can write it and browse it and not to execute any file they put into their share.
I used sudo chmod 666 /home/HDD0/main and in this case I have the erros - Access denied on file. Drive not found.
If I set it to 755 everything is working fine. Nobody can write/delete any other user folder/file but they can execute and I don't want this.
 Samba conf is at this share

comment = Samba server
path = /home/HDD0/main/
read only = no
browsable = yes
guest ok = no
writable = yes
valid users = user 1 ... user n

What can be the problem?

Thank you

Peter

You could try

```
sudo chmod -R 766 /home/HDD0/main
```

That will set Write and Read permissions for the Group and for Others. As owner, you will have full permissions: read, write, execute (7).
If you don't want Others to have any access if they're not part of the group who's supposed to access the files, then try

```
sudo chmod -R 760 /home/HDD0/main
``` 

Note that a 755 permission, as you wrote, allows users to execute files.

I don't run samba, but a test with regular folders and files worked for the instructions above. I don't know if Samba config can override these permissions.

---

### Post by Peter1981 on 2013-05-01
Thanks,

But I want everyone just write into his/her own folder, make new folders, copy files. Not execute at all.
So I tried 644 as owner can read and write his/her own folder and the others just can read. But I get the same error always.

---

### Post by nerdtron on 2013-05-01
You'll really get the same error as long as you use a 4 in the permissions because a folder, for it to be opened or accessed needs to be declared as executable. 
What are you restricting them to execute? scripts or something? By default when a parent folder is created and wth permissions 777, everyone will be able to read, write, and execute (access) that folder. Now start creating a file inside that folder and type ```
ls -l
```

(I'm not in my linux box right now to test but I think the files inside that folder will only have read and write permissions.)

---

### Post by Peter1981 on 2013-05-01
Thanks,

But I want everyone just write into his/her own folder, make new folders, copy files. Not execute at all.
So I tried 644 as owner can read and write his/her own folder and the others just can read. But I get the same error always.

I tried many chmod now and the share works only with the 755 and 555. If I use anything else I get the Access denied error.
555 means read and execute but I was able to write.

---

### Post by nerdtron on 2013-05-01
Another option is to use the the permission 700. Then use chown command to change the owner of the folder for each username. This way, only the owner of that directory will be able to access it and copy files, make new folders inside, etc. Other users will neither see it, nor accessed.

---

### Post by clearski on 2013-05-01
If your folders in the share are /mark, /paul, /caty and if all users  belong to a group (samba, for example), you might try this:

chown -R mark:samba /mark
chown -R paul:samba /paul
chown -R caty:samba /caty

Then

chmod -R 700 /mark
chmod -R 700 /paul
chmod -R 700 /caty

This way only the owner will have access to files. Actually, that is what @nerdtron suggested above.

---

### Post by Peter1981 on 2013-05-01
Thanks for the advice for you guys. 
As nerdtron mentioned the folders has to be executable and it can be a problem. Because if the folder itself can not be executable it can not be opened either.
I think I'll get stuck with the 755 and tell the users how to use it.

---

