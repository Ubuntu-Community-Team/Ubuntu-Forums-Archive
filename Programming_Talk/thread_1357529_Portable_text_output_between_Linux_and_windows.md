---
title: "Portable text output between Linux and windows"
date: 2009-12-17
forum: Programming Talk
---

### Post by vgokul on 2009-12-17
Hello all,
         I am working on Windows as host and Ubuntu through VirtualBox. I have a C code to write a text format file which is a configuration file for a 3rd party Windows tool. 
        I create this file as part of a bigger application that should run in both windows and linux. I have access to all the source files and compile and link separately in Windows and Linux. 
        When I open the file created in a Linux run in the 3rd party tool in Windows the file is not loadable. If I open the file in wordpad and save it , then I can open the file in the 3rd party windows tool.
      I understand that this is because of the different ways Windows and Linux handle the newline (CR+LF vs LF). I use fprintf statements with \n
 
Can you please suggest what changes I should make in the code that I can make the text file portable (atleast one way - Linux to Windows)?
 
Regards
V.Gokul

---

### Post by lisati on 2009-12-17
Short of using a purpose-written tool (e.g. unix2dos) do convert the files on the target os, you might want to manually insert the proper newline sequence for the target OS instead of using the '\n' escape sequence in your output.

---

### Post by Reiger on 2009-12-17
Please note that this problem looks worse than it actually is: \n is ANSI C convention. This means that an ANSI C compiler on Windows would automatically convert the \n to \r\n; and one on MAC would convert to \r.

This means that in effect as long as you do not need to share configuration files for Windows with those for Linux you will not run into this problem at all.

---

### Post by wmcbrine on 2009-12-17
...and if you do, then write out the files in binary mode, use "\r\n" as the line endings when writing, and strip both '\r' and '\n' when reading.

---

