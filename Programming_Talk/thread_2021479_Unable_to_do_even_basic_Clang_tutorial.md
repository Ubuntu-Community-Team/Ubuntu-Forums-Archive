---
title: "Unable to do even basic Clang tutorial"
date: 2012-07-09
forum: Programming Talk
---

### Post by nyknicksfan on 2012-07-09
I'm trying to do the tutorials at:

[https://github.com/loarabia/Clang-tutorial/wiki/TutorialOrig](https://github.com/loarabia/Clang-tutorial/wiki/TutorialOrig)

and I can't even do the first tutorial. I installed LLVM 3.1 and Clang 3.1 and when I do:

~/loarabia-Clang-tutorial-3d79443$ clang++ tutorial1.cpp In file included from tutorial1.cpp:5: In file included from ./llvm/Support/raw_ostream.h:17: ./llvm/Support/llvm/ADT/StringRef.h:13:10: fatal error: 'llvm/Support/type_traits.h' file not found

include "llvm/Support/type_traits.h"
     ^
1 error generated.

Do you know what I am doing wrong? I'm not sure what is the best way to handle this header file problem.

I'm running Ubuntu 12.04.

Thank you.

---

### Post by dwhitney67 on 2012-07-09
Based on the information you posted, I would guess that you need to include a hash-mark before the include directive.  Something like:
```

+---- Hash mark
|
v
#include "llvm/Support/type_traits.h"

```

---

### Post by nyknicksfan on 2012-07-09
> **dwhitney67 said:**
> Based on the information you posted, I would guess that you need to include a hash-mark before the include directive.  Something like:
```

+---- Hash mark
|
v
#include "llvm/Support/type_traits.h"

```


The problem is not about a missing hash mark... thanks.

---

### Post by 11jmb on 2012-07-09
It's really hard to tell what the problem is with so little information. perhaps you could share how you attempted the build or relevant lines from the source files in question?

---

### Post by ofnuts on 2012-07-10
> **nyknicksfan said:**
> I'm trying to do the tutorials at:

[https://github.com/loarabia/Clang-tutorial/wiki/TutorialOrig](https://github.com/loarabia/Clang-tutorial/wiki/TutorialOrig)

and I can't even do the first tutorial. I installed LLVM 3.1 and Clang 3.1 and when I do:

~/loarabia-Clang-tutorial-3d79443$ clang++ tutorial1.cpp In file included from tutorial1.cpp:5: In file included from ./llvm/Support/raw_ostream.h:17: ./llvm/Support/llvm/ADT/StringRef.h:13:10: fatal error: 'llvm/Support/type_traits.h' file not found

include "llvm/Support/type_traits.h"
     ^
1 error generated.

Do you know what I am doing wrong? I'm not sure what is the best way to handle this header file problem.

I'm running Ubuntu 12.04.

Thank you.
Depends where "llvm/Support/type_traits.h" has been put on your disk. If it's under "/usr/include" then use brackets instead of quotes:
```

#include <llvm/Support/type_traits.h> 
```else find a way to specify a user include path to clang and make it point to the parent directory of "llvm"

---

