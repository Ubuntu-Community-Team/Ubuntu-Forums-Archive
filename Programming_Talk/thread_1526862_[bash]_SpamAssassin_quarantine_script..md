---
title: "[bash] SpamAssassin quarantine script."
date: 2010-07-08
forum: Programming Talk
---

### Post by prodigy_ on 2010-07-08
It's really a pity that SpamAssassin can either mark mail as spam or delete it. A built-in quarantine option would be really nice, but developers don't want to implement it for some reason. So we're left with just two options and none of them is any good. Marking mail doesn't help with **filtering** spam, so resources are just wasted. And deleting everything that was recognized as spam is a bad idea because of possible false positives.

So I wrote this little and simple script that monitors Qmail folders for incoming mail with "X-Spam-Flag: YES" and moves everything that matches to a designated spam account (e.g [email]spam@example.domain[/email]):

```
#!/bin/sh

# Define log file location.
QUAR_LOGFILE="/var/log/spamq.log" 

f_MoveMarked () {
	# Find any file that was modified within the last 5 minutes in "Maildir/new/" 
	# and "Maildir/cur/" subfolders of every account except our designated spam account.
	RECENT_NEW=$(find /var/qmail/mailnames/${1}/*/Maildir/new/ -mmin -5 -type f|grep -v '\/spam\/')
	RECENT_CUR=$(find /var/qmail/mailnames/${1}/*/Maildir/cur/ -mmin -5 -type f|grep -v '\/spam\/')

	for i in $RECENT_NEW $RECENT_CUR
	do
		# Check for spam headers.
		if	[ -n "$(head -1 $i|grep 'X-Spam-Flag: YES')" ] || [ -n "$(head -50 $i|grep '\*\*\*\*SPAM\*\*\*\* ')" ]; then
			# Log sender address.
			HDR_FROM=$(grep -m 1 -A 1 -i '^From:' $i|grep -m 1 '.*@.*\..*'|sed 's/[\<\>]/ /g'|awk '{ print $NF }')
			# Log current time.
			date >> $QUAR_LOGFILE
			# Log spam mail filename.
			printf "%b" "${HDR_FROM}\t${i}\nMoving... " >> $QUAR_LOGFILE
			# Move spam mail.
			mv -f $i /var/qmail/mailnames/${1}/spam/Maildir/cur
			# Log exit status.
			if	[ "$?" -eq "0" ]; then
				printf "%s\n\n" "done! " >> $QUAR_LOGFILE
			else
				printf "%s\n\n" "ERROR! " >> $QUAR_LOGFILE
			fi
		fi
	done
}

# Stay resident and wake every 5 seconds.
while	true
do
	f_MoveMarked example.domain	# Of course you need to specify your actual domain name instead of "example.domain" here.
	sleep 5
done
```

As far as I can tell the script works (I've been testing it for about a month) but I'd like to hear any suggestions about how to improve it. :-)

---

