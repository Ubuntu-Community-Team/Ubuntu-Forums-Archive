---
title: "n-pass vs n-parse - What the .....?"
date: 2009-07-15
forum: Programming Talk
---

### Post by lisati on 2009-07-15
Has anyone else encountered this?

I was having a look at Wikipedia's [discussion page]("http://en.wikipedia.org/wiki/Talk:Compiler#Disputed") on the entry on [compilers]("http://en.wikipedia.org/wiki/Compiler")

I was a bit baffled by a reference to "n-parse" compilers - I always thought it was "n-pass" because a compiler might have to have "n" passes (scans) over a source file to be able to compile it into its final form.

---

### Post by Reiger on 2009-07-15
Haven't had a look, but it is perfectly possible for some compiler to `parse' in multiple passes in the sense that it mangles the syntax tree to equivalent forms that are easier to compile or to simply compile in multiple stages. It's where adjectives like "shallow" and "deep" come into play.

With shallow parsing it is possible to resolve scope, which can be used to build the abstract syntax tree in the first place. Then other built-in parsers/tools can work their way on individual blocks/inline statements which can be easier than to write one big parser to encompass all possibilities. So the other tools could then interact with the syntax tree, much in the same way you transform raw XML with XSLT.

Taking C as an example, the C preprocessor part of the compiler/tools doesn't have to worry about the actual C in the file it only needs to resolve the preprocessor statements and imports. So this can be done by 'running a C-preprocessor template' on the "C-preprocessor-nodes" of a document. 

And for a functional language it is perfectly possible for a compiler to have an insertion-sort like algorithm for "symbols" in the code to avoid "undefined symbols" in the lower-level code you compile to. This would allow you to pretend in the original language that order of definition/declaration doesn't matter.

So it is quite possible for a compiler with n-passes to parse the file m times (with m a positive integer large than 1).

---

### Post by lisati on 2009-07-15
Thanks......

---

