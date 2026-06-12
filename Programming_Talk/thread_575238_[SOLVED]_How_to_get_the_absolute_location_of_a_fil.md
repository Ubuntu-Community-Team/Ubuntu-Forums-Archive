---
title: "[SOLVED] How to get the absolute location of a file? (C)"
date: 2007-10-13
forum: Programming Talk
---

### Post by Vadi on 2007-10-13
Hi all,

I'm doing some programming in C, and while I can read, and write to files with the stdio.h library just fine, it doesn't seem to provide a function where I can get the absolute location of a file - like starting from the file system, then /home, then /user name and such.

Does anyone know of a way I can get about this limitation?

Thank you.

---

### Post by Lux Perpetua on 2007-10-13
I don't understand the question. Get the absolute location...based on what? If you don't know the path and name of the file, what do you know about it?

---

### Post by Vadi on 2007-10-13
The program can interact fine with the files in it's own folder, for that, I just need to specify the file's name only.

But how can I get the absolute location based on the start of the file system. Like "home/myaccount/myprogram/file.txt", as an example.

---

### Post by fdrake on 2007-10-13
you mean you cannot use files that are outside the folder you're working. i am not a c programmer but i am interested in it.:-o

---

### Post by vambo on 2007-10-13
Have a look at getenv

```
path = getenv ("$HOME")
```should return /home/user_name
in "path" - check the syntax - I did this off the top of my head - which is not as reliable as I'd like :(

---

### Post by Ptero-4 on 2007-10-13
What the OP meant is that he is making his program read and write to a plain file whose name is hardcoded in the program, but he currently needs to have the file in the same path as the program binary, and he wants to know how to tell the program to look in a specific path (in the format /path/to/the/file.txt) no matter if the file and program binary are on different parts of the filesystem.

---

### Post by Vadi on 2007-10-13
Oh dear, I think I confused myself.

Okay, in short, I do this - open a file, that's inside the same folder as the program, so I don't need to worry about hopping dirs. I write to it, and when I want to output "Data saved to *path_to_file*/file.txt", hence the absolute location. Like for windows users, it should start with C:/ and such.

Does anyone know how can I do that? I suppose all I need is the absolute location of the program itself, really.

---

### Post by CptPicard on 2007-10-13
When you start your process, it's got a working directory which is implicitly added in front of the path you use in your filesystem calls. You can figure it out by using the  [getcwd]("http://www.gnu.org/software/libc/manual/html_node/Working-Directory.html#Working-Directory") function :)

---

### Post by Vadi on 2007-10-13
Awesome, thank you. I'll take a look.

---

### Post by Lux Perpetua on 2007-10-13
So you want to basically want to prepend the current working directory to the filename? getenv("PWD") will get you the current directory, and you can work from there.

---

### Post by CptPicard on 2007-10-13
Why mess around with env variables when there is a clear-cut standard library call? (that I found out by a simple googling of "glibc currect working directory" or somesuch) :)

---

### Post by Vadi on 2007-10-13
Thank you! The getcwd function did it.

---

