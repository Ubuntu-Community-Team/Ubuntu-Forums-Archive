---
title: "[C] Problem with Runtime Segmentation Fault"
date: 2011-04-25
forum: Programming Talk
---

### Post by stlbhoy on 2011-04-25
Hi there! I'm working on a project for a compilers class where our code must be written in C. He has given us some source code to modify and use to test, however when I try to test I get a Segmentation Fault.

The program is meant to take a "tuple" file and make a linked list of the basic blocks. However before doing this it prints them to a GraphViz file. It seems as though the segmentation error occurs when passing or manipulating pointers within the function that prints to the .gv file.

This is the main file:

```
#include "tuplec.h"

void graph_tree (node * tree);


int main ( int argc, char * argv[]){

    node * tree = (node*)yyparse();

    if (tree){
        graph_tree (tree);
    } else {
        printf("do'oh\n");
    }

    return 0;

}

char * prod_name (node * n);
int is_useless ( node * n);
int _graphAST (node * n, int * i);
int _graphCST (node * n, int * i);
void graph_tree ( node * tree)
{
    int i = 0;
    printf("digraph G {\n");

    /*
     * ok, here's the deal... change this to:
     * 1) _graphCST if you want a complete syntax tree
     * 2) _graphAST if you want a more "abstract" syntax tree
     */
    //_graphAST (tree, &i);
    _graphCST (tree, &i);
    printf("}\n");

}


int _graphCST (node* n, int * i)
{
    int me = -1;
    int l;

  if( !n )  //handle NULL children
    return -1;

  switch (n->production){

    case REG_SPECIAL:
            me = *i; (*i)++;
            printf("REG_SPECIAL_%d [label=\"%s\"];\n", me, (char*) n->data);
        break;

    case NUM:
            me = *i; (*i)++;
            printf("NUM_%d [label=\"%d\"];\n",me, *(int*) n->data);
        break;

    case DONE:
            me = *i; (*i)++;
            printf("EXIT_%d [label=\"EXIT\"];\n", me);
        break;

    default:
        /* first label ourselves */
        me = *i; (*i)++;
        printf("%s_%d [label = \"%s\"];\n", prod_name(n), me, prod_name(n));
         /* we can always try all three branches b/c we can handle null children */
        if( (l = _graphCST( n->child1, i)) != -1) { printf("%s_%d -> %s_%d ;\n", prod_name(n), me, prod_name(n->child1), l); }
        if( (l = _graphCST( n->child2, i)) != -1) { printf("%s_%d -> %s_%d ;\n", prod_name(n), me, prod_name(n->child2), l); }
        if( (l = _graphCST( n->child3, i)) != -1) { printf("%s_%d -> %s_%d ;\n", prod_name(n), me, prod_name(n->child3), l); }
  }

  return me;
}


char * prod_name (node * n)
{
  switch( n->production )
  {
    case PROGRAM:
      return "PROGRAM"; break;

    case INSTR_LIST:
      return "INSTR_LIST";  break;

    case INSTR:
      return "INSTR";  break;

    case ASN:
      return "ASSIGN"; break;

    case ADD:
      return "ADD";   break;

    case SUB:
      return "SUB";  break;

    case JMP:
      return "JUMP";  break;

    case BRANCH:
      return "BRANCH";  break;

    case LABL:
      return "LABEL";  break;

    case READ:
      return "READ";  break;

    case WRITE:
      return "WRITE";  break;

    case ARG:
      return "ARG";  break;

    case REGARG:
      return "REGARG";  break;

    case REG_NUM:
      return "REG_NUM";  break;

    /* these are special cases */
    case DONE:
      return "EXIT";  break;

    case REG_SPECIAL:
      return "REG_SPECIAL";  break;

    case MEM:
      return "MEMORY"; break;

    case NUM:
      return "NUM";  break;

    default:
      return "";
  }
}


#if 1

int is_useless ( node * n)
{

    if (n == NULL)
        return 1;

    switch (n->production)
    {
        case INSTR:
        case REGARG:
        case ARG:
            return 1;

        default:
            return 0;
    }

}

int _graphAST (node* n, int * i)
{
    int me = -1;
    int l;

  if( !n )  //handle NULL children
    return -1;

  switch (n->production){

    case REG_SPECIAL:
            me = *i; (*i)++;
            printf("N_%d [label=\"%s\"];\n", me, (char*) n->data);
        break;

    case NUM:
            me = *i; (*i)++;
            printf("N_%d [label=\"%d\"];\n",me, *(int*) n->data);
        break;

    case DONE:
            me = *i; (*i)++;
            printf("N_%d [label=\"EXIT\"];\n", me);
        break;

    default:
        me = *i; (*i)++;

        if (is_useless(n)){
            if( (l = _graphAST( n->child1, i)) != -1) { me = l; }
        }
        else {
           /* first label ourselves */
            printf("N_%d [label = \"%s\"];\n", me, prod_name(n));

           /* we can always try all three branches b/c we can handle null children */
            if( (l = _graphAST( n->child1, i)) != -1) { printf("N_%d -> N_%d ;\n", me, l); }
            if( (l = _graphAST( n->child2, i)) != -1) { printf("N_%d -> N_%d ;\n", me, l); }
            if( (l = _graphAST( n->child3, i)) != -1) { printf("N_%d -> N_%d ;\n", me, l); }
        }

  }

  return me;
}

#endif


```

I've been looking for the segfault for a while but I'm not very good with pointers to be honest. I've been running it using this test file:

test1.tup
```
(ASSIGN,BP,0)
(ASSIGN,SP,0)
(ASSIGN,FP,SP)
(ADDI,SP,FP,2)
(ASSIGN,M[FP],3)
(JUMP,2)
(LABEL,0)
(ADDI,SP,SP,1)
(ADDI,SP,SP,1)
(ASSIGN,R0,M[FP+4])
(READI,M[FP+4])
(ASSIGN,R1,M[FP+5])
(ASSIGN,R2,4)
(ASSIGN,M[FP+5],R2)
(ASSIGN,M[SP],4)
(ADDI,SP,SP,1)
(ASSIGN,M[SP],FP)
(ADDI,SP,SP,1)
(SUBI,M[SP],SP,2)
(ADDI,SP,SP,1)
(ASSIGN,R3,M[FP+4])
(ASSIGN,R4,R3)
(ASSIGN,M[SP],R4)
(ADDI,SP,SP,1)
(ASSIGN,R5,M[FP+5])
(ASSIGN,R6,R5)
(ASSIGN,M[SP],R6)
(ADDI,SP,SP,1)
(SUBI,FP,SP,5)
(JUMP,1)
(LABEL,4)
(ASSIGN,SP,M[FP+2])
(ASSIGN,FP,M[FP+1])
(JUMP,M[FP])
(LABEL,1)
(ASSIGN,R7,M[FP+3])
(ASSIGN,R8,R7)
(ASSIGN,R9,M[FP+4])
(ASSIGN,R10,R9)
(ADDI,R11,R8,R10)
(WRITEI,R11)
(JUMP,M[FP])
(LABEL,2)
(ADDI,SP,SP,1)
(ADDI,SP,SP,1)
(ADDI,SP,SP,1)
(ADDI,SP,SP,1)
(ADDI,SP,SP,1)
(ASSIGN,R12,M[FP+5])
(READI,M[FP+5])
(ASSIGN,R13,M[FP+5])
(ASSIGN,R14,R13)
(WRITEI,R14)
(ASSIGN,R15,M[FP+6])
(ASSIGN,R16,R15)
(WRITEI,R16)
(ASSIGN,M[SP],5)
(ADDI,SP,SP,1)
(ASSIGN,M[SP],FP)
(ADDI,SP,SP,1)
(SUBI,M[SP],SP,2)
(ADDI,SP,SP,1)
(ASSIGN,R17,M[FP+5])
(ASSIGN,R18,R17)
(ASSIGN,M[SP],R18)
(ADDI,SP,SP,1)
(SUBI,FP,SP,4)
(JUMP,0)
(LABEL,5)
(ASSIGN,SP,M[FP+2])
(ASSIGN,FP,M[FP+1])
(JUMP,M[FP])
(LABEL,3)

```

---

### Post by dwhitney67 on 2011-04-25
What does the yyparse() function look like?

Btw, have you tried using gdb or valgrind to find where in the code the seg-fault is occurring?

-----------

EDIT:

Check here:
```

char * prod_name (node * n)
{
  **if (n == NULL) return "";**   /* add this line */

  switch( n->production )
  {
    ...
  }

  ...
}

```

---

### Post by stlbhoy on 2011-04-25
> **dwhitney67 said:**
> What does the yyparse() function look like?

Btw, have you tried using gdb or valgrind to find where in the code the seg-fault is occurring?

the yyparse function is part of using flex and bison to come up with a grammar for the tuple language. i know the segfault comes after this though as when i run it using

