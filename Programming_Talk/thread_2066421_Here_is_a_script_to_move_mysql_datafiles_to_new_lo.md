---
title: "Here is a script to move mysql datafiles to new location"
date: 2012-10-04
forum: Programming Talk
---

### Post by shumifan50 on 2012-10-04
Please don't flame me, I am not a script writer, but I thought this script might be useful to somebody. Feel free to edit and improve it.
It was developed for Ubuntu and therefore assumes that my.cnf is at /etc/mysql/my.cnf, but it can be overidden on command line.
It requires mysql to be down for a minimum of time by syncing the directories(twice) before stopping mysql and then doing a another(quick) sync after mysql has been stopped.
Usage:
You will have to "chmod 777 move-mysql-database.txt" to make it executable and possibly rename it to suit your needs.

move-mysql-database.txt <from dir> <to dir> <mysql conf file>
   <from dir> must not include ending slashes e.g. /var/lib/mysql
   <to dir> must not include ending slashes e.g. /mysql_data
   <mysql conf dir> is the full filename of my.cnf e.g. /etc/mysql/my.cnf
   so to move from the standard location to /mysql_data
       move-mysql-database.txt /var/lib/mysql /mysql_data
OR
   move-mysql-database.txt where
     to find out where the running mysqld looks for my.cnf

If the source directory does not exist it will abort.
If the destination directory does not exist it will create it(after you confirm it should) and set owner/group to mysql and permissions to 711. If it exists it will ask you whether it should remove the files in it - BEWARE THAT YOU ONLY REMOVE THE DATA FILES. The remove will remove all ibdata* files(mysql default names for innodb data files).

It uses rsync to copy the files (found example on cPanel forum).
It uses sed to replace the old directories with the new location - note that only innodb_home_directory will be updated to the new location(or inserted if it does not exist). It only syncs ibdata* files, not the complete directory.

It is strongly advised not to move the innodb datafiles to the mysql ('datadir' entry in my.cnf) directory.

It can be run while mysql is up. It will stop it at the appropriate moment and restart it after the change is complete. If mysql server is not running when the script is run, it will leave it not running, you will have to execute it by hand.

if it fails to restart mysql server, it will copy back the backup of my.cnf and restart with the old configuration (if mysql server was running when the script was started).

This new version does a lot more checking to try and prevent accidental corruption of the mysql database or installation.

The main intention of this script is to move the innodb datafiles if you run into a (potential) space problem and need to move the files to a directory with more space or to move the innodb files to a different location from the mysql files(datadir directive in my.cnf) after having set up the database(what I needed it for).
The general flow is:

1. Checks current running mysql uses the entered source directory and some further basic checks
2. Check target dir exists and deletes ibdata* files from it, or creates the target directory.
3. rsync (twice) ibdata* from source to target, leaving source intact
4. Change my.cnf to reflect new target dir for 'innodb_data_home_dir'
5. Stop mysql
6. rsyncs ibdata* from source to target, leaving source ibdata* files intact. This one should be really quick.
7. Restarts mysql (if it was running)
8. Checks if mysqld is running and if not, revert to saved my.cnf and try starting again.
9. Check that the running mysqld is using the new locations.
10. Checks that innodb-file-per-table is not set for mysql version < 5.6 as the older versions does not support a location other than the 'datadir' setting.
11. innodb-file-per-table is not yet implemented as I don't have 5.6 installed yet - the script will terminate with a message.

I hope it is useful to somebody.

---

### Post by shumifan50 on 2012-10-05
Found a serious flaw in the script:
If my.cnf does not have an entry for "innodb_data_home_dir" or the current directory setting for it does not match the 'from directory' entered, then it will not be updated correctly and the old configuration will still be used, even though the new directory has been created.

I am working on fixing this. Any help on using a Linux util to insert the entry if it is not there will be appreciated, otherwise I will have to write a program to do the update[SOLVED using sed]. It has to follow the [mysqld] setting, prefered after the InnoDB comment:
```

[mysqld]
...
# * InnoDB
innodb_data_home_dir = /var/lib/mysql
...
...

```

NEW VERSION UPLOADED - see first post

---

### Post by shumifan50 on 2012-10-07
Somewhat improved version  updated on the first post.
1. Added lots of error checking.
2. Added move-mysql-database.sh where
The where option will print out the order in which the running mysqld reads my.cnf files and indicate which one(s) exist.

---

