---
title: "(C - strtok) Getting program to print all tokens"
date: 2010-03-07
forum: Programming Talk
---

### Post by trilobite on 2010-03-07
Hi all - 

 In the process of experimenting with strtok in C, I've done the following code - 
```
 
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>
      
int main(void)
{
  
  char text[80];
  char *tokens;
  
    puts("Enter some text :");
    scanf("%s", text);     
    tokens = strtok(text, " ");
    
    while (tokens != NULL) {

    printf("Token = %s\n", tokens);
    
    tokens = strtok(NULL, " ");    
            
    }      
      
  return 0;
 
}
 

``` 

This compiles and runs, but when I type (for example) "This is a test" and press enter, the program only outputs -  
Token = This

In other words, only the first token. 

How can I get it to output all of the tokens - not just the first one?  

Many thanks in advance - 
- trilobite

---

### Post by LKjell on 2010-03-07
Check what scanf do... > s - String of characters. This will read subsequent characters until a whitespace is found 
(whitespace characters are considered to be blank, newline and tab).
[http://www.cplusplus.com/reference/clibrary/cstdio/scanf/](http://www.cplusplus.com/reference/clibrary/cstdio/scanf/)

Use fgets to read a line. Do not use gets even thought it might be tempted.
The rest is correct.

---

### Post by trilobite on 2010-03-07
> **LKjell said:**
> Check what scanf do... 
[http://www.cplusplus.com/reference/clibrary/cstdio/scanf/](http://www.cplusplus.com/reference/clibrary/cstdio/scanf/)

Use fgets to read a line. Do not use gets even thought it might be tempted.
The rest is correct.

Hi LKjell - thanks very much for that!  
Great! I replaced the scanf with fgets, and now it works perfectly! 
Thanks again, bye for now - 
- trilobite

---

