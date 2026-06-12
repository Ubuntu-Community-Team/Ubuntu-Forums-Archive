---
title: "[lex ] unrecognized rule problems"
date: 2009-07-23
forum: Programming Talk
---

### Post by retval on 2009-07-23
I'm trying to create a BNF file I was given into a grammar. My lex file gives me many "unrecognized rule" and I dont have a clue why. I'm not even sure what they all have in common.

Here are the errors
```

lexicalAnalyzer.l:163: unrecognized rule
lexicalAnalyzer.l:165: unrecognized rule
lexicalAnalyzer.l:166: unrecognized rule
lexicalAnalyzer.l:167: unrecognized rule
lexicalAnalyzer.l:168: unrecognized rule
lexicalAnalyzer.l:170: unrecognized rule
lexicalAnalyzer.l:171: unrecognized rule
lexicalAnalyzer.l:171: unrecognized rule
lexicalAnalyzer.l:171: unrecognized rule
lexicalAnalyzer.l:171: unrecognized rule
lexicalAnalyzer.l:171: unrecognized rule
lexicalAnalyzer.l:171: unrecognized rule
lexicalAnalyzer.l:171: unrecognized rule
lexicalAnalyzer.l:171: unrecognized rule
lexicalAnalyzer.l:171: unrecognized rule
lexicalAnalyzer.l:190: unrecognized rule
lexicalAnalyzer.l:191: unrecognized rule
lexicalAnalyzer.l:194: unrecognized rule
lexicalAnalyzer.l:194: unrecognized rule
make: *** [compiler] Error 1

```

