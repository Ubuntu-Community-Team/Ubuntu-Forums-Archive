---
title: "How to stop a desktop icon appearing for shared drives that aren't there?"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by mingle on 2008-07-15
Hi,

I have a few windows shares mapped using Samba and they work fine.

However, when my network shares are not there (ie: I don't have my XP boxes switched on) the icons still appear on the desktop.

Is there any way to set up the shares so that they're only mounted when the shared drive is actually online?

Cheers,

Mike.

---

### Post by joshsmith on 2008-07-18
you could write a small shell script to do this

if you use te program gvfs-ls to show you in the share is online, and then mount it if it is. ie something like
```

if (gvfs-ls smb://{here goes the path to the share}
then gvfs-mount smb://{here goes the path to the share}
fi

```
the mounted share will then appear on your desktop, if it is online. you could put this as a script and add it to your session start up

or for proper mounting and unmounting,  when things change:
```

while [ 0 ]
do
if (gvfs-ls smb://{here goes the path to the share}
then gvfs-mount smb://{here goes the path to the share}
else gvfs-mount -u smb://{here goes the path to the share}
fi
sleep 1m
done

```

---

### Post by alpdo on 2008-10-10
ive been reading about gvfs... and im interested to learn about how to use it... im a newbie to ubuntu... 
can i mount network share using gvfs to other mount point rather than in ~/.gvfs ????:confused:

---

### Post by alpdo on 2008-10-10
and if i can mount it to other mount point... how can i umount it???? heheheh

---

