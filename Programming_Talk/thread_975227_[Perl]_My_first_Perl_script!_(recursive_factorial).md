---
title: "[Perl] My first Perl script! (recursive factorial)"
date: 2008-11-08
forum: Programming Talk
---

### Post by nvteighen on 2008-11-08
Hi, here's my first Perl script. Nothing special:

```
[color=#408080]*#!/usr/bin/env perl*[/color]

[color=#008000]**use**[/color] strict;
[color=#008000]**use**[/color] warnings;

[color=#008000]**sub **[/color][color=#0000FF]fact[/color]
{
    [color=#408080]*# Recursive factorial function*[/color]

    [color=#008000]**my**[/color] [color=#19177C]$arg[/color] [color=#666666]=[/color] [color=#008000]shift[/color];

    [color=#008000]**if**[/color] ([color=#19177C]$arg[/color] [color=#666666]==[/color] [color=#666666]1[/color])
    {
        [color=#008000]**return**[/color] [color=#666666]1[/color];
    }
    
    [color=#008000]**my**[/color] [color=#19177C]$var[/color] [color=#666666]=[/color] [color=#19177C]$arg[/color] [color=#666666]*[/color] fact([color=#19177C]$arg[/color] [color=#666666]-[/color] [color=#666666]1[/color]);
    
    [color=#008000]**return**[/color] [color=#19177C]$var[/color];
}

[color=#408080]*# Dumb interface*[/color]
[color=#008000]**print**[/color] [color=#BA2121]"Factorial of: "[/color],;
[color=#008000]**my**[/color] [color=#19177C]$in[/color] [color=#666666]=[/color] [color=#666666]<[/color][color=#008000]STDIN[/color][color=#666666]>[/color];
[color=#008000]**print**[/color] fact([color=#19177C]$in[/color]);

```

Some questions:
1. Is that Perl-ish code? No, please don't point me to Haikus and Obfuscated Perl code... I just want to know whether I'm following good practices or not.

2. Why if I write **print fact(<STDIN>)** it waits for EOF to continue and not when I write the code above?

3. I'm using the Perldocs to learn and consider them really good to learn having programming experience... But, just in case, if you have a suggestion, please tell me.

4. I really don't understand why people believe Perl is difficult... :p

---

### Post by vishzilla on 2008-11-08
Thats a good code. I too am learning Perl I am enjoying every moment of it.

---

### Post by jimi_hendrix on 2008-11-08
> 

3. I'm using the Perldocs to learn and consider them really good to learn having programming experience... But, just in case, if you have a suggestion, please tell me.

  laroza's wiki links to a good online book

---

### Post by vishzilla on 2008-11-08
> **jimi_hendrix said:**
> laroza's wiki links to a good online book

oh yes.. laroza's links are useful.

---

### Post by fredscripts on 2008-11-08
> **nvteighen said:**
> Hi, here's my first Perl script. Nothing special:

```
[color=#408080]*#!/usr/bin/env perl*[/color]

[color=#008000]**use**[/color] strict;
[color=#008000]**use**[/color] warnings;

[color=#008000]**sub **[/color][color=#0000FF]fact[/color]
{
    [color=#408080]*# Recursive factorial function*[/color]

    [color=#008000]**my**[/color] [color=#19177C]$arg[/color] [color=#666666]=[/color] [color=#008000]shift[/color];

    [color=#008000]**if**[/color] ([color=#19177C]$arg[/color] [color=#666666]==[/color] [color=#666666]1[/color])
    {
        [color=#008000]**return**[/color] [color=#666666]1[/color];
    }
    
    [color=#008000]**my**[/color] [color=#19177C]$var[/color] [color=#666666]=[/color] [color=#19177C]$arg[/color] [color=#666666]*[/color] fact([color=#19177C]$arg[/color] [color=#666666]-[/color] [color=#666666]1[/color]);
    
    [color=#008000]**return**[/color] [color=#19177C]$var[/color];
}

[color=#408080]*# Dumb interface*[/color]
[color=#008000]**print**[/color] [color=#BA2121]"Factorial of: "[/color],;
[color=#008000]**my**[/color] [color=#19177C]$in[/color] [color=#666666]=[/color] [color=#666666]<[/color][color=#008000]STDIN[/color][color=#666666]>[/color];
[color=#008000]**print**[/color] fact([color=#19177C]$in[/color]);

```

