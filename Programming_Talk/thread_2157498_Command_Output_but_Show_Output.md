---
title: "Command Output but Show Output"
date: 2013-06-25
forum: Programming Talk
---

### Post by kidovate on 2013-06-25
How can I get the output of a command, for example like this: `mycommand`, but show the command in the terminal as it runs?

---

### Post by Kujua on 2013-06-25
If you are running the command from a script, then please try this:
```
bash -v abc.sh
```

---

### Post by gordintoronto on 2013-06-25
It's not clear what you want. Perhaps you want to see the output from a command, at the same time as you capture it to a file? In that case, use tee. Eg: mycommand | tee ....

For details, run: man tee

---

### Post by papibe on 2013-06-26
Hi kidovate.

If I understand correctly, you are looking for some kind debugging option that let you 'see' what happens inside an expression.

You may use Bash's option xtrace  (**-x**) to do that.

Let say you have this script (script.sh):
```
#!/bin/bash

var=$(pwd)
echo $var

```
Then you can debug it like this:
```
bash **-x** ./script.sh
```
Or, if you prefer, you can turn it on and off just in the parts of code you need debugging. For instance:
```
#!/bin/bash

**set -x**
var=$(pwd)
**set +x**

echo $var

```
Let us know if that helps you accomplish what you are looking for.
Regards.

---

