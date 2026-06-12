---
title: "FindWindow() function for windows example"
date: 2014-06-04
forum: Programming Talk
---

### Post by codyj110 on 2014-06-04
Ok so I had to do a little fiddling around with this function and noticed almost no were on the internet is there a good example of working code.

```

#include <windows.h>
#include <winuser.h>

using namespace std;

int main()
{

    HWND hWnd = FindWindow(L"SciCalc",0);

    SetForegroundWindow(hWnd);

}

```

SciCalc is the classname of windows calculator. To find the class name of a window download WinSpy++. You will need to add L in front of any string you want to use in arguments.

---

### Post by dwhitney67 on 2014-06-05
Wow!

---

### Post by ofnuts on 2014-06-05
Of course, posting this in a Linux forum gives it the visibility it merits with Windows developers :)

Wow? (Why On Windows?)

---

### Post by codyj110 on 2014-06-05
just small program i was making for someone using qt in ubuntu. Just wanted to put it out there for anyone else to help give working code not the garbage of badly arranged code, and or overly long code you have to read through to find usefual information regarding this function.

---

