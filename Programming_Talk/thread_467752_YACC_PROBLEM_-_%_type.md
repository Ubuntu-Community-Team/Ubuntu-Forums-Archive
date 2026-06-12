---
title: "YACC PROBLEM - % type"
date: 2007-06-08
forum: Programming Talk
---

### Post by jenny__ on 2007-06-08
[U]Good morning all!:KS

I would like your help on yacc program I have made!;)[/U]

%{

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
/* #include "parser.h" */

%}

%start  program

%union {
                char *string;
                int integer;
                }


%token <string>  ID
%token <integer> NUMBER
%token <string> STRING
%token IF ELSE WHILE FOR
%token FUNCTION RETURN
%token TRUE FALSE NIL AND NOT OR

%left           '='
%left           "||"
%left           "&&"
%nonassoc        "==" "!="
%nonassoc       '>' ">=" '<' "<="
%left           '+' '-'
%left           '*' '/' '%'
%right          '!' "++" "--" UMINUS
%left           '.'

%%

program:        statements
                ;

statements:          statements stmt
                |
                ;

stmt:
                ';'
                |expr ';'
                |whilestmt
                |forstmt
                |returnstmt
                |block
                |funcdef
                |ifstmt
                ;

expression:
                assignexpr
                |expr '+' expr   { $$ = $1 + $3;} /*  HERE IS THE PROBLEM  *
/
                |expr '-' expr
                |expr '*' expr
                |expr '/' expr  /*{ if($3==0)
                                                yyerror(.divide 0.);
                                           else
                                                $$ = $1 / $3;}              
  */
                |expr '%' expr
                |expr '>' expr
                |expr ">=" expr
                |expr '<' expr
                |expr "<=" expr
                |expr "==" expr
                |expr "!=" expr
                |expr "&&" expr
                |expr "||" expr
                ;


expr:           expression
                ;
%%


int main() {

}



[U]But it does not work!:confused: 
In the example.y file we have the terminal symbols and non-terminal symbols.

The terminal symbols I use are NUMBER,ID,STRING. 
I  have defined a type for them
e.g. ID has a string value, NUMBER has an integer value etc
Well I'm  :confused: as far as the % type is concerned.
 We have to give a type to non terminals too.


If we do yacc example.y we take the **[COLOR="DarkGreen"]output[/COLOR]**:
[/U]

hello.y:58.36-37: $$ of `expression' has no declared type
hello.y:58.41-42: $1 of `expression' has no declared type
hello.y:58.46-47: $3 of `expression' has no declared type

_This happens cause expression which is a non-terminal symbol has no type!_

_What type can this symbol take?shall i define a struct for this?_

_If i do  : %type <integer> expression i take :_

hello.y:61.18-30: warning: type clash on default action: <integer> != <>
hello.y:62.18-30: warning: type clash on default action: <integer> != <>
hello.y:63.18-30: warning: type clash on default action: <integer> != <>
hello.y:67.18-30: warning: type clash on default action: <integer> != <>
hello.y:68.18-30: warning: type clash on default action: <integer> != <>
hello.y:69.18-31: warning: type clash on default action: <integer> != <>
hello.y:70.18-30: warning: type clash on default action: <integer> != <>
hello.y:71.18-31: warning: type clash on default action: <integer> != <>
hello.y:72.18-31: warning: type clash on default action: <integer> != <>
hello.y:73.18-31: warning: type clash on default action: <integer> != <>
hello.y:74.18-31: warning: type clash on default action: <integer> != <>
hello.y:75.18-31: warning: type clash on default action: <integer> != <>


I would be really grateful if there is someone out there who can help me!

Thank you!

Have a nice day

Jenny

---

### Post by bunker on 2007-06-08
I'm not sure you can do this:

```

%token <string> ID
%token <integer> NUMBER
%token <string> STRING

```

When I made a compiler I used flex to get the tokens.  In this way your grammar looks more like:

```

expr : expr TOKEN_PLUS expr { $$ = $1 + $3; }
       | expr TOKEN_MINUS term { $$ = $1 - $3; }
       ;

