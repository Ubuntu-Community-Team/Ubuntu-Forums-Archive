---
title: "Bash Script Not Outputting Line Breaks"
date: 2010-02-11
forum: Programming Talk
---

### Post by joshpennington on 2010-02-11
I am trying to make a script that will show me specific system stats so I can try and see what is causing the memory on the system to be completely used up.

I want to do this via a bash script so that I can have it send me an email every X minutes (I'll do that in cron).

Now when I run the script, it is not respecting the line breaks that would happen if I just ran the program.

For example I run:

free -t -m

I would get the following output:

             total       used       free     shared    buffers     cached
Mem:         16058       3256      12802          0        412       2459
-/+ buffers/cache:        383      15674
Swap:         1984          0       1984
Total:       18042       3256      14786

Here is my script:

echo "Memory Useage"
echo -e `free -t -m`

However, when I run the script I get the following output:

total used free shared buffers cached Mem: 16058 3249 12808 0 412 2459 -/+ buffers/cache: 376 15681 Swap: 1984 0 1984 Total: 18042 3249 14793


Is there a way to get the output to match?

Any help would be appreciated.

Josh Pennington

---

### Post by SecretCode on 2010-02-11
Why use echo at all? Why not just have 
```
free -t -m 
```
in your script?

But if you need to, it looks like
```
echo "`free -t -m`" 
```
will do the trick.

---

### Post by kamaji792 on 2010-02-11
Hi Dude,

I think the following should do what you want.

```
#!/bin/bash

echo "Memory useage"
echo "`free -tm`"
```

Note the **double quotes** round the `free -tm`.

atb

---

### Post by pbrane on 2010-02-11
another way to do this, in case you want to gather information and then format and display it later on in the script:
```


memory=$(free -t -m)
.
.
.
echo "$memory"

```

---

### Post by joshpennington on 2010-02-11
That works great!  Thanks guys!

---

