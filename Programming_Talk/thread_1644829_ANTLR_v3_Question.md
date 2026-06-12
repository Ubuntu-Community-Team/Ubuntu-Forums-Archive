---
title: "ANTLR v3 Question"
date: 2010-12-13
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-12-13
I am learning ANTLR...first time used is today.  I am trying to parse a file with test instance descriptions which look like this:

[PHP]Test node1
{
	Attribute1 = "value1";
	Attribute2 = "value2";
	Attribute3 = "value3";
}

Test node2
{
	Attribute1 = "value1";
	Attribute2 = "value2";
	Attribute3 = "value3";
}[/PHP]

..and so on.  I came up with this grammar which compiles, but does nothing:

[PHP]grammar firstgrammar;

tokens {
	SEMICOLON 	= ';';
	QUOTE	= '"';
	EQUALS	= '=';
	LBRACKET = '{';	
	RBRACKET = '}';
}


testinstanceblock 	: TEST ID ID LBRACKET PARAMETERS RBRACKET
	;	 

ID  :	('a'..'z'|'A'..'Z'|'_') ('a'..'z'|'A'..'Z'|'0'..'9'|'_')*
    ;

fragment
TEST		
	:	'Test'
	;

PARAMETERS
	:	ID EQUALS VALUE SEMICOLON
	;

VALUE	
	:	ID | ( QUOTE ID QUOTE)
	;[/PHP]

I want to represent each test instance as a class which will store the test instance name and contain an array of parameters where each parameter will be a string name, value pair.  Does anyone know how to do this in ANTLR?  I know how to assign action rules in Flex / YACC, but not familiar with ANTLR.  I read up on rule re-writes, but not interested in optimization, just simply want to store test instances with their parameters.

---

