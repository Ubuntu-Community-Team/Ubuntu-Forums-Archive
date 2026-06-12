---
title: "How do I use the Grep command to find this"
date: 2013-10-28
forum: New to Ubuntu
---

### Post by lombe.chileshe on 2013-10-28
I have a list in a file that contains various strings.
The question is I should grep a list that's talking about the country "china" in my file.
The problem is Taiwan is also called "The republic of china" and China is called The "People's Republic of China".
I only want to return information talking about China and none talking about Taiwan.
How do I go about this?

---

### Post by Toz on 2013-10-28
Hello and welcome to the forums.

Is this a homework request? You should know that requesting answers to homework questions is frowned upon in this community. However, I will point you in the right direction. Open a terminal window and type in:
```
man grep
```
...or view the man page online here: [http://manpages.ubuntu.com/manpages/precise/man1/grep.1.html]("http://manpages.ubuntu.com/manpages/precise/man1/grep.1.html").

Your answer can be found there.

---

### Post by lombe.chileshe on 2013-10-28
@ Toz. not a homework request. Just a question I saw in some notes ( Trying to teach my self to learn how to use Ubuntu)
I'll look through that. Thanks

---

### Post by Toz on 2013-10-28
Okay. In that case have a look through the documentation I linked. Man pages are a very helpful resource for learning unix/linux but can also be a little intimidating to the new user. Try a few things and if your still stuck, post back what you've tried. We'll be glad to guide you in the right direction.

---

### Post by lombe.chileshe on 2013-10-28
@ Toz the worst thing about the manuals is they don't have any examples. Difficult to understand the context for a beginner like me.

---

### Post by vasa1 on 2013-10-28
Why don't *you* provide an actual sample of text?

---

### Post by lombe.chileshe on 2013-10-28
@Toz. That being said, I tried using this, but I'm still getting Republic of China.

cat enwiki-20130904-all-titles | grep -iw "china" | grep -i  "republic"

---

### Post by Toz on 2013-10-28
> **lombe.chileshe said:**
> @Toz. That being said, I tried using this, but I'm still getting Republic of China.

cat enwiki-20130904-all-titles | grep -iw "china" | grep -i  "republic"

> The problem is Taiwan is also called "The republic of china" and China is called The "People's Republic of China".
The only difference between those two labels is the word "People's". Grepping for that word should help.

---

### Post by sudodus on 2013-10-28
I suggest that you search in two steps using pipeline '|'

1. search for all lines containing china (case insensitive) [FONT=courier new]**grep -i china**[/FONT]

2. try searching for all lines not containing 'the republic' (case insensitive) [FONT=courier new]**grep -iv  'The republic'**[/FONT]

You might need to try several methods or wordings to find what you want (more or less manual)

```
grep -i china|grep -iv  'the republic' filename
```

---

### Post by lombe.chileshe on 2013-10-28
@Vasa1. It's a really long list. Over 10,000 components.

---

### Post by lombe.chileshe on 2013-10-28
@Toz & @Sudodus. Thanks for the help. I will try both of those things.

---

### Post by steeldriver on 2013-10-28
Probably the most elegant way to handle something like this is via perl-style *lookarounds*

For example, if you have

```

$ cat china.txt
1) china
2) China
3) Republic of China
4) People's Republic of China
5) Mao's Republic of China
6) any other line
7) more non-China text

```

then you can write a perl-style grep (pgrep) to match occurrences of "china" that are NOT preceded by "republic of" as

```

$ grep -Pi '(?<!republic of )china' china.txt
1) china
2) China
7) more non-China text

```

(*negative lookbehind*). You can then add back matches of "republic of" that ARE explicitly preceded by  "people's" (sorry about the ugly escaped \27 for the single-quoted apostrophe)

```

$ grep -Pi '((?<=people\x27s) republic of )china' china.txt
4) People's Republic of China

```

(*positive lookbehind*). Putting them together with a logical OR we get

```

$ grep -Pi '((?<!republic of )|((?<=people\x27s) republic of ))china' china.txt
1) china
2) China
4) People's Republic of China
7) more non-China text

```

For clarity I've used literal single spaces between words - you could make it a little more robust by using \s or \s+ (although note that the lookbehinds themselves cannot be variable length).

---

