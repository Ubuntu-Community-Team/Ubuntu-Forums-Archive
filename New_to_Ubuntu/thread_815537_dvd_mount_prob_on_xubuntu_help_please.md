---
title: "dvd mount prob on xubuntu help please"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by wltdwiz on 2008-06-01
hi all 
anyone know how to get my dvd/cd writer to mount in xunbutu ?
ive searched but no answers.
i put disk in but it will not show it
thanks in advance

---

### Post by corkscrew on 2008-06-01
I had a problem mounting hard drives at boot time if you read this it should help you
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

I used the easy method being a newbie myself which is to install and use the device manager pysdm

---

### Post by Prospero2006 on 2008-06-01
Open up a terminal and type

```
 
dmesg

```

That will give you a lot of output, but you can filter through it with grep.

Try this as an example:
```

dmesg | grep dvd

```

In all likelyhood you'll be able to identify your cdrom or dvd as either
/dev/cdrom
or
/dev/dvd

So, in order to mount it manually you need to create a directory and then tell the system to 'mount' the dvd in that directory.

```

sudo mkdir /mnt/cdrom
mount /dev/cdrom /mnt/cdrom
cd /mnt/cdrom
ls

```

That will hopefully allow you to see the directory contents on the cd.
Obviously, you would substitute /dev/dvd for /dev/cdrom 
if it is a dvd.

---

### Post by wltdwiz on 2008-06-01
thanks for the info but the terminal asks for my password but will not let me type it in odd problem:(


> **Prospero2006 said:**
> Open up a terminal and type

```
 
dmesg

```

That will give you a lot of output, but you can filter through it with grep.

Try this as an example:
```

dmesg | grep dvd

```

In all likelyhood you'll be able to identify your cdrom or dvd as either
/dev/cdrom
or
/dev/dvd

So, in order to mount it manually you need to create a directory and then tell the system to 'mount' the dvd in that directory.

```

sudo mkdir /mnt/cdrom
mount /dev/cdrom /mnt/cdrom
cd /mnt/cdrom
ls

```

That will hopefully allow you to see the directory contents on the cd.
Obviously, you would substitute /dev/dvd for /dev/cdrom 
if it is a dvd.

---

### Post by wltdwiz on 2008-06-01
thanks this seemed to help i can access disks now 


> **corkscrew said:**
> I had a problem mounting hard drives at boot time if you read this it should help you
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

I used the easy method being a newbie myself which is to install and use the device manager pysdm

---

### Post by Maestro23 on 2008-06-01
You password is not displayed when you type it in the terminal.

Type it and hit Enter.

---

### Post by wltdwiz on 2008-06-01
thanks that has been driveing me nuts 
but now it says desktop:~$ mount /dev/cdrom /mnt/cdrom
mount: only root can do that

---

