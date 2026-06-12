---
title: "is a goto the only sane solution here?"
date: 2009-12-23
forum: Programming Talk
---

### Post by monkeyking on 2009-12-23
Hi i'm trying to parse a huge chunk of data represented as char string using strtok.
The first call to strtok should be with the chararray, and all subsequent with NULL, by the strtok documentation.

So If I want to avoid copying code, or doing a comparison for each iteratation isn't the following with a goto the smartest?

[PHP]
//with a goto, looks like the best solution
int main(){

  const char* str1 = "1 2 junk\n3 4 junk\n5 6 \n\0";
  char *str = strdup(str1);
  char *a,*b,*ret;

  a = strtok(str," ");
  goto myFirstGoto;

  while((ret=strtok(NULL,"\n"))!=NULL){
    a=(strtok(NULL," "));
  myFirstGoto:
    b=(strtok(NULL," "));
    fprintf(stdout,"a=%s\tb=%s\n",a,b);

  }
  return 0;
}
[/PHP]

as opposed to copying the contents of the loop

[PHP]
int main(){

  const char* str1 = "1 2 junk\n3 4 junk\n5 6 \n\0";
  char *str = strdup(str1);
  char *a,*b,*ret;

  a = strtok(str," ");
  b = strtok(NULL," ");
  fprintf(stdout,"a=%s\tb=%s\n",a,b);
  
  while((ret=strtok(NULL,"\n"))!=NULL){
    a=(strtok(NULL," "));
    b=(strtok(NULL," "));
    fprintf(stdout,"a=%s\tb=%s\n",a,b);

  }
  return 0;
}
[/PHP]

as opposed to using a conditional that needs to be checked for each iteration.

[PHP]
int main(){

  const char* str1 = "1 2 junk\n3 4 junk\n5 6 \n\0";
  char *str = strdup(str1);
  char *a,*b,*ret;
  int firstRun = 1;
  
  while((ret=strtok(NULL,"\n"))!=NULL){
    if(firstRun){
      a=(strtok(str," "));
      firstRun = 0;
    }else
      a=(strtok(NULL," "));
    b=(strtok(NULL," "));
    fprintf(stdout,"a=%s\tb=%s\n",a,b);

  }
  return 0;
}
[/PHP]

I think this is the first case I've ever come across where a goto is the best solution.

Can anyone come up with better solution,
and btw dont recommend std::string or boost.
I want to keep this lowlevel and fast.

---

### Post by falconindy on 2009-12-23
A do-while loop is what you're looking for. Something like:
```
#include <stdio.h>
#include <string.h>

int main(){ 

  const char* str1 = "1 2 junk\n3 4 junk\n5 6 \n\0"; 
  char *str = strdup(str1); 
  char *a,*b,*ret; 

  a = strtok(str," "); 

  do{ 
    a=(strtok(NULL," ")); 
    b=(strtok(NULL," ")); 
    fprintf(stdout,"a=%s\tb=%s\n",a,b); 
  } while((ret=strtok(NULL,"\n"))!=NULL);
  return 0; 
} 
```
I realize this isn't perfect, but you really should **never** need to use a goto.

---

