---
title: "Linux And DLLs?"
date: 2007-04-23
forum: Programming Talk
---

### Post by Frederick J. Harris on 2007-04-23
Completely new to Linux here.  Have build-essential package installed and working though, and my C and C++ compilers seem to be good.  I'm wanting to start programming in Linux, but I have some fundamental questions about the OS.  Does it do dynamic linking like Windows???  

     In Windows I like to program as close to the bare metal as possible, and so I do Win32 SDK style Api coding.  Now the core system components that comprise the operating system are Kernel32.dll, Gdi32.dll, and User32.dll.  If Windows is running these components will be in memory.  I can write a complete GUI program which dynamically links with the huge number of system functions in these Dlls without statically linking that code in my exe.  Hence, Windows programs written in this way are very small, and depending on the compiler used, a Hello, World! program may only be 8 to 30 K or so.

     Now as soon as you start using Class libraries such as MFC or Borland's OWL you start getting into megabyte sized Hello, World! programs because all that library code is linked in with the program.  In terms of the .NET framework, there are about 20 megabytes of system code involved which Microsoft now includes with the operating system, so its there, but I actually have some performance issues with .NET, so I'm not really anxious to use it here or there.

     For the past several days I have been researching this issue, not particularly the Dll issue, but trying to find what GUI libraries I should use in attempting to learn GUI programming in Linux.  In following up some leads on wxWidgets I ended up at Amazon.com reading reviews on a book written by the creator of wxWidgets.  A reviewer said that in compiling with that library he/she ended up with an 800K executable!

     I'd personally find that hard to take.  From what I'm learning it looks to me like I might be at home using the X Window interface directly, and I've ordered a couple of books from Amazon.com on that that also has some Motif stuff in it.  Would anyone be able to shed some light on these issues for me?  For example, Xlib
doesn't include much in the way of graphical user interface elements such as buttons, scroll bars, combo boxes does it???  If that is the case then I've either got to create them myself or use another library that sits on top of XLib, Right?

     Is this a good forum for me?  Any other good programming sites anyone would recommend?

PS -- I realize this isn't Windows!  If Linux doesn't do stuff like Windows that is OK with me.  I'll try to learn
how to do things the Linux way.  Where I'm coming from here is just trying to understand and get info on
the operating system and linking.

---

### Post by leg on 2007-04-23
Linux has the concept of both static and dynamic linking. Static libs end with .a and dynamic ones end with .so. Kernel stuff ends with .ko. Look through /usr/lib, /usr/share/lib There are a few libs for GUIs gtk+ is the only one I can remember at the moment. I will search for some links I have and post them for you I am at work at the moment.

Leon.

[edit]
heres a couple
[ - Writing Gnome Apps]("http://developer.gnome.org/doc/books/WGA/")
[ - Art of Unix]("http://www.catb.org/%7Eesr/writings/taoup/html/")  - Not sure how good that will be but it should be ok
[ - pdf about dev platform]("http://www.informit.com/content/downloads/perens/0130091154.pdf")

---

### Post by simonn on 2007-04-23
Windows has the GUI as part of the kernel. Linux has no such thing.

There are essentially two main GUI toolkits used by the vast majority of Linux distributions, GTK and QT. Gnome (e.g. Ubuntu), XFCE (e.g. Xubuntu) and many other windows/session managers are based on GTK. KDE is based on QT.

GTK is written in C but has bindings for many other langauages. It is quite cross platform, but it looks, well... GTK-like (weird, to some) on windows and OSX. Arguably, it fits in better than QT with the open source thing by being entirely GPLed.

QT is written in C++. Not sure about the available bindings. It is very cross platform and is developed by a commercial company called Trolltech. It is dual (multi?) licensed so commercial companies can pay a licensing fee so they do not have to release there code as open source. As a result a lot of closed source linux applications use this toolkit, e.g. skype, google earth, opera etc. They also license it under the GPL for developers who release there work as open source.

wxWidgets is slightly different as it uses other toolkits or controls native to the OS to create it's widgets e.g.  a wxWidgets application could be compiled against GTK using wxGTK for a GTK based environment or link to wxWindows to compile the same code on windows. It is basically a layer above existing toolkits.

