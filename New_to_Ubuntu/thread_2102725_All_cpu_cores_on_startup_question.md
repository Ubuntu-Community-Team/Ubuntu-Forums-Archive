---
title: "All cpu cores on startup question"
date: 2013-01-08
forum: New to Ubuntu
---

### Post by HatoExB on 2013-01-08
Hi,

According to [http://www.itworld.com/software/306665/speed-ubuntu-1210-using-all-cpu-cores-during-startup ]("http://www.itworld.com/software/306665/speed-ubuntu-1210-using-all-cpu-cores-during-startup"), the instructions are asking for change CONCURRENCY = "none"  to CONCURRENCY="makefile".

> if [ "none" != "$CONCURRENCY" ] ; then
        test -s /etc/init.d/.depend.boot  || CONCURRENCY="none"
        test -s /etc/init.d/.depend.start || CONCURRENCY="none"
        test -s /etc/init.d/.depend.stop  || CONCURRENCY="none"
        if test -e /etc/init.d/.legacy-bootordering ; then
                CONCURRENCY="none"
        fi
        startpar -v      > /dev/null 2>&1 || CONCURRENCY="none"
fi
Do I edit all of concurrency or just the one under legacy-bootordering?

Sorry for the stupid question.  I'm running ubuntu 12.10 on my Dell studio 1535.  

Thanks in advanced

---

### Post by coldcritter64 on 2013-01-08
> **HatoExB said:**
> Hi,

According to [http://www.itworld.com/software/306665/speed-ubuntu-1210-using-all-cpu-cores-during-startup ]("http://www.itworld.com/software/306665/speed-ubuntu-1210-using-all-cpu-cores-during-startup"), the instructions are asking for change CONCURRENCY = "none"  to CONCURRENCY="makefile".

> if [ "none" != "$CONCURRENCY" ] ; then
test -s /etc/init.d/.depend.boot || CONCURRENCY="none"
test -s /etc/init.d/.depend.start || CONCURRENCY="none"
test -s /etc/init.d/.depend.stop || CONCURRENCY="none"
if test -e /etc/init.d/.legacy-bootordering ; then
**CONCURRENCY="none"**
fi
startpar -v > /dev/null 2>&1 || CONCURRENCY="none"
fi

Do I edit all of concurrency or just the one under legacy-bootordering?

Sorry for the stupid question.  I'm running ubuntu 12.10 on my Dell studio 1535.  

Thanks in advancedI've bolded the line I see the linked guide as referring to. That is the line I'd try changing.

---

### Post by 3rdalbum on 2013-01-08
```
if test -e /etc/init.d/.legacy-bootordering; then
CONCURRENCY="none"
```

On my system, /etc/init.d/.legacy-bootordering does not exist, so the next line does not run. Looks like .legacy-bootordering is a file you can create if you want to force Upstart to work like the old-fashioned Init system. Like a switch that is turned off by default.

In other words, this HOWTO does nothing useful at all!

Upstart uses concurrency by default, where it's appropriate of course. Back in the days before Upstart I think we all tried that "concurrency" trick :-)

---

### Post by deadflowr on 2013-01-08
Makefile is the default from 12.04 at least on up.
Besides you're looking at the wrong area of the file, the line is more towards the beginning of the file around line 20 or 30. It's one of the first uncommented lines in the file. And it is a stand alone line.

Look for this:

```
# Specify method used to enable concurrent init.d scripts.
# Valid options are 'none' and 'makefile'.  Obsolete options
# used earlier are 'shell' and 'startpar'.  The obsolete options
# are aliases for 'makefile' since 2010-05-14.  The default since
# the same date is 'makefile', as the init.d scripts in Debian now
# include dependency information and are ordered using this
# information.  See insserv for information on dependency based
# boot sequencing.
CONCURRENCY=makefile
```

---

### Post by marks_linux on 2013-01-08
The line at the beginning (line 31) is already set to makefile in my install (12.10).

Changing the other line (line 108) stops my laptop from shutting down (or at least it didn't shut down for 5 mins) - core i7 processor, and made no discernible difference to startup time.

---

### Post by deadflowr on 2013-01-08
> **marks_linux said:**
> The line at the beginning (line 31) is already set to makefile in my install (12.10).

Changing the other line (line 108) stops my laptop from shutting down (or at least it didn't shut down for 5 mins) - core i7 processor, and made no discernible difference to startup time.

In other words, it's best to leave well enough alone.

It seems the how-to tip is a bit antiquated.

---

