---
title: "can someone help me with an rsync script please, quite urgent.."
date: 2008-06-02
forum: New to Ubuntu
---

### Post by srossnz on 2008-06-02
here is my current script:

```
#!/bin/sh
/bin/date >> /var/log/rsyncnet.log
/usr/bin/rsync -av -e ssh /var/www/vhosts/mydomain.org ****@usw-****.rsync.net: >>/var/log/rsyncnet.log 2>&1
/usr/bin/rsync -av -e ssh /var/lib/mysqlbackup ****@usw-****.rsync.net: >>/var/log/rsyncnet.log 2>&1
```

I have a folder in /var/www/vhosts/mydomain.org that i need to exclude.  It is httpdocs/ads2/sessions

I know enough to get into my server and change the script but no idea how to code it.  Thanks gurus!

---

### Post by HalPomeranz on 2008-06-02
This should work:

```
#!/bin/sh
/bin/date >> /var/log/rsyncnet.log
/usr/bin/rsync -av --exclude=/var/www/vhosts/mydomain.org/httpdocs/ads2/sessions /var/www/vhosts/mydomain.org ****@usw-****.rsync.net: >>/var/log/rsyncnet.log 2>&1
/usr/bin/rsync -av /var/lib/mysqlbackup ****@usw-****.rsync.net: >>/var/log/rsyncnet.log 2>&1
```

The trick is the "--exclude=..." option.  You don't actually need the "-e ssh" option-- this is the default for all recent versions of rsync.

---

