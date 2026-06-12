---
title: "Error cross compiling for windows"
date: 2011-01-19
forum: Packaging and Compiling Programs
---

### Post by uberwulu on 2011-01-19
I'm taking my first programming class, and I'm sure the ability to create windows executables is going to be a part of it.  I am using Ubuntu 10.10 with CodeBlocks 10.05.  I downloaded the MinGW32/64 suite and wxgtk2.8 from the repositories.  I created a basic hello world program, which, when I clicked Build, generated the following messages during linking:

```

File                                     Line   Message
/home/username/...                       6      multiple definition of 'main'
obj/Debug/helloApp.o:/home/username/...  21     first defined here

```

I assumed this meant that there was already an instance of "main" somewhere.  I opened the helloApp.cpp file referenced in the 2nd message, but didn't see any "main" function.  I'm new to this, so I'm not really sure what I'm doing.  Any help would be greatly appreciated.

---

### Post by uberwulu on 2011-01-19
I just created a new wx project from scratch called WinHello and created one file: WinHello.cpp which contains the following:

```
#include <iostream>

using std::cout;    using std::cin;

int main()
{
    cout << "Hello World!\n";

    char delay;
    cin >> delay;

    return 0;
}

```

I clicked Build and received the same error, except in reverse (line 21: multiple definition of 'main' and line 6: first defined here).

The pre-generated HelloApp.cpp in which it claims there is a "main" looks like this:

```
/***************************************************************
 * Name:      WinHelloApp.cpp
 * Purpose:   Code for Application Class
 * Author:    Me
 * Created:   2011-01-19
 * Copyright: Me
 * License:
 **************************************************************/

#ifdef WX_PRECOMP
#include "wx_pch.h"
#endif

#ifdef __BORLANDC__
#pragma hdrstop
#endif //__BORLANDC__

#include "WinHelloApp.h"
#include "WinHelloMain.h"

IMPLEMENT_APP(WinHelloApp);

bool WinHelloApp::OnInit()
{
    
    WinHelloDialog* dlg = new WinHelloDialog(0L, _("wxWidgets Application Template"));
    
    dlg->Show();
    return true;
}

```

Where line 21 is the ```
IMPLEMENT_APP(WinHelloApp);
```

---

