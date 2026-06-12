---
title: "Creating a C-like language parser in C/C++"
date: 2009-04-28
forum: Programming Talk
---

### Post by kpatz on 2009-04-28
Say I wanted to write a program in C or C++ that parses an input file that contains constructs including nested expressions and bracketed expressions (e.g. like functions/if statements in C), as well as quoted string literals.  What's the best way to go about this?

For example, parsing out something like this:
```

  rule rulename(flag1, flag2...)
 {
    if (regex("some regex pattern") or (regex("another pattern") and regex("yet another pattern")))
      do_something;
  }

```

Do it from scratch?  (a rather daunting task)
Use something like bison?
Use something other than bison?
Some library function I'm not aware of?
Suggestions?

Thanks...

---

### Post by aanderse on 2009-04-29
Flex and Bison are great. I've just recently started learning them and am really impressed at how powerful they are. I bought the Lex and Yacc book and have started going through it (internet tutorials were good, but I thought a book might help out some too).

I've looked at projects who roll their own parsers and compared that to flex/bison and the ideas are very similar once you are familiar with the terms, it's just the syntax which is different. Either way I recommend you trying out Flex and Bison!

What is the extent of your c-like language parser?

---

### Post by kpatz on 2009-04-29
It's for a spam filter I'm developing.  I already have a version that uses a "flat file" structure, where I can specify things like "if this regex matches between lines 1-5 of the headers and that regex matches in the body then this is spam".

I'd like to switch to a more flexible parser so I can add more complex expressions (e.g. using parentheses to set precedence, mixing "and" and "or", having nested expressions, macros, variables, etc.).

I'm currently playing around with bison and will probably go that route, initially at least.

I may grab the source code for mawk and see how it does things.  (EDIT: Just did, it uses yacc/bison).

---

### Post by tgu on 2009-04-29
If you decide to go with bison and prefer C++ over C, check out bisonc++ which generates a pure C++ parser. I've been using it lately to parse a custom language and like it alot.

---

### Post by ibuclaw on 2009-04-29
A step away from bison/flex, but the boost library for C++ also has an object-oriented parser routine called Spirit.

