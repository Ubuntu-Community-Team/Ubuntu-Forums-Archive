---
title: "How to use cron and rsync to transfer files from remote server to local path"
date: 2016-04-06
forum: Programming Talk
---

### Post by jlivin252 on 2016-04-06
Hello Folks

I am looking for some knowledge to help me understand why my use of cron fails when using rsync to transfer files from remote server to local path.

My aim is to have a scheduled cron job run at a set time and successfully execute my transfer script

From numerous Google searches I put together the following rsync command:

```
rsync --protect-args --remove-source-files --chmod=Du=rw,Dgo=rw,Fu=rw,Fog=r -apvzrc pi@192.168.0.10:/media/pi/USBSTORAGE32/ /media/Data_1/"James' Files"/
```

I have set up the remote server so it doesn't ask for a password by using ssh-keygen rsa to generate a public key which is stored in an authorised_keys file. I log into the 'local' machine using SSH and type the command to 'pull' the files from the remote server to the local machine.

Once I'd tested the rsync command above I thought I had it nailed so popped this into a script which then added to cron via crontab. My added line looks like this

```
55 * * * * sudo /home/jlivin25/bin/myscripts/sync.sh > /var/log/james/cronsync.log 2>&1
```

And my script looks like this:

```
#!/usr/bin/env bash
rsync --protect-args --remove-source-files --chmod=Du=rw,Dgo=rw,Fu=rw,Fog=r -apvzrc pi@192.168.0.10:/media/pi/USBSTORAGE32/ /media/Data_1/"James' Files"/
```

The scheduled task fails to run as expected, cron trys to run the script but the following error message is logged in my log file:

```
sudo: no tty present and no askpass program specified
```

And its at this point that I'm stuck, because by 'googling' the above message I get lots of differing reasons that what I have done is not working. I'm not sure where to chase the error to, is the issue with my use of cron, ssh or rsync.

Any help would be appreciated.

littlejeem

---

### Post by ian-weisser on 2016-04-06
sudo won't work in a cronjob. Run the job as the appropriate user (or root).

Ensure that user has access to the key....

---

### Post by jlivin252 on 2016-04-07
[TABLE="width: 660"]
[TR="class: comment"]
[TD="class: comment-actions"][TABLE]
[TR]
[TD][/TD]
[/TR]
[/TABLE]
[/TD]
[TD="class: comment-text"]Hello ian-weisser. Thanks for your reply, I moved my desired cron job to root crontab. Removed the sudo from the command. I also generated an rsa public key for root user and am testing tonight. Will update with how it goes.
[/TD]
[/TR]
[/TABLE]

---

