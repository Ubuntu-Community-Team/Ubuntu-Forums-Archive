---
title: "What is prelink.bin and why was it running?"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by pqwoerituytrueiwoq on 2012-04-07
i never noticed it running till now (and i have been using lucid sicne it was released) it was using about 10% cpu and a saw the sudden hdd activity 
for what i read it does something to speed up startup time but i am wondering why it was suddenly running
could it be have been running cause i had to load my backup a few days ago to my hdd since my cheap ssd failed (3ed time)

---

### Post by QIII on 2012-04-07
I tried man prelink and man prelink.bin and got nothing.

I did find this, however:

[http://www.digipedia.pl/man/doc/view/prelink.bin.8/](http://www.digipedia.pl/man/doc/view/prelink.bin.8/)

---

### Post by pqwoerituytrueiwoq on 2012-04-07
looks like it is a dependency of execstack
prelink 0.0.20090925-1 has been installed on my system since Tue 02 Feb 2010
```
cat /etc/cron.daily/prelink 
#!/bin/bash

. /etc/default/prelink

renice +19 -p $$ >/dev/null 2>&1

# Default action. Won't do anything. Bug#231007.
if [ "$PRELINKING" != yes ] && [ "$PRELINKING" != no ]; then
    echo "Default action. Modify /etc/default/prelink to change this." > /var/log/prelink.log
    exit 0
fi

PRELINK_OPTS="$PRELINK_OPTS -T"

if [ "$PRELINKING" = no ]; then
  if [ -f /etc/prelink.cache ]; then
    echo /usr/sbin/prelink -ua > /var/log/prelink.log
    /usr/sbin/prelink -ua >> /var/log/prelink.log 2>&1 \
      || echo Prelink failed with return value $? >> /var/log/prelink.log
    rm -f /etc/prelink.cache
    # Restart init if needed
    [ -n "$(find `ldd /sbin/init | awk 'NF == 4 { print $3 }'` /sbin/init -ctime -1 2>/dev/null )" ] && /sbin/telinit u
  fi
  exit 0
fi

if [ ! -f /etc/prelink.cache -o -f /var/lib/misc/prelink.force ] \
   || grep -q '^prelink-ELF0.[0-2]' /etc/prelink.cache; then
  # If cache does not exist or is from older prelink versions or
  # if we were asked to explicitely, force full prelinking
  rm -f /etc/prelink.cache /var/lib/misc/prelink.force
  PRELINK_OPTS="$PRELINK_OPTS -f"
  date > /var/lib/misc/prelink.full
  cp -a /var/lib/misc/prelink.{full,quick}
elif [ -n "$PRELINK_FULL_TIME_INTERVAL" \
       -a "`find /var/lib/misc/prelink.full -mtime -${PRELINK_FULL_TIME_INTERVAL} 2>/dev/null`" \
      = /var/lib/misc/prelink.full ]; then
  # If no more than PRELINK_NONRPM_CHECK_INTERVAL days elapsed from last prelink
  # (be it full or quick) and no packages have been upgraded via dpkg since then,
  # don't do anything.
  [ "`find /var/lib/misc/prelink.quick -mtime -${PRELINK_NONRPM_CHECK_INTERVAL:-7} 2>/dev/null`" \
    -a -f /var/lib/dpkg/status \
    -a /var/lib/dpkg/status -ot /var/lib/misc/prelink.quick ] && exit 0 
  date > /var/lib/misc/prelink.quick
  # If prelink without -q has been run in the last
  # PRELINK_FULL_TIME_INTERVAL days, just use quick mode
  PRELINK_OPTS="$PRELINK_OPTS -q"
else
  date > /var/lib/misc/prelink.full
  cp -a /var/lib/misc/prelink.{full,quick}
fi

echo /usr/sbin/prelink -a $PRELINK_OPTS > /var/log/prelink.log
/usr/sbin/prelink -a $PRELINK_OPTS >> /var/log/prelink.log 2>&1 \
  || echo Prelink failed with return value $? >> /var/log/prelink.log
# Restart init if needed
[ -n "$(find `ldd /sbin/init | awk 'NF == 4 { print $3 }'` /sbin/init -ctime -1 2>/dev/null )" ] && /sbin/telinit u

exit 0
```
does this write data anywhere outside of /var on a daily basis?

---

### Post by QIII on 2012-04-07
Hmmm.  Don't know.

Was this activity transitory or is it constant?

---

### Post by haqking on 2012-04-07
prelinking speeds up applications by prelinking libraries upon boot time.

I didnt think it was needed anymore in Ubuntu since feisty but not sure on that, i think it was replaced by Dt-Gnu-hash but you will have to check that.

---

### Post by pqwoerituytrueiwoq on 2012-04-07
since execstack says it replaces prelink and execstack seems to be stock in lucid i purged prelink we will see if anything breaks

---

