---
title: "1st program in FASM with Ubuntu"
date: 2009-02-17
forum: Programming Talk
---

### Post by Jack Shankle on 2009-02-17
I have downloaded the FASM Compiler and uncompressed it to:
places/home/jack/fasm. The program is in places/home/jack/fasmjps.asm and is
a file not a folder. I want to compile fasmjps.asm and put the result in 
A1stprog. Nothing I have tried works. A 10 minute task is taking many hours
with no success. 
Thanks for any help.

2% ubuntu working on 3%

---

### Post by Caduceus on 2009-02-17
Might be a good idea to see whether you've installed the compiler correctly, I don't think sticking it in a folder works properly

---

### Post by jimi_hendrix on 2009-02-17
is there a man fasm?

---

### Post by Jack Shankle on 2009-02-17
If I don't put it in that folded then it would go into a folder I have called "mydownload". That is a place I download all programs.

I have no idea what a man fasm version is.

Also I've been reading about command line entries. How do I do that in Ubuntu/fasm????

Thanks for any help.

2% Ubuntu working on 3%

---

### Post by NathanB on 2009-02-17
Assuming you've D/Led fasm into your home folder, then this...

[php]cd ~
tar xzvf fasm-1.67.32.tgz[/php]

...will unpack it.

Now try this:

[php]cd fasm
./fasm ~/fasm/examples/elfexe/hello.asm hw[/php]

Now you can run the program with:
[php]./hw
[/php]

More information here:

[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

---

### Post by Jack Shankle on 2009-02-18
Thanks NathanB. 
The link you provided is a gold mine. I'll be chewing on that one for
quite awhile. If you know of any other goodies like that, I would appreciate your telling me in this thread. I had no idea it even existed. People have to understand that those coming from Windows have an awful learning curve to tackle. My long term habits are messing me up in Ubuntu. 
I will delete all my attempts at FASM and redo everything according 
to your instructions and see how I do then.

2% Ubuntu working on 3%
Maybe not even that much.

---

### Post by NathanB on 2009-02-19
[https://help.ubuntu.com/](https://help.ubuntu.com/)

[http://tldp.org/](http://tldp.org/)

---

