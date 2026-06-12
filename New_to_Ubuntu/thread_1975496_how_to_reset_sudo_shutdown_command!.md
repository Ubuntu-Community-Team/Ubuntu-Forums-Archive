---
title: "how to reset sudo shutdown command!"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by tojonukokhadush on 2012-05-07
like, i used the command- 'sudo shutdown -h +30' in ubuntu terminal for i needed to move out but have some downloads to finish. then i realized that i can manage my time and now do not expect my system to shut down. how can i make that command not work and make my system keep running without being shut at the assigned time. i tried reset as well but this does not seem to work. please help.

---

### Post by Cheesemill on 2012-05-07
Proper answer, read:
```
man shutdown
```

Quick answer:
```
sudo shutdown -c
```

---

### Post by Mark_in_Hollywood on 2012-05-07
from:

[http://stackoverflow.com/questions/526329/possible-to-abort-shutdown-on-linux](http://stackoverflow.com/questions/526329/possible-to-abort-shutdown-on-linux)

You can use  ps  to find the shutdown process and abort it, for example with ps|grep shutdown.

Alternate and less eyeball-intensive versions of this:

pkill shutdown
killall shutdown
kill `cat /var/run/shutdown.pid`

---

### Post by tojonukokhadush on 2012-05-08
thank you all very much for your help.

---

