---
title: "How do I add another run level (level 7) in Ubuntu?"
date: 2008-09-21
forum: Programming Talk
---

### Post by Diabolis on 2008-09-21
Ubuntu has 8 run levels (0-6 and S), I want to add the run level 7.

I have done the following:

1.- Created the folder **/etc/rc7.d/**, which contains some symbolic links to **/etc/init.d/**

2.- Created the file **/etc/event.d/rc7** This is its content:

[PHP]# rc7 - runlevel 7 compatibility
#
# This task runs the old sysv-rc runlevel 7 ("multi-user") scripts.  It
# is usually started by the telinit compatibility wrapper.

start on runlevel 7

stop on runlevel [!7]

console output
script
    set $(runlevel --set 7 || true)
    if [ "$1" != "unknown" ]; then
        PREVLEVEL=$1
        RUNLEVEL=$2
        export PREVLEVEL RUNLEVEL
    fi

    exec /etc/init.d/rc 7
end script[/PHP]

I thought that would be enough, but **telinit 7** still throws this error: *telinit: illegal runlevel: 7*

---

### Post by slavik on 2008-09-21
you're going to have to change some kernel/init code methinks.

by default Ubuntu boots in runlevel 2 for the regular boot, why don't you want to use 3 or 4 or 5?

---

