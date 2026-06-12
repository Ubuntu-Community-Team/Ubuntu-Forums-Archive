---
title: "Execute Shell script from another Shell Script"
date: 2010-07-14
forum: Programming Talk
---

### Post by danielgroves on 2010-07-14
Hi,

How can I execute a shell script with another?  I have searched online and not found anything on this!

Thanks,
Dan.

---

### Post by Zorgoth on 2010-07-14
Just type the location of the shell script?

e.g.

script1.sh
```

./script2.sh

```

---

### Post by danielgroves on 2010-07-15
> **Zorgoth said:**
> Just type the location of the shell script?

e.g.

script1.sh
```

./script2.sh

```

Tried that, did't do anything!

---

### Post by -grubby on 2010-07-15
Make sure it's set to execute.

```

chmod +x script2.sh

```

---

### Post by CannibalZerg on 2010-07-15
script1-cmd
```

[COLOR=Red]#!/bin/sh[/COLOR]
/home/john/script2-cmd param1 param2

```

script2-cmd
```

[COLOR=Red]#!/bin/sh[/COLOR]
echo "script2-cmd running now with parameters:"
echo "$1"
echo "$2"

```

Both files should be marked as executables ( chmod +x )

---

