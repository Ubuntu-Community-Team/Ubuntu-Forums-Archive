---
title: "system restore in ubuntu?"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by macvr on 2008-08-18
hi,i'm new to ubuntu
does ubuntu have a system restore option? like the one in windows?

if its there , i'm not able to find it!

---

### Post by meanburrito920 on 2008-08-18
Nope, no system restore. But dont panic! It doesn't need it because it is so much easier just to make constant incremental back ups. do a google search for 'making backups in linux' and you'll find tons of info on it, or just search the forum for it. There have been plenty of posts on the subject.

---

### Post by wolfen69 on 2008-08-18
there are many disc imaging programs out there. acronis is one of my favs.

---

### Post by aktiwers on 2008-08-18
I use PartImage
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

Very nice program

---

### Post by macvr on 2008-08-18
ok , so backup can be done and used like system restore? that is what u are saying?

so i checked out the synaptics and found 2 softwares
backuppc
bacula

in add/remove programs i found:
simple backup
home user backup


which is easier? pls keep in mind i'm new to linux[ so preferably with a gui, but complete user settings backup ]

i could install them and check it out but i thought a could use  suggestions

---

### Post by aktiwers on 2008-08-18
I know the install is not totally newbie friendly, but have a look at this program

[http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)

[IMG]http://lh5.ggpht.com/kered.org/RzvnQ-7GiWI/AAAAAAAAAZI/sAofEdkcO6M/s512/Screenshot-flyback.png[/IMG]

The installation instructions are on the site!

---

### Post by macvr on 2008-08-18
ok will give it a try... thanx

---

### Post by hyper_ch on 2008-08-18
I rather prefer incremental snapshot-style backups. I make everyday a "full" backup and keep it for 90 days.

---

### Post by macvr on 2008-08-18
> **hyper_ch said:**
> I rather prefer incremental snapshot-style backups. I make everyday a "full" backup and keep it for 90 days.

using which software?

---

### Post by hyper_ch on 2008-08-18
using the power of rsync and hardlinks and a little shell script.

backup.sh
```

#!/bin/bash
unset PATH

# USER VARIABLES
BACKUPDIR=/backup        # Folder on the backup server
MYSQLUSER=root
MYSQLPWD=************
MYSQLHOST=localhost
MYSQLBACKUPDIR=/mysql_backup
EXCLUDES=/backup/backup_exclude        # File containing exludes
DAYS=90         # After how many days shall the backups be deleted?

# PATH VARIABLES
CP=/bin/cp;
MK=/bin/mkdir;
DATE=/bin/date;
RM=/bin/rm;
GREP=/bin/grep;
MYSQL=/usr/bin/mysql;
MYSQLDUMP=/usr/bin/mysqldump;
RSYNC=/usr/bin/rsync;
TOUCH=/bin/touch;
FIND=/usr/bin/find;

##                                                      ##
##      --       DO NOT EDIT BELOW THIS HERE     --     ##
##                                                      ##

# CREATING CURRENT DATE / TIME
$MK $BACKUPDIR/current
$MK $BACKUPDIR/old
NOW=`$DATE '+%Y-%m'-%d_%H:%M`
MKDIR=$BACKUPDIR/old/$NOW/
$MK $MKDIR

# CREATE MYSQL BACKUP
# Remove existing backup dir
$RM -Rf $MYSQLBACKUPDIR

# Create new backup dir
$MK $MYSQLBACKUPDIR

#Dump new files
for i in $(echo 'SHOW DATABASES;' | $MYSQL -u$MYSQLUSER -p$MYSQLPWD -h$MYSQLHOST|$GREP -v '^Database$'); do
  $MYSQLDUMP                                                    \
  -u$MYSQLUSER -p$MYSQLPWD -h$MYSQLHOST                         \
  -Q -c -C --add-drop-table --add-locks --quick --lock-tables   \
  $i > $MYSQLBACKUPDIR/$i.sql;
done;

# RUN RSYNC INTO CURRENT
$RSYNC                                                          \
        -avzp --delete --delete-excluded                        \
        --exclude-from="$EXCLUDES"                              \
        /                                                       \
        /$BACKUPDIR/current ;

# UPDATE THE MTIME TO REFELCT THE SNAPSHOT TIME
$TOUCH $BACKUPDIR/current

# MAKE HARDLINK COPY
$CP -al $BACKUPDIR/current/* $MKDIR

# REMOVE OLD BACKUPS
for file in "$( $FIND $BACKUPDIR/old/ -maxdepth 1 -type d -mtime +$DAYS )"
do
  $RM -Rf $file
done

exit 0

```

---

### Post by macvr on 2008-08-18
> **hyper_ch said:**
> using the power of rsync and hardlinks and a little shell script.

backup.sh


ok i searched the add/remove and found Grsync the graphical interface for rsync, got it installed,
but dont know what hardlinks is!

and how to use the script u have given[where to place it,and save it as backup.sh?]

