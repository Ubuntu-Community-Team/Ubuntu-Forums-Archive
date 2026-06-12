---
title: "Which brace style do you prefer?"
date: 2008-08-16
forum: Programming Talk
---

### Post by NovaAesa on 2008-08-16
Which bracketing style do you prefer? I'm not talking about what you work or uni makes you do, but rather what **you** prefer to use. Which is the best and why? Is there any advantage of one over the other or is it just personal preference?

Also, people who don't use languages with curly braces please don't vote.




K&R, BSD KNF:
```

<blockstart> {
    <block_contents>
}

```

Allman style:
```

<blockstart>
{
    <block_contents>
}

```

Whitesmiths:
```

<blockstart>
    {
    <block_contents>
    }

```

GNU style:
```

<blockstart>
  {
    <block_contents>
  }

```

Pico style:
```

<blockstart>
{ <block_contents1>
  <black_contents2> }

```

Banner style:
```

<blockstart>  {
  <block_contents>
  }

```

---

### Post by lisati on 2008-08-16
I'm about 50/50 for Whitesmiths & GNU in the rare occasions that I use 'C', it depends on my mood at the time.

---

### Post by LaRoza on 2008-08-16
Allman, although I also like GNU.

---

### Post by NovaAesa on 2008-08-16
Well as for me, I use K&R.

---

### Post by -grubby on 2008-08-16
I don't write much code that warrants brackets.. But in CSS I usually use K&R style

---

### Post by Kadrus on 2008-08-16
GNU,but i like Pico as well.

---

### Post by samjh on 2008-08-16
Ahem: [http://ubuntuforums.org/showthread.php?t=758698](http://ubuntuforums.org/showthread.php?t=758698) ;)

I chose K&R, but will also use Allman.

---

### Post by NovaAesa on 2008-08-16
Woops, I probably should have checked if this kind of thing had been done before :S


EDIT: anyway, my reasoning for K&R is that it is most like Visual Basic. Yes I know, an MS language etc etc, but it was my first :P

K&N greatly resembles this:
```

IF i = 5 THEN
    i = i + 1
END IF

```

---

### Post by bobbocanfly on 2008-08-16
Allman, without a doubt. Everything else looks too messy for me, and when you are drunk at 3 in the morning trying to write C, it definately helps to have clean(ish) code.

---

### Post by nvteighen on 2008-08-16
Allman.

---

### Post by jimi_hendrix on 2008-08-16
i knew that it didnt matter how you placed your brackets but i never knew there were "styles" for it

---

### Post by nvteighen on 2008-08-16
> **jimi_hendrix said:**
> i knew that it didnt matter how you placed your brackets but i never knew there were "styles" for it
It's one of the religious wars in the C universe!

EDIT: See this from Hackles! [http://hackles.org/cgi-bin/archives.pl?request=98](http://hackles.org/cgi-bin/archives.pl?request=98)

---

### Post by NovaAesa on 2008-08-16
It's almost as big as Vi vs Emacs.

---

### Post by grndrush on 2008-08-16
The type that itches the least.

*"See y'all at the debates, bitches."  -- Paris Hilton*

---

### Post by jimi_hendrix on 2008-08-16
well i like allmans because its cleanest and i tear my hair out when i see any of the other styles in a book

---

### Post by tad1073 on 2008-08-16
I don't code very often, but when I do, I prefer to use Allman or GNU.

---

### Post by Torajima on 2008-08-16
Definitely Pico... I started doing this style on my own, didn't know there was a name for it.

---

### Post by LaRoza on 2008-08-16
> **bobbocanfly said:**
> Allman, without a doubt. Everything else looks too messy for me, and when you are drunk at 3 in the morning trying to write C, it definately helps to have clean(ish) code.

+1. The K&R style is way to messy for me.


> **nvteighen said:**
> It's one of the religious wars in the C universe!

EDIT: See this from Hackles! [http://hackles.org/cgi-bin/archives.pl?request=98](http://hackles.org/cgi-bin/archives.pl?request=98)

I love Hackles, especially that cartoon (and the one about editors as well)

> **NovaAesa said:**
> It's almost as big as Vi vs Emacs.

No, bigger. It doesn't matter if other developers are using Emacs or Vi as long as it is readable in other editors (means, no notepad). However, the braces style matters more to others.

---

### Post by pmasiar on 2008-08-16
What about Python-style braces? :-)

Best braces are no braces!

In case someone is wondering, it was just a joke. K&R braces for me, or whatever IDE supports.

---

### Post by LaRoza on 2008-08-16
> **pmasiar said:**
> What about Python-style braces? :-)

Or Lisp.

> 
Best braces are no braces!

True, but since the braces have to be there, there are many ways of dealing with them. Most of the styles try to accommodate the braces and keep it readable. The indenting part is easy (like Python), what to do with the two little characters that hang around isn't.

---

### Post by NovaAesa on 2008-08-16
Here is what python-like braces would be like (if there was such a thing :P)

```

if (booleanCondition) {
    do some stuff }
else {
    do some other stuff }

```

```

while (booleanCondition) {
   do some stuff
   do some more stuff }

```

---

### Post by imdano on 2008-08-16
K&R when I'm writing Java, Allman if I'm doing C/C++.

---

### Post by kostkon on 2008-08-16
K & R, don't like putting the start brace in a new line.

---

### Post by issih on 2008-08-16
I tend to do Allman for just about everything except function and class opening and closing braces where I use K&R, provided there are no initialisation lists to confuse things.

Basically code flow I use Allman, function/object definition K&R, to me it makes sense to differentiate, but then I am odd.

---

### Post by elithrar on 2008-08-16
K&R, though it's a tough choice between that & Allman. Most of my code is Python, though, so it's not something I have to think about that often.

---

### Post by pmasiar on 2008-08-16
> **NovaAesa said:**
> Here is what python-like braces would be like (if there was such a thing :P)

```

if (booleanCondition) {
    do some stuff }
else {
    do some other stuff }

```

```

while (booleanCondition) {
   do some stuff
   do some more stuff }

```

Such braces: Never!

Guido is genius, he avoided such useless holy wars with single brilliant decision (of not having braces at all). That way, it's much easier to agree where not to place them :-)

---

### Post by slavik on 2008-08-16
and then he started another one, how many spaces for indentation and whether to use spaces or tabs. :)

