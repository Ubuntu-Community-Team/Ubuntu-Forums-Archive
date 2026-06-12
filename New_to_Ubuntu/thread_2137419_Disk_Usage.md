---
title: "Disk Usage"
date: 2013-04-20
forum: New to Ubuntu
---

### Post by theondr on 2013-04-20
I need to create a script sends an email message to the user specified on the command line if 

any of the filesystems are at more than 70% of capacity. The script should not process special 

filesystems as /proc. It should only process filesystems which are either locally mounted or are 

mounted via NFS.

An individual email should be sent for each filesystem which is at the warning level. There should 

be a subject on the email with a message "Warning: Filesystem <put filesystem the>here is at 

<X>% of capacity" If the filesystem is at greater than 90% of capacity, the "Warning" should be 

changed to "Critical Warning".

I may use any scripting language including /bin/sh, ksh, bash, awk or perl but not C-Shell. This 

will be done on my own Linux/UNIX system.


Thank you,

Theo

---

### Post by prodigy_ on 2013-04-20
```
#!/bin/bash

warn_types=([70]=WARNING [90]=CRITICAL)
fs_types="ext|ntfs|cifs|fuseblk" # Add what you need

while read line; do
	perc_used=$(df $line | awk -F" " 'NR>1{print $5}')
	for i in 90 70; do
		if [ ${perc_used%\%} -gt $i ]; then
			echo "${warn_types[$i]}: $line is $perc_used full" | \
				# insert mail sending command here
				# e.g. mailx -A accountname -s 'subject' address@example.com
			break
		fi
	done
done < <(mount | grep -E "type $fs_types" | cut -d' ' -f 3)
```

---

