---
title: "What is HANDLE mean in windows programming?"
date: 2007-11-15
forum: Programming Talk
---

### Post by amazingjxq on 2007-11-15
I'm confused. It seems that most type in windows API contains H.
HINSTANCE,HDC.
I just don't know what type are they.

---

### Post by CptPicard on 2007-11-15
I'm not much of a Windows programmer, but IIRC a "handle" in Windows is essentially just some identifier for a resource... and the type is probably just an integer.

For example, consider the idea that you have multiple windows on your screen... each of them is identified by a "handle" which is essentially just a system "name" for the window... and could, at simplest, be just a running number id...

---

### Post by j_g on 2007-11-16
A handle is most definitely not an int on Windows. Windows doesn't use signed (ie, int) values for handles. A handle on a 64-bit version of Windows will be a 64-bit unsigned value, whereas upon 32-bit versions, it will be 32-bits unsigned. As far as an app is concerned, a Win32 handle is just a void *.

In a nutshell, a Win32 handle is (typically) a pointer to a struct that Windows doesn't want you to directly manipulate. It's a struct that is meant to be passed to, and manipulated by, only operating system functions. For example, you call CreateWindow() and it returns a handle to a window. Your app refers to it as an **HWND**, which is typedef'ed to a **void *** in Windows.h for the benefit of apps. A pointer to what? You don't know. Only the Windows operating system knows. It's a "window struct". What's that? You don't know. What members are in this struct? You don't know. Only the operating system knows. What do you do with this handle? You don't do anything at all with it, except to pass it to a great many other operating system functions that require you to pass it, definitely know what it really is, what its members are, and directly read/write those members.

What's the point of this? First of all, the operating system needs to allocate some sort of "window struct" (ie, memory area) to store your own app's settings. After all, you've got your own window, distinct from any other app's windows. Your own window has its own distinct width and height, and title bar text, and lots of other settings that are unique to your own window. There has to be somewhere to store these personal "window settings" of yours. So the windows operating system allocates this "window struct" to store your own window settings. Then, the operating system (ie, CreateWindow) returns a pointer to this struct. It's telling you *"Save this pointer to something. Don't you dare directly access its contents. I'm not going to even tell you what is in this struct. Just save this pointer somewhere. Then when you call some other OS function, such as SetWindowText to change your window's title bar text, pass this pointer to SetWindowText, and I, the operating system, can know which window we're talking about, and I can change whatever member stores the title bar text of your window".*

The other point of this is that: If in a future version of Windows, Microsoft decides they need to change the layout of this "window struct", it won't break older apps. After all, your program _never_ actually touches the members of this struct. So what do you care if, tomorrow someone runs your app on a new version of Windows that redefines the contents of that window struct. You never touch its contents. All you do is pass it around to different OS functions. What concern is it of yours that now, every single OS function you pass this pointer to, is operating upon a slightly different "window struct" than those functions were yesterday?

An HINSTANCE is really a pointer to an "instance struct". What are its members? Only Microsoft knows. All we know is that it has something to do with storing settings about your EXE. An HWND is really a pointer to a "window struct". Only MS knows what it really is. All we know is that it's something to do with storing settings about a particular window. An HFONT is a pointer to a "font struct". Only MS knows what it really is. All we know is that it's something to do with storing settings about a particular font. Etc.

As far as you're concerned, they are all a void *. Hell, you could typedef HSOMETHING to be a void *, and call them all an HSOMETHING. So why didn't MS do that, instead of having hundreds of these H...whatevers? Because then you'd really get confused. You don't want to mistakenly pass that "font struct" (HFONT) to SetWindowText (in lieu of a pointer to a "window struct"). And you don't want to mistakenly pass a HWND to GetModuleFilename() (in lieu of passing a pointer to an "instance struct"). So think of all these H...whatever as MS's way of helping you distinguish these various pointers, without giving you any more information about them than you need -- specifically, not any information about the actual content of these structs.

Got it?

---

### Post by aks44 on 2007-11-16
j_g's post explains it quite well.

I'll just add that for many (most? all?) handle types the OS maintains some kind of "repository" so that when you pass a handle to an API it can verify whether this handle actually exists before using it.

Also, some (many?) handle types are indeed just indexes into a kernel map (handle => struct), even though they are typedef'ed to void*. HFILE immediately comes to mind.

---

