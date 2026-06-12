---
title: "g++ default libraries"
date: 2008-11-08
forum: Programming Talk
---

### Post by UbeBuntu on 2008-11-08
Hello all.

Until yesterday i have been successfully compiling stuff on ubuntu with g++ compiler. It was not necessary to include some libraries (stdlib.h, string.h ...) at the beginning of *.cpp file.
But now after i have upgraded to 8.10 Intrepid Ibex i just can't do this anymore, i get an error if i try to compile a file without this libraries included in the file.

Can someone please explain me how to set somewhere something that these libraries will be included by default. And please don't tell me i need to apt-get install build-essential...

Thanks

---

### Post by cmay on 2008-11-08
hi.
since you have already become aware of the build-essentials package i have just asked for your tread to be moved to the programming talk section.
i had way too much coffee and i am really not that good at this anyway .
but i hope there is someone that can help you there.
good luck.

---

### Post by ju2wheels on 2008-11-08
If you used functions/features that are typically in string.h and similar C/C++ libraries and it didnt complain when you didnt include them, then it was definitely something wrong with the environment or compiler making assumptions and really should not compile.

Would you mind giving a small code example that wont compile or explain a little more about what your problem is? In general, if you use features of a standard libary, you must always include them at the top of your file. That is standard and no way around that, or else the compiler wont know where to look to include the code for the features you are using.

Edit: BTW, you are making references to standard C libraries (not C++ libraries). So if you are including "string.h" and the such, as opposed to the C++ "string" library you may have to make sure gcc and the standard C libraries are installed. The following should do it for C/C++:

```

sudo apt-get install build-essential gcc g++ libstdc++6 libc6

```

---

### Post by UbeBuntu on 2008-11-08
> 
If you used functions/features that are typically in string.h and similar C/C++ libraries and it didnt complain when you didnt include them, then it was definitely something wrong with the environment or compiler making assumptions and really should not compile.

It has compiled always without including string.h on Ubuntu until now, and on Gentoo also. So i think you're wrong here. There must be some path to these standard libraries or sth alike.

Example (here string.h is not needed):

```

$ cat convert_string_to_double.cpp

#include <iostream>
using namespace std;

int main()
{
        string a = "3.14";
        cout << strtod( a.c_str(), NULL ) << endl;
}

```

```

$ g++ convert_string_to_double.cpp

convert_string_to_double.cpp: In function &#8216;int main()&#8217;:
convert_string_to_double.cpp:7: error: &#8216;strtod&#8217; was not declared in this scope

```

```

# sudo apt-get install build-essential gcc g++ libstdc++6 libc6
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
gcc is already the newest version.
g++ is already the newest version.
g++ set to manually installed.
libstdc++6 is already the newest version.
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by ad_267 on 2008-11-08
You definitely should have to include stdlib.h there. I think something was wrong previously if that could compile without including it.

---

### Post by ju2wheels on 2008-11-08
You are missing the following line:

```

#include <string>

```

So you should have:

```

#include <iostream>
#include <cstdlib>
#include <string>
using namespace std;

int main()
{
        string a = "3.14";
        cout << strtod( a.c_str(), NULL ) << endl;
}

```

Ive been coding in C/C++ for 13 years. Some environments are setup differently than others. If you write your code correctly, the standard way, it wont have problems compiling. But suits you as to what you would like to believe.

Edit: Also be aware strtod is a C function, I added cstdlib as well...

The proper C++ way to convert a string to double, without the use of Boost:

```

#include <sstream>
#include <iostream>
#include <string>
using namespace std;

int main(int argc, char* argv[])
{
    double dblNumber = 0.0;
    stringstream strBuf;
    string strDbl = "3.14159";

    strBuf << strDbl;
    strBuf >> dblNumber;

    cout << "Converted string to double" << dblNumber;

    return 0;

}

```

---

### Post by Sef on 2008-11-08
moved to programing talk.

---

### Post by UbeBuntu on 2008-11-08
It's funny, i never really bothered with including c libraries when mixing c and c++ code beacause it just worked. I still can compile this code on Gentoo! And i also could on Ubuntu 8.04, but on 8.10 i can't anymore. Something must have changed with the upgrade, that's what i'm trying to find out.

However, the real problem is that i am using Numerical Recipes files and that i have been able to compile them so far without any problems. And now, after the update and after compiling doesn't work the same way as it did, i get a lot of errors when i try to compile NR code.
This is why i want the compiler to work as it did, because i don't want to include libraries for every NR file. Well i guess this could also be done only once as an option given to the compiler?

And i just found out what was missing to one of NR files:
```

#include <cstdlib>

```
When i added this it got compiled. I quite new to programming but i think NR is a well tested bunch of code and it should get compiled regularly.

---

