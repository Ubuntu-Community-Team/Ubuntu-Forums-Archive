---
title: "Looking for help with a bash backup script."
date: 2007-07-22
forum: Programming Talk
---

### Post by CzarAlex on 2007-07-22
I'd like some BASH scripting help. 

I have a bash script that backs up a file weekly for me and puts a formatted date in the file name.

 Example:
 moo20070701.tar.gz
 moo20070708.tar.gz
 moo20070715.tar.gz
 moo20070722.tar.gz

Id like to keep the last 4 weeks of backups (meaning 4 files) Could someone assist me in writing a script that will keep only the 4 most recent backups and drop the oldest one?

For example, when the script is run next week, moo20070729.tar.gz will be made and I'd like the oldest of the files, in this case, moo20070701.tar.gz to be removed.

How can I do this?

---

### Post by Mr. C. on 2007-07-23
You can use logrotate to do this.  

```
man logrotate
```

and look at examples in **/etc/logrotate.d**

MrC

---

### Post by CzarAlex on 2007-08-06
Here's what I ended up doing, in case others can find it useful.

```
find /home/czar/backup -name 'moo*' -mtime +31 -delete

```

What It`ll do, is find any file in the /home/czar/backup directory that starts with "moo" AND has gone 31 days or more WITHOUT being modified..and then delete them. 

Be careful though, as the directory used to be called moobackups but the search criteria would also catch the directory name and erase the whole directory, hence the name backup instead.

---

### Post by fatsheep on 2007-08-06
> **CzarAlex said:**
> Here's what I ended up doing, in case others can find it useful.

```
find /home/czar/backup -name 'moo*' -mtime +31 -delete

```

What It`ll do, is find any file in the /home/czar/backup directory that starts with "moo" AND has gone 31 days or more WITHOUT being modified..and then delete them. 

Be careful though, as the directory used to be called moobackups but the search criteria would also catch the directory name and erase the whole directory, hence the name backup instead.

That's a pretty neat command there.  I forget sometimes that find can do a lot more then just list file.  I'm assuming you looked at logrotate and didn't find it useful?

---

### Post by jyba on 2007-08-06
CzarAlex wasted his time here. Mr. C. pointed him at the solution. (You might also look at /etc/logrotate.conf)

---

