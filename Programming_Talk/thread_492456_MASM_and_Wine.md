---
title: "MASM and Wine"
date: 2007-07-04
forum: Programming Talk
---

### Post by bluehue on 2007-07-04
Hello everyone,

I was wondering if anyone has ever ran masm under wine who might be able to help me with a little problem. First, my source code:
```

title   Hello World Program                             (hello.asm)
; This program displays "Hello, World!"

dosseg
.model small
.stack 100h

.data
hello_message db 'Hello, World!',0dh,0ah,'$'

.code
main  proc
      mov    ax,@data
      mov    ds,ax

      mov    ah,9
      mov    dx,offset hello_message
      int    21h

      mov    ax,4C00h
      int    21h
main  endp
end   main
```
And the contents of my masm directory:
```

spiral@spiral-desktop:/storage/My Documents/CS264/masm$ ls
ADVISOR.HLP  CVPACK.EXE   EXP.EXE    HELPMAKE.EXE  make16a.bat  MSPDB60.DLL   QH.HLP        SMARTDRV.EXE
ALANG.HLP    DMW0.DLL     first.asm  HIMEM.SYS     make16.bat   mymacs.inc    RAMDRIVE.SYS  TLD1COM.DLL
CREF.DOC     DOSXNT.EXE   first.exe  IMPLIB.EXE    make32.bat   NEW-CONF.SYS  RCVCOM.EXE    TLD1LOC.DLL
CREF.EXE     EED1CXX.DLL  first.obj  LIB.EXE       MASM.EXE     NEW-VARS.BAT  runCV.bat     TOOLS.INI
CURRENT.STS  EMD1D1.DLL   H2INC.ERR  LINK32.EXE    ML.ERR       NMAKE.EXE     runQH.bat     Uninst.isu
CV.EXE       EMM386.EXE   H2INC.EXE  LINK.EXE      ML.EXE       NMAKER.EXE    SHD1.DLL      UTILS.HLP
CV.HLP       EXEHDR.EXE   hello.asm  LINK.HLP      ML.HLP       QH.EXE        SMARTDRV.DOC

```
Evidently, the hello.asm file assembles and links successfully:
```

spiral@spiral-desktop:/storage/My Documents/CS264/masm$ wine masm hello.asm
Microsoft (R) MASM Compatibility Driver
Copyright (C) Microsoft Corp 1993.  All rights reserved.

 Invoking: ML.EXE /I. /Zm /c /Ta hello.asm 

Microsoft (R) Macro Assembler Version 6.15.8803
Copyright (C) Microsoft Corp 1981-2000.  All rights reserved.

 Assembling: hello.asm
spiral@spiral-desktop:/storage/My Documents/CS264/masm$ wine link hello.obj

Microsoft (R) Segmented Executable Linker  Version 5.60.339 Dec  5 1994
Copyright (C) Microsoft Corp 1984-1993.  All rights reserved.

Run File [hello.exe]: 
List File [nul.map]: 
Libraries [.lib]: 
Definitions File [nul.def]: 
spiral@spiral-desktop:/storage/My Documents/CS264/masm$
```
Updated masm directory contents:
```

spiral@spiral-desktop:/storage/My Documents/CS264/masm$ ls
ADVISOR.HLP  DMW0.DLL     first.exe     HIMEM.SYS    make32.bat    NEW-VARS.BAT  runQH.bat     UTILS.HLP
ALANG.HLP    DOSXNT.EXE   first.obj     IMPLIB.EXE   MASM.EXE      NMAKE.EXE     SHD1.DLL
CREF.DOC     EED1CXX.DLL  H2INC.ERR     LIB.EXE      ML.ERR        NMAKER.EXE    SMARTDRV.DOC
CREF.EXE     EMD1D1.DLL   H2INC.EXE     LINK32.EXE   ML.EXE        QH.EXE        SMARTDRV.EXE
CURRENT.STS  EMM386.EXE   hello.asm     LINK.EXE     ML.HLP        QH.HLP        TLD1COM.DLL
CV.EXE       EXEHDR.EXE   hello.exe     LINK.HLP     MSPDB60.DLL   RAMDRIVE.SYS  TLD1LOC.DLL
CV.HLP       EXP.EXE      hello.obj     make16a.bat  mymacs.inc    RCVCOM.EXE    TOOLS.INI
CVPACK.EXE   first.asm    HELPMAKE.EXE  make16.bat   NEW-CONF.SYS  runCV.bat     Uninst.isu
```
The problem occurs when I try to run the executable file:
```

spiral@spiral-desktop:/storage/My Documents/CS264/masm$ wine hello.exe
Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.


```
Wine hangs with this last error (wineserver and winevdm are both running under System Monitor) until I close the process with ctrl+c. Any ideas as to what I'm doing wrong here? :confused: That last command should have displayed the 'Hello, World!' message.

