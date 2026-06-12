---
title: "Killing task without &quot;notification&quot;"
date: 2017-01-13
forum: New to Ubuntu
---

### Post by CrewDK on 2017-01-13
Every time when I'm killing bg task I got notification that this task has been killed. 

```
$ sleep 500  & 
$ kill sleep
[1]+  Terminated              sleep 500

```

Is there any way I can get rid of this noise notifications at least in bash script? I tried to remove all output with > /dev/null but it's didn't helps at all. :(

---

### Post by SeijiSensei on 2017-01-13
The message is probably sent to the "syserr" device.  You can suppress it with
```
kill sleep > /dev/null 2>&1
```
That redirects errors on the syserr device to standard output, "sysout," which is then sent to /dev/null.

---

### Post by CrewDK on 2017-01-13
And this method also was tested without any success.  :(

---

### Post by geeksmith on 2017-01-13
```
set +m
sleep 500 &
pkill sleep
```

---

### Post by SeijiSensei on 2017-01-13
> **CrewDK said:**
> And this method also was tested without any success.  :(

Sorry.  I forgot to use "killall" or "pkill" rather than "kill" to terminate a process by its name instead of its process ID.  So either
```
kill 12345 > /dev/null 2>&1
```
or
```
killall sleep > /dev/null 2>&1
```
would work if the sleep process has ID 12345.

Be careful with killall or pkill if you're trying to kill a process like a server daemon that spawns children.  For instance, if you run "ps ax | grep apache" on a machine running the Apache web server, you'll see half-a-dozen identically named processes running as /usr/sbin/apache2.  Running "killall apache2" would terminate all of these.

---

### Post by Habitual on 2017-01-14
```
pkill sleep
```?

---

### Post by geeksmith on 2017-01-16
The notification isn't coming from the kill or pkill or killall command. It's coming from bash because job monitoring is enabled. As I posted above, you can suppress bash job monitoring and its associated output with the "set +m" command in bash.

---

