---
title: "Help with sed script"
date: 2016-06-28
forum: Programming Talk
---

### Post by Sigma1 on 2016-06-28
Hello,
Doing linguistics research I've got a text on line 1, which I'd like to replace when the sequence on lines 1 and 2 form a certain pattern. I can locate the string with regex, but how can I replace the string, partly with something new, and partly with something old?
Concretely, I've got
```
en	PRO:PER	en
vieillissant
```
and I want
```
en	PRP	en
vieillissant
```
I can find the sequence with
```
en\tPRO:PER\ten\n.*ant
```
But how can I just replace "PRO: PER" with "PRP" inside this sequence?
Thanks in advance for any tips!

---

### Post by sudodus on 2016-06-28
Use [SIZE=3]***s***[/SIZE] for 'substitute' for example

```
sed s/PRO:PER/PRP/
```

---

### Post by Sigma1 on 2016-06-28
Thanks. I wasn't explicit enough perhaps. I know the basic sed syntax. Thing is, I don't want to remove all instances of "PRO: PER" in the document. "PRO: PER" is a grammatical tag, "personal pronoun". Here it should be "PRP" for "preposition", but in other places, I'm going to need the PRO: PER tag.
Now the word "en" in French is wrongly tagged "PRO: PER" in certain environments (when followed by a word that ends with "ant", basically), so I want to replace it in those environments only, while leaving the "ant" word as it was. I think I probably need to set up a variable for the "ant" word, and to use this in the replacement text.
Hope that's a bit clearer, and thanks for the interest!

---

### Post by steeldriver on 2016-06-28
Would

```

sed '/en\tPRO:PER\ten/ {N; /\n.*ant$/ s/PRO:PER/PRP/}' yourfile

```

work for you?

---

### Post by Sigma1 on 2016-06-28
Thanks for looking into this. Unfortunately no, that didn't do the trick. I might have to go with perl, which will probably handle the variables better than sed. More trial and error ahead...

---

### Post by steeldriver on 2016-06-28
It works for me, when given the exact input specified in your first post

```

$ cat input
en    PRO:PER    en
vieillissant

en    PRO:PER    en
something else

```
```

$ sed '/en\tPRO:PER\ten/ {N; /\n.*ant$/ s/PRO:PER/PRP/}' input
en    PRP    en
vieillissant

en    PRO:PER    en
something else

```

So I suspect you are not accurately describing your requirements

---

### Post by Sigma1 on 2016-06-28
Thanks for sticking with me. The original text, then, is:

```
en	PRO:PER	en
vieillissant	VER:ppre	vieillir
```

stored in a file infile.txt

When I run

```
sed '/en\tPRO:PER\ten/ {N; /\n.*ant$/ s/PRO:PER/PRP/}' infile.txt > outfile.txt
```

Then the outfile.txt created is exactly the same as infile.txt whereas I would like it to be:

```
en	PRP	en
vieillissant	VER:ppre	vieillir
```

i.e. substitute PRO: PER with PRP when "en" is followed with a word ending in "ant". Thanks again for your help.

---

### Post by steeldriver on 2016-06-28
OK so it should just be a matter of replacing the $ (which anchors the .*ant pattern to the end of the line) with \b (which anchors it to the end of a word):

```

sed '/en\tPRO:PER\ten/ {N; /\n.*ant**\b**/ s/PRO:PER/PRP/}' input

```

If there's any chance of the ant\b sequence occurring elsewhere in the line, you might want to limit it to the first word (i.e. sequence of non whitespace characters) after the newline, e.g.

```

sed '/en\tPRO:PER\ten/ {N; /**\n[^[:space:]]*ant\b**/ s/PRO:PER/PRP/}' input

```

---

### Post by Sigma1 on 2016-06-28
Thanks a million. Looks like that works! If you have a minute to explain what's going on here (the curly braces and the N; declaration), it would help me do my own stuff in future, but thanks again in any case!

---

### Post by steeldriver on 2016-06-28
Breaking it down:
[INDENT]if [FONT=courier new]/en\tPRO:PER\ten/[/FONT] matches in the current line; then
[/INDENT]
[INDENT=2][FONT=courier new]{
[/FONT][/INDENT]
[INDENT=2][FONT=courier new]N [FONT=arial]# append the next line, separated by[/FONT] \n
/\n[^[:space:]]*ant\b/ s/PRO:PER/PRP/ [FONT=arial]# test to see if the part after the[/FONT] \n [FONT=arial]matches[/FONT] [^[:space:]]*ant\b [FONT=arial]and if it does, substitute[/FONT] PRP [FONT=arial]for[/FONT] PRO:PER
}[/FONT]
[/INDENT]

---

### Post by Sigma1 on 2016-06-28
Pure poetry. I'll sleep a little wiser this evening. Thanks for your time and patience.

---

