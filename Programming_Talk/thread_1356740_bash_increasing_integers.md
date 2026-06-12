---
title: "bash: increasing integers"
date: 2009-12-16
forum: Programming Talk
---

### Post by kindofblue89 on 2009-12-16
I want to run a command in the BASH that creates a file so that each time the command is run, the new file will have a file name with **the previous file's integer [COLOR="Red"]plus one[/COLOR]**.

Is this possible in the terminal? I want to run this command at startup so that it will produce a new log file for a program I am running.

---

### Post by lloyd_b on 2009-12-16
> **kindofblue89 said:**
> I want to run a command in the BASH that creates a file so that each time the command is run, the new file will have a file name with **the previous file's integer [COLOR="Red"]plus one[/COLOR]**.

Is this possible in the terminal? I want to run this command at startup so that it will produce a new log file for a program I am running.

Yes, it's possible, but you'll probably want a "key file" to store the next integer to use.  Here's a simple script to illustrate the concepts:```
#!/bin/bash

# First, read the contents of "/etc/nextfilenumber" to determine the integer value to use.
# If that file doesn't exist, start at 1

if [ -f /etc/nextfilenumber ]; then
    # Note the "backtics" around the cat command - NOT single quotes!
    INTVAL=`cat /etc/nextfilenumber`
else
    INTVAL=1
fi

# Write something to a file named "/etc/testfile#.txt", where # is the integer value
echo "This is a test" > /etc/testfile$INTVAL.txt

# Increment the integer value
INTVAL=$((INTVAL + 1))

# Write out the new integer value to /etc/nextfilenumber
echo "$INTVAL" > /etc/nextfilenumber
```

Lloyd B.

---

### Post by kindofblue89 on 2009-12-16
Thanks man!

---

