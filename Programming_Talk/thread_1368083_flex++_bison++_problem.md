---
title: "flex++ bison++ problem"
date: 2009-12-30
forum: Programming Talk
---

### Post by eris86 on 2009-12-30
Hi, 
I'm writing scanner and parser for HTML code. The trouble is that I can't return string value from scanner. If I use this code, it will work perfectly for tokens (logically) but I need to extract string value from font_phrase_cont rule. Any idea how to do that? With this code I get some strange looking characters...:confused:

part of parser.y
------------
```

%}

%union {

    const char *str;
} 
%token <str> _STRING
bold_statement
:_OB _RANCHOR font_phrase_cont _CB _RANCHOR  {

	$<str>$=$<str>3;
	out<< "QFont font( "<<$<str>$<<");"<<
    "font.setWeight( QFont::Bold );"<<"showFontInfo( font );"<<endl;


} 
;

font_phrase_cont
:font_phrase_cont text {$<str>$ = $<str>2
}
|
;
text
:_STRING {$<str>$=&<str>1;}
}


|special
|font

; 

```

part of scanner.l
```

%option c++
%option noyywrap


%{
#include<sstream>
#include <iostream>
#include <string.h>
#include "parser.h"

#include <cstdlib>  

 
extern yy_Parser_stype yylval;

%}

yyFlexLexer lexer
letter                      [_a-zA-Z]
DIGIT [0-9]

%%
">" {return Parser::_RANCHOR;}
"<"[bB] {return Parser::_OB;}
"</"[bB] {return Parser::_CB;}
\"[^\"]*\"           {yylval.str=yytext; return Parser::_STRING;}


<<EOF>> {
yyterminate();
}

%%  

```

---

### Post by JulioGR on 2009-12-30
Hi,
You should take a look at the c++ example in the bison documentation : [http://www.gnu.org/software/bison/manual/bison.html#A-Complete-C_002b_002b-Example](http://www.gnu.org/software/bison/manual/bison.html#A-Complete-C_002b_002b-Example)

You'll find what you need. It extracts integers instead of strings.

---

### Post by eris86 on 2009-12-30
Unfortunately I need strings not integers.

---

### Post by mmix on 2009-12-30
then,
[http://en.wikipedia.org/wiki/Itoa](http://en.wikipedia.org/wiki/Itoa)

but, there is also other way to do it in bison, i guess.

---

### Post by JulioGR on 2009-12-30
> **eris86 said:**
> Unfortunately I need strings not integers.
This is exactly the same. You'll just don't use atoi...

---

### Post by eris86 on 2010-01-04
> **JulioGR said:**
> This is exactly the same. You'll just don't use atoi...
I've tried that. Now I don't get trash, but it seems to me that scanner is not returning any kind of value to parser. I just get an empty value when I print $$ ... :confused:

---

