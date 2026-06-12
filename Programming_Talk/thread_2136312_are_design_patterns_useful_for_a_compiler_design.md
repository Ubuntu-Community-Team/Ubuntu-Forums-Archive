---
title: "are design patterns useful for a compiler design?"
date: 2013-04-17
forum: Programming Talk
---

### Post by cybo on 2013-04-17
Hello everyone.

I will be taking a compiler design class this coming fall. I know that compilers are hard in general, so I want to be prepared for it. I have heard of design patterns but never used them. My understanding is that they can help in the design of the software. Do you guys think it will be helpful for me to learn some of those patterns, and if you do then which ones I should learn, which would be the most helpful patterns?

Any help is appreciated.

---

### Post by slickymaster on 2013-04-17
See this: [http://sourcemaking.com/design_patterns](http://sourcemaking.com/design_patterns)

---

### Post by cybo on 2013-04-17
> **slickymaster said:**
> See this: [http://sourcemaking.com/design_patterns](http://sourcemaking.com/design_patterns)
l was mostly asking which patterns would be the most useful. Do you know which ones I should look at?

---

### Post by slickymaster on 2013-04-17
IMHO, you should at least take a look at  Creational (CategoryCreationalPatterns), Structural (CategoryStructuralPatterns) and Behavioral (CategoryBehavioralPatterns).

---

### Post by cybo on 2013-04-17
> **slickymaster said:**
> IMHO, you should at least take a look at  Creational (CategoryCreationalPatterns), Structural (CategoryStructuralPatterns) and Behavioral (CategoryBehavioralPatterns).
That's all the patterns on the page you have provided. Which ones from each category would be the most useful?

---

### Post by slickymaster on 2013-04-17
> **cybo said:**
> That's all the patterns on the page you have provided. Which ones from each category would be the most useful?

All of them. 

Thing is, since basically what a compiler does is to translate (or compile) a program written in a high-level programming language that is suitable for human programmers into the low-level machine language that is required by computers (during this process, the compiler will also attempt to spot and report obvious programmer mistakes), I really think it would be advisable for you to approach them all.

Creational Patterns for instance, groups patterns that parameterize the behavior of a system based on the classes of objects it creates. Or, more simply put, patterns for dynamically selecting the class of objects to create.
Structural Patterns use various language mechanisms for structuring code and assembling objects.
Lastly, Behavioral Patterns based on class tend to use inheritance to describe algorithms and flow of control, whereas the behavioral patterns that target objects usually describe how a group of objects collaborate to perform some task that no single object can perform alone.

---

### Post by JDShu on 2013-04-17
While design patterns are useful to know because you'll come across them all the time, I don't think it's going to help you that much for a compiler course, especially if you're just learning now. Knowing when to apply which pattern can be tricky business, and you have a good chance of overcomplicating things and missing the main lessons from compilers.

---

### Post by schragge on 2013-04-17
I guess some understanding of what lexical analyzers are and how they work may be helpful. E.g. see [this quick flex tutorial](http://alumni.cs.ucr.edu/~lgao/teaching/flex.html).

---

### Post by r-senior on 2013-04-17
The most important aspect of a design pattern is the motivation for using it. If you don't have the problem it exists to solve, there's no point applying it. I've seen many cases where design patterns are used only because the designer or programmer thinks they should be using a design pattern. 

For compiler writing, I'd follow on from schragge's suggestion and say that the compiler writing tools are more important: lex/flex, yacc/bison and a basic understanding of grammars. Also state machines, recursive descent parsers and hash tables. You should research all of these things and find tutorials. IMO these things will be more important for the specific task of compiler writing than design patterns per se.

---

### Post by ofnuts on 2013-04-18
> **cybo said:**
> Hello everyone.

I will be taking a compiler design class this coming fall. I know that compilers are hard in general, so I want to be prepared for it. I have heard of design patterns but never used them. My understanding is that they can help in the design of the software. Do you guys think it will be helpful for me to learn some of those patterns, and if you do then which ones I should learn, which would be the most helpful patterns?

Any help is appreciated.

The hard part in compiler design isn't the "object" part. Compilers antedate the "Design patterns" books by about 40 years... Better get acquainted with language grammars.

---

