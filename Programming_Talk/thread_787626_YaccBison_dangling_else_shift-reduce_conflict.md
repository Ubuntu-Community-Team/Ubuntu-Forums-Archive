---
title: "Yacc/Bison dangling else shift-reduce conflict"
date: 2008-05-09
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-05-09
I have a parser for a simple language that I am working on and I have one problem with a dangling else.  I looked at some tutorials on the web, and I think I am doing the same as they suggest.

I declare my shifting priorities:

%left IFNOELSE
%right T_ELSE
%right '='
%left T_Or
%left T_And
%left T_Equal T_NotEqual
%left '<' T_LessEqual T_GreaterEqual '>'
%left '+' '-'
%left '*' '/' '%'
%right '!' 
%right '[' '.'

IfStmt		:	T_If '(' Expr ')' Stmt T_Else Stmt 	  
		|	T_If '(' Expr ')' Stmt 	 %prec IFNOELSE
		;

The error state is this:

state 187

   63 IfStmt: T_If '(' Expr ')' Stmt . T_Else Stmt
   64       | T_If '(' Expr ')' Stmt .

    T_Else  shift, and go to state 194

    T_Else    [reduce using rule 64 (IfStmt)]
    $default  reduce using rule 64 (IfStmt)

So I can see that yacc is unsure if it should shift or reduce, but have I not resolved the conflict using the priorities?  The else is given higher priority compared ot the IFNOELSE state.  I don't see why I still have a shift-reduce conflict. Any ideas?

---

### Post by SNYP40A1 on 2008-05-25
[http://marvin.cs.uidaho.edu/~heckendo/CS445/danglingElse.html](http://marvin.cs.uidaho.edu/~heckendo/CS445/danglingElse.html)

---

