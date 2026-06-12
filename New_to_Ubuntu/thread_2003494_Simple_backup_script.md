---
title: "Simple backup script"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by madcharlie61 on 2012-06-14
Hi people 

I am new to linux and thought id try write a script to back up my user folder i just used cp to do it and used -ruv i have just backed it up to the home folder what i want to do is get this script to autorun when in plug in my usb drive.

i understand i will have to make the destnation the usb drive but i need to be pointed in the right direction on how to get the auto run to work

---

### Post by CharlesA on 2012-06-14
I've heard of people using udev to run scripts:
[http://www.banquise.org/hardware/how-to-automatically-run-a-script-after-inserting-a-usb-device-on-ubuntu/](http://www.banquise.org/hardware/how-to-automatically-run-a-script-after-inserting-a-usb-device-on-ubuntu/)

As for using cp - why not just use rsync? I use rsync -ai --delete /path/to/source /path/to/destination

---

### Post by madcharlie61 on 2012-06-14
i used cp cos it seamed to do the job and useing the -u part only copys new stuff to make it faster. what does r sync do better than cp.

Just asking i like to know why something is better than another.

---

### Post by CharlesA on 2012-06-14
rsync only copies the parts of files that have changed. I haven't used cp with -u, so I don't know if it is the same thing,  but judging from the man page, using -u copies the whole file if the source is newer than the destination.

---

### Post by madcharlie61 on 2012-06-14
That does sound better and i think your right the cp -u does copy the whole file thanks for  that.

---

### Post by CharlesA on 2012-06-14
> **madcharlie61 said:**
> That does sound better and i think your right the cp -u does copy the whole file thanks for  that.
Welcome.

Check out the man page:
[http://linux.die.net/man/1/rsync](http://linux.die.net/man/1/rsync)

---

### Post by woppie on 2012-06-14
How about cron. You can use that to run the script every so often.

---

### Post by CharlesA on 2012-06-14
> **woppie said:**
> How about cron. You can use that to run the script every so often.
That is true. However you would need the script to check to make sure the drive is mounted before trying to backup.

That's how I have my daily backups set up, but if you just want to do a backup when a drive is plugged in, udev seems to be the way to go.

---

