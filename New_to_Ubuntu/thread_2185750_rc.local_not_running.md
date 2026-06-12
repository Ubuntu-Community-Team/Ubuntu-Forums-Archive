---
title: "rc.local not running"
date: 2013-11-04
forum: New to Ubuntu
---

### Post by prao060 on 2013-11-04
My rc.local file isn't running on startup. It has permissions and i can run it from terminal after booting my computer and it will work just fine. It just won't run on startup, which is what i want. This is the contents of the file-

```
   #!/bin/bash
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
cd /home/prashant/Desktop
./startup-runner.sh || exit 1
exit 0
```

---

### Post by steeldriver on 2013-11-04
What does startup-runner.sh do? what services / other stuff does it rely on (networking, X server...?)

IMHO as a matter of good practice, *system* startup scripts shouldn't be calling scripts from *user* dirs - if you have something you want to do on startup for all users the scripts should probably go somewhere like /usr/local/bin

---

### Post by pqwoerituytrueiwoq on 2013-11-04
rc.local must exit 0 yet you just told it to exit 1
what is in that sh script and is it marked as executable

---