---

### Post by LaRoza on 2008-08-16
> **slavik said:**
> and then he started another one, how many spaces for indentation and whether to use spaces or tabs. :)

That is important in C as well.

---

### Post by NovaAesa on 2008-08-16
Except that in C it doesn't matter if you have a mix (from different people in your team having different preferences). If you try doing that in Python.... uh oh.

---

### Post by British0zzy on 2008-08-16
I use allman for functions, and K&R for everything else (if, else, while, for, structs, etc...)

---

### Post by Darkhack on 2008-08-16
When I first started programming I used K&R.  A friend later showed me Allman style.  I've been using Allman for the past couple years but I can easily switch between it and K&R with no problems.  I think I prefer Allman though, because if I'm searching through code, I can find the opening and ending of the block with no problems.  With K&R, the opening of the block isn't as easy to see on a glance.  I could tell by whitespace (a la Python), but having an actual character there makes it easier it seems.  Also any IDE that's worth my time will highlight code blocks.

As for creating whitespace.  Tabs.  An IDE isn't worth using if it doesn't have an option to change how large a tab is.  That way, other programmers can change the setting and automatically the code is set to their preferred tab size.  Plus all you have to do is hit a single tab key.  With spaces, you can't change the size and you have to hit the space bar multiple times.  I prefer that a tab equals four spaces, but that's just me.

I can understand why people have different opinions on brace style and tab size, but it baffles the mind to think that anyone would prefer spaces to tabs.

---

### Post by Npl on 2008-08-16
Allman for almost everything, K&R for smallish and simple (not many levels) do/while/if blocks

---

### Post by pmasiar on 2008-08-16
> **NovaAesa said:**
> it doesn't matter if you have a mix (from different people in your team having different preferences). If you try doing that in Python.... uh oh.

That's common myth (that different preferences in Python project will clash), but the only problem is mixing tabs and spaces (which will be syntax error in Py3K).  

Certainly different parts of code can be written using different preferences (it might be ugly, like such mixed code is in any language, but certainly not a syntax problem). The only limit is to maintain single preferences inside any block.

