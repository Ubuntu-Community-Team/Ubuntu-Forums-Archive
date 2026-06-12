---
title: "How to change brace colour in SciTE?"
date: 2008-04-04
forum: Programming Talk
---

### Post by fogus on 2008-04-04
Hello all,

For those of you who don't want to read this whole thing, basically I want to colour my braces independently from other parts of my program.

Quick question for you guys (Version 1.72, [http://www.scintilla.org/SciTE.html](http://www.scintilla.org/SciTE.html)):
I would like the braces (ie these things ---> (), {}, [] ) to be a different colour than my text.

I have been messing around with the cpp.properties and the SciTEGlobal.properties files for a long time. Then I went to google and searched endlessly.

I am programming in Java in a dark background.

In cpp.properties I have:
-----------------------------------------

keywordclass.java=abstract assert boolean break byte case catch char class \
const continue default do double else extends final finally float for future \
generic goto if implements import inner instanceof int interface long \
native new null outer package private protected public rest \
return short static super switch synchronized this throw throws \
transient try var void volatile while true false
keywords.*.java=$(keywordclass.java)

...

# Keyword
style.cpp.5=fore:#cc0000

...

# Keywords2
style.cpp.16=fore:#CC6600

------------------------------------------------------

Now, what I thought I should do would be to add on the symbols I want to the end of the keywords part, like:
keywordclass.java=abstract assert boolean break byte case catch char class \
...
transient try var void volatile while true false { } ( ) [ ]
keywords.*.java=$(keywordclass.java)

But that doesn't do anything. When I add my own words it works fine. (like "dog" and "bark"). SciTE doesn't seem to recognize brackets as keywords.

What I really want to do is to have my brackets a different colour than my keywords. I'm thinking a light purple (dark background remember). My keywords are in fire engine red. Could I have them part of my own keywords2.java or keywordsclass2.java? Maybe even put other things in there too? That would be just dandy. I have no idea how to do it.

One last thing, has anyone found a way to have the braces rotate through a variety of colours (so they don't all look the same)? I know I've seen it done before.

Cheers everyone,
~fogus

---

