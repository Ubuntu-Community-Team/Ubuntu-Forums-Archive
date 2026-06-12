---
title: "The Logic behind solving Logic?"
date: 2010-04-14
forum: Programming Talk
---

### Post by Pyro.699 on 2010-04-14
Hello,

Ive reached a point in my program where i decided to come to the outside community to try and get a bit of advice or methodology behind the task i have at hand. Here is a basic setup of a given array:

[php]
operations = [
    [ ["a"], ["c"] ],
    [ ["b"], ["d"] ], 
    [ ["a","c"], ["a","e"], ["a","f"], ["c","e"], ["c","f"], ["e","f"] ], 
    [ ["f"], ["g"] ], 
    [ ["f"], ["g"] ], 
    [ ["b","d"], ["b","g"], ["b","h"], ["d","g"], ["d","h"], ["g","h"] ], 
    [ ["c"], ["e"], ["f"], ["i"] ], 
    [ ["d","g","h"], ["d","g","j"], ["d","h","j"], ["g","h","j"] ], 
    [ ["e","f"], ["e","i"], ["e","k"], ["e","l"], ["e","m"], ["f","i"], ["f","k"], ["f","l"], ["f","m"], ["i","k"], ["i","l"], ["i","m"], ["k","l"], ["k","m"], ["l","m"] ], 
    [ ["f"], ["g"], ["l"], ["m"], ["n"] ], 
    [ ["f"], ["g"], ["m"], ["n"], ["o"] ], 
    [ ["g","h"], ["g","j"], ["g","n"], ["g","o"], ["g","p"], ["h","j"], ["h","n"], ["h","o"], ["h","p"], ["j","n"], ["j","o"], ["j","p"], ["n","o"], ["n","p"], ["o","p"] ] 
]
[/php]

The formula followed for this is that the **operations[x]** will contain all of the condition sets. **operations[x][y]** will be the set of conditions, each new entry in this set is treated as another &#8853; to the set. **operations[x][y][z]** will be sets of ^ conditions to be joined with the other **operations[x][y]** sets with &#8853;. If that was a little confusing here is what the translation of the above would be.

[LIST]
[*](A) &#8853; (C)
[*](B) &#8853; (D)
[*](A ^ C) &#8853; (A ^ E) &#8853; (A ^ F) &#8853; (C ^ E) &#8853; (C ^ F) &#8853; (E ^ F)
[*](F) &#8853; (G)
[*](F) &#8853; (G)
[*](B ^ D) &#8853; (B ^ G) &#8853; (B ^ H) &#8853; (D ^ G) &#8853; (D ^ H) &#8853; (G ^ H)]
[*](C) &#8853; (E) &#8853; (F) &#8853; (I)
[*](D ^ G ^ H) &#8853; (D ^ G ^ J) &#8853; (D ^ H ^ J) &#8853; (G ^ H ^ J)
[*](E ^ F) &#8853; (E ^ I) &#8853; (E ^ K) &#8853; (E ^ L) &#8853; (E ^ M) &#8853; (F ^ I) &#8853; (F ^ K) &#8853; (F ^ L) &#8853; (F ^ M) &#8853; (I ^ K) &#8853; (I ^ L) &#8853; (I ^ M) &#8853; (K ^ L) &#8853; (K ^ M) &#8853; (L ^ M)
[*](F) &#8853; (G) &#8853; (L) &#8853; (M) &#8853; (N)
[*](F) &#8853; (G) &#8853; (M) &#8853; (N) &#8853; (O)
[*](G ^ H) &#8853; (G ^ J) &#8853; (G ^ N) &#8853; (G ^ O) &#8853; (G ^ P) &#8853; (H ^ J) &#8853; (H ^ N) &#8853; (H ^ O) &#8853; (H ^ P) &#8853; (J ^ N) &#8853; (J ^ O) &#8853; (J ^ P) &#8853; (N ^ O) &#8853; (N ^ P) &#8853; (O ^ P)
[/LIST]

For those of you who are unfamiliar with the symbols:

[LIST]
[*][_[COLOR=Blue]&#8853; = XOR = A or B but not A and B[/COLOR]_]("http://en.wikipedia.org/wiki/Exclusive_or")
[*][_[COLOR=Blue]^ = AND = both A and B[/COLOR]_]("http://en.wikipedia.org/wiki/Logical_conjunction")
[/LIST]

Given all of this logic you are able to deduce this information:

[LIST]
[*]A
[*]! B
[*]! C
[*]D
[*]E v F
[*]G v H
[*]! I
[*]J
[*]K
[*]! L
[*]! M
[*]! N
[*]! O
[*]! P
[/LIST]

From the array above how would you go about getting the values (without brute-forcing, there are 65536 possibilities).

I have a few ideas, but i know if i follow them they will lead me no-wheres so any thing that you could offer would be greatly appreciated.

Thanks
~Cody Woolaver

---

### Post by CptPicard on 2010-04-14
You may find Prolog interesting -- it does a search for provable van Horn clauses which your clauses are very close to. Look into how Prolog's search is implemented.

Otherwise it needs to be noted that these sorts of problems always flirt with NP-completeness, so brute-forcing is often the only way to go.

---

### Post by Pyro.699 on 2010-04-14
I love how the real problem im trying to solve is an np=p complete problem all on its own and even the sub-problems happen to have the same characteristics xD

My current method of doing the main problem is brute-forcing, and after a few million calculations it gets very very tiresome. Ive even crashed one computer by running out of memory. I have the quick easy methods down pat, now its time to analaize and rewrite my code to improve it :devil:

Thank-you very much for your reply, ill check it out now while i wait for other replies :)

~Cody

---

### Post by Zugzwang on 2010-04-14
You ran out of memory when doing a brute force search? Then you did something wrong as this approach should have a memory consumption that is linear in the number of variables (which is basically almost nothing).

Other than that, you might want to modify the Davis-Puttnam algorithm or the DPLL algorithm for achieving what you want. Another google search term is "XOR-SAT". It also shouldn't be too hard to prove NP-hardness of your problem which justifies using such approaches.

Note that in your previous post, you used the term "np=p complete problem". What it that supposed to mean? Whatever it means, it doesn't look correct.

---

