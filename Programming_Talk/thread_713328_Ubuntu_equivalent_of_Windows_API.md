---
title: "Ubuntu equivalent of Windows API"
date: 2008-03-02
forum: Programming Talk
---

### Post by Neon612 on 2008-03-02
I've been using Visual Basic in Windows for a while now, and been experimenting with the API calls and such. I"d like to know what their equivalent is in Ubuntu is?

And also what programming languages will be good to use them in.

---

### Post by CptPicard on 2008-03-02
If you want to use Windows, use Windows.

If you use Linux, use Linux and learn the API of the language/platform you choose to program on Linux in. There is no "VB equivalent".

If I were you, I'd probably look into Python. It's cross-platform too, can be used on Windows as well.

---

### Post by Neon612 on 2008-03-02
The API calls are for the Windoze system itself, not just the programming language you choose.

Is there something like that for Ubuntu?

---

### Post by CptPicard on 2008-03-02
I really wouldn't even want to answer this, but WINE provides a Windows API layer for Linux. No, you don't want to code for that.

Python has its own standard library, a lot of which is built on top of the C standard library and various other libraries. Those, in turn at the deepest level, call kernel system calls, which you can familiarize yourself with if you're so inclined.

---

### Post by Neon612 on 2008-03-02
Okay Python sounds like a good starting pad.

From VB I'm used to the GUI aspect (no command line) is there a Python app out that is similar to VB with the graphic Interface?

---

### Post by CptPicard on 2008-03-02
If you're going to write GTK apps, look at Glade. I've got no personal experience of it though. QT Designer for KDE.

---

### Post by pmasiar on 2008-03-02
Look at sticky FAQ. If there is not enough info, ask more direct questions, and consider inproving FAQ. Good luck!

---

### Post by Fbot1 on 2008-03-02
Posix?

---

### Post by slavik on 2008-03-02
The kernel API. You can start with this: [http://www.amazon.com/Understanding-UNIX-LINUX-Programming-Practice/dp/0130083968/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1204506657&sr=8-1](http://www.amazon.com/Understanding-UNIX-LINUX-Programming-Practice/dp/0130083968/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1204506657&sr=8-1)

EDIT: POSIX is a standard (part of it is API). Don't expect all Unix/Linux systems to be fully compliant. :)

---

### Post by a9bejo on 2008-03-02
> **Neon612 said:**
> The API calls are for the Windoze system itself, not just the programming language you choose.

Is there something like that for Ubuntu?

Yes, many of them.  The Win32 API is Microsofts way of offering developers access to windows functionality.  Since Ubuntu/GNU/Linux is an open project, there is no reason to restrict developers in such a way:  You have access to the APIs of every module and different toolkits that are on the system.  For example, you might want to search for 'GTK' or 'QT' to find two huge Toolkits that provide APIs for GUI development and much more.  But keep in mind that on Linux,  you can do many things that would require an API call in Windows with simple File IO.

---

### Post by jay019 on 2008-03-04
You could use java and the Desktop API. For example, an app I wrote checks for Desktop support and then checks for support for opening/printing of files. In linux it allows me to open the file, while in windows it will print the file.

I guess what would help is an idea of what kind off program you are wanting to write and then someone may be able to suggest a few ways to go about creating it.

---

