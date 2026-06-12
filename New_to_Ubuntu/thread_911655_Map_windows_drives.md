---
title: "Map windows drives"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by fawzley on 2008-09-05
How do I map windows drives into Linux?

And how do I share Local Ubuntu drives with windows PC's?

Thx, Fawzley

---

### Post by bobbob1016 on 2008-09-05
First, as many people would say, search around before posting, but we all make mistakes from time to time, so read below.

Install samba, "sudo apt-get install samba".  Then you have to add the shared drive to your /etc/fstab file.  I made a file in my home folder called .smbcredentials, with text edit.  I put my username and info in that file like this:

username:username
password:password
domain:domain

Replace the second username, password, and domain with your username, password, and domain.  Domain is usually mshome or workgroup.

My smb line in my fstab is in the form of:
//Share-IP/Share /media/share cifs rw,credentials=/home/ian/.smb-credentials 0 0

Replace Share-IP with the IP address of the computer with the share.  Replace Share with the folder you want to share.  Replace /media/share with the place you want the drive mounted.

To share the folder from Ubuntu to XP, right click the folder and do Sharing Options, and check the Share this folder box, check Allow other people to write in this folder if you want, and Guest access if you want that.

---

### Post by orpheus07 on 2008-09-05
after installing samba, install the nautilus-share extension. 

```
sudo apt-get install nautilus-share
```

then you can share your files by just a right click->"Sharing Options" in your Ubuntu box.

As for mapping network drives, i don't think you can do this easily... I did this before by using **smbmount**. you have to install smbfs first before you can use it:

```
sudo apt-get install smbfs
```

as bobbob1016 said,search the forums, i'm sure someone have asked this question before.

---

