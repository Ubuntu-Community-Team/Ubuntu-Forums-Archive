---
title: "C++11 threading."
date: 2013-10-24
forum: Programming Talk
---

### Post by simon5 on 2013-10-24
Yep. Moving 'Buntu 13.10 has been nothing short of [disastrous]("http://ubuntuforums.org/showthread.php?t=2183314"). Another thing I've found to be working improperly is threading.
Consider this simple piece of code:
```
#include <iostream>
#include <thread>
int main()
{
    std::thread t ([]()
    {
        std::cout << "Hello, World!";
    });
    t.join();
    return 0;
}
```
Compiled with: ```
[COLOR=#000000][FONT=Consolas]g[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]++[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]  main[/FONT][/COLOR][COLOR=#000000][FONT=Consolas].[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]cpp [/FONT][/COLOR][COLOR=#000000][FONT=Consolas]-[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]o main [/FONT][/COLOR][COLOR=#000000][FONT=Consolas]-[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]pthread [/FONT][/COLOR][COLOR=#000000][FONT=Consolas]-[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]std[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]=[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]c[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]++[/FONT][/COLOR][COLOR=#800000][FONT=Consolas]11[/FONT][/COLOR]
```
That, on 13.10, throws an exception:
```
terminate called after throwing an instance of 'std::system_error'  what():  Enable multithreading to use std::thread: Operation not permitted
Aborted (core dumped)
```

... and executes just fine on 13.04. The compiler used in both cases is GCC 4.8.1.
Compiled, and linked against pthread, the same way in both cases.

What's the matter with you, 13.10? What am I doing wrong?

---

### Post by Vaphell on 2013-10-24
apparently bugzored g++
if you check the result with *ldd* there is no pthread to be seen

workaround: slap **-Wl,--no-as-needed** at the end
[https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/1228201](https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/1228201)

---

### Post by simon5 on 2013-10-24
> **Vaphell said:**
> apparently bugzored g++
if you check the result with *ldd* there is no pthread to be seen

workaround: slap **-Wl,--no-as-needed** at the end
[https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/1228201](https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/1228201)

Bah. Thank you. I should seriously improve my search-fu.

---

