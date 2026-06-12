---
title: "cpu usage in notification"
date: 2013-10-16
forum: Programming Talk
---

### Post by vasa1 on 2013-10-16
In the script below, is it possible to have the value of **NR==2** as part of the notification in place of "**value**" so that the notification would look like:
CPU alert
CPU 8%
for example? 

```
#!/usr/bin/env bash

sleep_period=8m 

while true; do
  if ps -eo %C --sort -%cpu | head -2 | awk 'NR==2 { exit !($1>8); }'; then
      notify-send 'CPU alert!' 'CPU usage value%'
  fi
  sleep ${sleep_period}
done

```

---

### Post by Vaphell on 2013-10-16
you should simply store the output of ... '{ print int($1) }' and test it against the threshold in bash and then use the value.

```
t=8
cpu=$( ps -eo %C --sort -%cpu | head -2 | awk 'NR==2 { print int($1); }'
(( cpu>t )) && notify-send 'CPU alert!' 'CPU $cpu%'

```

That said, it's possible to hack it out using the exit code
```
t=8
if ps -eo %C --sort -%cpu | head -2 | awk -vt="$t" 'NR==2 { exit ($1>t)?int($1):0; }'
then
    :
else
    notify-send 'CPU alert!' 'CPU $?%'
fi
```

---