---

### Post by lisati on 2007-07-04
Just a guess that might kick-start a discussion that finds the answer: perhaps someone else out there will know if WINE (or similar) supports the older segmented memory models?

---

### Post by AlexThomson_NZ on 2007-07-04
hmm interesting problem- I tend to agree with lisati theory.

Just out of curiosity, have you tried running the executable on a real windows machine?

---

### Post by bluehue on 2007-07-04
> **AlexThomson_NZ said:**
> hmm interesting problem- I tend to agree with lisati theory.

Just out of curiosity, have you tried running the executable on a real windows machine?Oh no I haven't as I only run Ubuntu on my machine. Reinstalling windows just to run masm will be my last resort.

---

### Post by AlexThomson_NZ on 2007-07-04
Email it to me if you like, and I can try it on the missus's windows box tonight (thomson.alex.w at gmail dot com)

---

### Post by bluehue on 2007-07-04
> **AlexThomson_NZ said:**
> Email it to me if you like, and I can try it on the missus's windows box tonight (thomson.alex.w at gmail dot com) E-mail sent. Thanks!

---

### Post by AlexThomson_NZ on 2007-07-04
Hmm didn't come through, probably bounced by gmail for being an .exe - was it tar-ed?

---

### Post by bluehue on 2007-07-04
> **AlexThomson_NZ said:**
> Hmm didn't come through, probably bounced by gmail for being an .exe - was it tar-ed?Yup, the e-mail bounced back due to the .exe file. Re-sent it as a tar archive. Thanks for the help.

---

### Post by AlexThomson_NZ on 2007-07-04
Got it now.  Might give it a go here at work if I can find a willing vic- er... guinea pig ;)

---

### Post by AlexThomson_NZ on 2007-07-04
Hey I tried it on a win2k virtual machine here, and it worked...

That was a bit surprising to me, that Wine would have a problem with such a simple program.  I don't have Wine on my machine here at work, but are there any options that need tweaking to support this "old-school" type memory model?

---

### Post by bluehue on 2007-07-05
> **AlexThomson_NZ said:**
> Hey I tried it on a win2k virtual machine here, and it worked...

That was a bit surprising to me, that Wine would have a problem with such a simple program.  I don't have Wine on my machine here at work, but are there any options that need tweaking to support this "old-school" type memory model?Yeah, it really is surprising and I'm running the latest version (wine-0.9.40). I've tried running it under every windows environment setting within wine, from windows 2.0 to vista, to no avail. A buddy of mine ran into the same problems on a Debian Lenny box as well. And NASM is also out of the question, for it seems to support a different assembly syntax. But regardless, thank you for the help thus far. :)

---

