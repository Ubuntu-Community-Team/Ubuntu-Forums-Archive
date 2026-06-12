---
title: "Cron Job not completeing"
date: 2006-11-10
forum: Programming Talk
---

### Post by drezha on 2006-11-10
Not sure if it's *strictly* programming but thought this was best place for it.

I've got a cron job that runs every Sunday morning to back up my documents but it doesn't complete. It only backs about 5Mb up before stopping.

I've got a file called DocBackup that has the following in.

```
* 5 * * 0 tar pzcvf /home/chris/Desktop/DocsBackup.tgz --exclude="/home/chris/Disc2/Documents/My Music" --exclude="/home/chris/Disc2/Documents/My Videos" /home/chris/Disc2/Documents
```

The command works when I use it in the terminal. I submitted the file to the cron list. Now when I type crontab -l I get the line above. Is there any reason why it doesn't finish?

Would like to wake up in the morning and just stick a CD in and burn the file off rather than having to redo the command in the terminal.

---

### Post by dwblas on 2006-11-10
It should mail any messages to /var/spool/mail/username for the default e-mail user you set up.  See if you have something informative.  My first thought was that you are using a normal user cron to back up files with root access only, but I have no way of confirming that.  If that is the case you want to sudo crontab -e to setup your backup in root's cron.

---

### Post by drezha on 2006-11-11
Obviously I haven't setup a default email user because there's nothing there.

No, it's not got root only access. It's my documnets and thus I have permission to do all to them.

I've added ```
>/var/log/Docsbackup.log
``` to the command so I'll have a log of it.

I've now also changed the cron for ```
0 5 * * 0 /home/chris/ShellScripts/DocsBackup >/var/log/Docsbackup.log
```

and the file it leads to is 
```
#!/bin/sh

tar pzcvf /home/chris/Desktop/DocsBackup.tgz --exclude="/home/chris/Disc2/Documents/My Music" --exclude="/home/chris/Disc2/Documents/My Videos" /home/chris/Disc2/Documents
```

I've run the shell script seperatly and it works so I think tomorrow I may be all sorted :)

---

### Post by dwblas on 2006-11-11
Consider installing exim4 if you don't have any program to handle internal e-mail.  It's very simple to set up.  Then messages, including cron's,  will be mailed to you.

---

### Post by drezha on 2006-11-11
Cheers.

I'll let what changes I've done to it run tonight and see if it works. Also see if it leavees a log file.

Otherwise I'll install exim then :)

---

