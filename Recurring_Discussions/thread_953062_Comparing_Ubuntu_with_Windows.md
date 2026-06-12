---
title: "Comparing Ubuntu with Windows"
date: 2008-10-19
forum: Recurring Discussions
---

### Post by poldie on 2008-10-19
I was just wondering if there was a resource/site which detailed the difference between, say, Ubuntu and XP in terms of the registry, COM objects, ini files, tasks/processes etc so that I could quickly see the major differences between windows and linux development.  I can google for stuff individually but I was hoping there'd be some recommended primer for developers.

---

### Post by Soupcan on 2008-10-19
What I know:
Ubuntu does not have a registry.

---

### Post by bodhi.zazen on 2008-10-19
Moved to recurring discussions. There are tons and tons of things on these forums and elsewhere discussing these issues, most of them opinions.

If you wish start with the on line help or the wiki :

[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by Delever on 2008-10-20
> **poldie said:**
> I was just wondering if there was a resource/site which detailed the difference between, say, Ubuntu and XP in terms of the registry, COM objects, ini files, tasks/processes etc so that I could quickly see the major differences between windows and linux development.  I can google for stuff individually but I was hoping there'd be some recommended primer for developers.

registry:

Configuration files.

COM:

Thanks God no such thing.

ini files:

They don't need to end with "ini".

Now, it depends on what is your programming language and what are you going to port. Quick list of what I know (just some pointers):

Application-specific configuration is usually in /etc.
User-specific configuration is in /home/user directory.

If you are porting C# application to mono, Windows.Forms can be used, but it looks ugly. However, there is GTK+ wrapper you can use. Also, no calls to windows native libraries.

If you are porting C++ code, you will need to isolate windows-specific stuff: access to any windows API, including forms, threads, registry, sockets. Good news! There are libraries to use just for that, like boost, pthreads for windows, GTK+, and more. You may want/need to learn GNU automake for compiling. Eclipse is one of IDE's.

If you are porting Java code... Obviosly it should have no calls to native libraries, and you can reuse same interface without much hassle.

Then there are such obvious things like file paths "/" vs "\", no drive letters, not DirectX but OpenGL.

This reply should give you some keywords to use in google.

---

