---
title: "Sudden Log file size issue"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by bodam on 2008-11-07
I've suddenly started having space issues with /.  This is unexpected since it's 18GB and I have /home on another partition.  Using the Disk Usage Analyzer, I see that most of the space is eaten up by 2 files, located in /var/log:
Syslog.O (4.2GB)
kern.log.O (4.2GB)

I recently upgraded to 8.10.  Does anyone know why they're so large?  How do I shrink them?

thanks

Dave

---

### Post by scragar on 2008-11-07
it's .0, not .O, but both are safe to delete, they are not in use(just don't delete the version without the 0 though, that's the current log :P).
```
cd /var/log
sudo rm syslog.0
sudo rm kern.log.0
```
Oh, before you do anything, you might want to take a look in them using the text editor, see why they are so large, it's rare for them to be that large, so I know I would be interested to know why they are.

---

### Post by kingtiger01 on 2012-04-08
i know this is a old topic, but the issue has arisen with one of my servers.

Im not a complete Amateur to Linux and No where near a Amateur when it comes to linux administration.

My syslog and kern.log are both jumping within seconds from 800k to 9.4gb, the exact size of the log partition each.(we keep logs for years, for Archival Purposes.) Anyways, upon Inspection of  the files, there are empty. Completely. As if they were overwritten with Touch and non-ascII data was entered.... or fill was used...

Anyways, to verify it wasnt some wierd Permission issue with my Console Text editor of choice(dav, since i hate VI.) i open it with the root user, resulting in the same outcome.

----

If there is any typos,  im sorrry having some wierd problems with the open nvidia driver for this old laptop(small mobile terminal budget). So bitm half of the screen whites out after a few seconds... so im typing blind

---

