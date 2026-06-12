---
title: "Java Regular Expressions"
date: 2008-04-12
forum: Programming Talk
---

### Post by DBQ on 2008-04-12
Hi everybody.

Simple question about java regular expressions.  Using the Pattern and Matcher classes.  

Suppose my text contains characters such as "( )" .  However, these are special characters used for capturing strings.  Suppose I want to get the tokens inside the if statement "if(x==y)"  do I specify the parenthesis as regular characters using "\(\)"? -- like in Perl?

---

### Post by nick_h on 2008-04-12
Have a look at the "Backslashes, escapes, and quoting" section in [this](http://java.sun.com/j2se/1.5.0/docs/api/java/util/regex/Pattern.html) link.

Use \\( and \\)

---

