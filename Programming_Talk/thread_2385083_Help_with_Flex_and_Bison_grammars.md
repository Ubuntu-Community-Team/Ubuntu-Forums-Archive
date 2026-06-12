---
title: "Help with Flex and Bison grammars"
date: 2018-02-16
forum: Programming Talk
---

### Post by trilobite2 on 2018-02-16
Hi all - 

 I'm trying to use Flex and Bison to put together a small programming language (I've called it miniFPL for "mini functional programming language").  
I'm trying to make the syntax somewhat Haskell-ish (although unlike Haskell it doesn't use indentation, it does use semicolons and it isn't a "lazy evaluation" language).  

Anyway, I'm getting these errors from Bison at present -  

~/miniFPL $ bison -d miniFPL.y
miniFPL.y:55.17-20: error: symbol BOOL is used, but is not defined as a token and has no rules
             |   BOOL 
                 ^^^^
miniFPL.y:53.17-20: error: symbol CHAR is used, but is not defined as a token and has no rules
             |   CHAR 
                 ^^^^
miniFPL.y:52.17-21: error: symbol FLOAT is used, but is not defined as a token and has no rules
             |   FLOAT 
                 ^^^^^
miniFPL.y:51.17-19: error: symbol INT is used, but is not defined as a token and has no rules
 type:           INT 
                 ^^^
miniFPL.y:56.17-20: error: symbol LIST is used, but is not defined as a token and has no rules
             |   LIST  
                 ^^^^
miniFPL.y:57.17-20: error: symbol NONE is used, but is not defined as a token and has no rules
             |   NONE 
                 ^^^^
miniFPL.y:54.17-22: error: symbol STRING is used, but is not defined as a token and has no rules
             |   STRING 
                 ^^^^^^
miniFPL.y:21.15-18: error: symbol bool is used, but is not defined as a token and has no rules
           |   bool
               ^^^^
miniFPL.y:19.15-18: error: symbol char is used, but is not defined as a token and has no rules
           |   char 
               ^^^^
miniFPL.y:18.15-19: error: symbol float is used, but is not defined as a token and has no rules
           |   float 
               ^^^^^
miniFPL.y:17.15-21: error: symbol integer is used, but is not defined as a token and has no rules
           |   integer 
               ^^^^^^^
miniFPL.y:20.15-20: error: symbol string is used, but is not defined as a token and has no rules
           |   string 
               ^^^^^^
miniFPL.y:7.8-23: warning: symbol translation_unit is used, but is not defined as a token and has no rules [-Wother]
 %start translation_unit
        ^^^^^^^^^^^^^^^^
miniFPL.y:93.17-23: error: symbol varname is used, but is not defined as a token and has no rules
 func_vars:      varname 
                 ^^^^^^^

This is my Flex file -  miniFPL.l   -  

```
 
/*  miniFPL.l  */ 

digit            [0-9]
letter          [a-zA-Z_]


%{

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <errno.h>
#include "y.tab.h"

void count(void);
%}

%%

[0-9]+      { 
             yylval = atoi(yytext); 
             return INTEGER;
            }  


[a-zA-Z_][a-zA-Z_][0-9]  { return IDENTIFIER;  } 
 
\"([^\\\"]|\\.)*\"       { return STRING_LITERAL; }  


"/*"                { comment(); }
"//"[^\n]*          { /* double-slash comment */   }

"case"              { count();  return(CASE);      } 
"of"                { count();  return(OF);        }  
"otherwise"         { count();  return(OTHERWISE); }  
"print"             { count();  return(PRINT);     }  

"<="                { count();  return(LE);    }
">="                { count();  return(GE);    }
"=="                { count();  return(EQ);    }
"!="                { count();  return(NE);    }
";"                 { count();  return(';');   }
"="                 { count();  return('='); }
"<"                    { count();  return('<'); }
">"                 { count();  return('>'); }
"+"                 { count();  return('+'); }
"-"                 { count();  return('-'); }
"*"                 { count();  return('*'); }
"/"                 { count();  return('/'); }
"^"                 { count();  return('^'); }

[ \t\v\n\f]         { count(); }

%%

int yywrap(void)
{
    return 1;
}


void comment(void)
{
    char c, prev = 0;
  
    while ((c = input()) != 0)      /* (EOF maps to 0) */
    {
        if (c == '/' && prev == '*')
            return;
        prev = c;
    }
    error("unterminated comment");
}


int column = 0;

void count(void)
{
    int i;

    for (i = 0; yytext[i] != '\0'; i++)
        if (yytext[i] == '\n')
            column = 0;
        else if (yytext[i] == '\t')
            column += 8 - (column % 8);
        else
            column++;

    ECHO;
}


``` 


