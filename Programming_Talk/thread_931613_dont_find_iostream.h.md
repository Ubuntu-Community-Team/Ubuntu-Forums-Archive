---
title: "dont find iostream.h"
date: 2008-09-27
forum: Programming Talk
---

### Post by giuseppe500 on 2008-09-27
hy.
I have this code in eclipse.
```

#include "iostream.h"
using namespace std;

int main() {
	cout << "!!!Hello World!!!" << endl; // prints !!!Hello World!!!
	return 0;
}

```

the compiler catch an error on this line:
#include "iostream.h"

and i can't find iostream.h anywhere in the filesystem.
I use ubuntu 8
ps.Everitime that i compile in the shell appear this row:Unable to find full path for "g++"

---

### Post by gomputor on 2008-09-27
> **giuseppe500 said:**
> hy.
I have this code in eclipse.
```

#include "iostream.h"
using namespace std;

int main() {
	cout << "!!!Hello World!!!" << endl; // prints !!!Hello World!!!
	return 0;
}

```

the compiler catch an error on this line:
#include "iostream.h"

and i can't find iostream.h anywhere in the filesystem.
I use ubuntu 8

Just use:
```
#include <iostream>
```

---

### Post by Joeb454 on 2008-09-27
[php]#include "iostream.h"[/php] tells the compiler to look in the current directory, which - I'm assuming - isn't the correct one.

Also I assume you have installed [build-essential]("apt://build-essential")?

---

### Post by LaRoza on 2008-09-27
> **giuseppe500 said:**
> hy.
I have this code in eclipse.
```

#include "iostream.h"
using namespace std;

int main() {
	cout << "!!!Hello World!!!" << endl; // prints !!!Hello World!!!
	return 0;
}

```


iostream.h is an old version. C++ standard library headers don't have extensions. 

Make sure you have all you need, see [http://ubuntuforums.org/showthread.php?t=689635](http://ubuntuforums.org/showthread.php?t=689635)

---