All the above contain other code to deal with things like linked lists, arrays, hash tables, Unicode etc etc as well as just GUI code.

Personally, I would start with GTK, partly because C is my native language, but mainly because it is very OSS. Oh, and I am not that interested in writing software for platforms other than linux.

---

### Post by j_g on 2007-04-23
> In Windows I do Win32 SDK style Api coding.

You sound just like me. I make lots of Win32 DLLs, and code them entirely in C going straight to the Win32 API. I don't even use the C library. (On Linux, bypassing the C library is impractical when writing C code. But that doesn't matter much. The C library on Linux comes in "DLL form" and is almost guaranteed to already be loaded on any running Linux system).

So, I know _exactly_ where you're coming from, and therefore, can give you very pertinent advice.

Yes, Linux does support "shared libraries" (ie, DLLs in Windows parlance). When compiling a DLL with gcc, you must specify the -fPIC option. And when linking, use the -shared option. For more info on making a shared lib under Linux, go to google and do a search on "Linux shared libraries".

One point that is often overlooked in Linux lib tutorials: You can define a function to be called by the OS when a Linux shared lib is loaded. This is akin to having a DllMain in a Win32 DLL, handling the DLL_PROCESS_ATTACH. Define your function as so:

```
static void MyInit() __attribute__((__constructor__));
static void MyInit()
{
   /* Put your initialization code here */
}
```

One caveat is that, unlike the Win32 DLL_PROCESS_ATTACH, the Linux initialization function has no return failure code. So if you do something that fails, you'll have to figure out another way of letting your host app know about the failure.

You can also define a function to be called when the DLL is unloaded. This is akin to handliing DLL_PROCESS_DETACH in your Win32 DLL. Define it as so:

```
static void MyEnd() __attribute__((__destructor__));
static void MyEnd()
{
   /* Put your cleanup code here */
}
```

Another caveat: When a Win32 app crashes, Windows goes through all of the loaded DLLs in that process, calling the DllMain's DLL_PROCESS_DETACH. So a Win32 DLL can free any resources there, even in the event of failure. Linux doesn't call a DLL's cleanup function on a process crash, so it can''t cleanup its resources. (Sigh. In many ways, Linux is not as fully featured as Win32. But I guess that's to be expected with a free OS).

For "dynamic linking", your host app loads/opens your shared lib with a call to the dlopen() function. This is akin to Win32's LoadLibrary(). You gain access to a particular function with dlsym() which is akin to Win32's GetProcAddress(). And you unload the lib with dlclose() which is akin to Win32's FreeLibrary().





As far as a GUI, forget about wxWidgets. It's a cross-platform thing. You don't need, and obviously don't want, that. As someone mentioned, the two main GUI toolkits used on Linux today are QT and GTK+. The former would require you to use C++. If you're using C (as I do), go with the latter.

Both toolkits come in the form of numerous shared libs (DLLs). If you're running Ubuntu, then you've got the Gnome desktop. This desktop uses GTK+ so those shared libs are mostly already loaded by virtue of the desktop coming up. If you're using Kubuntu, then you're using the KDE desktop. This desktop uses QT so the QT shared libs are mostly already loaded by the desktop. This doesn't mean that you can't run an app using QT under the Gnome desktop, nor can't run an app using GTK+ under the KDE desktop. It just means that, if you run an app using GTK+ under the QT desktop, for example, then those GTK+ shared libs will have to be loaded. So to minimize memory usage, you may want to choose the same toolkit that your desktop is already using.

Now ultimately both toolkits do ride on top of the X Windows system. So yes, you could instead choose to code directly to the X Windows API. The X API itself doesn't have any "controls" (widgets in Linux parlance) such as buttons, sliders, list boxes, etc. But, there is a low level toolkit called Xt (Intrinsics) which has a basic set of widgets. Frankly, this toolkit is exceedingly ugly. There is also the Motif toolkit which is an alternative low level toolkit that tries to improve the looks. But again, I find it to be exceedingly ugly. And neither of these toolkits offer you some of the more advanced widgets you'll find in GTK+ or QT. Plus as I mentioned, if using the Gnome or KDE desktops, then you already have lots of GTK+ or KDE shared libs loaded. So you save nothing by using Xt or Motif (and indeed, those extra toolkit libs have to be loaded now).

