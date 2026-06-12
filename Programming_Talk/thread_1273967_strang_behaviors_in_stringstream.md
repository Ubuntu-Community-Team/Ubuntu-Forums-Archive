---
title: "strang behaviors in stringstream"
date: 2009-09-24
forum: Programming Talk
---

### Post by TheBuzzSaw on 2009-09-24
I am a huge fan of stringstreams now, but I ran into one small issue.
```
#include <iostream>
#include <sstream>
using namespace std;

int main(const int argc, const char** argv)
{
    stringstream ss;
    ss << "55 66 77";
    cout << ss.str() << endl;

    int x, y, z;
    ss >> x >> y >> z;
    cout << ss.str() << endl;
    cout << "values: " << x << " " << y << " " << z << endl;

    ss.str(string());
    ss << "hello";
    cout << "new value: " << ss.str() << endl;

    return 0;
}
```

I suspect that reading in x, y, and z puts some iterator past the end of the character array or something because I can no longer reset the value and/or add "hello" later on. However, if I add a space...
```
ss << "55 66 77 ";
```
...or just not read in all values...
```
ss >> x >> y;
```
...everything works fine. I can empty the stream and/or continue adding values.

Anyone know why this is?

---

### Post by Zugzwang on 2009-09-24
I added some checks to your program:

[PHP]
#include <iostream>
#include <sstream>
using namespace std;

int main(const int argc, const char** argv)
{
    stringstream ss;
    ss << "55 66 77";
    cout << ss.str() << endl;

    int x, y, z;
    ss >> x >> y >> z;
    std::cout << "ss.fail(): " << ss.fail() << "\n";
    std::cout << "ss.eof(): " << ss.eof() << "\n";
    cout << ss.str() << endl;
    std::cout << "ss.fail(): " << ss.fail() << "\n";
    std::cout << "ss.eof(): " << ss.eof() << "\n";
    cout << "values: " << x << " " << y << " " << z << endl;

    ss.str(string());
    std::cout << "ss.fail(): " << ss.fail() << "\n";
    std::cout << "ss.eof(): " << ss.eof() << "\n";
    ss << "hello";
    cout << "new value: " << ss.str() << endl;
    std::cout << "ss.fail(): " << ss.fail() << "\n";
    std::cout << "ss.eof(): " << ss.eof() << "\n";

    return 0;
}
[/PHP]

Obviosly, "ss << 'hello'" causes the problem. Looks like you are not allowed to write to the string after the eof has been reached. So you add a "ss.clear()" right after the "ss.str(string());" command and everything works fine.

---

### Post by TheBuzzSaw on 2009-09-24
Ah yes. Adding a call to clear() indeed fixed everything! Thank you so much.

Why did you add **std::** prefixes to everything when **std** was the active namespace? :P

---

### Post by Zugzwang on 2009-09-24
> **TheBuzzSaw said:**
> Why did you add **std::** prefixes to everything when **std** was the active namespace? :P

Oh, because I usually don't use the line "using namespace std;" but rather prefer to write "std" explicitely all the time. This allows fast moving of the respective functions to header files in case I want to inline some of them for performance reasons, even if they still contain "std::cout/std::cerr" debugging code (e.g., triggered by some #define command).

---

