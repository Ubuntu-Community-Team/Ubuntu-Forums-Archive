---
title: "Laptop reboot instead of shutdown."
date: 2014-07-28
forum: New to Ubuntu
---

### Post by dejan_87 on 2014-07-28
Hi,
I just installed ubuntu 14.04.1 on my Acer Aspire V5-571 and everything works fine so far,but i have one problem.When i try to shutdown it reboots instead of shutdown.This happends on AC power and on battery too.
So i search on net and find a solution for this problem on this link:[http://www.pbehnke.com/main/node/11](http://www.pbehnke.com/main/node/11)
After executing this:```
for i in /sys/bus/usb/devices/*/power/control;
    do echo on > $i
done
``` shutdown works fine.
So, how can i make some service file or something with this command that can be executed on startup?
Thanks.

---

### Post by veddox on 2014-07-28
Looks suspiciously like a workaround, but I haven't a clue what the underlying problem might be either...

To make it run at startup, copy the above code into a bash script and save it somewhere in your home directory. Then go to the Dash and open "Startup Applications". Click add, type in a name for your script, a comment, and the command
 ```
bash /path/to/file/shutdown.sh
```
obviously inserting the location where you saved the script.

That should do the trick.

---

### Post by dejan_87 on 2014-08-03
Hi,
Thanks for reply.. sorry but this doesn't work.Only when i execute the command in terminal i can shutdown my laptop.

---

