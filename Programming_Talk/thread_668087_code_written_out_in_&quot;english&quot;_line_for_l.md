---
title: "code written out in &quot;english&quot; line for line?"
date: 2008-01-15
forum: Programming Talk
---

### Post by nchase on 2008-01-15
is there anywhere something like this has been posted

---

### Post by hardyn on 2008-01-15
like a programming language that is pretty much english straight up?

python is pretty close, i understand that cobol was too.

---

### Post by Compyx on 2008-01-15
cdecl works for C declarations:

```

cdecl> explain void (*foo)(int **)
declare foo as pointer to function (pointer to pointer to int) returning void

```

But I assume you want a tool that takes a source file in some language and outputs the flow of the source in plain English.

I have never heard of such tools, nor do I see any use for them, translating code to plain English usually goes on in your head when reading code. In my opinion such a tools would be a waste of time since any context of the code will be lost.

For example:
```

i++;

```
can be explained in English as:
"evaluate i and discard the result, then increment i by one" 
or
"add 1 to i"
or
"increment the index in the list of whatever" (context)
or
"increment the count of whatever by one" (context)

Sure you can write such a tools that parses comments in the code to supply context, but that'll severly slow down the development cycle of programs and will probably be even worse than for example all the gibberish you have to add to C sources to keep lint happy.

So basically: if you want to know what a piece of code does, learn the language in which the code is written.

---

### Post by pedro_orange on 2008-01-15
You mean Pseudocode? 
[http://en.wikipedia.org/wiki/Pseudocode](http://en.wikipedia.org/wiki/Pseudocode)

There is no such language sophisticated enough for you to just be able to write out a sentence/paragraph describing what you want to happen and for it to compile/link/run it. 
English is way too flexible on ways you can say things for a start.

I'm not into this Python thingie - all I know is whitespace matters :) - but I hear it's easy.
The only language I've known to be close to English is that of Visual Basic. But then don't quote me on that.

Pick whatever makes sense to you, good luck.

---

### Post by hod139 on 2008-01-15
English is not a [context-free grammar]("http://en.wikipedia.org/wiki/Context-free_grammar").  Most programming languages and compilers are designed using the concepts from the above theory.

---

### Post by Zugzwang on 2008-01-15
> **nchase said:**
> is there anywhere something like this has been posted

As you can see from the posts above, your question is ambiguous:
[LIST]
[*]Are you searching for something that converts existing code in C/C++/Java/whatever into some pseudocode for easier understanding?
[*]Are your searching for some programming language close or even identical to English syntax?
[*]Are your searching for some program which has documentation for every line of code to allow you to learn the basic concepts of programming this way?
[*](something I haven't considered)
[/LIST]

---

### Post by slavik on 2008-01-15
Perl can be very close to english, you can even write poetry with it. :)

---

### Post by LaRoza on 2008-01-15
> **slavik said:**
> Perl can be very close to english, you can even write poetry with it. :)
[php]
not exp log srand xor s qq qx xor
s x x length uc ord and print chr
ord for qw q join use sub tied qx
xor eval xor print qq q q xor int
eval lc q m cos and print chr ord
for qw y abs ne open tied hex exp
ref y m xor scalar srand print qq
q q xor int eval lc qq y sqrt cos
and print chr ord for qw x printf
each return local x y or print qq
s s and eval q s undef or oct xor
time xor ref print chr int ord lc
foreach qw y hex alarm chdir kill
exec return y s gt sin sort split
[/php]

I found that to be poetic, but I doubt that is what the OP is looking for...

---

### Post by pedro_orange on 2008-01-15
```

@P=split//,".URRUU\c8R";@d=split//,"\nrekcah xinU / lreP rehtona tsuJ";sub p{
@p{"r$p","u$p"}=(P,P);pipe"r$p","u$p";++$p;($q*=2)+=$f=!fork;map{$P=$P[$f^ord
($p{$_})&6];$p{$_}=/ ^$P/ix?$P:close$_}keys%p}p;p;p;p;p;map{$p{$_}=~/^[P.]/&&
close$_}%p;wait until$?;map{/^r/&&<$_>}%p;$_=$d[$q];sleep rand(2)if/\S/;print

```

Beautiful.

---

### Post by slavik on 2008-01-15
both are 'just another perl hacker' althought I like the first one because it is completely impossible to tell.

---

### Post by LaRoza on 2008-01-16
> **slavik said:**
> both are 'just another perl hacker' althought I like the first one because it is completely impossible to tell.

I like the first one too, although I know nothing of Perl that would help me understand why it works.

---

