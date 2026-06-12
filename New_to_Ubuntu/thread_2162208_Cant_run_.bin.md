---
title: "Cant run .bin"
date: 2013-07-13
forum: New to Ubuntu
---

### Post by tsi25 on 2013-07-13
Alright so I've looked around online and it seems that if i run chmod +x file-name.bin followed by sudo ./file-name.bin (where ./ is the path) then it will run the .bin. Ive tried this and it just says "command file-name.bin not found" as an error in the terminal. Am i missing some piece of software that would let me run a .bin? am i trying to use the wrong command?

im on linux ubuntu 12.04 64bit on a system 76 laptop - lemur ultra.

---

### Post by oldos2er on 2013-07-13
Are you sure you need "sudo"? 

You need to be in the same folder where the *.bin file is to run those commands.

---

### Post by tsi25 on 2013-07-13
running it without sudo yields the same error, command not found. the .bin file is in a folder - call it folder-name on my desktop. ive changed directories to "name@name-Lemur-Ultra:~/Desktop/folder-name $" so im pretty sure im in the right folder.

---

### Post by The Cog on 2013-07-13
Linux is case sensitive. Maybe that's the problem?

When in that directory, can you do
```
ls -l
./filename.bin
```
and post the results (both the commands you typed and the results) here. It's got to be something simple but we need to see exactly what files are there and what you are typing.

---

### Post by tsi25 on 2013-07-13
tsi25@tsi25-Lemur-Ultra:~/Desktop/Black  and White 2$ twk-bw2a.bin
twk-bw2a.bin: command not found
tsi25@tsi25-Lemur-Ultra:~/Desktop/Black  and White 2$ ls -l
total 2935428
-rw-r--r-- 1 tsi25 tsi25      5590 Jul 12 12:31 Serial.nfo
-rwxrwxrwx 1 tsi25 tsi25 788886672 Jul 12 13:44 twk-bw2a.bin
-rw-r--r-- 1 tsi25 tsi25 782206992 Jul 12 13:44 twk-bw2b.bin
-rw-r--r-- 1 tsi25 tsi25 782206992 Jul 12 13:44 twk-bw2c.bin
-rw-r--r-- 1 tsi25 tsi25 652501248 Jul 12 13:44 twk-bw2d.bin
tsi25@tsi25-Lemur-Ultra:~/Desktop/Black  and White 2$ 


i hope its something simple.

---

### Post by The Cog on 2013-07-13
> i hope its something simple.
I think it is.
The command you need to enter is
```
./twk-bw2a.bin
```
Note the "./" on the front.

Normally, in Linux (and *nix in general), the current directory is not in your search path (a security thing), so you need to put the ./ on the front to say where to find the command you want to run.

---

### Post by tsi25 on 2013-07-13
tsi25@tsi25-Lemur-Ultra:~/Desktop/Black  and White 2$ ./twk-bw2a.bin
bash: ./twk-bw2a.bin: cannot execute binary file
tsi25@tsi25-Lemur-Ultra:~/Desktop/Black  and White 2$ sudo ./twk-bw2a.bin
[sudo] password for tsi25: 
./twk-bw2a.bin: 1: ./twk-bw2a.bin: Syntax error: "&" unexpected (expecting ")")
tsi25@tsi25-Lemur-Ultra:~/Desktop/Black  and White 2$ 

here are the results of that.

---

### Post by Impavidus on 2013-07-13
Adding sudo usually only helps against the "permission denied" message. Even then, only prepend it when you know why.

Can you try```
file twk-bw2a.bin
```That will show us what kind of file this really is. Extensions don't say a lot on Linux systems. It seems the system doesn't know how to execute it.

---

### Post by tsi25 on 2013-07-13
tsi25@tsi25-Lemur-Ultra:~/Desktop/Black  and White 2$ file twk-bw2a.bin
twk-bw2a.bin: data
tsi25@tsi25-Lemur-Ultra:~/Desktop/Black  and White 2$ 

any ideas?

---

### Post by Impavidus on 2013-07-13
This file is not a Linux executable. If there is some kind of interpreter that can run the file, Ubuntu doesn't know which one. Does this file come from a different kind of system? Windows, Mac? Then you may be out of luck. There may be several file formats with the .bin extension, but this one isn't simply executable on Linux.

---

### Post by monkeybrain2012 on 2013-07-13
Just did a google search, your file is apparently from a Mac game, won't run in Linux.
[http://en.wikipedia.org/wiki/Black_%26_White_2](http://en.wikipedia.org/wiki/Black_%26_White_2)

---

