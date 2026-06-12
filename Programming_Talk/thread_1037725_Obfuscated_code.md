---
title: "Obfuscated code"
date: 2009-01-12
forum: Programming Talk
---

### Post by Sockerdrickan on 2009-01-12
post your code! :popcorn:
[php]//gcc guess.c && ./a.out

            i,r,t;main()
       {srand        (time(0))
    ;r=rand()          %9;puts(
    "guess"           " 0-9");do
     {scanf            ("%d",&i)
       ;++t            ;puts(i<
                     r?"higher"
                   :"lower"
                  );}while
                (i-r);
               printf
              ("yes "
              "(%d "
              "trie"

              "s)\n"
              ,t);}
[/php]

---

### Post by u-slayer on 2009-01-12
> **Tux0r said:**
> post your code! :popcorn:
[php]//gcc guess.c && ./a.out

            i,r,t;main()
       {srand        (time(0))
    ;r=rand()          %9;puts(
    "guess"           " 0-9");do
     {scanf            ("%d",&i)
       ;++t            ;puts(i<
                     r?"higher"
                   :"lower"
                  );}while
                (i-r);
               printf
              ("yes "
              "(%d "
              "trie"

              "s)\n"
              ,t);}
[/php]

Haven't bothered to compile it, but from a quick read thru, this code generates a random number 0-8 and asks the user to guess it, it then prompts the user higher or lower as to how to guess again while keeping track of the number of tries.

What confuses me is how you got away with not declaring or initializing i, r, t.

---

### Post by slavik on 2009-01-12
I believe they are int types by default.

---

### Post by Tuna-Fish on 2009-01-12
> **u-slayer said:**
> Haven't bothered to compile it, but from a quick read thru, this code generates a random number 0-8 and asks the user to guess it, it then prompts the user higher or lower as to how to guess again while keeping track of the number of tries.

What confuses me is how you got away with not declaring or initializing i, r, t.

```
i,r,t;main()
```

Right there.

---

### Post by slavik on 2009-01-12
Perl one liner (it is actually one statement).
[php]
print join ", ", map { join " ", @$_ } sort { $a->[1] <=> $b->[1] } map { [split /\s+/] } split /\s*,\s*/, <>;
[/php]

---

### Post by Greyed on 2009-01-12
The bane of writing in Python, obfuscation is hard.  If there was ever a proof of a language being easier to write good code I think that would be it.  Of course if I took the cheap way out with map(), reduce() and lamba() like Slavik did I guess that could be obfuscated.  But with the full power of Perl at his fingertips I think Slavik has to make a real entry which doesn't use any of those.  ;)

---

### Post by slavik on 2009-01-12
> **Greyed said:**
> The bane of writing in Python, obfuscation is hard.  If there was ever a proof of a language being easier to write good code I think that would be it.  Of course if I took the cheap way out with map(), reduce() and lamba() like Slavik did I guess that could be obfuscated.  But with the full power of Perl at his fingertips I think Slavik has to make a real entry which doesn't use any of those.  ;)
Here's a cop out answer for you: in Perl6, for loops also return lists like maps ;)
ie: @arr = map { 1 } 1..100 is similar to @arr = for 1..100 { 1 };

---

### Post by Greyed on 2009-01-12
> **slavik said:**
> Here's a cop out answer for you: in Perl6, for loops also return lists like maps ;)
ie: @arr = map { 1 } 1..100 is similar to @arr = for 1..100 { 1 };

Bah, Perl6, the Duke Nuk'em Forever of languages.

And just so I am not remiss in an entry.

```

,+.+.+.+.+.

```

---

### Post by slavik on 2009-01-12
> **Greyed said:**
> Bah, Perl6, the Duke Nuk'em Forever of languages.

And just so I am not remiss in an entry.

```

,+.+.+.+.+.

```
I already write Perl6 code :)

---

### Post by loell on 2009-01-12
> **slavik said:**
> I already write Perl6 code :)

I envy you, i already know 1/4 of perl 5.x and yet you do perl 6, swoosh just like that. :)

---

### Post by slavik on 2009-01-12
[http://rakudo.org/](http://rakudo.org/)

Back on topic: Anyone else got neat obfuscated code?

---

### Post by nvteighen on 2009-01-12
> **slavik said:**
> [http://rakudo.org/](http://rakudo.org/)

Back on topic: Anyone else got neat obfuscated code?
```

yq28whww; %(8, 8); ?
?? * + ]

```

It's that obfuscated that even I don't know what language it is and what it does :D

---

### Post by slavik on 2009-01-12
> **nvteighen said:**
> ```

yq28whww; %(8, 8); ?
?? * + ]

```

It's that obfuscated that even I don't know what language it is and what it does :D
HAHA, perfect ....

---

