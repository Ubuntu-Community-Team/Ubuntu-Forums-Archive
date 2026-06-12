---
title: "Python regex problem (åäö) - swedish spec chars"
date: 2010-07-20
forum: Programming Talk
---

### Post by wconstantine on 2010-07-20
I'm trying to make my regex match a word with Swedish special characters in it. 

This is a line from a file.
```
690382r3<räkneord>fyrtiofjärde
```

My regex looks like this: ```
p = re.compile("\w+<[a-z\såäö]+>", re.IGNORECASE)
```

Why does it not match? I think it's something with the special characters; åäö.

---

### Post by surfer on 2010-07-20
```

#!/usr/bin/python
# -*- coding: utf-8 -*-

import re

swe="690382r3<räkneord>fyrtiofjärde"

p = re.compile("\w+<[a-z\såäö]+>", re.IGNORECASE)

res = p.search(swe)
print res.group(0)

```

...this works for me.

---

### Post by wconstantine on 2010-07-21
You are quite right. I think the fault lies elsewhere in the code now. Thank you.

---

### Post by Hellkeepa on 2010-07-21
HELLo!

Make sure that the line, and the script, are both encoded in UTF-8. That's a common issue when using the local characters with ASCII-codes > 126, like you've done.

Happy codin'!

---

