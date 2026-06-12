---
title: "Scheduling Backups to NAS and waking from suspend"
date: 2013-12-27
forum: New to Ubuntu
---

### Post by steveearle86 on 2013-12-27
Hi there,
I have been using Ubuntu 13.10 and have just about got it as I want. The only outstanding issue which is causing me a lot of headache is scheduled back ups.

What I want to do is this: Every 4 weeks at 12:00, wake the computer from suspend, backup the home folder to the NAS drive (and delete the previous backup), suspend again.

I have mounted the NAS as a bookmark using the instructions here [http://www.youtube.com/watch?v=CGd0M3gNUCo](http://www.youtube.com/watch?v=CGd0M3gNUCo)
Now every time I restart the PC, the NAS is a bookmark and I can click it and it loads the files no problem.

I have tried a number of applications and can't seem to get a solution to what seems to be a simple problem!
I am thinking that a command line solution using cron would maybe be the best bet

Can anyone help me out here please?
Thanks

---

### Post by steveearle86 on 2013-12-30
I have been doing a bit of playing and am getting there. I have this:

First, map the NAS drive as a local folder called NAS (as opposed to a bookmark which I was doing previously):
> sudo mount -t cifs -o username=steve //192.168.2.8/Volume_1 /NAS

Backup home folder and sleep
> sudo rsync -av /home/steve/ /NAS && sudo pm-suspend

The problem is that each time I restart, the drive needs mounting again, secondly, the command gives Permission Denied (13) for each file it tries to copy. When I change the rsync command to copy to a different folder (IE one on the local hard drive) it works perfectly.

Any ideas?

---

### Post by tgalati4 on 2013-12-30
Put the mount in your /etc/fstab.  The NAS probably does not accept root copy attempts as a security precaution.  You should be able to use *rsync* with your user privileges to copy your home account to the NAS.  Otherwise, you don't have your NAS set up correctly.

---

### Post by steveearle86 on 2014-01-09
I have now completed this. Solution as follows:

1. Auto mount the NAS as a local folder:
-Edit fstab with gedit. Add the following as a line at the bottom of the file
> //<nas ip address>/<folder to mount> /NAS cifs credentials=/home/<nas username>/.smbcredentials,uid=<nas username>,gid=<nas username> 0 0

2. Create shell script to run rsync and when complete, suspend the PC
-in emacs, create new file
-insert following:

> #!/bin/sh

#Backup
sudo rsync -av /home/<user> /NAS/Bedroom && sudo pm-suspend

-save as home/<user>/backup.sh
-make the script executable:>  chmod +x /home/<user>/backup.sh

3.Use Cron to run the script at a specified interval
-edit the root crontab: > sudo crontab -e
-add the following to crontab file to run backup .sh at 12 noon on the 1st of the month
> 00 12 1 * * /home/<user>/backup.sh

4.create script to suspend PC and wake at 11:55 on the 1st of the month
-in Emacs, create shell script and save as suspendandwake.sh
> #!/bin/bash

#current system time and waketime
old=`date '+%H:%M'`
new=11:55


THISYEAR=`date +'%Y' -d 'now'`
NEXTMONTH=`date +'%m' -d 'next month'`


#if next month is January, increment the year by 1
if [ $NEXTMONTH == 01 ]
then
    THISYEAR=`date +'%Y' -d '1 year'`
fi


#current system date and wake date(1st of next month)
olddate=`date +%Y-%m-%d`
newdate=$THISYEAR"-"$NEXTMONTH"-01"


IFS=: read old_hour old_min <<< "$old"
IFS=: read hour min <<< "$new"


# convert the date in seconds from Unix EPOCH time
sec_old=$(date -d "$olddate $old_hour:$old_min:00" +%s)
sec_new=$(date -d "$newdate $hour:$min:00" +%s)


DIFFERENCE=$(( (sec_new - sec_old) )) 


#suspend the system and wake in this many seconds
sudo rtcwake -m mem  -s $DIFFERENCE
-create a desktop launcher to run suspendandwake.sh and use instead of suspend option in menu bar

---

### Post by tgalati4 on 2014-01-09
That is exactly how I would do it.  One thing I would add, if there is an error in the rsync, send a text message to your phone.

---

### Post by steveearle86 on 2014-01-11
Thanks,
I am only struggling with a few final tweaks: 
[URL="http://ubuntuforums.org/showthread.php?t=2198622"]
http://ubuntuforums.org/showthread.php?t=2198622[/URL] <-- running suspendandwake.sh from launcher

and when putting the computer to sleep with the suspendandwake.sh script, when the computer wakes up, it doesn't go to the same login/lock screen that you see if you had suspended from the system menu bar, it just wakes straight back into your desktop which is not ideal.

---

### Post by steveearle86 on 2014-01-12
Launcher Suspend issue now sorted. Just need to find a way to lock the screen on wake.....

---

### Post by tgalati4 on 2014-01-12
Depending on what desktop environment you are running, there is a switch to lock the screen but it is found in screensaver settings.  Check both activate screensaver when idle and lock screen with screensaver.  This works for the most part, but there are some cases when the computer wakes without the screensaver and lock.  You could add a logout command after a successful rsync and that would require a login on the next wake cycle.

---

### Post by steveearle86 on 2014-01-14
I think I have found the command with xscreensaver. However, I am struggling to get ANY command to run from a script from wake.

As a test, I have created the following script:

```

#!/bin/bash 


echo "hello" >> /home/steve/test.txt


case "$1" in
    hibernate|suspend)
    #do nothing


        ;;
    thaw|resume)
        echo "THIS IS a test" >> /home/steve/test.txt
        ;;
esac

```

I have made this script executable by using chmod and place it in etc/pm/sleep.d and can run it from the terminal and outputs "hello" to the text file as expected. However, When restarting from suspend, there is no output to the file which suggests the file is not being run. I am using SuspendAndWake.sh above to suspend the PC.

Any idas why the script is not executing?

---

### Post by tgalati4 on 2014-01-14
Try sending the file to /tmp.  It's possible that sleep and resume are acting on other than root privilege as a security improvement.  And you should use test1.txt, test2.txt, and test3.txt so you can see which file gets written to and when.  Put an extra echo command in the suspend case so you can see that call as well.

---

### Post by Jason_Gibson on 2014-01-14
Deleted

---

### Post by steveearle86 on 2014-01-16
I have managed to narrow it down to an issue with rtcwake. I have the following amended file in etc/pm/sleep.d

```
#!/bin/bash 

echo "run" >> /home/steve/test.txt


case "$1" in
    hibernate|suspend)
	echo "suspend" >> /home/steve/test.txt




        ;;
    thaw|resume)
        echo "wake" >> /home/steve/test.txt
        ;;
esac

```

If I run ```
sudo pm-suspend
``` at the terminal, the output to the file "test.txt" reads

run
suspend
run
wake

as expected.

If I suspend the system with rtc wake: ```
 rtcwake -m mem -s 20
```, the text is not written to the file.

Any ideas on how I amend the rtcwake command in SuspendAndWake.sh above to put the system in the same sort of sleep as pm-suspend?

---

### Post by steveearle86 on 2014-01-16
Sorted,
Forget all the above. I fixed by modifying SuspendAndWake.sh by putting

```
xscreensaver-command-lock
```

before the final command.

Thanks for the help

---

### Post by steveearle86 on 2014-01-19
A couple of further tweaks having notices some bugs:

When restarting the system, chown settings are lost. Therefore I created a script called Chowner.sh:

```

sudo chown steve /dev/rtc
sudo chown steve /sys/power/state

```

I call this script from /etc/rc.local:

```

/home/steve/Chowner.sh

```

Also xscreensaver was not running after a restart. It needs adding as a new startup programs entry with the following command

```

xscreensaver -no-splash

```

Furthermore, there was a bug in backup.sh. I had put sudo at the beginning so it would ask for password. Furthermore, it does a suspend when complete, whereas I want it to do an rtcwake so it can wake again on the 1st of next month. backup.sh changed to:

```

rsync -av /home/steve /NAS/bedroom
/home/steve/SuspendWake.sh

```

---

### Post by steveearle86 on 2014-02-11
A few further amendments as the above was not sleeping the PC through the SuspendWake call when run through cron, however it was fine through the command line. I added the PATH line to the SuspendWake.sh and instead of calling backup.sh from the root crontab, made it run from the user's crontab.

Updated SuspendWake.sh

```

#!/bin/bash
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/home/steve/SuspendWake.sh
############################################################
##puts the system to sleep and wakes at the specified time##
##    (just before the cron job to run backup runs)       ##
############################################################


#current system time and waketime
old=`date '+%H:%M'`
new=11:55


THISYEAR=`date +'%Y' -d 'now'`
NEXTMONTH=`date +'%m' -d 'next month'`


#if next month is January, increment the year by 1
if [ $NEXTMONTH == 01 ]
then
    THISYEAR=`date +'%Y' -d '1 year'`
fi


#current system date and wake date(1st of next month)
olddate=`date +%Y-%m-%d`
newdate=$THISYEAR"-"$NEXTMONTH"-01"


IFS=: read old_hour old_min <<< "$old"
IFS=: read hour min <<< "$new"


# convert the date in seconds from Unix EPOCH time
sec_old=$(date -d "$olddate $old_hour:$old_min:00" +%s)
sec_new=$(date -d "$newdate $hour:$min:00" +%s)


DIFFERENCE=$(( (sec_new - sec_old) )) 


#lock the screen
xscreensaver-command -lock


#suspend the system and wake in this many seconds
rtcwake -m mem  -s $DIFFERENCE

```

---

### Post by steveearle86 on 2014-03-04
Ok, does anyone have any ideas how I would execute some code if rsync fails for whatever reason?

---

### Post by tgalati4 on 2014-03-04
Put *exit 0* at the bottom of your backup.sh script.  Put *exit 1* at the line of your rsync with an appropriate test for "did it work?".

```
man test
```

What errors are you seeing?

You can add switches to *rsync* such as --stats and --log-file then perform a test on the log file for size of the backup or some other meanful parameter.  If the test fails then exit 1 and use *logger* to make a system log entry that your rsync failed.

There is probably a more elegant way to do this, but I'm tired and it is late.

---

