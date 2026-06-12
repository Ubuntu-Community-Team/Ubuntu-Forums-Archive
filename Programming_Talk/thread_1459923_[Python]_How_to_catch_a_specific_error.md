---
title: "[Python] How to catch a specific error"
date: 2010-04-22
forum: Programming Talk
---

### Post by dodle on 2010-04-22
I'm trying to catch this specific error and run an exception:
```
OSError: [Errno 39] Directory not empty
```From the Python documentation it looks like I'm supposed to use "os.errno".  So I tried this:[php]import os

try:
	os.rmdir("/home/user/Desktop/New Folder")
except os.errno.ENOTEMPTY:
	print "Directory not empty"[/php]
But I still get the same exact error message.  I know that I can catch the error by doing either of the following:
[php]except:[/php][php]except OSError:[/php]But I want only to catch this specific error.  Is there a way to do it?

---

### Post by dodle on 2010-04-22
Here is the solution I found:
```
import os

try:
    os.rmdir("/home/user/Desktop/New Folder")
except OSError as os.errno.ENOTEMPTY:
    print "Directory not empty"
```

---

### Post by dodle on 2010-04-23
I guess this isn't really a solution:
[quote="Micseydel"]I don't believe that's a solution here. For example, this would work exactly the same -
```
except OSError as anything:
```

In fact, I'm not certain but your code may actually change the os module (what you have running at the time, not a permanent change).[/quote]

---

### Post by matja on 2010-04-23
Hi dodle,

I think what you want is
```

import os

try:
    os.rmdir("/home/user/Desktop/New Folder")
except OSError as exc:
    if exc.errno == os.errno.ENOTEMPTY:
        print "Directory not empty"
    else:
        raise

```

This catch any OSError and names the caught instance *exc*. OSError exceptions carries with them the error number in the instance variable errno. If it's ENOTEMPTY, an error message is printed, otherwise we re-raise the exception since we only want to handle ENOTEMPTY errors.

Regards,
Mattias

---

### Post by dodle on 2010-04-23
Awesome, that is exactly what I needed.  Thanks for your help.

---

