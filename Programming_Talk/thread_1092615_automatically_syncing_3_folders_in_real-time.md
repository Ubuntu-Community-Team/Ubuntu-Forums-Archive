---
title: "automatically syncing 3 folders in real-time"
date: 2009-03-10
forum: Programming Talk
---

### Post by qmqmqm on 2009-03-10
Hi

Is there a program to synchronize 2 (sorry, the "3" in title is a typo) directories constantly?

So say I have directory A as a master and directory B as a slave. If I make any changes to any files in A, B gets changed immidiately as well?

Thanks,

Tom

---

### Post by nunki on 2009-03-10
I may be way off, but I would think rsync combined with a cronjob would work...although I dont know if something else is better suited. To sync master to slave per your example
```

rsync -av --delete /master/ /slave/

```

You could then setup a cron job to run every minute or so to sync the directories..just my 2 cents

---

### Post by qmqmqm on 2009-03-10
how about on a windows machine... ?

Are there similar commands or programs that do the same job?

---

### Post by vandorjw on 2009-03-10
look into SVN.

Although, I don't think this is what you want, unless those folders are across different computers, then this is exactly what you want.

snv doensn't update realtime, but will update with the command

svn update
svn commit

Cheers - CC7

---

### Post by spupy on 2009-03-10
Possible solutions:
- on Linux: man ln
- on Windows: shortcuts?
;)

---

### Post by slavik on 2009-03-10
what are you trying to achieve with this?

---

### Post by qmqmqm on 2009-03-11
> **slavik said:**
> what are you trying to achieve with this?

Hi slavik

I have a php project in Eclipse workspace, but it needs to be put into xampp/htdocs in order to run. So every time I make a change in my workspace I need to delete and copy the project to xampp/htdocs, and that turns out to be quite annoying...

So I wanted to have the xampp/htdocs/myproject directory automatically sync with my Eclipse workspace real-time (on my Windows machine).

Thanks,

Tom

---

### Post by qmqmqm on 2009-03-17
Does anyone have any other solutions?

Thanks,

Tom

---

### Post by imdano on 2009-03-17
You could try [cwrsync](http://www.itefix.no/i2/node/10650), which is rsync for Windows.  I think it basically installs cygwin on your machine and rsync inside of that.  There's a "Scheduled Task" feature in Windows that I think works like cron you could use to schedule it every few minutes/hours/whatever.

If you were using Linux you could use inotify to watch the directory in realtime, but I don't know if anything like that exists for Windows.

---

### Post by slavik on 2009-03-19
just make the other directories symlink to one single directory.

---

