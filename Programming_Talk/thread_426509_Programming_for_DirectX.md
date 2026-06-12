---
title: "Programming for DirectX"
date: 2007-04-28
forum: Programming Talk
---

### Post by M$LOL on 2007-04-28
I'm starting to learn how to program for both OpenGL and DirectX, and I was wondering if I can program for DirectX without using Visual C++ (and any other Microsoft programming util is out of the question, since I know C++ better than any of the others). I would like to use GCC for it, but I don't know if that's possible, considering the headers and libraries it would need. I really don't mind what I use, but I would prefer if I cold use something non-Microsoft. Is that possible?

---

### Post by Tomosaur on 2007-04-28
I don't have any direct experience of DirectX myself, but I don't see any reason why GCC wouldn't be able to handle it. As long as you have the libraries / header files, you should just be able to use them as you would in any other project.

---

### Post by samjh on 2007-04-28
I think DirectX uses some VC++ extensions, so GCC won't do unless you do a whole lot of work to find ways around problems.

---

### Post by JT673 on 2007-04-28
I remember DirectX uses COM, IDL, and .dlls (though I may be mixing up some stuff), so I don't think that's possible.  My advice would be to stick with OpenGL, because it's easier and cross-platform.  You can install wine or dual-boot, though.

But I think VC++ isn't needed for DirectX, although I haven't touched DirectX in a year or so.

---

### Post by j_g on 2007-04-29
Yes, you can use DirectX with any C++ compiler. In fact, since DirectX is COM-based, you can even use it from C with any modern C compiler. (I wrote a series of articles about using COM in plain C on [www.codeproject.com](www.codeproject.com). I didn't discuss DirectX in particular, but the information is relevant to any COM-based tech. The examples in those articles use MSVC only because that compiler/linker is, for example, smart enough to automatically find any MS SDKs installed on the system. With a bit more fuss, it would be possible to adapt to gcc. But most programmers don't like having to wrestle with the compiler/linker).

The reason why so many DirectX examples use ATL (ActiveX template library), MFC (Microsoft foundation classes), or WTL (Windows template library) is because these frameworks have lots of boilerplate code for COM. Without these frameworks, you have to do more work on your own, for example, initializing COM by calling ComInitialize(), and coding the Invoke(), and other functions, for any IDispatch objects you create. It's not especially hard to do yourself in C++ (if you know what you're doing), but since a lot of the MS frameworks have lots of boilerplate code to set things up for you, most people seem to use those frameworks. There aren't many examples of doing COM in plain C++, especially without MSVC, but that's not because it can't be done. It's just that it can be more difficult, so people tend to go with the easier, better supported solutions. Check out [http://ript.net/~spec/captcom/journal2](http://ript.net/~spec/captcom/journal2) for a C++ example of writing your own COM objects, in C++, without any framework. Check out my codeproject articles by Jeff Glatt, for plain C, without any frameworks.

An .IDL file is simply a text file that is compiled into a .TLB binary. That TLB binary lets COM know about the functions in any COM objects you make -- the parameters passed to them, and the return value types. You won't need to be involved with IDL/TLB files unless you're:

A). Making your own COM objects.
B). You want your objects to be accessible from a script language, such as VB, python, C#, etc.

(Note that some COM technologies do require you to create your own COM objects, including IDispatch derived objects. For example, if you want to use ActiveX Script engines, such as VbScript or JScript, the engine will require you to create specific COM objects as defined in MS header files).

