---
title: "Code::Blocks 8.02 help can't compile anything"
date: 2008-07-25
forum: Programming Talk
---

### Post by benzi on 2008-07-25
I am a new Linux(Hardy) user and also a beginner in coding. I dled Code::Blocks 8.02 but have been unable to compile anything at all using it. Currently I still do not have g++ installed but even building a C code in Code::Blocks failed.

```
#include <stdio.h>
#include <stdlib.h>

int main()
{
    printf("Hello world!\n");
    return 0;
}
```

I get:
[COLOR="Red"]error: stdio.h: No such file or directory
error: stdlib.h: No such file or directory[/COLOR]

Really a noob question but really need help.

Thank you very much.

---

### Post by Zugzwang on 2008-07-25
Read the stickies about compiling your first C program. Although you are using an IDE, you still have to follow the instructions for the first time.

---

### Post by Frederick J. Harris on 2008-07-25
I just discovered Code::Blocks yesterday and installed it for Windows.  I had been using Dev C++ for a lot of the C/C++ coding I do, but the Code::Blocks looks pretty neat.  I havn't installed it yet under Linux, but there is a footnote there about having to add some additional repositories to your sources.lst file.  Also, you need for sure to have the build-essential package installed because all the libraries and utilities are in there.  I don't know whether or not the Ubuntu download of Code::Blocks would install that stuff.  This is the first time I've ever saw a download package for a Linux/Ubuntu program seperate from the 'repositories' concept? (I'm rather new to Linux too).

---

### Post by WW on 2008-07-25
benzi: Follow the instructions in "Step 0" [here](http://ubuntuforums.org/showthread.php?t=689635).  (This is what  "Read the stickies..." means.)

---

### Post by Frederick J. Harris on 2008-07-25
You could test whether you have build essential installed by trying to compile your Hello, World! program in the terminal.
If the name of the file is HelloWorld.c this is the syntax...


gcc HelloWorld.c  -o HelloWorld

You could put it in your /home directory, open Terminal to there, and run the above.  To run the program type...

./HelloWorld [ENTER]

if it compiles.

---

