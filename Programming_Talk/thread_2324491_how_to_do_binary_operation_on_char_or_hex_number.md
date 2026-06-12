---
title: "how to do binary operation on char or hex number?"
date: 2016-05-14
forum: Programming Talk
---

### Post by zerop2 on 2016-05-14
got segmentation fault when run below
how to do binary operation?

```
unsigned char mapa(unsigned char bits1, unsigned char bits2)
{
 printf("here3");
 if(bits1 == 0x1 && bits2 == 0x0)
   return 0x0;
 else
   return 0x1;
}
unsigned char* mapa2(unsigned char* bits1, unsigned char* bits2)
{
 unsigned char result[8];
 int i=0; 
 printf("here1");
 for(i=7; i>=0; --i)
 {
  result[i] = mapa(bits1[i],bits2[2]);
 }
 printf("here2");
 return result;
}
unsigned char a1 = 0x01;
unsigned char b1 = 0x00;
int main()
{
printf("test %x\r\n",mapa2(a1,b1));
printf("test %x\r\n",mapa2(b1,a1));



```

---

### Post by dwhitney67 on 2016-05-14
The mapa2() function is attempting to treat the given parameters as if they were an array of unsigned bytes.  This is incorrect; each parameter value is a single 8-bit value.

To examine the individual bits of a value, you need to conjure a bit-mask that can be ANDed to the value.  If the result is 0, then the bit is not set; otherwise it is.

For example:
```

#include <stdio.h>

int main(void)
{
    unsigned char value = 0x33;
    unsigned char mask  = 0x01;

    for (int i = 0; i < 8; ++i)
    {
        printf("bit %d is %s\n", i, ((value & mask) != 0 ? "set" : "unset"));

        mask <<= 1;
    }

    return 0;
}

```

---

### Post by zerop2 on 2016-05-14
i convert a character to character array to store the bits

how to convert this bits array back to hex number store in one character ?

#include <stdio.h>
#include <stdlib.h>


unsigned char mask = 1;
unsigned char bits[8];


unsigned char mapa(unsigned char bits1, unsigned char bits2)
{
 //printf("here3\r\n");
 if(bits1 == 1 && bits2 == 0)
   return 0;
 else
   return 1;
}
unsigned char* mapa2(unsigned char bits1, unsigned char bits2)
{
 unsigned char inputbits1[8];
 unsigned char inputbits2[8];
 int j = 0;
 for (j = 0; j < 8; ++j)
 {
  inputbits1[j] = (bits1 & (mask << j)) != 0;
 }
 for (j = 0; j < 8; ++j)
 {
  inputbits2[j] = (bits2 & (mask << j)) != 0;
 }
 for(j=7; j >= 0; --j)
 {
  printf("input 1 result:%d\r\n",inputbits1[j]);
 }
 for(j=7; j >= 0; --j)
 {
  printf("input 2 result:%d\r\n",inputbits2[j]);
 }




 unsigned char result[8];
 int i=0; 
 printf("here1\r\n");
 for(i=7; i >= 0; --i)
 {
  result[i] = mapa(inputbits1[i],inputbits2[i]);
 }


 for(i=0; i < 8; ++i)
 {
  printf("result:%d\r\n",result[i]);
 }
 
 
 /*
 char* p;
 long int la1 = strtol(result, p, 2);
 printf("after convert:%ld", la1);
 printf("here2");*/
 return result;
}
unsigned char a1[8];
unsigned char b1[8];


//xxd -b readasbinary.csv > export.txt
int main()
{
printf("herem\r\n");
strcpy(a1, "\x01");//0000 0001
strcpy(b1, "\x00");//0000 0000
printf("a1:%s", a1);


unsigned char bits3 = "0";
unsigned char* result = (char*)malloc(sizeof(char));
unsigned char* aa = mapa2(a1,b1);
printf("aa:%d\r\n", aa);


char* p;
long int la1 = strtol(aa, p, 2);
printf("after convert:%ld", la1);

---

### Post by dwhitney67 on 2016-05-15
An unsigned char value can range from 0 to 255; in hex, the equivalent range is 0x00 to 0xFF.  This transformation can easily be achieved using printf() (or other functions such a sprintf()).

You could consider taking your unsigned value to deduce the most-significant and the least-significant values of the hex number by using the division and modulo operations.  For example:
```

...
const char hexDigits[] = { '0', '1', '2', '3', '4', '5', '6', '7', '8', '9', 'A', 'B', 'C', 'D', 'E', 'F' };

void toHex(unsigned char value)
{
    printf("Value %u in hex is 0x%c%c\n", value, hexDigits[value / 16], hexDigits[value % 16]);
}
...

```

As for your code, the mask value that you are using is not being reset after the conversion of 'bits1' and prior to the conversion of 'bits2'.

Worse, your mapa2() is returning a locally defined array ('result').  Once this array goes out of scope, whether it contains the data you expect is unpredictable.  You need to find a better way to return the data.  Perhaps you could augment the function to accept an array (provided by the user) where the result can be stored.

---

### Post by zerop2 on 2016-05-16
i succeed to change.

thank you

---

