---
title: "Bash scripting: How to get the PID of a specific process?"
date: 2010-02-18
forum: Programming Talk
---

### Post by CyberAngel on 2010-02-18
Hello,

I have written a bash script like the following one, to monitor a file for new line additions and make some calculations..

```
#!/bin/bash

tail -f somefile | while read line; do
        echo $line
        #Do whatever with the line
done
```

The problem is that If I kill the script, the "tail -f somefile" process is still running.
How can I "trap" the process to kill it too when the script that called the process has been killed?

Thanks

---

### Post by dwhitney67 on 2010-02-18
```

#!/bin/bash

tail -f **--pid=$$** somefile | while read line
do
        echo $line
        #Do whatever with the line
done

```

---

### Post by CyberAngel on 2010-02-19
> **dwhitney67 said:**
> ```

#!/bin/bash

tail -f **--pid=$$** somefile | while read line
do
        echo $line
        #Do whatever with the line
done

```

Thanks!
That one worked :)

---

