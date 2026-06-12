---
title: "Insufficient permission for adding an object to repository database ./objects"
date: 2010-10-10
forum: Programming Talk
---

### Post by huangyingw on 2010-10-10
Hello
    I have met a nightmare with GIT. For I could not push back my local to my smbfs mounted remote repository: /media/smb now:(:(:(.
```
//192.168.0.8/volgrp /media/smb/    smbfs   default,iocharset=utf8,username=huangyingw,
```
    You see, I try to push with command:
```
root@Ubuntu10:/home/huangyingw/myproject/git/demo# git push /media/smb/myproject/git/demo/ --all
Counting objects: 5, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 299 bytes, done.
Total 3 (delta 0), reused 0 (delta 0)
error: insufficient permission for adding an object to repository database ./objects

fatal: failed to write object
error: unpack failed: unpack-objects abnormal exit
To /media/smb/myproject/git/demo/
 ! [remote rejected] master -> master (n/a (unpacker error))
error: failed to push some refs to '/media/smb/myproject/git/demo/'

```
But, I have checked that I have "write" right, with the following simple experiment:
```
root@Ubuntu10:/home/huangyingw/myproject/git/demo# mkdir /media/smb/myproject/git/demo/objects/temp
root@Ubuntu10:/home/huangyingw/myproject/git/demo# ls -ld /media/smb/myproject/git/demo/objects/temp
drwxr-xr-x 2 huangyingw huangyingw 0 2010-10-10 00:23 /media/smb/myproject/git/demo/objects/temp

```
In this demo, the remote repository "/media/smb/myproject/git/demo/" is a bare clone one.

---

### Post by huangyingw on 2010-10-10
> **huangyingw said:**
> Hello
    I have met a nightmare with GIT. For I could not push back my local to my smbfs mounted remote repository: /media/smb now:(:(:(.
```
//192.168.0.8/volgrp /media/smb/    smbfs   default,iocharset=utf8,username=huangyingw,
```
    You see, I try to push with command:
```
root@Ubuntu10:/home/huangyingw/myproject/git/demo# git push /media/smb/myproject/git/demo/ --all
Counting objects: 5, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 299 bytes, done.
Total 3 (delta 0), reused 0 (delta 0)
error: insufficient permission for adding an object to repository database ./objects

fatal: failed to write object
error: unpack failed: unpack-objects abnormal exit
To /media/smb/myproject/git/demo/
 ! [remote rejected] master -> master (n/a (unpacker error))
error: failed to push some refs to '/media/smb/myproject/git/demo/'

```
But, I have checked that I have "write" right, with the following simple experiment:
```
root@Ubuntu10:/home/huangyingw/myproject/git/demo# mkdir /media/smb/myproject/git/demo/objects/temp
root@Ubuntu10:/home/huangyingw/myproject/git/demo# ls -ld /media/smb/myproject/git/demo/objects/temp
drwxr-xr-x 2 huangyingw huangyingw 0 2010-10-10 00:23 /media/smb/myproject/git/demo/objects/temp

```
In this demo, the remote repository "/media/smb/myproject/git/demo/" is a bare clone one.
Maybe I find the cause, but I am still don't know how to fix this trouble.
For I create soft links /home/huangyingw/myproject", and "/root/myproject", both point to the same directory: /media/volgrp/myproject.
So, if I push the same local repository, sometimes as "root", sometimes as "huangyingw", would cause this trouble.
Could someone help me, how to solve this trouble?

---

### Post by huangyingw on 2010-10-10
> **huangyingw said:**
> Maybe I find the cause, but I am still don't know how to fix this trouble.
For I create soft links /home/huangyingw/myproject", and "/root/myproject", both point to the same directory: /media/volgrp/myproject.
So, if I push the same local repository, sometimes as "root", sometimes as "huangyingw", would cause this trouble.
Could someone help me, how to solve this trouble?
Seems that the remote repository lock my local. So, till now, my stupid solution is git clone --bare a new one to replace the original remote and "central" repository.
Does someone has better solution?

---

