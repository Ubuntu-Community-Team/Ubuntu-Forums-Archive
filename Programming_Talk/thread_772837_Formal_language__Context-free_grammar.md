---
title: "Formal language / Context-free grammar"
date: 2008-04-28
forum: Programming Talk
---

### Post by defmomo on 2008-04-28
I am in the process of writing a shell application in C as a school project, and I was told that using BNF-style grammar would make the code much tidier and secure. From what I understood of it, It would be a real advantage, since by understanding and being able to implement it, I could be able to parse almost any input I would want.

P.S: This is not an attempt to not do my homework myself, I strongly believe this project will teach me lots about programming if I finish it myself, I just want some opinions on BNF grammar from other programmers, and, if you know of any, links to documentation in case my own research doesn't find them all.

---

### Post by CptPicard on 2008-04-28
Well, BNF is just a way of specifying grammars, with matching rules on the left and produced string on the right. Different grammar types are then an issue on themselves... an important research topic.

Context-free grammars in particular are an important type of grammar.. if you can express your language in terms of one, there are well known and efficient and even simple parsing algorithms for them... in particular if your grammar fulfills certain criteria (LL(1)), a simple recursive descent down the grammar according to the string will parse it for you.

I wouldn't recommend you write your own parser from scratch though, there are many parser generators... yacc and bison for example. You just specify your language in terms of the grammar and let the parser generator generate the code for you.

Google Is Your Friend :)

---

### Post by defmomo on 2008-04-28
I know that writing the parser code is pretty tedious and that there are code generators that would do it well and fast, but I want to try it at least once, just out of curiosity, and the school would probably consider it cheating anyways.

---

### Post by defmomo on 2008-04-28
I know that writing the parser code is pretty tedious and that there are code generators that would do it well and fast, but I want to try it at least once, just out of curiosity, and the school would probably consider it cheating anyways.
I have found lots of hits in the newsgroups on BNF, google is indeed very friendly!

---

### Post by CptPicard on 2008-04-28
Depends on what you're supposed to prove you can do in this exercise. If the parser is not the "point" so to speak, generating it using a parser generator should be ok.

And btw, that "...being able to parse about any input you want" part in your original post... now... that's quite wrong, and that's why it is a research topic ;) What sort of grammars can express what kind of strings, and what kind of strings generated from what sort of grammars are parseable by what kind of algorithms, is a fairly core issue in CS. There are pretty interesting and strictly defined classes of expressiveness there. And they relate rather deeply to very profound concepts in CS in general -- what is computable in the first place, what is computable but very expensive to compute, etc.

---

### Post by defmomo on 2008-04-28
Of course, you're right, but what I meant by "parse anything I want" was that as long as I know what "language" or the syntax used by the input(ted?) string, it can still be processed.

---

### Post by pmasiar on 2008-04-28
be careful about 'parse anything I want'. Even very simple example can go out of hand: see 
[(almost) famous Tseitin's undecidable grammar](http://books.google.com/books?id=iNpZYeUvQVAC&pg=PA445&lpg=PA445&dq=tzeitin+example&source=web&ots=v0aSNfpCTt&sig=2FkN8NgmAaCvNF4KyHMQLSs0DKU&hl=en)

---

### Post by defmomo on 2008-04-29
I am not sure I understood everything in that book, need some time to fully process it, so I will do that later in the day, but from what I see, a parser trying to make heads or tails of that particular grammar would end up in an infinite loop.

---

### Post by evymetal on 2008-04-29
Not sure I get the technical meaning of "decidable" - glancing at pmasiar's link is it the same as saying the language is complete (and consistent - but I'm including that)?

If I've got the idea right then this is a **really** interesting problem, since it is in direct correspondence to fundamental statements about mathematics (and some would say philosophy) - and in CS it's directly related to statements such as saying you can't find a program that will decide if any program you give it will terminate or not. It's fairly tough to prove the completeness of any non-trivial 1st order language.

---

### Post by public_void on 2008-04-29
What about a lexical analyzer to pass tokens to the parser? 

As previous posters have said, writing your own parser isn't the best way to approach this. You may find you are more concern writing the C code rather than the lexical analysis and parsing. Using flex and bison are IMO the best approach. As you have said creating the BNF rules is important. Some of these rules can be used for by the lexer to get tokens, such as numbers, keywords, etc. I would start with lexical analysis before parsing because you need a lexer first. The BNF can, with a few changes, be put into bison. I'm seen someone literal generate bison rules from BNF rules with some clever emacs commands, mainly advance regex finding and replacing. After writing the parser you could generate a symbol table and parse tree for semantic analysis. Even compile your language, if possible, into C and compile that using GCC into machine code. These are possible, but made a lot easier using tools already available. It also depends on how far your willing to develop the parser.

---

### Post by CptPicard on 2008-04-29
> **evymetal said:**
> Not sure I get the technical meaning of "decidable" - glancing at pmasiar's link is it the same as saying the language is complete (and consistent - but I'm including that)?

