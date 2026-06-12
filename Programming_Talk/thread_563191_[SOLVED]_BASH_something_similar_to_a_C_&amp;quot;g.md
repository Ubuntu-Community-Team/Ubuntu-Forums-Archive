---
title: "[SOLVED] BASH: something similar to a C &amp;quot;goto&amp;quot; command?"
date: 2007-09-29
forum: Programming Talk
---

### Post by ryanVickers on 2007-09-29
I'm looking for something that does the same thing as "goto" in C(++) for BASH.  I know it's primitive, but... :p

---

### Post by ryanVickers on 2007-09-29
I know theres nothing that comes with BASH, but if there's an add-on program in the repositories, or anything! [-o<

---

### Post by Ramses de Norre on 2007-09-29
Using goto statements is considered bad practice and goto isn't being implemented in modern languages anymore (except some). You should use the more advanced control structures (while, if, for, case, ...).

---

### Post by 1337455 10534 on 2007-09-29
Unless you gotsta use bash, I suggest using the os mod in Python and using while loops :lolflag:. Worked for me!
- Hey, thankx a lot for all the help with my gnome/terminal thread!

---

### Post by ryanVickers on 2007-09-29
I'll try, but it won't be pretty! :p

In this case, a goto would be really useful, and quite harmless, but I can see why *they* would want to discourage use of them :p

---

### Post by 1337455 10534 on 2007-09-29
Are you trying to use it for the delete useless files script? Yes, then, a goto would be benign.
Are there no loop funcs in BASH? weird...

---

### Post by ryanVickers on 2007-09-29
> **1337455 10534 said:**
> Are you trying to use it for the delete useless files script? Yes, then, a goto would be benign.
Are there no loop funcs in BASH? weird...

no, no no!  that's long done and working :p

there are loops in bash, but in this particular case, it's very complicated and would be a pin to use them :)

---

### Post by ryanVickers on 2007-09-29
ok, how do you check if a file does *not* exist :p; I need the opposite of this :):
if [ -e $where ]
then
blah blah blah
....

---

### Post by walkerk on 2007-09-29
perhaps (i haven't tested this)
```
if [ ! -e $where ]; then 
echo "Not there guy!"
fi
```


[look]("http://www.gentoo.org/doc/en/articles/bash-by-example-p3.xml")

---

### Post by ryanVickers on 2007-09-29
seems to work, but hold on everyone, I'll be a while before I get this working...

---

### Post by ryanVickers on 2007-09-29
can while loops have else? :)

---

### Post by Wybiral on 2007-09-29
> **ryanVickers said:**
> can while loops have else? :)

Everything after the while loop?

---

### Post by ryanVickers on 2007-09-29
right! :p

oh, dear, I'm getting tired.  Well, I managed to *finish* it at least - just one more feature...

---

### Post by HermanAB on 2007-09-29
Hmm, you should consider making it a Perl script instead.  Perl is easier to code than Bash and much more powerful. (and no, Perl doesn't *have* to look like line noise).

---

### Post by ryanVickers on 2007-09-29
ok, thanks for all the help everyone, and sorry to anyone else reading this who needs a goto command :p

You can all check out the new version of "mkrar", number 1.7!  It is now even more safe and adapting!; it will detect if a file/folder you want to rchive/go into exists or not, and if it doesn't, it will tell you and let you try again to type a correct path in!  Also, it already assumed the home directory for the path to the file, and now it will automatically assume the folder/file to archive to be the first item in the folder!!!  check it out!

---

### Post by 1337455 10534 on 2007-09-29
I would declare this thread as solved...
Ryan, if you'd do the honors?...

---

### Post by ryanVickers on 2007-09-29
> **HermanAB said:**
> Hmm, you should consider making it a Perl script instead.  Perl is easier to code than Bash and much more powerful. (and no, Perl doesn't *have* to look like line noise).



Yeah, I've heard good things about it, but I don't really want to learn *another* language! :p  I already know actionscript 1 and 2, a tiny bit of C, (I can read better than wrote :)), and now I'm learning bash, but I think that would just be too much! :p  Unless it's **really** easy...

---

### Post by ryanVickers on 2007-09-29
> **1337455 10534 said:**
> I would declare this thread as solved...
Ryan, if you'd do the honors?...

yes, indubitably! :)

---

### Post by ghostdog74 on 2007-09-29
> **ryanVickers said:**
> I'm looking for something that does the same thing as "goto" in C(++) for BASH.  I know it's primitive, but... :p
comes with csh though.

---

### Post by ryanVickers on 2007-09-29
Does that include all the same features as bash? (for other users - I"m done here :p)

---

### Post by ghostdog74 on 2007-09-29
> **ryanVickers said:**
> Does that include all the same features as bash? (for other users - I"m done here :p)
I randomly picked a site [here]("http://elqui.dcsc.utfsm.cl/util/unix/UnixIntro/Scripts.html"). you can take a look at how gotos are done in csh. you can also read [this]("http://www.tac.nyc.ny.us/mirrors/tcsh-book/csh-whynot"). by the way, i am just giving information and not advocating the use of csh just because it has goto.

---

### Post by engla on 2007-09-30
read the man page for 'test'; strangely, test and [ are synonyms.

Can't you use functions instead of a goto?

---

### Post by mssever on 2007-09-30
> **HermanAB said:**
> Hmm, you should consider making it a Perl script instead.  Perl is easier to code than Bash and much more powerful. (and no, Perl doesn't *have* to look like line noise).
Ruby is a more modern language that includes many of Perl's features. I used to do a lot of bash scripting. However, since I've learned Ruby, I've found that I much prefer Ruby over bash. Yes, there's some learning involved, but you don't have to deal with bash's syntax and quoting oddities. And, in ruby you can run any shell command any time you want, if you find that easier for some particular task. Plus, Ruby is much more  readable than even well-written Perl code.
> **ghostdog74 said:**
> comes with csh though.
[http://www.faqs.org/faqs/unix-faq/shell/csh-whynot/](http://www.faqs.org/faqs/unix-faq/shell/csh-whynot/)

---

### Post by ghostdog74 on 2007-09-30
> **mssever said:**
> 
[http://www.faqs.org/faqs/unix-faq/shell/csh-whynot/](http://www.faqs.org/faqs/unix-faq/shell/csh-whynot/).
read the second link of of my post.

---

