---
title: "Initialise environment variables before eclipse IDE starts"
date: 2009-03-06
forum: Programming Talk
---

### Post by m_kk on 2009-03-06
Hi,

If I need to initialize specific environment variables (like by executing a startup file or specifying the variables inside eclipse)before running a java project can I do it in eclipse?. 

 I am using eclipse Ganymede on 8.10 Ubuntu.

The reason is I am using System.getenv(variable_name); in my java program and generally in production we run it using shell script. But for running from eclipse I have to edit the java file and set the values manually.

thanks in advance

---

### Post by dwhitney67 on 2009-03-06
Put them in your .bashrc file, which is in your home folder.

For example:
```

export MYVAR=something

```

---

### Post by m_kk on 2009-03-06
thanks but i want the variable to be initialized just for eclipse.

---

### Post by slavik on 2009-03-06
something like the following will work :)

```

#!/bin/bash

export MY_ENV_VAR1=MY_ENV_VAL1 MY_ENV_VAR2=MY_ENV_VAL2

exec eclipse

```

---

### Post by m_kk on 2009-03-06
well that worked out, thanks

---

