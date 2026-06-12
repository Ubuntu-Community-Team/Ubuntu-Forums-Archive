---
title: "dynamic c++ array"
date: 2009-09-11
forum: Programming Talk
---

### Post by chris200x9 on 2009-09-11
I've written a function that works but I don't understand why one part works. I would appreciate anyone telling me how this works. Thanx :P
```
 
void decimaltobinary()
{
	int decimal;
	int* a = NULL;
	int n =0;
	cin >> decimal;
	int num = 0;
	a = new int[num];  
	for (int i=0; i<num; i++) {
		a[i] = 0;    
	}
	while (decimal > 0)
	{
		a[n] =decimal % 2;
		decimal /= 2;
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
I just question how it dynamically allocates the array when the size is zero?

---

### Post by Habbit on 2009-09-11
The new[] operator, like malloc(), is guaranteed to return _different_ pointers when asked for a block of memory of size 0. If your code works it's because the region it's stepping into with its a[i] references (which it does not own, because a is a pointer to an array of zero ints) happens to not be in use by any other part of the code.

Put bluntly, if you run that code tomorrow, your computer might catch on fire, or trigger a nuclear launch sequence. Num should be the prospective size of the array, most likely ceil(log2(decimal)) - if I managed to remember my math right.

However, your version is highly inefficient, mostly because your "decimal" number is already in a binary form: you can output it with this *completely untested* code ```
void decimaltobinary()
{
	int decimal;
	int cur_bit;

	cin >> decimal;

	// Skip leading zeroes - note the empty loop
	for (cur_bit = sizeof(int) * 8 - 1; (decimal & (1u << cur_bit)) == 0 && cur_bit >= 0; --cur_bit)
		;
		
	// Now print the actual number
	for ( ; cur_bit >= 0; --cur_bit)
		if ((decimal & (1u << cur_bit)) != 0)
			cout << '1';
		else	cout << '0';
	cout << endl;
}

```
Of course, the (decimal & (1 << cur_bit)) tests the "cur_bit"th bit in the (binary expression of) decimal.

---

### Post by dwhitney67 on 2009-09-11
Agreed... the code in the OP is highly subject to failure.  Aside from the crude/blatant attempt to allocate an array of zero-size, the rest of the code appears as if purposely written to fail as well.

Here's my stab at converting a decimal value to binary:
```

#include <string>
#include <iostream>

template <typename T>
T getInput(const std::string& prompt)
{
   T input;

   while (true)
   {
      std::cout << prompt;
      std::cin  >> input;

      if (std::cin.good()) break;

      std::cout << "Bad input; try again...\n" << std::endl;
      std::cin.clear();
      std::cin.ignore(1024, '\n');
   }

   return input;
}

std::string decimalToBinary(unsigned int value)
{
   std::string binary;

   while (value > 0)
   {
      binary += (value % 2) ? "1" : "0";
      value /= 2;
   }

   return std::string(binary.rbegin(), binary.rend());
}

int main()
{
   unsigned int num    = getInput<unsigned int>("Enter a number: ");
   std::string  binary = decimalToBinary(num);

   std::cout << "binary representation: %" << binary << std::endl;
}

```

---

### Post by MadCow108 on 2009-09-11
ha my code is shorter :P
```

bitset<sizeof(long)*8> bit(494353534L);
std::cout << bit << std::endl;

```

@topic how come that the compiler doesn't warn about that?
I see no possible use.

---

### Post by chris200x9 on 2009-09-11
> **Habbit said:**
> The new[] operator, like malloc(), is guaranteed to return _different_ pointers when asked for a block of memory of size 0. If your code works it's because the region it's stepping into with its a[i] references (which it does not own, because a is a pointer to an array of zero ints) happens to not be in use by any other part of the code.

Put bluntly, if you run that code tomorrow, your computer might catch on fire, or trigger a nuclear launch sequence. Num should be the prospective size of the array, most likely ceil(log2(decimal)) - if I managed to remember my math right.

However, your version is highly inefficient, mostly because your "decimal" number is already in a binary form:

i see thanx!

---

### Post by Lux Perpetua on 2009-09-13
> **MadCow108 said:**
> @topic how come that the compiler doesn't warn about that?
I see no possible use.Of course, you as a human can read the code and immediately see that it doesn't make sense, but syntactically, it isn't wrong or even suspicious. To figure out that this particular code is wrong, you basically have to simulate executing it (mentally), which is beyond what a compiler can be expected to do.

---

