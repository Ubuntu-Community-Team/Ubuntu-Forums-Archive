---
title: "Simple question about echo in a bash script"
date: 2007-03-05
forum: Programming Talk
---

### Post by LotsOfPhil on 2007-03-05
I want to suppress the on-screen echo when you type. For example:

```

#!/bin/bash
echo -n "Tell me your password: "
read pass

```

Would give:
```

Tell me your password: WHATEVER-YOU-TYPE

```

What I want is this:
```

Tell me your password: 

```
i.e., it's hidden when you are typing.

---

### Post by LotsOfPhil on 2007-03-05
RTFM n00b!

Hehe. Right after I typed this up I figured out the problem was with read, not echo. Thinking back to DOS too much.

Here is what you need, LotsOfPhil:
```

#!/bin/bash
echo -n "Tell me your password: "
read -s pass

```

Note the read **-s** pass

---

