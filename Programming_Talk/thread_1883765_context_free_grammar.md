---
title: "context free grammar"
date: 2011-11-19
forum: Programming Talk
---

### Post by grieves on 2011-11-19
Hello there :), just wondering if anyone could help me understand context free grammar more. I'm trying to make a grammar for this language:

{a^n b^y a^m a^x*n+m |m,n>=0, x = 2 y =3} 

but failing hard, I've only read the basics from a book and stuck with this exercise. 

I've only done this but Im sure its completely wrong 

S-> aSa | bbb | aA | E
A-> aA | bbb | E
B-> aB | E
C-> aC | E

Hope someone could help and thanks in advance.

---

### Post by schauerlich on 2011-11-20
> **grieves said:**
> Hello there :), just wondering if anyone could help me understand context free grammar more. I'm trying to make a grammar for this language:

{a^n b^y a^m a^x*n+m |m,n>0, x = 2 y =3} 

but failing hard, I've only read the basics from a book and stuck with this exercise. 

I've only done this but Im sure its completely wrong 

S-> aSa | bbb | aA | E
A-> aA | bbb | E
B-> aB | E
C-> aC | E

Hope someone could help and thanks in advance.

The empty string is not in your language. it will always contain at least 'abbbaaaa'. Your B and C rules are also inaccessible from the start symbol. Also notice that since a^m and a^x*n+m are right next to each other, it can be rewritten as a^2n a^2m. This is an equivalent language:

```
{a^n bbb a^2n a^2m | m, n > 0}
```

I believe that will make it easier to see the rules you'll need.

---

### Post by nvteighen on 2011-11-20
As a linguist, I certify that notation is awful.

---

### Post by grieves on 2011-11-20
@schauerlich oh sorry, I forgot to put m,n>=0 instead of m,n>0. Editing it now. Thanks for your reply I'll try it again.

@nvteighen I know :lol:, I just literally  started reading the topic :oops:

---

### Post by grieves on 2011-11-20
Ok I tried making the grammar again with schauerlich's language and added an = to m,n>0:

{a^n bbb a^2n a^2m | m, n >= 0}

S-> aSaaaa | bbb | aA | E
A-> aA | bbb | aaB | E
B-> aaB | aaC | E
C-> aaC | E

Is this right? Any suggestions?

---

### Post by schauerlich on 2011-11-20
> **grieves said:**
> Ok I tried making the grammar again with schauerlich's language and added an = to m,n>0:

{a^n bbb a^2n a^2m | m, n >= 0}

S-> aSaaaa | bbb | aA | E
A-> aA | bbb | aaB | E
B-> aaB | aaC | E
C-> aaC | E

Is this right? Any suggestions?

No.

Keep in mind that every time you add an a on the left side of the 3 b's, you must add two on the right. Then you have the option of any even number of a's on the far right. The empty string still isn't in your language.

---

### Post by grieves on 2011-11-20
Ok from all the info, I came up with this :confused:

S-> aSaa | bbbA 
A-> aaA

---

### Post by Barrucadu on 2011-11-20
That will never finish expanding, as every nonterminal produces a nonterminal.

---

### Post by grieves on 2011-11-20
> **Barrucadu said:**
> That will never finish expanding, as every nonterminal produces a nonterminal.

So does that mean I need to include null?

---

### Post by schauerlich on 2011-11-20
> **grieves said:**
> So does that mean I need to include null?

The A rule will also include the empty string.

---

### Post by grieves on 2011-11-20
So is this correct?

S-> aSaa | bbbA 
A-> aaA | E

---

### Post by schauerlich on 2011-11-20
> **grieves said:**
> So is this correct?

S-> aSaa | bbbA 
A-> aaA | E

Play around with it. See what string it produces, and see if those are in your language. Try to take different paths through the rules and see if you end up with anything weird.

---

### Post by Barrucadu on 2011-11-20
I haven't confirmed it, but this looks ok to me:

S -> N | bbbM
N -> aNaaM | bbb
M -> aaA | E

Also, I don't think your last attempt is right - the a^2m is coming before the a^2n in that grammar, I think.

---

### Post by schauerlich on 2011-11-21
> **Barrucadu said:**
> Also, I don't think your last attempt is right - the a^2m is coming before the a^2n in that grammar, I think.

It shouldn't matter, they're all a's anyhow and there's nothing between them.

---

### Post by grieves on 2011-11-21
Thanks for helping me guys I'll be doing some more reading and exercises hopefully I'll pass my exam :) Thanks again.

---

