---
title: "Buffered input and CTRL+D"
date: 2010-02-07
forum: Programming Talk
---

### Post by u.user on 2010-02-07
Hello all.

I was running this simple C code in ubuntu 9.10

```


#include <stdio.h>

int main(void){
    char c;
    
    while((c=getchar())!=EOF)
    putchar(c);
    
    return 0;
}

```

When I input a word, like test for exmple and press CTRL-D, it gets automatically outputed like 

(what happens in console, italic is the output)
```

$./test
test<CTRL+D>*test*

123<ENTER>
*123*
<CTRL+D>
*PROGRAM EXITS*

```

My question is, knowing that getchar() uses buffer, meaning, all what is input will be available to it after pressing ENTER, why is it that when i type test<CTRL+D> without pressing enter i get test as output and i can continue inputting... so what is CTRL+D doing here?  Also when i just press CTRL+D when there is no input before it, it is exitting. Can someone please explain what is happening?

Thank you

---

### Post by nvteighen on 2010-02-07
What's happening is exactly what you've described: You're suffering from buffering :p The variable c isn't filled with anything before \n... and Ctrl+D is sending an EOF to stdin, interrupting the stream, but leaving it incomplete. The output you get instead is because the loop starts again and stdin still holds stuff, so that stuff gets into c... and as no \n is encountered, stdin asks for more.

I can't think of a trivial way to make Ctrl+D be recognized as soon as typed without using signals or ncurses.

---

### Post by The Cog on 2010-02-07
As nvteighen says, Ctrl-D is sending an EOF (End Of File) to the program, causing it to read what's in the buffer and then exit because there's no more input.

It is the terminal handler that does this interpretation of Ctrl-D into EOF, and it can be configured with the command **stty** if you want (use **man stty** to see details).

---