Some questions:
1. Is that Perl-ish code? No, please don't point me to Haikus and Obfuscated Perl code... I just want to know whether I'm following good practices or not.

2. Why if I write **print fact(<STDIN>)** it waits for EOF to continue and not when I write the code above?

3. I'm using the Perldocs to learn and consider them really good to learn having programming experience... But, just in case, if you have a suggestion, please tell me.

4. I really don't understand why people believe Perl is difficult... :p

You should chomp the input:

```
chomp(my $in = <STDIN>);
```

Also, I think the curly braces like

```
sub foo {
       ...
}
```

Are more perlish.

Finally, as a personal opinion, its cooler using:

```
my $arg = shift;

return $arg == 1? 1: $arg*fact($arg-1);
```

Haven't tested it but it should work.

---

### Post by ZuLuuuuuu on 2008-11-08
- The comma after "Factorial of: " is unnecessary, I think?
 - Beware that there is a new line after the input number, but it doesn't effect the program in this case.
 - You know there is no need for the "return $var;" the last expression calculated is automatically returned but writing a return explicitly is a good programming habit if you ask me.

It would be unfair to Python or Ruby if we would call Perl as easy to learn as Python or Ruby :)  It is of course not "unlearnable" but quite hard with it's exceptions and interesting features compared to other languages. But it is surprisingly fun :)

---

### Post by nvteighen on 2008-11-08
> **fredscripts said:**
> 
Finally, as a personal opinion, its cooler using:

```
my $arg = shift;

return $arg == 1? 1: $arg*fact($arg-1);
```

Haven't tested it but it should work.

Oh no... it looks almost like a Perl-oneliner...

> **ZuLuuuuuu said:**
> - The comma after "Factorial of: " is unnecessary, I think?

Yes. Unnecessary.

> 
 - Beware that there is a new line after the input number, but it doesn't effect the program in this case.


So, Perl behaives like C in this case, placing '\n' when entering stuff from keyboard. Just that in C you have to avoid it by remembering its array index :p

> 
 - You know there is no need for the "return $var;" the last expression calculated is automatically returned but writing a return explicitly is a good programming habit if you ask me.


Didn't know that... but I really don't like having implicit return values.

> It would be unfair to Python or Ruby if we would call Perl as easy to learn as Python or Ruby :)  It is of course not "unlearnable" but quite hard with it's exceptions and interesting features compared to other languages. But it is surprisingly fun :)

It's a suprisingly natural language. I'm not saying that's easy as Python (I don't know Ruby...), but its quite logical to me from a morphological point of view... It doesn't rely much on syntax, but in form and semantics; it's quite interesting.

Ok, here, with input sanitizing:
```
[color=#408080]*#!/usr/bin/env perl*[/color]

[color=#008000]**use**[/color] strict;
[color=#008000]**use**[/color] warnings;

[color=#008000]**sub **[/color][color=#0000FF]fact[/color]
{
    [color=#408080]*# Recursive factorial function*[/color]

    [color=#008000]**my**[/color] [color=#19177C]$arg[/color] [color=#666666]=[/color] [color=#008000]shift[/color];

    [color=#008000]**return**[/color] [color=#19177C]$arg[/color] [color=#666666]==[/color] [color=#666666]1[/color] ? [color=#666666]1[/color] : [color=#19177C]$arg[/color] [color=#666666]*[/color] fact([color=#19177C]$arg[/color] [color=#666666]-[/color] [color=#666666]1[/color]);
}

[color=#408080]*# Dumb interface*[/color]
[color=#008000]**print**[/color] [color=#BA2121]"Factorial of: "[/color];
[color=#008000]**my**[/color] [color=#19177C]$in[/color] [color=#666666]=[/color] [color=#666666]<[/color][color=#008000]STDIN[/color][color=#666666]>[/color];
[color=#008000]chomp[/color]([color=#19177C]$in[/color]);

[color=#008000]die[/color] [color=#19177C]$in[/color], [color=#BA2121]" is not a valid number!"[/color] [color=#008000]**if**[/color] ([color=#666666]![/color]([color=#19177C]$in[/color] [color=#666666]=~[/color][color=#BB6688] /^\d+$/[/color]));

[color=#008000]**print**[/color] fact([color=#19177C]$in[/color]);

```

