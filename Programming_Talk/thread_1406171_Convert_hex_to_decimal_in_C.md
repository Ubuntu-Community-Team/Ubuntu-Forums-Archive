---
title: "Convert hex to decimal in C"
date: 2010-02-13
forum: Programming Talk
---

### Post by Yes on 2010-02-13
I get a hex number, and I need to convert it to int to do some operations on it.  Can anyone tell me how to do that?

I found the function 'htoi' but the compiler can't find that.

Thanks.

---

### Post by MadCow108 on 2010-02-13
double post

---

### Post by MadCow108 on 2010-02-13
just read it in as hex:
int number;
cin >> hex >> number;
cout << dec << number;

edit oops though C++.
in C use scanf with %x as format flag

---

### Post by Shpongle on 2010-02-13
heres a code example [http://www.dreamincode.net/code/snippet888.htm](http://www.dreamincode.net/code/snippet888.htm)

---

### Post by MadCow108 on 2010-02-13
hehe edited before you could quote :P
nevertheless your code "reinvents the wheel" more specific the scanf %x flag
```

#include <stdio.h>
int main()
{
  int a;
  scanf("%x", &a);
  printf("%d\n", a);
}

```

but of course its also nice to see how it works

---

### Post by wmcbrine on 2010-02-13
You could also use strtol() with a base of 16.

BTW, I note that your subject line says "hex to decimal", while the body of your post says "to int". These are not synonymous. If anything, converting it to an int is "hex to binary".

---

### Post by Yes on 2010-02-13
Ah sorry that's not what my problem was.  Here's my code -

```
eeprom_read_byte (11, &buffer2);
tempC = buffer2;
tempF = ((tempC*9)/5)+32;
```

The problem is that eeprom_read_byte puts a decimal value (say, 21) into buffer2.  When I set tempC (an int) equal to buffer2, it thinks buffer2 is a hex value and converts it to it's decimal - so the 21 becomes 33.  How can I stop this from happening?

Thanks!

---

### Post by Some Penguin on 2010-02-14
Computers don't 'think' numbers are hexadecimal or decimal -- that's strictly for human consumption.  They're all binary, all the time.

You might want to describe the data as well as eeprom_read_byte.

---

### Post by dwhitney67 on 2010-02-14
> **Yes said:**
> Ah sorry that's not what my problem was.  Here's my code -

```
eeprom_read_byte (11, &buffer2);
tempC = buffer2;
tempF = ((tempC*9)/5)+32;
```

The problem is that eeprom_read_byte puts a decimal value (say, 21) into buffer2.  When I set tempC (an int) equal to buffer2, it thinks buffer2 is a hex value and converts it to it's decimal - so the 21 becomes 33.  How can I stop this from happening?

Thanks!
For the sake of trying to help you, I'll assume your code looks something like:
```

#include <stdio.h>

void eeprom_read_byte(int loc, char* data)
{
   /* whatever */

   *data = 0x21;   /* from ASCII table, this is same value as '!' */
}

int main()
{
   char buffer2;
   int  tempC;
   int  tempF;

   eeprom_read_byte(11, &buffer2);
   tempC = buffer2;
   tempF = ((tempC*9)/5)+32;

   printf("tempC = %d\n", tempC);
   printf("tempF = %d\n", tempF);

   return 0;
}

```
I suspect your eeprom_read_byte() is not reading decimal 21, but instead hex 21.  This is equal to 33 decimal; 2*16 + 1 = 33.

P.S.  If you want better accuracy for your tempF, I suggest that you use 'float' or 'double'.  You will lose precision when performing 'int' division.

---

