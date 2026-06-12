---
title: "a char is i byte and int is 4 byte then how does char a='Z' work"
date: 2011-06-19
forum: Programming Talk
---

### Post by jamesbon on 2011-06-19
I am not clear with a simple situation

```
char a='Z';
```

that is what we mostly use to assign Z to a.
Now the question is 

```
sizeof(a) gives 1
```

and Z is it its integer value which is 4 bytes.Then how can a 

```
char a (1 byte)='Z'(4 bytes)
```

statement works.
```

#include<stdio.h>

int main (){

char c='a';
printf("%d %d", sizeof(c),sizeof('a'));
}
```

The above code will give output 
```
1 4
```

---

### Post by ChipOManiac on 2011-06-19
I'm kind of new to programming... but doesn't a character variable act as a pointer to the address of where the data is? perhaps this is the explaination... :( I'm not sure... but in case I'm wrong or just plain stupid I'm ready for whiplash :D

---

### Post by GeneralZod on 2011-06-19
As far as I can tell: this is a rather odd language quirk and the reasons why 'Z' would be an int rather than a char seem to be rather murky and historical.  See e.g.

[http://stackoverflow.com/questions/433895/why-are-c-character-literals-ints-instead-of-chars](http://stackoverflow.com/questions/433895/why-are-c-character-literals-ints-instead-of-chars)

for more discussion.

---

### Post by sanderd17 on 2011-06-19
EDIT: sorry, completely wrong.

---

### Post by JupiterV2 on 2011-06-20
A _char_acter is 1 byte, a byte in modern programming being 8bits. The maximum values of a signed byte are: -128 to 127, or 0 to 255. The main use of char is for displaying human-readable characters (though not exclusively). Search for 'ascii character' too see what they are.

An _int_eger is an number. It is, on some systems, 4 bytes. That's 32 bits, or 2^32. It can hold a character because a character is a digit to a computer. An integer, therefore, can hold a character since its maximum unsigned value is 255.

To clarify, when you use sizeof ('A'), the compiler sees sizeof (int), which is four bytes. This is because 'A' is used as a constant, and therefore it is actually interpreted an integer when you use it as you have. 'A' can be stored in a single byte char, an integer, a long, etc. A number is a number.

If you want to see the digit which represents a character use:
```
#include <stdio.h>

int main(void)
{
  char i;

  for (i = 'A'; i <= 'Z')
    {
      printf ("%d\n", (int) i);
    }
  return 0;
}
```

---

### Post by StephenF on 2011-06-20
.

---

