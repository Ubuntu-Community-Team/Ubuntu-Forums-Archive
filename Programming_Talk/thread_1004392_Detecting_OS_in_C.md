---
title: "Detecting OS in C"
date: 2008-12-07
forum: Programming Talk
---

### Post by bluedalmatian on 2008-12-07
Is there a way to detect the OS from C. I dont need to know detailed version info but being able to detect if Linux,Solaris,OS X, Windows etc. would be useful.

---

### Post by Delever on 2008-12-07
Your C program won't work (let's say ;)) on all platforms.

That means you can't include "winsock.h" in your Linux program or "sys/socket.h" in your windows program. Both platforms should use different libraries, so your program will be compiled for both platforms separately.

What I am saying: platform is chosen when compiling, and preprocessor can check if, for example "WIN32" symbol is defined, and include/exclude source code according to that. Like this:

```

#ifdef WIN32
#  include <winsock.h>
#else
#  include <sys/types.h>
#  include <sys/socket.h>
#  include <arpa/inet.h>
#  include <netinet/in.h>
#endif

```

To extend this example, you can write different "main" method for win32 systems and other systems, like this:


```

#ifdef WIN32
int main()
{
   print("Hello from win32");
   return 0;
}
#else
int main()
{
   print("Hello from other system");
   return 0;
}
#endif

```

However, it is good idea to make your code as much platform independent as possible, so you don't have to maintain jungle of "defines".

---

### Post by lovelyvik293 on 2008-12-07
@Delever 
great work.It means that we can chose any of two function in which one runs on win and other on linux only.

---

