---
title: "granting read/write permission to external usb drive for all users"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by newandconfused on 2012-01-02
Hello all,
I am a new Ubuntu user and I am getting a little confused( information overload...brain melting..etc)

 I have an Iomega external hd that I want all the users to be able to use.  If I reboot the hd when logged in a particular user's account then ownership switches to that user and no one else can access it.  I tried changing permissions with the gui, as admin, but it would not allow me - something to do with the fact that it is an nstf(sp??) formated drive??

Hopefully with will help with help I can get...

output from sudo ndf -T:
```

Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda1     ext4   476593176  11890016 440493548   3% /
udev      devtmpfs     2054872         4   2054868   1% /dev
tmpfs        tmpfs      824760      1112    823648   1% /run
none         tmpfs        5120         0      5120   0% /run/lock
none         tmpfs     2061896      2388   2059508   1% /run/shm
/dev/sr1   iso9660      637568    637568         0 100% /media/WXPVOL_EN
/dev/sdb1  fuseblk   1953512000 613708628 1339803372  32% /media/Iomega HDD

```


part of output  from mount
```

/dev/sdb1 on /media/Iomega HDD type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

```

---

### Post by anewguy on 2012-01-02
Can you just place the permissions you want in place of "default permissions"?

---

### Post by newandconfused on 2012-01-02
> 
Can you just place the permissions you want in place of "default permissions"?     
do you want to elaborate please?
where do you place the default permissions?

---

