---
title: "C++ self source printing"
date: 2011-08-22
forum: Programming Talk
---

### Post by shashanksingh on 2011-08-22
Write a C++ program that prints its own source code when executed but does perform any input or file reading.

---

### Post by lisati on 2011-08-22
> **shashanksingh said:**
> Write a C++ program that prints its own source code when executed but does perform any input or file reading.

I'm sorry, my C++ skills aren't up to the task. 

Is this homework or a programming challenge? If homework, I'm sure someone will be able to give you some pointers without actually doing your work for you, as per the forum code of conduct.

---

### Post by nmaster on 2011-08-22
its called a quine. did u not try google?

[http://www.cs.uleth.ca/~holzmann/C/C/cselfprint.html](http://www.cs.uleth.ca/~holzmann/C/C/cselfprint.html)
[http://www.cplusplus.com/forum/unices/14588/](http://www.cplusplus.com/forum/unices/14588/)

---

### Post by shashanksingh on 2011-08-22
@lisati: It was just an exercise question in a book Im refering to get acquinted with C++. No homework. HONEST.

@nmaster:  thank you. I did not try google, I kind of like discussing it here with actual people if it needs any, but yes, I should have googled first. Agreed.

---

### Post by shanept on 2011-08-22
I used to work with a simple language called AutoIt in my days running Windows. Basically their method is as follows:

1. Program it so it opens the file and copies contents at compilation time.
2. Create a command line parameter so when called (eg. --decompile) it writes the code to a file.
3. Program it so it writes the contents to a file.
4. Compile.

Basically, you want to use a function to copy the file contents to a variable then write it to a file. Compile the project. _YOU DO NOT COPY THE CODE BY HAND_.

---

### Post by shashanksingh on 2011-08-22
> **shanept said:**
> I used to work with a simple language called AutoIt in my days running Windows. Basically their method is as follows:

1. Program it so it opens the file and copies contents at compilation time.
2. Create a command line parameter so when called (eg. --decompile) it writes the code to a file.
3. Program it so it writes the contents to a file.
4. Compile.

Basically, you want to use a function to copy the file contents to a variable then write it to a file. Compile the project. _YOU DO NOT COPY THE CODE BY HAND_.

I fail to comprehend that clearly, but I guess it must have involved file handling. Quine has to do it without I/O & file handling

---

