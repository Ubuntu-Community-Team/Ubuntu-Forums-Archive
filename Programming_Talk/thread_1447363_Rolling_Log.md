---
title: "Rolling Log"
date: 2010-04-05
forum: Programming Talk
---

### Post by rockom on 2010-04-05
Hello,

I've been trying to find some information on creating log files.  This forum and google has helped me out some with finding log4c.  I'm using code:blocks and gcc for a console app.  Nothing fancy...straight C.

I'd like to do some logging though. Hopefully something to manage the file size automatically.  I haven't found any good examples or tutorials though. 
If something simpler than log4c is available, that would be great.

Any help would be appreciated.

Thanks,
-Rocko

---

### Post by kblft on 2010-04-05
There is an application called logrotate that does logfile size handling

It doesn't do the actual logging - but looks at your logfiles and rotates them when they fit a certain criteria you select

---

