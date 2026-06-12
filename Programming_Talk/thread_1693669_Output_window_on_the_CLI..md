---
title: "Output window on the CLI."
date: 2011-02-23
forum: Programming Talk
---

### Post by madhater on 2011-02-23
I use the CLI for writeing and compileing my programs. I use vim and gcc. For some reason I have not yet found, when I execute my most resunt programs, the output is put before the next prompt, e.g lke this: 

"Hello, World" james@larry-desktop$: 

This did not use to happen. It used to output like this: 


"Hello, Wolrd" 

james@larry-desktop$: 

This is the code for a program which otputs how it used to:

#include <stdio.h> 

int main()

{

printf( "Hello, World" );

}

My other example programs output in the first manner. Why????

Sorry the code looky bad, but my brother is bugging me to get of.

---

### Post by cthulhu_54 on 2011-02-23
Could be a problem/change in your Bash instance? Made any changes to .bashrc lately?

---

### Post by Arndt on 2011-02-23
> **madhater said:**
> I use the CLI for writeing and compileing my programs. I use vim and gcc. For some reason I have not yet found, when I execute my most resunt programs, the output is put before the next prompt, e.g lke this: 

"Hello, World" james@larry-desktop$: 

This did not use to happen. It used to output like this: 


"Hello, Wolrd" 

james@larry-desktop$: 

This is the code for a program which otputs how it used to:

#include <stdio.h> 

int main()

{

printf( "Hello, World" );

}

My other example programs output in the first manner. Why????

Sorry the code looky bad, but my brother is bugging me to get of.

Try with a newline at the end of the string: "Hello, World\n"

---

### Post by madhater on 2011-02-23
Thanks for replying qiuckly. I have not made any changes to my .bashrc file. Your sugested fix worked. Thanks one again.

---

