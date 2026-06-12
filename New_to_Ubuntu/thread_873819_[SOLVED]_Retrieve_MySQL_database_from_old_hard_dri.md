---
title: "[SOLVED] Retrieve MySQL database from old hard drive"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by esd2609 on 2008-07-29
Hello,

My old computer's motherboard crashed but the hard drive is fine.  I installed Ubuntu on a new machine.  My question is what's the best way to import my MySQL databases off of the old hard drive?  Is it just a matter of copying the databases from one drive to the other?

Thanks for the help,

Tristan

---

### Post by BDNiner on 2008-07-29
did you create a backup of the database? i don't think it is as simple as just copying the database from one drive to another. if you have a backup on the old HD then you can restore the backup using MYSQL administrator.

---

### Post by esd2609 on 2008-07-29
No, I unfortunately don't have back-ups of all of them.  I was backing up the disk but not the databases.

I might try to boot the disk and then make back-ups of the DBs.  I was hoping it would be as simple as moving the files into the right directory and then maybe having to add the DB schema to some file.  But now that I write that, I see it might be easier just to try booting the disk and backing-up the DBs.

---

### Post by unutbu on 2008-07-29
To mount your old hard drive in your new computer:

Open the old computer and take out the hard drive.
Open your new computer and connect the hard drive to the drive data ribbon.
If you are uncomfortable with that, you can  buy a "rack" which plugs into a USB port on the new computer and which allows you to insert the naked internal drive into the rack. I think there are also things called USB enclosures which do the same thing. Sorry though -- I don't know that much about the hardware end of things.


Boot up the new computer and Ubuntu should hopefully recognize the new drive (most of the time there is no problem).

A second drive will be given a device name like /dev/sdb.
The first partition would be called /dev/sdb1. To mount the first partition:
```

sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1 
```

To recover your database:

First install mysql on the new machine. 
```

sudo apt-get install mysql-server-5.0
```

If your old database was called 'mydata', then you might want to create an empty database on your new machine also called 'mydata'. This will create the appropriate folder. I'm not sure this is really necessary however.

Your old computer's first partition would then be mounted at /media/sdb1.
The mysql database (if it is on the first partition) would be located at /media/sdb1/var/lib/mysql. 

First stop the mysql server:
```

sudo /etc/init.d/mysql stop
```

Now simply the copy the files from 

/media/sdb1/var/lib/mysql/mydata/

to 

/var/lib/mysql/mydata

Check that the files are owned by mysql, part of the mysql group, and have owner and group read/write permissions. 

Then restart the mysql server:

```

sudo /etc/init.d/mysql start
```
You should then be able to access your database again.

---

### Post by esd2609 on 2008-07-29
Thanks very much for the explanation.  That did it.

---

