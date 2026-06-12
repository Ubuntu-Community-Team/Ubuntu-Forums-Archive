---
title: "getche not declared"
date: 2013-12-06
forum: Packaging and Compiling Programs
---

### Post by rt-ops on 2013-12-06
```

#include <iostream>
#include <conio.h>
using namespace std;
int main()
{
    int chcount=0;
    int wdcount=1;
    char ch='a';
    cout<<"enter a phrase"<<endl;
    while(ch != '\r')
    {
        ch = getche();
        if(ch==' ')
            wdcount++;
        else
            chcount++;
    }
    cout<<"world = "<<wdcount<<endl;
    cout<<"Letters = "<<chcount<<endl;
    return 0;
}
```

I want to correct this errors

---

### Post by r-senior on 2013-12-06
Are you compiling on Linux? If so, you probably don't have conio.h which is where getche is declared. So you need an alternative, such as getchar.

[http://www.cplusplus.com/reference/cstdio/getchar/](http://www.cplusplus.com/reference/cstdio/getchar/)

---

