---
title: "HOWTO: LTSP: Kill orphaned processes"
date: 2006-12-07
forum: Outdated Tutorials &amp; Tips
---

### Post by murraymints on 2006-12-07
Hi,

For anyone using LTSP and is having problems with orphaned processes caused by terminals which are not logged out of properly e.g. due to power-cuts, etc. Then this script may come in useful.

WARNING 1:This script should be seen as beta qualty and is not suitable for any production LTSP servers.

WARNING 2:You must make sure that any services you are running are running from system users, for example I had to adjust apache2 and no-ip services which where running as myself and nobody respectivley before this script worked properly. 

OK, onto the sript;

Open a text editor with root priveledges e.g. gksudo gedit

Cut and past the code below into the text editor, save the file as /usr/sbin/orphkill.

Then sudo chown root /usr/sbin/orphkill
     sudo chmod 700 /usr/sbin/orphkill

Then run it with sudo /usr/sbin/orphkill (dont worry this wont actually kill any processes yet) and open the file /var/log/killed.log to check which processes it would have killed. If you see the processes of any logged in users or running services then there is a bug, post post about it here.

Otherwise open the script with gksudo gedit /usr/sbin/orphkill and remove the comment before the kill command near the bottom of the script. Then save and run the script again and if everything is ok then add the the script to the crontab using sudo crontab -e

and adding the following line:

*/3 *   *   *   *    /usr/sbin/orphkill >& /dev/null

which will execute the script every 3 minutes. You can change the number 3 to specify the number of minutes.

That's it! Any problems or improvements then please post them as replies here.

```

#!/bin/bash

# orphKill - This program searches for orphaned processes and kills them.
# This is particulary usefull for LTSP servers where the terminals are not logged off
# properly due to powercuts, etc.

# Written by Murray Fleming

# Declare arrays
declare -a procUsers #Process usernames
declare -a procIDs #Process IDs
declare -a safeUsers #List of safe users

# Fill procUsers and procUds arrays
num=0
num2=0
for i in `ps aux | awk '{print $1 " " $2}'` ; do
	rem=$(($num % 2))
        if [ $rem -eq 0 ]; then
		procUsers[$num2]=$i
	else 
		procIDs[$num2]=$i
		num2=$(($num2 +1))
	fi
        num=$(($num + 1))
done
# Remove ps aux column headers
unset procUsers[0]
unset procIDs[0]
# Protect samba, imapd and gam_server daemons by marking their users as root
for i in `pgrep smbd && pgrep gam_server && pgrep imapd` ; do
	num=0
 	while [ $num -lt ${#procIDs[@]} ]; do
        	if [ "$i" == "${procIDs[$num]}" ]; then
			procUsers[$num]="root"
		fi
             	num=$(($num + 1)) 
        done
done

# Fill safeUsers array
num=0
# Add logged in usernames and uids
for i in `last | awk '/'"still logged in"$'/ {print $1}'` ; do
	safeUsers[$num]=$i
	num=$(($num + 1))
	if [ ${#i} -eq 8 ]; then
		safeUsers[$num]=`grep ^$i /etc/passwd | awk 'BEGIN {FS = ":"} {print $3}'`
	else
		safeUsers[$num]=`grep ^$i: /etc/passwd | awk 'BEGIN {FS = ":"} {print $3}'`
	fi
	num=$(($num + 1))
done
# Add system usernames and uids
for i in `cat /etc/passwd | awk 'BEGIN {FS = ":"} {if ($3 < 1000) print $1" "$3}'` ; do
	safeUsers[$num]=$i
	num=$(($num + 1))
done
# Add ssh logins
# This is a hack round 'last' not showing ssh and su logins and assumes they will always timeout
for i in `ps aux | grep "sshd\|su" | awk '{print $1}'` ; do
	if [ "$i" != "root" ]; then
		safeUsers[$num]=$i
		num=$(($num + 1))
	fi
done
# Add nobody user
# This prevents killing of in.tftpd processes which may be related to booting terminals
safeUsers[$num]="nobody"

# Kill any process with a user id not in the safeUsers array
num=1 #Start at 1 to skip ps aux column headers on first line of output
for i in ${procUsers[@]} ; do
	found="no"
	for j in ${safeUsers[@]} ; do
		if [ "$i" == "$j" ]; then
			found="yes"
		fi
	done
	if [ "$found" == "no" ]; then
		echo Orphaned process found at PID: ${procIDs[$num]} UID: ${procUsers[$num]} Time: `date +%H:%M` `date +%d-%m-%Y` >> /var/log/killed.log
		echo `ps aux | grep ${procIDs[$num]} | grep -v grep` >> /var/log/killed.log
		kill ${procIDs[$num]}
	fi
	num=$(($num + 1))
done

```

---

### Post by RedBoot on 2006-12-12
Thanks for sharing your work, murraymints. I'm new to LTSP, but I'll keep this handy for future reference.

One question, will this work with 6.10 since I've heard it's using a newer LTSP?

---

### Post by murraymints on 2006-12-15
I would assume this will work with ubuntu 6.10 since the script is not making any use of any parts of LTSP or anything particulary fancy. I am using this script on an ubuntu 6.06 server with LTSP 4.2 installed (not the ubuntu "muekow" ltsp).

If there have been improvements to the latest versions of LTSP included with ubuntu which make scripts like this unecessary (i.e. can you reset a logged in terminal and log back in without it complaining that everything is still open) then please post a reply here.

Also, a little bit off topic but have you had any success using a printer attatched to a terminal with ubuntu ltsp 6.10? This is my main reason for sticking with LTSP 4.2.

---

