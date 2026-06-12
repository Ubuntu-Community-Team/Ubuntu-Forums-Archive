---
title: "script help"
date: 2006-11-16
forum: Programming Talk
---

### Post by cyris| on 2006-11-16
Hey everyone.

I have this script that compresses a few directories on my system and ftp's them to a local server, however if i cron the job sometimes it doesn't complete and im thinking this is happening because of some of the file names are long and weirdly stamped.

Could anyone provide any suggestions?

#!/bin/sh
FILENAME=`date +%F`'.tar.gz'
SERVER=xx.xx.xx.xx
USER=backup
PASSWORD=alpha!
cd /home/wildgoosed/scripting/
tar czpf files-$FILENAME /usr/files
tar czpf email-$FILENAME /home/vpopmail
ftp -n xxx.xxx.xxx.xxx <<End-of-Session
user "xxxx" "xxxx"
cd "\files_email\files"
pwd
bin
put files-$FILENAME
ls
cd "\files_email\email
pwd
bin
put email-$FILENAME
ls
quit

---

### Post by dataw0lf on 2006-11-16
redirect stdout (and stderr if need be) to files.

like so:

```

ERR_LOG=err.log
OUT_LOG=out.log
exec 3>&2 4&>1
...

```

This will save the file descriptors for stderr and stdout to fds 3 & 4 (ERR_LOG, OUT_LOG).  Hopefully this is a start for you, I'd rewrite the whole thing, but I have a deadline here at work ;)

---

### Post by nik77 on 2006-11-16
I think some time the ftp put command fails. In my opinion you have to try catching the ftp return code ( and try to send the file an other time ).

---

