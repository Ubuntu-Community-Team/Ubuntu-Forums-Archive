---
title: "Python Lex &amp; Yacc (PLY)"
date: 2009-02-08
forum: Programming Talk
---

### Post by matmatmat on 2009-02-08
I've created a simple calculator with PLY (mainly from the documentation):

Lex: 
[PHP]
import ply.lex as lex

reserved = {'print':'PRINT', 'quit' : 'QUIT'}

# List of token names.   This is always required
tokens = [
   'NUMBER',
   'NAME',
   'PLUS',
   'MINUS',
   'TIMES',
   'DIVIDE',
   'LPAREN',
   'RPAREN',
   'EQUALS',
   'STRING',
] + list(reserved.values())

# Regular expression rules for simple tokens
t_PLUS    = r'\+'
t_MINUS   = r'-'
t_TIMES   = r'\*'
t_DIVIDE  = r'/'
t_LPAREN  = r'\('
t_RPAREN  = r'\)'
t_EQUALS = r'='

def t_NAME(t):
    r'[a-zA-Z_][a-zA-Z_0-9]*'
    t.type = reserved.get(t.value,'NAME')    # Check for reserved words
    return t


# A regular expression rule with some action code
def t_NUMBER(t):
    r'\d+'
    t.value = int(t.value)    
    return t

# Define a rule so we can track line numbers
def t_newline(t):
    r'\n+'
    t.lexer.lineno += len(t.value)
    
def t_STRING(t):
    r'\"([^\\"]|(\\.))*\"'
    escaped = 0
    str = t.value[1:-1]
    new_str = ""
    for i in range(0, len(str)):
        c = str[i]
        if escaped:
            if c == "n":
                c = "\n"
            elif c == "t":
                c = "\t"
            new_str += c
            escaped = 0
        else:
            if c == "\\":
                escaped = 1
            else:
                new_str += c
    t.value = new_str
    return t


# A string containing ignored characters (spaces and tabs)
t_ignore  = ' \t'

# Error handling rule
def t_error(t):
    print "Illegal character '%s'" % t.value[0]
    t.lexer.skip(1)

# Build the lexer
lexer = lex.lex()
[/PHP]

Yacc:
[PHP]
import ply.yacc as yacc
import sys

# Get the token map from the lexer.  This is required.
from calclex import tokens

names = {}
def p_statement_assign(t): 
	'statement : NAME EQUALS expression' 
	names[t[1]] = t[3] 
	
def p_statement_expr(t): 
	'statement : expression' 
	print t[1] 

def p_expression_name(t): 
	'expression : NAME' 
	try: 
		t[0] = names[t[1]] 
	except LookupError: 
		print "Undefined name '%s'" % t[1] 
		t[0] = 0 

def p_expression_plus(p):
    'expression : expression PLUS term'
    p[0] = p[1] + p[3]

def p_expression_minus(p):
    'expression : expression MINUS term'
    p[0] = p[1] - p[3]

def p_expression_term(p):
    'expression : term'
    p[0] = p[1]

def p_term_times(p):
    'term : term TIMES factor'
    p[0] = p[1] * p[3]

def p_term_div(p):
    'term : term DIVIDE factor'
    p[0] = p[1] / p[3]

def p_term_factor(p):
    'term : factor'
    p[0] = p[1]

def p_factor_num(p):
    'factor : NUMBER'
    p[0] = p[1]

def p_factor_expr(p):
    'factor : LPAREN expression RPAREN'
    p[0] = p[2]

def p_print(p):
	'''expression : PRINT LPAREN STRING RPAREN
			  	  | PRINT LPAREN expression RPAREN''' 
	p[0] = p[3]

def p_quit(p):
	'expression : QUIT'
	sys.exit()

# Error rule for syntax errors
def p_error(p):
    print "Syntax error in input!"

# Build the parser
parser = yacc.yacc()

if len(sys.argv) == 1:
	while True:
		try:
			s = raw_input('calc > ')
		except EOFError:
			break
		if not s: continue
		result = parser.parse(s)
		print result
elif sys.argv[1] == "-f":
	f = open(sys.argv[2], "r")
	s = f.readlines()
	for line in s:
		result = parser.parse(line)
		print result


[/PHP]

When I run it:
```

matio@ubuntu:~/Desktop/ply$ python yacc.py 
calc > 1 + 2
3
None
calc > 

```

Why does it print "None" out? Is it the p_statement_expr function?

---

### Post by maximinus_uk on 2009-02-08
The None is the standard return value of a function if you don't give one, so I assume you code somewhere is doing

print(some_function())

where some_function() actually produces the first part, and then returns a value of None, which you are then seeing printed.

Hope that makes some kind of sense - I didn't look at the code that closely :o

---

### Post by Wybiral on 2009-02-08
> **maximinus_uk said:**
> The None is the standard return value of a function if you don't give one, so I assume you code somewhere is doing

print(some_function())

where some_function() actually produces the first part, and then returns a value of None, which you are then seeing printed.

Hope that makes some kind of sense - I didn't look at the code that closely :o

Yep, my guess is that it's in the p_statement_expr function too, since it prints instead of returning a value. Should that just return the value? I've never used ply, so this is just a guess.

---

### Post by matmatmat on 2009-02-09
Thanks, I deleted the last print & it doesn't print the "None". Does anyone know how you would do if's (or anything that would need to be indented/put between { and }?

---

### Post by matmatmat on 2009-02-09
bump

---

### Post by matmatmat on 2009-02-10
bump

---

### Post by matmatmat on 2009-02-15
bump

---

### Post by maximinus_uk on 2009-02-15
Ok! That's enough bumps. Obviously nobody here knows the answer. Instead of bumping, why not try the PLY documentation - [http://www.dabeaz.com/ply/ply.html]("http://www.dabeaz.com/ply/ply.html") which looks fairly comprehensive, or even the PLY newsgroup - [http://groups.google.com/group/ply-hack?pli=1]("http://groups.google.com/group/ply-hack?pli=1").

What you're asking for is fairly specific knowledge, so best to ask in specific places :)

---

### Post by matmatmat on 2009-02-15
I've already tried the ply-hack & nobody is answering.

---

### Post by unutbu on 2009-02-15
Are you willing to switch to pyparsing? I think creating a calculator with indented grammar would not be too difficult using this module.

There are plenty of examples here:
[http://pyparsing.wikispaces.com/Examples](http://pyparsing.wikispaces.com/Examples) including a simple calculator: [http://pyparsing.wikispaces.com/file/view/SimpleCalc.py](http://pyparsing.wikispaces.com/file/view/SimpleCalc.py) and a parser for indented grammars:
[http://pyparsing.wikispaces.com/file/view/indentedGrammarExample.py](http://pyparsing.wikispaces.com/file/view/indentedGrammarExample.py)

Documentation on pyparsing can be found here:
[http://rephrase.net/days/07/04/pyparsing](http://rephrase.net/days/07/04/pyparsing)
[http://www.onlamp.com/pub/a/python/2006/01/26/pyparsing.html?page=1](http://www.onlamp.com/pub/a/python/2006/01/26/pyparsing.html?page=1)
[http://www.geocities.com/ptmcg/python/confs/pyCon2006_pres1.html](http://www.geocities.com/ptmcg/python/confs/pyCon2006_pres1.html)
/usr/share/doc/python-pyparsing/

pyparsing is provided by the python-pyparsing package.

---

### Post by matmatmat on 2009-02-17
Thanks, I'll have a look.

---

