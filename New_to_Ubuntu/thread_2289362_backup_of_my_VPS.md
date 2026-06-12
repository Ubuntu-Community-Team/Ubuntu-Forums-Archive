---
title: "backup of my VPS"
date: 2015-08-03
forum: New to Ubuntu
---

### Post by marchello_lippi2 on 2015-08-03
Hi all, 

How do I perform backup of my VPS ? 
I got VPS with 3 GB space, only 477M left, so I can't archivate all data at VPS. 
What else I can do to perform it?

---

### Post by SeijiSensei on 2015-08-03
Does your provider offer a backup service? 

Otherwise you should copy anything irreplaceable over to a machine at your home or office.  Take a look at: [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by marchello_lippi2 on 2015-08-03
SeijiSensei

>>> Does your provider offer a backup service? 

Nope 

>>> Otherwise you should copy anything irreplaceable over to a machine at your home or office. 

Yep, trying to do it now in mc using shell-connection. 

>>>Take a look at: [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

I tried it, but as far as I can see, it allows to copy local data into remote ssh server. I have ssh and public IP address at VPS, but I do not have public IP address at home/office. So it doesn't work for me. 

So I stick to mc+shell-connection now. 

Thanks for your reply.

---

### Post by nerdtron on 2015-08-03
> **marchello_lippi2 said:**
> SeijiSensei


>>>Take a look at: [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

I tried it, but as far as I can see, it allows to copy local data into remote ssh server. I have ssh and public IP address at VPS, but I do not have public IP address at home/office. So it doesn't work for me. 

Thanks for your reply.

rsync also allows you to copy from remote server to your local machine.

Syntax for rsync is: rsync [-options] <source> <destination>

If you need to from your remote server to your local machine, then just follow the syntax like something below:
```
rsync -avh --progress username@serverpublicIP:/folder/to/copy /mylocal/folder/backupfolder/
```

---

