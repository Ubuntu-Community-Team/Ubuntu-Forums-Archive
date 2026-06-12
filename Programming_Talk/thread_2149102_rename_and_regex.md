---
title: "rename and regex"
date: 2013-05-27
forum: Programming Talk
---

### Post by rebeltaz on 2013-05-27
How can you batch rename files while retaining certain portions and replacing others? For example:

original filename:
prefix.Y01Z18.suffix.ext

renamed to:
y01z18.ext

All files have this same format but: the suffix is not always the same text; the prefix is not always the same; the numbers after Y and Z change from file to file. 

What I am looking for is something along the lines of

rename 's/.+YxxZxx.+\.ext/yxxzxx\.ext/' *.ext

where xx leaves that digit intact. I know about a program but that is overkill for what I want and it actually adds more than I want to the filenames. 

Thanks...

---

### Post by steeldriver on 2013-05-27
You can do that by grouping the bits you want to keep between parentheses, and then substituting those groups using $1, $2, etc. in the replacement string e.g.

```
$ rename -nv 's/.*[.]S**([0-9]+)**E**([0-9]+)**[.].*[.]mp4/s**$1**e**$2**.mp4/' *.mp4
prefix.S01E18.suffix.mp4 renamed as s01e18.mp4
```

---

### Post by rebeltaz on 2013-05-27
Thank you SO much! That is exactly what I was looking for! :)

---

### Post by rebeltaz on 2013-05-27
One thing.. what does the [] around the dots do? Thanks.

---

### Post by steeldriver on 2013-05-27
In general [ ] defines a range of characters for example later we have [0-9] meaning any single digit, but in the case of [.] it's just a way to escape the regex meaning of '.' (= any single character) so that it matches a literal period instead - an alternative way to do the same thing is with a backslash escape ie \. but sometimes [.] is easier to read

---

### Post by HiImTye on 2013-05-27
'[.]' is the same as '\.' - it means match one of the characters inside (or one not inside) the square brackets, ie [xyzX] will match any of x, y, x, or X, while [^xyzX] will match any that is NOT x, y, z, or X. as usual you can use *+? etc to specify repetition.

anyway you do this because '.' means 'any character'

edit: a better way would be
```
rename -n 's|.*([a-zA-Z][0-9][0-9][a-zA-Z][0-9][0-9]\.[a-zA-Z0-9]*)|\L$1|' fileOrFiles
```
which will match any of
```
blahblah.S11E11.ext
blahy32Z32.extension
really long filename.with.extra.stuff.A12B33.extension
```
and turn them into
```
s11e11.ext
y32z32.extension
a12b33.extension
```


[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by rebeltaz on 2013-05-27
Oh, OK.. that was what confused me. I am used to seeing it as \. 

Thanks again!

---

### Post by rebeltaz on 2013-05-27
> **HiImTye said:**
> 
edit: a better way would be
```
rename -n 's|.*([a-zA-Z][0-9][0-9][a-zA-Z][0-9][0-9]\.[a-zA-Z0-9])|\L$1|' fileOrFiles
```
which will match any of
```
blahblah.S11E11.ext
blahy32Z32.extension
really long filename.with.extra.stuff.A12B33.extension
```
and turn them into
```
s11e11.ext
y32z32.extension
a12b33.extension
```

[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

OK... I guess '|' is taking the place of '/'. It looks like that just extracts the a12b34 pattern and carries it to the other side along with the extension? I like that. What does the 'L' in 'L$1' do?

---

### Post by HiImTye on 2013-05-27
\L converts everything that follows to lowercase, while \l converts the next letter to lowercase. I'd share a good info page but I need to set up Firefox Sync on my tablet again

and yeah, I like pipes, it prevents picket fencing

edit: I edited my previous post so thst it grabs more than one letter extensions /braindead
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by rebeltaz on 2013-06-02
> **HiImTye said:**
> \L converts everything that follows to lowercase, while \l converts the next letter to lowercase. I'd share a good info page but I need to set up Firefox Sync on my tablet again

and yeah, I like pipes, it prevents picket fencing

edit: I edited my previous post so thst it grabs more than one letter extensions /braindead
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]


I just now got around to trying this and it is grabbing everything after the first dot after the A12B33.

e.g.
really.long.filename.with.extra.stuff.A12B33.and.more.stuff.extension

  becomes

a12b33.and.more.stuff.extension

  instead of 

a12b33.extension


I have been trying to figure out on my own how to match the characters after the last dot, but nothing is working.. :(

---

### Post by Vaphell on 2013-06-03
```
$ rename -nv 's/.*([a-zA-Z][0-9]+[a-zA-Z][0-9]+).*[.]**([^.]+)**$/\L$1.**$2**/' really*
really.long.filename.with.extra.stuff.A12B33.and.m ore.stuff.extension renamed as **a12b33.extension**
```

---

### Post by rebeltaz on 2013-06-03
> **Vaphell said:**
> ```
$ rename -nv 's/.*([a-zA-Z][0-9]+[a-zA-Z][0-9]+).*[.]**([^.]+)**$/\L$1.**$2**/' really*
really.long.filename.with.extra.stuff.A12B33.and.m ore.stuff.extension renamed as **a12b33.extension**
```

Wow... regex may be REGULAR, but it makes my head hurt! OK, so...

I understand the .*([a-zA-Z][0-9]+[a-zA-Z][0-9]+).* but why the next [.] after that? How does [^.]+ match the extension? If I understand regex correctly (and I do not!) [^.] matches any character that is not a . (which is confusing because ^ without the brackets indicates the start of the line! ](*,) ). Would that not be every alphanumeric character including the extension?

I promise I am not looking JUST to have this written for me. I really do want to understand it so I can do this on my own next time. Yeah, I know... rather presumptuous of me :) 

