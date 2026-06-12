---
title: "decimal to hex"
date: 2009-09-15
forum: Programming Talk
---

### Post by chris200x9 on 2009-09-15
Hi I am having a problem, I just want to warn you this is homework I don't know if that violates the rules. My question is why my hex conversion program works perfectly converting any number into hex that don't require letters but fails on anything that requires letters? Warning two: sloppy code ahead.

```

void decimaltohex()
{
	int decimal;
	int* a = NULL;
	int n =0;
	cin >> decimal;
	int num = ceil(log2(decimal));
	a = new int[num];  
	for (int i=0; i<num; i++) {
		a[i] = 0;    
	}
	while (decimal > 0)
	{
		if (decimal % 16 == 1)
		{
			a[n] =1;
		}
		if (decimal % 16 == 2)
		{
			a[n] =2;
		}
		if (decimal % 16 == 3)
		{
			a[n] =3;
		}
		if (decimal % 16 == 4)
		{
			a[n] =4;
		}
		if (decimal % 16 == 5)
		{
			a[n] =5;
		}
		if (decimal % 16 == 6)
		{
			a[n] =6;
		}
		if (decimal % 16 == 7)
		{
			a[n] =7;
		}
		if (decimal % 16 == 8)
		{
			a[n] =8;
		}
		if (decimal % 16 == 9)
		{
			a[n] =9;
		}
		if (decimal % 16 == 10)
		{
			a[n] ='A';
		}
		if (decimal % 16 == 11)
		{
			a[n] ='B';
		}
		if (decimal % 16 == 12)
		{
			a[n] ='C';
		}
		if (decimal % 16 == 13)
		{
			a[n] ='D';
		}
		if (decimal % 16 == 14)
		{
			a[n] ='E';
		}
		if (decimal % 16 == 15)
		{
			a[n] ='F';
		}
		
		
			decimal /= 16;
			if (decimal != 0)
			{
			n++;
			}
			}
			while (n > 0 || n == 0)
			{
			cout << a[n];
			n--;
			}
			delete [] a; 
			}			

```

Thank you for any/all help :)

---

### Post by dwhitney67 on 2009-09-15
Easy...

```

#include <iostream>
#include <iomanip>

int main()
{
   int value = 1056;

   std::cout << std::hex << std::showbase << value << std::endl;
}

```

---

### Post by chris200x9 on 2009-09-15
> **dwhitney67 said:**
> Easy...

```

#include <iostream>
#include <iomanip>

int main()
{
   int value = 1056;

   std::cout << std::hex << std::showbase << value << std::endl;
}

```

we can't use anything "built in" I don't see why though...

---

### Post by sisco311 on 2009-09-15
hint: 

```
int main()
{
  int a='A';
  cout<<a<<endl;
}

```

output: 65

---

### Post by chris200x9 on 2009-09-15
> **sisco311 said:**
> hint: 'A', 'B', 'C'... are not integers.

funny thing I was thinking about that just as I clicked to view this :) I don't know what I was thinking thank you. If I change it to a char array it ignores my ints I'm assuming I would need two arrays but then how would I "piece them together" in the right order?

edit: oh yea '1' make it a char duh sorry I'm kinda stupid :P thank you!

---

### Post by dwhitney67 on 2009-09-15
The "hard" way...
```

#include <string>
#include <iostream>

std::string decToHex(int decNum)
{
   std::string result;
   std::string tmp;

   do
   {
      int rem = decNum % 16;

      if (rem >= 0 && rem <= 9)
      {
         tmp = ('0' + rem);
      }
      else
      {
         tmp = ('A' + (16 - rem));
      }

      result = tmp + result;

      decNum /= 16;

   } while (decNum != 0);

   return result;
}

int main()
{
   int number = 0;
   std::cout << "Enter a number: ";
   std::cin  >> number;

   std::cout << "\nYour number in hex is: 0x" << decToHex(number) << std::endl;
}

```

---

