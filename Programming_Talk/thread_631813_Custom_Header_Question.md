---
title: "Custom Header Question"
date: 2007-12-04
forum: Programming Talk
---

### Post by JupiterV2 on 2007-12-04
Correct me if I'm wrong but is it not good practice to refrain from including standard headers (or any other header for that matter) in custom headers if it can be helped?

Example:

```

#ifndef _CUSTOM_H
#define _CUSTOM_H

class MyClass {
    char* c;

    MyClass(char* str) { c = str; }
};

#endif /* _CUSTOM_H */

```

vs.

```

#ifndef _CUSTOM_H
#define _CUSTOM_H

#include <iostream>

class MyClass {
    std::string s;

    MyClass(std::string str) { s = str; }
};

#endif /* _CUSTOM_H */

```

Which method is preferred?

---

### Post by evymetal on 2007-12-04
er, well surely you have to include standard headers in custom headers sometime?

Otherwise every time you imported a library you would have to import every other library it depends on... (these mount up fast)

---

### Post by JupiterV2 on 2007-12-05
No, I understand that. I just wanted to know if it should be avoided when it was unnecessary, as in the above case where char* would suffice since the features of the string class aren't taken advantage of.

---

