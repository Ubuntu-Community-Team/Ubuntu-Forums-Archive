---
title: "Cannot overwrite files using Java Runtime"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by mrcurtin on 2008-11-12
Hi there,

I am trying to execute a bash script using Java.

I am using the Runtime class as follows

Runtime rt = new Runtime()

String[] cmd = new String[3];

cmd[0] = "cmd.exe" ;
cmd[1] = "-C" ;
cmd[2] = "test.bash";

Process child = rt.exec(cmd);


and using StreamGobblers to process the Error and Output streams.

All the test.bash file is doing is:

echo "1" > mytest.bash.

When I run the java program I am being told:

mytest.txt: cannot overwrite existing file.


when I execute the bash file 'normally' -> ./test.bash

it overwrites he file no problem.

Any help really appreciated.

Marius

---