But I do appreciate all of the help!

---

### Post by Vaphell on 2013-06-03
[^.]+ = not-dot 1-or-more times
general idea:
*anything*[COLOR="#0000CD"](char-digits-char-digits)[/COLOR]*anything*[dot][COLOR="#008000"](not-dots)[/COLOR]*end-of-line* => [COLOR="#0000CD"]$1[/COLOR].[COLOR="#008000"]$2[/COLOR]
obviously 2nd parenthesis can only store extension because it forces everything between last dot and end-of-line. In the replacement you invoke the content of that parenthesis with $2

your current code simply finds the episode number and takes everything after it verbatim, that's why any garbage that happens to be there after the number gets to the final name (first part up to the number gets transformed but anything after gets through).

**(something.[COLOR="#0000CD"]s01e01[/COLOR]=> [COLOR="#0000CD"]s01e01[/COLOR])**.garbage.ext       (bold shows the scope of your regex substitution)


In my regex i match the whole name from start to end, with **.*[.] ** to consume any garbage to the last dot leaving only extension to be captured and used to construct final name.

**something.[COLOR="#0000CD"]s01e01[/COLOR].garbage.[COLOR="#008000"]ext [/COLOR]=> [COLOR="#0000CD"]s01e01[/COLOR].[COLOR="#008000"]ext[/COLOR]**

---

### Post by rebeltaz on 2013-06-03
I think what I don't understand is why .*[.] stops at the LAST [.] instead of the first [.] it comes to...

---

### Post by ofnuts on 2013-06-03
> **rebeltaz said:**
> I think what I don't understand is why .*[.] stops at the LAST [.] instead of the first [.] it comes to...
Because that the normal "greedy" behavior in regular expressions. In "aaabbbcccaaabbbccc" you have three possible matches for "aaa.*ccc": the first "aaabbbccc", the second one, or the whole string. I know, you are going to ask, "But why the VisualBasic is the default behavior to match the whole string"? And the answer is, because it is a lot easier in that case to prevent that behavior
[*] and write an expression that matches only the first or last small strings than it would be, if the "frugal" behavior was the default, to construct a regexp that matches the whole string.   

Some regexp syntaxes have a modifier (*?, +?) that let you specify the shortest match. But Real Men don't use it :)

[*] "aaa[^a]*ccc"

---

### Post by Vaphell on 2013-06-03
just like ofnuts said by default regexes try to consume as much as possible, besides when you write regex .*[.][^.]+$ there is no other option, $ clarifies it: **line has to end with  [.][^.]+**. If after that dot only non-dots are allowed then it's the last one.

```
[COLOR="#0000FF"]abc[/COLOR].[COLOR="#008000"]def[COLOR="#FF0000"].[/COLOR]ghi[/COLOR] / [COLOR="#0000FF"] .*[/COLOR][.][COLOR="#008000"][^.]+[/COLOR]$
```
no way it will ever match, dot would have to be consumed by non-dot+ which is impossible

```
[COLOR="#0000FF"]abc.def[/COLOR].[COLOR="#008000"]ghi[/COLOR] / [COLOR="#0000ff"].*[/COLOR][.][COLOR="#008000"][^.]+[/COLOR]$
```
everything is fine

---

### Post by rebeltaz on 2013-06-03
Oh! I didn't see the dollar sign at the end of that equation. Now I get it. 

Aren't the two examples above (abc.def.ghi / .*[.][^.]+$) the same? 

Thank you all. You have been a great help! :)

---

### Post by trent.josephsen on 2013-06-03
> **rebeltaz said:**
> Oh! I didn't see the dollar sign at the end of that equation. Now I get it.
That's good, but it's important to note that the pattern will match (for the example strings) in exactly the same way without the dollar sign, because of the greediness of the * and + quantifiers and because [^.]+ matches only non-dots.

> Aren't the two examples above (abc.def.ghi / .*[.][^.]+$) the same?

What Vaphell was pointing out was that some parts of the pattern match different parts of the string, which affects the substrings ($1 and $2) captured by the parentheses () in the original pattern.

E.g. when matching against the string "hello, world":

[LIST=1]
[*]/([a-z]*)/ will match the first 5 characters of the string, putting 'hello' into $1;
[*]/.*([a-z]*)/ will match the whole string, putting '' (the empty string) into $1;
[*]/.*?([a-z]*)/ will match the whole string, putting 'world' into $1;
[*]/([a-z]*)$/ will match the last 5 characters of the string, putting 'world' into $1.[/LIST]

The first three patterns match all the same strings -- it's not possible to construct a string for which one of them succeeds but another fails. (The fourth pattern only matches at the end of the string, so it'll never match a string like "hello, world4".) The differences lie in which parts of the string they match *first*, and how quickly that happens. (In many cases, /.**PATTERN*/ matches the same thing as /*PATTERN*$/, but is likely to do it faster -- sometimes much faster.)

This is stuff I picked up from the Camel book, and happens to apply because rename is written in Perl. Other languages and regex engines have slightly different rules, syntaxes and performance profiles, but the general concepts (like greediness) are the same.

---

### Post by rebeltaz on 2013-06-03
I think I understand, but I may need to take college course on regex if I ever attempt this again!

---

### Post by ofnuts on 2013-06-04
No need for a college course. Everything is there: [http://www.amazon.com/Mastering-Regular-Expressions-Jeffrey-Friedl/dp/0596528124/](http://www.amazon.com/Mastering-Regular-Expressions-Jeffrey-Friedl/dp/0596528124/)

---

### Post by rebeltaz on 2013-06-04
lol... I'll have to order that. Thanks!

---

### Post by ofnuts on 2013-06-04
Don't hesitate... the shortest path to regexp guru status.

---

