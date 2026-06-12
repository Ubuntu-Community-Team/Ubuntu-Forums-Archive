---
title: "Regular expression for nested parenthes"
date: 2012-06-28
forum: Programming Talk
---

### Post by yc2 on 2012-06-28
Hello,

I have a string  where I easily can find either the starting or the ending parenthesis. Like for example this:

a * (22 + b) + [COLOR="DarkGreen"][COLOR="Blue"]**(**[/COLOR]((4+c)*d)/(5*e + f)[/COLOR]**[COLOR="Red"])[/COLOR]** = value;

Here I can easily find the ending parenthesis **[COLOR="Red"])[/COLOR]** - it is succeeded by a "=".

But is there a general regular expression that would let me find the whole expression (marked in green) backwards to the corresponding starting parenthesis? The corresponding starting parenthesis is marked in blue.

I want a regular expression that finds a string (containing nested parentheses) up to the corresponding parenthesis.

Thanks

---

### Post by sudodus on 2012-06-28
This will be done if you use the editor ***emacs***. It works for me, and I think I have the default settings.

[[COLOR="Red"]_http://emacswiki.org/emacs/ParenthesisMatching_[/COLOR]]("http://emacswiki.org/emacs/ParenthesisMatching")

*Edit: In emacs the above functionality helps while editing, but if you want to do it in a script file, I guess you can add one to a counter at '(' and subtract one from it at ')', so that you are set when reaching zero.*

---

### Post by yc2 on 2012-06-28
Thanks for pointing at emacs. I was on the vi-side in the holy wars of editors, haha. Only because I never learned emacs, I am sure it is excellent.

I agree. Counting +1 for "(" and -1 for ")" is a simple way.

I still wonder, maybe mostly out of curiosity since I like to practice regular expressions, if this can be accomplished with reg exp?

---

### Post by steeldriver on 2012-06-28
There are quite a few hits if you google "regex parse arithmetic expression", e.g.

[http://stackoverflow.com/questions/2595254/matching-math-expression-with-regular-expression](http://stackoverflow.com/questions/2595254/matching-math-expression-with-regular-expression)

I don't know too much about this kind of thing but I would think a simple parser using python (pyparser?) for example - or lex/yacc if you are really oldschool -  would be a better approach (more readable/extensible/maintainable at least)

---

### Post by yc2 on 2012-06-30
Thanks. Now I also searched "matching brackets/parentheses", "balanced parentheses". There does not seem to be a simple regex. I must also learn about Perl. Or just parse it manually with a counter like suggested.

[http://perl.plover.com/yak/regex/samples/slide083.html](http://perl.plover.com/yak/regex/samples/slide083.html)

---

### Post by slavik on 2012-06-30
this is not a problem for a regex solution.

---

### Post by Zugzwang on 2012-06-30
> **slavik said:**
> this is not a problem for a regex solution.

Perhaps it is worthwhile to elaborate. Regular expressions can only recognize stuff that is formally called a "regular language". It can be formally proven that if you want to match braces, then this is not a regular language. Hence, you can't find a suitable regular expression. Thus, "this is not a problem for a regex solution" should not be interpreted as "there are better tools for the job" but rather as "you really can't do it with regular expressions".

However, some implementations of regular expressions have some extensions, and in principle could allow such a thing. See here for more details: [http://en.wikipedia.org/wiki/Regular_expression#Patterns_for_non-regular_languages](http://en.wikipedia.org/wiki/Regular_expression#Patterns_for_non-regular_languages)

---

