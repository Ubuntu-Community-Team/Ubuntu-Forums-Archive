---
title: "Bash script using touch for time stamp"
date: 2016-09-21
forum: Programming Talk
---

### Post by Gobugs on 2016-09-21
Howdy

Using Ubuntu 14LTS on desktop

I want to incramentally add 2 minutes to each of the files in a particular folder.
First file  +2 minutes.
Second file +4 minutes.
Thrird file +6 minutes,
etc until end of folder.

This is what I have so far, but its not incramenting like I would like.

#!/bin/bash
#Correct the file time stamps
#  using existing file time stamp
i=2
for item in *
$(i++)
do
  touch -r $item -d '+$i minute' $item
done

This adds 2 to existing for _all_, but not incramented per file.
What did I not understand ??   Educate me please :)

Thanks

---

### Post by steeldriver on 2016-09-21
Your syntax for incrementing $i looks wrong - and is in the wrong place (outside the 'do ... done')

Also shell variables don't get expanded when inside single quotes - so your code should have responded something like

```

touch: invalid date format ‘+ $i minutes’

```

You could try something like

```

i=2
for item in *; do 
  touch -r "$item" -d "+ $i minutes" "$item"
  ((i+=2))
done

```

```

$ touch file{1..5}
$
$ ls --full-time
total 0
-rw-rw-r-- 1 steeldriver steeldriver 0 2016-09-21 20:04:26.660592756 -0400 file1
-rw-rw-r-- 1 steeldriver steeldriver 0 2016-09-21 20:04:26.660592756 -0400 file2
-rw-rw-r-- 1 steeldriver steeldriver 0 2016-09-21 20:04:26.660592756 -0400 file3
-rw-rw-r-- 1 steeldriver steeldriver 0 2016-09-21 20:04:26.660592756 -0400 file4
-rw-rw-r-- 1 steeldriver steeldriver 0 2016-09-21 20:04:26.660592756 -0400 file5
$
$ i=2; for item in *; do touch -r "$item" -d "+ $i minutes" "$item"; ((i+=2)); done
$
$ ls --full-time
total 0
-rw-rw-r-- 1 steeldriver steeldriver 0 2016-09-21 20:06:26.660592756 -0400 file1
-rw-rw-r-- 1 steeldriver steeldriver 0 2016-09-21 20:08:26.660592756 -0400 file2
-rw-rw-r-- 1 steeldriver steeldriver 0 2016-09-21 20:10:26.660592756 -0400 file3
-rw-rw-r-- 1 steeldriver steeldriver 0 2016-09-21 20:12:26.660592756 -0400 file4
-rw-rw-r-- 1 steeldriver steeldriver 0 2016-09-21 20:14:26.660592756 -0400 file5

```

---

### Post by Gobugs on 2016-09-22
Thanks for the education,  I do appreciate learning :)

---

