---
title: "[C++] substr() behaving strange in 'for' loop"
date: 2009-02-08
forum: Programming Talk
---

### Post by Nexusx6 on 2009-02-08
Hello. I'm new to programming in C++ and am writing a program that needs to read four blocks of characters from a user inputed string at a time in order to manipulate it. 

The way I have it written right now is to user substr() in a 'for loop' until the end of the string is reached. It seemed to work fine at first, but after the first loop substr() returns more than four chunks at a time and I can't seem to understand why. Here is an example and result:
[PHP]
#include <iostream>
#include <string>

using namespace std;

int main()
{
     string msg = "123456789012";
     string string_block;

     for (int i = 0; i<msg.length(); i+=4){
        cout << "i: " << i << endl;         //shows the value of i in the loop purely for debugging
        string_block = msg.substr(i,i+4);   //should only read exactly 4 blocks at time
        cout << "String Block: " << string_block << endl;
     }

    return 0;
}[/PHP]

the 'msg' example is exactly 12 characters long so the loop should run 3 times and pull out 3 blocks of 4-character long strings; instead this is the output:

> 
i: 0
String Block: 1234
i: 4
String Block: 56789012
i: 8
String Block 9012


First and last run of the loop does exactly what I want it to, but the middle draws out 8 blocks instead of 4.If the 'msg' string is longer than 12 characters, say for instance 16 or 24, then the behavior is even more exagerated in the output from the middle. Why is substr() pulling more than 4 blocks at a time for any loop that isn't the first or last?

---

### Post by cyfur01 on 2009-02-08
The general usage of this function is:

#include <string>
    string string::substr(size_type index, size_type length = npos);

Thus, the first argument is the starting index, and the second argument is the number of characters to read. In what you are doing before, you start at index i, and read i+4 characters, so the output is "proper", just not what you wanted. For what you wanted, remove the "i+":
```

#include <iostream>
#include <string>

using namespace std;

int main()
{
     string msg = "123456789012";
     string string_block;

     for (int i = 0; i<msg.length(); i+=4){
        cout << "i: " << i << endl;
        string_block = msg.substr(i,4);   // Now "4", not "i+4"
        cout << "String Block: " << string_block << endl;
     }

    return 0;
} 

```

The fact that the 3rd iteration worked as expected before is just a coincidence since starting at the 8th index there are then only 4 characters left in the string.

---

### Post by jamescox84 on 2009-02-08
```
#include <iostream>
#include <string>

using namespace std;

int main()
{
     string msg = "123456789012";
     string string_block;

     for (int i = 0; i<msg.length(); i+=4){
        cout << "i: " << i << endl;         //shows the value of i in the loop purely for debugging
        string_block = msg.substr(i, 4);   // second argument of substr is length, not end.
        cout << "String Block: " << string_block << endl;
     }

    return 0;
}  
```

Second argument of substr is length, not end.  Hope that helps.

---

### Post by Nexusx6 on 2009-02-08
Aaah! That explains everything. Much appreciated guys, code works perfectly! :KS

---

