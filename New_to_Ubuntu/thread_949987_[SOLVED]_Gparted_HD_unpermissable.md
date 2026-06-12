---
title: "[SOLVED] Gparted HD unpermissable"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by I-dontknow on 2008-10-16
I did a format of one hard drive with gparted, ext3.
I have three harddrives, Ubuntu is the only OS installed. 

I've restarted. I can't do anything to the hard drive I just formated.
I tried another format and it's doing the same thing.

Why is it that by default permissions are assigned only to root? 
And how do I change that?

I tried gksu nautilus in terminal, but it's not opening anything.

---

### Post by I-dontknow on 2008-10-16
Is it so hard for an answer?

---

### Post by slugboat on 2008-10-16
did you format all of your hard drives? If you formatted the one with the operating system installed on it, you may have to reinstall it.

---

### Post by Sarmacid on 2008-10-16
How are you mounting the device?

If you're using mount on console, you should try this

```
mkdir -p /mnt/mydisk
mount -o uid=1000,gid=1000 /dev/sdb1 /mnt/mydisk
```

To find out your uid and gid

```
id
```

And remember to change sdb1 for the name of the device you want to mount.

---

### Post by I-dontknow on 2008-10-16
Thanks for replying.

> **slugboat said:**
> did you format all of your hard drives? If you formatted the one with the operating system installed on it, you may have to reinstall it.

No, I just formatted one of two backup Harddrives. 
The one I am installed on I am doing nothing to.

> **Sarmacid said:**
> How are you mounting the device?

If you're using mount on console, you should try this

```
mkdir -p /mnt/mydisk
mount -o uid=1000,gid=1000 /dev/sdb1 /mnt/mydisk
```

To find out your uid and gid

```
id
```

And remember to change sdb1 for the name of the device you want to mount.

Would you mind telling me what the -p option is, and what -o uid=1000,gid=1000 means?

I am not using mount in terminal, the drive mounts, but its permissions are assigned only to root.
So I can't put anything in it.

---

### Post by slugboat on 2008-10-16
the -p option in mkdir, from the mkdir 'manpage' is:
> 
-p, --parents
              no error if existing, make parent directories as needed

any time you cant tell what option to use or what they do, you can always check it out by typing

```
$man[command name]
```

to get the manual for that command.

I think Sarmacid means for you to use the program 'id' in terminal to lookup and insert your UID and GID into the code snippet he gave you. Im not 100% on exactly what these are, but I remember having to put my uid into my bootloader program to get one of my machines to boot recently. I think its just a hex address to your harddrive? I'm not an expert exactly, but thats what i've got so far.

I've been able to mount drives using the mount command in the syntax:

```

mkdir /mnt/mydisk
mount /dev/sdb1 /mnt/mydisk
```

where you replace 'sdb1' with the sdxx tag that corresponds to that volume. I bet Sarmacid's method is a bit more precise though, it gives mount more information about the volume.

The permissions command is:

```

$sudo chmod 777 /mnt/mydisk

```

sudo gives you root privlidges, and will ask for your password, and chmod changes the permissions, in this case, to read, write, and execute permission for the user and the group. 755 is a safer choice, but the explanation can be found in chmod's manpage. I'm sorry if this isn't the best way to do this, but its the way I know how.

---

### Post by I-dontknow on 2008-10-16
> **slugboat said:**
> the -p option in mkdir, from the mkdir 'manpage' is:


any time you cant tell what option to use or what they do, you can always check it out by typing

```
$man[command name]
```

to get the manual for that command.

I think Sarmacid means for you to use the program 'id' in terminal to lookup and insert your UID and GID into the code snippet he gave you. Im not 100% on exactly what these are, but I remember having to put my uid into my bootloader program to get one of my machines to boot recently. I think its just a hex address to your harddrive? I'm not an expert exactly, but thats what i've got so far.

I've been able to mount drives using the mount command in the syntax:

```

mkdir /mnt/mydisk
mount /dev/sdb1 /mnt/mydisk
```

where you replace 'sdb1' with the sdxx tag that corresponds to that volume. I bet Sarmacid's method is a bit more precise though, it gives mount more information about the volume.

The permissions command is:

```

$sudo chmod 777 /mnt/mydisk

```

sudo gives you root privlidges, and will ask for your password, and chmod changes the permissions, in this case, to read, write, and execute permission for the user and the group. 755 is a safer choice, but the explanation can be found in chmod's manpage. I'm sorry if this isn't the best way to do this, but its the way I know how.

Thanks very much.
Now that I've read over your very helpful post, I believe I know how to do it the way I want it.
By default Ubuntu mounts to /media/ so I edited the chmod command to let me use the mount in media.
I had done your mnt before. Which means there's a copy in the /mnt/ dir.
This will disappear after restart I'm hoping?

I tried to do umount commands but I don't know too much about it.
Yes, I should start getting into man pages. :D

Thanks a lot.

---

