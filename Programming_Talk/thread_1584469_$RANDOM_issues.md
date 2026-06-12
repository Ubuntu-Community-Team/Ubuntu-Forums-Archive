---
title: "$RANDOM issues"
date: 2010-09-29
forum: Programming Talk
---

### Post by Stunts on 2010-09-29
I'm not sure this is the adequate place for this question, but here it goes.
I'm trying to use the $RANDOM function in a bash script however I'm getting strange results using ubuntu.

Here is the script:
```
RANDOM=$$       
echo $RANDOM$RANDOM $RANDOM$RANDOM $RANDOM$RANDOM
```

Using ArchLinux I get the expected behaviour (for example):
```
380520935 19553849 114661392
```

However, using Ubuntu 10.04 server I get:
```
71507150 71507150 71507150
```

It's always the same. Why does this happen? And what can I do to make it run as expected?
Is this a bug or a feature?

Thank you in advance.

---

### Post by spjackson on 2010-09-29
Your script is probably being processed by /bin/sh, not /bin/bash. Make sure the script begins with:
```

#!/bin/bash

```

---

### Post by Stunts on 2010-09-29
> **spjackson said:**
> Your script is probably being processed by /bin/sh, not /bin/bash. Make sure the script begins with:
```

#!/bin/bash

```

You are dead on!
Problem solved. I suppose this has to do with the default shell on both OSes?
Thank you very much.

---

