---
title: "disabling my touchscreen"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by tahahojati on 2012-07-03
Hi guys,
I migrated from Windows 7 to Ubuntu 2 days ago, and while almost everything has been awesome, I  cannot lower the sensitivity of my touchscreen in Ubuntu.  So my mouse pointer is constantly clicking everywhere, launching apps and etc.  I don't really care much about the touch screen, so all I intend to do at the moment is to deactivate it somehow.  I went to /lib/modules, there I found 3 directories (3.2.0-23-generic/ & 3.2.0-25-generic/ & 3.2.0-26-generic/).  In each of these three I found the subdirectories kernel/driver/input/touchscreen/  and  kernel/driver/input/tablet/.   Then I removed all of the files in those subdirectories.  I expected that by doing this, the drivers would be removed and my touchscreen be disabled, alas nothing happened.  So can anyone help me get rid of my touchscreen?

---

### Post by ubudog on 2012-07-03
Hi and welcome to the forums!  What are your specs?

Could you run (in a terminal) and post the output of:
```
xinput --list
```

---

### Post by debug87 on 2012-07-03
> **ubudog said:**
> Hi and welcome to the forums!  What are your specs?

Could you run (in a terminal) and post the output of:
```
xinput --list
```
same problems (sr ,my Enghlish ability is not good )
Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=12	[slave  keyboard (3)]

---

