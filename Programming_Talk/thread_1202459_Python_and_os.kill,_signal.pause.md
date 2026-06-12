---
title: "Python and os.kill, signal.pause"
date: 2009-07-02
forum: Programming Talk
---

### Post by master_kernel on 2009-07-02
Hi,

I'm having trouble implementing a pause and continue button in Python (the code part, not the button). Right now I'm using a BASH script to do it, but it's kinda iffy, and I would love to be able to do it in Python.

Here's the BASH script:
```
#!/bin/bash

SPEC=$1

find_children() {
    for pid in $(ps -ef | awk "{if ( \$3 == $1 ) { print \$2 }}")
        do
        if [ "$SPEC" = "CONT" ]; then kill -CONT $pid; fi
        if [ "$SPEC" = "STOP" ]; then kill -STOP $pid; fi
        find_children $pid
    done
}

find_children $2

exit 0
```

I know there should be a way to do this using os.killpg() and the signal.pause() function, but I have no idea how. Can anybody help?

---

### Post by smartbei on 2009-07-02
I think that os.killpg can do it all. After all, it accepts a signal number as an argument. You can get the signal numbers from the man file for kill.

---

### Post by soltanis on 2009-07-02
Or by running 
```

kill -l

```

In the command line (they're listed in ascending order, from 1 upwards, left to right).

---

### Post by master_kernel on 2009-07-04
> **smartbei said:**
> I think that os.killpg can do it all. After all, it accepts a signal number as an argument. You can get the signal numbers from the man file for kill.
I'll try using SIGSTOP and SIGCONT when I get a chance. Thanks!

---

### Post by meditatingfrog on 2009-08-20
I wanted to write a script that would use pkill -stop to pause processes that are taking up cpu that I leave open but I'm not currently using.  CPU usage without using the program happens with gnome-gnuchess, wesnoth, and firefox.  I was told os.kill could do it in #python on freednode.irc.net, so now I'm searching for os.kill info.

---