Here is the file
```

%{
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdarg.h>
#include "y.tab.h"

void lexEcho(char *format, ...);
%}

single_quoted       	[']{sq_char}{sq_char}*[']
sq_char             	([\40-\46\50-\133\135-\176]|[\\]['\\])
distinct_object     	["]{do_char}{do_char}*["]
do_char             	([\40-\41\43-\133\135-\176]|[\\]["\\])

dollar_word         	{dollar} {lower_word}
dollar_dollar_word  	{dollar} {dollar} {lower_word}
upper_word          	{upper_alpha} {alpha_numeric}*
lower_word         	{lower_alpha} {alpha_numeric}*

real                	({decimal_fraction}|{decimal_exponent})
signed_integer     	{sign} {unsigned_integer}
unsigned_integer    	{decimal_natural}
decimal_exponent    	({decimal}|{decimal_fraction}){exponent} {decimal}
decimal_fraction    	{decimal} {dot_decimal}
decimal             	({signed_decimal}|{decimal_natural})
signed_decimal     	{sign} {decimal_natural}
decimal_natural		([0]|{non_zero_numeric} {numeric}*)
dot_decimal         	[.]{numeric numeric}*
sign                	[+-]
exponent            	[Ee]

alpha_numeric		({lower_alpha}|{upper_alpha}|{numeric}|[_])
numeric         	[0-9]
non_zero_numeric	[1-9]
lower_alpha      	[a-z]
upper_alpha        	[A-Z]
dollar           	[$]
printable_char     	.
viewable_char      	[.\n]

%%

"|"			{lexEcho("[|]"); return VLINE;}
"*"			{lexEcho("[*]"); return STAR;}
"+"			{lexEcho("[+]"); return PLUS;}
"!"			{lexEcho("[!]"); return FOR_ALL;}
"?"			{lexEcho("[?]"); return THERE_EXISTS;}
"~"			{lexEcho("[~]"); return NEGATION;}
"&"			{lexEcho("[&]"); return AND;}
"|"			{lexEcho("[|]"); return OR;}
"<=>"			{lexEcho("[<=>]"); return DOUBLE_ARROW;}
"=>"			{lexEcho("[=>]"); return RIGHT_ARROW;}
"<="			{lexEcho("[<=]"); return LEFT_ARROW;}
"-->"			{lexEcho("[-->]"); return GENTZEN_ARROW;}
"<~>"			{lexEcho("[<~?]"); return XOR;}
"~|"			{lexEcho("[~|]"); return NOR;}
"~&" 			{lexEcho("[~&]"); return NAND;}
"="			{lexEcho("[=]"); return EQUAL;}
"!="			{lexEcho("[!=]"); return NOT_EQUAL;}

"thf"			{lexEcho("[thf]"); return THF;}
"fof"			{lexEcho("[fof]"); return FOF;}
"cnf"			{lexEcho("[cnf]"); return CNF;}

"axiom"			{lexEcho("[axiom]"); return AXIOM;}
"hypothesis"		{lexEcho("[hypothesis]"); return HYPOTHESIS;}
"definition"		{lexEcho("[definition]"); return DEFINITION;}
"assumption"		{lexEcho("[assumption]"); return ASSUMPTION;}
"lemma"			{lexEcho("[lemma]"); return LEMMA;}
"theorem"		{lexEcho("[theorem]"); return THEOREM;}
"conjecture"		{lexEcho("[conjecture]"); return CONJECTURE;}
"negated_conjecture"	{lexEcho("[negated_conjecture]"); return NEGATED_CONJECTURE;}
"plain"			{lexEcho("[plain]"); return PLAIN;}
"fi_domain"		{lexEcho("[fi_domain]"); return FI_DOMAIN;}
"fi_functors"		{lexEcho("[fi_functors]"); return FI_FUNCTORS;}
"fi_predicates"		{lexEcho("[fi_predicates]"); return FI_PREDICATES;}
"type"			{lexEcho("[type]"); return TYPE;}
"unknown"		{lexEcho("[unknown]"); return UNKNOWN;}

"oType"			{lexEcho("[oType]"); return OTYPE;}
"o"			{lexEcho("[o]"); return O;}
"iType"			{lexEcho("[iType]"); return ITYPE;}
"i"			{lexEcho("[i]"); return I;}
"tType"			{lexEcho("[tType]"); return TTYPE;}
"real"			{lexEcho("[real]"); return REAL;}
"int"			{lexEcho("[int]"); return INT;}

"true"			{lexEcho("[true]"); return TRUE;}
"false"			{lexEcho("[false]"); return FALSE;}
"equal"			{lexEcho("[equal]"); return EQUAL;}

"inference"		{lexEcho("[inference]"); return INFERENCE;}
"introduced"		{lexEcho("[introduced]"); return INTRODUCED;}
"definition"		{lexEcho("[definition]"); return DEFINITION;}
"axiom_of_choice"	{lexEcho("[axiom_of_choice]"); return AXIOM_OF_CHOICE;}
"tautology"		{lexEcho("[tautology]"); return TAUTOLOGY;}
"assumption"		{lexEcho("[assumption]"); return ASSUMPTION;}
"file"			{lexEcho("[file]"); return TPTP_FILE;}
"theory"		{lexEcho("[theory]"); return THEORY;}
"equality"		{lexEcho("[equality]"); return EQUALITY;}
"ac"			{lexEcho("[ac]"); return AC;}
"creator"		{lexEcho("[creator]"); return CREATOR;}

"description"		{lexEcho("[description]"); return DESCRIPTION;}
"iquote"		{lexEcho("[iquote]"); return IQUOTE;}	
"status"		{lexEcho("[status]"); return STATUS;}

"suc"			{lexEcho("[suc]"); return SUC;}
"unp"			{lexEcho("[unp]"); return UNP;}
"sap"			{lexEcho("[sap]"); return SAP;}
"esa"			{lexEcho("[esa]"); return ESA;}
"sat"			{lexEcho("[sat]"); return SAR;}
"fsa"			{lexEcho("[fsa]"); return FSA;}
"thm"			{lexEcho("[thm]"); return THM;}
"eqv"			{lexEcho("[eqv]"); return EQV;}
"tac"			{lexEcho("[tac]"); return TAC;}
"wec"			{lexEcho("[wec]"); return WEC;} 
"eth"			{lexEcho("[eth]"); return ETH;}
"tau"			{lexEcho("[tau]"); return TAU;}
"wtc"			{lexEcho("[wtc]"); return WTC;}
"wth"			{lexEcho("[wth]"); return WTH;}
"cax"			{lexEcho("[cax]"); return CAX;} 
"sca"			{lexEcho("[sca]"); return SCA;} 
"tca"			{lexEcho("[tca]"); return TCA;} 
"wca"			{lexEcho("[wca]"); return WCA;}
"cup"			{lexEcho("[cup]"); return CUP;} 
"csp"			{lexEcho("[csp]"); return CSP;} 
"ecs"			{lexEcho("[ecs]"); return ECS;} 
"csa"			{lexEcho("[csa]"); return CSA;} 
"cth"			{lexEcho("[cth]"); return CTH;} 
"ceq"			{lexEcho("[ceq]"); return CEQ;} 
"unc"			{lexEcho("[unc]"); return UNC;}
"wcc"			{lexEcho("[wcc]"); return WCC;}
"ect"			{lexEcho("[ect]"); return ECT;}
"fun"			{lexEcho("[fun]"); return FUN;} 
"uns"			{lexEcho("[uns]"); return UNS;}
"wuc"			{lexEcho("[wuc]"); return WUC;} 
"wct"			{lexEcho("[wct]"); return WCT;}
"scc"			{lexEcho("[scc]"); return SCC;}
"uca"			{lexEcho("[uca]"); return UCA;}
"noc"			{lexEcho("[noc]"); return NOC;}

"assumptions"		{lexEcho("[assumptions]"); return ASSUMPTIONS;}
"refutation"		{lexEcho("[refutation]"); return REFUTATION;}
"include"		{lexEcho("[include]"); return INCLUDE;}

"thf"			{lexEcho("[thf]"); return THF;}
"fof"			{lexEcho("[fof]"); return FOF;}
"cnf"			{lexEcho("[cnf]"); return CNF;}
"fot"			{lexEcho("[fot]"); return FOT;}

{single_quoted}			{lexEcho("[single_quoted]"); return SINGLE_QUOTED;}
{sq_char}			{lexEcho("[sq_char]"); return SQ_CHAR;}
{distinct_object}		{lexEcho("[distinct_object]"); return DISTINCT_OBJECT;}
{do_char}			{lexEcho("[do_char]"); return DO_CHAR;}

{dollar_word}			{lexEcho("[dollar_word]"); return DOLLAR_WORD;}
{dollar_dollar_word}		{lexEcho("[dollar_dollar_word]"); return DOLLAR_DOLLAR_WORD;}
{upper_word}			{lexEcho("[upper_word]"); return UPPER_WORD;}
{lower_word}			{lexEcho("[lower_word]"); return UPPER_WORD;}

{real}				{lexEcho("[real]"); return REAL;}
{signed_integer}		{lexEcho("[signed_integer]"); return SIGNED_INTEGER;}
{unsigned_integer}		{lexEcho("[unsigned_integer]"); return UNSIGNED_INTEGER;}
{decimal_exponent}		{lexEcho("[decimal_exponent]"); return DECIMAL_EXPONENT;}
{decimal_fraction}		{lexEcho("[decimal_fraction]"); return DECIMCAL_FRACTION;}
{decimal}			{lexEcho("[decimal]"); return DECIMAL;}
{signed_decimal}		{lexEcho("[signed_decimal]"); return SIGNED_DECIMAL;}
{decimal_natural}		{lexEcho("[decimal_natural]"); return DECIMAL_NATURAL;}
{dot_decimal}			{lexEcho("[dot_decimal]"); return DOT_DECIMAL;}
{sign}				{lexEcho("[sign]"); return SIGN;}
{exponent}			{lexEcho("[exponent]"); return EXPONENT;}

{alpha_numeric}			{lexEcho("[alpha_numeric]"); return ALPHA_NUMERIC;}
{numeric}			{lexEcho("[numeric]"); return NUMERIC;}
{non_zero_numeric}		{lexEcho("[non_zero_numeric]"); return NON_ZERO_NUMERIC;}
{lower_alpha}			{lexEcho("[lower_alpha]"); return LOWER_ALPHA;}
{upper_alpha}			{lexEcho("[upper_alpha]"); return UPPER_ALPHA;}
{dollar}			{lexEcho("[dollar]"); return DOLLAR;}
{printable_char}		{lexEcho("[printable_char]"); return PRINTABLE_CHAR;}
{viewable_char}			{lexEcho("[viewable_char]"); return VIEWABLE_CHAR;}

%%

void lexEcho(char *format, ...) {
	va_list args;
	
	#ifdef LEX_DEBUG
		va_start(args, format);
		vfprintf(stderr, format, args);
		va_end(args);
	#endif
}

```

