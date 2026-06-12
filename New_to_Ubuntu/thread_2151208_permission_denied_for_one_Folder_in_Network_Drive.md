---
title: "permission denied for one Folder in Network Drive"
date: 2013-06-03
forum: New to Ubuntu
---

### Post by beyond2000 on 2013-06-03
hi all
Hope someone out here can help! 
For some reason i cannot access one folder in my network drive! 
it give me a error message [B]"The folder contents could not be displayed." You do not have the permissions necessary to view the contents of "109CANON".
[/B]when i manually mount the drive to a folder and cd to that folder and do :ls -al 
it give me the following

drwxrwxrwx  4 501 501 0 May 31 20:58 .
drwxrwxrwx 21 501 501 0 Jun  2 14:24 ..
drwx------  2 501 501 0 Nov 12  2011 109CANON
drwxrwxrwx  2 505 702 0 May 31 20:58 New folder

I than try to change permission by: sudo chown -R happy: 109CANON

it give me the following:
 
chown: changing ownership of `109CANON': Permission denied

Does anyone know what i can do now?

Many thanks in advance!

---

