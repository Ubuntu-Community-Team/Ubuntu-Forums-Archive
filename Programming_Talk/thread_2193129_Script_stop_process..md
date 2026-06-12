---
title: "Script stop process."
date: 2013-12-11
forum: Programming Talk
---

### Post by termvrl on 2013-12-11
Hi all,
I try to write a bash script to translate this command.

```

$ ps -ax | grep sec   
379  p0  S+     0:00.18 perl sec.pl -conf=C5.1.01.conf -input=- -debug=4 $ 
kill -USR1 379

```

this is what i use:

```

#!/bin/bash

PID=ps -ax | grep sec | awk '{print $1}'
kill -USR1 PID
fi

```

Here the error:

```

./restartsec.sh: line 3: -ax: command not found
./restartsec.sh: line 4: kill: PID: arguments must be process or job IDs
./restartsec.sh: line 5: syntax error near unexpected token `fi'
./restartsec.sh: line 5: `fi '

```

how can i solve this?
Thanks

---

### Post by steeldriver on 2013-12-11
You would need to do something like

```
PID=**$(**ps -ax | grep sec | awk '{print $1}'**)**
```

You might want to look at using pgrep instead of ps + grep + awk, or even just pkill

---

### Post by r-senior on 2013-12-11
+1 for pkill

Doesn't the grep match itself in the example above?

```
$ ps ax | grep thisisme
 2824 pts/0    S+     0:00 grep thisisme
```

I think you'd have to do something like:

```
$ ps ax | grep [t]hisisme
```

---

### Post by termvrl on 2013-12-11
Hi all,
i have try. but still same the error.

```

 root@ubuntu:/home/term# ps ax | grep [s]ec
1669 pts/0    S+     0:01 perl sec -conf=tim.conf -input=-
root@ubuntu:/home/term#
root@ubuntu:/home/term# ps ax | grep [s]ec | awk '{print $1}'
1669

```

Here my script.
```

#!/bin/bash
PID2=$(ps ax | grep [s]ec | awk '{print $1}')
echo PID2
kill -USR1 PID2
fi

```

but still got error.

```

root@ubuntu:/home/term# ./restartsec.sh
PID2
./restartsec.sh: line 4: kill: PID2: arguments must be process or job IDs
./restartsec.sh: line 5: syntax error near unexpected token `fi'
./restartsec.sh: line 5: `fi '

```

It seem that the PID is still empty or invalid.
And i have try pkill, but it doesnt work.

Thanks

---

### Post by r-senior on 2013-12-11
You need to remove that line with 'fi' on it. You don't have an 'if' statement that needs a 'fi' to terminate it.

To print out the PID, you need

```
echo $PID2
```

and the same '$' prefix in the kill command.

---

### Post by Habitual on 2013-12-11
```
kill -USR1 $(ps ax | grep [s]ec | awk '{print $1}')
```

---

### Post by termvrl on 2013-12-11
Hi All,

Thanks for the reply. Its work.

```

#!/bin/bash
PID2=$(ps ax | grep [s]ec | awk '{print $1}')
kill -USR1 $PID2

```

---

