---
title: "File not recognised? .bin?"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Ph4nt0mOMG on 2008-05-16
Hello
I'm new to Linux (and Ubuntu). I got it a day ago for a spare PC I had lying around to try and host up a source server on. Everything is fine, I'm slowly learning Terminal, but no matter what I try and which tutorial i read, nothing helps me to open the damn file.

This is what I'm typing into Terminal.
> sam@sam-linux:~/Desktop$ ls
hldsupdatetool.bin
sam@sam-linux:~/Desktop$ chmod +x hldsupdatetool.bin
sam@sam-linux:~/Desktop$ sudo ./hldsupdatetool.bin
sudo: unable to execute ./hldsupdatetool.bin: No such file or directory

Why does it say it isn't there when it blatantly is? Help greatly appreciated.

---

### Post by robalcorn on 2008-05-16
the file may not be executable try right clicking on it go to the tab that says permissions and click on exectuable than try again.

---

### Post by Ph4nt0mOMG on 2008-05-16
Ah yes, I forgot to say I did that too. But surely it would still find it even if it wasn't executable.

---

### Post by bumanie on 2008-05-16
You may not have installed build-essential yet which is a c compiler and necessary to install some programs from source.
> sudo apt-get install build-essential Even if this doesn't sort out your present problem, it is important to have build-essential.

---

### Post by StOoZ on 2008-05-16
> **Ph4nt0mOMG said:**
> Hello
I'm new to Linux (and Ubuntu). I got it a day ago for a spare PC I had lying around to try and host up a source server on. Everything is fine, I'm slowly learning Terminal, but no matter what I try and which tutorial i read, nothing helps me to open the damn file.

This is what I'm typing into Terminal.

Why does it say it isn't there when it blatantly is? Help greatly appreciated.

whats the output of:
> file hldsupdatetool.bin


---

### Post by robalcorn on 2008-05-16
Try this

chmod +x hldsupdatetool.bin 

./hldsupdatetool.bin

---

### Post by Ph4nt0mOMG on 2008-05-16
file hldsupdatetool.bin returns:
> sam@sam-linux:~/Desktop$ file hldsupdatetool.bin
hldsupdatetool.bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), stripped


Robalcorn, I get
> sam@sam-linux:~/Desktop$ chmod +x hldsupdatetool.bin
sam@sam-linux:~/Desktop$ ./hldsupdatetool.bin
bash: ./hldsupdatetool.bin: No such file or directory


I'm gonna install build essential, ill get back once its done.

EDIT: 
> sam@sam-linux:/$ sudo apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential

Hmm.... Maybe ill find it in add programs.

---

### Post by robalcorn on 2008-05-16
build-esential can be found under Synaptic.

---

### Post by mkoehler on 2008-05-16
Robalcorn, apt-get = same repos as synaptic.  Personally, I'd go into synaptic and make sure that you have all of the repositories enabled, then do a "sudo apt-get update" and "sudo apt-get install build-essential".  However, having this package shouldn't make much of a difference in your situation.  I would probably rename the file (take of the .bin part...we all know that it's supposed to be a bin file), check the permissions using "ls -l", and if all checks out, try running "./hldsupdatetool"

---

### Post by mkoehler on 2008-05-16
Also, if it's a shell script, as I'm guessing it might be (check the first like of the file using "cat <filename>".  If that first like says #!/bin/sh, then it wouldn't hurt to try running

```
sudo sh ./<filename>
```

Cheers!

---

