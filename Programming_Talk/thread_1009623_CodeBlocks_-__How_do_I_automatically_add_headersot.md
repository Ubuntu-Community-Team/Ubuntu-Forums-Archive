---
title: "Code::Blocks -  How do I automatically add headers/other things to all new files?"
date: 2008-12-12
forum: Programming Talk
---

### Post by linkmaster03 on 2008-12-12
How can I set Code::Blocks to automatically add certain headers or declarations to all new source files? Like when I start it up, it is already there. Things like '#include <iostream>' or 'using namespace std;'.

---

### Post by jpkotta on 2008-12-12
RTFM: Sect. 1.10.1.  Default Code

[http://www.codeblocks.org/en-docs-wrapper](http://www.codeblocks.org/en-docs-wrapper)

---

### Post by Caduceus on 2008-12-12
You could make a file with:

```

#include <iostream>
[..Other headers..]
using namespace std;

int main()
{
  return 0;
}

```

Open it, modify as necessary then save as. If there's a quicker way I'd like to know as well.

---

### Post by linkmaster03 on 2008-12-12
> **jpkotta said:**
> RTFM: Sect. 1.10.1.  Default Code

[http://www.codeblocks.org/en-docs-wrapper](http://www.codeblocks.org/en-docs-wrapper)

:oops: Thank you!

---

