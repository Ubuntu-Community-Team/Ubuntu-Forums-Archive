---
title: "Some C++ help"
date: 2009-03-29
forum: Packaging and Compiling Programs
---

### Post by abbec on 2009-03-29
If anyone could be kind enough to help me I would be very happy...

This code is working fine if i compile it under windows, but when i compile it under Ubuntu in Code:blocks, it is behaving very strange. I read data from a text file, and it just reads one line.

Is this because of g++?

When i use cout the float that is coming after the name is placed at the beginning of the row. Why?

Please help!

(Code is attatched below)

Thanks in advance :)

---

### Post by Dejai on 2009-03-29
Open Terminal.

Extract file:
tar zxvf code.tar.gz

Use the following command:
g++ -Wall -Werror -o myProgram main_uppg2.cpp diver_info.cpp

This compiles the program, shows errors (-Wall) treats all warnings as errors (-Werror) and makes an binary called myProgram (-o myProgram) then I just added your two .cpp files. It seemed to work fine no problems.

EDIT: This was before I actually read the question read the post below it...
Also g++ has different standards to Microsoft version of C++ you may want to look that up.

---

### Post by Dejai on 2009-03-29
I don't have time now to go through the code line by line... But your best bet is to make sure their is no system specific command calls. I would read up on the differences between UNIX and Windows systems when it comes to reading files. Also it would be very much appreciated if you elaborated on your problem more and gave some debugging information. Its a bit much to expect someone to debug your application of 4 pages + for you. After all it is a learning experience :P

---

### Post by abbec on 2009-03-30
Yes i understand that, but I just wanted to clarify what could be wrong, so thanks very much, the help is very much appreciated :)

---

### Post by WakkiTabakki on 2009-03-30
Since you're reading from a text file, it may be as simple as this... 
Windows and Linux/Unix treat line-endings differently. Windows uses two characters (ASCII values 10 and 13, representing line feed and carriage return) while Linux only uses ASCII value 10 (line feed).

Check it out here:
[http://en.wikipedia.org/wiki/Newline](http://en.wikipedia.org/wiki/Newline) 

Simple way to try if this is it, make sure you test run your Ubuntu-compiled program on a text file created in Ubuntu...

Good luck
/N

---

