---
title: "lex problem?"
date: 2009-02-19
forum: Programming Talk
---

### Post by abhilashm86 on 2009-02-19
i did this simple lex program to count characters,lines,word.

problem error is word part is not counting??can anyone tell the modification to be done?

> %{
#include<stdio.h>
int charc=0,wordc=0,linec=0;
%}

word [^\t\n]+
eol \n
%%
{word}  {wordc++; charc +=yyleng;}
{eol}   {charc++; linec++;}
.       charc++;
%%

main()
{
        yylex();
        printf("line count=%d\nwprdcount=%d\ncharcount=%d\n",linec,wordc,charc);
}

also can i count spaces used?

---

