---
title: "Can't find the auto c++ code completion option in Eclipse"
date: 2009-08-12
forum: Programming Talk
---

### Post by colau on 2009-08-12
Hi,

The C++ file is run successfully in Eclipse IDE but i can't get the option of auto code completion after typing dot(.) .

Example:
```

#include<iostream>
#include<cstdio>
#include<vector>
#include<algorithm>
#include<string>
#include<cstring>
#include<cmath>
#include<iterator>
#include<map>
#include<queue>
#include<stack>
using namespace std;


int main() {
    vector<int>vvt;
    vvt.
    return 0;
}

```
After the dot (vvt.) can't find the name of the built in functions of vector<int> class.

Am i missing any plugin to install or do I have to configure something?

---

### Post by colau on 2009-08-12
dkpg -l | grep eclipse
```

ii  eclipse                                    3.2.2-5ubuntu3                            Extensible Tool Platform and Java IDE
ii  eclipse-cdt                                3.1.2-2                                   C/C++ Development Tools for Eclipse
ii  eclipse-efj                                3.2.2-5ubuntu3                            Eclipse Java code formatter
ii  eclipse-gcj                                3.2.2-5ubuntu3                            Native Eclipse run with GCJ
ii  eclipse-jdt                                3.2.2-5ubuntu3                            Java Development Tools plug-ins for Eclipse
ii  eclipse-jdt-gcj                            3.2.2-5ubuntu3                            Java Development Tools plug-ins for Eclipse (GCJ versio
ii  eclipse-pde                                3.2.2-5ubuntu3                            Plug-in Development Environment to develop Eclipse plug
ii  eclipse-pde-gcj                            3.2.2-5ubuntu3                            Plug-in Development Environment to develop Eclipse plug
ii  eclipse-platform                           3.2.2-5ubuntu3                            Eclipse platform without plug-ins to develop any langua
ii  eclipse-platform-gcj                       3.2.2-5ubuntu3                            Eclipse platform without plug-ins to develop any langua
ii  eclipse-rcp                                3.2.2-5ubuntu3                            Eclipse rich client platform
ii  eclipse-rcp-gcj                            3.2.2-5ubuntu3                            Eclipse rich client platform (GCJ version)
ii  eclipse-sdk                                3.2.2-5ubuntu3                            Extensible Tool Platform and Java IDE
ii  eclipse-source                             3.2.2-5ubuntu3                            Eclipse source code plug-ins

```

---

### Post by colau on 2009-08-12
Bump

---