It sounds like my own approach toward programming is very, very similiar to yours. What I found to be best was:

1) Use GTK+ for my GUI, since I run the Gnome desktop, and also program in C.
2) Create Linux shared libraries, much like I do on Win32, to share code between apps. The only difference is that my Linux libs do not bypass the C API.
3) Eschew the Linux IDEs since they all use the GNU autotools, which produce human unreadable make files, and the IDEs are not well-integrated with those make files. Therefore, Linux IDEs suck. I use Gedit with the "make" plugin, and write my own make files by hand.

---

### Post by Frederick J. Harris on 2007-04-23
Thanks for the info Leon, and Simonn.  The Gnome book by Sheets looks interesting.  I immediately saw some
stuff in it explaining  'autoconf', a word I've come across that I didn't know what it was about.  By the way,
how many K would the smallest possible Graphical User Interface program be in Linux that created a Window/Dialog/Form, that is, a 'Hello, World!" program?  I guess the answer to that question depends on the toolkits/libraries used, but a range would give me some idea.  Also, would anyone know what packages,
if any, I need to install to get started trying to figure out XLib.  I've found some beginning tutorials on the
internet about it and they all start with 

#include <X11/Xlib.h>

I've found numerous X11 directories on my new Ubuntu installation, but no Xlib.h.  My gcc and g++ compilers are working though.  And I guess I'd better study up on GTK too.

---

### Post by psusi on 2007-04-23
On both Linux and windows, you can choose to link to libraries either statically or dynamically.  If you don't want a large executable, then link to the mfc dll instead of the static library.  On Linux link to the shared library ( libfoo.so ).

---

### Post by harun on 2007-04-23
> **Frederick J. Harris said:**
> I immediately saw some stuff in it explaining  'autoconf', a word I've come across that I didn't know what it was about.

[http://sources.redhat.com/autobook/](http://sources.redhat.com/autobook/)

You know what make is, basically the autotool's automate the creation of make files which help you down the road with a growing application and one you want to be portable. I didn't understand what was meant by the term either until I found the above link and worked through their examples. Not bad and you will understand how those tools work and how to use them when you are done.

Enjoy.

---

### Post by Frederick J. Harris on 2007-04-23
So, what I'm coming to understand is that Linux uses 'shared' libraries too!  And at the bottom  is X Lib, on top of that is GTK.  And on top of both is Gnome?  Yes, I have a standard Ubuntu 6.1 installation with Gnome.  Well, these libraries will be in memory then if the OS is loaded.  So, theoretically, the exes could be small if they can dynamically link with shared (in memory)  files.  I'm getting way ahead of myself here.  It was only the Sunday before last I installed Ubuntu, and only middle or late last week I got my compilers working.  I was planning to try to be happy with console programs for awhile, but then I got interested in researching this GUI thing, and here I am.

Like I said in my first post I've ordered a couple XLib books, plus with all the online material I'll hopefully figure it all out.  I like to start with the very basics of things though, so that's why I immediately gravitated to the XLib stuff. 

Thanks for the excellent info J_G.  I mostly do C too.  Probably the biggest reason I never got into C++ that much is that I never liked any of the class libraries that much even though, in the abstract, I do like C++).  Lately I've been putting my own class library together so that I might get into C++ a bit more.  I use C mostly for eMbedded programming with Win CE.  For Windows desktop programs I'm more apt to use Bob Zale's PowerBASIC compiler. Below is a Win32 PowerBASIC program that compiles down to 11776 bytes.  It creates a main window with a button and a textbox on it.  When you click the button a line of text is put in the textbox.  So it is just a 'hair' more than a Hello, World!.  Bye the way, that company is working on a Linux version of their compiler.