./tuplec < test1.tup

which prints out to the terminal rather than a .gv file, it gets to the printf("digraph G{\n"); inside the graph_tree function before printing Segmentation Fault

I downloaded gdb but I'm not sure how to use it just yet. I was under the impression though that it mainly caught seg errors at compilation rather than runtime

---

### Post by dwhitney67 on 2011-04-25
> **stlbhoy said:**
> ... i know the segfault comes after this though as when i run it using

I just edited my first post to include some additional information; please re-read it.

---

### Post by stlbhoy on 2011-04-25
Hmm... I added the check in there but it's still giving me the error :(

I also just realized this might be helpful. This is where the node type is defined:

```

/*
 * the ast node structure
 *
 */

typedef enum {
    PROGRAM = 1, INSTR_LIST, INSTR, ASN, ADD, SUB, JMP, BRANCH, LABL, READ, WRITE, DONE, ARG, REGARG, REG_NUM, REG_SPECIAL, MEM, NUM
} production_t;

typedef struct node {

    struct node * child1;
    struct node * child2;
    struct node * child3;
    production_t production;
    void * data;
    unsigned int lineno;
} node;

```

---

### Post by stlbhoy on 2011-04-25
i think it must be in the prod_name function because when i call printf("%s", tree); before printing printf("digraph G{\n"); I get the segfault right away. Am I passing and returning strings correctly?

---

### Post by dwhitney67 on 2011-04-25
All I can suggest is that you recompile your source code using the "-g" option, and then run it in gdb.  Here's how:
```

gcc -Wall -g YourSource.c -o app

gdb ./app

gdb>  set args < test1.tup

gdb>  run

```
gdb should indicate where the program crashes.

---

### Post by dwhitney67 on 2011-04-25
> **stlbhoy said:**
> Am I passing and returning strings correctly?
Technically, you should return a const char*, but I do not believe the seg-fault issue is related to your usage of the strings.  Of course, I may have missed something when spot-checking your code.

---

### Post by stlbhoy on 2011-04-25
Hey thanks a lot for your help with gdb. It gave me the following when I ran it:
```


Program received signal EXC_BAD_ACCESS, Could not access memory.
Reason: KERN_INVALID_ADDRESS at address: 0x0000000000106cf8
0x0000000100000ea5 in _graphCST (n=0x106ce0, i=0x7fff5fbff99c) at tuplec.c:50
50      switch (n->production){


```

I also got a segmentation fault when I tried doing this:
```

printf("%d", tree->lineno);

```

I put that before the printf("digraph G{\n"); and I got the error before it printed that. So that makes me think 

node * tree = (node*)yyparse();

isn't doing what it's supposed to. Which sucks because that is fully code given by my professor/using bison. And the .c file that contains yyparse() is really tough to decipher ](*,)


if you feel like rummaging through it though here it is
```

/* A Bison parser, made by GNU Bison 2.3.  */

/* Skeleton implementation for Bison's Yacc-like parsers in C

   Copyright (C) 1984, 1989, 1990, 2000, 2001, 2002, 2003, 2004, 2005, 2006
   Free Software Foundation, Inc.

   This program is free software; you can redistribute it and/or modify
   it under the terms of the GNU General Public License as published by
   the Free Software Foundation; either version 2, or (at your option)
   any later version.

   This program is distributed in the hope that it will be useful,
   but WITHOUT ANY WARRANTY; without even the implied warranty of
   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
   GNU General Public License for more details.

   You should have received a copy of the GNU General Public License
   along with this program; if not, write to the Free Software
   Foundation, Inc., 51 Franklin Street, Fifth Floor,
   Boston, MA 02110-1301, USA.  */

/* As a special exception, you may create a larger work that contains
   part or all of the Bison parser skeleton and distribute that work
   under terms of your choice, so long as that work isn't itself a
   parser generator using the skeleton or a modified version thereof
   as a parser skeleton.  Alternatively, if you modify or redistribute
   the parser skeleton itself, you may (at your option) remove this
   special exception, which will cause the skeleton and the resulting
   Bison output files to be licensed under the GNU General Public
   License without this special exception.

   This special exception was added by the Free Software Foundation in
   version 2.2 of Bison.  */

/* C LALR(1) parser skeleton written by Richard Stallman, by
   simplifying the original so-called "semantic" parser.  */

/* All symbols defined below should begin with yy or YY, to avoid
   infringing on user name space.  This should be done even for local
   variables, as they might otherwise be expanded by user macros.
   There are some unavoidable exceptions within include files to
   define necessary library symbols; they are noted "INFRINGES ON
   USER NAME SPACE" below.  */

/* Identify Bison output.  */
#define YYBISON 1

/* Bison version.  */
#define YYBISON_VERSION "2.3"

/* Skeleton name.  */
#define YYSKELETON_NAME "yacc.c"

/* Pure parsers.  */
#define YYPURE 0

/* Using locations.  */
#define YYLSP_NEEDED 0



/* Tokens.  */
#ifndef YYTOKENTYPE
# define YYTOKENTYPE
   /* Put the tokens into the symbol table, so that GDB and other debuggers
      know about them.  */
   enum yytokentype {
     LPAREN = 258,
     RPAREN = 259,
     COMMA = 260,
     LSQBRACE = 261,
     RSQBRACE = 262,
     PLUS = 263,
     ASSIGN = 264,
     ADDI = 265,
     SUBI = 266,
     JUMP = 267,
     JNZ = 268,
     LABEL = 269,
     READI = 270,
     WRITEI = 271,
     EXIT = 272,
     REG = 273,
     REG_SP = 274,
     MEMORY = 275,
     NUMBER = 276
   };
#endif
/* Tokens.  */
#define LPAREN 258
#define RPAREN 259
#define COMMA 260
#define LSQBRACE 261
#define RSQBRACE 262
#define PLUS 263
#define ASSIGN 264
#define ADDI 265
#define SUBI 266
#define JUMP 267
#define JNZ 268
#define LABEL 269
#define READI 270
#define WRITEI 271
#define EXIT 272
#define REG 273
#define REG_SP 274
#define MEMORY 275
#define NUMBER 276




/* Copy the first part of user declarations.  */
#line 1 "tuple.y"

// parsing file for Tuple
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include "globals.h"
    
    int        lineno    = 1;    /* number of current source line */
    extern int    yylex();    /* lexical analyzer generated from lex.l */
    extern char    *yytext;    /* last token, defined in lex.l  */
    
    void yyerror(char *s)
    {
            fprintf(stderr,"Syntax error on line #%d: %s\n",lineno,s);
            fprintf(stderr,"Last token was \"%s\"\n",yytext);
            exit(1);
    }
    
    node* node_alloc(production_t production)
    {
        node* n = (node*)malloc( sizeof( node ) );
        if( !n )
        {
            fprintf( stderr, "failed to allocated memory!\n" );
            exit(1);
        }
        n->child1 = NULL;
        n->child2 = NULL;
                n->child3 = NULL;
        n->production = production;
        n->data = NULL;
        n->lineno = lineno;
        return n;
    }
    


/* Enabling traces.  */
#ifndef YYDEBUG
# define YYDEBUG 0
#endif

/* Enabling verbose error messages.  */
#ifdef YYERROR_VERBOSE
# undef YYERROR_VERBOSE
# define YYERROR_VERBOSE 1
#else
# define YYERROR_VERBOSE 0
#endif

/* Enabling the token table.  */
#ifndef YYTOKEN_TABLE
# define YYTOKEN_TABLE 0
#endif

#if ! defined YYSTYPE && ! defined YYSTYPE_IS_DECLARED
typedef union YYSTYPE
#line 39 "tuple.y"
{
    node* node_ptr;
}
/* Line 193 of yacc.c.  */
#line 179 "tuple.tab.c"
    YYSTYPE;
# define yystype YYSTYPE /* obsolescent; will be withdrawn */
# define YYSTYPE_IS_DECLARED 1
# define YYSTYPE_IS_TRIVIAL 1
#endif



/* Copy the second part of user declarations.  */


/* Line 216 of yacc.c.  */
#line 192 "tuple.tab.c"

#ifdef short
# undef short
#endif

#ifdef YYTYPE_UINT8
typedef YYTYPE_UINT8 yytype_uint8;
#else
typedef unsigned char yytype_uint8;
#endif

#ifdef YYTYPE_INT8
typedef YYTYPE_INT8 yytype_int8;
#elif (defined __STDC__ || defined __C99__FUNC__ \
     || defined __cplusplus || defined _MSC_VER)
typedef signed char yytype_int8;
#else
typedef short int yytype_int8;
#endif

#ifdef YYTYPE_UINT16
typedef YYTYPE_UINT16 yytype_uint16;
#else
typedef unsigned short int yytype_uint16;
#endif

#ifdef YYTYPE_INT16
typedef YYTYPE_INT16 yytype_int16;
#else
typedef short int yytype_int16;
#endif

#ifndef YYSIZE_T
# ifdef __SIZE_TYPE__
#  define YYSIZE_T __SIZE_TYPE__
# elif defined size_t
#  define YYSIZE_T size_t
# elif ! defined YYSIZE_T && (defined __STDC__ || defined __C99__FUNC__ \
     || defined __cplusplus || defined _MSC_VER)
#  include <stddef.h> /* INFRINGES ON USER NAME SPACE */
#  define YYSIZE_T size_t
# else
#  define YYSIZE_T unsigned int
# endif
#endif

#define YYSIZE_MAXIMUM ((YYSIZE_T) -1)

#ifndef YY_
# if defined YYENABLE_NLS && YYENABLE_NLS
#  if ENABLE_NLS
#   include <libintl.h> /* INFRINGES ON USER NAME SPACE */
#   define YY_(msgid) dgettext ("bison-runtime", msgid)
#  endif
# endif
# ifndef YY_
#  define YY_(msgid) msgid
# endif
#endif

/* Suppress unused-variable warnings by "using" E.  */
#if ! defined lint || defined __GNUC__
# define YYUSE(e) ((void) (e))
#else
# define YYUSE(e) /* empty */
#endif

/* Identity function, used to suppress warnings about constant conditions.  */
#ifndef lint
# define YYID(n) (n)
#else
#if (defined __STDC__ || defined __C99__FUNC__ \
     || defined __cplusplus || defined _MSC_VER)
static int
YYID (int i)
#else
static int
YYID (i)
    int i;
#endif
{
  return i;
}
#endif

#if ! defined yyoverflow || YYERROR_VERBOSE

/* The parser invokes alloca or malloc; define the necessary symbols.  */

# ifdef YYSTACK_USE_ALLOCA
#  if YYSTACK_USE_ALLOCA
#   ifdef __GNUC__
#    define YYSTACK_ALLOC __builtin_alloca
#   elif defined __BUILTIN_VA_ARG_INCR
#    include <alloca.h> /* INFRINGES ON USER NAME SPACE */
#   elif defined _AIX
#    define YYSTACK_ALLOC __alloca
#   elif defined _MSC_VER
#    include <malloc.h> /* INFRINGES ON USER NAME SPACE */
#    define alloca _alloca
#   else
#    define YYSTACK_ALLOC alloca
#    if ! defined _ALLOCA_H && ! defined _STDLIB_H && (defined __STDC__ || defined __C99__FUNC__ \
     || defined __cplusplus || defined _MSC_VER)
#     include <stdlib.h> /* INFRINGES ON USER NAME SPACE */
#     ifndef _STDLIB_H
#      define _STDLIB_H 1
#     endif
#    endif
#   endif
#  endif
# endif

# ifdef YYSTACK_ALLOC
   /* Pacify GCC's `empty if-body' warning.  */
