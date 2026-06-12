---
title: "remove pattern matched line from logfile"
date: 2009-06-15
forum: Programming Talk
---

### Post by Lampi on 2009-06-15
I have script scanning for various error patterns in syslog.

I get an alert if on of these errors occur. I can confirm this error - after confirm I'd like the script to remove this error line only, keeping the rest of logfile.

Can this be done using sed or awk? If so: How?

---

### Post by ghostdog74 on 2009-06-15
awk
```

#!/bin/bash
awk '/222/{
 print "want to delete " $0 "? (y|n)"
 getline ch < "-"
 if ( ch ~ /[Yy]/){ next }
 else{ print $0 > "temp" }
}END{
 cmd = "mv temp " FILENAME
 system(cmd)
}' file 

```

---

