---
title: "EOF (stdin) in Ubuntu 10.04 Lucid Lynx"
date: 2011-07-30
forum: Programming Talk
---

### Post by gnometorule on 2011-07-30
A friend learning C using KR asked me a question that pointed out a behavior that confuses me too. When going over the early book examples (e.g., ch. 1.5.1) in which you just mirror input and output such as (straight from book)....

```

#include <stdio.h>

main(){

   int c;
   
   while ( (c = getchar()) != EOF)
      putchar(c);

}

```...you need to hit twice ^d to get out of the loop. The effect is as if one ^d only was hit. Any explanations?

---

### Post by Bachstelze on 2011-07-30
I only need to hit ^D once here... But the behavior of hitting ^D may differ in different terminal emulators or even different shells. Contrary to popular belief, ^D *does not* send EOF.

---

### Post by gnometorule on 2011-07-30
Ah. So it could be just a terminal emulation oddity that one, for practical purposes, accepts and ignores? Or is there another way to communicate 'EOF' to a stdin stream?

---

### Post by papibe on 2011-07-30
Does it get stuck if you use files? Something like this:
```
./yourprogram < afile > otherfile
```
Regards.

---

### Post by Bachstelze on 2011-07-30
Basically, you do not "communicate" EOF to the process: EOF is by definition not a character, it is the name given to the value getchar will return when it can't read any character. So anything that causes the input to stop will make getchar return EOF.

---

### Post by gnometorule on 2011-07-30
Good idea. Your piping suggestion copies the input file perfectly fine to the output file. 

I played with it more on my Toshiba (grub Ubuntu/W7), and also under Lucid Lynx. For stdin, the behavior in slightly more involved (slightly) programs playing with stdin gets weird while more or less on target. 

In sum, I take it as a terminal emulation quirk in this setup affecting only stdin, and am fine with it?

---

### Post by gnometorule on 2011-07-30
@ Bachstelze (nice name, I'm German too while living away from home)

I don't understand how or if that explains an answer to my question though. If it does, kindly try again.

---

### Post by Bachstelze on 2011-07-30
> **gnometorule said:**
> 
In sum, I take it as a terminal emulation quirk in this setup affecting only stdin, and am fine with it?

Probably. When you use a file as input it's simple: the output ends when all the characters in the file have been read, so there is no ambigity as to when getchar will return EOF. When you're reading from a terminal, however, it basically depends on when exactly your terminal "cuts" the input stream. It rarely really matters, though, whether you have to press ^D once or twoce.

---

### Post by gnometorule on 2011-07-30
Thanks everyone. Closing this now.

---

### Post by Arndt on 2011-07-30
> **gnometorule said:**
> Thanks everyone. Closing this now.

Sorry for continuing a closed thread, but I think the situation when you have to type ^D twice is when you did not just enter a newline.

Also, I think it's the terminal (pty) driver that has this behaviour, not the terminal emulator. It may be documented in some manual page in section 7.

---

