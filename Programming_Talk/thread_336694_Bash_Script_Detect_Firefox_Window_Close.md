---
title: "Bash Script Detect Firefox Window Close"
date: 2007-01-11
forum: Programming Talk
---

### Post by SuperMike on 2007-01-11
From a Bash script, if I load 2 instances of Firefox, and one has a titlebar that has "My Website" in the URL and the other one does not, is there a way to have my Bash script detect when the second window instance (the one that says "My Website") is closed and run some command?

This is important because I need to [shutdown 'thttpd' when my XUL application closes]("http://www.ubuntuforums.org/showthread.php?t=333862").

---

### Post by ghostdog74 on 2007-01-12
just an idea: you can save the PIDs after you launch each of the firefox instances ( to a file maybe?? ) and then have another script to periodically check the current processes against the stored PID values. ..

---

### Post by Engnome on 2007-01-12
Another idea: you can start firefox from a shell script and when firefox exits have your code after it. If you wan't to exit firefox without running your crash code you can try closing the terminal in which the script is running.

---

### Post by SuperMike on 2007-01-15
> **ghostdog74 said:**
> just an idea: you can save the PIDs after you launch each of the firefox instances ( to a file maybe?? ) and then have another script to periodically check the current processes against the stored PID values. ..

Ghostdog, how does Bash get that PID for me? I guess I never learned that one, although I know quite a lot of Bash.

---

### Post by ghostdog74 on 2007-01-16
hi
you can use $! .
for example only: test.sh
```

#!/bin/bash
while [ 1=1 ];
do
   echo "testing"
   sleep 5
done

```

test1.sh :
```

#!/bin/bash
./test.sh &
echo $!

```

By invoking test1.sh, you can get the process id of test.sh  using $!. Of course,this is just an example.

---

### Post by SuperMike on 2007-01-16
Ah, but this only works if you sent the process to the background with '&', I found. And I can't do that because this is a process I need in the foreground until someone clicks X.

What I need is some kind of X11 command that returns a window list.

---

### Post by SuperMike on 2007-01-16
Oh, I found it!

If you know what the window name is going to be, you can do something like loop with the xwininfo command. For instance:

xwininfo -name 'MyAppWindow' 2>&1 | grep -iv 'No window' | wc -l

returns 0 if 'MyAppWindow' is not open, and returns a non-zero value if it is open.

---