#  define YYSTACK_FREE(Ptr) do { /* empty */; } while (YYID (0))
#  ifndef YYSTACK_ALLOC_MAXIMUM
    /* The OS might guarantee only one guard page at the bottom of the stack,
       and a page size can be as small as 4096 bytes.  So we cannot safely
       invoke alloca (N) if N exceeds 4096.  Use a slightly smaller number
       to allow for a few compiler-allocated temporary stack slots.  */
#   define YYSTACK_ALLOC_MAXIMUM 4032 /* reasonable circa 2006 */
#  endif
# else
#  define YYSTACK_ALLOC YYMALLOC
#  define YYSTACK_FREE YYFREE
#  ifndef YYSTACK_ALLOC_MAXIMUM
#   define YYSTACK_ALLOC_MAXIMUM YYSIZE_MAXIMUM
#  endif
#  if (defined __cplusplus && ! defined _STDLIB_H \
       && ! ((defined YYMALLOC || defined malloc) \
         && (defined YYFREE || defined free)))
#   include <stdlib.h> /* INFRINGES ON USER NAME SPACE */
#   ifndef _STDLIB_H
#    define _STDLIB_H 1
#   endif
#  endif
#  ifndef YYMALLOC
#   define YYMALLOC malloc
#   if ! defined malloc && ! defined _STDLIB_H && (defined __STDC__ || defined __C99__FUNC__ \
     || defined __cplusplus || defined _MSC_VER)
void *malloc (YYSIZE_T); /* INFRINGES ON USER NAME SPACE */
#   endif
#  endif
#  ifndef YYFREE
#   define YYFREE free
#   if ! defined free && ! defined _STDLIB_H && (defined __STDC__ || defined __C99__FUNC__ \
     || defined __cplusplus || defined _MSC_VER)
void free (void *); /* INFRINGES ON USER NAME SPACE */
#   endif
#  endif
# endif
#endif /* ! defined yyoverflow || YYERROR_VERBOSE */


#if (! defined yyoverflow \
     && (! defined __cplusplus \
     || (defined YYSTYPE_IS_TRIVIAL && YYSTYPE_IS_TRIVIAL)))

/* A type that is properly aligned for any stack member.  */
union yyalloc
{
  yytype_int16 yyss;
  YYSTYPE yyvs;
  };

/* The size of the maximum gap between one aligned stack and the next.  */
# define YYSTACK_GAP_MAXIMUM (sizeof (union yyalloc) - 1)

/* The size of an array large to enough to hold all stacks, each with
   N elements.  */
# define YYSTACK_BYTES(N) \
     ((N) * (sizeof (yytype_int16) + sizeof (YYSTYPE)) \
      + YYSTACK_GAP_MAXIMUM)

/* Copy COUNT objects from FROM to TO.  The source and destination do
   not overlap.  */
# ifndef YYCOPY
#  if defined __GNUC__ && 1 < __GNUC__
#   define YYCOPY(To, From, Count) \
      __builtin_memcpy (To, From, (Count) * sizeof (*(From)))
#  else
#   define YYCOPY(To, From, Count)        \
      do                    \
    {                    \
      YYSIZE_T yyi;                \
      for (yyi = 0; yyi < (Count); yyi++)    \
        (To)[yyi] = (From)[yyi];        \
    }                    \
      while (YYID (0))
#  endif
# endif

/* Relocate STACK from its old location to the new one.  The
   local variables YYSIZE and YYSTACKSIZE give the old and new number of
   elements in the stack, and YYPTR gives the new location of the
   stack.  Advance YYPTR to a properly aligned location for the next
   stack.  */
# define YYSTACK_RELOCATE(Stack)                    \
    do                                    \
      {                                    \
    YYSIZE_T yynewbytes;                        \
    YYCOPY (&yyptr->Stack, Stack, yysize);                \
    Stack = &yyptr->Stack;                        \
    yynewbytes = yystacksize * sizeof (*Stack) + YYSTACK_GAP_MAXIMUM; \
    yyptr += yynewbytes / sizeof (*yyptr);                \
      }                                    \
    while (YYID (0))

#endif

/* YYFINAL -- State number of the termination state.  */
#define YYFINAL  24
/* YYLAST -- Last index in YYTABLE.  */
#define YYLAST   65

/* YYNTOKENS -- Number of terminals.  */
#define YYNTOKENS  22
/* YYNNTS -- Number of nonterminals.  */
#define YYNNTS  19
/* YYNRULES -- Number of rules.  */
#define YYNRULES  32
/* YYNRULES -- Number of states.  */
#define YYNSTATES  78

/* YYTRANSLATE(YYLEX) -- Bison symbol number corresponding to YYLEX.  */
#define YYUNDEFTOK  2
#define YYMAXUTOK   276

#define YYTRANSLATE(YYX)                        \
  ((unsigned int) (YYX) <= YYMAXUTOK ? yytranslate[YYX] : YYUNDEFTOK)

/* YYTRANSLATE[YYLEX] -- Bison symbol number corresponding to YYLEX.  */
static const yytype_uint8 yytranslate[] =
{
       0,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     2,     2,     2,     2,
       2,     2,     2,     2,     2,     2,     1,     2,     3,     4,
       5,     6,     7,     8,     9,    10,    11,    12,    13,    14,
      15,    16,    17,    18,    19,    20,    21
};

#if YYDEBUG
/* YYPRHS[YYN] -- Index of the first RHS symbol of rule number YYN in
   YYRHS.  */
static const yytype_uint8 yyprhs[] =
{
       0,     0,     3,     5,     7,    10,    11,    13,    15,    17,
      19,    21,    23,    25,    27,    29,    37,    47,    57,    63,
      71,    77,    83,    89,    93,    95,    97,    99,   101,   104,
     106,   113,   118
};