[http://spirit.sourceforge.net/](http://spirit.sourceforge.net/)

You can essentially do the exact same job, but in a C++ environment.

Regards
Iain

---

### Post by UBForty on 2009-05-01
It may be interesting to know that lex/yacc and flex/bison are generally recommended by people who have never used anything else. People who have been building parsers with different tools are generally not so quick in recommending them. If this is just a quick and dirty implementation then perhaps it doesn't matter, but if you want to select the best tool for the job, then you probably want to do a little research first. There are tons of tools to choose from. The following list should be a good start.

[http://www.thefreecountry.com/programming/compilerconstruction.shtml](http://www.thefreecountry.com/programming/compilerconstruction.shtml)

As for building a parser from scratch, that is not actually as daunting a task as it may sound. Parser generator tools are quite complex beasts and it is difficult for a novice to understand how they do what they do. This leads to the assumption that coding it yourself is difficult. However, this view misses out on an important piece of information: Almost all parser generators are using a very different approach to the approach used when writing a parser by hand.

Most parser generators build so called table-driven parsers. The operation of such a parser happens on large tables and the tables direct what the parser will do as it does its work. Therefore, when you look at the source code it is difficult to see how the parser does what it does. Most of the necessary information that sheds light on its operation is in the data which is not seen in the source code. This leads to the impression that the whole business is rocket science and cannot be understood by lesser mortals.

When you write a parser by hand, you are very unlikely to choose the table-driven approach. Almost all hand written parsers use an approach where you can see what it is doing in the source code, just like most software. You can read the source code and it makes sense. This approach is called "recursive descent parsing" or sometimes also "top-down parsing". A recursive descent parser has one function for each production (rule) in the grammar and it is very easy to translate a grammar rule directly into the code that goes into the function. So, it is not really difficult to write a parser by hand in this way. Once you have done your grammar, it can be coded by a code monkey, so to speak.

For example, a hypothetical grammar rule for an if-then-else-elsif-endif statement may look like this ...

if-statement ::= "if" expression "then" statement ["elsif" expression "then" statement] "endif"

this can be translated into a function for a recursive descent parser as follows ...

int if_statement(int sym) {

  if (sym == if_token) {
    sym = get_sym(); /* consume this token */
    sym = lookahead_sym(); /* take a look at the next one */
    if (sym == /* any token which starts an expression */) {
      sym = expression(sym);
      if (sym == then_token) {
        sym = get_sym(); /* consume this token */
        sym = lookahead_sym(); /* take a look at the next one */
        if (sym == /* any token which starts a statement */) {
          sym = statement(sym);
          if (sym == elsif_token) {
            sym = get_sym(); /* consume this token */
            sym = lookahead_sym(); /* take a look at the next one */ {
            if (sym == /* any token which starts an expression */ {
              sym = expression(sym);
              ...
             } else {
               syntax_error("expected any of .... but found ...");
               ...
             }
           ...
          } else if (sym == "endif") {
            sym = get_sym(); /* consume this token */
            return(lookahead_sym(); /* return the lookahead token to the calling function */
          } /* done */
....

as you can see, this is not rocket science. Any grammar rule has its own such function and when you encounter the name of the rule inside another rule, then you simply call that rule's function in your code. This is why this approach is called recursive descent. Very straightforward.

the example also shows that the grammar must be written such that the parser can figure out what to do next by looking at the next token (one symbol lookahead), there must be no ambiguity such that two possible alternatives can start with the same token, because in that case the parser does not know which function to call next. This type of grammar is called an LL(1) grammar. LL(1) grammars are slightly more restrictive than the grammars which can be handled by table driven parsers but in practise this is not a serious restriction, most grammars, even if they are not LL(1), can be written to satisfy the LL(1) constraints.

There are advantages to writing a parser by hand, especially if your grammar isn't very big. If you have a grammar like Ada or C++, with hundreds of grammar rules, then you probably want to use a parser generator tool, but if your grammar has 10 or 50 or even 150 rules, then it isn't too much effort to write your parser by hand using the recursive descent approach. The main advantage is that the parser will be very fast. Table driven parsers are slow. Another big advantage is that recursive descent parsers are easy to understand and therefore it is easy to maintain the code, even if the maintainer changes.

Another big advantage is that the parser always knows what is wrong when there is an error in the source to be translated. A table driven parser knows that there is *something* wrong and it is *somewhere close to here*. This is why you get all those misleading error messages from GCC, it simply isn't very good at telling you what precisely the error is because it can't figure it out. A recursive descent parser can always tell you exactly where and why: Expected "foo" or "bar" or "baz" but found "bozo".

So, I wouldn't rule out writing the parser by hand outright. Carefully research all your options and weigh them against each other, the handwritten approach may just turn out to be your best choice.

---

### Post by João Jerónimo on 2010-01-04
> **UBForty said:**
> Another big advantage is that the parser always knows what is wrong when there is an error in the source to be translated. A table driven parser knows that there is *something* wrong and it is *somewhere close to here*. This is why you get all those misleading error messages from GCC, it simply isn't very good at telling you what precisely the error is because it can't figure it out. A recursive descent parser can always tell you exactly where and why: Expected "foo" or "bar" or "baz" but found "bozo".

Sorry for necroposting, but GCC actually uses a Recursive Descent Parser  coded by hand. It used Bison in the past, but the official parsers are all coded by hand since GCC 3.
[http://en.wikipedia.org/wiki/GNU_Compiler_Collection#Front-ends](http://en.wikipedia.org/wiki/GNU_Compiler_Collection#Front-ends)

Besides, almost every nowadays compiler uses parsers coded by hand, don't ask me why. In fact, the only production compiler that I found that still uses flex+yacc is PCC (Portable C Compiler, written by Yacc's creator himself in 1973). Recently created compilers like FreePascal and FreeBasic also use hand-written parsers, I think.

I'm at this moment studying the hand-written parser of the Java compiler by Sun (javac). It's a different case, however: when it was written, I suspect there was no parser generator which could produce Java code.

Finally, error reporting in Bison doesn't seem to be that bad. Thinking about that now, I think it reports an error when it find the first character that doesn't make sense. I'm not sure, however...

JJ

---

