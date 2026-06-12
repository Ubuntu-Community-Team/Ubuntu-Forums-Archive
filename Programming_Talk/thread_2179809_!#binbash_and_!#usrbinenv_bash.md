---
title: "!#bin/bash and !#/usr/bin/env bash"
date: 2013-10-10
forum: Programming Talk
---

### Post by vasa1 on 2013-10-10
What is the difference? Are there times one is preferable?

In the following codes, both work the same:```
#!/bin/bash

sleep 1m;

 COUNTER=0
    while [  $COUNTER -lt 10 ]; do
       mplayer -really-quiet /usr/share/sounds/freedesktop/stereo/phone-incoming-call.oga
          let COUNTER=COUNTER+1 
    done

```and```
#!/usr/bin/env bash

sleep 1m;

 COUNTER=0
    while [  $COUNTER -lt 10 ]; do
       mplayer -really-quiet /usr/share/sounds/freedesktop/stereo/phone-incoming-call.oga
          let COUNTER=COUNTER+1 
    done

```

---

### Post by Vaphell on 2013-10-10
/bin/bash points directly to the binary file
env abstracts the true location away which is useful in case of less essential stuff that can be put in different locations in different distros. Obviously this improves portability, you don't care where distro managers put let's say python - it's the env's job to find it. Also in case of multiple versions in parallel you can switch the default one and have the scripts follow.

[http://stackoverflow.com/questions/2429511/why-do-people-write-usr-bin-env-python-on-the-first-line-of-a-python-script](http://stackoverflow.com/questions/2429511/why-do-people-write-usr-bin-env-python-on-the-first-line-of-a-python-script)

---

### Post by vasa1 on 2013-10-10
Thank you :)

Marking it [Solved]

---

### Post by azzamite on 2013-10-10
> **Vaphell said:**
> 
env abstracts the true location away which is useful in case of less essential stuff that can be put in different locations in different distros. 


Interesting!

Is env always located in /usr/bin/env for all distros?

Does it exists in older *nixes? (Solaris, Freebsd, etc)

---

### Post by sisco311 on 2013-10-10
> **azzamite said:**
> Interesting!

Is env always located in /usr/bin/env for all distros?

Does it exists in older *nixes? (Solaris, Freebsd, etc)

This should answer all your questions: [http://www.in-ulm.de/~mascheck/various/shebang/](http://www.in-ulm.de/~mascheck/various/shebang/)


Here is another interesting article which is also related to this topic:
[http://www.freedesktop.org/wiki/Software/systemd/TheCaseForTheUsrMerge/](http://www.freedesktop.org/wiki/Software/systemd/TheCaseForTheUsrMerge/)

---

