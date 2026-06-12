---
title: "[C++] Parser First Order Logic (FOL)"
date: 2010-10-08
forum: Programming Talk
---

### Post by erotavlas on 2010-10-08
Hi All,

I'm searching a parser of FOL clauses. Do you know if exist some open source implementation that I can use?


Thank you

---

### Post by blackmail on 2010-10-08
Hello, I may not be the most helpful around but maybe this helps:

math parser:
[http://www.codeproject.com/KB/recipes/FastMathParser.aspx](http://www.codeproject.com/KB/recipes/FastMathParser.aspx)

or this:
[http://users.soe.ucsc.edu/~avg/Papers/hotptp-parser-ijcar06.pdf](http://users.soe.ucsc.edu/~avg/Papers/hotptp-parser-ijcar06.pdf)

I may have missed the point of your post, and also pls take a look at the expr command. Mainly this would be all my advice. Hope it helps somewhat :D

---

### Post by erotavlas on 2010-10-08
Thank you. The point of my post is that I'm searching a parser written in C++ for [FOL]("http://en.wikipedia.org/wiki/First-order_logic")
I have found this [http://www.buraak.com/2007/06/02/first-order-logic-parser/](http://www.buraak.com/2007/06/02/first-order-logic-parser/).

---

### Post by erotavlas on 2010-11-02
I'm studying how I can implement a parser for FOL clauses. Now I need to make a choice for lexical analyzer and grammar parser. What is the best (simple and efficient) between lex and flex? and between yacc and bison?

Thank you

---

### Post by Arndt on 2010-11-02
> **erotavlas said:**
> I'm studying how I can implement a parser for FOL clauses. Now I need to make a choice for lexical analyzer and grammar parser. What is the best (simple and efficient) between lex and flex? and between yacc and bison?

Thank you

As I see them, flex and bison are more modern implementations (and perhaps extensions) of the older lex and yacc, so I wouldn't call one simpler than the other.

---

### Post by erotavlas on 2010-11-02
> **Arndt said:**
> As I see them, flex and bison are more modern implementations (and perhaps extensions) of the older lex and yacc, so I wouldn't call one simpler than the other.

With "simple" I intend which is simpler to implementation.

---

