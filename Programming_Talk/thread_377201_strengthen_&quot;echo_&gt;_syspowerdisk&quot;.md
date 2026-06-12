---
title: "strengthen &quot;echo &gt; /sys/power/disk&quot;"
date: 2007-03-05
forum: Programming Talk
---

### Post by frogotronic on 2007-03-05
Hello,

  I wanted to add the -h, or the -P flag to shutdown that appears in the **/sys/power/disk** file, which is called by the ACPI hibernate.sh script.  I tried using sudo pico to edit the file, but I got an "Error: Invalid Argument" error when I tried to write the modified file.

The file currently consists of one line:

```
shutdown
```

I'd like to try to change it to

```
shutdown -h
```

or 

```
shutdown -P
```

What am I missing?

Thanks,
- CH

---

### Post by Mr. C. on 2007-03-05
Show the command and output exactly as it is on the screen.

MrC

---

### Post by frogotronic on 2007-03-05
hmmm

okay, I'm trying to fix hibernate function on my laptop.

During the hibernate process, ACPI executes the hibernate.sh script.  The last four lines of the script are:

```
echo -n $HIBERNATE_MODE >/sys/power/disk
echo -n "disk" >/sys/power/state

$LAPTOP_MODE stop

. /etc/acpi/resume.sh
```

BUT the machine goes all the way down but doesn't poweroff.  I'd like to try to tell the system to power off at **shutdown** (which is called by /sys/power/disk) by using a flag.

- CH

---

### Post by Mr. C. on 2007-03-05
Change this line of the script:

echo -n $HIBERNATE_MODE >/sys/power/disk

to this:

echo -n "$HIBERNATE_MODE -h"  >/sys/power/disk

or

echo -n "$HIBERNATE_MODE -p"  >/sys/power/disk

as you desire.
MrC

---

### Post by frogotronic on 2007-03-06
Thanks  for the help

- CH   :KS

---

