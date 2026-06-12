---
title: "LAMP backup to Windows"
date: 2013-02-06
forum: New to Ubuntu
---

### Post by ChickenNoodle on 2013-02-06
Hello,
I'm new to ubuntu (linux in general) and was hoping for some general advice.  
I have recently decided to go ahead with an ubuntu 12.4 server, we have a completely Windows environment otherwise.

I had reason to install laravel for a developer doing some work for us and decided to go with ubuntu.    Ubuntu has been so easy to install and a pleasure to use (with exception of network problem but I'll post later about that) ...so to the point....

I will now need to make sure and create daily ubuntu backups and I would like to push this data to my local (Windows based) backup folder to be included in our daily offsite backup.

I would really appreciate some advice on what I should be backing up (so I'm including all relevant LAMP data and config if possible)  and what are the best tools to use make the backup then shove it onto my local Windows backup server.

Many thanks in advance to those who reply !

---

### Post by Mark Phelps on 2013-02-06
Whatever you use, make sure that it preserves the Linux filesystem permissions.

I have been doing Clonezilla backups of my Ubuntu installs to shared NTFS partitions for years without problems -- but that's because it's an image file.  

Just copying files and folders to NTFS partitions will work, but that loses the Linux filesystem permissions in the process.

---

### Post by SeijiSensei on 2013-02-06
Are you just serving web pages or are you running applications with database backends?  For the former, just backing up the directories where the pages are stored is fine.  If you are using a database like PostgreSQL or MySQL as well, you should look into the "dump" commands for those DBs, pg_dump and mysqldump.  These create plain-text backups in SQL that you can use to recreate the databases if disaster strikes.  Don't bother backing up the binaries in /var/lib/pgsql and /var/lib/mysql.  The plain-text method is much more portable.

As Mark says, you'll need to deal with file permissions.  Here are two approaches I might suggest:

1)  Install a copy of [VirtualBox]("http://www.virtualbox.org/") on some Windows machine, and then install another instance of Ubuntu server in a virtual machine.  Then you could use "rsync" to image the relevant directories off the live server.  You can also take snapshots of the VM so you have a second line of defense.

2)  A more conventional approach might be to first use [Clonezilla]("http://clonezilla.org/") or some similar application to create a backup of the entire machine once you've massaged it into the condition you like.  Then you simply need to create updates of the directories where files might be changing.  One solution that works with Windows is to create a compressed "tarball" of the relevant directories.  I would run a script each night that creates the SQL dump files referenced above, then uses tar to create a compressed backup of that file and the contents of any website directories like /var/www.  Something like this:

```

cd /
tar cjvpf todays-backup.tar.bz2 var/www path/to/dumpfiles

```

For "todays-backup" I actually use a dated name like 20130206.backup.tar.bz2.  You can generate the date code with the command "date +%Y%m%d".  Here's a little snippet that shows how you could use the shell to create the filename you need:

```

#!/bin/bash
TODAY=$(date +%Y%m%d)
cd /
tar cjvpf $TODAY-backup.tar.bz2 var/www path/to/dumpfiles

```

I posted a script to back up MySQL on multiple servers in [this thread](http://ubuntuforums.org/showthread.php?t=1956580).  Maybe it will give you some starting points.

If you export a share off a Windows server, you can mount it with [CIFS]("https://help.ubuntu.com/community/MountWindowsSharesPermanently") in Linux and write to it directly.  So after the tarball is created, just copy it to the mounted Windows share with the cp command.

---

### Post by ChickenNoodle on 2013-02-07
Thanks for your replies, this is most helpful.   I'll let you know how I get on.
Thanks again :)

---

