---
title: "cleaning those backup more than 1 months older"
date: 2006-03-08
forum: Programming Talk
---

### Post by yccheok on 2006-03-08
hello all, previously, i am perfroming my CVS backup through cron job. by executing the following script.

#!/bin/bash

filename=/home/yccheok/`date +%b-%d-%y`.tar.gz

/bin/tar -zcpf $filename /cvsroot

cat $filename |ssh 192.168.0.165 "cd backup; cat > $filename"


The following script is re-inside my cron job list. However, as time goes on, I realize my backup server space is not enough.

How can I create another cron job in the backup server, so that it can delete those backup file which is 30 days old? Any example script to perfrom that?

Thank you.

cheok

---

