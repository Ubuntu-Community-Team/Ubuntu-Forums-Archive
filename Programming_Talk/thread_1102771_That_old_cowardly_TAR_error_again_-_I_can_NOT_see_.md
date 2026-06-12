---
title: "That old cowardly TAR error again - I can NOT see the problem"
date: 2009-03-22
forum: Programming Talk
---

### Post by sofasurfer on 2009-03-22
EDIT: First off let me say that the subject line SHOULD say "I can NOT see the problem".
Now, on with my problem...
I created the script and it worked fine. Now, all of a sudden I get the "tar: Cowardly refusing to create an empty archive".
I am running it with "sudo".
Can anyone see the problem?


```

DOW=`date +%a`                                          #current day of week.. Mon, Tue
FULLBACKUPFILE=$DOW"fullarchive.1.tar"                  #full backup name
INCBACKUPFILE=$DOW"incarchive.2.tar"              #incremental backup name                       DIRECTORYNAME=/home/terry                               #directory being backed up

#Full weekly backup


cd /
if [ $DOW = "Sun" ]; then
  echo backing up $FULLBACKUPFILE
  tar cf $FULLBACKUPFILE --listed-incremental=/snar $DIRECTORYNAME

fi

```

The "echo" command works but the "tar" command must be giving the problem.

---

### Post by sofasurfer on 2009-03-22
I found that the problem is cured by adding a "/" before "$DIRECTORYNAME" in the tar line like this... 
tar cf $FULLBACKUPFILE --listed incremental=/snar /$DIRECTORYNAME

This was not nessessary before, so my question now, why did this need for a "/" suddenly occur?

I also am now getting these messages which were not occurring before...

```

tar: /home/daryl/.gvfs: Cannot stat: Permission denied
tar: /proc/6497/fd/5: Cannot stat: No such file or directory
tar: /proc/6497/fdinfo/5: Cannot stat: No such file or directory
tar: /proc/6497/task/6497/fd/5: Cannot stat: No such file or directory
tar: /proc/6497/task/6497/fdinfo/5: Cannot stat: No such file or directory

```

---

### Post by sisco311 on 2009-03-22
/proc and ~/.gvfs are virtual file systems created at boot time.
you can use the exclude them from the archive:
```
tar [options] --exclude=/proc --exclude=~/.gvfs [blabla]
```

why don't you use rsync?

---

### Post by sofasurfer on 2009-03-22
Because I am just obsessed with figuring tar out. I did use rsync a couple of time through a package I downloaded and which I do not remember what it was. There is so much damn confusion about the differant backup methods, each of which can be used through 4200 differant program packages and each of these can be configured in 5000 differant ways to accomplish 10,000 differant purposes. I just wanted to learn to operate the basic backup command and learn to option it my self.

Another problem that is occurring...
That directory that I am backing up (this is just practice) only is 294 kb in size but it backups up for at least 10 minutes and then I halt the operation. There is something bizarre going on.

Well, I'm going to bed soon. Maybe I will see the problem in the morning.

---

### Post by sofasurfer on 2009-03-22
I just ran the tar command with actual filenames instead of variables and it works perfect and backsup that little file in about one half second. Hmmmm...

---

