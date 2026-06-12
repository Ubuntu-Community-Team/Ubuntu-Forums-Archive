---
title: "awk regular expressions: \1"
date: 2014-01-09
forum: Programming Talk
---

### Post by sha1sum on 2014-01-09
Hello guys,

With grep -E (or egrep), you can do something like this:

```
grep -E '(.)(.)\2\1' *target.txt*
```

This matches everything with the pattern **abba**.

However, I found that it doesn't work in awk. If you make an awk command like this:

```
awk '/(.)(.)\2\1/' *target.txt*
```

It will not work. (Using two backslashes ( \\ ) doesn't work either).

Is there a way to do that in awk?

---

### Post by trent.josephsen on 2014-01-09
The search term you're looking for is **backreference**. A quick Google search seems to indicate that awk doesn't support backreferences.

---

### Post by kurum! on 2014-01-09
> **trent.josephsen said:**
> A quick Google search seems to indicate that awk doesn't support backreferences.
wrong

---

### Post by trent.josephsen on 2014-01-09
From the first hit I got on Google, [http://awk.freeshell.org/Backreferences](http://awk.freeshell.org/Backreferences):
> If you need to match a pattern using a regular expression with backreferences, like eg you do in sed or similar things, then well, you can't do that easily with awk.

Saying "wrong" is not constructive. Is the page I linked incorrect? Am I misinterpreting it? For OP's sake, please don't be rude.

---

### Post by steeldriver on 2014-01-09
I may be wrong, but my understanding is that *gawk *natively supports backreferences **only in the replacement string**, and only via the gensub function i.e. something like

```

$ echo 'noon' | awk '{print gensub(/(.)(.)/,"\\2\\1","g")}'
onno

```

whereas the OP is asking about backreferences in the **pattern**

---

### Post by kurum! on 2014-01-10
Proof of concept.

```

# echo 'abba' | awk '{a=$0; b=gensub(/(.)(.)/,"\\2\\1","g"); c=gensub(/(.)(.)/,"\\2\\1","g",b); if (c==a) print "match"}'
ok

```

---

### Post by sha1sum on 2014-01-10
Hello guys. Thank you all for taking the time to answer my question. The conclusion I draw is that awk doesn't support backreferences (apart from the gensub function, which you can use to make a work-around. Although I guess that one gets very laborious if you have more complex cases.). I also came to that conclusion based on what I read in my reference book, but I found it really hard to believe that such a versatile tool as awk doesn't support something as basic as backreferences. I guess that's just the way it is.

Thanks again to all of you.

---

### Post by erind on 2014-01-10
> **sha1sum said:**
> Hello guys. Thank you all for taking the time to answer my question. The conclusion I draw is that awk doesn't support backreferences (apart from the gensub function, which you can use to make a work-around. Although I guess that one gets very laborious if you have more complex cases.). I also came to that conclusion based on what I read in my reference book, *but I found it really hard to believe that such a versatile tool as awk doesn't support something as basic as backreferences*. I guess that's just the way it is.

Thanks again to all of you.

It does not support backreferences because generally awk distributions use a different (simpler) regex engine (DFA), whereas perl, sed, etc, use the NFA engine. Now in **gawk**'s (**Gnu awk**) case it uses a hybrid regex engine DFA+NFA and that's why it supports backreferences and only in the gensub function. There are quite a few awk distributions out there (old awk, nawk, tawk, ...) that as far as I know use only the DFA regex engine. Quoting from:

[www.softec.lu/site/RegularExpressions/RegularExpressionEngines]("http://www.softec.lu/site/RegularExpressions/RegularExpressionEngines")
> 
Regex implementation are based on two main kind of engine: DFA and NFA. Perl, Java, .NET languages, PHP, Python, Ruby,... and most tools implement a Traditional NFA engines. Some less widespread tools like mawk use a POSIX NFA engine which is a variation of the previous one. Awk, egrep, flex, lex, MySQL,... that mostly needs to verify efficiently the success of an overall match implement the more efficient DFA engine. Finally some tools like GNU awk, GNU egrep and Tcl used the best of both world with an hybrid NFA/DFA engine.
--
> Although I guess that one gets very laborious if you have more complex cases.
If you want to explore the full potential of regexes then you really need to look elsewhere - *perl, python, ruby,* etc ... and there's no need to learn the whole language to use their complex regexes, just the right syntax (I'm thinking perl). It'll make life much easier. 

Finally, one of the best books that I've found on the subject of regexes is: *Mastering Regular Expressions *by Jeffrey Friedl.

---

### Post by sha1sum on 2014-01-10
Thanks for that excellent piece of additional information.

> **erind said:**
> If you want to explore the full potential of regexes then you really need to look elsewhere - *perl, python, ruby,* etc ... and there's no need to learn the whole language to use their complex regexes, just the right syntax (I'm thinking perl). It'll make life much easier. I think you are right. The last two weeks I've been studying awk to learn all of it's functions. Partly for the fun and kicks of completely mastering this tool, and partly operating under the philosophy that it's better to know one programming language completely, than to know a little bit of many languages. However it appears like I'm running into awk's limitations, meaning that I'm going to have to start studying something else sooner or later. (I already have a book on Perl and I'm likely going to start reading it one of these days).

