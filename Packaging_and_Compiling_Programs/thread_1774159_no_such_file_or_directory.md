---
title: "no such file or directory"
date: 2011-06-02
forum: Packaging and Compiling Programs
---

### Post by jon zendatta on 2011-06-02
Hi all. I've downloaded a file, which now resides in Desktop.Then did this
[PHP]~/Desktop$ tar -xzvf CrackWiFiMachine6-program.tar.gz
tar (child): CrackWiFiMachine6-program.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
[/PHP]
Ah so what does that error message mean?:KS

---

### Post by SevenMachines on 2011-06-03
Not really the right forum for this, you might want to 'report abuse' and get them to move it to another forum. But... assuming you actually have the filename right? Case and all? Because the error means it doesnt exist :)
Try,
>  $ ls -al ./
I've seen things where a *badly* corrupted filesytem can show the file from one point of view but think it doesnt exist from another but only very, very rarely.

---

### Post by jon zendatta on 2011-06-03
okay so originally i got file name wrong.
[PHP]~/Desktop$ ls 
CrackWiFiMachine6 - program.tar.gz
j0n@j0n-Aspire-5740:~/Desktop$ tar -xzvf CrackWiFiMachine6 - program.tar.gz
tar (child): CrackWiFiMachine6: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now[/PHP]:KS
and same error message

---

### Post by SevenMachines on 2011-06-03
Spaces would need to be escaped, they separate file names as far as the command line is concerned so you need to tell it that they dont in this case and that its one filename
```
 $ tar  -zvxf CrackWiFiMachine6\ -\ program.tar.gz
```

Note that pressing tab having typed a partial file or command name, or these days even command arguments, autocompletes these things and make this all a lot easier

---

