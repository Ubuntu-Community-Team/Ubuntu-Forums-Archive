---
title: "Backup script considering file dates"
date: 2007-02-18
forum: Programming Talk
---

### Post by jconnett on 2007-02-18
Greetings.

Firstly, let me just say that the entire ubuntuforums site has been a very valuable resource to me in my efforts to learn linux and, specifically, Ubuntu.

I run a server at my church that uses sbackup.  Those of you who have used this program know that it will create a file for each backup that's initiated.  I have mine incrementally backing up every day and doing a full backup every 7 days...so I either have a FULL or INCREMENTAL backup file created each day of the month.

I'd like to find a way to better manage these incremental files as they fill up my hard drive quickly.

Here's what I'd like for the script to do the FIRST DAY of each month (I already know how to set up the cronjob):::

1) search my backup folder for all files with a time/date stamp in the previous month (this is Feburary, so search for all files in /backup that have a date stamp in January)
2) tar those files into one single file, naming it the month and year of the backup. (so...if I'm tar-ing all January backup files, the filename should be January07.tar (or 0107.tar)...something like that.
3) delete all the individual files just compressed into a single file (so...if I'm deleting all of January's backups, I'll be deleting 31 individual files.)

Any scripting gurus that would like to take a crack at this?  Of course, I'll test your creation on test files to verify it works before putting it into "production" and let you know the results.

Again, my thanks!
--Jim

---

