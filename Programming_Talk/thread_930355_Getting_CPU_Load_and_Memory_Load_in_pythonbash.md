---
title: "Getting CPU Load and Memory Load in python/bash"
date: 2008-09-25
forum: Programming Talk
---

### Post by TechWizrd on 2008-09-25
I wrote this code to get the CPU Load and Memory usage in python. However, the outputs I get from this are far different than what I get from conky. I think something somewhere is broken or doesn't work.

If anyone can find out what is wrong or has a better way of getting CPU load and memory usage from python/bash, please post your ideas/solutions. This is annoying me to no end.

```
#import all the neccesary modules
import os

#adds up the cpu load and memory load columns in the process list
os.system("ps -eao \'pcpu\' | awk \'{a+=$1} END {print a}\'")
os.system("ps -eao \'pmem\' | awk \'{a+=$1} END {print a}\'")
```

Computer: *Dell B130 Laptop*
CPU: *1.4 Ghz Intel M*
Graphics: *Intel 945G*
RAM/core: *512 MB*
Python version: *2.5.2*
GCC version: *4.2.3*
Operating System: *Ubuntu Hardy Heron (8.10)*

---

