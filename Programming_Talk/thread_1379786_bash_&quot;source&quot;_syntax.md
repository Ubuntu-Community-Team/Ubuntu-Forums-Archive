---
title: "bash &quot;source&quot; syntax??"
date: 2010-01-12
forum: Programming Talk
---

### Post by xzero1 on 2010-01-12
To put it simply:

This works...

```
#!/bin/bash

#for myfile in *.ts
    source ./mplayerAAPI2.sh 
#done
```

but this does not (syntax error near unexpected token `source')

```
#!/bin/bash

for myfile in *.ts
    source ./mplayerAAPI2.sh 
done
```

that is source call does not work inside the loop.
what am I missing?

note that mplayerAAPI2.sh simply calls mplayer with various parameters and the passed

---

### Post by croto on 2010-01-13
I believe you're missing a "do":
```

#!/bin/bash

for myfile in *.ts; do
    source ./mplayerAAPI2.sh 
done

```

---

### Post by xzero1 on 2010-01-13
DUUUUUHHHH!!  that did it

Now, if I execute the source command in the loop, the commands are forked into multiple processes (nice to know) but what if I don't want it to return until the process completes?

---

### Post by croto on 2010-01-13
I don't know what's into mplayerAAPI2.sh, but I guess you're running a process in the background. In that case, if you want to wait for all processes to finish before continuing, you can use the "wait" command:
```

#!/bin/bash

for myfile in *.ts; do
    source ./mplayerAAPI2.sh 
done

wait

```

---

