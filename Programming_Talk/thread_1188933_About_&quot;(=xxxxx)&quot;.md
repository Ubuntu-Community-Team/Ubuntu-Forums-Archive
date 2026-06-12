---
title: "About &quot;(?=xxxxx)&quot;"
date: 2009-06-16
forum: Programming Talk
---

### Post by huangyingw on 2009-06-16
Hello, I use following pattern
```

(?=NT_)Windows

```
to try to match out
```

Windows

```
from 
```

NT_Windows

```
But, it return me nothing, what is the problem?

---

### Post by jespdj on 2009-06-16
What programming language? Show us your source code.

---

### Post by huangyingw on 2009-06-16
> **jespdj said:**
> What programming language? Show us your source code.
I am using c# in MonoDevelop. Source code
```

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Text.RegularExpressions;

namespace Regulator
{
    class Program
    {
        static void Main(string[] args)
        {
            Match m = Regex.Match(@"NT_Windows", @"(?=NT_)Windows");
            Console.WriteLine("Match=" + m.ToString());
        }
    }
}

```

---

### Post by ghostdog74 on 2009-06-16
no need regular expression. simple logic will do
```

 if "NT_windows" in string or "Windows" in string 
   do  something

```
check your C# documentation on how to check whether a string contains a substring

---

### Post by huangyingw on 2009-06-16
> **ghostdog74 said:**
> no need regular expression. simple logic will do
```

 if "NT_windows" in string or "Windows" in string 
   do  something

```
check your C# documentation on how to check whether a string contains a substring
Hi, thanks. Your solution could work around in such a simple case. While it might be difficult to solve my real one. This one is just a simply one to clerify my confusion. My real one is like (?=(\d{2,3}-\d{2,3}(\1)(?=_branch)))_build. I am sorry to forget it at this time. I found that the (?=branch) works, while the (?=(...)) does not work, so I write this one to try to clerify my confusion:(.....
You see, I have BTW-ly mentioned this in the following thread:
[http://ubuntuforums.org/showthread.php?t=1186866](http://ubuntuforums.org/showthread.php?t=1186866)
because this current issue is not the main focusing confusion in that above mentioned thread, so I open this new one. Sorry for this...

---

