---
title: "double data type in C++"
date: 2010-07-14
forum: Programming Talk
---

### Post by nebu on 2010-07-14
I want to get the 52 bits of data which is the mantissa of a double and 11 bit of data which is the exponent seperately

I want to know if it is possible to do that in c

I could manage to do that in java using the Double.doubleToLongBits
Is there something in C++ which does the same thing??

Will the byte order make a difference to in which order these bits are stored in the memory using the ieee754 format??

thanks for the help

---

### Post by donsy on 2010-07-14
Here's a program I wrote some time ago. Hope this helps.
```
#include <iostream> 
#include <algorithm> 
#include <string> 
#include <cmath> 
using namespace std; 
 
string fraction( double f )  
{ 
/* 
Prints the binary fraction equivalent of a decimal fraction. 
There are 53 bits of precision in the IEEE double significand, only 52 
of which are actually stored.  The MSB of the significand is always 1 
and is therefore implied. 
*/ 
  string temp = "."; 
  double frac = f - floor( f );      //separate the fractional part 
  for( int bit = 1; bit <= 53; bit++ ) { 
    double result = 2 * frac; 
    if (result >= 1)    //if the integer part is 1 
      temp = temp + "1"; 
    else                //the integer part is 0 
      temp = temp + "0"; 
    //cout << frac << ' '; //debug 
    frac = result - floor(result);  //save the fractional part 
  } 
  //cout << "\n\n"; //debug 
  return temp; 
} 
 
string integer(double f) 
{ 
  string temp = ""; 
  int i = floor( f ); 
  while ( i ) { 
    if ( i % 2 ) 
      temp = temp + "1"; 
    else 
      temp = temp + "0"; 
    i = i / 2; 
  } 
  reverse(temp.begin(), temp.end()); 
  return temp; 
} 
 
int main(int argc, char* argv[]) { 
  if (argc != 2) { 
    cout << "Needs a floating point parameter\n"; 
    return -1; 
  } 
  double f = atof(argv[1]); 
  cout << integer(f) + fraction(f) << endl; 
  return 0; 
}
```

---

### Post by johnl on 2010-07-14
Here's some C code which will break the ieee754 double into it's parts for you:

```

#include <stdlib.h>
#include <stdio.h>
#include <stdint.h>
#include <math.h>

int main(int argc, char* argv[]) {
    double d = 8796093022208.0; /* this is 2^43 so the mantissa will be 0 */
    uint64_t n = *(uint64_t*)(&d);

    int sign = (n >> 63);               /* sign is the top bit */
    int exponent = (n >> 52) & 0x07ff;  /* exponent is 11 bits starting at
                                         * bit 52 */
    int exp_value = exponent - 1023; /* subtract 1023 to get the 'real'
                                      * value of the exponent */
    uint64_t mantissa = (n & 0x07ffffffffffffLL); /* the mantissa is the
                                                   * bottom 52 bits */
    printf("double: %lf\n", d);
    printf("bits:   ");
    int i;
    for(i = 63; i >= 0; --i) {
        printf("%c", (n >> i) & 0x1 ? '1' : '0');
    }
    printf("\n");
    printf("sign:   %c\n", sign ? '-' : '+');
    printf("exponent: 0x%03x (%d)\n", exponent, exp_value);
    printf("mantissa: 0x%llx (%lld)\n", mantissa, mantissa);

    return 0;
}

```

---

