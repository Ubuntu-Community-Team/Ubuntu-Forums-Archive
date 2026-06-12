---
title: "hardy: locate, s and m"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by imputerate on 2008-05-27
a few weeks after installing hardy, i tried to run 'locate'; an error message complained about slocate.db;

turns out that the slocate cron job doesn't work if mlocate is installed, which it is on ubuntu hardy; here's the script:

-------------------------------------
#! /bin/sh

if [ -x /usr/bin/slocate ] && [ ! -x /usr/bin/mlocate ]
then
if [ -f /etc/updatedb.conf ]
then
. /etc/updatedb.conf
fi

# Adjust I/O priority of current process (default: best effort)
ionice -c ${IONICE_CLASS:-2} -n ${IONICE_PRIORITY:-7} -p $$

if [ -f /etc/updatedb.conf ]
then
nice -n ${NICE:-10} /usr/bin/slocate -u
else
nice -n ${NICE:-10} /usr/bin/slocate -u -f proc
fi
chown root.slocate /var/lib/slocate/slocate.db
fi

---------------------------------------

why didn't the etc/cron.daily/mlocate script, if it was executing, fix it so my 'locate' command would work.

here it is:
--------------------------------
#! /bin/sh

set -e

[ -x /usr/bin/updatedb.mlocate ] || exit 0

# See ionice(1)
if [ -x /usr/bin/ionice ]; then
IONICE="/usr/bin/ionice -c3"
fi

$IONICE /usr/bin/updatedb.mlocate
---------------------------------

is it the case that 'locate' uses the /var/lib/slocate/slocate.db instead of /var/lib/mlocate/mlocate.db?

hodgson@ubu:~$ ls -l $(which locate)
lrwxrwxrwx 1 root root 24 2008-03-25 20:59 /usr/bin/locate -> /etc/alternatives/locate
hodgson@ubu:~$ which locate
/usr/bin/locate
 
is this a bug? 

should i fix it so that 'locate' runs slocate, and then uninstall mlocate? how?

what's a newbie to do?

---

### Post by master5o1 on 2008-05-27
What's the difference between slocate and mlocate?

---

### Post by sdennie on 2008-05-27
I'm not familiar with the differences between the two but, you could try:

```

sudo update-alternatives --config locate

```

---

### Post by natirips on 2008-05-31
Do I really need any of them? What do they do? I mean, they just clog up my proccessor and harddrive from time to time... Can I just disable them by adding a . (period) in cron.daily to their filenames without breaking my system?

---

### Post by Monicker on 2008-05-31
You don't need them.  Some distros do not even install them by default.  Their purpose is to make it easier to find any files on your system.  Updatedb periodically index all of the files on the system, and the m/slocate commands reference that index in order to show you where a file is located.  You can pretty much do it manually with the find command; you would just have to wait longer for the results.  I find the locate command to be very helpful at times. The indexing by default should be running at a time of the day when nobody is usually active on the computer; I have never seen a performance hit from it.

---

### Post by sayakb on 2008-05-31
As a file search app, you might try catfish
```
sudo apt-get install catfish
```Then goto Aplications->Accessories->Catfish to search files.

---

