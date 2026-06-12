---
title: "Simple Backup Config - what does &quot;simply&quot; mean?"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by grikdog on 2008-08-09
Simple Backup Config 0.10.4 on the Time panel offers "simply" as an option for how to schedule a backup.  "Precisely" (and cron), I understand.  Should I guess that "simply" somehow invokes anacron to run the job?  If so, when does it run?  How do I suggest that I'd like the backup run within a few moments after I log on?  

More to the point, why do I have to *guess* what "simply" means?  Shouldn't it be documented?  The existing docs do not include a manpage, and the example configuration shows nothing more complex than include/exclude.  The *live* /etc/sbackup.conf is indecipherable, at least on this "simply" point, because it is uncommented.

TIA, baffled as usual...:confused:

---

### Post by sdennie on 2008-08-09
> **grikdog said:**
> Simple Backup Config 0.10.4 on the Time panel offers "simply" as an option for how to schedule a backup.  "Precisely" (and cron), I understand.  Should I guess that "simply" somehow invokes anacron to run the job?  If so, when does it run?  How do I suggest that I'd like the backup run within a few moments after I log on?  

More to the point, why do I have to *guess* what "simply" means?  Shouldn't it be documented?  The existing docs do not include a manpage, and the example configuration shows nothing more complex than include/exclude.  The *live* /etc/sbackup.conf is indecipherable, at least on this "simply" point, because it is uncommented.

TIA, baffled as usual...:confused:

It does actually have a man page.  I did a:

```

dpkg -L sbackup

```

And, it lists the files installed by the package.  It doesn't explain what "simply" means though.  :)

---

### Post by mc4100 on 2008-08-09
I don't have the slightest bit of experience with this program, but if you asked me what "simple" meant in terms of back-up, I'd say basic or easy. I'd guess it means little configuration, or perhaps a non-thorough backup.

---

### Post by Elfy on 2008-08-09
The answer is here [https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/126280](https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/126280)

> This "simply" option is meant for anacron ...Then simply was a word I chose myself because I couldn't find another one that would have fit

---

### Post by grikdog on 2008-08-09
Ah, ha!  Thanks!  About what I expected, but I agree entirely with the bug report.  Comments or docs would have been very much appreciated.

"When you ASSUME, you make an *** of U and ME!" -- Felix, on The Odd Couple

---

### Post by grikdog on 2008-08-09
Whaddaya know?  You're right!

But it's for <code>man sbackupd</code>, not <code>man sbackup</code>

Anyhoo, thanx!

---

### Post by richg on 2008-08-09
It means, Simple for the techie types, difficult for users.

Rich

---

