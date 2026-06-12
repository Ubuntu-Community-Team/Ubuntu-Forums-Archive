---
title: "Automated Backups on Ubuntu Server"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by benauld345 on 2008-06-06
Hi,

I'm quite new to the linux community, and I'm really impressed with Linux, however I'm stuck on something!

I've got a few folders on my server which need to be backed up daily at 6am on to my portable hard drive. My portable hard drive has been mounted as /portablehd .

I need to backup the following directories:
/music
/auction
/var/www

And MySQL (if possible)

Any help will be much appreciated!

Thanks

Ben

---

### Post by HalPomeranz on 2008-06-06
You can just use rsync and mysqldump out of cron.  Use "sudo crontab -e" and add an entry like:

```

0 6 * * * /usr/sbin/mysqldump --all-databases | gzip >/portablehd/msqldump.gz; /usr/bin/rsync -aH /music/ /auction/ /var/www/ /portablehd/

```

---

### Post by benauld345 on 2008-06-06
Hi,

Thanks for your input. I installed rsync no problem, I entered the command into the cron, everything went OK. Just to be on the safe side I thought I better test the script to make sure it all works. I ran the script and got the following error:

-bash: /portablehd/msqldump.gz: Permission denied
sudo: /usr/sbin/mysqldump: command not found

rsync: failed to set times on "/portablehd/.": Operation not permitted (1)
rsync: recv_generator: mkdir "/portablehd/Auction Program" failed: Permission denied (13)
*** Skipping everything below this failed directory ***
rsync: recv_generator: mkdir "/portablehd/Music" failed: Permission denied (13)
*** Skipping everything below this failed directory ***
rsync: failed to set times on "/portablehd/.": Operation not permitted (1)
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]

Sorry to be a pain, and thanks again for your help.

Ben

---

### Post by cariboo on 2008-06-06
It looks like you don't have write permissions set on your external drive, so fix that first. Next give **simplebackup** a try it's located in the repositories. It's quite easy to setup.

Jim

---

### Post by benauld345 on 2008-06-06
Thanks for your input Jim, would you know how to change permissions at all?

Thanks

Ben

---

### Post by cariboo on 2008-06-06
This will make the drive world readable so here goes:
in a terminal type:

```
sudo chmod -R 777 /path_to_external_drive
```

Where path_to_external_drive is where your external drive is mounted eg: /media/disk

Or if you have it permanently mounted through /etc/fstab you can change the ro to rw

Jim

---

### Post by benauld345 on 2008-06-06
Hi,

Thanks for all the responses, all works now :)

Ben

---

### Post by HalPomeranz on 2008-06-06
Please do not make the external drive world-writable!  This is not a good idea from a security standpoint.  Of course, you've done "chown -R ..." now and it's going to be very difficult to put things back the way they were.  *sigh*

Your problem with running the script was that you didn't have full root privs when you ran the commands.  The "sudo" you used at the front of the command only applies to the first command (mysqldump) and not the rest of the command line.

So if you want to test the script, execute these commands in a terminal window:

```

sudo su -
/usr/sbin/mysqldump --all-databases | gzip >/portablehd/msqldump.gz
/usr/bin/rsync -aH /music/ /auction/ /var/www/ /portablehd/
exit

```

The first line will give you a fully-interactive root shell.  Then the subsequent commands will execute with root privilege.  The last "exit" will exit the superuser shell and get you back to your normal user account.

---

