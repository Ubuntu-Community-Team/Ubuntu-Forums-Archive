---
title: "NTFS - execute permission on file"
date: 2013-10-07
forum: New to Ubuntu
---

### Post by tigerjack89 on 2013-10-07
Hi all. As the title said, I want to execute a file located in a NTFS partition. At this time, I can't be able to do this.
I mount the partition at the boot; this is the fstab line regarding the partition
```
UUID=0B7D0020211269BD /media/Data ntfs auto,rw,noatime,exec,users,dmask=000,fmask=111,nls=utf8 0 0
```

However, I can't be able to eecute file located on this disk neither change the permissions; I mean, if I type something like
```
sudo chmod +x ./abc
```
the permissions don't change.

How can I solve the problem? Also, how can I give to my user the permissions to execute files on that partition?

Thanks in advance for your reply and sorry for my bad english :)

---

### Post by Morbius1 on 2013-10-07
> UUID=0B7D0020211269BD /media/Data ntfs auto,rw,noatime,exec,users,dmask=000,fmask=111,nls=utf8 0 0

```
UUID=0B7D0020211269BD /media/Data ntfs auto,rw,noatime,umask=000,nls=utf8 0 0
```

*** You can't change linux permissions on an individual file on an ntfs partition since it has no linux permissions bits to change.
*** Mounting an ntfs partition in Linux creates a "view" such that it appears as if it has Linux permissions but globally - all files have the same permissions.
*** The "users" option turns the execute bit off on the mounted partition.
*** "fmask=111" also turns off the execute bit on all files.

"umask=000" makes all directories and files have permissions of rwx.

---

### Post by tigerjack89 on 2013-10-07
Thanks, a lot of interesting things :)
Some questions: why I have to delete exec?
Also, is it possible to give different permissions to files and folders? If yes, what does it mean? If not, what is the sense of fmask and umask for ntfs?

BTW, now it works ;)

---

### Post by Morbius1 on 2013-10-07
By default and unless overridden explicitly by other options ntfs partitions mount with the following options:
> **rw**, **exec**, **auto**, **nouser**, and **relatime.**
There's probably a few others that I can't remember at the moment but those are the important ones. There is no need to explicitly state these options unless you introduce an option that disables one of them which you want to re-enable. So if you add something like "users" ( which really has no relevance in this situation ) that disables "exec" you need to add it back. And the line in fstab is read from left to right so "users,exec" would have turned off exec and then enabled it. "exec,users" would have resulted in "exec" being ignored because it's already enabled followed by "users" which turns it off.

You can give folders and files different permissions through the use of dmask and fmask and some folks do just that. Folders have to be "executable" or else you can't open them to get to what's inside. The decision about files is up to the user.

---

### Post by tigerjack89 on 2013-10-07
Again, thanks a lot!! All make sense now :)

---

