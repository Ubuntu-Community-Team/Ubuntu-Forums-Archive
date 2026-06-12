---
title: "Compiling the program in codeblocks??"
date: 2013-09-25
forum: New to Ubuntu
---

### Post by abhayaasp on 2013-09-25
I have tried to compile a simple program in the ubuntu. And i got the following result.
<code>
sh 1: /media/stuff4/sample: Permission denied
</code>
How to resolve these sort of problem.

---

### Post by Bucky Ball on 2013-09-25
Try using 'sudo' before your command.

---

### Post by whitesmith on 2013-09-25
Ubuntu is organized so that you need elevated permissions (as in Bucky Ball's suggestion) to do anything but read outside $HOME. If you set up to compile to ~/stuff4 you wouldn't need sudo. An even better plan is to create a bin directory in your home directory and path it, so that your programs can be accessed more easily from a terminal.

---

### Post by steeldriver on 2013-09-25
is 'sample' the executable produced by the compiler? is /media/stuff4 a FAT or NTFS formatted external device (like a USB stick)? if so then even if you have write permissions, Linux **execute** permissions aren't going to work on it (at least not easily). For that reason alone you should do all your compiling inside your home dir.

---

### Post by abhayaasp on 2013-09-25
I have tried to debug the "sample.c" with codeblocks and when i debug by saving it in home directory, it works fine but when trying to compile from that location of the harddisk, it gives the respective error. Is there any way to debug the program from that respecitve location????

---

### Post by abhayaasp on 2013-09-25
I am trying to debug from the codeblocks and it works fine when trying to compile in the home directory. But it gives the respective mentioned problem when trying to debug from that location of the hard-disk. Is there any way out to debug from that location with the help of the codeblocks or the terminal command is only way to resolve that type of stuff? To much curious to know.

---

### Post by abhayaasp on 2013-09-25
I searched these stuff over net and i can create the directory but as i am in the begineer stage in the ubuntu , i can't path to the respective location and [COLOR=#000000]stuff4 is the partionized part of the hard-disk. Plz, how we need to path it. [/COLOR]

---