This is my Bison file -  miniFPL.y   -  

```
 


%token IDENT CONSTANT STRING_LITERAL 
%token CASE OF OTHERWISE PRINT 

%start translation_unit
%%

expr:          simple_expr 
          |    complex_expr 
          |    ";" simple_expr  
          |    ";" complex_expr    
          ; 

terminal:     var_name 
          |   integer 
          |   float 
          |   char 
          |   string 
          |   bool
          |   list  
          ; 

list:         empty_list 
          |   filled_list  
          ; 

empty_list:  "[" "]"
          ; 

filled_list:  "[" terminal 
          |   filled_list ","  terminal "]"   
          ; 

simple_expr:    terminal
            |   "(" expr ")"
            |   var_name "=" simple_expr
            |   condition
            |   print_expr
            |   func_call 
            |   simple_expr "*" simple_expr
            |   simple_expr "/" simple_expr
            |   simple_expr "+" simple_expr
            |   simple_expr "-" simple_expr
            ;   

print_expr:     PRINT expr ";" 
            ; 

type:           INT 
            |   FLOAT 
            |   CHAR 
            |   STRING 
            |   BOOL 
            |   LIST  
            |   NONE 
            ;          

complex_expr:    case_expr 
             |   func_expr 
             ;    

case_expr:       case_head case_body 
             ; 

case_head:       CASE var_name OF "\n" 
             ; 

case_body:        case_line 
             |    case_body "\n" case_line  
             ; 

case_line:        in_value "->" out_value ";" 
             ;

in_value:        integer 
             |   float 
             |   char 
             |   string 
             |   bool
             |   list  
             |   OTHERWISE 
             ;  
             
out_value:       in_value 
             |   simple_expr
             ;   

func_call:      func_name func_vars ";" 
             ; 

func_vars:      varname 
             |  func_vars varname 
             ; 

func_expr:      func_decl func_body 
             ; 

func_decl:      func_name "::"  arg_types  "->" return_type ";"       
             ; 

arg_types:       type 
             |   arg_types "->" type  
             ;   

return_type:     type 
             ;  

func_body:      simple_expr  ";" 
             |  func_body simple_expr 
             |  case_expr  
             ; 

condition:      simple_expr
            |   condition "and" condition
            |   condition "or" condition
            |   "not" condition
            |   simple_expr ">"  simple_expr
            |   simple_expr ">=" simple_expr
            |   simple_expr "<"  simple_expr
            |   simple_expr "<=" simple_expr
            |   simple_expr "==" simple_expr
            |   simple_expr "!=" simple_expr
            ;  

var_name:       identifier 
            ; 

func_name:    identifier 
            ;  

identifier:    IDENT 
            ; 


``` 


A few small examples of code that the tools should parse -  this will give an idea of the "flavour" that I'm after -  
```
  

area r = pi * r ^ 2 ; 

areaRect l w = l * w ; 

sq :: num -> num ;
sq n = n * n  ;  

 mylist = ["foo", "bar", "baz"]  ;  

list2 =  [ 1 , 2 , 3 ]  ;  

case a of 
   1  ->  "One" ;
   2  ->  "Two"  ; 
   3  ->  "Three"  ;  
otherwise  ->  "Something else" ;   

print  "foo bar baz"  ;  
    

```  

So -  any help with these is very gratefully received!  

Many thanks -  
- trilobite

---

