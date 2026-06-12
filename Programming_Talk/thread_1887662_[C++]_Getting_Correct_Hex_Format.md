---
title: "[C++] Getting Correct Hex Format"
date: 2011-11-27
forum: Programming Talk
---

### Post by dodle on 2011-11-27
I'm trying to get the hex values from file data that I imported into a character buffer. I use a stringstream to convert each char to a hex string but it is not in the format that I want.

```
...
ffffffe2
ffffff85
ffffffbb
44
16
ffffffa6
0
0
0
0
49
45
4e
44
ffffffae
42
60
ffffff82
...
```

I want them to print out as "0xa6", "0x00", "0x49", etc. Here is my code:

[php]#include <iostream>
#include <fstream>
#include <sstream>
#include <string>
using namespace std;

int main()
{
    ifstream infile;
    infile.open("clock.png", ifstream::binary);
    
    int length;
    infile.seekg(0, ifstream::end);
    length = infile.tellg();
    infile.seekg(0, ifstream::beg);
    
    char data1[length];
    
    infile.read(data1, length);
    infile.close();
    
    string data2[length];
    
    for (int x = 0; x < length; x++)
    {
        stringstream ss;
        ss << hex << (int)data1[x];
        data2[x] = ss.str();
        cout << data2[x] << endl;
    }
    
    return 0;
}[/php]

Any advice?

**----- EDIT -----**
Okay, I made this change:
[php]    for (int x = 0; x < length; x++)
    {
        stringstream ss;
        ss << hex << (int)data1[x];
        data2[x] = "0x";
        data2[x] += ss.str();
        cout << data2[x] << endl;
    }[/php]

Now I get:
```
...
0x16
0xffffffa6
0x0
0x0
0x0
0x0
0x49
0x45
0x4e
0x44
0xffffffae
0x42
0x60
0xffffff82
...
```

My question is how to convert [color=blue]ffffffae[/color] to [color=blue]ae[/color] and [color=blue]0[/color] to [color=blue]00[/color].

---

### Post by GeneralZod on 2011-11-27
This should do the trick:  Remember that "char" can be signed! 

```

#include <iostream>
#include <fstream>
#include <sstream>
#include <string>
#include <iomanip>

using namespace std;

int main()
{
    ifstream infile;
    infile.open("clock.png", ifstream::binary);
    
    int length;
    infile.seekg(0, ifstream::end);
    length = infile.tellg();
    infile.seekg(0, ifstream::beg);
    
    char data1[length];
    
    infile.read(data1, length);
    infile.close();
    
    string data2[length];
    
    for (int x = 0; x < length; x++)
    {
        stringstream ss;
        ss << "0x" << hex << setw(2) << setfill('0') << (int)(unsigned char)data1[x];
        data2[x] = ss.str();
        cout << data2[x] << endl;
    }
    
    return 0;
}  

```

There are probably more elegant & efficient ways of doing it, especially as we know that all output values will be exactly 4 characters long ("0xXY").

---

### Post by McNils on 2011-11-27
use printf instead.

include<stdio.h>

printf("0x%02x\n", data1[x]);

I don't understand why you want to change ffffffae to ae.

---

### Post by dodle on 2011-11-27
You're awesome GeneralZod! Thank you.

---

### Post by dodle on 2011-11-27
Deleted!!!

---

