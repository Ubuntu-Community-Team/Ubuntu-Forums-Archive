---
title: "small problem with partitions"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by JeppeM on 2008-06-02
Hey all,

I made a small mistake when i reinstalled Hardy on my freshly formatted disk earlier today... I made 4 primary partitions: one for /, one for swap, one for /boot and one for /home - I only used around half my harddisk space, and when i now try in gparted to make a new partition, it tells me that i cant make any more partitions unless i make an extended partition (or something like that).

My question is: Is there any way to move /home to the / partition, so i can make the last partition into an extended partition and from there make some logicals :)

thanks a lot - Loving Hardy btw :)

---

### Post by dracayr on 2008-06-02
there's probably a better way, but I think this should work:

to put home on /:

first mount your root partition a second time:

```
sudo mkdir /mnt/*replace with partition name*
sudo mount /dev/*replace with partition name*  /mnt/*replace with partition name*
```


then, copy your home directory (assuming you are in your home directory):

```
tar cf - ..|(cd /mnt/*replace with partition name*/home ; sudo tar xfp -)
```

then to prevent hardy from mounting your /home partition, comment the line regarding your /home partition in /etc/fstab (put a '#' before it)

on the next boot, /home should be on /

dracayr

---

### Post by JeppeM on 2008-06-03
thanks a lot...

It didnt work exactly like we wanted it to though, i somehow was left without any file in neither /home/jeppe or in /mnt/sda4/jeppe - Which means that somehow, my entire home folder was deleted :(

I get it fixed via. the recovery mode (dropped to shell, edited /etc/fstab to unmount sda4 where /home was, and then userdel + useradd + passwd), so now i at least dont have /home mounted on another partition now. 

do you know of any way to recover the files that got deleted from the partion?

---

### Post by dracayr on 2008-06-04
hi,

they should still be on the previous home partition (If you haven't formatted that yet). I've just tested that tar commmand. You're right, It didn't work. I've got it from a book about linux, so I assumed it would work... No time now, but I'll look for the error.

EDIT:tried again now, and somehow it worked this time. In my book, the command is written with spaces in between the brackets, pipe, letters, etc., but I don't think that should be the problem. I think the reason could have been that some of the configuration files etc. changed while they were "tarred". Now that you have the files on a seperate partition, that shouldn't be the case. However, you can't just replace the files in your home directory while you're logged in, because some of them are needed by various programs (those files are in you home directory, but you can't see them in the file browser unless you press Ctrl+H). So, I guess you would have to log in as another user, and mount the previous home directory on /mnt/*partition name* just like you did with the root partition in my last post. then execute the following as root (you might have to set a root password first, do this with ```
sudo passwd
```. To change to root, type ```
su -
```)
```
cd /mnt/*partition name*/*your username*
tar cf - . | ( cd /home/*your username* ; tar xfp - )
```
then, If you want to save the home directories of other users, log in as yourself again, and execute the same commands, except that you replace *your username* with the username of the user whose files you want to save.

dracayr

---