> **erind said:**
> 
Finally, one of the best books that I've found on the subject of regexes is: *Mastering Regular Expressions *by Jeffrey Friedl.
I'll be on the lookout for that book. Thanks for steering me in that direction.

---

### Post by ofnuts on 2014-01-10
> **erind said:**
> 
Finally, one of the best books that I've found on the subject of regexes is: *Mastering Regular Expressions *by Jeffrey Friedl.

I disagree. It is not "one of the best". It is "the best". Period. Instant regex guru status guaranteed :)

---

### Post by erind on 2014-01-10
> **sha1sum said:**
> Thanks for that excellent piece of additional information.

I think you are right. The last two weeks I've been studying awk to learn all of it's functions. Partly for the fun and kicks of completely mastering this tool, and partly operating under the philosophy that it's better to know one programming language completely, than to know a little bit of many languages. 
[...]

There's nothing wrong with your approach, I started with awk and use it daily. It's simple, it comes in handy in many situations, especially when working in terminal with quick one liners, or there might be times when working on a (small or old) system that has a limited set of commands, where awk & sed are almost guaranteed to be there.

However you'll hit their limitations down the line. So instead of wasting hours to make an awk script work (been there, done that), simply use the right tool for the job and be done with it. I'd just consider awk as a stepping stone towards higher languages, and it'll definitely help learning these languages faster. 

> **ofnuts said:**
> 
I disagree. It is not "one of the best". It is "the best". Period. Instant regex guru status guaranteed :smile:

Absolutely, agree 100% !! :)

---

### Post by kurum! on 2014-01-10
regex is not the only way to solve the problem. regex are just string manipulation. awk is good enough to solve most common string manipulation without regex.
regex is just a convenience. If you can't have it, then do it with functions. substr(), splits(), index(), going through character by character looking for stuff etc.

---

### Post by Vaphell on 2014-01-10
OP, remember:
>     Some people, when confronted with a problem, think "I know, I'll use regular expressions." Now they have two problems.

    -- Jamie Zawinski, 1997

but amusingly enough
>     Whenever faced with a problem, some people say `Lets use AWK.'
    Now, they have two problems.

    -- D. Tilbrook, 1988

;-)

[http://www.codinghorror.com/blog/2008/06/regular-expressions-now-you-have-two-problems.html](http://www.codinghorror.com/blog/2008/06/regular-expressions-now-you-have-two-problems.html)
[http://regex.info/blog/2006-09-15/247](http://regex.info/blog/2006-09-15/247)
[http://codemines.blogspot.com/2006/08/now-they-have-two-problems.html](http://codemines.blogspot.com/2006/08/now-they-have-two-problems.html)

---

### Post by ofnuts on 2014-01-11
> **kurum! said:**
> regex is not the only way to solve the problem. regex are just string manipulation. awk is good enough to solve most common string manipulation without regex.
regex is just a convenience. If you can't have it, then do it with functions. substr(), splits(), index(), going through character by character looking for stuff etc.
[LIST]
[*]C is a convenience, you could do it in assembler
[*]Assembler is a convenience, you could do it in machine code
[*]Machine code is a convenience, you could do it with an FPLA
[*]FPLA is a convenience, you could do it with discrete electronics
[/LIST]
 
I work with people that don't know how to use regexes...  I see piles of substr/index/lastindex that can be replaced by one rather simple regex (not even a complex one). This code is hard to to figure out, hard to test...

---

### Post by kurum! on 2014-01-11
> **ofnuts said:**
> 
[LIST]
[*]C is a convenience, you could do it in assembler
[*]Assembler is a convenience, you could do it in machine code
[*]Machine code is a convenience, you could do it with an FPLA
[*]FPLA is a convenience, you could do it with discrete electronic
[/LIST]

what do you want to prove? you are not even realistic.
 
> 
 This code is hard to to figure out, hard to test...
So is a whole bunch of unreadable symbols .

---

### Post by vasa1 on 2014-01-11
> **kurum! said:**
> what do you want to prove? you are not even realistic.
...
Chill! We're all on the same side :)

---