Guido officially pronounced (in his blog) [Python: Myths about Indentation](http://www.secnetix.de/olli/Python/block_indentation.hawk) as official FAQ dispelling such myths.

---

### Post by NovaAesa on 2008-08-16
> **Darkhack said:**
> With spaces, you can't change the size and you have to hit the space bar multiple times.
Any good plain text editor (and IDEs) should be able to insert the desired number of spaces when you press the tab key.

[QUOTE=Darkhack]I can understand why people have different opinions on brace style and tab size, but it baffles the mind to think that anyone would prefer spaces to tabs.[/QUOTE]
What happens when you need to keep the maximum width of each line to 80 characters? (this is a standard in many languages). Tab sizes aren't universally defined, so a line might display as 82 characters wide on one setup and 78 wide on another.

[quote=pmasiar]That's common myth (that different preferences in Python project will clash), but the only problem is mixing tabs and spaces (which will be syntax error in Py3K).[/quote]my bad :S

---

### Post by jmillikin on 2008-08-16
Allman, with tabbed indentation. I hate viewing code indented with spaces because they usually have very small indents (2/4 spaces), which I find hard to read.

> **NovaAesa said:**
> Any good plain text editor (and IDEs) should be able to insert the desired number of spaces when you press the tab key.

If the author of the code uses 4 spaces to indent, and you prefer 8 spaces, I've never seen an IDE that lets you view the 4 as 8 without changing the file.

> **NovaAesa said:**
> What happens when you need to keep the maximum width of each line to 80 characters? (this is a standard in many languages). Tab sizes aren't universally defined, so a line might display as 82 characters wide on one setup and 78 wide on another.

If you're so bothered by a line being 2 extra characters long, just shorten your tabs.

---

### Post by LaRoza on 2008-08-16
> **Darkhack said:**
> 
I can understand why people have different opinions on brace style and tab size, but it baffles the mind to think that anyone would prefer spaces to tabs.

Because a space is a space and will look like a space no matter what. With tabs, you risk mixing them (I often press the space bar instead of hitting the tab button (which enters four spaces anyway))

---

### Post by bruce89 on 2008-08-16
I wonder if people know there's a note in K&R which says "we're doing it like this to save paper".

---

### Post by Sinkingships7 on 2008-08-16
K&R. I just find it much easier to read. Don't waste precious white spaces.

---

### Post by happysmileman on 2008-08-16
K & R plus Allman.

Basically classes and functions get Allman and if, else, while, for etc. get K & R

e.g.

```

class myClass
{
    ...;
};

int main(int argc, char* argv[])
{
    if (x == 3) {
        ...;
    } else {
        ...;
    }

    for (int i = 0; i < 6; ++i) {
        ...;
    }

    do {
        ...;
    } while (x == 3);
}
```

---

### Post by yabbadabbadont on 2008-08-16
> **LaRoza said:**
> Because a space is a space and will look like a space no matter what. With tabs, you risk mixing them (I often press the space bar instead of hitting the tab button (which enters four spaces anyway))

That is why you tab to the base indentation level, and then use spaces to adjust from there if needed.  That way, you can change the tab width to anything you want, but stuff will still be aligned correctly.  (assuming that that is important)

---

### Post by lisati on 2008-08-16
> **NovaAesa said:**
> 

What happens when you need to keep the maximum width of each line to 80 characters? (this is a standard in many languages).

Isn't the 80-character limit a hanger-on from the days when punched cards were more common and when the displays on your typical x86-based PC were 80 text-mode characters wide?

---

### Post by pmasiar on 2008-08-16
> **lisati said:**
> Isn't the 80-character limit a hanger-on from the days when punched cards were more common and when the displays on your typical x86-based PC were 80 text-mode characters wide?

No, kernel code still has that restriction.

It helps code readablity immensely if you don't have to scroll sideways to read it - and if you need more than 3-4 indents, your code has bad design and you better redo it. Line length is important CodeSmell test.

---

### Post by yabbadabbadont on 2008-08-16
> **lisati said:**
> Isn't the 80-character limit a hanger-on from the days when punched cards were more common and when the displays on your typical x86-based PC were 80 text-mode characters wide?

72 columns for us old FORTRAN users...  the extra columns at the end were usually used for card sequence numbers.  God help you if you didn't use them and then dropped a deck of cards...

---

### Post by yabbadabbadont on 2008-08-16
> **pmasiar said:**
> No, kernel code still has that restriction.
That is a convention, not a physical restriction of the compiler or editors used.  Unlike with punched cards.  ;)

> **pmasiar said:**
> It helps code readablity immensely if you don't have to scroll sideways to read it - and if you need more than 3-4 indents, your code has bad design and you better redo it. Line length is important CodeSmell test.

You are quite right about that.

---

### Post by pmasiar on 2008-08-16
> **yabbadabbadont said:**
> That is a convention, not a physical restriction of the compiler or editors used. 

Try to tell that to Linus :-)

Of course it is a convention - but without it, email-based review of code patches would be much harder.

---

### Post by Wybiral on 2008-08-16
> **pmasiar said:**
> Try to tell that to Linus :-)

Of course it is a convention - but without it, email-based review of code patches would be much harder.

Also, coding in a terminal-based editor becomes frustrating (since most terminals are 80x20, or something like that).

But mostly, it's good to have standards... And more than 80-chars wide is hard to visually parse for information.

---

### Post by yabbadabbadont on 2008-08-16
> **Wybiral said:**
> Also, coding in a terminal-based editor becomes frustrating (since most terminals are 80x20, or something like that).

But mostly, it's good to have standards... And more than 80-chars wide is hard to visually parse for information.

80x25 was the old DOS standard.  Console ttys and X terminals can be just as big as the connected display will allow.  My text console is 160x64 while my xterm windows are only 158x60.  (different font sizes in each)

---

### Post by indecisive on 2008-08-16
> **samjh said:**
> Ahem: [http://ubuntuforums.org/showthread.php?t=758698](http://ubuntuforums.org/showthread.php?t=758698) ;)

And?  It provides fewer options and the options are very biased.  Perhaps that is why you have different results from your poll...

---

### Post by LaRoza on 2008-08-16
> **bruce89 said:**
> I wonder if people know there's a note in K&R which says "we're doing it like this to save paper".

Probably not. Most people don't read K&R, they just have a copy in their house in a place people will see it.

> **yabbadabbadont said:**
> That is why you tab to the base indentation level, and then use spaces to adjust from there if needed.  That way, you can change the tab width to anything you want, but stuff will still be aligned correctly.  (assuming that that is important)

Are you suggesting mixing tabs and spaces or did I read that wrong? In the big picture, using all tabs, or all spaces doesn't matter, however, the convention for Python is to use four spaces. I find that to be a good size, very readable without wasting space, so I use it. I go for individuality in my personal life, but not when I write code (or other things I want people to understand with minimal effort)

---

