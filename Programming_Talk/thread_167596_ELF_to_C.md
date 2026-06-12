---
title: "ELF to C"
date: 2006-04-28
forum: Programming Talk
---

### Post by dave on 2006-04-28
I was wondering if there were any tools that allowed someone to take a compiled file, and convert it back to the language it was writen in.

I know it wont be perfect because GCC does all sorts of crazy optimizations that ruin exactly what I wrote, but something that would still give me the structure (idea) of the binary?

--
dave

---

### Post by asimon on 2006-04-28
You look for a decompiler like [REC](http://www.backerstreet.com/rec/rec.htm) or [Boomerang](http://boomerang.sourceforge.net/). There you can also find some example and information to see what you can expect from such tools.

---

### Post by rplantz on 2006-04-28
If you read assembly language, you can use objdump with the -d option to disassemble an object file. Then you will see how the compiler optimized the code.

---

### Post by pedro1977 on 2012-06-09
I have tried countless ways to decompile these two files but with little success.  They are elf files which are apparantly written in c, they are for android.  Do you know of an windows gui based apps that will decompile these files and another to compile them?
One is a so library the other an archive without an extension.

---

### Post by lisati on 2012-06-09
Based on my limited experience with such tools, I'd say that converting an executable file back to source code isn't a trivial task. Even if you have access to debugging information provided by the original compiler, it can get very tedious making sure that your chosen tool is correct in its assumptions about the various elements of the binary file.

---

### Post by pedro1977 on 2012-06-09
I dont believe these are executables.

---

### Post by Bachstelze on 2012-06-10
[font=monospace]file[/font] says thay are executables, but ARM ones. So you will need a tool that supports ARM.

---

### Post by pedro1977 on 2012-06-11
> **Bachstelze said:**
> [FONT=monospace]file[/FONT] says thay are executables, but ARM ones. So you will need a tool that supports ARM.


thanks for your input ill take a look around for a decompiler

---

### Post by Tony Flury on 2012-06-12
Unless you have all the debug information, it is unlikely that you will be to extract meaningful variable or function names etc from a binary.

I have to also ask - why are you doing this ? If the application is open source, just ask for the original source code. If the application is copyrighted and a limited license you could find that under some jurisdictions that even attempting to decompile could be seen as a breach of that license. If you are doing this for education purposes and you own the source code, then compile it with the appropriate options to generate the assembly language so you can see the translation.

---

### Post by pedro1977 on 2012-06-13
> **Tony Flury said:**
> Unless you have all the debug information, it is unlikely that you will be to extract meaningful variable or function names etc from a binary.

I have to also ask - why are you doing this ? If the application is open source, just ask for the original source code. If the application is copyrighted and a limited license you could find that under some jurisdictions that even attempting to decompile could be seen as a breach of that license. If you are doing this for education purposes and you own the source code, then compile it with the appropriate options to generate the assembly language so you can see the translation.

I think theyt were executable, but your right after decompiling it it didn reveal too much, lots of sub routines and functions.  I am actually looking for com.android.gpslocationprovider/locationprovider but I am not sure where this is located in the android OS.

GPSD is actually opensource, but appears to have been omiited from the source code for this product at opensource.samsung.com.  There is a bug with the device and we would like to review the code for errors - nothing more.  This is related to GPS functionality.  My best bet is looking for location provider but I dont know where to start.

---

### Post by pbrane on 2012-06-14
If you are looking for the source to GPSd look here at the official website.
[http://catb.org/gpsd/]("http://catb.org/gpsd/")

---

