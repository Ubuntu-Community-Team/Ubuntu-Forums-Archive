---
title: "Quick bash question,"
date: 2012-04-07
forum: Programming Talk
---

### Post by CaptainMark on 2012-04-07
Hi guys, this is probably a simple one for some of our more seasoned vets but I cant seem to get the answer I need via google, I'm probably using the wrong terminology or something.

how do I get a bash script to write an error log only if there is something to write to it?

for example ```
touch now
rm now 2>error.log
```will create the file error.log regardless of if there are any errors or not but it will be empty if the command executes with no problems. ive also tried ```
touch now
rm now || 2>error.log
```but this only creates an error.log if theres a problem but bash will print the error to the terminal screen not pass it to the error.log, 

any help would be much appreciated

regards
mark

---

### Post by CaptainMark on 2012-04-10
Bump, anyone?

---

### Post by CynicRus on 2012-04-10
I think - if you want to write it errors, then the script to capture the output of running the program, and analyze it accordingly. Of course - you need to know that the program displays an error in the case. If you want to write another script log, then do not see any big deal.

---

### Post by julioneander on 2012-04-10
You will need to check the errors manually. This little script worked for me:

```
#!/bin/bash
errors=$(rm now 2>&1)

if [ "$errors" ] ; then
  echo "$errors" > error.log
fi
```2>&1 gets the stderr stream and merges with stdout
You can then trap the output into a variable and check it.

This might be helpful: [http://ubuntuforums.org/showthread.php?t=689289](http://ubuntuforums.org/showthread.php?t=689289)

Regards.

---

### Post by ofnuts on 2012-04-10
> **CaptainMark said:**
> Hi guys, this is probably a simple one for some of our more seasoned vets but I cant seem to get the answer I need via google, I'm probably using the wrong terminology or something.

how do I get a bash script to write an error log only if there is something to write to it?
If nothing is written to the log, it will have a  zero size. So at the end you script can check for the log size and erase it if it is empty:
```

[[ 0 -eq $(wc -c error.log | cut -d " " -f 1) ]] && rm error.log

```

---

### Post by Vaphell on 2012-04-10
-s = test for non-emptiness
```
[ ! -s error.log ] && rm error.log
```

---

### Post by sisco311 on 2012-04-10
You can pipe the stderr of the command in a while loop:
```

rm [OPTION]... FILE... 2>&1 | \
while read -r ; do
    printf '%s\n' "$REPLY" >> error.log
done

```

---

### Post by CaptainMark on 2012-04-10
thanks, good option, ill try them all and see which works best for this script,

---

### Post by ofnuts on 2012-04-11
> **Vaphell said:**
> -s = test for non-emptiness
```
[ ! -s error.log ] && rm error.log
```
* blushes and facepalms * :)

---

