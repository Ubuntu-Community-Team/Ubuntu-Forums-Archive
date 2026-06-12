---
title: "How to put encrypted home file on backup"
date: 2013-06-07
forum: New to Ubuntu
---

### Post by MickeyPilgrim on 2013-06-07
I understand that my entire home file is automaticly encrypted, though I don't know how well).
I would like to back-up those files on an external hard drive.
I use ubuntu 12.04.  I don't see how I'd ever recover the external backed up data if the desktop[ died.

MickeyPilgrim

---

### Post by vadimkolchev on 2013-06-07
Well, I don't remember for 12.04, but in system settings of 13.04 there is an app providing the means of backup. There you can choose folders that you want backup for and also choose destination of backups to be saved. I think it should work with encryption as well. When you want to restore, you just use the same program.

---

### Post by MickeyPilgrim on 2013-06-07
There doesn't seem to be anything like that on my 12.04

---

### Post by Paqman on 2013-06-07
How were you intending to do the backup?

In general the way home folder encryption works is that once you log in, your home folder is decrypted. So if you then copy the files to another location they won't be encrypted. Your home folder is only encrypted if viewed from anything other than your account. So if you use another machine to do the backup, you'll just get a big encrypted blob, but if you do it in your own account on your machine you'll get unencrypted data. Obviously you could also encrypt it again during the backup if you need that data protected.

---

### Post by vadimkolchev on 2013-06-07
Here I found a screenshot of 12.04 standard installation system settings. Are you sure you don't have anything like this?

[ATTACH=CONFIG]243623[/ATTACH]

---

### Post by newb85 on 2013-06-07
The default program vadimkolchev indicated is deja dup.  It includes options for encrypting the backup with a password.

---

### Post by MickeyPilgrim on 2013-06-07
I have the deja-dup, icon and all, but it says nothing about encryption. no choices, boxes references...

---

### Post by vadimkolchev on 2013-06-07
I think that as soon as you will create backup from within your account, you shouldn't have any problems with encryption. It has the choice to save to ubuntu one cloud or to some folder.

---

### Post by newb85 on 2013-06-08
> **MickeyPilgrim said:**
> I have the deja-dup, icon and all, but it says nothing about encryption. no choices, boxes references...
It won't ask about encryption until you start the first backup.  Then it will open a dialog asking if you want to encrypt and for a password if you do.

---

