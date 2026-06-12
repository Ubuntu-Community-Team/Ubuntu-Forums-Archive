---
title: "Wanted:  help compiling a Windows program"
date: 2009-07-07
forum: Programming Talk
---

### Post by nonconventional on 2009-07-07
I have a windows program that is itself open source, but which links to a non-free DLL, so I understand there is no way to compile it to a native binary, but I'd like to at least compile it from ubuntu, but if that fails, I can use VirtualBox.
The problem? The author has disappeared from the face of the 'net, and there is no Makefile or equivalent. I've tried importing into and IDE but that requires a Makefile, and starting a new project and manually adding all the files didn't work either, even with what I thought were the correct library paths. I really have no clue where I'm supposed to start.
I've found references of other people **almost** getting it to build, but none of success, library errors were mentioned.

The source is available at [http://www.geocities.com/aprosenf/]("http://www.geocities.com/aprosenf/") (the yahoo email address has expired)
The external library is QuickTime. QuickTime greater than [version 7.1.6]("http://support.apple.com/downloads/QuickTime_7_1_6_for_Windows") failed in Wine.
The QuickTime development headers are available either through ADC or from Apple's FTP site.
Is anyone who knows what they're doing willing to point me in the right direction?

---

### Post by nonconventional on 2009-07-19
bump+update: (Note: this post is proof that trying to prove that you've done your best before asking for help on a forum may cause you to solve some of your problems yourself. I've left the original errors so that others can fix it too.)
well, I was experimenting on Windows (XP Pro) and noticed a couple of things that indicated my problems might be because I was using MinGW. So, I downloaded MS VC++ 2008 Express. I'm trying to build it from command line, since actually making it a project introduces another layer of confusion:
```

cl /EHsc /I"C:\Program Files\QuickTime SDK\CIncludes" *.cpp

```
and most of the files build to .obj without complaining. But I get one:
```

CRLEResource.cpp(346) : error C2440: 'type cast' : cannot convert from 'std::_Vector_iterator<_Ty,_Alloc>' to 'char *'
        with
        [
            _Ty=UCHAR,
            _Alloc=std::allocator<UCHAR>
        ]
        No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
CRLEResource.cpp(1401) : error C2440: 'initializing' : cannot convert from 'const char *' to 'char *'
        Conversion loses qualifiers

```
I got the second one to go away by adding the const to this line:
```

const char *pExtension = strrchr(szFilename, '.');

```
But the first one... Hmm, I found a grand total of 2 references on Google...
let's try
```

if(pInput >= (char *)&*m_vData1.end())

```
now that file compiles, but I have no idea why adding the &* changed anything.

So, now that this is done,
How do I link the .obj files into an .exe?
I added the main file name (EVNEW.cpp) in front of the wildcard so it knew what .exe to make (I don't think it appearing twice causes any issue, but if there were, all the filenames start with C... hmmm. maybe there was an issue...), and I got a screen full of errors, ending with:
```

EVNEW.exe : fatal error LNK1120: 98 unresolved externals

```
Then I notice the resources.rc file. This file looks important.
So I run rc resource.rc, and I get a missing header file warning: afxres.h
I find this file in the MinGW include directory, and copy it over. It looks pretty simple - basically, just include <windows.h> - so I figure this can't hurt.
now rc resources.rc works, and I follow that with cvtres to get an obj file like the rest.
I try to link the objs (at this point cl will just directly invoke link, so it shouldn't matter which I call)
link evnew.obj c*.obj resources.obj
and I still get 115 unsatisfied external link errors.
Do I have to specify the libraries? I tried adding /libpath:'s to cl after /link, for quicktime libraries and both of the promising windows library locations (C:\Program Files\Microsoft SDKs\Windows\v6.0A\Lib (did this come with it? I can't tell - but I don't think I've installed anything else on this machine...) and C:\Program Files\Microsoft Visual Studio 9.0\VC\lib), but none of that changed anything. Incidentally, it appears that the libpath thing doesn't like quoted spaces - it kept trying to open input file Files\Micrsoft.obj. So I used 8.3 names, and it tried. But still, 115 errors. See attached log.

So, can someone help me solve this link problem?

And for future, what's the best strategy to change to build with GNU tools, on Windows? Because I think there should be no problem converting from MinGW for windows to the MinGW cross-compiler for Linux...

Edit: I forgot to add the Utils.cpp file to the command line. This decreases the error count to 98. 
attachment updated
oh, and my the final commands I used to compile (all in one step):
```

rc resources.rc
cl  /EHsc /I"C:\Program Files\QuickTime SDK\CIncludes" EVNEW.cpp c*.cpp utils.cpp resources.res

```
with the special PATH from starting the "Visual Studio 2008 Command Prompt" from the Start Menu.

---

### Post by nonconventional on 2009-07-29
Well, I found out what my problem was, and it was simple: I didn't realize I had to specify the libraries, I thought the path was enough. So by Googling each of the specific error lines, I found I needed to add: advapi32.lib comctl32.lib comdlg32.lib gdi32.lib user32.lib qtmlClient.lib (at this point I was letting the IDE do the work - since I got it to give the identical error message - but they can just be appended after the /link)

---

