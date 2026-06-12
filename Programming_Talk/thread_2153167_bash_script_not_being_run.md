---
title: "bash script not being run"
date: 2013-06-10
forum: Programming Talk
---

### Post by dryder on 2013-06-10
Hi
12.04 classic AMD64

I have a script called change-backgrounds - it works if I use it manually (even when run from /etc/init.d).

I placed it in /etc/init.d with a link to it in  /etc/rc1.d. In /etc/rc1.d prefixed with K15: K15change-backgrounds as I want it to run on shutdown.

My problem is ether:
[LIST]
[*]it does not run on shutdown
[*]or the file containing the counter (/usr/share/backgrounds/contest/c.txt) is not written to.
[/LIST]

I don't pretend it's the most elegant script - I'll concentrate on improving how it could be written later. For now, I just want it to run on shutdown.
```
#!/bin/bash
## 
# count=$(</home/david/bash-scripts/c.txt)
count=$(</usr/share/backgrounds/contest/c.txt)
#
# echo $count
# read -p "pause ..." nothing
#
if [ $count -eq 1 ]
then
  cp /usr/share/backgrounds/contest/space.xml /usr/share/backgrounds/contest/precise.xml
fi
#
if [ $count = 2 ]
then
  cp /usr/share/backgrounds/contest/karmic.xml /usr/share/backgrounds/contest/precise.xml
fi
#
if [ $count -eq 3 ]
then
  cp /usr/share/backgrounds/contest/lucid.xml /usr/share/backgrounds/contest/precise.xml
fi
#
if [ $count -eq 4 ]
then
  cp /usr/share/backgrounds/contest/maverick.xml /usr/share/backgrounds/contest/precise.xml
fi
#
if [ $count -eq 5 ]
then
  cp /usr/share/backgrounds/contest/natty.xml /usr/share/backgrounds/contest/precise.xml
fi
#
if [ $count -eq 6 ]
then
  cp /usr/share/backgrounds/contest/oneiric.xml /usr/share/backgrounds/contest/precise.xml
fi
#
if [ $count -eq 7 ]
then
  cp /usr/share/backgrounds/contest/precise-backup.xml /usr/share/backgrounds/contest/precise.xml
fi
#
if [ $count -eq 8 ]
then
  cp /usr/share/backgrounds/contest/quantal.xml /usr/share/backgrounds/contest/precise.xml
fi
#
if [ $count -eq 9 ]
then
  cp /usr/share/backgrounds/contest/raring.xml /usr/share/backgrounds/contest/precise.xml
fi
#
if [ $count -eq 9 ]
then
count=0
fi
##
# NOW INCREASE COUNT
count=$((count+1))
##
# AND WRITE TO FILE
# echo $count > /home/david/bash-scripts/c.txt
echo $count > /usr/share/backgrounds/contest/c.txt
#
#

```

The count file (/usr/share/backgrounds/contest/c.txt) only updates if I run it manually.

Advice welcome - thanks

---

### Post by Lars Noodén on 2013-06-10
The place for shutdown scripts would be rc0.d and also rc6.d  Normal operation should be rc2.d.  Scripts in rc1.d would only get run when the system enters single-user mode.

See the manual page for [runlevel(7)](http://manpages.ubuntu.com/manpages/raring/en/man7/runlevel.7.html) for the full list.  

Alternately you might think about converting the script to an [Upstart script](http://upstart.ubuntu.com/cookbook/)

---

### Post by dryder on 2013-06-10
I have moved the link to the correct runlevel - and changed the K to S in the file name so it starts when that runlevel is entered.

It seems to work.

Thanks

---

