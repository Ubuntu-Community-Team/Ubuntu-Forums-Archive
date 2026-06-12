---
title: "regex (regular expression) to find and replace all words in geany"
date: 2010-04-11
forum: Programming Talk
---

### Post by nexx on 2010-04-11
I am using geany to program javaScript, html and css and find it to be a wonderful program. But I cannot find a regular expression to enclose all words in a sentence with  html tags.
What I want to do is taking a phrase like: An example phrase.
And modify it to get: <i>An</i> <i>example</i> <i>phrase</i>.

For example: (\<)(.*)(\>)
replace with: <i>\2</i>

will do: <i>An example phrase.</i>

I have tried all kind of variation with the: \<	(This supposedly matches the start of a word) and \> (This is supposed to match the end of a word)

---

### Post by geirha on 2010-04-11
The thing is that * is greedy, so it'll match as much as it can. Instead of matching any char greedily, match non-space greedily.

So try to match: \<[^ ]*\>
And replace with: <i>&</i>

I've never used geany, so I don't know if that's correct with regards to its regex implementation.

---

### Post by nexx on 2010-04-11
search:
\<([^ ]*)\>

replace with:
<i>\1</i>

did the trick, thank you

---