/* YYRHS -- A `-1'-separated list of the rules' RHS.  */
static const yytype_int8 yyrhs[] =
{
      23,     0,    -1,    24,    -1,    25,    -1,    26,    25,    -1,
      -1,    27,    -1,    28,    -1,    29,    -1,    30,    -1,    31,
      -1,    32,    -1,    33,    -1,    34,    -1,    35,    -1,     3,
       9,     5,    37,     5,    36,     4,    -1,     3,    10,     5,
      37,     5,    37,     5,    36,     4,    -1,     3,    11,     5,
      37,     5,    37,     5,    40,     4,    -1,     3,    12,     5,
      36,     4,    -1,     3,    13,     5,    37,     5,    36,     4,
      -1,     3,    14,     5,    40,     4,    -1,     3,    15,     5,
      37,     4,    -1,     3,    16,     5,    36,     4,    -1,     3,
      17,     4,    -1,    37,    -1,    40,    -1,    38,    -1,    39,
      -1,    18,    40,    -1,    19,    -1,    20,     6,    38,     8,
      40,     7,    -1,    20,     6,    38,     7,    -1,    21,    -1
};

/* YYRLINE[YYN] -- source line where rule number YYN was defined.  */
static const yytype_uint8 yyrline[] =
{
       0,    69,    69,    70,    76,    83,    84,    84,    84,    84,
      84,    84,    84,    84,    84,    90,    97,   105,   113,   119,
     126,   132,   138,   144,   149,   149,   155,   161,   167,   173,
     180,   187,   193
};
#endif

#if YYDEBUG || YYERROR_VERBOSE || YYTOKEN_TABLE
/* YYTNAME[SYMBOL-NUM] -- String name of the symbol SYMBOL-NUM.
   First, the terminals, then, starting at YYNTOKENS, nonterminals.  */
static const char *const yytname[] =
{
  "$end", "error", "$undefined", "LPAREN", "RPAREN", "COMMA", "LSQBRACE",
  "RSQBRACE", "PLUS", "ASSIGN", "ADDI", "SUBI", "JUMP", "JNZ", "LABEL",
  "READI", "WRITEI", "EXIT", "REG", "REG_SP", "MEMORY", "NUMBER",
  "$accept", "accept", "program", "instr_list", "instr", "asn", "add",
  "sub", "jmp", "branch", "labl", "read", "write", "done", "arg", "regarg",
  "reg", "mem", "num", 0
};
#endif

# ifdef YYPRINT
/* YYTOKNUM[YYLEX-NUM] -- Internal token number corresponding to
   token YYLEX-NUM.  */
static const yytype_uint16 yytoknum[] =
{
       0,   256,   257,   258,   259,   260,   261,   262,   263,   264,
     265,   266,   267,   268,   269,   270,   271,   272,   273,   274,
     275,   276
};
# endif

/* YYR1[YYN] -- Symbol number of symbol that rule YYN derives.  */
static const yytype_uint8 yyr1[] =
{
       0,    22,    23,    24,    25,    25,    26,    26,    26,    26,
      26,    26,    26,    26,    26,    27,    28,    29,    30,    31,
      32,    33,    34,    35,    36,    36,    37,    37,    38,    38,
      39,    39,    40
};

/* YYR2[YYN] -- Number of symbols composing right hand side of rule YYN.  */
static const yytype_uint8 yyr2[] =
{
       0,     2,     1,     1,     2,     0,     1,     1,     1,     1,
       1,     1,     1,     1,     1,     7,     9,     9,     5,     7,
       5,     5,     5,     3,     1,     1,     1,     1,     2,     1,
       6,     4,     1
};

/* YYDEFACT[STATE-NAME] -- Default rule to reduce with in state
   STATE-NUM when YYTABLE doesn't specify something else to do.  Zero
   means the default is an error.  */
static const yytype_uint8 yydefact[] =
{
       5,     0,     0,     2,     3,     5,     6,     7,     8,     9,
      10,    11,    12,    13,    14,     0,     0,     0,     0,     0,
       0,     0,     0,     0,     1,     4,     0,     0,     0,     0,
       0,     0,     0,     0,    23,     0,    29,     0,     0,    26,
      27,     0,     0,    32,     0,    24,    25,     0,     0,     0,
       0,    28,     0,     0,     0,     0,    18,     0,    20,    21,
      22,     0,     0,     0,     0,     0,    31,     0,    15,     0,
       0,    19,     0,     0,     0,    30,    16,    17
};

/* YYDEFGOTO[NTERM-NUM].  */
static const yytype_int8 yydefgoto[] =
{
      -1,     2,     3,     4,     5,     6,     7,     8,     9,    10,
      11,    12,    13,    14,    44,    45,    39,    40,    46
};

/* YYPACT[STATE-NUM] -- Index in YYTABLE of the portion describing
   STATE-NUM.  */
#define YYPACT_NINF -33
static const yytype_int8 yypact[] =
{
       5,     3,    10,   -33,   -33,     5,   -33,   -33,   -33,   -33,
     -33,   -33,   -33,   -33,   -33,    27,    30,    33,    35,    36,
      37,    38,    39,    41,   -33,   -33,     4,     4,     4,     8,
       4,    25,     4,     8,   -33,    25,   -33,    42,    44,   -33,
     -33,    45,    46,   -33,    43,   -33,   -33,    47,    49,    50,
      51,   -33,   -16,     8,     4,     4,   -33,     8,   -33,   -33,
     -33,    23,    52,    53,    54,    56,   -33,    25,   -33,     8,
      25,   -33,    55,    57,    59,   -33,   -33,   -33
};

/* YYPGOTO[NTERM-NUM].  */
static const yytype_int8 yypgoto[] =
{
     -33,   -33,   -33,    60,   -33,   -33,   -33,   -33,   -33,   -33,
     -33,   -33,   -33,   -33,   -32,   -21,    12,   -33,   -31
};

/* YYTABLE[YYPACT[STATE-NUM]].  What to do in state STATE-NUM.  If
   positive, shift that token.  If negative, reduce the rule which
   number is the opposite.  If zero, do what YYDEFACT says.
   If YYTABLE_NINF, syntax error.  */
#define YYTABLE_NINF -1
static const yytype_uint8 yytable[] =
{
      48,    50,    35,    36,    51,    38,    41,    42,     1,    47,
      24,    49,    15,    16,    17,    18,    19,    20,    21,    22,
      23,    62,    35,    36,    37,    65,    35,    36,    37,    43,
      66,    67,    26,    63,    64,    27,    72,    73,    28,    74,
      29,    30,    31,    32,    33,    34,    43,    56,    52,    53,
      54,    55,    57,    58,    59,    60,    68,     0,    69,    70,
      71,    76,    75,    77,    61,    25
};

static const yytype_int8 yycheck[] =
{
      31,    33,    18,    19,    35,    26,    27,    28,     3,    30,
       0,    32,     9,    10,    11,    12,    13,    14,    15,    16,
      17,    53,    18,    19,    20,    57,    18,    19,    20,    21,
       7,     8,     5,    54,    55,     5,    67,    69,     5,    70,
       5,     5,     5,     5,     5,     4,    21,     4,     6,     5,
       5,     5,     5,     4,     4,     4,     4,    -1,     5,     5,
       4,     4,     7,     4,    52,     5
};

/* YYSTOS[STATE-NUM] -- The (internal number of the) accessing
   symbol of state STATE-NUM.  */
static const yytype_uint8 yystos[] =
{
       0,     3,    23,    24,    25,    26,    27,    28,    29,    30,
      31,    32,    33,    34,    35,     9,    10,    11,    12,    13,
      14,    15,    16,    17,     0,    25,     5,     5,     5,     5,
       5,     5,     5,     5,     4,    18,    19,    20,    37,    38,
      39,    37,    37,    21,    36,    37,    40,    37,    40,    37,
      36,    40,     6,     5,     5,     5,     4,     5,     4,     4,
       4,    38,    36,    37,    37,    36,     7,     8,     4,     5,
       5,     4,    40,    36,    40,     7,     4,     4
};

#define yyerrok        (yyerrstatus = 0)
#define yyclearin    (yychar = YYEMPTY)
#define YYEMPTY        (-2)
#define YYEOF        0

#define YYACCEPT    goto yyacceptlab
#define YYABORT        goto yyabortlab
#define YYERROR        goto yyerrorlab


/* Like YYERROR except do call yyerror.  This remains here temporarily
   to ease the transition to the new meaning of YYERROR, for GCC.
   Once GCC version 2 has supplanted version 1, this can go.  */

#define YYFAIL        goto yyerrlab

#define YYRECOVERING()  (!!yyerrstatus)

#define YYBACKUP(Token, Value)                    \
do                                \
  if (yychar == YYEMPTY && yylen == 1)                \
    {                                \
      yychar = (Token);                        \
      yylval = (Value);                        \
      yytoken = YYTRANSLATE (yychar);                \
      YYPOPSTACK (1);                        \
      goto yybackup;                        \
    }                                \
  else                                \
    {                                \
      yyerror (YY_("syntax error: cannot back up")); \
      YYERROR;                            \
    }                                \
while (YYID (0))


