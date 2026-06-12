---
title: "need nautilus script for &quot;run in terminal&quot;"
date: 2010-01-12
forum: Programming Talk
---

### Post by xzero1 on 2010-01-12
I would like to write a nautilus script that runs in a terminal so that its output can be seen. Any ideas?

---

### Post by kaibob on 2010-01-12
> **xzero1 said:**
> I would like to write a nautilus script that runs in a terminal so that its output can be seen. Any ideas?
See post 9 in the following thread. It contains a nautilus script that runs in gnome-terminal:

[http://ubuntuforums.org/showthread.php?t=1376386](http://ubuntuforums.org/showthread.php?t=1376386)

---

### Post by xzero1 on 2010-01-13
That method does not return control to "host" script. Still thanks to your help I have found a way.:)

Scripts for playing all video ".ts" files fullscreen in the current directory with output:


calling script (playallTS):

```
#!/bin/bash
gnome-terminal -x tsPlayList.sh
```

called script (tsPlayList.sh):

```
#!/bin/bash

trap 'pkill -ALRM mplayer;exit 1' INT

for myfile in *.ts
do
    stop=`mplayer -fs $myfile | grep -c "End of file"`
    if [ $stop = "0" ]
    then 
       break
    fi 
done
```

---