```

#Compile Exe               //11776 bytes
#Include "Win32api.inc"
%IDC_BUTTON    =   1250
%IDC_EDIT      =   1275
'
Type WndEventArgs
  wParam As Long
  lParam As Long
  hWnd   As Dword
  hInst  As Dword
End Type
'
'
Sub WndProc_OnCommand_OnButton_Click(Wea As WndEventArgs)
  Local szString As Asciiz*48
  szString="Here Is Some Text To Go In A Textbox!"
  SetWindowText(GetDlgItem(Wea.hWnd,%IDC_EDIT),szString)
End Sub
'
'
Function WndProc_OnCreate(Wea As WndEventArgs) As Long
  Local pCreateStruct As CREATESTRUCT Ptr
  Local hWnd As Dword
  '
  pCreateStruct=Wea.lParam
  Wea.hInst=@pCreateStruct.hInstance
  hWnd=CreateWindow("button","Button",%WS_CHILD Or %WS_VISIBLE,90,20,100,25,Wea.hWnd,%IDC_BUTTON,Wea.hInst,0)
  hWnd=CreateWindow("edit","",%WS_CHILD Or %WS_VISIBLE Or %WS_BORDER,10,70,265,25,Wea.hWnd,%IDC_EDIT,Wea.hInst,0)
  '
  WndProc_OnCreate=0
End Function
'
'
Function WndProc_OnCommand(Wea As WndEventArgs) As Long
  Select Case LoWrd(Wea.wParam)
    Case %IDC_BUTTON
      Call WndProc_OnCommand_OnButton_Click(Wea)
  End Select
  WndProc_OnCommand=0
End Function
'
'
Function WndProc_OnDestroy(Wea As WndEventArgs) As Long
  Call PostQuitMessage(0)
  WndProc_OnDestroy=0
End Function
'
'
Function WndProc(Byval hWnd As Long,Byval wMsg As Long,Byval wParam As Long,Byval lParam As Long) As Long
  Static szString As Asciiz*28
  Static Wea As WndEventArgs
  '
  Select Case As Long wMsg
    Case %WM_CREATE
      Wea.wParam=wParam : Wea.lParam=lParam : Wea.hWnd=hWnd
      WndProc=WndProc_OnCreate(Wea)
      Exit Function
    Case %WM_COMMAND
      Wea.wParam=wParam : Wea.lParam=lParam : Wea.hWnd=hWnd
      WndProc=WndProc_OnCommand(Wea)
      Exit Function
    Case %WM_DESTROY
      Wea.wParam=wParam : Wea.lParam=lParam : Wea.hWnd=hWnd
      WndProc=WndProc_OnDestroy(Wea)
      Exit Function
  End Select
  '
  WndProc=DefWindowProc(hWnd,wMsg,wParam,lParam)
End Function
'
'
Function Winmain(Byval hIns As Long, Byval hPrev As Long, Byval lpCL As Asciiz Ptr, Byval iShow As Long) As Long
  Local szAppName As Asciiz*16
  Local hWnd As Dword
  Local wc As WndClAssEx
  Local Msg As tagMsg
  '
  szAppName="Form1"
  wc.cbSize=Sizeof(wc)
  wc.style=%CS_HREDRAW Or %CS_VREDRAW
  wc.lpfnWndProc=Codeptr(WndProc)
  wc.cbClsExtra=0
  wc.cbWndExtra=0
  wc.hInstance=hIns
  wc.hIcon=LoadIcon(%NULL,Byval %IDI_APPLICATION)
  wc.hCursor=LoadCursor(%NULL, Byval %IDC_ARROW)
  wc.hbrBackground=GetStockObject(%LTGRAY_BRUSH)
  wc.lpszMenuName=%NULL
  wc.lpszClAssName=Varptr(szAppName)
  wc.hIconSm=LoadIcon(hIns, Byval %IDI_APPLICATION)
  Call RegisterClAssEx(wc)
  hWnd=CreateWindow(szAppName,"Form1",%WS_OVERLAPPEDWINDOW,200,100,295,175,0,0,hIns,Byval 0)
  Call ShowWindow(hMainWnd,iShow)
  While GetMessage(Msg,%NULL,0,0)
    TranslateMessage Msg
    DispatchMessage Msg
  Wend
  '
  Function=msg.wParam
End Function

```

