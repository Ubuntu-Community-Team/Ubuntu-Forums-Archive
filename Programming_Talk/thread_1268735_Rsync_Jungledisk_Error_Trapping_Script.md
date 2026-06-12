---
title: "Rsync Jungledisk Error Trapping Script"
date: 2009-09-17
forum: Programming Talk
---

### Post by jimjawn on 2009-09-17
This is a cross post.  I couldn't figure out how to move it to this forum so I'm reposting.  I'll try to kill the other one.  Just seems like I'll get better answers in here.  Thanks...

Hey All,

I've recently started using jungledisk in combination with rsync to backup my files and I love it!  I have a backup.sh script with the rsync command that I run via cron each night.  However, I've found that sometimes, an error occurs either with the jungledisk daemon or my internet connection goes out and I don't realize it for a few days.  

Instead of checking each night to see if it sync'd up, I'd like to trap any errors that occur during the rsync.  I don't want successful emails, just errors.

I've done some simple bash scripting but I'm not sure how to go about checking for errors from the rsync command.  Can anyone point me in the right direction?  I know this involves grabbing the output from stdin/stdout but I'm not sure where to start.

Perhaps an explanation of these two lines:

```
rsync -az -e ssh --delete $HOSTTOBACKUP:$SOURCE $DR_BACKUP_DIR/daily.0 > $tempfile 2>&1
if [ $? -eq 0 ]

```
Thanks,

Jim

---

### Post by DaithiF on 2009-09-17
the >$tempfile 2>&1 at the end of the rsync command captures stdout and stderr output and directs it some file (defined previously in the script, denoted by the $tempfile variable)

The if [ $? -eq 0 ] says if the exit status from the previous command was 0 (meaning no error) then ....

but the ... part is not completed.  Maybe you want something like this:

```
if [[ $? -ne 0 ]]; then
    cat $tempfile | mail -s "Problem with rsync" yourname@email.com
fi

```

meaning if the exit status is non-zero (ie. some error occurred) then mail the contents of that tempfile to you.

(you will need to install a mail transfer agent program if you haven't already one installed)

---

### Post by DaithiF on 2009-09-17
forgot to mention, you may have noticed that I used [COLOR=Red]if [[  ... ]][/COLOR], rather than[COLOR=Red] if [ ... ][/COLOR] as in your snippet.  They are more or less the same, but [[   ]] is a feature built into the shell, whereas [ is an external program (/usr/bin/[ on my system).  

(just in case that difference was confusing.)

---

### Post by jimjawn on 2009-09-18
Sweet!  Thanks for the help.  I do have one other question.  So lets say I'm running rsync 5 times.  Is there an easy way to aggregate the responses and if any of the 5 rsyncs fail then, then email?

I guess the trick would be to append to a single text file but the $? result could differ depending on results of each command.  I'm guessing the if statement would change.

I guess export results of command1 ... command5 into rsync.err 

Then check the rsync.err file for an error
  error exists email rsync.err file

The logic is essentially the same but the semantics would differ.  How much harder would this be to accomplish?  

Thanks again man, I really appreciate it.

---

### Post by DaithiF on 2009-09-18
one way would be to accumulate the exit status results in a variable, at the end test if the variable is 0 (no errors), or if > 0 then you know how many errors occurred.

so after each rsync 
TOTAL=$(( TOTAL + $? ))

at the end:
if [[ TOTAL -gt 0 ]]; then
    echo "$TOTAL errors occurred..."
    # send email, etc.
fi

---

