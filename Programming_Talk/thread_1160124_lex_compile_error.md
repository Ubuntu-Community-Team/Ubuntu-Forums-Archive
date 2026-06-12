---
title: "lex compile error??"
date: 2009-05-15
forum: Programming Talk
---

### Post by abhilashm86 on 2009-05-15
[PHP]%{
#include<cstdio>
int idcount=0;
%}
id [a-zA-Z][=]*[a-zA-Z0-9]* 
decn "int"|"float"|"double"|"char"
%s defn
%%
{decn} {BEGIN (defn);}
<defn> {id}\, {idcount++;}
<defn> {id}\; {idcount++;BEGIN(0);}
%% 

int main(int argc,char **argv)
{
if(argc==2)
yyin=(fopen(argv[1],"r");
else
{
printf("error in opening file");
return 0;
}
yylex();
printf("number of identifiers is %d\n",idcount);
return 0;
}
[/PHP]
program is all about counting number of identifiers, 
abhilash@abhilash:~$ lex l3a.l
l3a.l:11: unrecognized rule
l3a.l:11: unrecognized rule
l3a.l:11: unrecognized rule
l3a.l:11: unrecognized rule
so what is wrong actually, seeing my code 10 times, couldn't get it :(

---

