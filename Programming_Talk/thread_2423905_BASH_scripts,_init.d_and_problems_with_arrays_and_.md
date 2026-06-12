---
title: "BASH scripts, init.d and problems with arrays and zenity"
date: 2019-07-31
forum: Programming Talk
---

### Post by jeremybearemy on 2019-07-31
Hi all, long-term but low-knowledge linux user here. Not entirely sure if I'm in the right place, but here goes: I wrote a BASH script to back up my Ubuntu boxen in various ways. All good so far until I tried to modify it to detect when a drive is plugged in so it can back up automatically. The only way I could think of was to code a daemon mode for the script and start it with an init.d script. It mostly works fine, but there's a couple of bits that don't.

First, I load the output of grepped blkid and lsblk commands into arrays with

```
a=($(blkid | grep $UUID))
```

and

```
a=($(lsblk | grep $DEVICEURI))
```

Now, I can create a service okay and set it running manually, but the array comes out malformed. For debugging, I checked that the output of blkid and lsblk was what I was expecting, and it was, but the array element I'm looking at, instead of containing, for example, the mount point of the volume, contains the word MOUNTPOINT. And in other situations the array elements I'm after are just blank. When I use this method for other non-daemon-mode parts of the script it works fine.

I have no idea why this is happening, so any clues would be really very helpful.

Another issue is that, while in daemon mode, the script uses zenity to let me know when backups are started and completed, but this doesn't work. If I start the script with

```
sudo /etc/init.d/backup start
```

I get the zenity dialog boxes pop up okay, but if I start with 

```
sudo service backup start
```

or if the service starts at boot time, zenity errors out with something like "could not access display." Now I'm assuming that's because init.d scripts don't by default have access to the display, but I don't know how to give my script that access. Is this possible, or am I barking up the wrong tree?

If you want to see the code itself, it's at [my github page]("https://github.com/hp6000x/backup.sh_2.1_WIP/blob/master/backup.sh")

I'd suggest opening it in geany or similar, because there's a lot of functions there and it's getting close to a thousand lines. The functions of interest here are doCreateStartupScript, doDestroyStartupScript and daemonMode

I'd be immensely grateful for any help and advice on this matter as it's completely stumped me.

---

### Post by SeijiSensei on 2019-07-31
I can't answer your array question, but I can show you the code I use to make sure the external device I use for backups is mounted. I mount the device to /media/external.

```

echo "Checking for backup device" >> $LOG 
# check that backup device is mounted 
TEST=$(df | grep "/media/external") 
if [ "$TEST" = "" ] 
then 
    # not mounted try remounting 
    umount -f /media/external 
    sleep 4 
    mount /media/external
    sleep 4 
    
    TEST=$(df | grep "/media/external") 
    if [ "$TEST" = "" ] 
    then 
        echo "Cannot mount backup device!" >> $LOG
        echo 'Cannot mount backup on server' | mail -s 'backup failure' admin 
        exit 1 
    fi 
fi

```

---

### Post by jeremybearemy on 2019-07-31
Thanks for that, but I'm able to mount the drive in the right place no problem, it's just that for neatness' sake I like to unmount it if it's mounted elsewhere before I mount it to the correct mountpoint, and to do that I need to catch the output of blkid and lsblk, and the simplest way I can do that is by stuffing it into an array

---

### Post by aromo2 on 2019-07-31
For your first problem, you can try something like this:
```

deviceid=$( blkid | grep $UUID | cut -d: -f1 )
mountpt=$( lsblk -p | grep $deviceid | awk '{print $NF}' )

```

For the second problem, when you run it as a service you are sacrificing the access to the screen (a service is supposed to run in the background as a daemon). Therefore, you need to re-think how you want it to deliver its messages, perhaps creating syslog entries?

---

### Post by jeremybearemy on 2019-07-31
Thanks very much, I'll give that a try. Yeah, I'll have to ditch the dialog boxes; I'm already writing to a log file, so the info is there, I just wanted dialog boxes so if a less savvy user used it, they'd have the info.

Do you think the script would work if I started it via a script in /etc/profile.d rather than init.d or would it then run as the user and not root?

Edit

Forgot I also need to get the device id for a folder mounted at $BACKUPROOT to compare against the device id of my target device. Doing it the way that doesn't work, I'd just pull the first item from the array, but this way I'd have to get the output of lsblk and get from char 2 (starting at 0, of course) to just before the location of the first space. so I think I would need something like

```

a=$(lsblk -p | grep $BACKUPROOT)
a=${a/ */}
deviceid=${a:2}

```
Does that seem correct to you?

---

### Post by jeremybearemy on 2019-07-31
Yup, that's done the trick perfectly, thank you very much aromo2. The script now unmounts and mounts like a champ. Marked as solved.

I'm curious to know how that awk pipe you gave me works, I have zero experience with awk and printf.

---

### Post by aromo2 on 2019-07-31
My pleasure, I'm glad it worked for you.
In awk the variable NF is the number of fields (default separator is a blank space), $1 is the first field , $2 the second and so on. Therefore, $NF is the last field of the line.
awk is very useful, I suggest you read up on it if you're serious in bash scripting.

Cheers!

Edit: if you want to exclude $BACKUPROOT from being detected, try ```

mountpt=$( lsblk -p | grep $deviceid | awk '{print $NF}' | grep -v $BACKUPROOT ) 
```

Edit2: Yeah, /etc/profile.d will run it as the user, not as root.

---

