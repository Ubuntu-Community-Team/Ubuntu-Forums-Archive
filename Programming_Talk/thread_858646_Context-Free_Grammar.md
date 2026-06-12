---
title: "Context-Free Grammar"
date: 2008-07-13
forum: Programming Talk
---

### Post by kenshinofkin on 2008-07-13
I miss a class on context-free grammars at my school and am having a problem understanding how to create them. Here is a question from my book:

For all problems use the alphabet sigma = { a , b }.

1) Create a context-free grammar for the language that consists of all strings containing ‘aaa’.

If anyone could help me with how to create the grammar it would help me alot. I just need to see a problem done and I think I will understand it from there.

Thanks

---

### Post by kknd on 2008-07-13
Using S as the starting simbol, and & as "empty word":

S -> XaaaX
X -> aX | bX | &

---

### Post by kenshinofkin on 2008-07-13
Thank you so much! Just to see if I am doing this right.

2) Create a context-free grammar for the language that consists of all strings where the first letter equals the last letter.

I came up with:

S -> aA | bB
A -> aA | bA | C
B -> aB | bB | D
C -> a
D -> b

I hope this is right. Thanks again!!!

---

### Post by kknd on 2008-07-13
Hi, I think that its correct!

---

### Post by KedDeK on 2008-07-13
> **kenshinofkin said:**
> 
2) Create a context-free grammar for the language that consists of all strings where the first letter equals the last letter.

I came up with:

S -> aA | bB
A -> aA | bA | C
B -> aB | bB | D
C -> a
D -> b
You are missing some border cases, for example empty string (doesn't have any letter so the first letter equals the last letter) and also words with only 1 letter (in which first and last are the same, so they are equal). Also note that variables C and D are unnecessary.

So the fix would be:

S -> aA | bB | a | b | &
A -> aA | bA | a
B -> aB | bB | b

This grammar also does the same, and has 1 variable less :)

S -> aAa | bAb | a | b | &
A -> aA | bA | &

---

