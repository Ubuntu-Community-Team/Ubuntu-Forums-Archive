---
title: "symbian-gcc"
date: 2006-10-13
forum: Programming Talk
---

### Post by ilias on 2006-10-13
hi,
from 
[http://www.inf.u-szeged.hu/symbian-gcc/index.php](http://www.inf.u-szeged.hu/symbian-gcc/index.php)
I downloaded two separate versions of gcc for symbian systems
both versions when configuring with prefix=/usr/local/symbian-gcc
had the same error:

>checking system version (for dynamic loading)... ./configure: line 5089: >syntax error near unexpected token `)'
>./configure: line 5089: `    OSF*)'
>configure: error: ./configure failed for unix
>Configure in /usr/local/src/symbian-gcc/tcl failed, exiting.

I'm using dapper drake on a compaq evo 
and linux 2.6.15-27-386

Can anyone identify what the problem is?
I know that it's completely irrelevant but could it be that i'm using a i386 kernel but the configure script identifies my machine as a i686?

I was directed to the site above from the site below:
[http://www.koeniglich.de/sdk2unix/symbian_sdk_on_unix.html](http://www.koeniglich.de/sdk2unix/symbian_sdk_on_unix.html)
any help???

---

### Post by toojays on 2006-10-13
Sometimes these embedded compilers are given out with Windows line endings, which ends up breaking the configure script when you bring it back to a GNU system.

If this is the case, you will need to run the whole lot through dos2unix (from the tofrodos package?). Hint: you can use the find command to make this less time consuming.

Also, you will probably need to install an older version of GCC to compile with. GCC 3.3 and 2.95 should be in the repos.

---

### Post by ilias on 2006-10-14
it's ok i found it...
first I have to install sdk2unix... and through sdk2unix I installed the gcc and UIQ (for sony/ericsson P900 mobiles) and although i haven't tested it yet i can possibly make programs for symbian UIQ OSes...
Thinking about making it a package???
I would love to take over it but I haven't got a clue about package management...

---

