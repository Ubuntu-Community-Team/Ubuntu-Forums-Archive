---
title: "[Code::Blocks 8.02] Compiling programs for Ubuntu 10.04"
date: 2011-06-07
forum: Programming Talk
---

### Post by Rivkah on 2011-06-07
Alright, well I have installed Code::Blocks 8.02 to my recently installed Ubuntu 10.04. Although I can run the programs fine through Code::Blocks with the debugger, they do not run in Ubuntu. They are just .exe executables and attempt to be extracted. New to Code::Blocks and Linux, so please excuse any stupidity or such. (Yes, I tried to search around for it, no other posts seemed to fit) Yes, I looked in build preference and it is set to "ALL". But another option says "Build and Debug are only for Windows Platforms" or such. I am running C++ Console programs and thought that they should run under Linux. Can anybody help me build whatever linux uses as binaries?

[Seemed to have mistakingly placed this under "Programming Talk", please move accordingly]

---

### Post by Rivkah on 2011-06-08
/Bumping before bed :)

---

### Post by Vaphell on 2011-06-08
while the c/c++ code is somewhat portable, binary files being a result of compilation most certainly are not. You need to compile your program for each platform you want to run it on. Windows and linux speak different languages, so your code in 'english' needs to be translated to 'windowsish' and 'linuxish'.

Open your project in CB on linux box, compile it (build project or whatever, it should be the same as in win version of CB), look for binary file in project folder.

---

### Post by Petrolea on 2011-06-08
As post above already said, don't expect any .exe to work on Linux distros (excluding emulators). Linux doesn't even use .exe, executable files don't have extension at all. You are probably used to running executable files by double-clicking them, this won't work here either, you need to run it in command line.

If you still have trouble compiling the same code on Ubuntu as on Windows, try posting it here and we'll see where the problem is.

---

### Post by Rivkah on 2011-06-08
Oh, thanks..Yea, was so use to double clicking it to get it to work. I finally got it to create non-.exe executables that I thought would work..But could only get to run them from the Terminal, thought something was just wrong with them. Is there anyway to get them so they can open their own terminal and run it?

---

### Post by Petrolea on 2011-06-08
> **Rivkah said:**
> Oh, thanks..Yea, was so use to double clicking it to get it to work. I finally got it to create non-.exe executables that I thought would work..But could only get to run them from the Terminal, thought something was just wrong with them. Is there anyway to get them so they can open their own terminal and run it?

Not that I know. Only GUI apps open by double-click.

---

### Post by Rivkah on 2011-06-08
Alright, thanks. Setting thread to solved. :)

---

### Post by faizanzahid2137 on 2011-12-19
i have installes ubuntu 8.02 in ubuntu 10.4 when i compile it error comes "your files need to  rebuilt rebuild again "      and this message comes again and again and i can not compile my code what can i do now?

---

