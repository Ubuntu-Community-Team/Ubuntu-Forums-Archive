---
title: "[C++]Another fstream question..."
date: 2007-11-20
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2007-11-20
I have a problem. When I use this code:```

s = "//home//<username>//dd.txt";
    settings.open(s.c_str(), std::ios::out);
    if (settings.is_open()) settings << "works";
```

But if I use this, it doesn't work:```

s = "//home//<username>//<new folder>//dd.txt";
    settings.open(s.c_str(), std::ios::out);
    if (settings.is_open()) settings << "works";
```

The difference is that I am trying to create the txt file in a new folder. I was hoping that fstream will automatically create the new folder but it doesn't. Can you tell me how do I create a new folder?

thank you in advance

---

### Post by smartbei on 2007-11-20
You can use the mkdir() function found in the header direct.h. This will only work for linux though. For windows you will need the WinAPI function CreateDirectory()

```

include <direct.h>

int main ()
{
    mkdir("<your directory>");
    return 0;
}

```

See [http://www.warpspeed.com.au/cgi-bin/inf2html.cmd?..\html\book\IBMVACPP\CPPLIB.INF+1105](http://www.warpspeed.com.au/cgi-bin/inf2html.cmd?..\html\book\IBMVACPP\CPPLIB.INF+1105) for reference on that function.

---

### Post by SledgeHammer_999 on 2007-11-20
thanks. I was hoping for something portable. Well, since I can't avoid it, I'll use the wxWidgets functions to do I/O.

---

### Post by smartbei on 2007-11-20
Well, there is the boost function create_directory which is portable - that is if you want to use boost.

---

### Post by aks44 on 2007-11-20
> **smartbei said:**
> Well, there is the boost function create_directory which is portable - that is if you want to use boost.

+1

Anyway if you don't want to use boost, that's probably because you don't know it yet... :p

---

### Post by SledgeHammer_999 on 2007-11-20
> **aks44 said:**
> +1

Anyway if you don't want to use boost, that's probably because you don't know it yet... :p

Well, no. I am already using wxwidgets for the gui in my app, so I will use the wxwidgets functions.

thanks for your posts.

---

