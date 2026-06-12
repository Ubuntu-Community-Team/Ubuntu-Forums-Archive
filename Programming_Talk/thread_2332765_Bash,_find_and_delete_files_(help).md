---
title: "Bash, find and delete files (help)"
date: 2016-08-03
forum: Programming Talk
---

### Post by Drenriza on 2016-08-03
Hi all

As many others i have created my own backup solution (Bash) for a tailored system, which works just as expected.
Now i've reached the stage that i also need to delete unwanted backups and here i have a question i am hoping to get a little help with.

All my backups follow the same pattern
year-mm-dd-week-timestamp.full.dir
year-mm-dd-week-timestamp.inc.dir

_**Question**_
During a week i dont necessarily end up with 7 backups, since some days i do more than one incremental backup.
So lets say i want to delete backups for two weeks, and this equal 20 backup folders.

How can i in Bash say "find & delete 2x X.full.dir backups + all associated inc backups"?

I am not a programmer, so i dont know the technical term for the above.
If their is a smarter way of doing the above please let me know so i can learn.

Thanks on advance!!
Kind regards

---

### Post by smartmagnet on 2016-08-05
I cannot specifically answer your question but an alternative solution to your question would be to either user 'tar' or 'rsync' for your backups.

tar - can archive your files, sort of like zip, and store the archive file wherever you want in a tar container.
rsync - can mirror your files from a source to a target destination.

Rsync has its advantages in that the same files are mirrored on both ends.  For example, if I wanted to mirror all my files in /home/user to an external USB hard drive.  I would do something like this:

rsync -auvz --delete /home/user/ /mnt/usbexternaldrive/HOME_BACKUP/

OR

[If you don't want the archive attributes mirrored to the target destination]
rsync -ruvz --delete /home/user/ /mnt/usbexternaldrive/HOME_BACKUP/

Notice the option -delete which will delete extraneous files from the target destination.  Which means rsync will always mirror the source and the target destination by adding or deleting any files that do or does not exist in the target destination.

I strongly suggest running various rsync dry run in a test environment to familiarized yourself.  rsync will remove folders and files without prompting, so you really have to be extra careful with the options you choose along with specifying the correct absolute pathname.

---

### Post by Drenriza on 2016-08-10
Thanks for the reply!

I create the backups already with rsync and a series of options (no --delete since i dont need).

For those who are interested.

I decided to create a small Java snippet that find the correct week, start and end date for backup folders i need to delete.

_I have no doubt that this can be done in Bash, but i dont know how._

```

ZoneId zoneId = ZoneId.of("Europe/Copenhagen");
ZonedDateTime timeNow = ZonedDateTime.now(zoneId);
        
 int week = timeNow.get(IsoFields.WEEK_OF_WEEK_BASED_YEAR);
        
LocalDate firstDayOfWeek = LocalDate.now().with(IsoFields.WEEK_OF_WEEK_BASED_YEAR, week).
     with(TemporalAdjusters.previousOrSame(DayOfWeek.MONDAY));
LocalDate lastDayofWeek = firstDayOfWeek.plusDays(6);

```

Result
> 
Current week number: 32
Start date: 2016-08-08
End date: 2016-08-14


---

### Post by SeijiSensei on 2016-08-10
Use the date command with appropriate formats; for instance, "date +%Y-%m-%d" returns "2016-08-10".  In scripts, you can put the string into an environment variable like this
```
TODAY=$(date +%Y-%m-%d)
```
then refer to it as $TODAY.

Look at "[man date]("http://linux.die.net/man/1/date")" for a complete list of format codes.

---

### Post by Drenriza on 2016-08-25
Thanks for the reply @SeijiSensei

---

