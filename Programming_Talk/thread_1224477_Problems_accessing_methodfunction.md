---
title: "Problems accessing method/function"
date: 2009-07-27
forum: Programming Talk
---

### Post by James- on 2009-07-27
I'm currently using code::blocks (I'm coding on Linux, obviously :P) when I go to compile my program I get the fallowing error:
> 
~/codeblocks/readconfig/readconfig.h|25|error: 'std::string ReadConfig::ReadConfParameter(char*)' used but never defined|
||=== Build finished: 1 errors, 0 warnings ===|


and if I remove static I get that I have an undefined reference to 'ReadConfige:;readConfParameter(char*)'

readconfig.h
```
 
#ifndef READCONFIG_H_INCLUDED
#define READCONFIG_H_INCLUDED
//.......[skip defines]
namespace ReadConfig
{
	static std::string ReadConfParameter(char* ConfigParam);   //Line 25
}
#endif // READCONFIG_H_INCLUDED

```

main.cpp
```

#include <iostream>
#include <cstdio>
#include <string>
#include "readconfig.h"

using namespace std;

int main()
{
	ReadConfig::ReadConfParameter(conf_STANDBY);
	return 0;
}

```

readconfig.cpp
```

#include "readconfig.h"
#include <iostream>
#include <cstdio>
#include <string>

using namespace std;

std::string ReadConfParameter(char* ConfigParam)
{
//do stuff
}


```

---

### Post by MindSz on 2009-07-27
Been a long time since I c++'ed, but shouldn't you include the '.cpp' file somewhere?

---

### Post by JordyD on 2009-07-27
> **MindSz said:**
> Been a long time since I c++'ed, but shouldn't you include the '.cpp' file somewhere?

No. You compile together all the .cpp files and #include the .h.

---

### Post by dribeas on 2009-07-27
The function should not be static. The undefined reference is probably due to another problem (are you compiling both .cpp files together (or just compiling separatedly and linking together)?

```

g++ -o test main.cpp readconfig.cpp

```

---

### Post by James- on 2009-07-27
indeed it didn't need to be static...code::blocks decided to add the file to the project but decided to NOT add em to build list under(Project->Properties->Build Targets-> Build Target Files: )  I checked them and works great without static :D

---

### Post by dwhitney67 on 2009-07-27
Your method is declared within a namespace.  You may want to define it (in readconfig.cpp) within the same namespace to feel the joy of success.

P.S.  You should avoid including system header files before your project header files.  Always do it the other way around.

P.S. #2  Your method does not need to be declared static.

---

### Post by nvteighen on 2009-07-28
> **dwhitney67 said:**
> 
P.S.  You should avoid including system header files before your project header files.  Always do it the other way around.


There was a reason for that which I don't remember :p

---