---

### Post by slavik on 2008-11-08
umm, what about factorial of zero? (which is 1 by definition). Also, I suggest 'use bignum;' (to enable transparent bignum) and 'use integer;' (to force integer arithmetic)

as for the implicit return of the last calculation and the ?: shortcut, that comes from C.

And why use regex to validate input? You can send a string in and it would still work (a string in integer context is 0), but if you wanted to validate it, here's a simpler way:

if ($str eq int($str))

---

### Post by unutbu on 2008-11-08
nvteighten, I think your question about <STDIN> points out an interesting difference between Perl and Python. 

In Perl, syntactic expressions like <STDIN> are not objects (like in Python). <STDIN> is a function call. <...> is the function, STDIN is a filehandle. What it returns depends on context. For example,

```

@list=<STDIN>
$list=<STDIN>
```

are both allowed. The value <STDIN> returns depends on the context. **This dependency on context breaks the object paradigm.** Is <STDIN> a list? or is it a scalar? No one knows until it appears in context. (This is most unlike Python, but it is rather like English, where the meaning of a word depends on how it is used in the sentence.) The magic behavior can make Perl convenient, but it is not conceptually beautiful nor simple.

When you write func(<STDIN>), <STDIN> returns a list. The list elements are separated by $/ which by default is set to "\n". The list ends when an EOF is encountered. 

You have to tell <STDIN> that you want a scalar for it to return a scalar.
This is why $in=<STDIN> works.

If you wish to eliminate $in, you could do this:
```

print fact($_=<STDIN>),"\n";

```

---

### Post by nvteighen on 2008-11-08
Addressing 0! = 1 (thanks, slavik):

EDIT: Fixed some stuff. No more regexp needed.

```
[color=#408080]*#!/usr/bin/env perl*[/color]

[color=#008000]**use**[/color] strict;
[color=#008000]**use**[/color] bignum;

[color=#008000]**sub **[/color][color=#0000FF]fact[/color]
{
    [color=#408080]*# Recursive factorial function*[/color]

    [color=#008000]**my**[/color] [color=#19177C]$arg[/color] [color=#666666]=[/color] [color=#008000]shift[/color];

    [color=#008000]**return**[/color] (([color=#19177C]$arg[/color] [color=#666666]==[/color] [color=#666666]1[/color]) [color=#666666]||[/color] ([color=#19177C]$arg[/color] [color=#666666]==[/color] [color=#666666]0[/color])) ? [color=#666666]1[/color] : [color=#19177C]$arg[/color] [color=#666666]*[/color] fact([color=#19177C]$arg[/color] [color=#666666]-[/color] [color=#666666]1[/color]);
}

[color=#408080]*# Dumb interface*[/color]
[color=#008000]**print**[/color] [color=#BA2121]'Factorial of: '[/color];
[color=#008000]**my**[/color] [color=#19177C]$in[/color] [color=#666666]=[/color] [color=#666666]<[/color][color=#008000]STDIN[/color][color=#666666]>[/color];
[color=#008000]chomp[/color]([color=#19177C]$in[/color]);

[color=#008000]die[/color] [color=#BA2121]"$in is not a valid number!"[/color] [color=#008000]**if**[/color] ([color=#19177C]$in[/color] [color=#AA22FF]**ne**[/color] [color=#008000]int[/color]([color=#19177C]$in[/color]));

[color=#008000]**print**[/color] fact([color=#19177C]$in[/color]), [color=#BA2121]"\n"[/color];

```

---

