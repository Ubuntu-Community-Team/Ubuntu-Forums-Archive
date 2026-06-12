---
title: "Opening brace not expected in Geany in C++?"
date: 2010-02-11
forum: Programming Talk
---

### Post by Kenny_Strawn on 2010-02-11
I need some help here. I am trying to set a range of numbers to return numbers within - correctly this time.

I have run into plenty of problems:

[quote="Geany"]
enccrack.cpp:7: error: a function-definition is not allowed here before ‘{’ token

enccrack.cpp:14: error: a function-definition is not allowed here before ‘{’ token
[/quote]

What exactly does this mean? What should I use to combat this error, because I don't see a reason for it. How can you define a function without braces?

---

### Post by Some Penguin on 2010-02-11
What do those lines actually have?

---

### Post by NovaAesa on 2010-02-11
Sounds like a syntax error. It's hard to work out precisely what is wrong without seeing the code you are trying to compile.

---

### Post by Kenny_Strawn on 2010-02-11
> **Some Penguin said:**
> What do those lines actually have?

This is the block defined by line 7:

```

int key(int lowerLimit, int upperLimit)
{
        lowerLimit = 0x00000000000000000000000000;
        upperLimit = 0xffffffffffffffffffffffffff;
        return (upperLimit, lowerLimit);
};

```

And this is the block defined by line 14:

```

void crack ()
{
        key >= lowerLimit;
        key <= upperLimit;
        return key;
};

```

Mods, I am only trying to get support on this issue. Don't think I am trying to post this as a conspiracy to crack encryption.

---

### Post by lisati on 2010-02-11
Troubleshooting tip: when a compiler puts out an error message, it usually points out where it noticed the problem. Sometimes the real problem is two or three (or more) lines earlier.

---

### Post by Kenny_Strawn on 2010-02-11
> **lisati said:**
> Troubleshooting tip: when a compiler puts out an error message, it usually points out where it noticed the problem. Sometimes the real problem is two or three (or more) lines earlier.

This is the whole file:

```

#include <iostream>
#include <cmath>
    
int main ()
{
    int key (int lowerLimit, int upperLimit)
    {
        lowerLimit = 0x00000000000000000000000000;
        upperLimit = 0xffffffffffffffffffffffffff;
        return (upperLimit, lowerLimit);
    };
    
    void crack ()
    {
        key >= lowerLimit;
        key <= upperLimit;
        return key;
    };
    return 0;
};

```

As you can see, it is only 20 lines long. Is it something to do with the main() function? I was thinking this...

---

### Post by lisati on 2010-02-12
I'm more familiar with the general layout of C than C++, but suspect that the compiler might be getting tripped up by having the functions defined within main().

---

### Post by schauerlich on 2010-02-12
> **Kenny_Strawn said:**
> This is the whole file:
As you can see, it is only 20 lines long. Is it something to do with the main() function? I was thinking this...

Four things right off the bat:
[list][*]You're trying to define a function inside of main. The function definitions should be above main, and replaced inside of main with function calls.
[*]There's no semicolon after function definitions.
[*]You're giving a hex value (and an obscenely large one, at that) to an int.
[*]Neither of your functions achieve anything useful, or even follow basic C++ syntax.[/list]

---

### Post by Kenny_Strawn on 2010-02-12
> **schauerlich said:**
> Four things right off the bat:
[LIST]
[*]You're trying to define a function inside of main. The function definitions should be above main, and replaced inside of main with function calls.
[*]There's no semicolon after function definitions.
[*]You're giving a hex value (and an obscenely large one, at that) to an int.
[*]Neither of your functions achieve anything useful, or even follow basic C++ syntax.
[/LIST]


Okay, I moved the function definitions to the outside of main.

As for the semicolons after function definitions, I have them after the closing curly brace, which is definitely legal, as I have a "Hello World" program with the same syntax as far as semicolons in function definitions is concerned.

Third: Which operators handle hex values?

Fourth: What this program is supposed to be is a program that uses a listed range of hex codes (notice the "<=" and ">=" values before the lower and upper limits of the range) to crack encryption on certain devices (such as iPhones) and mount them in Linux using the console (and mentioning the block device of the volume after the command, of course). No, it is not intended as a malicious program, either, so Mods, you don't need to worry.

---

### Post by MadCow108 on 2010-02-12
you don't need operators to handle hex values, hex is just a representation of a number (and its all binary internally anyway, no matter which format you use in your code)
to output in hex format pipe "hex" into your streams
cout << hex << someinteger << endl;

but you should really look at the basics of C/C++ again.
Your code is plain wrong in almost every line.
You can't return tuples in that way. You need define a data structure for that (or use std::pair), there are no <= >= assignment operators in C++ (just comparison)
and your return types are wrong

Also have a look at datatypes. your numbers are far to big to be saved in a 32 bit integer

---

### Post by CptPicard on 2010-02-12
Consider:

```

void try_crack(unsigned int key) {
  // magic happens here
}

int main() {

  for (unsigned int i = 0; i < 0xFFFFFFFF; i++)
    try_crack(i);

}

```

(I'm assuming a 32 bit unsigned int key)

I honestly don't understand how you imagine your code is supposed to work, but that's how one would go about a really naive brute-force enumeration of a (not real) keyspace. Of course, if it worked like that, encryption would be useless.

---

### Post by Kenny_Strawn on 2010-02-12
> **CptPicard said:**
> Consider:

```

void try_crack(unsigned int key) {
  // magic happens here
}

int main() {

  for (unsigned int i = 0; i < 0xFFFFFFFF; i++)
    try_crack(i);

}

```(I'm assuming a 32 bit unsigned int key)

I honestly don't understand how you imagine your code is supposed to work, but that's how one would go about a really naive brute-force enumeration of a (not real) keyspace. Of course, if it worked like that, encryption would be useless.

The ultimate question: Can C++ handle 128-bit hex values?

---

### Post by TehCodr on 2010-02-12
instead of lowerlimit=(enter number here), it should be &lowerlimit, to show you're defining location, not value.

---

### Post by CptPicard on 2010-02-12
> **Kenny_Strawn said:**
> The ultimate question: Can C++ handle 128-bit hex values?

Yes, with a suitable long-int implementation. "Hex" is just the base-16 representation of an integer; the underlying integer is always the same, and in machine terms, in bits.

> **TehCodr said:**
> instead of lowerlimit=(enter number here), it should be &lowerlimit, to show you're defining location, not value.

His code is totally wrong nevertheless.

---

