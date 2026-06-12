---
title: "How to spin down, unused Internal Disks?"
date: 2012-03-15
forum: New to Ubuntu
---

### Post by mikodo on 2012-03-15
Hi, 

I am thinking of putting a couple of extra internal HD's, in my computer. I would only do that, if there is a way to have them spin down, when not using them.

Is there a way to do this, outside of yanking the power lines?

Thanks.

---

### Post by mikewhatever on 2012-03-15
Use 'hdparm'. It's a command line tool for disk power management. Let's say, one of the drives you add is designated as /dev/sdb, then, to spin it down after 10 minutes, you'd use the following as admin:

```

hdparm -B 127 -S 120 /dev/sdb

```

-B stands for advanced power management, with values from 1 - 127 permitting spindown. -S is the spingdown timeout, in the example above - 120x5=600 seconds, or 10 minutes.

Check out 'man hdparm' for more info.

To automate the procedure, just add a line for each HDD to /etc/rc.local.

---

### Post by mikodo on 2012-03-15
> **mikewhatever said:**
> Use 'hdparm'. It's a command line tool for disk power management. Let's say, one of the drives you add is designated as /dev/sdb, then, to spin it down after 10 minutes, you'd use the following as admin:

```

hdparm -B 127 -S 120 /dev/sdb

```-B stands for advanced power management, with values from 1 - 127 permitting spindown. -S is the spingdown timeout, in the example above - 120x5=600 seconds, or 10 minutes.

Check out 'man hdparm' for more info.

To automate the procedure, just add a line for each HDD to /etc/rc.local.Sounds simple enough.

Can you give me an other example of entering a line, for automating the proceedure:

```
gksu gedit /etc/rc.local          *OR* 

sudo nano /etc/rc.local
``````

#!/bin/sh -e
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

exit 0
```Thanks.

---

### Post by mikewhatever on 2012-03-15
The lines would look very similar, with only the hdd designations changing:
```
#!/bin/sh -e
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
[COLOR="DarkRed"]hdparm -B 127 -S 120 /dev/sdb[/COLOR]
[COLOR="DarkRed"]hdparm -B 127 -S 120 /dev/sdc[/COLOR]
[COLOR="DarkRed"]hdparm -B 127 -S 120 /dev/sdd[/COLOR]
exit 0
```

If you want a time out other then 10 minutes, modify the -S value accordingly.

---

### Post by mikodo on 2012-03-15
> **mikewhatever said:**
> The lines would look very similar, with only the hdd designations changing:
```
#!/bin/sh -e
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
[COLOR=DarkRed]hdparm -B 127 -S 120 /dev/sdb[/COLOR]
[COLOR=DarkRed]hdparm -B 127 -S 120 /dev/sdc[/COLOR]
[COLOR=DarkRed]hdparm -B 127 -S 120 /dev/sdd[/COLOR]
exit 0
```If you want a time out other then 10 minutes, modify the -S value accordingly.Thank you, for the hand-holding!

---

### Post by tsucol11 on 2012-03-15
thank you

Brian

---

