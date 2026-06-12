---
title: "Given a grammar for a programming language..."
date: 2010-06-18
forum: Programming Talk
---

### Post by cdietschrun on 2010-06-18
I have been given the following grammar for a fake programming language called Shopper:


Program ::= "BEGIN" DP SP ES; 
DP ::= DP; | DP D; 
D ::= (REAL | INTEGER ) VLIST; 
VLIST ::= V | VLIST, V; 
SP ::= ST | SP, ST; 
ST ::= ASP | IOST; 
IOST ::= (READ | PRINT ), VLIST; 
ASP ::= V = AE; 
AE ::= TERM | TERM + AE | TERM - AE; 
TERM ::= V | TERM * V | TERM / V; 
ES ::= "END."; 
V ::= LETTER | LETTER DIGIT; 
LETTER = {Letter}; 
DIGIT = {Digit}; 

And I want to learn as much about the grammar as possible, i.e. is it a CFG? Is it left recursive? etc.. because the class needs me to write a scanner/lexer, an LL or LR parser, and finally a code generator.

I'd like to get a start on this and have more of an understanding of what kind of grammar I was presented with. Can anyone help me with any online tools or anything we can think of that will help? And I can't use Lex or Yacc or any tools to write my final compiler, but I can use whatever I want in helping me to understand where to start.

Any advice/help?

---

### Post by slavik on 2010-06-18
have you tried the textbook?

---

### Post by KdotJ on 2010-06-18
Do you understand the concepts of left-recursion is CFG's? and how to eliminate it to provide deterministic grammars?

---

