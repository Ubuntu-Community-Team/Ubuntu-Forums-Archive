---
title: "Cron combined with ssh and rsync"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by pietro2580 on 2008-08-28
Dear all,

I am trying to set up a backup system for my Ubuntu linux (8.04) laptop with a desktop linux machine (openSuse 9.x) using a combination of rsync, cron and ssh. 
The folowwing rsync command is working ok when I run it in a terminal (as normal user):
```
rsync -avz -e "ssh -i /home/userid/sync/PCxxxx-rsync-key" /home/userid/wanteddir/ userid@pcyyyy:/home/userid/backup/wanteddir/
```

When I put this command in my crontab file (running crontab -e), the rsync command fails.
```
46 10 * * * rsync -avz -e "ssh -i /home/userid/sync/PCxxxx-rsync-key" /home/userid/wanteddir/ userid@pcyyyy:/home/userid/backup/wanteddir/
```

However, the cron-log-file tells me that the job is excuted:
```
Aug 28 10:18:01 PCxxxx /USR/SBIN/CRON[19650]: (userid) CMD (rsync -avz -e "ssh -i /home/userid/sync/PCxxxx-rsync-key" /home/userid/wanteddir/ userid@pcyyyy:/home/userid/backup/wanteddir/)
```

If there would be an error-message resulting from this cron-job, where can I find it? Apparently not in the file /var/log/cron.log? Also in /var/log/messages I cannot find any entry related with my cronjob

Thanx in advance
P.

---

### Post by txcrackers on 2008-08-28
Try putting the rsync command in a shell script and capturing the STDOUT and STDERR to a temp file. Have the crontab entry fire off the shell script. And you don't need to specify SSH: rsync uses that by default these days.

---

### Post by hyper_ch on 2008-08-28
(1) make a script
```

#!/bin/bash
rsync -avz -e "ssh -i /home/userid/sync/PCxxxx-rsync-key" /home/userid/wanteddir/ userid@pcyyyy:/home/userid/backup/wanteddir/

```

(2) make it executable

(3) add the script to cron
```

46 10 * * /path/to/script

```

---

### Post by pietro2580 on 2008-08-29
Hi,

Thanx for your responses. However, all the suggestions you guys did, I already tried. I did initially put all my commands in a shell-script, but for debug-purposes I tried the rsync command immediately in the crontab-file. 
However, the suggestion of txcrackers to write the output of my shell script to the STDERR allowed me to track down the problem (to be honest, I had to google for this to find it out). It seemed that - unless I installed and copied a private key from the client to the host- the script still kept asking for the password (which was exactly what I wanted to avoid). If found the solution here:
[http://ubuntuforums.org/archive/index.php/t-30709.html](http://ubuntuforums.org/archive/index.php/t-30709.html)
So I had to change some things in the /etc/ssh/sshd_config -file on the server where I am writing to:
1) PasswordAuthentication no 
2) StrictModes no
(but were by default on yes).
This did the trick for me.

thanx a lot!
P.

---

### Post by hyper_ch on 2008-08-29
don't alter sshd config like that. Rather generate a key and use key-based authentication. That's quite simple.

Here's howto make key-based login:

[http://www.howtoforge.com/mirroring_with_rsync](http://www.howtoforge.com/mirroring_with_rsync)

and then you run a script like

```

# RUN RSYNC INTO CURRENT
KEY=/path/to/keyfile
rsync						\
        -avz					\
        -e "ssh -i $KEY"			\
	/path/to/local				\
	user@remote:/path			\
	/path/to/local ;

```

and then the backup server should log into the production server to get the data... not vice versa - based on the idea that the production server is more likely to be hacked. If the production server can gain ssh access to the backup server a hacker can compromise both systems.

---

### Post by pietro2580 on 2008-08-29
Hi hyper_ch,

Thanks for the advice.
I already create a private/public key -pair, however it keep prompting me for a password. But when I created the key, I also entered a password - instead of leaving it empty. 
Now I created a new key wihtout pass-word, set the StrictModes back to yes, and as you suggested this works.
However, what was then the problem? That I gave a password when creating a key? Or am I missing something?

P.

---

### Post by hyper_ch on 2008-08-29
> **pietro2580 said:**
> That I gave a password when creating a key?

That was the problem. Because then you have to "unlock" the key with the password.

---

### Post by pietro2580 on 2008-08-29
Ok, that makes sense.
Thanks a lot!!

P.

---

### Post by hyper_ch on 2008-08-29
as said, it's also recommended that yuo initiate the syncing from the backup box (if possible)

---

