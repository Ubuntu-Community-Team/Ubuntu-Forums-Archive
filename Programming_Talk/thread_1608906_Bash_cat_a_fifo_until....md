---
title: "Bash: cat a fifo until..."
date: 2010-10-29
forum: Programming Talk
---

### Post by OlyPerson on 2010-10-29
I'm developing a script where I wish to cat the output of a fifo on the system until I tell it not to (by keystroke preferably).  Here's what I want to do:

```

#! /bin/bash

do
   cat /dev/rtf0 >> my_file.txt
until I press q (or something)

# After that has been cancelled do something else
# e.g. echo "hello


```

The problem is that "cat /dev/rtf0 >> my_file.txt" will run indefinitely.  Is there some way I can have the script listen for keyboard input and then kill the process?

I'm fairly new to scripting still, but was thinking something along the lines of subscripts but I'm not sure.

---

### Post by Arndt on 2010-10-30
> **OlyPerson said:**
> I'm developing a script where I wish to cat the output of a fifo on the system until I tell it not to (by keystroke preferably).  Here's what I want to do:

```

#! /bin/bash

do
   cat /dev/rtf0 >> my_file.txt
until I press q (or something)

# After that has been cancelled do something else
# e.g. echo "hello


```

The problem is that "cat /dev/rtf0 >> my_file.txt" will run indefinitely.  Is there some way I can have the script listen for keyboard input and then kill the process?

I'm fairly new to scripting still, but was thinking something along the lines of subscripts but I'm not sure.

Would interrupting with ^C not be enough?

---

### Post by DaithiF on 2010-10-30
maybe something like:
```
cat /dev/rtf0 >> myfile.txt & pid=$!
until [[ "$keypress" == "q" ]]
do
        read -sn 1 keypress
done
kill $pid
echo "done"
```

---

