---
title: "if loops for csh"
date: 2009-02-05
forum: Programming Talk
---

### Post by wtruong on 2009-02-05
I have this script

#!/bin/csh
foreach pid (`cat pidtempfile`)
  kill -9 $pid
end

pidtempfile is a list of pid's

If the pid doesn't exist the failed kill breaks the for loop.  How do i fix this?

---

### Post by Tim Sharitt on 2009-02-05
You can use an if-then block to check for the file.

For example:
```

if (-e pidtempfile) then
    foreach pid (`cat pidtempfile`)
    kill -9 $pid
endif
end
```

Or to create the file first:
```

if (! -e pidtempfile) then
    #createfile
endif
foreach pid (`cat pidtempfile`)
kill -9 $pid
end

```

---