#define YYTERROR    1
#define YYERRCODE    256


/* YYLLOC_DEFAULT -- Set CURRENT to span from RHS[1] to RHS[N].
   If N is 0, then set CURRENT to the empty location which ends
   the previous symbol: RHS[0] (always defined).  */

#define YYRHSLOC(Rhs, K) ((Rhs)[K])
#ifndef YYLLOC_DEFAULT
# define YYLLOC_DEFAULT(Current, Rhs, N)                \
    do                                    \
      if (YYID (N))                                                    \
    {                                \
      (Current).first_line   = YYRHSLOC (Rhs, 1).first_line;    \
      (Current).first_column = YYRHSLOC (Rhs, 1).first_column;    \
      (Current).last_line    = YYRHSLOC (Rhs, N).last_line;        \
      (Current).last_column  = YYRHSLOC (Rhs, N).last_column;    \
    }                                \
      else                                \
    {                                \
      (Current).first_line   = (Current).last_line   =        \
        YYRHSLOC (Rhs, 0).last_line;                \
      (Current).first_column = (Current).last_column =        \
        YYRHSLOC (Rhs, 0).last_column;                \
    }                                \
    while (YYID (0))
#endif


/* YY_LOCATION_PRINT -- Print the location on the stream.
   This macro was not mandated originally: define only if we know
   we won't break user code: when these are the locations we know.  */

#ifndef YY_LOCATION_PRINT
# if defined YYLTYPE_IS_TRIVIAL && YYLTYPE_IS_TRIVIAL
#  define YY_LOCATION_PRINT(File, Loc)            \
     fprintf (File, "%d.%d-%d.%d",            \
          (Loc).first_line, (Loc).first_column,    \
          (Loc).last_line,  (Loc).last_column)
# else
#  define YY_LOCATION_PRINT(File, Loc) ((void) 0)
# endif
#endif


/* YYLEX -- calling `yylex' with the right arguments.  */

#ifdef YYLEX_PARAM
# define YYLEX yylex (YYLEX_PARAM)
#else
# define YYLEX yylex ()
#endif

/* Enable debugging if requested.  */
#if YYDEBUG

# ifndef YYFPRINTF
#  include <stdio.h> /* INFRINGES ON USER NAME SPACE */
#  define YYFPRINTF fprintf
# endif

# define YYDPRINTF(Args)            \
do {                        \
  if (yydebug)                    \
    YYFPRINTF Args;                \
} while (YYID (0))

# define YY_SYMBOL_PRINT(Title, Type, Value, Location)              \
do {                                      \
  if (yydebug)                                  \
    {                                      \
      YYFPRINTF (stderr, "%s ", Title);                      \
      yy_symbol_print (stderr,                          \
          Type, Value); \
      YYFPRINTF (stderr, "\n");                          \
    }                                      \
} while (YYID (0))


/*--------------------------------.
| Print this symbol on YYOUTPUT.  |
`--------------------------------*/

/*ARGSUSED*/
#if (defined __STDC__ || defined __C99__FUNC__ \
     || defined __cplusplus || defined _MSC_VER)
static void
yy_symbol_value_print (FILE *yyoutput, int yytype, YYSTYPE const * const yyvaluep)
#else
static void
yy_symbol_value_print (yyoutput, yytype, yyvaluep)
    FILE *yyoutput;
    int yytype;
    YYSTYPE const * const yyvaluep;
#endif
{
  if (!yyvaluep)
    return;
# ifdef YYPRINT
  if (yytype < YYNTOKENS)
    YYPRINT (yyoutput, yytoknum[yytype], *yyvaluep);
# else
  YYUSE (yyoutput);
# endif
  switch (yytype)
    {
      default:
    break;
    }
}


/*--------------------------------.
| Print this symbol on YYOUTPUT.  |
`--------------------------------*/

#if (defined __STDC__ || defined __C99__FUNC__ \
     || defined __cplusplus || defined _MSC_VER)
static void
yy_symbol_print (FILE *yyoutput, int yytype, YYSTYPE const * const yyvaluep)
#else
static void
yy_symbol_print (yyoutput, yytype, yyvaluep)
    FILE *yyoutput;
    int yytype;
    YYSTYPE const * const yyvaluep;
#endif
{
  if (yytype < YYNTOKENS)
    YYFPRINTF (yyoutput, "token %s (", yytname[yytype]);
  else
    YYFPRINTF (yyoutput, "nterm %s (", yytname[yytype]);

  yy_symbol_value_print (yyoutput, yytype, yyvaluep);
  YYFPRINTF (yyoutput, ")");
}

/*------------------------------------------------------------------.
| yy_stack_print -- Print the state stack from its BOTTOM up to its |
| TOP (included).                                                   |
`------------------------------------------------------------------*/

#if (defined __STDC__ || defined __C99__FUNC__ \
     || defined __cplusplus || defined _MSC_VER)
static void
yy_stack_print (yytype_int16 *bottom, yytype_int16 *top)
#else
static void
yy_stack_print (bottom, top)
    yytype_int16 *bottom;
    yytype_int16 *top;
#endif
{
  YYFPRINTF (stderr, "Stack now");
  for (; bottom <= top; ++bottom)
    YYFPRINTF (stderr, " %d", *bottom);
  YYFPRINTF (stderr, "\n");
}

# define YY_STACK_PRINT(Bottom, Top)                \
do {                                \
  if (yydebug)                            \
    yy_stack_print ((Bottom), (Top));                \
} while (YYID (0))


/*------------------------------------------------.
| Report that the YYRULE is going to be reduced.  |
`------------------------------------------------*/

#if (defined __STDC__ || defined __C99__FUNC__ \
     || defined __cplusplus || defined _MSC_VER)
static void
yy_reduce_print (YYSTYPE *yyvsp, int yyrule)
#else
static void
yy_reduce_print (yyvsp, yyrule)
    YYSTYPE *yyvsp;
    int yyrule;
#endif
{
  int yynrhs = yyr2[yyrule];
  int yyi;
  unsigned long int yylno = yyrline[yyrule];
  YYFPRINTF (stderr, "Reducing stack by rule %d (line %lu):\n",
         yyrule - 1, yylno);
  /* The symbols being reduced.  */
  for (yyi = 0; yyi < yynrhs; yyi++)
    {
      fprintf (stderr, "   $%d = ", yyi + 1);
      yy_symbol_print (stderr, yyrhs[yyprhs[yyrule] + yyi],
               &(yyvsp[(yyi + 1) - (yynrhs)])
                              );
      fprintf (stderr, "\n");
    }
}

# define YY_REDUCE_PRINT(Rule)        \
do {                    \
  if (yydebug)                \
    yy_reduce_print (yyvsp, Rule); \
} while (YYID (0))

/* Nonzero means print parse trace.  It is left uninitialized so that
   multiple parsers can coexist.  */
int yydebug;
#else /* !YYDEBUG */
# define YYDPRINTF(Args)
# define YY_SYMBOL_PRINT(Title, Type, Value, Location)
# define YY_STACK_PRINT(Bottom, Top)
# define YY_REDUCE_PRINT(Rule)
#endif /* !YYDEBUG */


/* YYINITDEPTH -- initial size of the parser's stacks.  */
#ifndef    YYINITDEPTH
# define YYINITDEPTH 200
#endif

/* YYMAXDEPTH -- maximum size the stacks can grow to (effective only
   if the built-in stack extension method is used).

   Do not make this value too large; the results are undefined if
   YYSTACK_ALLOC_MAXIMUM < YYSTACK_BYTES (YYMAXDEPTH)
   evaluated with infinite-precision integer arithmetic.  */

#ifndef YYMAXDEPTH
# define YYMAXDEPTH 10000
#endif



#if YYERROR_VERBOSE

# ifndef yystrlen
#  if defined __GLIBC__ && defined _STRING_H
#   define yystrlen strlen
#  else
/* Return the length of YYSTR.  */
#if (defined __STDC__ || defined __C99__FUNC__ \
     || defined __cplusplus || defined _MSC_VER)
static YYSIZE_T
yystrlen (const char *yystr)
#else
static YYSIZE_T
yystrlen (yystr)
    const char *yystr;
#endif
{
  YYSIZE_T yylen;
  for (yylen = 0; yystr[yylen]; yylen++)
    continue;
  return yylen;
}
#  endif
# endif

# ifndef yystpcpy
#  if defined __GLIBC__ && defined _STRING_H && defined _GNU_SOURCE
#   define yystpcpy stpcpy
#  else
/* Copy YYSRC to YYDEST, returning the address of the terminating '\0' in
   YYDEST.  */
#if (defined __STDC__ || defined __C99__FUNC__ \
     || defined __cplusplus || defined _MSC_VER)
static char *
yystpcpy (char *yydest, const char *yysrc)
#else
static char *
yystpcpy (yydest, yysrc)
    char *yydest;
    const char *yysrc;
