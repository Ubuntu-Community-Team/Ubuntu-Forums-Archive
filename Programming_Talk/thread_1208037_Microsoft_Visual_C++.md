---
title: "Microsoft Visual C++"
date: 2009-07-08
forum: Programming Talk
---

### Post by Swenghk on 2009-07-08
I know this is probably the wrong forum to be posting this, but you guys always give me the quickest and most knowledgeable response, but every time I run this code:

```
#define WIN32_LEAN_AND_MEAN // trim down the libraries used
#include <windows.h> // main Windows headers

// the main entry point to your program
int WINAPI WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, LPSTR lpCmdLine,
int nShowCmd)
{
// show a very simple message box with the text &#8220;Hello, world!&#8221; displayed
MessageBox(NULL, &#8220;\tHello, world!&#8221;, &#8220;My First Windows Application&#8221;, NULL);
return 0;
}
```

It always give me an error about the Hello World text not being able to be converted...help?

1>c:\users\seth\documents\visual studio 2008\projects\test\test\test.cpp(11) : error C2664: 'MessageBoxW' : cannot convert parameter 2 from 'const char [15]' to 'LPCWSTR'
1>        Types pointed to are unrelated; conversion requires reinterpret_cast, C-style cast or function-style cast

---

### Post by Reiger on 2009-07-08
Well obviously: you have a C-style null terminated string (incidentally, that is why it says const char[15], the \0 is the 15th char) where whatever it is that compiles wants you to have a LPCWSTR, god knows what that may be (am not a Win32 C++ nor a C++ programmer, see).

I'd guess the LPCWSTR is some kind of object to handle locale settings and what have you, a bit like the QString class the Qt toolkit has. I suggest you do a search for LPCWSTR on Google, especially in combination with the word cast.

---

### Post by WildeBeest on 2009-07-08
All you have to do is typecast the string

```

MessageBox(NULL, [COLOR=Red](LPCWSTR)[/COLOR]“\tHello, world!”, “My First Windows Application”, NULL);

```

---

### Post by stair314 on 2009-07-08
I agree that you need to cast it, but my guess is that there is probably a macro for doing the cast. It will look something like _T("Hello world!"). I'm not a Windows programmer either.

---

