---
title: "Learning C++: No Window?"
date: 2008-07-09
forum: Programming Talk
---

### Post by knight666 on 2008-07-09
Hi,

I'm trying to learn C++, so I installed KDevelop and started a "Simple Win32 GUI App.".

I'm using the following code to get a window on the screen, most of which is from a book called "Tricks of the Windows Game Programming Gurus Second Edition".

```
#ifdef HAVE_CONFIG_H
#include <config.h>
#endif
#include <windows.h>

#define WINDOW_CLASS_NAME  "WINCLASS1"

LRESULT CALLBACK WindowProc(HWND hwnd, UINT msg, WPARAM wparam, LPARAM lparam)
   {
   PAINTSTRUCT    ps;
   HDC            hdc;
   
   switch(msg)
      {
      case WM_CREATE:
         {
         return(0);
         }
      break;
      
      case WM_PAINT:
         {
         hdc = BeginPaint(hwnd,&ps);
         EndPaint(hwnd,&ps);
         return(0);
         }
      break;
      
      case WM_DESTROY:
         {
         PostQuitMessage(0);
         return(0);
      }
      break;
      
      default:break;
      }
   return (DefWindowProc(hwnd, msg, wparam, lparam));
   }

int STDCALL
WinMain (HINSTANCE hInst, HINSTANCE hPrev, LPSTR lpCmd, int nShow)
{
        MessageBox (NULL, "Hello, Windows!", "Hello", MB_OK);
        
        WNDCLASSEX   winclass;
        HWND         hwnd;
        MSG          msg;
        
        winclass.cbSize          = sizeof(WNDCLASSEX);
        winclass.style           = CS_DBLCLKS | CS_OWNDC | CS_HREDRAW | CS_VREDRAW;
        winclass.lpfnWndProc     = WindowProc;
        winclass.cbClsExtra      = 0;
        winclass.cbWndExtra      = 0;
        winclass.hInstance       = hInst;
        winclass.hIcon           = LoadIcon(NULL, IDI_APPLICATION);
        winclass.hCursor         = LoadCursor(NULL, IDC_ARROW);
        //winclass.hbrBackground   = (HBRUSH)GetStockObject(BLACK_BRUSH);
        winclass.lpszMenuName    = NULL;
        winclass.lpszClassName   = WINDOW_CLASS_NAME;
        winclass.hIconSm         = LoadIcon(NULL, IDI_APPLICATION);
        
        hwnd = CreateWindowEx(NULL,
        WINDOW_CLASS_NAME,
        "AwesoMe Window!",
        WS_OVERLAPPEDWINDOW | WS_VISIBLE,
        0,0,
        400,400,
        NULL,
        NULL,
        hInst,
        NULL);
        
        while (GetMessage(&msg,NULL,0,0))
            {
            TranslateMessage(&msg);
            DispatchMessage(&msg);
            }
        return 0;
}
```

I am using the latest version of Wine at the time of writing (1.1.0).
The messagebox at the beginning shows up, but the window doesn't.:confused:

When I run the program in a terminal, I don't get any messages from Wine.

Is there something wrong with my code or is there something wrong with Wine?

Thanks in advance.

---

### Post by nvteighen on 2008-07-09
Are you sure that's C++? It looks like C to me.

---

### Post by Zugzwang on 2008-07-09
You didn't register the window class prior to using it. See [here]("http://msdn.microsoft.com/en-us/library/ms632680(VS.85).aspx") for details. Also don't forget to add code for checking for error values (I would assume that CreateWindowEx returned NULL).

As far as the C++/C issue from the last message is concerned: It looks like the OP only used parts defined in both languages, so it is technically speaking both at the same time.

---

### Post by dribeas on 2008-07-15
> **knight666 said:**
> Hi,

I'm trying to learn C++, so I installed KDevelop and started a "Simple Win32 GUI App.".


I think you'll be better off asking in a windows-related c++ programming forum. Most of the code is windows-only and the problems are Win32 GUI related.

---

