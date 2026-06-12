---
title: "Unable to install from Ubuntu software center"
date: 2011-12-04
forum: New to Ubuntu
---

### Post by rajeevpert on 2011-12-04
i am using ubuntu 11.10 . when i try to install some package from Ubuntu Software center, i got following error
"There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks."

Plz provide help what to do.....

---

### Post by Dubslow on 2011-12-04
A quick Google came up with these ten posts:
[http://ubuntuforums.org/showthread.php?t=1854573](http://ubuntuforums.org/showthread.php?t=1854573)

The short answer is try running
```

apt-get update
apt-get upgrade

```
from the terminal. You'll probably need to use sudo.

---

### Post by Rubi1200 on 2011-12-04
Hi and welcome to the forums rajeevpert :)

You will need to use sudo for those commands to work.

Open a terminal with Ctrl+Alt+T and type them in. You won't see your password echoed but just enter it correctly and then press Enter.

If there are error messages with those commands, copy and paste from the terminal into a new post here.

---

