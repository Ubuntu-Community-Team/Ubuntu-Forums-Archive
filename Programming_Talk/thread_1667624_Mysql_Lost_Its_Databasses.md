---
title: "Mysql Lost Its Databasses"
date: 2011-01-15
forum: Programming Talk
---

### Post by concept08 on 2011-01-15
I recently had some serous memory problems.

After replacing all memory modules, and updating ubuntu 10.04 LTS

I just updated all updates in update manager.

When i went to start working coding i logged into MYSQL and i noticed all my databases are gone.

Now they are still there on the hard drive, but they are non existent to MYSQL

MYSQL also seems to have removed all of my users permissions etc.

My database's are still all there and i can confirm this because i can change directory ownership from mysql gain access and see all the databases still there.

the command 
mysqlbinlog ib_logfile1
or any variation there of does not seem to work or enable me to see the final moments before this stuff happened. 

My default SQL directory is not the install recommended default location.

the database location is 
/media/os150/database_location
etc/apparmor.d/usr.sbin.mysqls and all /etc/mysql/my.cnf files still reflect the updated mysql database location.

its just strange i have spent a great deal of time researching this type of problem and i cannot find anything that points to a bad update, my personal error, or whatever.

just having databases disappear but still being able to see the data on the hard drive is just strange.

thanks for any help that is given

---

### Post by concept08 on 2011-01-15
ok first of all the credit needs to go to a friend on this. for he helped me fix this problem in like 2 minutes.

the problem was exactly this.

my computer crashed due to bad memory after i replaced the memory and rebooted. SQL created its own directory (the ones i had listed in my.ini file) and then created all of the files it needed within said directory. 

then my OS (ubuntu 10.04) after SQL mounted the disk but it could not mount to its normal mount point because mysql already created that directory so my hard disk which contains all the mysql database information was mounted to 

/media/os150_ instead of /media/os150 

this is how my friend solved the problem

```

sudo mount

```will return a bunch of stuff but if u sift through it mine was located on the bottom of the output you will see all your added hard disks mounted 

this is what mine looked like

/dev/sdc1 on /media/os150_ type ext4 (rw,nosuid,nodev,uhelper=udisks)

if you notice the _ in os150 you can see that the problem is right there. that mount point should be os150

to confirm that this is the case

```

ls -lsah /media

```outputted

4.0K drwxr-xr-x  6 root   root   4.0K 2011-01-15 04:23 .
4.0K drwxr-xr-x 22 root   root   4.0K 2011-01-15 05:25 ..
   0 lrwxrwxrwx  1 root   root      7 2010-10-15 19:05 floppy -> floppy0
4.0K drwxr-xr-x  2 root   root   4.0K 2010-10-15 19:05 floppy0
4.0K drwxr-xr-x  3 root   root   4.0K 2011-01-15 05:22 os150
4.0K drwx---r-x  8 user user 4.0K 2010-10-16 19:45 os150_
4.0K drwxrwxrwx 20 user user 4.0K 2011-01-15 04:25 os300

as described above we can see what is going on here

mysql created a new directory in the /media directory called it os150 and then created all its needed database structures in that newly created directory in attempt to recover from a crash.

so here is what we do.

close anything that is using anything related to those file pointers.
for example

close all terminals that are CD into the /media/os150 directories
verify that you have no text files open and that nothing is using any part of those hard drives or directories.

then

```

sudo service mysql stop
sudo umount /dev/sdc1
sudo mount

```verify that the device is not mounted anymore

```

ls -lsah /media

```will give the output

4.0K drwxr-xr-x  4 root root 4.0K 2011-01-15 16:25 .
4.0K drwxr-xr-x 22 root root 4.0K 2011-01-15 05:25 ..
   0 lrwxrwxrwx  1 root root    7 2010-10-15 19:05 floppy -> floppy0
4.0K drwxr-xr-x  2 root root 4.0K 2010-10-15 19:05 floppy0
4.0K drwxr-xr-x  3 root root 4.0K 2011-01-15 05:22 os150

as we can see the drive is no longer mounted. but we still have that directory that mysql created.

so 

```

sudo mv /media/os150 /media/os150_trash
ls -lsah /media

```here is the output now

4.0K drwxr-xr-x  4 root root 4.0K 2011-01-15 16:32 .
4.0K drwxr-xr-x 22 root root 4.0K 2011-01-15 05:25 ..
   0 lrwxrwxrwx  1 root root    7 2010-10-15 19:05 floppy -> floppy0
4.0K drwxr-xr-x  2 root root 4.0K 2010-10-15 19:05 floppy0
4.0K drwxr-xr-x  3 root root 4.0K 2011-01-15 05:22 os150_trash



do not delete that directory if for whatever reason data got written to that new database. its a wise move to never delete any data untill you are absolutely sure you will never need it again. i dont see how there could be any important data that you will need in this fresh newly created mysql directory but hey you never know.
 
now

```

sudo mkdir /media/os150
sudo mount /dev/sdc1 /media/os150
ls -lsah /media/os150

```should show your database structure. (if you have permissions to see it)

4.0K drwxrwxrwx  3 mysql  mysql  4.0K 2010-10-16 18:57 database
4.0K drwxr-xr-x 17 mysql  mysql  4.0K 2010-12-22 04:18 database_location

now

```

sudo service mysql start

```now you have SQL back with all your old data.

thanks to my friend this was easy

hope this helps someone out in the future.

---

### Post by slavik on 2011-01-16
Is this a mount specified in /etc/fstab? I suggest you use that and mount it somewhere not in /media or /mnt.

---

### Post by concept08 on 2011-01-16
i had never thought of that.

thanks for the tip i will give it a try

---

