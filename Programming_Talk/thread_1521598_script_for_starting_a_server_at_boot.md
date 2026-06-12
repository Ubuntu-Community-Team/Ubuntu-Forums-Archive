---
title: "script for starting a server at boot"
date: 2010-07-01
forum: Programming Talk
---

### Post by tapas_mishra on 2010-07-01
I have a small script which starts a server of mine.I have to each time manually go to /usr/local/OLAT/
and then run as
```

./runOlat.sh

```
then I get some messages on my screen and after some time I am able to start my access my server [http://localhost:8080/application/](http://localhost:8080/application/)
the script runOlat.sh
has following 
```

#!/bin/sh

cd /usr/local/OLAT

# force to use ISO-8859-1 for file encoding
export JAVA_OPTS=-Dfile.encoding=ISO-8859-1

java -jar runOLAT.jar

```

what do I need to do so that it can be started each time at boot.
Ubuntu 9.04

---

### Post by Sanjeevtrip on 2010-07-01
Call your script from the file

```

/etc/rc.local

```

---

### Post by km0r3 on 2010-07-01
> **tapas_mishra said:**
> 
what do I need to do so that it can be started each time at boot.
Ubuntu 9.04

Just *one* way of doing this:

[LIST=1]
[*]Place the script `runOlat.sh` in the /etc/init.d directory (with root privileges)
[*]Switch into a terminal and run
```
sudo update-rc.d /etc/init.d/runOlat.sh defaults
```
[*]
Make sure it's executable.
**Hint:**```
chmod u+x /etc/init.d/runOlat.sh
```
[/LIST]

Questions? Please, always try the man-pages and the forum-search first. :-)

> man update-rc.d

---

