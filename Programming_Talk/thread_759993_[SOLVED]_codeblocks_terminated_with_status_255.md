---
title: "[SOLVED] codeblocks terminated with status 255"
date: 2008-04-19
forum: Programming Talk
---

### Post by yao_man on 2008-04-19
I have codeblocks svn 5000 on Kubuntu 8.04. I tried to compile and run a project with file test.cpp that I use to test out short code pieces. I compiled the project, and it worked.I tried to run it; however, and I got the following message
```
Checking for existence: /home/myfiles/Documents/c++/scripts/test/bin/Debug/test
Executing: xterm -T test -e /usr/bin/cb_console_runner /home/myfiles/Documents/c++/scripts/test/bin/Debug/test  (in /home/myfiles/Documents/c++/scripts/test/.)
Process terminated with status 255 (0 minutes, 0 seconds)
```
I would appreciate any help you can give me.

---

### Post by thornmastr on 2008-04-19
It is very hard to tell anything without the code. Also, what is the SVN number of your version off CODEBLOCKS?

---

### Post by yao_man on 2008-04-20
I'm running svn 5000. Here is the code
```
// const_cast
#include <iostream>
#include <fstream>
#include <sstream>
#include <string>
#include <cmath>
#include "/home/myfiles/Documents/c++/headers/stream_cast.h"
#include "/home/myfiles/Documents/c++/headers/stringcaps.h"
using namespace std;



int main()
{
    char var = 'a';
    cout << var << endl;
    return 0;
}


```

---

### Post by yao_man on 2008-04-20
I found the problem. xterm was not installed on my system. I ran "sudo aptitude install xterm" and it now executes as expected.

---

### Post by dilipchauhan2045 on 2011-11-21
> **yao_man said:**
> I found the problem. xterm was not installed on my system. I ran "sudo aptitude install xterm" and it now executes as expected.
How can i install this xterm?

---

### Post by dilipchauhan2045 on 2011-11-21
How can i install this xterm?
detail guide first?

---

