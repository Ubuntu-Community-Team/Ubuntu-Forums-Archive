---
title: "Problem with creating random strings in C++"
date: 2012-03-20
forum: Programming Talk
---

### Post by flurospar on 2012-03-20
I have encountered a problem where I must create a random string with a suffix, but this is giving me some problems.

I tried to do it this way:

```

#define RAND_STR_LENGTH 15

#include <iostream>
#include <cstdlib>
#include <ctime>
using namespace std;

int main()
{
    char rand_char_matrix[64] = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz1234567890";
    char *destination_filename = new char[RAND_STR_LENGTH];
    int counter = 0;
    srand(time(0));
    while (counter <= RAND_STR_LENGTH)
    {
        switch (counter)
        {
            case RAND_STR_LENGTH - 4:
                destination_filename[counter] = '-';
                break;
            case RAND_STR_LENGTH - 3:
                destination_filename[counter] = 'b';
                break;
            case RAND_STR_LENGTH - 2:
                destination_filename[counter] = 'i';
                break;
            case RAND_STR_LENGTH - 1:
                destination_filename[counter] = 'n';
                break;
            case RAND_STR_LENGTH:
                destination_filename[counter] = '\0';
                break;
            default:
                destination_filename[counter] = rand_char_matrix[rand() % 63];
                break;
        }
        counter++;
    }
    
    cout << destination_filename << endl;

}

```

It compiles, but when I run it a few times:

```

$ ./a.out
puxyv63Pwiu-bin
$ ./a.out
zcUay583xxr-bin
$ ./a.out
3DvPgOWY4UV-bin
$ ./a.out
7pUEHbv71u

```

Note that the last run did not produce any suffix, and in the other three cases, the output has 16 characters, instead of 15 (as in RAND_STR_LENGTH).

My question may be outright foolish and/or my C++ code is awful, but since this is just one of my first attempts to write a C++ program, so please help me if you can, and many thanks in advance!

---

### Post by Zugzwang on 2012-03-20
I can point out one thing in your code that is wrong, but don't know if that actually causes your problem.

The line "char *destination_filename = new char[RAND_STR_LENGTH];" should be "char *destination_filename = new char[RAND_STR_LENGTH+1];" as you actually write something into destination_filename[RAND_STR_LENGTH] (namely, '\0').

EDIT: Hey, wait: you only list 62 instead of 64 possible characters in rand_char_matrix - the 63rd should then be "\0", and picking that at random will terminate your string.

---

### Post by flurospar on 2012-03-20
> **Zugzwang said:**
> 

The line "char *destination_filename = new char[RAND_STR_LENGTH];" should be "char *destination_filename = new char[RAND_STR_LENGTH+1];" as you actually write something into destination_filename[RAND_STR_LENGTH] (namely, '\0').

**[...]**  you only list 62 instead of 64 possible characters in rand_char_matrix - the 63rd should then be "\0", and picking that at random will terminate your string.

Thanks a lot, man!

---

### Post by Bachstelze on 2012-03-20
If you don't want to reinvent the wheel:

```
`makepasswd --string "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz1234567890"`-$suffix
```

---

