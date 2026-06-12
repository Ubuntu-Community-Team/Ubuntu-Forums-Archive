---
title: "How do I Sed the output of Find?"
date: 2011-10-16
forum: Programming Talk
---

### Post by kliq on 2011-10-16
Hello

I wanted to filter the output of Find containing lines such as:
```

find: &#8216;/proc/4689/fd&#8217;: Permission denied

```by doing:
```

find / -name xli* -print | sed -n '/denied/d; p'

```but I still get all the "Permission denied" lines.
What am I doing wrong?

---

### Post by Vaphell on 2011-10-16
try
```

find / -name xli* **2>&1** | sed -n '/denied/d; p'
```
these are messages sent to stderr, while pipe catches stdout. This construct channels error messages to stdout

alternatively grep instead of sed
```
find / 2>&1 | grep -v denied
```

even better to redirect stderr to /dev/null with no piping at all
```
find / -name xli* **2>/dev/null**
```

---

### Post by papibe on 2011-10-16
Besides Vaphell's good advices, I just wanted to point out that the name expression will be affected by shell globbing. My guess is that you don't want that, and you are looking for files and directories that match the intact expression.

In order to do that use:
```
'xli*'
``` or this
```
xli\*
```
Regards.

---

### Post by kliq on 2011-10-17
Thank you Vaphell and Papibe for your help.

---

