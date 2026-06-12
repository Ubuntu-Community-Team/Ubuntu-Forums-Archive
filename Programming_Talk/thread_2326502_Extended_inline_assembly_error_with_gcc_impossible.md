---
title: "Extended inline assembly error with gcc: impossible constraints"
date: 2016-06-01
forum: Programming Talk
---

### Post by Ayush_Agrawal on 2016-06-01
[FONT=-moz-fixed]The other day I was reading a document about inline assembly  ([http://www.delorie.com/djgpp/doc/brennan/brennan_att_inline_djgpp.html](http://www.delorie.com/djgpp/doc/brennan/brennan_att_inline_djgpp.html)).

I got  stuck at the rep_movsl code. I tried running it on my PC. At first I got  no error when it was the only thing in the code. But when I tried to  actually use it, the compiler complained "‘asm’ operand has impossible  constraints". 

I am unable to figure out my way. I have already googled about it, but  all vain. 

I was wondering if there was something wrong with my compiling command.  All I am using is "gcc code.c". 

I would be great if anyone could look at my code (below) and help me out. 

Thnx. 

```
#include <stdio.h>

#define rep_movsl(src, dest, numwords) \
__asm__ __volatile__ ( \
  "cld\n\t" \
  "rep\n\t" \
  "movsl" \
  : : "S" (src), "D" (dest), "c" (numwords) \
  : "%ecx", "%esi", "%edi" )

int main(int argc, char const *argv[])
{
    int arr1[4] = {1, 2, 3, 4};
    int arr2[4];
    
    rep_movsl(arr1, arr2, 4);
    
    int i;
    for(i=0;i<4;++i)
        printf("%d ",arr2[i]);
    return 0;
}
```
[/FONT]

---