#endif
{
  char *yyd = yydest;
  const char *yys = yysrc;

  while ((*yyd++ = *yys++) != '\0')
    continue;

  return yyd - 1;
}
#  endif
# endif

# ifndef yytnamerr
/* Copy to YYRES the contents of YYSTR after stripping away unnecessary
   quotes and backslashes, so that it's suitable for yyerror.  The
   heuristic is that double-quoting is unnecessary unless the string
   contains an apostrophe, a comma, or backslash (other than
   backslash-backslash).  YYSTR is taken from yytname.  If YYRES is
   null, do not copy; instead, return the length of what the result
   would have been.  */
static YYSIZE_T
yytnamerr (char *yyres, const char *yystr)
{
  if (*yystr == '"')
    {
      YYSIZE_T yyn = 0;
      char const *yyp = yystr;

      for (;;)
    switch (*++yyp)
      {
      case '\'':
      case ',':
        goto do_not_strip_quotes;

      case '\\':
        if (*++yyp != '\\')
          goto do_not_strip_quotes;
        /* Fall through.  */
      default:
        if (yyres)
          yyres[yyn] = *yyp;
        yyn++;
        break;

      case '"':
        if (yyres)
          yyres[yyn] = '\0';
        return yyn;
      }
    do_not_strip_quotes: ;
    }

  if (! yyres)
    return yystrlen (yystr);

  return yystpcpy (yyres, yystr) - yyres;
}
# endif

/* Copy into YYRESULT an error message about the unexpected token
   YYCHAR while in state YYSTATE.  Return the number of bytes copied,
   including the terminating null byte.  If YYRESULT is null, do not
   copy anything; just return the number of bytes that would be
   copied.  As a special case, return 0 if an ordinary "syntax error"
   message will do.  Return YYSIZE_MAXIMUM if overflow occurs during
   size calculation.  */
static YYSIZE_T
yysyntax_error (char *yyresult, int yystate, int yychar)
{
  int yyn = yypact[yystate];

  if (! (YYPACT_NINF < yyn && yyn <= YYLAST))
    return 0;
  else
    {
      int yytype = YYTRANSLATE (yychar);
      YYSIZE_T yysize0 = yytnamerr (0, yytname[yytype]);
      YYSIZE_T yysize = yysize0;
      YYSIZE_T yysize1;
      int yysize_overflow = 0;
      enum { YYERROR_VERBOSE_ARGS_MAXIMUM = 5 };
      char const *yyarg[YYERROR_VERBOSE_ARGS_MAXIMUM];
      int yyx;

# if 0
      /* This is so xgettext sees the translatable formats that are
     constructed on the fly.  */
      YY_("syntax error, unexpected %s");
      YY_("syntax error, unexpected %s, expecting %s");
      YY_("syntax error, unexpected %s, expecting %s or %s");
      YY_("syntax error, unexpected %s, expecting %s or %s or %s");
      YY_("syntax error, unexpected %s, expecting %s or %s or %s or %s");
# endif
      char *yyfmt;
      char const *yyf;
      static char const yyunexpected[] = "syntax error, unexpected %s";
      static char const yyexpecting[] = ", expecting %s";
      static char const yyor[] = " or %s";
      char yyformat[sizeof yyunexpected
            + sizeof yyexpecting - 1
            + ((YYERROR_VERBOSE_ARGS_MAXIMUM - 2)
               * (sizeof yyor - 1))];
      char const *yyprefix = yyexpecting;

      /* Start YYX at -YYN if negative to avoid negative indexes in
     YYCHECK.  */
      int yyxbegin = yyn < 0 ? -yyn : 0;

      /* Stay within bounds of both yycheck and yytname.  */
      int yychecklim = YYLAST - yyn + 1;
      int yyxend = yychecklim < YYNTOKENS ? yychecklim : YYNTOKENS;
      int yycount = 1;

      yyarg[0] = yytname[yytype];
      yyfmt = yystpcpy (yyformat, yyunexpected);

      for (yyx = yyxbegin; yyx < yyxend; ++yyx)
    if (yycheck[yyx + yyn] == yyx && yyx != YYTERROR)
      {
        if (yycount == YYERROR_VERBOSE_ARGS_MAXIMUM)
          {
        yycount = 1;
        yysize = yysize0;
        yyformat[sizeof yyunexpected - 1] = '\0';
        break;
          }
        yyarg[yycount++] = yytname[yyx];
        yysize1 = yysize + yytnamerr (0, yytname[yyx]);
        yysize_overflow |= (yysize1 < yysize);
        yysize = yysize1;
        yyfmt = yystpcpy (yyfmt, yyprefix);
        yyprefix = yyor;
      }

      yyf = YY_(yyformat);
      yysize1 = yysize + yystrlen (yyf);
      yysize_overflow |= (yysize1 < yysize);
      yysize = yysize1;

      if (yysize_overflow)
    return YYSIZE_MAXIMUM;

      if (yyresult)
    {
      /* Avoid sprintf, as that infringes on the user's name space.
         Don't have undefined behavior even if the translation
         produced a string with the wrong number of "%s"s.  */
      char *yyp = yyresult;
      int yyi = 0;
      while ((*yyp = *yyf) != '\0')
        {
          if (*yyp == '%' && yyf[1] == 's' && yyi < yycount)
        {
          yyp += yytnamerr (yyp, yyarg[yyi++]);
          yyf += 2;
        }
          else
        {
          yyp++;
          yyf++;
        }
        }
    }
      return yysize;
    }
}
#endif /* YYERROR_VERBOSE */


/*-----------------------------------------------.
| Release the memory associated to this symbol.  |
`-----------------------------------------------*/

/*ARGSUSED*/
#if (defined __STDC__ || defined __C99__FUNC__ \
     || defined __cplusplus || defined _MSC_VER)
static void
yydestruct (const char *yymsg, int yytype, YYSTYPE *yyvaluep)
#else
static void
yydestruct (yymsg, yytype, yyvaluep)
    const char *yymsg;
    int yytype;
    YYSTYPE *yyvaluep;
#endif
{
  YYUSE (yyvaluep);

  if (!yymsg)
    yymsg = "Deleting";
  YY_SYMBOL_PRINT (yymsg, yytype, yyvaluep, yylocationp);

  switch (yytype)
    {

      default:
    break;
    }
}


/* Prevent warnings from -Wmissing-prototypes.  */

#ifdef YYPARSE_PARAM
#if defined __STDC__ || defined __cplusplus
int yyparse (void *YYPARSE_PARAM);
#else
int yyparse ();
#endif
#else /* ! YYPARSE_PARAM */
#if defined __STDC__ || defined __cplusplus
int yyparse (void);
#else
int yyparse ();
#endif
#endif /* ! YYPARSE_PARAM */



/* The look-ahead symbol.  */
int yychar;

/* The semantic value of the look-ahead symbol.  */
YYSTYPE yylval;

/* Number of syntax errors so far.  */
int yynerrs;



/*----------.
| yyparse.  |
`----------*/

#ifdef YYPARSE_PARAM
#if (defined __STDC__ || defined __C99__FUNC__ \
     || defined __cplusplus || defined _MSC_VER)
int
yyparse (void *YYPARSE_PARAM)
#else
int
yyparse (YYPARSE_PARAM)
    void *YYPARSE_PARAM;
#endif
#else /* ! YYPARSE_PARAM */
#if (defined __STDC__ || defined __C99__FUNC__ \
     || defined __cplusplus || defined _MSC_VER)
int
yyparse (void)
#else
int
yyparse ()

