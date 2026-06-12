---
title: "package manager running and will not close"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by mike widing on 2008-06-13
Hello 
I just installed 8 and I was running the update manager doing the updates it locked up froze the computer solid so I re-boot the computer.
I re-run up date manager and it tells me I need to go to the terminal and do a dpkg to complete up date so I do as it says.

 the up date seems to go ok it goes back to the opening prompt after the up date is finished I closed the terminal.

I decide to open the package manager and it comes up with a warning saying you can not have 2 package managers open at same time and I only had the one open (or trying to open)

I have ran into this before with other versions of Ubuntu does anyone have a suggestion Thank You

---

### Post by drs305 on 2008-06-13
Run this command to see what package installer is still running:
```
ps aux
```

If that is too much, then:
```
ps aux | grep synaptic
ps aux | grep apt*
```

You should get a list with the second entry in the column being a 4 or 5 digit PID number.

To end the process (XXXX is the PID number of the process you want to kill):
```
sudo kill -9 XXXX
```

---

### Post by ukripper on 2008-06-13
> **mike widing said:**
> Hello 
I just installed 8 and I was running the update manager doing the updates it locked up froze the computer solid so I re-boot the computer.
I re-run up date manager and it tells me I need to go to the terminal and do a dpkg to complete up date so I do as it says.

 the up date seems to go ok it goes back to the opening prompt after the up date is finished I closed the terminal.

I decide to open the package manager and it comes up with a warning saying you can not have 2 package managers open at same time and I only had the one open (or trying to open)

I have ran into this before with other versions of Ubuntu does anyone have a suggestion Thank You

go to system monitor and under Processes find synaptic or update-manager. Do you see them there?

---

### Post by Joeb454 on 2008-06-13
I'm guessing you'll most likely have to run ```
sudo dpkg --configure -a
``` from a terminal to fix it :)

---

