---
title: "proggraming puzzle"
date: 2009-09-22
forum: Programming Talk
---

### Post by Strongman332 on 2009-09-22
first off sorry for spelling programming wrong.

does any one know why in C++
```
#include <iostream>
#include <cmath>
#include <cassert>
using namespace std;

int main()
{
  int a;
  assert(sizeof(a)==4);
  a = int(pow(2.,31.))-1;
  cout << a << " + " << a << " = " << a+a << endl;
  return 0;
}
```

returns a negative 4??

also why does ```
int(pow(2.,31.))
``` = 2147483647 and not 2147483648

any help with this would be appreciated

---

### Post by MadCow108 on 2009-09-22
your overrunning the signed integer which only goes to 2^31 - 1 (32 bit - 1 sign bit) which results in undefined behavior (the sign bit gets overwritten in your case resulting in a negative number)
change everything to unsigned int and it works as expected
```

std::cout << (unsigned int)(pow(2.,31.)) << std::endl;
	
	unsigned int a;
	a = (unsigned int)(pow(2.,31.))-1;
	cout << a << " + " << a << " = " << a+a << endl;

```
```

2147483648
2147483647 + 2147483647 = 4294967294

```

---

### Post by Strongman332 on 2009-09-22
i understand how to fix the problem but i don't understand the behavior of the code

---

### Post by MadCow108 on 2009-09-22
in your case the following happens:
2^31 - 1 = 0(sign bit)1111111111111111111111111111110
2*(2*31 - 1) = 1(sign bit)1111111111111111111111111111100
the sign bit changed so the number is negative
on your machine integers are probably saved as "two's complement": [http://en.wikipedia.org/wiki/Signed_number_representations#Two.27s_complement](http://en.wikipedia.org/wiki/Signed_number_representations#Two.27s_complement)
so the result is -4

here a little code to illustrate:
```

#include <iostream>
#include <cmath>
#include <bitset>
using namespace std;
int main (int argc, char *argv[])
{
	int a;
	a = int(pow(2.,31.))-1;
	cout << a << " + " << a << " = " << a+a << endl;
	bitset<sizeof(unsigned int)*8> b1(a);
	std::cout << "a\t\t"<< b1 << " " << int(b1.to_ulong())<<  std::endl;
	unsigned int b = a;
	b+=a;
	bitset<sizeof(unsigned int)*8> b2(b);
	std::cout << "a+a (unsigned)\t"<< b2 << " " << b2.to_ulong() << std::endl;
	bitset<sizeof(unsigned int)*8> b3(b2.to_string());
	std::cout << "a+a (signed)\t" << b3 << " " << int(b3.to_ulong()) << std::endl;
	return 0;
}
2147483646 + 2147483646 = -4
a		01111111111111111111111111111110 2147483646
a+a (unsigned)	11111111111111111111111111111100 4294967292
a+a (signed)	11111111111111111111111111111100 -4

```

---

### Post by Bachstelze on 2009-09-22
I think 2^31 is

10000000 00000000 00000000 00000000

thus 2^31-1 is:

01111111 11111111 11111111 11111111

---