#endif
#endif
{
  
  int yystate;
  int yyn;
  int yyresult;
  /* Number of tokens to shift before error messages enabled.  */
  int yyerrstatus;
  /* Look-ahead token as an internal (translated) token number.  */
  int yytoken = 0;
#if YYERROR_VERBOSE
  /* Buffer for error messages, and its allocated size.  */
  char yymsgbuf[128];
  char *yymsg = yymsgbuf;
  YYSIZE_T yymsg_alloc = sizeof yymsgbuf;
#endif

  /* Three stacks and their tools:
     `yyss': related to states,
     `yyvs': related to semantic values,
     `yyls': related to locations.

     Refer to the stacks thru separate pointers, to allow yyoverflow
     to reallocate them elsewhere.  */

  /* The state stack.  */
  yytype_int16 yyssa[YYINITDEPTH];
  yytype_int16 *yyss = yyssa;
  yytype_int16 *yyssp;

  /* The semantic value stack.  */
  YYSTYPE yyvsa[YYINITDEPTH];
  YYSTYPE *yyvs = yyvsa;
  YYSTYPE *yyvsp;



#define YYPOPSTACK(N)   (yyvsp -= (N), yyssp -= (N))

  YYSIZE_T yystacksize = YYINITDEPTH;

  /* The variables used to return semantic value and location from the
     action routines.  */
  YYSTYPE yyval;


  /* The number of symbols on the RHS of the reduced rule.
     Keep to zero when no symbol should be popped.  */
  int yylen = 0;

  YYDPRINTF ((stderr, "Starting parse\n"));

  yystate = 0;
  yyerrstatus = 0;
  yynerrs = 0;
  yychar = YYEMPTY;        /* Cause a token to be read.  */

  /* Initialize stack pointers.
     Waste one element of value and location stack
     so that they stay on the same level as the state stack.
     The wasted elements are never initialized.  */

  yyssp = yyss;
  yyvsp = yyvs;

  goto yysetstate;

/*------------------------------------------------------------.
| yynewstate -- Push a new state, which is found in yystate.  |
`------------------------------------------------------------*/
 yynewstate:
  /* In all cases, when you get here, the value and location stacks
     have just been pushed.  So pushing a state here evens the stacks.  */
  yyssp++;

 yysetstate:
  *yyssp = yystate;

  if (yyss + yystacksize - 1 <= yyssp)
    {
      /* Get the current used size of the three stacks, in elements.  */
      YYSIZE_T yysize = yyssp - yyss + 1;

#ifdef yyoverflow
      {
    /* Give user a chance to reallocate the stack.  Use copies of
       these so that the &'s don't force the real ones into
       memory.  */
    YYSTYPE *yyvs1 = yyvs;
    yytype_int16 *yyss1 = yyss;


    /* Each stack pointer address is followed by the size of the
       data in use in that stack, in bytes.  This used to be a
       conditional around just the two extra args, but that might
       be undefined if yyoverflow is a macro.  */
    yyoverflow (YY_("memory exhausted"),
            &yyss1, yysize * sizeof (*yyssp),
            &yyvs1, yysize * sizeof (*yyvsp),

            &yystacksize);

    yyss = yyss1;
    yyvs = yyvs1;
      }
#else /* no yyoverflow */
# ifndef YYSTACK_RELOCATE
      goto yyexhaustedlab;
# else
      /* Extend the stack our own way.  */
      if (YYMAXDEPTH <= yystacksize)
    goto yyexhaustedlab;
      yystacksize *= 2;
      if (YYMAXDEPTH < yystacksize)
    yystacksize = YYMAXDEPTH;

      {
    yytype_int16 *yyss1 = yyss;
    union yyalloc *yyptr =
      (union yyalloc *) YYSTACK_ALLOC (YYSTACK_BYTES (yystacksize));
    if (! yyptr)
      goto yyexhaustedlab;
    YYSTACK_RELOCATE (yyss);
    YYSTACK_RELOCATE (yyvs);

#  undef YYSTACK_RELOCATE
    if (yyss1 != yyssa)
      YYSTACK_FREE (yyss1);
      }
# endif
#endif /* no yyoverflow */

      yyssp = yyss + yysize - 1;
      yyvsp = yyvs + yysize - 1;


      YYDPRINTF ((stderr, "Stack size increased to %lu\n",
          (unsigned long int) yystacksize));

      if (yyss + yystacksize - 1 <= yyssp)
    YYABORT;
    }

  YYDPRINTF ((stderr, "Entering state %d\n", yystate));

  goto yybackup;

/*-----------.
| yybackup.  |
`-----------*/
yybackup:

  /* Do appropriate processing given the current state.  Read a
     look-ahead token if we need one and don't already have one.  */

  /* First try to decide what to do without reference to look-ahead token.  */
  yyn = yypact[yystate];
  if (yyn == YYPACT_NINF)
    goto yydefault;

  /* Not known => get a look-ahead token if don't already have one.  */

  /* YYCHAR is either YYEMPTY or YYEOF or a valid look-ahead symbol.  */
  if (yychar == YYEMPTY)
    {
      YYDPRINTF ((stderr, "Reading a token: "));
      yychar = YYLEX;
    }

  if (yychar <= YYEOF)
    {
      yychar = yytoken = YYEOF;
      YYDPRINTF ((stderr, "Now at end of input.\n"));
    }
  else
    {
      yytoken = YYTRANSLATE (yychar);
      YY_SYMBOL_PRINT ("Next token is", yytoken, &yylval, &yylloc);
    }

  /* If the proper action on seeing token YYTOKEN is to reduce or to
     detect an error, take that action.  */
  yyn += yytoken;
  if (yyn < 0 || YYLAST < yyn || yycheck[yyn] != yytoken)
    goto yydefault;
  yyn = yytable[yyn];
  if (yyn <= 0)
    {
      if (yyn == 0 || yyn == YYTABLE_NINF)
    goto yyerrlab;
      yyn = -yyn;
      goto yyreduce;
    }

  if (yyn == YYFINAL)
    YYACCEPT;

  /* Count tokens shifted since error; after three, turn off error
     status.  */
  if (yyerrstatus)
    yyerrstatus--;

  /* Shift the look-ahead token.  */
  YY_SYMBOL_PRINT ("Shifting", yytoken, &yylval, &yylloc);

  /* Discard the shifted token unless it is eof.  */
  if (yychar != YYEOF)
    yychar = YYEMPTY;

  yystate = yyn;
  *++yyvsp = yylval;

  goto yynewstate;


/*-----------------------------------------------------------.
| yydefault -- do the default action for the current state.  |
`-----------------------------------------------------------*/
yydefault:
  yyn = yydefact[yystate];
  if (yyn == 0)
    goto yyerrlab;
  goto yyreduce;


/*-----------------------------.
| yyreduce -- Do a reduction.  |
`-----------------------------*/
yyreduce:
  /* yyn is the number of a rule to reduce with.  */
  yylen = yyr2[yyn];

  /* If YYLEN is nonzero, implement the default value of the action:
     `$$ = $1'.

     Otherwise, the following line sets YYVAL to garbage.
     This behavior is undocumented and Bison
     users should not rely upon it.  Assigning to YYVAL
     unconditionally makes the parser a bit smaller, and it avoids a
     GCC warning that YYVAL may be used uninitialized.  */
  yyval = yyvsp[1-yylen];


  YY_REDUCE_PRINT (yyn);
  switch (yyn)
    {
        case 2:
#line 69 "tuple.y"
    { return (int)(yyval.node_ptr); ;}
    break;

  case 3:
#line 71 "tuple.y"
    {
    node* n = node_alloc( PROGRAM );
    n->child1 = (yyvsp[(1) - (1)].node_ptr);
    (yyval.node_ptr) = n;
;}
    break;

  case 4:
#line 77 "tuple.y"
    {
    node* n =node_alloc (INSTR_LIST);
    n->child1 = (yyvsp[(1) - (2)].node_ptr);
    n->child2 = (yyvsp[(2) - (2)].node_ptr);
    (yyval.node_ptr) = n;
;}
    break;

  case 5:
#line 83 "tuple.y"
    { (yyval.node_ptr) = NULL; ;}
    break;

  case 14:
#line 85 "tuple.y"
    {
    node* n = node_alloc ( INSTR );
    n->child1 = (yyvsp[(1) - (1)].node_ptr);
    (yyval.node_ptr) = n;
;}
    break;

  case 15:
#line 91 "tuple.y"
    {
    node * n = node_alloc ( ASN);
    n-> child1 = (yyvsp[(4) - (7)].node_ptr);
    n->child2 = (yyvsp[(6) - (7)].node_ptr);
    (yyval.node_ptr) = n;
;}
    break;

  case 16:
#line 98 "tuple.y"
    {
    node * n = node_alloc (ADD);
    n->child1 = (yyvsp[(4) - (9)].node_ptr);
    n->child2 = (yyvsp[(6) - (9)].node_ptr);
    n->child3 = (yyvsp[(8) - (9)].node_ptr);
    (yyval.node_ptr) = n;
;}
    break;

  case 17:
#line 106 "tuple.y"
    {
    node * n = node_alloc (SUB);
    n->child1 = (yyvsp[(4) - (9)].node_ptr);
    n->child2 = (yyvsp[(6) - (9)].node_ptr);
    n->child3 = (yyvsp[(8) - (9)].node_ptr);
    (yyval.node_ptr) = n;
;}
    break;

  case 18:
#line 114 "tuple.y"
    {
    node * n = node_alloc (JMP);
    n->child1 = (yyvsp[(4) - (5)].node_ptr);
    (yyval.node_ptr) = n;
;}
    break;

  case 19:
#line 120 "tuple.y"
    {
    node * n = node_alloc (BRANCH);
    n->child1 = (yyvsp[(4) - (7)].node_ptr);
    n->child2 = (yyvsp[(6) - (7)].node_ptr);
    (yyval.node_ptr) = n;
;}
    break;

  case 20:
#line 127 "tuple.y"
    {
    node * n = node_alloc (LABL);
    n->child1 = (yyvsp[(4) - (5)].node_ptr);
    (yyval.node_ptr) = n;
;}
    break;

  case 21:
#line 133 "tuple.y"
    {
    node * n = node_alloc (READ);
    n->child1 = (yyvsp[(4) - (5)].node_ptr);
    (yyval.node_ptr) = n;
;}
    break;

  case 22:
#line 139 "tuple.y"
    {
    node * n = node_alloc (WRITE);
    n->child1 = (yyvsp[(4) - (5)].node_ptr);
    (yyval.node_ptr) = n;
;}
    break;

  case 23:
#line 145 "tuple.y"
    {
    node * n = node_alloc (DONE);
    (yyval.node_ptr) = n;
;}
    break;

  case 25:
#line 150 "tuple.y"
    {
    node * n = node_alloc (ARG);
    n->child1 = (yyvsp[(1) - (1)].node_ptr);
    (yyval.node_ptr) = n;
;}
    break;

  case 26:
#line 156 "tuple.y"
    { 
    node * n = node_alloc (REGARG);
    n->child1 = (yyvsp[(1) - (1)].node_ptr);
    (yyval.node_ptr) = n;
;}
    break;

  case 27:
#line 162 "tuple.y"
    {
    node * n = node_alloc (REGARG);
    n->child1 = (yyvsp[(1) - (1)].node_ptr);
    (yyval.node_ptr) = n;
;}
    break;

  case 28:
#line 168 "tuple.y"
    {
    node * n = node_alloc ( REG_NUM);
    n->child1 = (yyvsp[(2) - (2)].node_ptr);
    (yyval.node_ptr) = n;
;}
    break;

  case 29:
#line 174 "tuple.y"
    {
    node * n = node_alloc (REG_SPECIAL);
    if ((n->data = malloc ( strlen( yytext) + 1))  == NULL ) { printf("malloc error\n"); exit(1); }
    strcpy (n->data, yytext);
    (yyval.node_ptr) = n;
;}
    break;

  case 30:
#line 181 "tuple.y"
    {
    node * n = node_alloc (MEM);
    n->child1 = (yyvsp[(3) - (6)].node_ptr);
    n->child2 = (yyvsp[(5) - (6)].node_ptr);
    (yyval.node_ptr) = n;
;}
    break;

  case 31:
#line 188 "tuple.y"
    { 
    node * n = node_alloc (MEM);
    n->child1 = (yyvsp[(3) - (4)].node_ptr);
    (yyval.node_ptr) = n;
;}
    break;

  case 32:
#line 194 "tuple.y"
    {
    node * n = node_alloc (NUM);
    if ((n->data = malloc (sizeof(int)) ) == NULL ) { printf("Malloc err\n"); exit (1); }
    *(int*)n->data = atoi(yytext);
    (yyval.node_ptr) = n;
;}
    break;


/* Line 1267 of yacc.c.  */
#line 1636 "tuple.tab.c"
      default: break;
    }
  YY_SYMBOL_PRINT ("-> $$ =", yyr1[yyn], &yyval, &yyloc);

  YYPOPSTACK (yylen);
  yylen = 0;
  YY_STACK_PRINT (yyss, yyssp);

  *++yyvsp = yyval;


  /* Now `shift' the result of the reduction.  Determine what state
     that goes to, based on the state we popped back to and the rule
     number reduced by.  */

  yyn = yyr1[yyn];

  yystate = yypgoto[yyn - YYNTOKENS] + *yyssp;
  if (0 <= yystate && yystate <= YYLAST && yycheck[yystate] == *yyssp)
    yystate = yytable[yystate];
  else
    yystate = yydefgoto[yyn - YYNTOKENS];

  goto yynewstate;


/*------------------------------------.
| yyerrlab -- here on detecting error |
`------------------------------------*/
yyerrlab:
  /* If not already recovering from an error, report this error.  */
  if (!yyerrstatus)
    {
      ++yynerrs;
#if ! YYERROR_VERBOSE
      yyerror (YY_("syntax error"));
#else
      {
    YYSIZE_T yysize = yysyntax_error (0, yystate, yychar);
    if (yymsg_alloc < yysize && yymsg_alloc < YYSTACK_ALLOC_MAXIMUM)
      {
        YYSIZE_T yyalloc = 2 * yysize;
        if (! (yysize <= yyalloc && yyalloc <= YYSTACK_ALLOC_MAXIMUM))
          yyalloc = YYSTACK_ALLOC_MAXIMUM;
        if (yymsg != yymsgbuf)
          YYSTACK_FREE (yymsg);
        yymsg = (char *) YYSTACK_ALLOC (yyalloc);
        if (yymsg)
          yymsg_alloc = yyalloc;
        else
          {
        yymsg = yymsgbuf;
        yymsg_alloc = sizeof yymsgbuf;
          }
      }

    if (0 < yysize && yysize <= yymsg_alloc)
      {
        (void) yysyntax_error (yymsg, yystate, yychar);
        yyerror (yymsg);
      }
    else
      {
        yyerror (YY_("syntax error"));
        if (yysize != 0)
          goto yyexhaustedlab;
      }
      }
#endif
    }



  if (yyerrstatus == 3)
    {
      /* If just tried and failed to reuse look-ahead token after an
     error, discard it.  */

      if (yychar <= YYEOF)
    {
      /* Return failure if at end of input.  */
      if (yychar == YYEOF)
        YYABORT;
    }
      else
    {
      yydestruct ("Error: discarding",
              yytoken, &yylval);
      yychar = YYEMPTY;
    }
    }

  /* Else will try to reuse look-ahead token after shifting the error
     token.  */
  goto yyerrlab1;


/*---------------------------------------------------.
| yyerrorlab -- error raised explicitly by YYERROR.  |
`---------------------------------------------------*/
yyerrorlab:

  /* Pacify compilers like GCC when the user code never invokes
     YYERROR and the label yyerrorlab therefore never appears in user
     code.  */
  if (/*CONSTCOND*/ 0)
     goto yyerrorlab;

  /* Do not reclaim the symbols of the rule which action triggered
     this YYERROR.  */
  YYPOPSTACK (yylen);
  yylen = 0;
  YY_STACK_PRINT (yyss, yyssp);
  yystate = *yyssp;
  goto yyerrlab1;


/*-------------------------------------------------------------.
| yyerrlab1 -- common code for both syntax error and YYERROR.  |
`-------------------------------------------------------------*/
yyerrlab1:
  yyerrstatus = 3;    /* Each real token shifted decrements this.  */

  for (;;)
    {
      yyn = yypact[yystate];
      if (yyn != YYPACT_NINF)
    {
      yyn += YYTERROR;
      if (0 <= yyn && yyn <= YYLAST && yycheck[yyn] == YYTERROR)
        {
          yyn = yytable[yyn];
          if (0 < yyn)
        break;
        }
    }

      /* Pop the current state because it cannot handle the error token.  */
      if (yyssp == yyss)
    YYABORT;


      yydestruct ("Error: popping",
          yystos[yystate], yyvsp);
      YYPOPSTACK (1);
      yystate = *yyssp;
      YY_STACK_PRINT (yyss, yyssp);
    }

  if (yyn == YYFINAL)
    YYACCEPT;

  *++yyvsp = yylval;


  /* Shift the error token.  */
  YY_SYMBOL_PRINT ("Shifting", yystos[yyn], yyvsp, yylsp);

  yystate = yyn;
  goto yynewstate;


/*-------------------------------------.
| yyacceptlab -- YYACCEPT comes here.  |
`-------------------------------------*/
yyacceptlab:
  yyresult = 0;
  goto yyreturn;

/*-----------------------------------.
| yyabortlab -- YYABORT comes here.  |
`-----------------------------------*/
yyabortlab:
  yyresult = 1;
  goto yyreturn;

#ifndef yyoverflow
/*-------------------------------------------------.
| yyexhaustedlab -- memory exhaustion comes here.  |
`-------------------------------------------------*/
yyexhaustedlab:
  yyerror (YY_("memory exhausted"));
  yyresult = 2;
  /* Fall through.  */
#endif

yyreturn:
  if (yychar != YYEOF && yychar != YYEMPTY)
     yydestruct ("Cleanup: discarding lookahead",
         yytoken, &yylval);
  /* Do not reclaim the symbols of the rule which action triggered
     this YYABORT or YYACCEPT.  */
  YYPOPSTACK (yylen);
  YY_STACK_PRINT (yyss, yyssp);
  while (yyssp != yyss)
    {
      yydestruct ("Cleanup: popping",
          yystos[*yyssp], yyvsp);
      YYPOPSTACK (1);
    }
#ifndef yyoverflow
  if (yyss != yyssa)
    YYSTACK_FREE (yyss);
#endif
#if YYERROR_VERBOSE
  if (yymsg != yymsgbuf)
    YYSTACK_FREE (yymsg);
#endif
  /* Make sure YYID is used.  */
  return YYID (yyresult);
}


#line 201 "tuple.y"




```

---

