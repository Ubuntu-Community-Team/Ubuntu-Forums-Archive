---
title: "HELP: Lex and Yac Problem"
date: 2009-02-24
forum: Programming Talk
---

### Post by nvidia123 on 2009-02-24
Hi,

am trying to modify the scanner.l file to also allow variable & function names to have a lower or uppoer case letter followed by zero or more lower or upper case letters or digits. I have test.vsl that i'm trying it agains and at the moment i'm modifying variable to do what i want it to do. However, when i compiler the vsl code i.e

./vc < prog.vsl > prog.
which looks like this 
[PHP]

// this is comment
/* this is c style comment */

FUNC main()
{

VAR I

I := 0
}

[/PHP]
i keep getting an error saying
vc: syntax error near line 4
vc: Bad function syntax near line 4


In scanner.l i took away the default patter matching for variable i.e {lc_letter}({lc_letter}|{digit})*

and replaced it with my own which is curretently:
variable ({lc_letter}|{uc_letter})
but it still does not work. Can somebody help please. 

Thanks

---

