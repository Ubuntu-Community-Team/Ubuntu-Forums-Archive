---
title: "[SOLVED] fgets in C seems to act a bit wierd"
date: 2008-11-22
forum: Programming Talk
---

### Post by PmDematagoda on 2008-11-22
I'm using fgets to read the contents of a file line-by-line, this is the code:-
```
#include<stdio.h>
#include<string.h>

main(void){

  FILE *in , *out;
  char Names[10][17], temp[2];
  int NP;

  in = fopen("greedy.in","r");
  out = fopen("greedy.out","w");

  NP = atoi(fgets(temp, 2, in));
  int i;
  for (i = 0 ; i < NP +1 ; i++){
  fgets(Names[i], sizeof Names  , in);

  /* if (strlen(Names[0])== 1 ){ 
i = 0;
  } */
  }

}
```

Now the problem I get is that although the first fgets works properly, the next fgets code takes the 1st line again and not the 2nd as it should. Is there something wrong in what I am doing above?

Thanks in advance.

---

### Post by PmDematagoda on 2008-11-22
Ok, I figured it out(I know, it's stupid:-P), it seems that I must use the same range between all uses of fgets, however, something I cannot get is as to why it is like this, can anyone enlighten me on this? 

Thanks!

---

### Post by Tony Flury on 2008-11-22
1 problems i can spot : 

 your code is not reading to the end of the line - you only read two characters off the first line - but actually the first line might have more than two characters on it when you include the "\n" that is included by definition at the end of each line. Your code seems to assume that fgets automatically read the whole line, and just give you the first n bytes, and then throws the rest of the line away - that is not the case - it provides the next n bytes - off the same line if there is still characters left.

---

### Post by PmDematagoda on 2008-11-22
> **Tony Flury said:**
> 1 problems i can spot : 

 your code is not reading to the end of the line - you only read two characters off the first line - but actually the first line might have more than two characters on it when you include the "\n" that is included by definition at the end of each line. Your code seems to assume that fgets automatically read the whole line, and just give you the first n bytes, and then throws the rest of the line away - that is not the case - it provides the next n bytes - off the same line if there is still characters left.

Thanks for the explanation, that made me understand my mistake completely:).

---

### Post by Sockerdrickan on 2008-11-22
also don't write your code like main (void) write it like this: int main() or int main(int argc, char **argv)

---