---

### Post by retval on 2009-07-23
ok, after stairing at for a few hours I finally noticed i missed some braces

This seems todo the trick, sorry for useless post....
```

%{
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdarg.h>
#include "y.tab.h"

void lexEcho(char *format, ...);
%}

single_quoted       	[']{sq_char}{sq_char}*[']
sq_char             	([\40-\46\50-\133\135-\176]|[\\]['\\])
distinct_object     	["]{do_char}{do_char}*["]
do_char             	([\40-\41\43-\133\135-\176]|[\\]["\\])

dollar_word         	{dollar}{lower_word}
dollar_dollar_word  	{dollar}{dollar}{lower_word}
upper_word          	{upper_alpha}{alpha_numeric}*
lower_word         	{lower_alpha}{alpha_numeric}*

real                	({decimal_fraction}|{decimal_exponent})
signed_integer     	{sign}{unsigned_integer}
unsigned_integer    	{decimal_natural}
decimal_exponent    	({decimal}|{decimal_fraction}){exponent}{decimal}
decimal_fraction    	{decimal}{dot_decimal}
decimal             	({signed_decimal}|{decimal_natural})
signed_decimal     	{sign}{decimal_natural}
decimal_natural		([0]|{non_zero_numeric}{numeric}*)
dot_decimal         	[.]{numeric}{numeric}*
sign                	[+-]
exponent            	[Ee]

alpha_numeric		({lower_alpha}|{upper_alpha}|{numeric}|[_])
numeric         	[0-9]
non_zero_numeric	[1-9]
lower_alpha      	[a-z]
upper_alpha        	[A-Z]
dollar           	[$]
printable_char     	.
viewable_char      	[.\n]

%%

"|"			{lexEcho("[|]"); return VLINE;}
"*"			{lexEcho("[*]"); return STAR;}
"+"			{lexEcho("[+]"); return PLUS;}
"!"			{lexEcho("[!]"); return FOR_ALL;}
"?"			{lexEcho("[?]"); return THERE_EXISTS;}
"~"			{lexEcho("[~]"); return NEGATION;}
"&"			{lexEcho("[&]"); return AND;}
"|"			{lexEcho("[|]"); return OR;}
"<=>"			{lexEcho("[<=>]"); return DOUBLE_ARROW;}
"=>"			{lexEcho("[=>]"); return RIGHT_ARROW;}
"<="			{lexEcho("[<=]"); return LEFT_ARROW;}
"-->"			{lexEcho("[-->]"); return GENTZEN_ARROW;}
"<~>"			{lexEcho("[<~?]"); return XOR;}
"~|"			{lexEcho("[~|]"); return NOR;}
"~&" 			{lexEcho("[~&]"); return NAND;}
"="			{lexEcho("[=]"); return EQUAL;}
"!="			{lexEcho("[!=]"); return NOT_EQUAL;}

"thf"			{lexEcho("[thf]"); return THF;}
"fof"			{lexEcho("[fof]"); return FOF;}
"cnf"			{lexEcho("[cnf]"); return CNF;}

"axiom"			{lexEcho("[axiom]"); return AXIOM;}
"hypothesis"		{lexEcho("[hypothesis]"); return HYPOTHESIS;}
"definition"		{lexEcho("[definition]"); return DEFINITION;}
"assumption"		{lexEcho("[assumption]"); return ASSUMPTION;}
"lemma"			{lexEcho("[lemma]"); return LEMMA;}
"theorem"		{lexEcho("[theorem]"); return THEOREM;}
"conjecture"		{lexEcho("[conjecture]"); return CONJECTURE;}
"negated_conjecture"	{lexEcho("[negated_conjecture]"); return NEGATED_CONJECTURE;}
"plain"			{lexEcho("[plain]"); return PLAIN;}
"fi_domain"		{lexEcho("[fi_domain]"); return FI_DOMAIN;}
"fi_functors"		{lexEcho("[fi_functors]"); return FI_FUNCTORS;}
"fi_predicates"		{lexEcho("[fi_predicates]"); return FI_PREDICATES;}
"type"			{lexEcho("[type]"); return TYPE;}
"unknown"		{lexEcho("[unknown]"); return UNKNOWN;}

"oType"			{lexEcho("[oType]"); return OTYPE;}
"o"			{lexEcho("[o]"); return O;}
"iType"			{lexEcho("[iType]"); return ITYPE;}
"i"			{lexEcho("[i]"); return I;}
"tType"			{lexEcho("[tType]"); return TTYPE;}
"real"			{lexEcho("[real]"); return REAL;}
"int"			{lexEcho("[int]"); return INT;}

"true"			{lexEcho("[true]"); return TRUE;}
"false"			{lexEcho("[false]"); return FALSE;}
"equal"			{lexEcho("[equal]"); return EQUAL;}

"inference"		{lexEcho("[inference]"); return INFERENCE;}
"introduced"		{lexEcho("[introduced]"); return INTRODUCED;}
"definition"		{lexEcho("[definition]"); return DEFINITION;}
"axiom_of_choice"	{lexEcho("[axiom_of_choice]"); return AXIOM_OF_CHOICE;}
"tautology"		{lexEcho("[tautology]"); return TAUTOLOGY;}
"assumption"		{lexEcho("[assumption]"); return ASSUMPTION;}
"file"			{lexEcho("[file]"); return TPTP_FILE;}
"theory"		{lexEcho("[theory]"); return THEORY;}
"equality"		{lexEcho("[equality]"); return EQUALITY;}
"ac"			{lexEcho("[ac]"); return AC;}
"creator"		{lexEcho("[creator]"); return CREATOR;}

"description"		{lexEcho("[description]"); return DESCRIPTION;}
"iquote"		{lexEcho("[iquote]"); return IQUOTE;}	
"status"		{lexEcho("[status]"); return STATUS;}

"suc"			{lexEcho("[suc]"); return SUC;}
"unp"			{lexEcho("[unp]"); return UNP;}
"sap"			{lexEcho("[sap]"); return SAP;}
"esa"			{lexEcho("[esa]"); return ESA;}
"sat"			{lexEcho("[sat]"); return SAR;}
"fsa"			{lexEcho("[fsa]"); return FSA;}
"thm"			{lexEcho("[thm]"); return THM;}
"eqv"			{lexEcho("[eqv]"); return EQV;}
"tac"			{lexEcho("[tac]"); return TAC;}
"wec"			{lexEcho("[wec]"); return WEC;} 
"eth"			{lexEcho("[eth]"); return ETH;}
"tau"			{lexEcho("[tau]"); return TAU;}
"wtc"			{lexEcho("[wtc]"); return WTC;}
"wth"			{lexEcho("[wth]"); return WTH;}
"cax"			{lexEcho("[cax]"); return CAX;} 
"sca"			{lexEcho("[sca]"); return SCA;} 
"tca"			{lexEcho("[tca]"); return TCA;} 
"wca"			{lexEcho("[wca]"); return WCA;}
"cup"			{lexEcho("[cup]"); return CUP;} 
"csp"			{lexEcho("[csp]"); return CSP;} 
"ecs"			{lexEcho("[ecs]"); return ECS;} 
"csa"			{lexEcho("[csa]"); return CSA;} 
"cth"			{lexEcho("[cth]"); return CTH;} 
"ceq"			{lexEcho("[ceq]"); return CEQ;} 
"unc"			{lexEcho("[unc]"); return UNC;}
"wcc"			{lexEcho("[wcc]"); return WCC;}
"ect"			{lexEcho("[ect]"); return ECT;}
"fun"			{lexEcho("[fun]"); return FUN;} 
"uns"			{lexEcho("[uns]"); return UNS;}
"wuc"			{lexEcho("[wuc]"); return WUC;} 
"wct"			{lexEcho("[wct]"); return WCT;}
"scc"			{lexEcho("[scc]"); return SCC;}
"uca"			{lexEcho("[uca]"); return UCA;}
"noc"			{lexEcho("[noc]"); return NOC;}

"assumptions"		{lexEcho("[assumptions]"); return ASSUMPTIONS;}
"refutation"		{lexEcho("[refutation]"); return REFUTATION;}
"include"		{lexEcho("[include]"); return INCLUDE;}

"thf"			{lexEcho("[thf]"); return THF;}
"fof"			{lexEcho("[fof]"); return FOF;}
"cnf"			{lexEcho("[cnf]"); return CNF;}
"fot"			{lexEcho("[fot]"); return FOT;}

{single_quoted}			{lexEcho("[single_quoted]"); return SINGLE_QUOTED;}
{sq_char}			{lexEcho("[sq_char]"); return SQ_CHAR;}
{distinct_object}		{lexEcho("[distinct_object]"); return DISTINCT_OBJECT;}
{do_char}			{lexEcho("[do_char]"); return DO_CHAR;}

{dollar_word}			{lexEcho("[dollar_word]"); return DOLLAR_WORD;}
{dollar_dollar_word}		{lexEcho("[dollar_dollar_word]"); return DOLLAR_DOLLAR_WORD;}
{upper_word}			{lexEcho("[upper_word]"); return UPPER_WORD;}
{lower_word}			{lexEcho("[lower_word]"); return LOWER_WORD;}

{real}				{lexEcho("[real]"); return REAL;}
{signed_integer}		{lexEcho("[signed_integer]"); return SIGNED_INTEGER;}
{unsigned_integer}		{lexEcho("[unsigned_integer]"); return UNSIGNED_INTEGER;}
{decimal_exponent}		{lexEcho("[decimal_exponent]"); return DECIMAL_EXPONENT;}
{decimal_fraction}		{lexEcho("[decimal_fraction]"); return DECIMCAL_FRACTION;}
{decimal}			{lexEcho("[decimal]"); return DECIMAL;}
{signed_decimal}		{lexEcho("[signed_decimal]"); return SIGNED_DECIMAL;}
{decimal_natural}		{lexEcho("[decimal_natural]"); return DECIMAL_NATURAL;}
{dot_decimal}			{lexEcho("[dot_decimal]"); return DOT_DECIMAL;}
{sign}				{lexEcho("[sign]"); return SIGN;}
{exponent}			{lexEcho("[exponent]"); return EXPONENT;}

{alpha_numeric}			{lexEcho("[alpha_numeric]"); return ALPHA_NUMERIC;}
{numeric}			{lexEcho("[numeric]"); return NUMERIC;}
{non_zero_numeric}		{lexEcho("[non_zero_numeric]"); return NON_ZERO_NUMERIC;}
{lower_alpha}			{lexEcho("[lower_alpha]"); return LOWER_ALPHA;}
{upper_alpha}			{lexEcho("[upper_alpha]"); return UPPER_ALPHA;}
{dollar}			{lexEcho("[dollar]"); return DOLLAR;}
{printable_char}		{lexEcho("[printable_char]"); return PRINTABLE_CHAR;}
{viewable_char}			{lexEcho("[viewable_char]"); return VIEWABLE_CHAR;}

%%

void lexEcho(char *format, ...) {
	va_list args;
	
	#ifdef LEX_DEBUG
		va_start(args, format);
		vfprintf(stderr, format, args);
		va_end(args);
	#endif
}

```

---

