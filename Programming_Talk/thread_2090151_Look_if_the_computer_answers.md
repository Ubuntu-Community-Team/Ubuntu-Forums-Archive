---
title: "Look if the computer answers"
date: 2012-12-01
forum: Programming Talk
---

### Post by cazz on 2012-12-01
Hi
I trying to make or find a bash script that run and see if a computer answers that is there then it do something or when is not there nothing happend.

I have alot of script that is ready to use but them all is to advanced for the basic task I going to use.


I just want to make it look if the computer is in the network it run a command and if not nothing happend.

---

### Post by steeldriver on 2012-12-01
maybe just a simple ping test?

```

$ ping -c1 192.168.1.102 >/dev/null 2>&1 && echo "Do something here"
Do something here
$
$ ping -c1 192.168.1.103 >/dev/null 2>&1 && echo "Do something here"
$

```

---

### Post by Vaphell on 2012-12-01
```
if ping -c 1 *address* > /dev/null
then
  echo "it's alive"
else
  echo "it's dead, Jim"
fi
```

---

### Post by cazz on 2012-12-01
Thanks alot :)

---

