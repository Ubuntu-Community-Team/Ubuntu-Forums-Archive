---
title: "Recurring script to copy file to remote location"
date: 2011-03-15
forum: Programming Talk
---

### Post by Koffie24 on 2011-03-15
Hi there,

Can anyone help me with a recurring script to copy a file from the local machine to a folder on a remote machine on day one. Then on day 5 it should empty the folder of all its contents.

For example I want to copy /opt/Backup/Backup_File to /remotepc/Backups/ on day one. Then on day 5 it should delete the contents of /opt/Backup

Thanks guys!

---

### Post by Koffie24 on 2011-03-15
Hi Guys,

This is what I have so far. I know it's very basic, can someone give me a hand on refining it? For instance if there is a duplicate filename it should ask to overwrite. A place where errors will be logged to. That kinda thing.

Also I assume I can just make a cronjob for it to recur?

Thanks!

```

#!/bin/bash

echo "Do you want to copy the file now? Y/N"
read answer
if [ $answer = Y ]
then 
    cp /opt/Backup/Backup_File  /remotepc/Backups/ 
    echo "File Successfully copied"
else echo "Quitting"
fi
```

---

### Post by Koffie24 on 2011-03-15
Ok,

New code
```

#!/bin/bash
##
# Invocation eg.
#
# script.sh /opt/Backup/Backup_File  192.0.0.12 admin /home/Backups 
#

##
# Variables to be used
##
FILE_TO_MOVE=$1
IP=$2
USERNAME=$3
LOCATION_TO_MOVE_TO=$4
PASSWORD='password'

echo $PASSWORD | scp $FILE_TO_MOVE $USERNAME@$IP:$LOCATION_TO_MOVE_TO

```But this is still not working exactly like I want it to.

I'm having trouble with the SSH and can't get around it.

Someone? Please!

---

### Post by Koffie24 on 2011-03-15
To be more specific, the error is as follows:

Add correct host key in /home/user/.ssh/known_hosts to get rid of this message.
Offending key in /home/user/.ssh/known_hosts:1
RSA host key for xxx.xxx.xxx.xxx has changed and you have requested strict checking.
Host key verification failed.
lost connection

If I sudo it, it works. But obviously I want this automated, if I can get around this then the copy script is done.

---

### Post by AbhiJais on 2011-03-19
> **Koffie24 said:**
> To be more specific, the error is as follows:

Add correct host key in /home/user/.ssh/known_hosts to get rid of this message.
Offending key in /home/user/.ssh/known_hosts:1
RSA host key for xxx.xxx.xxx.xxx has changed and you have requested strict checking.
Host key verification failed.
lost connection

If I sudo it, it works. But obviously I want this automated, if I can get around this then the copy script is done.
Hi, the ssh key is generated each time, there is a change in file  system, as per my understanding. But you can add the correct key in the  list of known hosts.

1. open the file /home/<user>/.ssh/known_hosts.
2. If the file does not exists then create one with 700 permission.
3. then add the correct RSA key in front of remote host's IP, like:
X.X.X.X ssh-rsa XX:XX:XX:XX:XX:XX:XX:XX
([root@XXXXXX ~]# ssh XX.XXX.X.XX
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
c9:40:99:08:83:9e:ec:3f:61:36:88:fe:60:f2:67:1c.
Please contact your system administrator.
Add correct host key in /root/.ssh/known_hosts to get rid of this message.
Offending key in /etc/ssh/ssh_known_hosts:1
RSA host key for 10.170.0.66 has changed and you have requested strict checking.
Host key verification failed.
)

Note: Here c9:40:99:08:83:9e:ec:3f:61:36:88:fe:60:f2:67:1c is the RSA key of remote machine
4. Save the file and again try to ssh the remote machine.

Else you can try deleting the /home/<user>/.ssh/known_hosts  file,then try to ssh. In that case, the RSA key will automatically get  added to the file(It will ask you to add the RSA key to the list of  known hosts for first time). But make sure your machine does not use any  custom keys, or deleting will result in loss of prev. keys.

hope this solves your problem.

---

