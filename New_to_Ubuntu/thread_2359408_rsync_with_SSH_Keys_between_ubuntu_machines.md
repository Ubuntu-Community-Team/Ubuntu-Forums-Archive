---
title: "rsync with SSH Keys between ubuntu machines"
date: 2017-04-23
forum: New to Ubuntu
---

### Post by eddiefiggie on 2017-04-23
I have two machines running Ubuntu 17.04.  One is my client, the other is a remote server (VPS).

I'm trying to run the following command:

```
rsync -rav --delete /home/username/webstuff/websitestuff/ username@ip_address:/var/www/html/website
```

I use "4096-bit RSA key-pairs".  I have disabled root account login...  I have disabled password login...  My "keyed" user is a member of the sudo group on the server.  I have CHOWN added the user to the group of the /www/ folder (assuming the lower folders inherit the same...  Not sure about this.

When I run the above command...  I get this:

> sending incremental file list
rsync: chgrp "/var/www/html/website/." failed: Operation not permitted (1)
./
.doit.db
conf.py
rsync: recv_generator: mkdir "/var/www/html/website/__pycache__" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/var/www/html/website/cache" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/var/www/html/website/files" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/var/www/html/website/galleries" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/var/www/html/website/listings" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/var/www/html/website/output" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/var/www/html/website/pages" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/var/www/html/website/posts" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
__pycache__/
cache/
files/
galleries/
listings/
output/
pages/
posts/
rsync: mkstemp "/var/www/html/website/.doit.db.8Dfxoe" failed: Permission denied (13)
rsync: mkstemp "/var/www/html/website/.conf.py.ni0q4d" failed: Permission denied (13)

sent 145,532 bytes  received 1,666 bytes  98,132.00 bytes/sec
total size is 3,585,929  speedup is 24.36
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1196) [sender=3.1.2]





---

### Post by SeijiSensei on 2017-04-23
I always store my key in /root/.ssh/authorized_keys and connect to root@server.  That avoids all such permission issues.

---

