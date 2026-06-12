---
title: "ping script [help]"
date: 2007-02-11
forum: Programming Talk
---

### Post by madrano on 2007-02-11
hi everyone, 

I wanting simple script, or program (suggest) :)


ping   >> specified adress  (10.0.0.60) (10 second retry)

if ping fails run (specific program)

if ping success run (specific program)

if specified program running in system abort executing program (ping fail or success)



how can do that, ruby ? phyton ? or bash script ?

any example helpful :)

and lastly I'm pretty interested ruby language, where to find any of good tutorials, code snippets?

thanks for all answers

---

### Post by kidders on 2007-02-11
Hi there,

A quick shell script is probably the most straightforward thing to do. Assuming you mean 10 second *timeout* (retry?), how about something like this...
```
#!/bin/bash

if [ -z "$1" ]; then
	echo "Usage: `basename $0` ip-addr"
	exit 1;
fi

ping -c 1 -W 10 $1 &>/dev/null
if [ $? -eq 0 ]; then
	echo "Ping succeeded"
	# Commands here
else
	echo "Ping failed"
	# Commands here
fi
```

> **madrano said:**
> if specified program running in system abort executing program (ping fail or success)

You can test for running programs with something like **[ -n "`pidof whatever`" ]**, which would be true if "whatever" is running.

> **madrano said:**
> I'm pretty interested ruby language, where to find any of good tutorials, code snippets?I don't really know anything about ruby ... hopefully someone else will post some help there. :-)

---

### Post by madrano on 2007-02-11
sorry about my bad english but, script well working, one exception ! I mean 10 second retry, every 10 seconds script check specified address. and executed programs must 1 time

e.g

10.0.0.10 > ping success > exec(ktorrent)
after 10 seconds
10.0.0.10 > ping success > exec(none)
after 10 seconds
10.0.0.10 > ping success > exec(none)
after 10 sec
10.0.0.10 > ping fail > exec(close ktorrent)
after 10 sec
10.0.0.10 > ping fail > exec(none)
after 10 sec
10.0.0.10 > ping success > exec(ktorrent)


thanks :)

---

### Post by kidders on 2007-02-11
Hey again,

This may be what you need ... [http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-7.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-7.html)

Since you mentioned ktorrent, I suggest you increase the delay between pings though ... the possibility that ktorrent might be starting up & shutting down at 10-second intervals would be undesirable. Checks at 10-*minute* intervals might be more appropriate.

---

### Post by Note360 on 2007-02-11
I think you watn the sleep command. I am not sure if it isn bashbut I know ruby has one.

---

### Post by lnostdal on 2007-02-12
Here is a complete program that does what you want (I think): [http://nostdal.org/~lars/programming/lisp/clisp/madrano.lisp](http://nostdal.org/~lars/programming/lisp/clisp/madrano.lisp)

You'll need CLISP to run it, just do: ```
sudo aptitude install clisp
```

Here is an example run:
```

lars@ibmr52:~/programming/lisp/clisp$ cat success.sh 
#!/usr/bin/env bash

echo "Success!!!!!!"
lars@ibmr52:~/programming/lisp/clisp$ cat failure.sh
#!/usr/bin/env bash

echo "Failure!!!!!"
lars@ibmr52:~/programming/lisp/clisp$ 
lars@ibmr52:~/programming/lisp/clisp$ ./madrano.lisp 192.168.1.101 1 3 ./success.sh ./failure.sh 
Success!!!!!!   (instantly, since the host is already up)
(i wait a long while, then disconnect the host from the network)
Failure!!!!!
(i wait a long while, then reconnect the host to the network)
Success!!!!!!
(i wait a long while)

```

edit: note that you must do ```
chmod +x madrano.lisp
``` before you'll be able to execute the code as i do above

---

### Post by lnostdal on 2007-02-12
just a further note here; the programs must return immediately .. that means success.sh could wrap a program that does not return immediately in something that executes it in the background and stores the PID in some temporary file for failure.sh to act upon later

..but there is nothing stopping you from handling this directly inside madrano.lisp also .. just depends on what you want :)

---

