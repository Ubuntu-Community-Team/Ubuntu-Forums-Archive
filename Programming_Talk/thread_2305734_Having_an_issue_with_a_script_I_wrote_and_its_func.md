---
title: "Having an issue with a script I wrote and its functionality"
date: 2015-12-08
forum: Programming Talk
---

### Post by iziren on 2015-12-08
Greetings everyone, the guys at stackexchange have refused to give me a helping hand lol. But I believe it's a very simple question. 

Scenario: I have a script that calls for another script and it refreshes every 5 seconds. However, My called script should exit on any keypress. When I execute the called script by itself, the keypress works. However, when I attempt to exit the called script, it does not work. Please some advice. Here is some code taken from the called script:

```
#!/bin/bash
#Called function

#Time is displayed at the top in military time format.


keyinput=''
if [ -t 0 ]; then stty -echo -icanon -icrnl time 0 min 0; fi
  while [ "x$keyinput" = "x" ]; do
   echo "Press Any Key to Exit."
   echo "Users currently logged on:"
   w #Display who is currently logged on
   echo "Disk space utilization:"
   df -h #Display disk space utilization in human readable form
   echo "Memory and CPU Utilization:"
   ps axo user,pmem,pcpu #Display Username, % of Memory Used, CPU Usage %
  read -r -n 1 keyinput
  done
if [ -t 0 ]; then stty sane; fi
#echo "Thanks for using the Live Monitor, you pressed '$keyinput' to exit."




```

Anything I can do from the main script or from the called script to make sure it exits on keypress when it is called from the main script. Thanks in advance.

---

### Post by TheFu on 2015-12-08
Welcome to the forums.

Yes, it is a simple question. ;)

This question has many answers already on serverfault.  Look for "watchdog process."

There are better methods to accomplish the same thing. Use the $! variable to get the PID from the last process launched, then kill that other process when the keypress happens and exit this script.

Personally, I'd just setup system monitoring to capture this data. Then I'd get so much more. Munin, cacti, and about 20 other tools do this.  If you want to be old-school, use sar.  top, htop, saidar are some other, similar, options.

---

### Post by iziren on 2015-12-08
> **TheFu said:**
> Welcome to the forums.

Yes, it is a simple question. ;)

This question has many answers already on serverfault.  Look for "watchdog process."

There are better methods to accomplish the same thing. Use the $! variable to get the PID from the last process launched, then kill that other process when the keypress happens and exit this script.

Personally, I'd just setup system monitoring to capture this data. Then I'd get so much more. Munin, cacti, and about 20 other tools do this.  If you want to be old-school, use sar.  top, htop, saidar are some other, similar, options.

Thanks for the response, it's very much appreciated. I will definitely look into doing that, thanks!

---