### Post by lisati on 2007-07-05
I got hold of a copy of a couple of different versions TASM (Borland's equivalent to MASM) a couple of years ago, I might give it a whirl some time to see how it goes on Wine

---

### Post by the_unforgiven on 2007-07-05
I can tell you why it worked on windows - because of [NTVDM]("http://en.wikipedia.org/wiki/NTVDM") which traps DOS accesses and redirects them to windows system calls.
I doubt something like that is available as part of WINE - as WINE mainly focuses on Win32 API.

Maybe, you can try out the binary in [DOSBox]("http://dosbox.sourceforge.net/")?

HTH ;)

---

### Post by AlexThomson_NZ on 2007-07-05
> **the_unforgiven said:**
> I can tell you why it worked on windows - because of [NTVDM]("http://en.wikipedia.org/wiki/NTVDM") which traps DOS accesses and redirects them to windows system calls.
I doubt something like that is available as part of WINE - as WINE mainly focuses on Win32 API.

Maybe, you can try out the binary in [DOSBox]("http://dosbox.sourceforge.net/")?

HTH ;)

I guess thinking about it the windows kernel would add their own wrapper around the old DOS calls to prevent unauthorized disk/gfx access, etc.  in which case you wouldn't be able to use the interrupts willy nilly.

// quite obvious now I think about it...

---

### Post by bluehue on 2007-07-05
> **lisati said:**
> I got hold of a copy of a couple of different versions TASM (Borland's equivalent to MASM) a couple of years ago, I might give it a whirl some time to see how it goes on WineCool, let us know how it goes.
> **the_unforgiven said:**
> I can tell you why it worked on windows - because of [NTVDM]("http://en.wikipedia.org/wiki/NTVDM") which traps DOS accesses and redirects them to windows system calls.
I doubt something like that is available as part of WINE - as WINE mainly focuses on Win32 API.

Maybe, you can try out the binary in [DOSBox]("http://dosbox.sourceforge.net/")?

HTH ;)Thanks! That certainly clears things up. And I've previously installed dosbox but failed to get anywhere with it. I didn't give it much of a chance, to be honest, as I sought a quick and easy solution with wine. I'll give it another try.

---

### Post by bluehue on 2007-07-05
Well, DOSbox was able to run my executable (hello.exe), but it won't assemble my source code (although it will link the hello.obj file). Here's the error:
```

Z:\>mount C "/storage/My Documents/CS264/masm"
Drive C is mounted as local directory /storage/My Documents/CS264/masm

Z:\>C:

C:\>masm hello.asm
Microsoft (R) MASM Compatibility Driver
Copyright (C) Microsoft Corp 1993.  All rights reserved.

 Invoking: ML.EXE /I. /Zm /c /Ta hello.asm 

This program cannot be run in DOS mode.

```
At this point I have to assemble with wine to generate the hello.obj file:
```

spiral@spiral-desktop:/storage/My Documents/CS264/masm$ wine masm hello.asm
Microsoft (R) MASM Compatibility Driver
Copyright (C) Microsoft Corp 1993.  All rights reserved.

 Invoking: ML.EXE /I. /Zm /c /Ta hello.asm 

Microsoft (R) Macro Assembler Version 6.15.8803
Copyright (C) Microsoft Corp 1981-2000.  All rights reserved.

 Assembling: hello.asm
spiral@spiral-desktop:/storage/My Documents/CS264/masm$

```
Now I may use DOSbox to link the hello.obj file to produce the hello.exe executable which I run as my last step:
```

C:\>link hello.obj

Microsoft (R) Segmented Executable Linker  Version 5.60.339 Dec  5 1994
Copyright (C) Microsoft Corp 1984-1993.  All rights reserved.

Run File [hello.exe]: 
List File [nul.map]: 
Libraries [.lib]: 
Definitions File [nul.def]:

C:\>hello
Hello, World!

```So I have to rely on wine to assemble and DOSbox to link the object file and run the executable. I would much rather rely on wine or DOSbox, not both, for all required steps but I'm nevertheless happy with the results. 

Thanks for the help everyone! :)

---

