---
title: "rsync errors"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Twizzle on 2008-06-11
I am trying to use rsync in a script to provide a full system backup to a server which will allow me to roll back my system should there be a problem. I have followed a number of posts on here to try and get a 'timemachine' type setup which uses hard links to provide 30 days of backup.

The script will run but generates errors. A number of the errors seem to be produced during the rsync process and are:

```
rsync: chown(file name) : Permission Denied (13)
```

I then get some errors during the cp stage, eg:

```
/bin/cp: cannot create link `/home/john/SERVER/backup/old/2008-06-11_16:50/var/lib/defoma/gs.d/dirs/fonts/Courier_New_Italic.ttf': No such file or directory

```

The code in the script for this part is:

```
#Full backup into /Current
$RSYNC							\
	-aplvz --delete --delete-excluded		\
	--exclude-from="$EXCLUDES"			\
	/						\
	$CURRENT;
```

and:

```
$TOUCH $BACKUPDIR/current
# MAKE HARDLINK COPY
$CP -al $CURRENT/* $NOW
```

The bulk of the code was taken from [this]("http://ubuntuforums.org/showthread.php?t=816861") post.

My server that I am trying to store the backup on is formatted in ext3 and mounted via SAMBA (I have NTFS drives in it too).

I am not really sure what the errors mean. I assume that it is chown ing the files to ensure the permissions are kept the same as the source? If I look at the /current and /old backups there are a number of files that are locked and shown with root ownership.

I don't understand the second errors though as the files are there - the rsycn created them, so I don't know why it says they can't be found?

---

### Post by miss.magenta on 2008-06-11
The permissions errors are just that - the user you are using to run the script does not have adequate permissions to accomplish all of its tasks.

You can try to run the script as root using sudo, but that will only solve the issue if you are backing up to the same machine.

What you probably want to do, at least to get it to run (not sure if what you are doing will actually allow you to have a full, restorable, backup), is set nopasswd in your sudoers file on your remote machine:

ALL= NOPASSWD:/usr/bin/rsync

so that you're not prompted for a password during script execution.

then you'd want to do something like:

rsync -a -e "ssh" --rsync-path="sudo rsync" blah blah blah

to allow rsync to run as sudo on the remote machine - this should get you around the permissions issues.

---

### Post by Twizzle on 2008-06-11
I am running the script as sudo, but I guess, as you say, it is the permissions on the server that is causing the problems.

I am a bit confused by this though, as I am not running a command on the server, just on the main machine. If I needed to set no password for this as you say, would that not be the same for any access to the shared folder? Does this mean that Samba will only allow you to access / modify a shared folder as the user of the server as opposed to the user doing the work (if that makes sense)?

I take it that there will be security implications if I set it to NOPASSWD? I intend to run a webserver on the same server at somepoint.

---

### Post by miss.magenta on 2008-06-11
There are security implications, but if you set it that way, it's only using the nopasswd parameter for rsync and nothing else.  The other way that comes to mind is to enable root logins with ssh key authentication, but that is probably something you shouldn't even consider.

ooh, just thought of something else...if running the script interactively would work you could do something like

stty -echo; ssh remotehost sudo -v; stty echo 

prior to running the script - you'd be prompted for the sudo password...but that does nothing for you if you want to cron it.

---

### Post by Twizzle on 2008-06-11
Well that has given me something to think about. I think I will reasses how and what I want to / need to back up and my options. The more I think about it, as long as I back up my /home folder and contents, there is probably not a lot else I need. A fresh install is so much easier in Ubuntu than it was in Windows (I am slowly but surely breaking free :) )

Thanks for your help.

---

