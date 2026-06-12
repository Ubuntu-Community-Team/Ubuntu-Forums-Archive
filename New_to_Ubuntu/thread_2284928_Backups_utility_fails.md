---
title: "Backups utility fails"
date: 2015-07-02
forum: New to Ubuntu
---

### Post by soundgeek on 2015-07-02
I have used the "Backups" utility which is packaged in Ubuntu to backup to my plug-in USB drive many times.

Now, as soon as I try Back Up Now, I get an error box with the message:
Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1494, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1488, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1337, in main
    do_backup(action)
  File "/usr/bin/duplicity", line 1366, in do_backup
    sync_archive(decrypt)
  File "/usr/bin/duplicity", line 1100, in sync_archive
    remote_metafiles, ignored, rem_needpass = get_metafiles(remlist)
  File "/usr/bin/duplicity", line 992, in get_metafiles
    pr = file_naming.parse(fn)
  File "/usr/lib/python2.7/dist-packages/duplicity/file_naming.py", line 389, in parse
    pr = check_full()
  File "/usr/lib/python2.7/dist-packages/duplicity/file_naming.py", line 308, in check_full
    t = str2time((m1 or m2).group("time"), short)
  File "/usr/lib/python2.7/dist-packages/duplicity/file_naming.py", line 281, in str2time
    t = dup_time.genstrtotime(timestr.upper())
  File "/usr/lib/python2.7/dist-packages/duplicity/dup_time.py", line 278, in genstrtotime
    return override_curtime - intstringtoseconds(timestr)
  File "/usr/lib/python2.7/dist-packages/duplicity/dup_time.py", line 190, in intstringtoseconds
    error()
  File "/usr/lib/python2.7/dist-packages/duplicity/dup_time.py", line 181, in error
    raise TimeException(bad_interval_string % interval_string)
UnicodeDecodeError: 'ascii' codec can't decode byte 0xe6 in position 15: ordinal not in range(128)

What does all this mean?

Help please, I need to back up!

---

### Post by leunam12 on 2015-07-03
Try fsarchiver to do your backups. Sorry, I know it's not a solution, just a workaround

---

### Post by cmcanulty on 2015-07-03
I love grsync very easy and reliable. If it finds any errors it still backs up and you can click on details to find the errant files.

---

### Post by RobGoss on 2015-07-03
Hello and welcome, I prefer Clonezilla works flawlessly [http://clonezilla.org/](http://clonezilla.org/)

---

### Post by soundgeek on 2015-07-07
> **leunam12 said:**
> Try fsarchiver to do your backups. Sorry, I know it's not a solution, just a workaround

Thanks, I might try this. Does it have a nice GUI front end?

> **cmcanulty said:**
> I love grsync very easy and reliable. If it finds any errors it still backs up and you can click on details to find the errant files.

That sounds more user friendly. 

I don't know which backup command is behind the Backups utility. I wonder why this one was selected to be packaged?

Thanks for the advice.

> **RobGoss said:**
> Hello and welcome, I prefer Clonezilla works flawlessly [http://clonezilla.org/](http://clonezilla.org/)

I did look at Clonezilla. I found the interface a bit confusing & initially copied in the wrong direction!

It looks good for copying whole partitions?

---

### Post by howefield on 2015-07-07
> **soundgeek said:**
> I did look at Clonezilla. I found the interface a bit confusing & initially copied in the wrong direction! It looks good for copying whole partitions?

Clonezilla is good for cloning partitions or whole disks, I use it extensively for taking a snapshot of the operating system,  meaning that whatever happens it is always easy to get back to a known starting point. For the most part, seems that as long as you read each screen carefully and take the defaults, you'll be fine.

I don't find it so good for user data where files can change often.

Your error looks similar to this [bug]("https://bugs.launchpad.net/ubuntu/+source/duplicity/+bug/1401245"), if it is mark it as affecting you too.

---

### Post by cmcanulty on 2015-07-07
grsync is GUI in fact it stands for graphical rsync

---

### Post by soundgeek on 2015-07-11
> **howefield said:**
> Clonezilla is good for cloning partitions or whole disks, I use it extensively for taking a snapshot of the operating system,  meaning that whatever happens it is always easy to get back to a known starting point. For the most part, seems that as long as you read each screen carefully and take the defaults, you'll be fine.

I don't find it so good for user data where files can change often.

Your error looks similar to this [bug]("https://bugs.launchpad.net/ubuntu/+source/duplicity/+bug/1401245"), if it is mark it as affecting you too.

Thanks for the info & for the bug reference - I didn't find that. It looks directly relevant :)

---