### Post by the_unforgiven on 2007-07-05
I suggest you use WINE for all the build process - assembling and linking; and use DOSBox only for testing out/running the final binaries. I don't know what problems the linker might give in DOSBox.

Also, the link.exe version seems to be from an older distribution as compared to ML.exe..
Is it the way Microsoft ships it? Does it mean that the linker has not been updated at all to match up with the updated assembler?
Sounds strange to me... O_o

---

### Post by lisati on 2007-07-05
> **bluehue said:**
> Well, DOSbox was able to run my executable (hello.exe), but it won't assemble my source code (although it will link the hello.obj file). Here's the error:
```

Z:\>mount C "/storage/My Documents/CS264/masm"
Drive C is mounted as local directory /storage/My Documents/CS264/masm

Z:\>C:

C:\>masm hello.asm
Microsoft (R) MASM Compatibility Driver
Copyright (C) Microsoft Corp 1993.  All rights reserved.

 Invoking: ML.EXE /I. /Zm /c /Ta hello.asm 

This program cannot be run in DOS mode.

```
At this point I have to assemble with wine to generate the hello.obj file:
```

spiral@spiral-desktop:/storage/My Documents/CS264/masm$ wine masm hello.asm
Microsoft (R) MASM Compatibility Driver
Copyright (C) Microsoft Corp 1993.  All rights reserved.

 Invoking: ML.EXE /I. /Zm /c /Ta hello.asm 

Microsoft (R) Macro Assembler Version 6.15.8803
Copyright (C) Microsoft Corp 1981-2000.  All rights reserved.

 Assembling: hello.asm
spiral@spiral-desktop:/storage/My Documents/CS264/masm$

```
Now I may use DOSbox to link the hello.obj file to produce the hello.exe executable which I run as my last step:
```

C:\>link hello.obj

Microsoft (R) Segmented Executable Linker  Version 5.60.339 Dec  5 1994
Copyright (C) Microsoft Corp 1984-1993.  All rights reserved.

Run File [hello.exe]: 
List File [nul.map]: 
Libraries [.lib]: 
Definitions File [nul.def]:

C:\>hello
Hello, World!

```So I have to rely on wine to assemble and DOSbox to link the object file and run the executable. I would much rather rely on wine or DOSbox, not both, for all required steps but I'm nevertheless happy with the results. 
 
Thanks for the help everyone! :)
The message about "won't run in DOS mode" is usually given when you are running a Win32 program from MS-DOS, without the benefit of Windows being present. Quite  possibly the version of MASM you have is intended to be run in a WIN32 environment. If I remember I'll dig through my archives and see if I have a 16-bit version of MASM there....

---

### Post by the_unforgiven on 2007-07-05
On second thought (and after taking another look at your code), is it really important/necessary for you to use MASM?
I mean, there are other native assemblers available - like NetWide Assembler (NASM) or even GNU Assembler (as)..

