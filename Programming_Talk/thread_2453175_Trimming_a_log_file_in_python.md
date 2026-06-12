---
title: "Trimming a log file in python"
date: 2020-11-04
forum: Programming Talk
---

### Post by pqwoerituytrueiwoq on 2020-11-04
So i am making a plain text file for log data, but this just looks like a resource sink they way this is written
```
    if os.path.getsize(logFile) > 16000000:
        with open(logFile, 'r') as f:
            lines=f.readlines()
        x=0
        while x < 1001:
            del lines[x]
            x++
        with open(logFile, "w+")
            for line in lines:
                logFile.write(line)
```
The I/O time is not a big deal as this file is on a ram disk, but the CPU cycles...

---

### Post by TheFu on 2020-11-04
Just use logrotate.  Don't reinvent the wheel.

---

