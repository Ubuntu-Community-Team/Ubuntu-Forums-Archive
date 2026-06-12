---
title: "How To Scheduled Backups -- rsync and tar"
date: 2006-08-20
forum: Outdated Tutorials &amp; Tips
---

### Post by tagra123 on 2006-08-20
How To Backup A Ubuntu System with hourly, daily, and weekly backups.

Several different scripts are used:

Start a Terminal:
MENU: Applications > Accessories > Terminal

Type in the following commands:
***********************************************************************
First make sure tar and rsync are installed
***********************************************************************

```
sudo apt-get update
sudo apt-get install tar
sudo apt-get install rsync
```


***********************************************************************
Second &#8211; Install and Edit The Scripts.
***********************************************************************

```
cd ~
sudo mkdir myscripts
sudo chmod 666 myscripts
cd myscripts

wget http://www.watchtv.net/~graham/linux/how-to-backups/backupscripts_FILES.tar
wget http://www.watchtv.net/~graham/linux/how-to-backups/cron-root.txt
tar -xvf  backupscripts_FILES.tar -C ~/myscripts/

chmod +x *.sh
```


Edit the scripts and exclude file to meet your needs. All that really needs to be changed is to change the path to your scripts and select the files and directories to backup.

The following scripts can be edited (just follow the instructions and examples within the scripts)
 
a-hourly-big-snapshot.sh
a-daily-big-snapshot.sh
a-weekly-big-snapshot.sh

```
gedit a-hourly-big-snapshot.sh 
```

Change the paths to match your system and save the file. Use the same procedure for each file.

An include and exclude file is included in the example. You can add as many include or exclude files for the different folders that you have or you can add them for the hourly, daily, or weekly scripts.


***********************************************************************
Third &#8211; Setting Up the Cron Jobs
***********************************************************************
**For ubuntu users use METHOD 1** (I believe this is the preferred way on Ubuntu)

[U]METHOD 1 UBUNTU ROOT CRON JOBS in the /etc/crontab file
[/U]
```
sudo gedit /etc/crontab 
```

The text editor will open.

Add the following lines at the end of the existing text.


```

#
#Hourly Backups - This is set for a backup at 10 minutes after each hour listed
10 0,1,2,3,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23 * * * root /home/YOURUSERNAME/bin/myscripts/rsbackups/a-hourly-big-snapshot.sh
#
#Daily Backups - This backup is set to run at 4:01 AM each day
01 04 * * * root /home/YOURUSERNAME/bin/myscripts/rsbackups/a-daily-big-snapshot.sh
#
#Weekly Backups - This backup is set to run at 5:01 AM each Sunday
01 05 * * 0 root /home/YOURUSERNAME/bin/myscripts/rsbackups/a-weekly-big-snapshot.sh
 
```

------------------------------------------------------------------------

[U]METHOD 2 CRON JOBS (easier - another way to set up cronjobs )
[/U]

**You can skip this section if you used METHOD 1.**

Set up the cron jobs as root.

First check to see the existing root cron jobs:

```
sudo crontab -l
```

The above command will list the existing jobs, be sure to include these in the file below if you need them.  On some systems nothing will be listed with the above command &#8211; that just mean there are no cron jobs. Make sure to issue the sudo command or make sure you are root if not using Ubuntu.

Now edit the cron-root.txt file manually using your favorite text editor. (You will need to change the paths to match your system)

```
gedit crontab-root.txt 
```

Change the paths to match your system and save the file.

```
sudo crontab crontab-root.txt 
```    

(This overwrites the existing jobs and copys the contents to the crontab)
--------------------------------------------------------------------------

Backups are now automatic.

************************************************************************
RESTORING FILES:

For the RSYNC files you can either copy the needed file(s) back to the original directory or use rsync.

For the Tar Files you can open them in nautilus (the file manager) and extract them to the original location.


[B][COLOR="Red"]
FEISTY AND LATER (CHANGES)[/COLOR][/B]

/bin/sh no longer links to bash it is a link to dash and does not let the line containing "let" work correctly.

Simply change the #!/bin/sh to #!/bin/bash in the mtar-rotate-backup.sh scrpt and everyhthing then works correctly. With out adding the old backups will stop deleting and you will run into problems with too many backups accumulating

---

