---
title: "Lex problem"
date: 2009-11-17
forum: Programming Talk
---

### Post by kirilik on 2009-11-17
Hi,
 
I have some problem with Lex
 
if I write 1 + 1 I'm getting:
Found token INT ('1')
Found token OP ('+')
Found token INT ('1')
 
If I write 1+1 I'm getting:
Found token INT ('1')
Found token INT ('+1')
 
+1 is part of the language, what do I need to change so if I will write 1+1 I will get same as if I will write 1 + 1?
 
this is my regular expressions:
SIGN [+-]
DIGIT [0-9]
DIGIT_NZ [1-9]
INTEGER ([0])|(({SIGN}{0,1})({DIGIT_NZ}{1})({DIGIT}*))
 
Thanks

---

### Post by Arndt on 2009-11-18
> **kirilik said:**
> Hi,
 
I have some problem with Lex
 
if I write 1 + 1 I'm getting:
Found token INT ('1')
Found token OP ('+')
Found token INT ('1')
 
If I write 1+1 I'm getting:
Found token INT ('1')
Found token INT ('+1')
 
+1 is part of the language, what do I need to change so if I will write 1+1 I will get same as if I will write 1 + 1?
 
this is my regular expressions:
SIGN [+-]
DIGIT [0-9]
DIGIT_NZ [1-9]
INTEGER ([0])|(({SIGN}{0,1})({DIGIT_NZ}{1})({DIGIT}*))
 
Thanks

Remove {SIGN} from INTEGER. You will have to handle the occurrences of it where it's a unary operator in a later step.

---

### Post by johnl on 2009-11-18
(f)lex maps input to tokens.  In your case '+' in the context of '1 + 1' and '3 - +1' are the same token; you don't need to handle them differently.  Like Arndt said, differentiating between the two uses is part of syntactical analysis, which you can do with yacc or bison.  In this case you might have some rules like:


```

%token NUMBER PLUS MINUS LPAREN RPAREN TIMES DIVIDE

%left PLUS MINUS
%left TIMES DIVIDE
%left UNARY_MINUS UNARY_PLUS

%% 
expression:    NUMBER 
             | expression PLUS expression
             | expression MINUS expression 
             | expression TIMES expression
             | expression DIVIDE expression 
             | LPAREN expression RPAREN
             | MINUS expression %prec UNARY_MINUS
             | PLUS expression %prec UNARY_PLUS 

```

Which would properly allow infix arithmetic with unary plus or minus operators.

---

