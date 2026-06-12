---
title: "Quick bash script question"
date: 2007-11-07
forum: Programming Talk
---

### Post by pylon42 on 2007-11-07
I'm not a programmer. I'm just messing around with a bash script tutorial cause it looks fun and I'm bored at work.

Is there a way to get commands such as: grep, awk, and sed to refer within the script rather than looking for external files?

Ex:

grep PING blahPINGblah

where "blahPINGblah" is a string and not an external file reference?

---

### Post by PaulFr on 2007-11-07
```
echo blahPINGblah | grep PING

OR

echo blahPINGblah | grep -q PING
echo $? (check return status of 0, 1, 2)
```**man grep** for details of grep.

---

### Post by pylon42 on 2007-11-07
Thank you kindly

---

