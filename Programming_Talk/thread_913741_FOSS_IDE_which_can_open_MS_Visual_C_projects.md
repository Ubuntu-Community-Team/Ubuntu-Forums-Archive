---
title: "FOSS IDE which can open MS Visual C projects?"
date: 2008-09-08
forum: Programming Talk
---

### Post by MaxIBoy on 2008-09-08
Some code I need to modify, is in an MS Visual C project and doesn't work when loaded into other IDEs. Is there a good IDE which can load MS Visual C projects? Failing that, is there a poor IDE which can convert MS Visual C projects into a format which is readable by a good IDE?

---

### Post by Caduceus on 2008-09-08
I've heard mono is a good FOSS program for the .NET framework, never used it personally so sorry if it's not what you're looking for.

---

### Post by LaRoza on 2008-09-08
> **MaxIBoy said:**
> Some code I need to modify, is in an MS Visual C project and doesn't work when loaded into other IDEs. Is there a good IDE which can load MS Visual C projects? Failing that, is there a poor IDE which can convert MS Visual C projects into a format which is readable by a good IDE?

How about a text editor?

The IDE used shouldn't be a hinderance in a standardised language. A "good" IDE is one that doesn't get in the way and gives control to the user, not one that compensates for the failings of another.

---

### Post by nvteighen on 2008-09-08
Does MS Visual C store code in project files or in regular .c (C) or .cpp (C++) files?

If the code is in .c or .cpp, a text editor is all you need, but if Visual C uses some specific proprietary MS format (like Visual Basic project files), then I fear no FOSS IDE will open them.

(I used MS Visual C 6 only once in my life and can't remember how it works)

---

### Post by DavidBell on 2008-09-08
I would have a look at the code::blocks, eclipse, netbeans & anjunta websites, I wouldn't be surprised if they have converters.

Since at least VS2002 both project and solution files are just xml, so you can just see what's needed in any text file editor.

One problem might be if the project based on MFC/ATL (/.NET?) because those libraries are under commercial licences. Also many compiler switches will be different (though depending on what you are doing, the MSVC complier itself is free and callable from things like code::blocks)

HTH DB

---

### Post by cb951303 on 2008-09-08
code:blocks has a visual studio project converter

---

### Post by mujambee on 2008-09-08
Visual Studio has an "Export makefile" option that should (or not) simplify the task. However, it's quite simple if you want to do it manually:

The "project" is a .dsp file. It is a text file and it's quite straightforward. First, search for lines like this:

```

!IF  "$(CFG)" == "pr4 - Win32 Release"

or

!ELSEIF  "$(CFG)" == "pr4 - Win32 Debug"
```
And identify the build you want to extract.

All switches for the compiler and resource compiler are defined there, along with the list of libraries to link.

At the end of the file, there are a group of blocks defining the sources tree. You only need to look at the source lines:

```

SOURCE=.\main.cpp
```
However, if you want to use that in Linux you wont have the resource compiler, nor the set of libraries it links:

```

# ADD LINK32 kernel32.lib user32.lib gdi32.lib winspool.lib comdlg32.lib advapi32.lib shell32.lib ole32.lib oleaut32.lib uuid.lib odbc32.lib odbccp32.lib kernel32.lib user32.lib gdi32.lib winspool.lib comdlg32.lib advapi32.lib shell32.lib ole32.lib oleaut32.lib uuid.lib odbc32.lib odbccp32.lib /nologo /subsystem:console /debug /machine:I386 /pdbtype:sept
```

---

### Post by kirsis on 2008-09-08
MonoDevelop 2 is ditching its own project/solution file formats and adopting the visual studio 2005/2008 formats.  ([http://abock.org/2008/09/03/useful-tidbit-for-monodevelop-users/](http://abock.org/2008/09/03/useful-tidbit-for-monodevelop-users/))
(and yeah, you can use MonoDevelop for C/C++ too)

It's alpha atm though and kept crashing when I last tried it (a few weeks ago, maybe a month)

My humble suggestion would be to ditch IDEs and use gedit + a build system of your choice (autotools for me)

---

### Post by MaxIBoy on 2008-09-08
I suppose a text editor will do for now, but I was really hoping to use an IDE. It's a big project with lots of files, I thought an organized environment might help me learn my way around the code so I can modify it without randomly changing stuff.


Here's a link to a different forum wherein someone else discovered problems importing into bloodshed. 
[http://corent.proboards42.com/index.cgi?board=crarena&action=display&thread=3087&page=1#30603](http://corent.proboards42.com/index.cgi?board=crarena&action=display&thread=3087&page=1#30603)
On that forum I'm maxtothemax.

I've done some trying on my own, I've had the same experience as that lizardlighting guy.

---

### Post by cb951303 on 2008-09-09
> **MaxIBoy said:**
> I suppose a text editor will do for now, but I was really hoping to use an IDE. It's a big project with lots of files, I thought an organized environment might help me learn my way around the code so I can modify it without randomly changing stuff.


Here's a link to a different forum wherein someone else discovered problems importing into bloodshed. 
[http://corent.proboards42.com/index.cgi?board=crarena&action=display&thread=3087&page=1#30603](http://corent.proboards42.com/index.cgi?board=crarena&action=display&thread=3087&page=1#30603)
On that forum I'm maxtothemax.

I've done some trying on my own, I've had the same experience as that lizardlighting guy.

have you tried code::blocks??

---

### Post by samjh on 2008-09-09
Both Monodevelop and Code::Blocks can import or open Visual Studio project files.

---

