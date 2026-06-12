---
title: "Problem making a script for enemy territory"
date: 2006-09-09
forum: Programming Talk
---

### Post by fatsheep on 2006-09-09
Unfortunately, in order to get sound to work in enemy territory, I have to run these commands in a terminal before hand:
> 
sudo -s
killall esd	
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

This can get annoying so I thought I'd make a shell script to automate the process:

> #!/bin/sh
sudo -s
killall esd	
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
et


The file is named "enemy territory start".  When I run it in the terminal, all I get is this:

> 
root@fatsheep:~#


So basically only the first line (sudo -s) worked and the rest was ignored.  :confused:

---

### Post by nereid on 2006-09-09
The problem with your approach is, that you create a new session. Instead of opening a root session with sudo -s just prepend each command with sudo.

```

#!/bin/bash

sudo killall esd
sudo echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
et
```

This should do the job.

---

### Post by fatsheep on 2006-09-09
Thanks that worked really well!  :p

---

