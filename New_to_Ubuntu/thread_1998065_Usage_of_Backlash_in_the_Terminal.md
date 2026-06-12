---
title: "Usage of Backlash in the Terminal"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by prasanmouli on 2012-06-06
[FONT=Comic Sans MS]Hello! I am new to Linux and am getting used to working in the shell. I wanted to install the Gnu Compiler Collection and had planned on using the following commands to get it running.[/FONT]
[FONT=Courier New][SIZE=2]$ ./configure --prefix=/usr/local/AVR [COLOR=Red]\[/COLOR] 
        --target=avr --enable-languages="c,c++" [COLOR=Red]\[/COLOR]         
--disable-nls 
$ make 
# make install[/SIZE][/FONT]
[FONT=Comic Sans MS]
[/FONT][FONT=Century Gothic][FONT=Comic Sans MS]But I couldn't quite understand the function of the backslashes ('\'-marked them red here)[/FONT][COLOR=Black][FONT=Comic Sans MS].
This is what it typed in the terminal
[/FONT]
[FONT=Courier New][SIZE=2]prasan@ubuntu:~/Downloads/gcc-4.7.0$ ./configure --prefix=/usr/local/AVR \
> --target=avr --enable-languages='c,c++" \
> --disable-nls[/SIZE][/FONT]
[FONT=Courier New]>[/FONT]

1. Is this right?
[FONT=Comic Sans MS]2. If so, can someone please tell me how to complete this set of instructions so that I could run configure file?[/FONT]
(This '>' keeps coming as I return signaling that I haven't terminated the command properly)
[/COLOR]
[/FONT]

---

### Post by codemaniac on 2012-06-06
Shell treats backslash '\' as escape character ,that means whatever you type just after the '\' character will be ignored by the shell .
In your example to make the long commandline more readable , it has been split into several lines .So the return character just typed after the '\' has been ignored and the shell awaits for further input from the user .

[http://steve-parker.org/sh/escape.shtml](http://steve-parker.org/sh/escape.shtml)

---

### Post by 3v3rgr33n on 2012-06-06
Suppose you accidentally type it.. for instance ; you type
```
ls \
```
The shell will wait for more input, how do escape from that because I normally press Cntrl-C

---

### Post by prasanmouli on 2012-06-06
Thank You! Got it running now!

---

