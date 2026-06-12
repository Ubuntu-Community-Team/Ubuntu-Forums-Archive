---
title: "awk &amp; sed"
date: 2010-06-08
forum: Programming Talk
---

### Post by Drenriza on 2010-06-08
In sed you can search in a document for a word and replace it with another word.

Im not 100% sure what awk can or cant do. But can it for instance to the same as sed in this example?

Thanks on advance.
Kind regards

---

### Post by amauk on 2010-06-08
awk is a highly flexible scripting language that takes an arbitrary text stream input, processes it according to a list of rules, and outputs the result

sed, grep, etc. are more specialised programs
and came out of the common usage cases of awk
(rather than write a relatively big awk script to print matching lines, just use grep - a program specifically designed to print matching lines)

Think of the stream utilities (sed, grep, etc.) as providing a subset of awks functionality

Perl was also heavily influenced by awk

---

### Post by Compyx on 2010-06-08
This sed command:
```

sed -i 's/foo/bar/g' SOMEFILE

```
can be implemented in awk like this:
```

awk '{ gsub(/foo/, "bar", $0); print }' SOMEFILE

```

Generally awk is used to perform (complex) operations based on patterns, while sed is simply a stream editor. For simple substitutions, I'd use sed, but for more complex operations like generating reports, gathering statistics, and so forth, I'd use awk.

---

### Post by Drenriza on 2010-06-08
> **Compyx said:**
> 

Generally awk is used to perform (complex) operations based on patterns, while sed is simply a stream editor. For simple substitutions, I'd use sed, but for more complex operations like generating reports, gathering statistics, and so forth, I'd use awk.

gathering statistics is very intersting for me. What and how do you exactly gather? how detailed can you get?

---

### Post by Compyx on 2010-06-09
> **Drenriza said:**
> gathering statistics is very intersting for me. What and how do you exactly gather? how detailed can you get?

It depends on what you want. As far as I know Awk doesn't have any built-in statistical analysis tools/functions, but since Awk is a full-fledged programming language with support for floating point arithmetic, associative arrays and basically the same set of operators C has, you can write quite complex programs to do whatever you want.

Although Awk is generally used with one-shot, throw-away code, I'm using Awk to write a database application to keep track of all sorts of items, monsters and quests in Final Fantasy XII. I can do all sorts of things you'd normally use SQL for, simply with a bunch of Awk-scripts, glued together with shell-scripts. All my tables are simple flat text files which I edit with Vim. I'm having a blast working on it, and I'm learning a lot about shell-programming and Awk-programming in the process.

---

