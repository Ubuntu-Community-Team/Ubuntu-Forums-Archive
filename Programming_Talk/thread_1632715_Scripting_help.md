---
title: "Scripting help?"
date: 2010-11-28
forum: Programming Talk
---

### Post by conradin on 2010-11-28
Hi all,
Im trying to automate some root type activities.
The code imediately below seems to work fine, when I run the script, I am left with an open root terminal session.
```

#!/usr/bin/expect
spawn sudo -i
expect ":"
send "MyPassword\r"
expect "#"
interact

```

The problem comes when I try to add root functions, like shutting down the computer. I'm not sure if there is a timing issue or what is going on, but, I'm stumped. 



```

#!/usr/bin/expect
spawn sudo -i
expect ":"
send "MyPassword\r"
expect "#"
puts "Shutting down computer "
send "shutdown -h now\r"

```

also, if there is an easy way to do this without expect, I'd like to know what it is.

---

### Post by conradin on 2010-11-28
Ok i got it!
```

#!/usr/bin/expect
spawn sudo -i
expect ":"
send "MY_Password\r"
expect "#"
puts "Shutting Down Ethernet connection 0 "
send "\r"
send "ifdown eth1\r"
expect "configured"
puts "Shutting down computer "
send "\r"
send "shutdown -h now\r"
interact

```

---

