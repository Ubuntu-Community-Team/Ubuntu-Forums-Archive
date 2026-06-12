---
title: "ifstream unavalible ?"
date: 2010-08-15
forum: Programming Talk
---

### Post by Cha0sBG on 2010-08-15
Headers included:
```
#ifndef _STRING_
        #include <string>
#endif

#ifndef _STDINCLUDES_
	#include <stdio.h>
	#include <stdlib.h>
#endif

#include <iostream>
#include <fstream>
```

When i try to declare a ifstream variable it says ```
ifstream does not name a type
```

same with ```
ios::in
```

---

### Post by SledgeHammer_999 on 2010-08-15
How do you declare it? Do you have an example? Did you remember to include the "std" namespace?

---

### Post by Cha0sBG on 2010-08-15
Oh dear .... how stupid can i be i forgot that ifstream was part of the 'std' namespace ty for your help.

---

