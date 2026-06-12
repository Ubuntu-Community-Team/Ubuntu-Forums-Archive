---
title: "Can't change the group owner of a remotely mounted driv"
date: 2015-06-30
forum: New to Ubuntu
---

### Post by Raner on 2015-06-30
I run this command to mount a folder for root access only:

```
sudo sshfs [EMAIL="user@xxx.xxx.xxx.xxx"]user@xxx.xxx.xxx.xxx[/EMAIL]:/home/USER/Desktop/remote ~/Desktop/remote
```

but once it is mounted, if I try to change the folder's permissions so that another user can access (even trying to change it with root):

```
sudo chgrp -R mygroup remote

```
I receive:

```
chgrp: changing group of ‘remote’: Permission denied
```

My hope is to mount a remote drive, have a process copy some files into it, then unmount the drive.

---

### Post by dino99 on 2015-06-30
use chown first

---

### Post by Raner on 2015-07-11
I could not get chown to work either. Here are my commands:

from within /home/local-system/Desktop/:

```
mkdir 777 backups

sshfs -o idmap=user,allow_other,IdentityFile=/home/local-system/.ssh/id_rsa remote-user@xxx.xxx.xxx.xxx:/home/remote-user/Desktop/backups /home/local-system/Desktop/backups

cd /home/local-system/Desktop/backups

touch random-file

chown random-file root

*chown: changing ownership of &#8216;random-file&#8217;: Permission denied*

(try again as root)

sudo chown random-file root

*chown: changing ownership of &#8216;random-file&#8217;: Permission denied*

(try the same with chgrp:)

chgrp root random-file

*chgrp: changing group of &#8216;random-file&#8217;: Permission denied*

sudo chgrp root random-file

*chgrp: changing group of &#8216;random-file&#8217;: Permission denied*
```

---

