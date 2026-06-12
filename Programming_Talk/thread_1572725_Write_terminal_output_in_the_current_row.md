---
title: "Write terminal output in the current row?"
date: 2010-09-11
forum: Programming Talk
---

### Post by hakermania on 2010-09-11
Many programs use this. Programs like eg. plowshare. The output your current uploading/downloading speed in the currentline. They don't use something like this:
```
#!/bin/sh
a=1
while [ $a ]; do
echo "Current speed is $curspeed"
sleep 1
done
```
because this output in a newline. So, how do I output something on the same line?

---

### Post by Bachstelze on 2010-09-11
```
#!/bin/bash

echo -n "foo"
sleep 2
echo -ne "\b\b\b"
echo -n "bar"
echo

```

Not POSIX-compliant, though. Use printf (the command, not the shell builtin) if you want something portable.

---

### Post by nvteighen on 2010-09-11
> **hakermania said:**
> Many programs use this. Programs like eg. plowshare. The output your current uploading/downloading speed in the currentline. They don't use something like this:
```
#!/bin/sh
a=1
while [ $a ]; do
echo "Current speed is $curspeed"
sleep 1
done
```
because this output in a newline. So, how do I output something on the same line?

They use the '\r' character. Look at this: [http://chris-lamb.co.uk/2008/01/24/can-you-get-cp-to-give-a-progress-bar-like-wget/](http://chris-lamb.co.uk/2008/01/24/can-you-get-cp-to-give-a-progress-bar-like-wget/)

But another alternative would be to use ncurses.

---

### Post by hakermania on 2010-09-11
Thx [nvteighen]("http://ubuntuforums.org/member.php?u=273037"), your answer was better

---

