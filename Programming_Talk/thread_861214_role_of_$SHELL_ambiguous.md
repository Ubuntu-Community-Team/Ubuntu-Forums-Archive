---
title: "role of $SHELL ambiguous"
date: 2008-07-16
forum: Programming Talk
---

### Post by dexter.deepak on 2008-07-16
```
echo $SHELL
```
this is supposed to return the value of the shell we are using.
this is what i do :
```

dpak@dpak-server:~$ echo $SHELL
/bin/bash
dpak@dpak-server:~$ csh
% echo $SHELL
/bin/bash

```
i think it was supposed to return /bin/csh in the latter case.where am i wrong ? and is there any way to get the value of the "temporary" shell ?

---

### Post by dtmilano on 2008-07-16
What about this ?
```

ps -f

```

---

### Post by ghostdog74 on 2008-07-16
> **dexter.deepak said:**
> 
i think it was supposed to return /bin/csh in the latter case.where am i wrong ? and is there any way to get the value of the "temporary" shell ?

$SHELL is not a c-shell in built variable. Its for bash.  use $shell for csh.
```

/test# echo $shell
/bin/tcsh

```
always check the man page.

---