NASM uses nearly the same syntax (Intel syntax) as MASM whereas GNU assembler uses the AT&T syntax - it can work with Intel syntax too. 
Here is some info on GNU Assembler:
[http://en.wikipedia.org/wiki/GNU_Assembler](http://en.wikipedia.org/wiki/GNU_Assembler)

---

### Post by lisati on 2007-07-05
Tracked down a copy of TASM (and TLINK) that can be used with DOSEMU.... see attached

---

### Post by bluehue on 2007-07-05
> **the_unforgiven said:**
> I suggest you use WINE for all the build process - assembling and linking; and use DOSBox only for testing out/running the final binaries. I don't know what problems the linker might give in DOSBox.Yeah, even though I can link in DOSBox, I think that's a good suggestion.

> **the_unforgiven said:**
> Also, the link.exe version seems to be from an older distribution as compared to ML.exe..
Is it the way Microsoft ships it? Does it mean that the linker has not been updated at all to match up with the updated assembler?
Sounds strange to me... O_oI'm not altogether sure if it's the one officially distributed by MS as I'm using a version of masm (masm 6.15) provided by the college course I'm taking. I'll try to upload it onto my webspace later as I currently cannot ftp it there. It seems to be available from multiple sources on-line, however, and you'll also need a file called mymacs.inc in the directory where you extract masm.
> **lisati said:**
> The message about "won't run in DOS mode" is usually given when you are running a Win32 program from MS-DOS, without the benefit of Windows being present. Quite  possibly the version of MASM you have is intended to be run in a WIN32 environment. If I remember I'll dig through my archives and see if I have a 16-bit version of MASM there....If you can find it, that would be great. Thanks!
> **the_unforgiven said:**
> On second thought (and after taking another look at your code), is it really important/necessary for you to use MASM?
I mean, there are other native assemblers available - like NetWide Assembler (NASM) or even GNU Assembler (as)..

NASM uses nearly the same syntax (Intel syntax) as MASM whereas GNU assembler uses the AT&T syntax - it can work with Intel syntax too. 
Here is some info on GNU Assembler:
[http://en.wikipedia.org/wiki/GNU_Assembler](http://en.wikipedia.org/wiki/GNU_Assembler)Yeah the version of masm I'm using (masm 6.15) is the one officially provided by the course and I have no other recourse since my project deliverables will be tested by the professor, presumably by using the same version of masm. Because of this I don't want to submit sources and binaries, generated by a different assembler, that may or may not run on his machine. It was my understanding that NASM has a similar (updated?) but not the same sintax as masm but I'll give it a shot.
> **lisati said:**
> Tracked down a copy of TASM (and TLINK) that can be used with DOSEMU.... see attachedThanks!

---

### Post by bluehue on 2007-07-05
> **lisati said:**
> Tracked down a copy of TASM (and TLINK) that can be used with DOSEMU.... see attachedHere's what I get with wine:
```

spiral@spiral-desktop:/storage/My Documents/CS264/TASM$ wine TASM hello.asm
Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.

```
And with DOSBox:
```

C:\>TASM hello.asm

Turbo Assembler  Version 3.2  Copyright (c) 1988, 1992 Borland International

Assembling file:   hello.asm
Error messages:    None
Warning messages:  None
Passes:            1
Remaining memory:  472k

C:\>TLINK hello.obj

Failed to locate DPMI server (DPMI16BI.OVL)

C:\>
```It was clear I was missing a file called DPMI16BI.OVL, which I got from [http://www.geocities.com/SiliconValley/Network/2963/dpmi16.zip](http://www.geocities.com/SiliconValley/Network/2963/dpmi16.zip) and placed into the TASM directory. My results:
```

C:\>dir

Directory of C:\.
.              <DIR>            05-07-2007 12:46
..             <DIR>            05-07-2007 12:28
DPMI16BI OVL             50,576 21-02-1996  5:00
DPMILOAD EXE             22,324 05-07-2007  7:05
DPMIMEM  DLL             24,932 08-03-1993 10:01
HELLO    ASM                387 04-07-2007 14:23
OUT1     TXT                  0 05-07-2007 12:46
TASM     EXE            133,580 08-03-1993 10:01
TASM     TAH            176,061 08-03-1993 10:01
TASMX    EXE            146,988 08-03-1993 10:01
TCREF    EXE              7,856 08-03-1993 10:01
TLINK    EXE            150,569 08-03-1993 10:01
WINSTUB  EXE                578 08-03-1993 10:01
   11 File(s)           713,851 Bytes.
    2 Dir(s)        110,540,800 Bytes free.

C:\>tasm hello.asm

Turbo Assembler  Version 3.2  Copyright (c) 1988, 1992 Borland International

Assembling file:   hello.asm
Error messages:    None
Warning messages:  None
Passes:            1
Remaining memory:  472k

C:\>tlink hello.obj

Turbo Link  Version 5.1 Copyright (c) 1992 Borland International

C:\>hello
Hello, World!

C:\>dir

Directory of C:\.
.              <DIR>            05-07-2007 12:47
..             <DIR>            05-07-2007 12:28
DPMI16BI OVL             50,576 21-02-1996  5:00
DPMILOAD EXE             22,324 05-07-2007  7:05
DPMIMEM  DLL             24,932 08-03-1993 10:01
HELLO    ASM                387 04-07-2007 14:23
HELLO    EXE                576 05-07-2007 12:47
HELLO    MAP                232 05-07-2007 12:47
HELLO    OBJ                265 05-07-2007 12:46
TASM     EXE            133,580 08-03-1993 10:01
TASM     TAH            176,061 08-03-1993 10:01
TASMX    EXE            146,988 08-03-1993 10:01
TCREF    EXE              7,856 08-03-1993 10:01
TLINK    EXE            150,569 08-03-1993 10:01
WINSTUB  EXE                578 08-03-1993 10:01
   18 File(s)           715,952 Bytes.
    2 Dir(s)        110,540,800 Bytes free. 
```TASM in DOSBox works like a charm :) It does, however, generate an extra file (hello.map) not produced by masm :confused:

---

### Post by bluehue on 2007-07-05
And here are my results from attempting to assemble the hello.asm file from the original post using NASM:
```

spiral@spiral-desktop:~/Desktop$ nasm -f win32 hello.asm
hello.asm:1: error: parser: instruction expected
hello.asm:5: error: parser: instruction expected
hello.asm:6: error: parser: instruction expected
hello.asm:12: error: parser: instruction expected
hello.asm:17: error: comma or end of line expected
hello.asm:22: error: symbol `main' redefined
hello.asm:22: error: parser: instruction expected
hello.asm:23: error: parser: instruction expected
spiral@spiral-desktop:~/Desktop$ 

```#-o

---

### Post by lisati on 2007-07-05
> **bluehue said:**
> And here are my results from attempting to assemble the hello.asm file from the original post using NASM:
```

spiral@spiral-desktop:~/Desktop$ nasm -f win32 hello.asm
hello.asm:1: error: parser: instruction expected
hello.asm:5: error: parser: instruction expected
hello.asm:6: error: parser: instruction expected
hello.asm:12: error: parser: instruction expected
hello.asm:17: error: comma or end of line expected
hello.asm:22: error: symbol `main' redefined
hello.asm:22: error: parser: instruction expected
hello.asm:23: error: parser: instruction expected
spiral@spiral-desktop:~/Desktop$ 

```#-o

I've steered away from Nasm since it uses a different syntax to Tasm and Masm.

---

### Post by lisati on 2007-07-05
Just a thought - which was the first x86 assembler did the people here use?  For me it was a86

---

### Post by AlexThomson_NZ on 2007-07-05
Jeez, does 'debug' on a DR-DOS emulator on the Amiga count? (I did my first 'hello world' x86 asm program on that- kinda parallels your Wine experience! :) )

I think my first real native x86 assembler would have been Tasm, but can't remember for sure...

---

### Post by the_unforgiven on 2007-07-06
> **bluehue said:**
> 
Yeah the version of masm I'm using (masm 6.15) is the one officially provided by the course and I have no other recourse since my project deliverables will be tested by the professor, presumably by using the same version of masm. Because of this I don't want to submit sources and binaries, generated by a different assembler, that may or may not run on his machine. It was my understanding that NASM has a similar (updated?) but not the same sintax as masm but I'll give it a shot.
Thanks!
Well, I think it's better if you stick to MASM in that case ;)
The profs are a different breed altogether - I think they don't have ears/brains that can listen to whatever explanations we can give to use alternative software - even if the alternatives are way much better.. :(

As far as using NASM to compile your program as it is, well, that wasn't going to happen.
I said, it uses a nearly same syntax - not equivalent. What I wanted to stress on was the Intel syntax.
Maybe, I wasn't clear enough... :oops: 8-[

---

### Post by bluehue on 2007-07-10
> **lisati said:**
> Tracked down a copy of TASM (and TLINK) that can be used with DOSEMU.... see attachedSorry for the bump, but I was wondering, would you also happen to have a copy of Turbo Debugger 1.0 ([http://en.wikipedia.org/wiki/Turbo_Debugger](http://en.wikipedia.org/wiki/Turbo_Debugger)) on hand? I found a copy of v3.2 at [http://digilander.libero.it/rferru/software/TD.zip](http://digilander.libero.it/rferru/software/TD.zip) but I'm more interested in this older (original ?) version as the wikipedia page suggests that later version can cause problems with dos emulators.

---

### Post by lisati on 2007-07-10
> **bluehue said:**
> Sorry for the bump, but I was wondering, would you also happen to have a copy of Turbo Debugger 1.0 ([http://en.wikipedia.org/wiki/Turbo_Debugger](http://en.wikipedia.org/wiki/Turbo_Debugger)) on hand? I found a copy of v3.2 at [http://digilander.libero.it/rferru/software/TD.zip](http://digilander.libero.it/rferru/software/TD.zip) but I'm more interested in this older (original ?) version as the wikipedia page suggests that later version can cause problems with dos emulators.

The only copy remember having is on old 5.25" disks, and none of the machines I currently use can read them. I don't have the courage to try to blow the dust of the disk drives in my cupboard to try using them with XP or Ubuntu.

---

### Post by the_unforgiven on 2007-07-10
You can download some of the antique Borland software from here:
[http://dn.codegear.com/museum/antiquesoftware](http://dn.codegear.com/museum/antiquesoftware)

Unfortunately, Turbo Debugger is not in the list as a separate application.
Maybe, if you download Turbo C/C++/Pascal, it might come bundled with it.

HTH ;)

Edit: I downloaded both Turbo C and Turbo C++, unfortunately, the debugger doesn't ship with these antique versions. :(

---

### Post by DarkW0lf on 2007-07-21
This is actually easier than what many have posted.
Though you compiled a MS program it is still a unix box, you need to use 'wine ./hello.exe'
You have to remember to use a dot-slash for executables sitting in the working directory or change the path variable to include the working directory (like the way windows does).

There is a good MASM development package called MASM32 ([http://www.movsd.com](http://www.movsd.com))
I don't know of anyone that runs it under WINE but it has a lot of libraries and code for you to use.
(Note that using MASM in WINE on Linux violates the MS EULA and --hutch works to maintain the legal license so I don't think he'll help with this)

For Assembly on Linux I'd use GAS or HLA ([http://webster.cs.ucr.edu](http://webster.cs.ucr.edu))

---

### Post by bluehue on 2007-07-22
> **DarkW0lf said:**
> This is actually easier than what many have posted.
Though you compiled a MS program it is still a unix box, you need to use 'wine ./hello.exe'
You have to remember to use a dot-slash for executables sitting in the working directory or change the path variable to include the working directory (like the way windows does).It is not required to include the dot-forward slash when running a windows application through wine, but it would not be incorrect to include it:
```

spiral@spiral-desktop:/storage/My Documents/CS264/masm$ wine ./hello.exe
Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.

```The above generates the same error I mentioned in the first post:
```

spiral@spiral-desktop:/storage/My Documents/CS264/masm$ wine hello.exe
Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.

```
> There is a good MASM development package called MASM32 ([http://www.movsd.com](http://www.movsd.com))
I don't know of anyone that runs it under WINE but it has a lot of libraries and code for you to use.
(Note that using MASM in WINE on Linux violates the MS EULA and --hutch works to maintain the legal license so I don't think he'll help with this)

For Assembly on Linux I'd use GAS or HLA ([http://webster.cs.ucr.edu](http://webster.cs.ucr.edu))I'm restricted to MASM and TASM for reasons discussed but I'll give MASM32 a try. Thanks for the suggestion. 

Thus far, the combination of DOSBox and TASM has worked out wonderfully.

---

### Post by DarkW0lf on 2007-07-27
I never had a program work under wine without the proper notation. The path passed to wine is a unix path and relative paths still need the dot-slash, not sure how you got it to work otherwise.

But your error may be related to MASM's operation under wine. Your app was compiled to use a memory address not available under wine. What version of ml.exe are you using ?

---

### Post by Vivek788 on 2008-06-15
So can this be concluded in saying that compiling and linking must be done in wine whereas execution in DOSbox???

---

### Post by NathanB on 2008-06-15
> **Vivek788 said:**
> So can this be concluded in saying that compiling and linking must be done in wine whereas execution in DOSbox???

Only in the specific case concerned in this old thread.  The OP was required to produce the old DOS-style executables and the teacher gave him a somewhat eclectic mix of tools for the task -- a newer Masm (which only runs in Windows) and the necessary older linker to produce DOS execs.  Since Wine has no support for DOS, the DOSbox is needed to run the execs.  There are two alternatives for those who do not wish to run *both* Wine and DOSbox:

1)  Get a really old version of MASM (one that runs in DOS mode) and the linker and only produce DOS-style executables.  This way, you can use only DOSbox for the entire assemble-link-test cycle.

2)  Get the MASM32 package [http://www.movsd.com/](http://www.movsd.com/) and only produce Win32-style executables.  This way, you can use only Wine for the entire assemble-link-test cycle.

Nathan.

---

### Post by Vivek788 on 2008-06-16
hm...dos style exectutables as in..?
i use masm that runs in dos prompt.have 3 steps to get it running.so can i compeletely do it in dosbox...?thanks for the info..

---

### Post by sighk on 2008-10-02
If you are only using ubuntu why are you compiling microsoft assembly?

try nasm

sudo apt-get install nasm

the assembly is a little different

21h is kernel call for microsoft kernel

80h is linux,

assembly for linux itself is easier also

---

### Post by razorxpress on 2009-11-07
It's very simple. Download [Masm 6.15]("http://www2.hawaii.edu/~pager/312/masm%20615.ZIP") from [http://www2.hawaii.edu/~pager/312/masm%20615.ZIP](http://www2.hawaii.edu/~pager/312/masm%20615.ZIP)   Unzip it and use wine. I still cannot setup PATH for wine or wineconsole. I copied your source code to simple.asm. Then used wine to run it as 
$ wine ML ../Programs/simple.asm

To run ML I was inside the BIN directory of masm. I copied simple.asm in Programs directory outside BIN directory. 

The output was

Microsoft (R) Macro Assembler Version 6.14.8444
Copyright (C) Microsoft Corp 1981-1997.  All rights reserved.

 Assembling: ../Programs/simple.asm

Microsoft (R) Segmented Executable Linker  Version 5.60.339 Dec  5 1994
Copyright (C) Microsoft Corp 1984-1993.  All rights reserved.

Object Modules [.obj]: simple.obj 
Run File [simple.exe]: "simple.exe"
List File [nul.map]: NUL
Libraries [.lib]: 
Definitions File [nul.def]: 

Then i ran simple.exe

$ wine simple.exe 
Hello, World!

Some times wine alone may not run the program in that case use wineconsole.

---

### Post by trusktr on 2010-10-07
I know this is an old post, but in case anyone is wondering, I've got MASM fully working in dosBox compiling, linking, and executing.

I've posted the details here:
[http://www.atbskate.com/trusktr/2010/10/07/good-news-everyone-its-easy-to-get-masm-working-in-linux/](http://www.atbskate.com/trusktr/2010/10/07/good-news-everyone-its-easy-to-get-masm-working-in-linux/)

---

