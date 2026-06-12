---
title: "lex and yacc"
date: 2009-09-18
forum: Programming Talk
---

### Post by tonio81 on 2009-09-18
Hi, 

I'm developping a small program using Flex and Yacc, but I have a some strange problem, if some one has the time to look at and to gave me an advice ...
Here is the problem

First of all I'm trying to recognize a string with this form:

Filter "webungmrk1" : IF (IN 'AA' == 1) THEN (OUT 'BB' = 1)

or

Filter "webungmrk1" : IF (IN 'AA' == 1) AND (OUT 'CC' == X) THEN (OUT 'BB' = 1)
It's an example.

Here is the content of my lex file:

```

%{
 
#include "anlex.h"
#include "y.tab.h"
extern YYSTYPE yylval;

%}
espace          [\r\t ]
N        [^*]
M        [^*/]

SINGLE        [=]
under        [_]
sg        [']
dg        ["]

LETTRE        [a-zA-Z]

CHIFFRE        [0-9]

WORD        {LETTRE}+
 //identificatuer 
ID        (({sg}|{dg})({LETTRE})({LETTRE}|{CHIFFRE}|{under}|{espace})*({sg}|{dg}))|({WORD})

 //constantes: 0, 1
CST        {CHIFFRE}+

%%

{espace}    ;


{ID}        {
            if (strcmp("Filter",yytext)==0){
               printf("Filter ");
            return FILTER;
            }
        else if (strcmp("IN",yytext)==0){
            printf("IN ");
            return IN;
              }
        else if (strcmp("OUT",yytext)==0){
            printf("OUT ");
               return OUT;
              }
        else if (strcmp("IF",yytext)==0){
             printf("IF ");
              return IF; 
              }
        else if (strcmp("THEN",yytext)==0){
             printf("THEN ");
              return THEN;
              }
        else if (strcmp("NONE",yytext)==0){
            printf("NONE ");
             return NONE;
              }
        else if( strcmp("AND", yytext)==0){
            printf("AND ");
            return AND;
              }
        else if(strcmp("OR", yytext)==0){
            printf("OR ");
            return OR;
              }
        else if(strcmp("X", yytext) == 0){
            printf("X ");
            return X;
              }
              else{
            yylval.str = yytext;
              printf("%s", yytext);   
            return ID;
            }
    }

"("        {  
            printf("%s ", yytext); 
            return PAR_OUV; 
        }

")"        {  
            printf("%s ", yytext); 
            return PAR_FER;
        }

"!="        {   
          printf("%s ", yytext); 
          return NOT_EQU;
        }

"=="        {   
            printf("%s ", yytext); 
            return EQU;
        }

":"        {   
              printf("%s ", yytext); 
            return PTS;
        } 

"="        { 
            printf("%c ", yytext[0]); 
            return AFF;
        }

{CST}        { yylval.str = yytext;
          printf("%s ", yytext);  
          return CST;
        }
.        yyerror(yytext);
%%



```and of course the anlex.h

```

#ifndef MFC_H
#define MFC_H

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>


// type pour yylval
#define YYSTYPE token

/********************************************************************\
                 DEFINITIONS DES TYPES ET STRUCTURES
\********************************************************************/

typedef char *  string;

typedef struct {
  string str;    
} token;

#endif

```Now there is the yacc file:

```

%{

#include "anlex.h"
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>


/***************************************************************************\
                            VARIABLES GLOBALES
\***************************************************************************/


FILE * file;    //fichier de sortie

token tmp_tok; // pour step

%}

/***************************************************************************\
                            DECLARATIONS YACC                     
\***************************************************************************/

%start    config

%token FILTER IF THEN IN OUT NONE AND OR ID PAR_OUV PAR_FER NOT_EQU EQU CST X PTS AFF

%left    AND OR
%left    EQU NOT_EQU


%%

/***************************************************************************\
             config : Filter "name" ':' IF ... THEN ...
\***************************************************************************/

config:    FILTER ID PTS IF ifcond THEN PAR_OUV inst_exp PAR_FER config {

      

                                      }
    | { printf("\nEND\n"); }
     ;

ifcond:     PAR_OUV trigger PAR_FER {}
    |PAR_OUV trigger PAR_FER AND PAR_OUV expl PAR_FER {}
      ;

trigger:   io id EQU constante         {
                      //printf("2 %s", $2.str );
                    }
     | io id NOT_EQU constante     {
                       // printf("%s", $$.str);
                    }
     ;

/***************************************************************************\
                         expl: ( expl ) | expl AND expl | expl OR expl | io ID EQU constante | io ID NOT_EQU constante
\***************************************************************************/

expl:     '(' expl ')'            {}
    | PAR_OUV expl PAR_FER        {}
    |  expl  AND  expl        {}                    
    |  expl  OR  expl          {}  
    |  io id EQU constante        { 
                     // printf("%s", $2.str); 
                    }

    |  io id NOT_EQU constante    { 
                     // printf("%s", $1.str);
                    }
    ;

/***************************************************************************\
                      inst_exp : io id = constante | NONE
\***************************************************************************/


inst_exp:     io id AFF constante   { 
                     printf("\ninst_exp %s\n", $2.str);
                      } 

        |  NONE   { $$.str = "NONE"; 
              }
        ;

id:    ID { 
        $$ = $1; 
       // printf("\nID %s", $1.str); 
      }
    ;

/***************************************************************************\
                      constante : CST | X
\***************************************************************************/

constante:    CST {
            $$ = $1;
            //printf("CST %s", $1.str);
          }
        | X {
          $$.str = "X";
        }
        ;

io:    IN {
        $$.str = "IN";
      }
    | OUT {
        $$.str = "OUT";
          }
    ;

%%


int main(int argc, char ** argv)
{ 
  int fd;
  
  if( argc != 2){
    printf("Usage: %s <file source> \n",argv[1]);    
    exit(1);
  }

  close(0);
  fd = open(argv[1], O_RDONLY );  // stdin = 0 fichier en lecture
        
  yyparse();
  close(fd);
}

int yyerror(char * s) {
  printf("%s\n", s);
}


```So as you can see, the content it's not very complex. 

Now, if you take the grammar rule 

inst_exp -> io id AFF constante { printf("%s", $2.str); }
                | NONE {}
                ;

when the printf is executed I'm seeing on the screen (if we take the 1st example) 
`'AA'' = 1 but it should be just `'AA'' because the `id' is the second element at the right side of the rule.
I can't understand why it takes the `= 1'  too .. ?

If you make another printf at the rule:

id: ID 
    ;

You can see the "right" content, i.e. just the `'AA'' without `the = 1'
May be my grammar is not right or may be the lex file is not good but at my point of view the lexical analysis is ok and the grammar too.
Has someone  an idea where is the problem ?

Best regards, 

Anton

---

