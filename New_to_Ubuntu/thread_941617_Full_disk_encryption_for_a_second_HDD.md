---
title: "Full disk encryption for a second HDD"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by prius on 2008-10-08
Hello all,

  I installed second HDD and mounted it as /PERSONAL. There are some files on the second HDD already. Can anyone guide me or point me to a reference about how I do a full disk encryption on the second HDD (/dev/sdb). I would like the first and main HDD left as it is. I looked at a number of forum threads and they all seem to suggest that the encryption was done at setup time (and I have already set it up and have files on the disk). It is not a big deal to remove the files and copy them back to /dev/sdb, but it would be great not to have to do that. 

Thanks a lot.

---

### Post by Pelham123 on 2008-10-08
Have a look at 

[http://www.truecrypt.org](http://www.truecrypt.org)

There is some documentation to read and follow, and yes, if you want a full disk encryption you will have to move the files off the drive first.

---

### Post by jerome1232 on 2008-10-08
You could also use luks; That's what is used in the installation procedure.

you will need the cryptsetup package

edit: Looking at truecrypt I think I'll start using that on some of my external media, seems like you can make it pretty portable and OS transparent.

---

### Post by bodhi.zazen on 2008-10-08
+1 Truecrypt

You may also LUKS : [http://feraga.com/node/51](http://feraga.com/node/51)

Or encfs : [http://www.movingtofreedom.org/2007/02/21/howto-encfs-encrypted-file-system-in-ubuntu-and-fedora-gnu-linux/](http://www.movingtofreedom.org/2007/02/21/howto-encfs-encrypted-file-system-in-ubuntu-and-fedora-gnu-linux/)

---

### Post by crispy_420 on 2008-10-09
I second truecrypt...

---

### Post by hyper_ch on 2008-10-09
if you want to use luks/dm_crypt, start at step V here: [http://www.howtoforge.com/ubuntu_dm_crypt_luks](http://www.howtoforge.com/ubuntu_dm_crypt_luks)

And maybe also that one here:
[http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile](http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile)

---

