---
title: "lex yacc 2main conflict"
date: 2009-11-12
forum: Programming Talk
---

### Post by synhedionn on 2009-11-12
Hi,
I need to say 

l.l
main()
{"printf("Enter the string to analyse");
scanf("%s",st);
yylex()}



and 
l.y
NUMBER op NUMBER {  $$ =$1+$3;  /*for instance*/}
main()
{yyparse()}


But the 2 main() will conflict

How to do?

---

### Post by johnl on 2009-11-12
yyparse() will call yylex() for you.   You don't need to call them both.

---

### Post by synhedionn on 2009-11-12
ok,but how do I tell to lexerize after my "printf("Enter the string to analyse");
scanf("%s",st);" ?

---

