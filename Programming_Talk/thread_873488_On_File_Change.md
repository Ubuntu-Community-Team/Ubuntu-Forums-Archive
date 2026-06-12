---
title: "On File Change"
date: 2008-07-29
forum: Programming Talk
---

### Post by michael30 on 2008-07-29
I'm running a NeoStats server for a friends IRC network and sometimes the connection is lost. I've made shell scripts before but I have never seen before how to do this. I want a way for the script to sit idle until it notices that the pid file of the server has changed. When the file is changed it should restart the server. Any help is appreciated.

---

### Post by dexter.deepak on 2008-07-29
i am also a noob, but thought to give it a try (i havent tested it)
```

#!/bin/bash
#monitor_server.sh
init_pid=`pgrep server`
while sleep 5s;do
if [ "$init_pid"==`pgrep server`]; then
continue
else
restart server
break
fi
done
sh monitor_server.sh
disown
```

i actually cuoldnt understand what you mean by "pid file" , i supposed it to be just "pid" ...hope that doesnt mess up things :)

---

### Post by dexter.deepak on 2008-07-29
can you please reply if it worked ??

---

### Post by michael30 on 2008-07-29
I worked off your code and changed to meet my needs. Thanks a lot.

```
#!/bin/bash

dir="/home/michael/NeoStats3.0/"
ircdexe="/bin/neostats"
cfgfile="neostats.conf"
pidfile="neostats.pid"

while sleep 60s;do
if test -r $dir/$pidfile; then
  echo "Server is already running."
else
  echo "Starting server..."
  cd $dir
  $dir/$ircdexe start
fi
done
sh monitor_server.sh
disown
```

---

