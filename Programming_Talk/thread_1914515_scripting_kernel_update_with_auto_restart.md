---
title: "scripting kernel update with auto restart"
date: 2012-01-24
forum: Programming Talk
---

### Post by emiller12345 on 2012-01-24
is there a way to script a kernel update and if the kernel is has an update, to restart the computer when its done?
```

#!/bin/bash
apt-get install -y linux-generic linux-headers-generic linux-image-generic && shutdown -r now

```
this doesn't do the job, not sure how to go about doing this correctly. 
Any ideas?

---

### Post by gordintoronto on 2012-01-24
You did say, "any ideas..."

My friend uses Windows, and it automatically restarts after most system updates. Drives him crazy. He's lost a lot of unsaved work due to this. So my idea is, don't do this. [smile]

---

### Post by emiller12345 on 2012-01-24
this is part of a script that I will be executing and I know it will be okay to restart it.  I'm using this on a vast quantity of VM's which makes me *really* want to automate this. The more I can automate, the easier things will get.  I understand what your talking about with the issue in windows, I too would always choose 'Restart Later' but for this I need the updates to take place as soon as possible.

---

### Post by emiller12345 on 2012-01-24
BTW I found the answer here
[http://stackoverflow.com/questions/7039520/bash-how-to-detect-whether-apt-get-requires-a-reboot](http://stackoverflow.com/questions/7039520/bash-how-to-detect-whether-apt-get-requires-a-reboot)
 
basically I add
```
 && [ -f /var/run/reboot-required ] && shutdown -r now
```
after the apt-get command and it should work

---

