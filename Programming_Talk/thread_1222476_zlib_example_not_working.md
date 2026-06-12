---
title: "zlib example not working"
date: 2009-07-24
forum: Programming Talk
---

### Post by monkeyking on 2009-07-24
Hi I'm trying to get familiar with the zlib library,
but I cant even get the official example program to function
[http://www.zlib.net/zpipe.c](http://www.zlib.net/zpipe.c)

[PHP]
$ gcc zpipe.c -lz
$ cat test.txt 
"V1" "V2" "V3" "V4" "V5" "V6" "V7"
"1" 1 6 11 16 21 26 31
"2" 2 7 12 17 22 27 32
"3" 3 8 13 18 23 28 33
"4" 4 9 14 19 24 29 34
"5" 5 10 15 20 25 30 35
$ gzip test.txt 
$ ./a.out -d <test.txt.gz 
zpipe: invalid or incomplete deflate data
[/PHP]
But If i use the program it self to compress/decompress it works
[PHP]
$ ./a.out <test.txt 
x&#65533;&#65533;91
       C&#65533;&#65533;(&#65533;3&#65533;H&#65533;Id&#65533;C&#1636;&#65533;JG~J&#65533;&#65533;&#65533;&#65533;1&#65533;&#65533;2&#65533;&&#65533;DB
                                          OJ&#65533;&#65533;c2Z&#65533;xQ+&#65533;F&#65533;6.&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;::&#65533;&#65533;C&#65533;&#65533;&#65533;4PC7<&#65533;F&#65533;&#65533;&#65533;&#65533;&#65533;$ ./a.out <test.txt >test.gz
$ ./a.out -d <test.gz
"V1" "V2" "V3" "V4" "V5" "V6" "V7"
"1" 1 6 11 16 21 26 31
"2" 2 7 12 17 22 27 32
"3" 3 8 13 18 23 28 33
"4" 4 9 14 19 24 29 34
"5" 5 10 15 20 25 30 35

[/PHP]



Can someone point me in the right direction?

thanks in advance

---

### Post by monkeyking on 2009-10-09
For anyone that cares,
this must be the simple example of zlib

[PHP]
#include <iostream>
#include <zlib.h>


int main(int argc,char **argv){
  
  gzFile fpIn;


  if (!(fpIn = gzdopen(fileno(stdin), "r"))){ 
    fprintf (stderr, "failed to open stdin as .glz file\n") ; 
    return 1 ; 
  }

  char c;
  while (gzread (fpIn, &c, sizeof(char)))    {
    printf("%c",c);
  }

  return 0;
}
[/PHP]

---

