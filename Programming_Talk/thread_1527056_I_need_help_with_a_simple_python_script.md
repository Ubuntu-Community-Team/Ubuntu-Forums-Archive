---
title: "I need help with a simple python script"
date: 2010-07-08
forum: Programming Talk
---

### Post by kevin11951 on 2010-07-08
I am trying to write a simple python script that will read the contents of a file (/proc/acpi/battery/BAT1/state), and if it contains the line
```
charging state:          discharging
```
(or just the word "discharging" if that’s easier), then it will run the command 'halt' on the server.

---

### Post by schauerlich on 2010-07-08
Look into regular expressions. It may be easier to do this with awk/bash.

---

### Post by detrate on 2010-07-08
```
#!/bin/bash
if [[ $(grep "discharging" /proc/acpi/battery/BAT1/state | wc -l) > 0 ]]; then
  echo "halting"
  #halt
fi

```

Not python, but bash should be okay?
uncomment halt when you're ready to use it for real.

---

### Post by arsenic23 on 2010-07-08
Do you really want to use python?  It would be so much easier to deal with in bash.  Off the top of my head you could do something like:
[PHP]#!/bin/bash

batt=`grep ^charging\ state /proc/acpi/battery/BAT1/state | sed 's/^charging state[:]  *//'`
if [ $batt = "discharging" ]; then
	halt
fi[/PHP]

---

### Post by Can+~ on 2010-07-08
I just wrote this from the top of my head.

[PHP]filestate = open("/proc/acpi/battery/BAT1/state")

for line in filestate:
    if line.startswith("charging state:"):
        
        if line.rsplit(" ", 2)[-1].strip().lower() == "discharging":
            os.system("halt")

filestate.close()[/PHP]

---

### Post by detrate on 2010-07-08
> **Can+~ said:**
> I just wrote this from the top of my head.

[PHP]filestate = open("/proc/acpi/battery/BAT1/state")

for line in filestate:
    if line.startswith("charging state:"):
        
        if line.rsplit(" ", 2)[-1].strip().lower() == "discharging":
            os.system("halt")

filestate.close()[/PHP]

I just started learning python and the white space thing bothered me for a bit but it's code snippets like this which show how it almost reads like english that make me really appreciate it.  I know it's what the OP wanted anyway but just thought I'd say thanks for sharing.

---

