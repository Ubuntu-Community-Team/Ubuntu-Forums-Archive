---
title: "[C++] Convert decimal to hex"
date: 2012-08-30
forum: Programming Talk
---

### Post by neil_1 on 2012-08-30
Does anyone have a solution for converting decmial to hex ?
For example,
I have
```

int x = 28 ;

```

I would like an int or a long to have the equivalent hex i.e
```

long y = 1C ;

```

I don't want it in string/char[] as I need to do math operations on it.

---

### Post by bouncingwilf on 2012-08-30
Sorry  I'm not sure quite what you mean. In C (which C++ should handle as a valid subset) you can just declare or assign a valid hex value to an integer variable

i.e. 
long y = 0x1C; 

should be perfectly valid

Sorry if I have misunderstood your needs.

Bouncingwilf

---

### Post by neil_1 on 2012-08-30
I solved it!
I wanted a decimal to be converted to a long hex
here's the code:
```

#include <stdio.h>
#include <stdlib.h>
#include <iostream>
#include <string>
#include <sstream>
using namespace std;

int main ()
{
        string s("0x1C");
        unsigned long value;
        istringstream iss(s);
        iss >> hex >> value;
        cout << value << endl;
        return 0;
}
```

---

### Post by steeldriver on 2012-08-30
maybe I'm misunderstanding what you are trying to do, but you can just specify the hex value directly by prepending the 0x modifier

```
#include <iostream>

int main(int argc, char* argv[])
{
  int a = 28;
  long int b = 0x1CL;

  std::cout << a << " " << b << std::endl;

  return 0;
}
```

---

### Post by ofnuts on 2012-08-30
> **neil_1 said:**
> I solved it!
I wanted a decimal to be converted to a long hex
here's the code:
```

#include <stdio.h>
#include <stdlib.h>
#include <iostream>
#include <string>
#include <sstream>
using namespace std;

int main ()
{
        string s("0x1C");
        unsigned long value;
        istringstream iss(s);
        iss >> hex >> value;
        cout << value << endl;
        return 0;
}
```
In the general case there are more efficient ways to convert a string with a hex representation of a number to an integer. See [http://www.cplusplus.com/reference/clibrary/cstdlib/strtol/](http://www.cplusplus.com/reference/clibrary/cstdlib/strtol/)

---