how do i restore from this method?

does this work like in windows, full restore of system to the saved date?

---

### Post by hyper_ch on 2008-08-18
try to understand the script. It's not that difficult.

And no, it's not a "restore" program. I just backups your data.

---

### Post by stalkingwolf on 2008-08-18
there is also Remastersys.  It gives you a choice of making a backup image or a distributable image.
Here,
[http://www.remastersys.klikit-linux.com/]("http://www.remastersys.klikit-linux.com/")
here,
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html")
and here
[http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys]("http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys")

---

### Post by macvr on 2008-08-18
> **hyper_ch said:**
> try to understand the script. It's not that difficult.

And no, it's not a "restore" program. I just backups your data.

well i dont know anything about computers, other than the fact that i use them[i dont know C+orC++, i dont know what those 2mean either:)] {should get to know more bout linux though}
, so i wouldnt be able to understand it, 
its just like greek and latin to me :), all i can see is that there are a few commands to create directories n that its being scheduled
[U]
i'm just using Ubuntu mainly since i got fedup with a few things in Windows![/U]

if it doesnt restore the system then probably 
flyback or a few of the other programs mentioned here seem good.

---

### Post by macvr on 2008-08-18
> **stalkingwolf said:**
> there is also Remastersys.  It gives you a choice of making a backup image or a distributable image.
Here,
[http://www.remastersys.klikit-linux.com/]("http://www.remastersys.klikit-linux.com/")
here,
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html")
and here
[http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys]("http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys")

wow this seems cool,:guitar:
 just would have to carry a live CD and could be used anywhere, with all our customizations,
 would definitely make a live CD copy , just for emergency use, 
:guitar:

---

### Post by hyper_ch on 2008-08-18
> **macvr said:**
> all i can see is that there are a few commands to create directories n that its being scheduled

That's a good beginning...

The script itself isn't difficult to understand. You can lookup what each command does and then you will also understand it.

---

### Post by macvr on 2008-08-18
> **hyper_ch said:**
> That's a good beginning...

The script itself isn't difficult to understand. You can lookup what each command does and then you will also understand it.

hei,u seemed to know ur way around ubuntu>>> so i had sent u a pm  to look up 2 other of my threads that are unsolved, did u get it?

i thought that asking u to look at them via this thread would be out of topic, thts y i sent pm, hope u didnt take offence

---

### Post by hyper_ch on 2008-08-18
> **macvr said:**
> hei,u seemed to know ur way around ubuntu
I just pretend to know a few things about ubuntu...

but you should have a read at my sig. Especially the **bold** part of it.

---

### Post by macvr on 2008-08-18
> **hyper_ch said:**
> I just pretend to know a few things about ubuntu...

but you should have a read at my sig. Especially the **bold** part of it.

NO, NO, wasnt asking for private support,[i'v read sticky,how people hate requests for private support]
 it is just to keep it strictly in the forums, thought u might have missed previously, so instead of me bumping it again , just was directing u to those threads, guess bumping is the best way !!!

---

### Post by stalkingwolf on 2008-08-31
> just would have to carry a live CD 
after you make your customizations it usually requires a DVD, at least
it did for me.  I keep one at work along with a usb wifi adapter.
You would be surprised at how many windows users dont have wifi drivers
installed or have some wifi manager that they cant find.  I just plug in the adapter, boot ubuntu, and off they go.  another satisfied guest.

---

### Post by macvr on 2008-08-31
> **stalkingwolf said:**
> I keep one at work along with a usb wifi adapter.
which method did u use to create the live DVD?

cant i create a liveCD using remastersys containing just my customizations and no other backup files?
since a lot of old system [tht i know of] just have a CD drive than a DVD drive!

---

### Post by macvr on 2008-09-05
remastersys does not work on ubuntu 8.04.1
Hardy uses genisoimage, but remastersys was developed for mkisofs
have reported it to the developer
[http://loscompanion.com/forums/index.php?topic=4897.0]("http://loscompanion.com/forums/index.php?topic=4897.0")

 he says that a new version will fix the issue, untill then, remastersys doesnt work on ubuntu 8.04.1

or does any1 know a workaround?

---

### Post by Bucky Ball on 2008-09-05
[quote=hyper_ch]I just pretend to know a few things about ubuntu...[/quote]

Aw, hyper ... so humble!

Macvr: partimage rocks for me, maybe a little further down the track you will find that a quick and easy method too.

In terminal

**sudo apt-get install partimage**

Then:

**sudo partimage**

and follow thy nose, as they say ... :)

---

### Post by macvr on 2008-09-05
> **Bucky Ball said:**
>  partimage rocks for me, maybe a little further down the track you will find that a quick and easy method too.

In terminal

**sudo apt-get install partimage**

Then:

**sudo partimage**

and follow thy nose, as they say ... :)

partimage seems nice for restore...

do u have any other  replacements for remastersys?[create a live CD of the customized install?, with an option to install from the live CD?]

---

