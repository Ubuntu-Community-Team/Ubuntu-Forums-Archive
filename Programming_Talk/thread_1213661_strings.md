---
title: "strings"
date: 2009-07-15
forum: Programming Talk
---

### Post by zaac on 2009-07-15
hey,
ive been stuck on this for a while, it should be easy,but i just cant get it.

what im trying to do is take a single digit from a string of digits and convert it into an int. heres my code so far

```

#include <sstream>
#include <iostream>
#include <string>

using namespace std;

int main() {
    string str = "73167176";
    int i = 4;
    int num1;
    istringstream buffer(&str[i]);
    buffer >> num1;
    cout << num1 << endl;
}

```

the problem with this is that i get the number 7176 instead of 7.

if i pass in str[i] instead of &str[i] i get en error "invalid conversion from ‘char’ to ‘std::_Ios_Openmode’"

how do i fix this problem?, or point me in the right direction

thanks, zac

---

### Post by abhilashm86 on 2009-07-15
you need to output str instead of num1.............
check this
```

#include <sstream>
#include <iostream>
#include <string>

using namespace std;

int main() {
    string str = "73167176";
    int i = 4;
    int num1;
    istringstream buffer(&str[i]);
    buffer >> num1;
    cout << str[i] << endl;
}

```

---

### Post by zaac on 2009-07-15
but str is a string and i need an int

---

### Post by abhilashm86 on 2009-07-15
> **zaac said:**
> but str is a string and i need an int

here you are reading whole string from value pointed by integer i, so read just a single character, then you'll able to print intermediate values.........

---

### Post by bhagabhi on 2009-07-15
change your line
```

istringstream buffer(&str[i]);

```

to 
```

istringstream buffer(str.substr(4,1));

```

---

### Post by zaac on 2009-07-15
> **abhilashm86 said:**
> here you are reading whole string from value pointed by integer i, so read just a single character, then you'll able to print intermediate values.........

im trying to read a single character and convert it to an int, but when i but it into the buffer it automatically takes multiple characters. 

i need it as an int so it can be used in calculations, printing it is just to test to make sure it only takes one character

zac

---

### Post by zaac on 2009-07-15
thanks bhagabhi

---

### Post by MindSz on 2009-07-15
You can also get a character and type-cast it as an int and subtract 0x30 from it. That should give you the integer value.

Here's a simple program:

```
#include <stdio.h>
int main(){

  char c = '7';
  int n = (int) c;

  n -= 0x30;
  printf("%d\n", n);
  return 0;
}
```

---

### Post by c0mput3r_n3rD on 2009-07-15
> **MindSz said:**
> You can also get a character and type-cast it as an int and subtract 0x30 from it. That should give you the integer value.

Here's a simple program:

```
#include <stdio.h>
int main(){

  char c = '7';
  int n = (int) c;

  n -= 0x30;
  printf("%d\n", n);
  return 0;
}
```

+1
I find type casting to be much easier, and more readable.
You did it in c though and he's doing c++, it ends up being the same either way though.

---

