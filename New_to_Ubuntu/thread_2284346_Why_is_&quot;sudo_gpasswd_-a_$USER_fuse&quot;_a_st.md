---
title: "Why is &quot;sudo gpasswd -a $USER fuse&quot; a step in the ubuntu community guide to sshfs?"
date: 2015-06-28
forum: New to Ubuntu
---

### Post by Raner on 2015-06-28
Why is this

```
sudo gpasswd -a $USER fuse
```

important for sshfs?

It says to do it here, but I can't figure out why: [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

The following commands successfully allowed me to mount a remote folder:


```
sudo apt-get install sshfs
sudo apt-get install openssh-server

sshfs username@xxx.xxx.xxx.xxx:/path/to/remote/folder ~/mount/point
```


I want to be sure I am not making a mistake by not running this command to put my user into the fuse group. I don't know what is gained by doing so.

---

### Post by deadflowr on 2015-06-28
I believe it will allow you to issue fusermount commands without sudo.
The benefit of being in a group is the ability to run what/how the group can.

Sidenote: you only need the openssh-server package on the server side.
No need to have it on the client side.

---

### Post by Lars Noodén on 2015-06-29
> **Raner said:**
> Why is this

```
sudo gpasswd -a $USER fuse
```

important for sshfs?

It says to do it here, but I can't figure out why: [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)



I don't see that it's necessary to either mount or unmount using sshfs.  

It's certainly not needed in 14.04.  I wonder if there are any supported versions of Ubuntu where fuse group membership is needed to use sshfs.  If there aren't any, then that section can probably be removed.

---

### Post by Raner on 2015-06-30
Ok, I will just continue to try to mount without it for now. Thanks.

And openssh-server will only be installed on the server side.

---