---

### Post by j_g on 2007-04-23
I did the _same thing_ you're doing. I figured "Let me start with writing a simple X Window app, because that should be easiest". Actually, it wasn't. For example, none of the tutorials I perused showed how to capture the "close window event" from the window manager. The net result was that my X window disappeared from the screen but my app was still left running in the background. I eventually found how to do it, but in the process of searching for such info, I discovered that there is a dirth of uptodate X Windows tutorials/documentation and examples available. Most links you click on lead to 404 missing pages. For this reason, X windows programming is inevitably not easier than choosing a toolkit that is much more widely used today.

I recommend that you skip X Windows and just jump right into GTK+.

Furthermore, do not forget about the Glade3 GUI builder for GTK+. You know how MSVC has a built in "resource editor" that lets you create a window with controls, just by dragging and dropping controls where you want on the window, resizing/spacing them with the mouse, and setting "properties" for the controls? And you also have a menu editor to create your menus? Well, GTK+ has such a GUI builder too. It's called Glade3.

On Windows, the GUI builder spits out an .RC file which you feed to the linker. The resources then get compiled and linked into your EXE. With Glade, it outputs an XML (text file). You keep this XML file separate, but ship it with your executable. Your executable then calls a function named glade_xml_new() (in another Gnome shared lib called libglade), passing the name of that XML file. libglade then reads your XML file and creates your window with all its controls and menu. It's akin to calling Win32 CreateDialog (or DialogBox), passing the resource ID of the dialog to load. A single XML file can contain the definitions of numerous windows (and their controls).

So designing your GTK+ GUI using Glade, and loading it with libglade is very easy -- much easier than X windows (Xlib and Xt). There is no such equivalent for Xt or Motif toolkits. You have to manually create each window, and each control in it, and build up menus, just like you would in Win32 by calling CreateWindow to create each control, and CreateMenu etc. Mind you, you can still do the same thing with GTK+ if desired, but you have the option of Glade/libglade too.

---

### Post by wmcbrine on 2007-04-23
> **Frederick J. Harris said:**
> So, what I'm coming to understand is that Linux uses 'shared' libraries too!  And at the bottom  is X Lib, on top of that is GTK.  And on top of both is Gnome?Almost. XLib is nowhere near the bottom, although I guess you could call it the bottom of the GUI, from a programmer's perspective. Below that is the POSIX layer, and below that is the kernel.

If you haven't yet found Xlib.h, you need to install the xorg-dev package.

---

### Post by Mirrorball on 2007-04-24
Programming directly with xlib was really hard for me too and there is almost no documentation beyond the official specifications. I quit and decided to go with glut (because all I needed was a window, no "widgets").

---

### Post by Frederick J. Harris on 2007-04-24
I see now where you are coming from J_G.  I need to back up and follow my original plan of working my way
into this slow.  I have too many unresolved issues I'll need to address before I can jump right into GUI toolkits.  For example, I havn't even resolved my internet connectivity issue with Ubuntu yet, and downloading and installing the build-essential package by hand with dpkg took me something like two days.  I see the xorg-dev package looks even worse, and I'm just not prepared to spend days if not weeks trying to manually put together a build system that works before I can even concentrate on what I want to do which is code.  Thanks everyone for the help.

---

### Post by Jmccaffrey on 2007-04-24
> **Frederick J. Harris said:**
> I see now where you are coming from J_G.  I need to back up and follow my original plan of working my way
into this slow.  I have too many unresolved issues I'll need to address before I can jump right into GUI toolkits.  For example, I havn't even resolved my internet connectivity issue with Ubuntu yet, and downloading and installing the build-essential package by hand with dpkg took me something like two days.  I see the xorg-dev package looks even worse, and I'm just not prepared to spend days if not weeks trying to manually put together a build system that works before I can even concentrate on what I want to do which is code.  Thanks everyone for the help.

It is alot easier just to purchase a 30$ network card that works than trying to deal with questionably supported network hardware.  Just a heads up on that.

---

