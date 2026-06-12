---
title: "cant write or remove from media key"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-11
i can auto mount the key but i cant write or remove anything unless i use nautilus,but when i hit the properties key for the key ,permissions,
every time i choose read and write then confirm they revert to read only 
even does this in nautilus,any suggestions???
rick:confused:

---

### Post by neurostu on 2008-07-11
have you tried using:
```

sudo chown <yourlogin> <drive>

```
that sometimes works.

---

### Post by rixtr66 on 2008-07-11
ick@rick-laptop:~$ sudo chown rick:rick /media/sdb1
chown: changing ownership of `/media/sdb1': Operation not permitted
rick@rick-laptop:~$ 
:confused:

---

### Post by neurostu on 2008-07-11
Ok, i've had the same problem on some USB drives, but not on others, I'm not sure what the exact problem is though...

Try using pmount to mount the drive, I found that solves most of the problems.

---

### Post by cariboo on 2008-07-11
You can't change ownership on /media, but you can change permissions:

```
sudo chmod -R 777 /media/sdb1
```

Jim

---

### Post by rixtr66 on 2008-07-11
it didnt do any good,now i cant mount it at all:(
what about this how do i use this:rick@rick-laptop:~$ pmount -w
Usage:

pmount [options] <device> [<label>]

  Mount <device> to a directory below /media/ if policy requirements
  are met (see pmount(1) for details). If <label> is given, the mount point
  will be /media/<label>, otherwise it will be /media/<device>.
  If the mount point does not exist, it will be created.

pmount --lock <device> <pid>
  Prevent further pmounts of <device> until it is unlocked again. <pid>
  specifies the process id the lock holds for. This allows to lock a device
  by several independent processes and avoids indefinite locks of crashed
  processes (nonexistant pids are cleaned before attempting a mount).

pmount --unlock <device> <pid>
  Remove the lock on <device> for process <pid> again.

Options:
  -r          : force <device> to be mounted read-only
  -w          : force <device> to be mounted read-write
  -s, --sync  : mount <device> with the 'sync' option (default: 'async')
  --noatime   : mount <device> with the 'noatime' option (default: 'atime')
  -e, --exec  : mount <device> with the 'exec' option (default: 'noexec')
  -t <fs>     : mount as file system type <fs> (default: autodetected)
  -c <charset>: use given I/O character set (default: 'utf8' if called
                in an UTF-8 locale, otherwise mount default)
  -u <umask>  : use specified umask instead of the default (only for
                file sytems which actually support umask setting)
  --fmask <fmask>
                use specified fmask
  --dmask <dmask>
                use specified dmask
  -p <file>, --passphrase <file>
                read passphrase from file instead of the terminal
                (only for LUKS encrypted devices)
  -d, --debug : enable debug output (very verbose)
  -h, --help  : print this help message and exit successfuly
  --version   : print version number and exit successfully
rick@rick-laptop:~$ 

rick:confused:

---

### Post by rixtr66 on 2008-07-11
i originally had this working it would automount etc.i even hooked up
my psp but now i can do nothing:(

---