[http://en.wikipedia.org/wiki/Decidable_language](http://en.wikipedia.org/wiki/Decidable_language)

If you've got a Turing machine that can tell whether the string is in the language or not, the language is decidable.

> 
If I've got the idea right then this is a **really** interesting problem, since it is in direct correspondence to fundamental statements about mathematics (and some would say philosophy) - and in CS it's directly related to statements such as saying you can't find a program that will decide if any program you give it will terminate or not.

Exactly. Decidability is essentially the same thing as computability with an algorithm because you can always formulate your algorithmic problem as a decision "parsing" problem. Say, the halting problem simply takes an input that has a description of a Turing machine on the tape, and an input for that machine on the tape after that. Then you just ask "is this pair of machine and input in the set of strings where machine halts with the input?"

(It is important here to make a distinction between computability and computational complexity... for example class NP (like integer factorization) is typically easy to verify in that manner, but producing the answer is hard. Decidable, nevertheless)

---

### Post by Zugzwang on 2008-04-29
I guess we are starting to lose the focus. The OP was dealing with grammars in BNF form. If I remember correctly, these can always be parsed in O(n^2) or O(n^3) time (I forgot which it was) by some general algorithm, so this is not hard. Furthermore if a language that is designed to be written in by humans isn't context-free, then it is likely that the designer didn't do his/her job well. So claiming that this way one could parse "almost any language I want" is quite OK **in this context**. :)

However, stating that it's easier to use bison/yacc is like comparing apples with pears, as they are dealing with only a subset of the context-free languages. Furthermore they often need some additional information, such as specifying look-ahead and so on, so some general parser creating a parse tree from a text and a BNF would be very useful in fact.

In practice, however, O(n^2) or O(n^3) might be too slow. This is why most people use bison/yacc/ANTRL/javacc/whatever as the restricted subset LL(k), LALR(k) and so on are all parsable in linear time (correct me if I am wrong).

---

### Post by defmomo on 2008-04-29
I'm gonna go for coding the parser myself, since it is a code generator is not allowed, and sort of breaks the learning experience (I really haven't understood how to implement it in the code yet.. thinking bout binary trees). I'm not the only coder anyways, we're four, and we have over a month to finish the project. Since the most difficult thing will be the grammar part, I'm confident we'll succeed at it. Thanks for the feedback, it was really helpful.

---

### Post by CptPicard on 2008-04-29
If you're going to code it for yourself, at least use a known algorithm then and write your grammar in a form that that algorithm can parse. Writing completely custom parsers is painful and error-prone. :)

---

### Post by defmomo on 2008-04-29
I am not sure what you mean by algorithm. If you mean How the input will be parsed,  I will use LL, but if you mean how I will use the parsed input, a teacher told me I should use a binary tree and use recursivity(?) for that.

---

### Post by CptPicard on 2008-04-29
An algorithm is an exactly specified method for getting to some kind of result :)

Sounds like it's a [recursive descent]("http://en.wikipedia.org/wiki/Recursive_descent_parser") parser you're after. They can be almost trivially construed from a grammar fulfilling the LL(k) criteria. 

Not sure what you mean by binary trees though as I don't know what you're parsing...

---

### Post by defmomo on 2008-04-29
I'm writing a shell, so I will need to parse at least the same kind of grammar as sh. And by binary tree, I mean basically a structure list (not sure how to say it in english) that either has a link to a another tree, or a link to another level structure, and so on until it reaches a terminal value. For example, here's a tree for parsing the command "ls -l | more | wc -l";echo "hey!"
```

                         "ls -l"
                         /     \
                       "|"      "echo "hey!""
                      /
                    "more"
                   /        
                 "|"
                /
              "wc -l" 
```
I think that's how it goes, I still don't master the concept completely. But this way, the shell executes all the commands going the left-most route, then goes to the first right route, and repeats the same way.

---

### Post by evymetal on 2008-04-29
(sorry for taking this off-topic again)
> **CptPicard said:**
> 
If you've got a Turing machine that can tell whether the string is in the language or not, the language is decidable.


Yup, that's what I was saying - if a language is complete then every sentence is derivable in the sequent calculus (by the competeness thm). I'm just used to the notation from a pure mathematical background as opposed to CS.

---

### Post by CptPicard on 2008-04-29
> **evymetal said:**
> 
Yup, that's what I was saying - if a language is complete then every sentence is derivable in the sequent calculus (by the competeness thm). I'm just used to the notation from a pure mathematical background as opposed to CS.

Okay. Interesting -- never really got too familiar with the formulation from that direction, being a CS guy, but of course it makes sense -- we're just dealing with the kind of limits of symbolic manipulation that the incompleteness thm deals with, and the Turing machine limits follow from there.

As you said, the implications of this are of course totally profound, and I find it fascinating that there is something that deep in CS. One wouldn't think that you can draw parallels all the way to cognitive science through philosophy of AI, for example (like, are there Gödel sentences for the mind? :) )

---