### Post by kwyto on 2009-12-23
what do you need **char * ret **for?
look at this definition and example: [http://www.cplusplus.com/reference/clibrary/cstring/strtok/](http://www.cplusplus.com/reference/clibrary/cstring/strtok/)
 
also, strtok moves automatically the position of its pointer every time its called 
for example str = "0_1_2_3_4_5", underscore means blank space
myStr = strtok(str, " "); //after this call str = "1_2_3_4_5" , myStr = "0"

---

### Post by monkeyking on 2009-12-23
thanks people,

the do-while example is less than perfect because it will call strtok twice before reaching the b=strtok in the first iteration.

As with the 'char *ret',
you are right it could be avoided
doing a 
[PHP]
while(strtok(NULL,"\n")!=NULL){
...
} 
[/PHP]
But I like keeping the returnvalues, in case i need to debug.

I do know how strtok works, I also know that it moves the pointer to the next element.
But how does that explain how to avoid the first call with the string itself, without doing any tokenization.

I wonder how many people that has actually read the dijkstra paper on the "dont goto".

I think this code example justifies a goto, that is until I see a better codeexamples that solves the problem

thanks

---

### Post by PmDematagoda on 2009-12-23
Personally, I don't really like a goto, even though it has it's uses, it still has the potential to cause some confusion(which I definitely got in the code example provided). You can use a for loop for this, albeit it isn't that perfect either:-
```
#include <stdio.h>
#include <string.h>

int main(){

  const char* str1 = "1 2 junk\n3 4 junk\n5 6 \n\0";
  char *str = strdup(str1);
  char *a,*b,*ret;

  for (a = strtok (str, " "),
	 b = strtok (NULL, " ");
       strtok (NULL, "\n") != NULL;
       a = strtok (NULL, " "),
	 b = strtok (NULL, " "))
    fprintf (stdout, "a=%s\tb=%s\n", a, b);

  fprintf (stdout, "a=%s\tb=%s\n", a, b);

  return 0;
}
```
I realise that at first, it may be a little confusing, but at the end it really isn't. :)

---

### Post by monkeyking on 2009-12-23
> **PmDematagoda said:**
> Personally, I don't really like a goto, even though it has it's uses, it still has the potential to cause some confusion(which I definitely got in the code example provided). You can use a for loop for this, albeit it isn't that perfect either:-
```
#include <stdio.h>
#include <string.h>

int main(){

  const char* str1 = "1 2 junk\n3 4 junk\n5 6 \n\0";
  char *str = strdup(str1);
  char *a,*b,*ret;

  for (a = strtok (str, " "),
	 b = strtok (NULL, " ");
       strtok (NULL, "\n") != NULL;
       a = strtok (NULL, " "),
	 b = strtok (NULL, " "))
    fprintf (stdout, "a=%s\tb=%s\n", a, b);

  fprintf (stdout, "a=%s\tb=%s\n", a, b);

  return 0;
}
```
I realise that at first, it may be a little confusing, but at the end it really isn't. :)

Cheers :)

It was a construct like this I was looking for. I hadn't thought about wrapping it up in a for loop.

Thanks!

---

### Post by dwhitney67 on 2009-12-23
@ MonkeyKing -

Any reason why you chose to read/obtain your data in multi-line chunks versus just reading one line at a time?

Anyhow, here's a simple working solution based on the summary you provided earlier.
```

#include <string.h>
#include <stdlib.h>
#include <stdio.h>

int main()
{
   const char* str      = "1 2 junk\n3 4 junk\n5 6 \n\0";
   char*       dupstr   = strdup(str);
   char*       pdata    = dupstr;

   while (pdata && *pdata != '\0')
   {
      char* nd = 0;
      char* a  = strtok_r(pdata, " ",  &nd);
      char* b  = strtok_r(nd,    " ",  &nd);

      printf("a = %s, b = %s\n", a, b);

      char* nl = strchr(nd, '\n');
      pdata = ++nl;
   }

   free(dupstr);

   return 0;
}

```
Note how I elected to use strtok_r(), and when I conclude the loop, I free the original value that was returned from strdup().

---

### Post by monkeyking on 2009-12-26
> **dwhitney67 said:**
> @ MonkeyKing -

Any reason why you chose to read/obtain your data in multi-line chunks versus just reading one line at a time?

Anyhow, here's a simple working solution based on the summary you provided earlier.
```

#include <string.h>
#include <stdlib.h>
#include <stdio.h>

int main()
{
   const char* str      = "1 2 junk\n3 4 junk\n5 6 \n\0";
   char*       dupstr   = strdup(str);
   char*       pdata    = dupstr;

   while (pdata && *pdata != '\0')
   {
      char* nd = 0;
      char* a  = strtok_r(pdata, " ",  &nd);
      char* b  = strtok_r(nd,    " ",  &nd);

      printf("a = %s, b = %s\n", a, b);

      char* nl = strchr(nd, '\n');
      pdata = ++nl;
   }

   free(dupstr);

   return 0;
}

```
Note how I elected to use strtok_r(), and when I conclude the loop, I free the original value that was returned from strdup().

Thanks I hadn't heard about strtok_r() before, gonna look into that.

I want to read the entire file at once, just for the  sake of speed.
One huge read, should be faster than 10 mio times reading one line.

Nice trick copying the original pointer, to cleanup afterwards

---

### Post by LKjell on 2009-12-26
I would have read one line at a time and use sscanf to do the parsing.

Depends on what I am working at but I feel like working with pieces of chunk and send it to another process is much faster than waiting for the whole chunk. Consider the file you are parsing is very huge then you need to wait to allocate very much memory then load it in memory.

Well the keywords are asynchrony and synchronized.

---

### Post by monkeyking on 2009-12-26
Actually I did some benchmarks,
and it seems that there are no speeddifference doing either.

I guess, that on a heavily used harddrive, it should make a difference reading the entire file.
But I dont think its worth doing.

thanks for your replies

---

