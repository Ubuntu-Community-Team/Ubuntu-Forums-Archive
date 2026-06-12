---
title: "[SOLVED] Detect if script is running in terminal"
date: 2008-02-16
forum: Programming Talk
---

### Post by dje on 2008-02-16
Is there a command i can use in a shell script to detect whether or not itself is running in the terminal or without a terminal. Thanks in advance

dje

---

### Post by ghostdog74 on 2008-02-16
not tested
```

#!/bin/sh
terminal=`tty`
pid=$$
ps -ef | awk -v pid=$pid -v term=$terminal 'pid && $0 ~ term{ print "Running from terminal "term }'


```

---

### Post by stroyan on 2008-02-16
You could use the tty command and compare to 'not a tty'.

---

### Post by dje on 2008-02-16
Thanks ghostdog74 that was really helpful, i modified it slightly for my purposes. If the script isn't run from terminal an error dialog is displayed.

dje

---