```

Your syntax analyser will just repeatedly call the lexical analyser so you don't need any static definitions of tokens.  Not positive if that's what you're aiming for - it might be overkill - but it's how I did it.

Another thing you might need is to define YYSTYPE in your declarations.  This is the type of the $$ return.  For me, I used a binary tree since I was just building up a complete parse tree of whatever the text was.  I think it's integer by default.

(Also by the way you might want to use the code /code bbtags to put in big files like that - it's quite hard to see if there's just a simple error.)

---

### Post by jenny__ on 2007-06-08
Well thanks for replying :)

I made a lexical analyser and i use in it the yyparse function :)

Well i do :

flex jenny.l
yacc jenny.y
gcc lex.yy.c y.tab.c -o jenny

and i take the output:

jenny.y: In function `yyparse':
jenny.y:84: error: invalid operands to binary +
jenny.y:85: warning: assignment makes pointer from integer without a cast
jenny.y:86: error: invalid operands to binary *
jenny.y:90: error: invalid operands to binary /
jenny.y:91: error: invalid operands to binary %
jenny.y:92: warning: assignment makes pointer from integer without a cast
jenny.y:93: warning: assignment makes pointer from integer without a cast
jenny.y:94: warning: assignment makes pointer from integer without a cast
jenny.y:95: warning: assignment makes pointer from integer without a cast
jenny.y:96: warning: assignment makes pointer from integer without a cast
jenny.y:97: warning: assignment makes pointer from integer without a cast
jenny.y:98: warning: assignment makes pointer from integer without a cast
jenny.y:99: warning: assignment makes pointer from integer without a cast

All these warnings and errors appear in the this part of the jenny.y program

/* line 82 */ expression:
                assignexpr      { $$ = $1;}
                [COLOR="Magenta"]|expr '+' expr   {$$ = $1 + $3;}[/COLOR]
               [COLOR="Magenta"] |expr '-' expr   {$$ = $1 - $3;}[/COLOR]
                [COLOR="Magenta"]|expr '*' expr   {$$ = $1 * $3;}[/COLOR]
               [COLOR="Black"] [COLOR="Magenta"]|expr '/' expr   { if($3==0)[/COLOR][/COLOR]
                                                yyerror("divide 0");
                                           else
                                                [COLOR="Magenta"]$$ = $1 / $3;}[/COLOR]
              [COLOR="Magenta"]  |expr '%' expr  {$$ = $1 % $3;}[/COLOR]
                [COLOR="Magenta"]|expr '>' expr  {$$ = ($1 > $3);}
                |expr ">=" expr {$$ = $1 >= $3;}
                |expr '<' expr  {$$ = ($1) < ($3);}
                |expr "<=" expr {$$ = $1 <= $3;}
                |expr "==" expr {$$ = $1 == $3;}
                |expr "!=" expr {$$ = $1 != $3;}
                |expr "&&" expr {$$ = $1 && $3;}
                |expr "||" expr {$$ = $1 || $3;}[/COLOR]
                |term           {$$ = $1;}
                ;

The pink colour indicates error notice!

What shall i correct in these rules?

Thanks, in advance!!! :)

Be well!!!

---

### Post by bunker on 2007-06-08
Hm it still seems like a type error with YYSTYPE, but I'm really not positive how to fix it.  [This yacc tutorial](http://dinosaur.compilertools.net/yacc/index.html) seems a bit more relevant than my experience.  (And also good in general: [http://dinosaur.compilertools.net](http://dinosaur.compilertools.net)).

Sorry I couldn't help further.  I have uploaded the stuff I did for the compiler in case that helps you.  Here is the [lex file](http://www.bananadine.co.uk/stuff/lex2.l) and [yacc file](http://www.bananadine.co.uk/stuff/yacc3.y).

Edit: Fixed urls.  It censors a*s (as in assignment) - that made chuckle :).

---

### Post by jenny__ on 2007-06-08
Well i did what you told me with YYSTYPE and  i placed in jenny.l 

#define YYSTYPE Expr *  ->> Expr is a struct which consists of 

struct Expr
{
int intValue;
char *name;
double dval;
};

but again i take the same errors and warnings.

Well I have another question,  in my system i have two versions of Yacc.

In the first version(older one) when i do : flex jenny.l everything is ok

In the second version (new one) when i do flex jenny.l i take 

jenny.l:222: unrecognized rule
jenny.l:224: unrecognized rule
jenny.l:228: unrecognized rule
jenny.l:244: unrecognized rule

I think that these appear cause flex doen't recognise that way of writing these rules with pink

In jenny.l file i have written:

%x STRINGSTATE

%x COMMENTCONDITION1
%x COMMENTCONDITION2
%x COMMENTCONDITION3

{[COLOR="Magenta"]COMMENT1}      {BEGIN(COMMENTCONDITION1);}

[COLOR="Magenta"]{COMMENT2}      BEGIN(COMMENTCONDITION1);[/COLOR]
[/COLOR]

[COLOR="Magenta"]<STRINGSTATE>{COMMENT3}         BEGIN(COMMENTCONDITION2);

{COMMENT4}              BEGIN(COMMENTCONDITION3);[/COLOR]

The pink colour indicates where the problem is!

Do you have any idea on that?

Thanks for files you sent me! :) :KS

Jenny

---

