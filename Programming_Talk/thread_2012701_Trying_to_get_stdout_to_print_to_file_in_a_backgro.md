---
title: "Trying to get stdout to print to file in a background daemon"
date: 2012-06-29
forum: Programming Talk
---

### Post by Miltnoid on 2012-06-29
Hey guys, I'm using a start-stop-daemon tool on a python program, and I'm having issues having it print correctly to stdout.

Anyways, I'm trying to run

start-stop-daemon -Sbm /tmp/myfile.log -p $PIDFILE -c $APPUSER -d $APPDIR -x ${DAEMON} -- ${ARGS}

I've done a good number of differing things, but those all seem to not work, or just print stderr to /tmp/log.txt 

Some differing things I've tried are things like the -1 /tmp/log.txt flag, I've tried adding > /tmp/log.txt to the daemon, but none seem to work.  Is there something behind the scenes that's preventing me from seeing this info?

---

