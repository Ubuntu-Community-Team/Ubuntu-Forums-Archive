---
title: "Renaming multiple files using wildcards?"
date: 2014-09-06
forum: Programming Talk
---

### Post by stretch4 on 2014-09-06
Ok, so I have a list of Intellivision rom files like this:

```
...
Commando (1987).int
Congo Bongo (Sega).int
Deep Pockets-Super Pro Pool and Billiards (1990) (Realtime) [!].int
Defender (Atarisoft).int
Demon Attack (Imagic) [!].int
Dig Dug (1987) (Intv Corp).int
Diner (1987) (Intv Corp).int
Donkey Kong (Coleco).int
Donkey Kong Jr (Coleco).int
Dracula (Imagic) [!].int
Dragonfire (Imagic) [!].int
...

```

I would like to remove anything that's in parenthesis, resulting in a list like this:

```
...
Commando.int
Congo Bongo.int
Deep Pockets-Super Pro Pool and Billiards [!].int
Defender.int
Demon Attack [!].int
Dig Dug.int
Diner.int
Donkey Kong.int
Donkey Kong Jr.int
Dracula [!].int
Dragonfire [!].int
...

```

I've tried using pyRenamer and GPRename, but neither one seems to be able to do it. I imagine this could be done with the rename command, but I don't understand perl expressions.  This is what I tried with rename, but it didn't work...

```
rename -vn 's/^(*)//' *.int
```
```
rename -vn 's/\(*)//' *.int
```

I would prefer a GUI solution, but the terminal would be ok.

---

### Post by steeldriver on 2014-09-06
You basically got it - just a couple of things


[LIST]
[*]you're confusing shell globbing (where * means anything) and regex where it just means zero or more of the previous 'atom' - you need **.*** to mean zero or more (*) of any single character (.) 
[/LIST]

[LIST]
[*]you need to escape both parentheses \( and \) to stop them from being treated as grouping markers 
[*]you probably want to strip either the leading or trailing space else you will end up with things like  'Diner .int' instead of 'Diner.int' 
[/LIST]
 
```

rename -nv 's/**[COLOR=#0000ff]\s*[/COLOR][COLOR=#ff0000]\[/COLOR]([COLOR=#ff0000].[/COLOR]*****[COLOR=#ff0000]\[/COLOR])**//' *.int

```

---

### Post by stretch4 on 2014-09-06
> **steeldriver said:**
> you're confusing shell globbing (where * means anything) and regex where it just means zero or more of the previous 'atom' - you need **.*** to mean zero or more (*) of any single character (.) 
So...let me see if I got this straight. 
[LIST]
[*]* means zero or more of the previous atom. What's an atom? 
[*]I don't understand what you mean by "you need .* to mean zero or more (*) of any single character. (.)" Could you elaborate? 
[*]Using a \ to escape the parenthesis is simple enough. 
[/LIST]

If you could point me to a good website to learn this stuff, that would be much appreciated.

> ```
rename -nv 's/**[COLOR=#0000ff]\s*[/COLOR][COLOR=#ff0000]\[/COLOR]([COLOR=#ff0000].[/COLOR]*****[COLOR=#ff0000]\[/COLOR])**//' *.int
```
This one worked. Thank you.

---

### Post by Vaphell on 2014-09-07
> * means zero or more of the previous atom. What's an atom?


atom would be anything that answers the "what?" question
. any char
\. a literal dot
X a character X
[abc] character belonging to a defined subset
\s \w \d character belonging to abstract classes like any whitespace or "word chars" or digits
(abc[XYZ]) a parenthesized group treated as a single entity

in regular expressions these atoms are optionally followed by modifiers describing quantity. By default if you put X it means exactly one X, whatever that X would be.

<"atom"><optional modifier describing quantity>

modifiers defining quantity are as follows
*  0 or more
+ 1 or more
? 0 or 1
{n} - exactly n times
{n,m} - between n and m times

if you want to construct a pattern for "sequence of any length of whatever chars" you take any char **. **and multiply it by *****, thus yielding the **.* **pattern

at least 2 digits followed optionally by a lowercase letter?
[0-9][0-9][0-9]*[a-z]?
\d{2,}[a-z]?
or any other combination logically having the same meaning.


Chars . * + ? {}[]() | having regex meaning means that in order to use them in literal sense you need to "hide" them by escaping with \ or by burying them inside  [ ] (regex sees subset of chars)

---

### Post by stretch4 on 2014-09-07
Thank you Vaphell! Very helpful. I'll be saving this post to refer back to. I wash that info was in rename's man page.

---

### Post by Vaphell on 2014-09-08
regular expressions are used everywhere so it doesn't make much sense to put their rules in a manuals of tools utilizing them. That would be a lot of redundancy. Manuals just assume that you reference the regex docs for the actual pattern building.

google 'regular expressions' and you are golden. There are many websites covering them, there are also regex testers and builders available.

---