An IDL file is "compiled" into a TLB file using Microsoft's MIDL.EXE utility. If you need that, you can get it freely when you download the Windows Platform Software Development Kit (Platform SDK). It's found in the Bin directory. And the SDK also has all the C++/C header files you need for COM development (although for DirectX specifically, you'll also need the DirectX SDK). One of the advantages of using Microsoft tools such as Visual Studio, is that it easily finds these installed SDKs on your system. With GCC, you have to tell it where they are. Again, things like this are why people use MS tools instead of lowest-common-denominator ported software.

You don't need to deal with making a DLL unless, again, you're making your own COM object that you intend to be used by numerous other, third party entities. For example, the DirectX components are all in DLLs so that all of us can use those Microsoft DirectX objects. But merely using those objects doesn't mean that you have to make a DLL. You'll probably be making an EXE (and it can contain any COM objects that DirectX requires you to create/supply).

This is not a good forum to get information about Windows programming. This is a Linux forum, Ubuntu specifically. The info you get here about Windows stuff will likely be inaccurate and misleading. I recommend Code Project for Windows programming.

---

### Post by Tomosaur on 2007-04-29
> **j_g said:**
> 
This is not a good forum to get information about Windows programming. This is a Linux forum, Ubuntu specifically. The info you get here about Windows stuff will likely be inaccurate and misleading. I recommend Code Project for Windows programming.

Please don't write things like this, it just encourages people to get off topic. **Your** post was helpful, so why wouldn't others be? There are plenty of people here who program for both Windows and Linux - it is a generic programming forum, not just for Linux programmers.

---

### Post by M$LOL on 2007-04-29
> **j_g said:**
> 
This is not a good forum to get information about Windows programming. This is a Linux forum, Ubuntu specifically. The info you get here about Windows stuff will likely be inaccurate and misleading. I recommend Code Project for Windows programming.

I asked here because I know that there are some very good programmers here (by the sounds of it you're one of them) and I was looking for a way to program DX without Visual C++. Since I know how to use GCC to program for Linux, I wanted to use that instead of Visual C++ for DirectX, even though it's for Windows.

Anyway, thanks very much, your post explains a lot. How should I go about doing this? From the couple of tutorials I've seen, it seems I need windows.h and d3d8.h. Where do I get them?

---

### Post by j_g on 2007-04-29
> Please don't write things like this

I consider ALL of what I said to be very helpful advice, including the recommendation to defer Windows questions to other web sites. As an experienced Windows programmer, I have found the advice given on this forum to be mostly inaccurate and misleading -- much, much moreso than on sites such as CodeProject. It doesn't matter what you presume is the intent of this web site. The bottom line is the quality of the information, and it is very lacking here (and downright unhelpful, frankly). If I hadn't even posted a response to this person, he would have gotten some _wrong_ information about programming DirectX. And as a person who gave detailed, accurate information (not supposition) to him, it is definitely my right to also recommend to him where to get the most accurate info about Windows programming. On CodeProject, my response to his question would have been the rule, rather than the exception.

> Your post was helpful, so why wouldn't others be?

Because the other advice would have convinced him that he couldn't use DirectX with gcc, probably had to use Microsoft's compiler, and in general gave him pure suppositions (ie, "I think you need to do this, or get this, but I don't know where you get it and how you do it"). That isn't helpful because it doesn't offer the OP anything beyond his own suppositions about his problem, and therefore, offers him no progress whatsoever in solving his problem.

The bottom line is, if you didn't _know_ the answers to his questions, Tom, you should have refrained from answering, and instead directed him to a better source of information. That is the _responsible_ thing to do. This is the sort of thing that people do on CodeProject, but unfortunately do not do here. There is a big problem here in that certain people seem to insist upon answering every question with inaccurate suppositions, instead of simply redirecting people to better sources. So here I reiterate your advice to me: Please don't do that.

> There are plenty of people here who program for both Windows and Linux

That's irrelevant. The bottom line is the quality of the responses to questions about Windows programming. When most of the responses are pure suppositions and inaccuracies, that's bad. And frankly, I have personally found this to be the rule here in regard to Windows programming.

---

### Post by j_g on 2007-04-29
> I asked here because I know that there are some very good programmers here

Well, I'm just telling you that, as an experienced Windows programmer, I have found the Windows programming advice on this forum to be rife with pure supposition and inaccuracies. It's your choice whether you want to use this as a forum to get Windows advice, but I advise against it (because there are way, way too many people who don't _know_ the answers to such questions responding here, and they are really, really adamant about doing this to the point of being totally irresponsible about it). There are better forums for this.

> I was looking for a way to program DX without Visual C++.

And you can do that. I _know_ this to be true. This is not a supposition. The reason why even some examples that do not use any MS frameworks (ie, ATL, MFC, WTL) nevertheless have make files for MSVC (such as the examples I wrote for my CodeProject tutorials) is because MSVC is a smart Windows compiler that knows how to automatically find any additional MS SDKs you install. So it's a good compiler to use for Windows programming, and suitable for use in a tutorial.

> How should I go about doing this?

Using GCC with DirectX? Well, you may, or may not, find any existing examples. Do a google search and see what you come up with. But armed with the info I've given you here, and some generic examples that don't use any MS frameworks, you should be well on your way to doing this on your own.

> it seems I need windows.h and d3d8.h. Where do I get them?

Windows.h is one of the include files that gets installed when you install the Microsoft "Platform Software Development Kit" (Platform SDK). You'll find that, and all of the other standard Windows headers, in the "Include" directory where you install the SDK. For example, if you install the SDK in the directory "C:/Program Files/Microsoft Platform SDK" (the default location), then you'll find Windows.h in  "C:/Program Files/Microsoft Platform SDK/Include". You'll find useful utilities such as the aforementioned MIDL.EXE, GuidGen.exe (a utility to generate unique GUIDs), etc, in the "Bin" directory. You'll find the libs you specify to the linker in the "Lib" directory.

You must download the freely available "Microsoft Platform SDK" from MS' web site, and install it on your computer.

[http://www.microsoft.com/downloads/details.aspx?FamilyID=c2b1e300-f358-4523-b479-f53d234cdccf&DisplayLang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=c2b1e300-f358-4523-b479-f53d234cdccf&DisplayLang=en)

The above is the Vista Platform SDK which contains all the latest versions of the standard Win32 headers, and linker libs. Use it for Win2000, XP, Vista.

If you're using a MS compiler, no problem. It will find wherever you've installed the SDK. (ie, The compiler will find the Include dir, and the linker will find the Lib dir). If you're using GCC, you'll need to tell the compiler where to find the Include dir, and the linker where to find the Lib dir.

For DirectX programming, you'll also need to install the DirectX SDK. That's where you'll find headers such as d3d8.h, and the DirectX libs you supply to the linker. Again, a MS compiler will know where to find the Include and Lib dirs for this SDK too. But again, with GCC, you'll have to tell its compiler/linker.

[http://www.microsoft.com/downloads/details.aspx?FamilyID=86cf7fa2-e953-475c-abde-f016e4f7b61a&DisplayLang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=86cf7fa2-e953-475c-abde-f016e4f7b61a&DisplayLang=en)

P.S. The SDKs also contain the source to many examples. You'll want to check some of those out.

---

### Post by M$LOL on 2007-04-29
While I would love to have an ethics debate over good and bad advice, I would rather this thread stay on topic about DirectX and GCC. OK, I've already got [this ]("http://www.microsoft.com/downloads/details.aspx?FamilyID=9216652f-51e0-402e-b7b5-feb68d00f298&displaylang=en"), is that the same as the DirectX SDK you recommended? I'll download the Platform SDK tomorrow. Are there any libraries I need, or are the header files enough? Also, can I just copy windows.h to the dir my .cpp file is in and use #include "windows.h" ?

Thanks.

---

### Post by j_g on 2007-04-29
> is that the same as the DirectX SDK you recommend?

I'm not sure if that's a slightly older version of the DirectX SDK than the other link I gave, but it's DirectX 9.0 so it should suffice for your needs.

> Are there any libraries I need

The DirectX SDK contains the latest runtime DLLs for DirectX, so when you install the SDK, those are installed too. (But you can also get a package of _only_ the runtime DirectX DLLs, without any of the programming files. This is for people who want to install only the runtime without all the programming stuff like C compiler header files and linker libs). The SDK already contains everything.

The linker lib files, and include files, are also installed by the SDK (in the SDK's Lib and Include directories, as I explained above).

The Platform SDK covers most of the DLLs that are already part of any modern Windows system such as User32 and gdi32. It may also cover some DLLs that aren't part of older windows systems, such as WinInet, but you can find and freely download those newer runtime DLLs from MS' web site, if you need them. Suffice it to say that, if you have XP or Vista, you likely already have all the runtime DLLs you need for DirectX programming.

> are the header files enough?

No, you need both the header (.h) files for the compiler, as well as the linker lib (.LIB) files. But the SDK installs both the headers (in the "Include" directory) and libs (in the "Lib" directory).

An SDK contains everything you need for that SDK's component. (Ie, The DirectX SDK contains all the files for creating/running/debugging/testing DirectX. The Speech SDK contains all the files for creating/running/debugging/testing the Speech component. Etc.) The one exception is that most all windows programming, and therefore most other SDKs, require the Platform SDK to be installed. That contains all the basic Win32 API headers and linker libs.

> can I just copy windows.h to the dir my .cpp file is in and use #include "windows.h" ?

No. Windows.h references _many_ of the other .h files of the Platform SDK, which in turn reference other .h files. You'd have to copy over the entire Include directory. If you're using an MS IDE, it doesn't matter. These IDEs are all smart enough to automatically find where any MS SDK is installed. If you're using GCC, you have to tell its compiler where the .h files are (use the -I option) and its linker where the .lib files are (use the -l option). You'll have to do this for both the Platform, and the DirectX, SDK's Include and Lib directories.

---

### Post by jlebrech on 2007-04-30
Try Winelib directx programming. 

The advantage is portability, and if it runs smoothly on Linux you're sure it'll work at fullspeed on windows when you port.

Or try the Mono directx stuff, which I think is in beta or something.

---

