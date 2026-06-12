---
title: "Crontab error: Host key verification failed."
date: 2016-07-05
forum: New to Ubuntu
---

### Post by albertramsbottom on 2016-07-05
Hi

I am running a crontab under a user called ```
userbak
``` from server2 that grabs Tar files from server1 and puts them in a share on server2

I have set up the keys and when I run and output the cron to a log file I get an error 

```
Host key verification failed
```

If I 
```
[CODE]sudo -u userbak ssh server
```1[/CODE] from server2, it connects to server1 without login or password so it works fine

The odd thing here is I have two servers working with this system, but every new one set up takes hours of fiddling to get it to work and clearly I have forgotten what the fiddles were once I have it working.

Any ideas what might be going on

Thanks

---

### Post by TheFu on 2016-07-05
Put the public keys from user1id@server1 in the user2id@server2 ~/.ssh/authorized_keys file. Double check that the permissions for the ~/.ssh/ directory and all files inside are correct.

Don't use **sudo** inside a crontab. In the crontab for the system doing the "pulls", use something like ** /usr/bin/ssh user2id@server2**.  Always use full paths inside cron and scripts. Cron doesn't provide much of an environment, so commonly known variables aren't set with cron is used. If you want some environment set, put those into the script that is called from the crontab.

OTOH, tar isn't really the best way to perform backups. Use something ilke rdiff-backup, which works over ssh anyway and provides an efficient method to have many backup versions.

---

### Post by albertramsbottom on 2016-07-05
Here is the backup grabber script running on server2

```
#!/bin/bash
#
# Generate a list of apps to grab
df|grep appbackups|awk -F/ '{ print $NF }'>/tmp/applistsmb

# Get each app in turn

for APP in `cat /tmp/applistsmb`
do
        cd /srv/appbackups/$APP
        scp $APP:* .
done
```

This works on two servers.

I have copied the keys and I know they work as I can ssh to server1 from server2 without login using the user that runs the crontab below

```
*/5 * * * * /opt/bin/backup-grabberSMB.sh > /home/userbak/logs/backup.log 2>&1
```


The odd thing is if a SU to userbak, user and run the backup-grabber script by:

```
bash backup-grabberSMB.sh
```

It asks for me to confirm the authenticity

```
The authenticity of host 'myhost.co.uk (198.MyIP)' can't be established.
ECDSA key fingerprint is myfingerprint.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'myhost.co.uk' (ECDSA) to the list of known hosts
```

After which it works and continues to work

The only thing I can think off is the fact that when I have been coping the key over to server1 I have been using the IP address

such as :

```
ssh-copy-id userbak@198.MyIP
```

Cheers for your help

---

### Post by TheFu on 2016-07-05
**su **
  and[B]
su - [/B]
aren't the same thing.  There are similar subtle options with sudo. I don't think **sudo -u** does what you want. Think you need **sudo -i** Be certain you understand the differences, to achieve the desired results.

The userid AND environment from which you run ssh-copy-id matters.  It is possible the wrong public key is being pushed. Can't tell from the information provided, but suspect when changing to the other userid, it isn't a full, complete, change, including the other user's environment.  This would explain why the crontab doesn't work.

Also, using the full path for all programs used in any script/crontab is a *best practice* for a good reason, to ensure the program being run AND any assumed config files are actually the ones intended. Just because something works interactively, doesn't mean it will work from cron.  Over the years, I've learned the hard way to do the things I'm trying to convey above. Saves time overall.

---

### Post by albertramsbottom on 2016-07-06
Well I solved it

It was the fact that I was sending the Tar files to a SMB share and had the enteries for the servers in the hosts file

I was using:

```
ssh-copy-id userbak@198.MyIP
```

Rather than

```
ssh-copy-id userbak@198.MyShare
```

Although completely unrelated your assistance got me thinking and solved the problem#

Many Thanks

---

