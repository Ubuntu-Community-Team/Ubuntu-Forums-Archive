---
title: "Code:Blocks syntax error"
date: 2014-01-23
forum: Programming Talk
---

### Post by toaster3 on 2014-01-23
I am doing some *very* basic coding in C using code blocks. I kept running into a syntax error, even on something as fundamental as a hello, world:

#include <stdio.h>

main ()

{

    printf("tests");
    return 0;

}

I compile it, change permission on the file, and get this error:

 syntax error: *word unexpected* (*expecting* ")"

Some poking around indicates this may arise from choosing the wrong compiler-- I chose the GNU GCC Compiler.

 I am running Ubuntu 13.10
Processor : Intel® Core™ i5-4200M CPU @ 2.50GHz × 4 
OS type : 64 bit

Can anyone point me in the right direction? I'm stumped.

---

### Post by nidzo732 on 2014-01-23
Could you post the exact steps you used to compile your program, you might be trying to run the wrong file.
Usually you do it like this: 
```

gcc file.c -o executable
./executable

```
Or why don't you just run it from codeblocks, it does these things automatically. 
Also, main should return int, so you should use
```

[COLOR=#000000]#include <stdio.h>[/COLOR]

[COLOR=#000000]int main ()[/COLOR]

[COLOR=#000000]{[/COLOR]

[COLOR=#000000]printf("tests");[/COLOR]
[COLOR=#000000]return 0;[/COLOR]

[COLOR=#000000]}[/COLOR]

```
in your code

---

### Post by ofnuts on 2014-01-23
Works for me with GCC. It could be some invisible control character(s) (your code has  a rather unusual formatting, with a lot of spaces and line feeds).

---

### Post by toaster3 on 2014-01-23
> **nidzo732 said:**
> Could you post the exact steps you used to compile your program, you might be trying to run the wrong file.
Usually you do it like this: 
```

gcc file.c -o executable
./executable

```
Or why don't you just run it from codeblocks, it does these things automatically. 
Also, main should return int, so you should use
```

[COLOR=#000000]#include <stdio.h>[/COLOR]

[COLOR=#000000]int main ()[/COLOR]

[COLOR=#000000]{[/COLOR]

[COLOR=#000000]printf("tests");[/COLOR]
[COLOR=#000000]return 0;[/COLOR]

[COLOR=#000000]}[/COLOR]

```
in your code

I have been using code blocks to compile/run. Basically, I build it, then I have to change permission on the file (code blocks doesn't seem to make it executable), then run it. When I run it (using code blocks) I get that error. 

When I added int, it says Syntax error "(" unexpected. The maddening thing here is that it compiles, or appears to. I get this error when running.

---

### Post by nidzo732 on 2014-01-23
Could you run it from the terminal like I wrote above (the first code). Replace "file.c" with the name of your file.
If it goes wrong, post the entire contents of the terminal here.

---

### Post by toaster3 on 2014-01-23
> **nidzo732 said:**
> Could you run it from the terminal like I wrote above (the first code). Replace "file.c" with the name of your file.
If it goes wrong, post the entire contents of the terminal here.

Here's when I get:

```

toddbert@toddbert-ubuntu:~/Documents$ ./Testicles
./Testicles: line 2: syntax error near unexpected token `('
./Testicles: line 2: `int main ()'
```

(yes, I am two years old with the filenames)

I feel this is some thing I am missing with setup or permissions or something weird like that. This progam is simply too simple to not 'just work'.

---

### Post by steeldriver on 2014-01-23
it looks like you made the ***source code*** file executable, and tried to run that

---

### Post by toaster3 on 2014-01-23
> **steeldriver said:**
> it looks like you made the ***source code*** file executable, and tried to run that


Ok, forgive me a little here, but what is Code Blocks meant to spit out when you hit 'compile and run'? Where is the acutal executable file meant to end up? I'm literally building a single file (there's no project or anything fancy here). This is making me feel incredibly dippy, as 'hello world' should just sort of run, shouldn't it?

---

### Post by nidzo732 on 2014-01-23
The executable is in PROJECT_FOLDER/bin/Debug.
You're not supposed to run the source code itself.
You can compile the source manually, without codeblocks
```

cc Testicles.c -o Testicles 
./Testicles

```

---

### Post by toaster3 on 2014-01-23
> **nidzo732 said:**
> The executable is in PROJECT_FOLDER/Bin/Debug.
You're not supposed to run the source code itself

Then there is no executable:

/home/toddbert/Documents
toddbert@toddbert-ubuntu:~/Documents$ ls
Testicles
toddbert@toddbert-ubuntu:~/Documents$ 

So it's obviously failing to compile, period.

Ok. It compiles outside of Code Blocks:

```
toddbert@toddbert-ubuntu:~/Documents$ cc Testicles.c -o Testicles
toddbert@toddbert-ubuntu:~/Documents$ ./Test
bash: ./Test: No such file or directory
toddbert@toddbert-ubuntu:~/Documents$ ./Testicles
Test 
```


So, hooray. As to why it won't compile and run IN Code Blocks, well, that's a bit of a quandary. Furthermore, if I name the file <filename>.c in Code Blocks, the 'build' toolbar is greyed out. If I name it <filename> with no extension, it is there.

Looks like I have some more reading to do about Code Blocks, I guess. Unless somone here has a quick answer to that question, I thank everyone for making my first question here a pleasant one.

---

### Post by spjackson on 2014-01-23
Too Slow - deleted.

---

### Post by nidzo732 on 2014-01-23
What is the name of your source file, it should have a ".c" extension if it is a C language file.

---

### Post by toaster3 on 2014-01-23
> **nidzo732 said:**
> What is the name of your source file, it should have a ".c" extension if it is a C language file.

Wow, this moves fast! Sorry, see my answer above.

This was a combination of settings issues, and attempting to figure out new software at 2AM. Thanks again for the quick answers. Hopefully, I can return the favor sometime soon!

---

