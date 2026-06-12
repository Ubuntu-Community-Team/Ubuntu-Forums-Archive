---
title: "echo $123 outputs 23"
date: 2010-08-23
forum: Programming Talk
---

### Post by adit on 2010-08-23
I didn't define any environment variable 123.  When I type echo $123 in the terminal I get the output 23.  How?

---

### Post by GeneralZod on 2010-08-23
> **adit said:**
> I didn't define any environment variable 123.  When I type echo $123 in the terminal I get the output 23.  How?

Presumably, "$123" is parsed as 

```
$1
``` followed by the string

```
23
```

---

### Post by surfer on 2010-08-23
```

#!/bin/bash
echo $123

```

if you save that in a shell script and call is test.sh

```

$ ./test.sh hello

```
will give you hello23.

bash variables must not start with numbers! $1 is the first argument you pass on the command line.

---

