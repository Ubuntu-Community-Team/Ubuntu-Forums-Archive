---
title: "bash script: &quot;*&quot; files exist?"
date: 2007-03-01
forum: Programming Talk
---

### Post by tocleora on 2007-03-01
[SIZE="2"]I'm creating a bash script that moves files to external usb drives, will do this every day.  The problem I'm running into is that the log files I'm moving are by date, but also by an employee id that may change over time.  I've got this command working:

```
if [ ! -f "$DRIVENAME/LOG/filename.log" ]; then
```

But I need to just generally check to see if log files exist in that directory, I want to see if any log file exists in $DRIVENAME/LOG before deleting the log files off of the original server.  Unfortunately this:

```
if [ ! -e "$DRIVENAME/LOG/*.log" ]; then
```

says no files exist (they do and if I put a specific file name in, it reports that it exists correctly).  is there an easy way to do this? TIA...[/SIZE]

---

### Post by ghostdog74 on 2007-03-01
i chose to use find instead
```

find $DRIVENAME/LOG -type d -name "*.log" -exec rm -f {} \;

```

---

### Post by tocleora on 2007-03-01
And how would I use that in a bash script?

---

### Post by tocleora on 2007-03-01
Oh I think I understand, I would just run that... thanks.

---

### Post by tocleora on 2007-03-05
> **ghostdog74 said:**
> i chose to use find instead
```

find $DRIVENAME/LOG -type d -name "*.log" -exec rm -f {} \;

```

Ok, apparently this isnt going to work as the {} is the file in $DRIVENAME/LOG, where I want to delete the original file if the one in $DRIVENAME/LOG exists.  Any thoughts?

---

### Post by Mr. C. on 2007-03-05
First, lets take a look at your original idea of:


if [ ! -e directory/* ]
  ...

Will this work?  Think about how many arguments does the test -e function accept ?

If there were 5 file, what would the -e mean?  1 file exists, 2 files exist, any files exist ?

After you've understood the above, help me understand the problem a little better.  I'm understanding:

you have directory A, and you want to move files to directory B.  And you want to remove the log file for user X from directory A only after that log has been copied successfully to directory B ?

If that's all you want, the mv command will take care of that for you.

Help us understand your question better.

MrC

---

### Post by ghostdog74 on 2007-03-05
> **tocleora said:**
> Ok, apparently this isnt going to work as the {} is the file in $DRIVENAME/LOG, where I want to delete the original file if the one in $DRIVENAME/LOG exists.  Any thoughts?

if should be ```
find $DRIVENAME/LOG -type f -name "*.log" -exec rm -f {} \;
``` . This says find all *.log files in  $DRIVENAME/LOG and remove them .

---

### Post by Mr. C. on 2007-03-05
For ghostdog74,

Use xargs instead of -exec rm.  The -exec in find will run an rm command for every file found - that could add up to thousands of rm commands run.  Very slow.

Instead use something like:

 find dir -name "*.log" | xargs rm -f

If this solves the OPs problem, we're done.  But if not, I'd still like a clarficiation if the OP is interested.

MrC

---

### Post by tocleora on 2007-03-07
> **ghostdog74 said:**
> if should be ```
find $DRIVENAME/LOG -type f -name "*.log" -exec rm -f {} \;
``` . This says find all *.log files in  $DRIVENAME/LOG and remove them .

That's not what I want to do. I don't want to remove the files I found, I want to remove the original files if I find the copied files.  I could do a mv as Mr. C pointed out but these log files are extremely valuable (as I'm now finding out the hard way as we lost two hours of them Monday and it's causing about 20 people in our company some headaches) and I just thought copying, then making the sure the files were successfully copied before deleting the originals would be the safest.  Am I overthinking it?

---

### Post by tocleora on 2007-03-07
> **Mr. C. said:**
> 
Instead use something like:

 find dir -name "*.log" | xargs rm -f



Yeah that still doesn't work as it attempts to rm -f the file it found.  

Ok, here's the scenario.

1. I have log files in /var/www/html/logs
2. I'm copying them to /media/usbdisk/YYYYMMDD (where YYYYMMDD is the current date)
3. Then I want to verify log files exist in /media/usbdisk/YYYYMMDD
4. If they do exist, delete the log files in /var/www/html/logs

I don't have to verify specific log files exist, just log files in general, I'm going to assume if there's a .log file of any kind in that directory then overall it was successful.  But I guess it would be smarter to verify each one in case like, the hard drive fills up or something.  Also, ultimately it would be nice if I could get an if/then statement to work as I might eventually run a series of commands if those logs (or other files I copy over) are found, but I'll take what I can get. :)

Hope that makes more sense. :)  Thanks guys!

---

### Post by tocleora on 2007-03-07
I guess what I could do, this would be kind of hokey so if there's a better way I'm open, but something like:

rm -f ~/found

find /media/usbdisk/YYYYMMDD -name "*.log" | xargs touch ~/found

if [ -e ~/found ]; then
rm -f /var/www/html/logs/*.log
fi

Is that the best way to do it?

---

### Post by Mr. C. on 2007-03-07
> **tocleora said:**
> That's not what I want to do. I don't want to remove the files I found, I want to remove the original files if I find the copied files.  I could do a mv as Mr. C pointed out but these log files are extremely valuable (as I'm now finding out the hard way as we lost two hours of them Monday and it's causing about 20 people in our company some headaches) and I just thought copying, then making the sure the files were successfully copied before deleting the originals would be the safest.  Am I overthinking it?

The mv command will NOT remove a file until the copy is successful.

The mv command simply changes the name of the file, with the move is on the same filesystem.  This is harmless.

The mv command COPIES the file when the destination file system is not the same as the source file system.

You have nothing to worry about.  Any lost files we not due to the mv command.

Your step 3 below is unnecessary, and misses the point.  You want to verify that the "mv" command returned a successful status instead.

```

mv source destination/dir
if [ $? = 0 ] ; then
  echo good move
else 
  echo bad move
fi
```

Easier ways to do this is to learn to use tar.

---

### Post by tocleora on 2007-03-07
> **Mr. C. said:**
> Easier ways to do this is to learn to use tar.

Aaah yes, that's a great idea, then I'm just working with one file! and it compresses!(?) Thanks!

---

### Post by Mr. C. on 2007-03-07
Tar itself doesn't; it calls helper programs

tar -cz backup-logs.tgz file1 file2 ...

MrC

---

