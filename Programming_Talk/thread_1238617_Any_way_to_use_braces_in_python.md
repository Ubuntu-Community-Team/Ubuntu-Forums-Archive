---
title: "Any way to use braces in python?"
date: 2009-08-12
forum: Programming Talk
---

### Post by stair314 on 2009-08-12
Does anybody know if there's an emacs/gedit plugin that lets you write Python code with braces and then maps it to correctly indented Python code without braces? it's annoying to have to re-indent things every time I comment an if statement in or out during development.

---

### Post by SunSpyda on 2009-08-12
Forced indenting is one of Python's finest features - Why would anyone want to get rid of it?

It makes code very clear, and forced good practices.

Why would this need re indenting? Just remove the #s and you're ready to go...
```

a, b = 5, 10
#if a < b:
#    print('Hello, World!')

```

---

### Post by stair314 on 2009-08-12
This is the kind of code that needs reindenting:

```

#if a < b:
     print "Now removing the check on a < b is an O(n) instead of an O(1) operation"

```

There are many other situations where the indentation is a pain, such as if you and your collaborators are using text editors that disagree on how tabs are handled.

Anyway, I am not asking for Python to be changed, just asking if there is some way of having the tabs automatically generated. Note that the kind of plugin I'm talking about would still create the properly indented files-- they would just be hidden from people such as me, who don't share your taste.

---

### Post by NathanB on 2009-08-12
Forced indenting is one of Python's **worst** features!  Use Ruby instead!  hehehe

Inability to be used for automatic code generation is why Python is the most practically useless language ever invented.  Use it only for prototyping, then use something more practical during your production cycle.

---

### Post by .Maleficus. on 2009-08-12
I'm not aware of a plugin like this, but you can learn how to write your own [Gedit plugins here]("http://live.gnome.org/Gedit/PythonPluginHowTo") (in Python, the recommended choice).
> **stair314 said:**
> There are many other situations where the indentation is a pain, such as if you and your collaborators are using text editors that disagree on how tabs are handled.
Python convention is 4 spaces per level.  If you or your collaborators don't agree with that then you are writing poor Python code.

---

### Post by SunSpyda on 2009-08-12
Ahhh, I see now.

.Maleficus beat me to it - Use 4 space indents - it's the convention. 

Usually, when I want to disable a if statement, I do this -
```

a, b = 3, 7
if False: # a < b:
    print('Hello, World!')

```

So, the statement will be disabled, but no indent mayhem. Just remove the "False: #" bit and it works again. Obviously you could do the same technique for enabling if statements to always work...
```

a, b = 7, 3
if True: # a < b:
    print('Hello, World!')

```

EDIT - I found this on a site...[I]
Having said that, you can use keywords to indicate the end of a block (instead of indentation), such as "endif". These are not really Python keywords, but there is a tool that comes with Python which converts code using "end" keywords to correct indentation and removes those keywords. It can be used as a pre-processor to the Python compiler. However, no real Python programmer uses it, of course. [Update] It seems this tool has been removed from recent versions of Python. [/I]

@ NathanB - Ruby would have been good if it didn't suffer the same thing as Perl - inconsistency.

---

### Post by wmcbrine on 2009-08-12
> **stair314 said:**
> This is the kind of code that needs reindenting:

```

#if a < b:
     print "Now removing the check on a < b is an O(n) instead of an O(1) operation"

```Just do this:

```

if True: #a < b:
    blah blah blah

```

> *There are many other situations where the indentation is a pain*No, there aren't (including that one).

---

### Post by Can+~ on 2009-08-12
> **NathanB said:**
> Forced indenting is one of Python's **worst** features!  Use Ruby instead!  hehehe

Inability to be used for automatic code generation is why Python is the most practically useless language ever invented.  Use it only for prototyping, then use something more practical during your production cycle.

Flamebait.

---

### Post by Mirge on 2009-08-12
> **Can+~ said:**
> Flamebait.

Pretty much. This thread was doomed to turn into a completely off-topic thread from the get-go though... so far, so good. It'll happen I'm sure though.

---

### Post by nvteighen on 2009-08-13
> **stair314 said:**
> Does anybody know if there's an emacs/gedit plugin that lets you write Python code with braces and then maps it to correctly indented Python code without braces? it's annoying to have to re-indent things every time I comment an if statement in or out during development.

Python lacks something that it would make it very powerful: a preprocessor. If they implemented a preprocessor (and the nearer to Common Lisp's or Scheme's, the better!), the language would have metaprogramming abilities and all the advantages that means.

> **NathanB said:**
> Forced indenting is one of Python's **worst** features!  Use Ruby instead!  hehehe

Inability to be used for automatic code generation is why Python is the most practically useless language ever invented.  Use it only for prototyping, then use something more practical during your production cycle.

I agree with NathanB. Python's forced indentation is its worst feature, because it is a bit counterintuitive in a linguistic point of view... where natural languages work much more with delimiters and also the majority of programming languages, Python insists in reproduce all syntactic information about the upper-levels in all lower-level "sentences"...

I wrote something about this [here]("http://lambdagrok.wikidot.com/forum/t-167147/change-the-way-we-code#post-529494").

> **wmcbrine said:**
> Just do this:

```

if True: #a < b:
    blah blah blah

```

No, there aren't (including that one).

There are several situations where this may occur... and usually you can't do that trick. The one I encounter at most is when I see I can actually create a new function out of a chunk of code I'm repeating... Then, I'll have to fix the indentation manually... And worse is if I do that to create a new method for a class... as any code in any method in a class will start with 2 indents...

---

### Post by unutbu on 2009-08-13
In emacs, to manually shift blocks of code you first select the region and then type:

```
C-c C->        # shifts region one level of indention to the right
C-c C-<        # shifts region one level of indention to the left
C-u 8 C-c C->  # shifts region 8 spaces (2 levels) to the right
C-u 8 C-c C-<  # shifts region 8 spaces (2 levels) to the left

```
You can also use "Rectangle" commands to 
```
C-x r o      # insert a rectangle of space  (M-x open-rectangle)
C-x r k      # kill a rectangle of space    (M-x kill-rectangle)

```

---

### Post by JordyD on 2009-08-13
> **unutbu said:**
> In emacs, to manually shift blocks of code you first select the region and then type:

```
C-c C->        # shifts region one level of indention to the right
C-c C-<        # shifts region one level of indention to the left
C-u 8 C-c C->  # shifts region 8 spaces (2 levels) to the right
C-u 8 C-c C-<  # shifts region 8 spaces (2 levels) to the left

```
You can also use "Rectangle" commands to 
```
C-x r o      # insert a rectangle of space  (M-x open-rectangle)
C-x r k      # kill a rectangle of space    (M-x kill-rectangle)

```

Vim equivalents (visual mode):
```
> #in command mode prefix with : 
<
8> #in command mode prefix with : and flip the 8 and >
8<
```

You can combine this with navigation commands to do block indenting.

Not sure how to insert rectangles, if even possible.

---

### Post by jpkotta on 2009-09-19
Of course Emacs has that (I have not tried it): [http://www.emacswiki.org/emacs/PyIndent](http://www.emacswiki.org/emacs/PyIndent).  

python-mode.el's py-indent-region will take a correctly indented region and move it to the correct column.  I also like how its TAB indentation works.

---

### Post by unutbu on 2009-09-19
Can you give an example of how py-indent-region is used? I can't seem to get it to do anything.

---

### Post by jpkotta on 2009-09-19
> **unutbu said:**
> Can you give an example of how py-indent-region is used? I can't seem to get it to do anything.

```

    defun foo(blah):
        if blah:
            bar()
            baz()

```

Say you don't care about "blah" anymore.  Make the region as underlined and run py-indent-region.
```

    defun foo(blah):
[U]            bar()
            baz()
[/U]
```

It will not change any indentation inside the region, it only changes the horizontal position of the region.  It doesn't seem to work well if you're already at the top indentation level.

In Emacs23, it should be invoked when you hit TAB and the region is active.  In earlier versions, you might need to advise indent-for-tab-command.

---

### Post by unutbu on 2009-09-19
Ah, now I get it :) Thanks very much!

---

### Post by fiddler616 on 2009-09-19
@nvteighen
I think it's reasonable to lose a second or two cleaning up indentation (and any good text editor will make it a one-button affair) in exchange for much more readable code. Good curly brace code should be indented exactly the same as Python.

And I think it's rare to look at mis-indented code and not see an error--something will look out of place, since it's such a visible feature.

---

### Post by JordyD on 2009-09-19
> **fiddler616 said:**
> And I think it's rare to look at mis-indented code and not see an error--something will look out of place, since it's such a visible feature.

I agree, ggVG= in vim has saved me many times.

---

### Post by nvteighen on 2009-09-20
> **fiddler616 said:**
> @nvteighen
I think it's reasonable to lose a second or two cleaning up indentation (and any good text editor will make it a one-button affair) in exchange for much more readable code. Good curly brace code should be indented exactly the same as Python.

And I think it's rare to look at mis-indented code and not see an error--something will look out of place, since it's such a visible feature.

Yes, but sometimes it produces logical bugs that, depending on the code, may be really difficult to track...

Of course, curly-brace code should be indented, but as it has no relevance in execution, at least the code will still **mean** the same and do the same.

---

### Post by fiddler616 on 2009-09-20
By the way, @OP:
```
>>> from __future__ import braces
Traceback (most recent call last):
    SyntaxError: not a chance (<input>, line 1)
```

---

### Post by Simian Man on 2009-09-20
[QUOTE=SunSpyda]Ahhh, I see now.

.Maleficus beat me to it - Use 4 space indents - it's the convention.[/quote]
But I like to indent 2 spaces why should the language I use change that?

[QUOTE=SunSpyda]
Usually, when I want to disable a if statement, I do this -
```

a, b = 3, 7
if False: # a < b:
    print('Hello, World!')

```

So, the statement will be disabled, but no indent mayhem. Just remove the "False: #" bit and it works again. Obviously you could do the same technique for enabling if statements to always work...
```

a, b = 7, 3
if True: # a < b:
    print('Hello, World!')

```
[/QUOTE]
Do you really think that that is a good solution?  That is an unwieldy hack.

---

### Post by SunSpyda on 2009-09-20
I know - it's dreadful. It's nearly as bad as having to type all those braces in C languages.

Conventions are useful, as code then becomes consistent across coders, making it easier to reuse, read, and maintain. And Python's consistencies are one of its great features.

I personally think it's a elegant way if doing it - the conditional statement remains in the program structure, the original intent is still there, and depending on true/false it's easy to enable/disable. There isn't much hacky about it.

Anyhow, the OP has the solution, so posts about the merits/cons of Python isn't helping.

---

### Post by Reiger on 2009-09-20
> **SunSpyda said:**
> Conventions are useful, as code then becomes consistent across coders, making it easier to reuse, read, and maintain. And Python's consistencies are one of its great features.

But that is *exactly* the point. Python is *not* _automatically_ consistent because it will accept any kind of indentation as long as _that_ indentation itself is consistent. Meaning that there is nothing about Python which *actually* says you _shall_ use 4 spaces per indentation level. That isn't bad per se, but it is exacerbated by the fact that there is no opening/closing sign. Now, if either thing was in place (true indentation consistency, guaranteed by the syntax rules) or opening/closing pairs those subtle bugs mentioned simply would not exist. 

At least the brace languages mandate you _shall_ enclose blocks in braces. Of course they have then their own inconsistencies with if() and else() and such...

---

### Post by fiddler616 on 2009-09-20
> **Reiger said:**
> But that is *exactly* the point. Python is *not* _automatically_ consistent because it will accept any kind of indentation as long as _that_ indentation itself is consistent. Meaning that there is nothing about Python which *actually* says you _shall_ use 4 spaces per indentation level. That isn't bad per se, but it is exacerbated by the fact that there is no opening/closing sign. Now, if either thing was in place (true indentation consistency, guaranteed by the syntax rules) or opening/closing pairs those subtle bugs mentioned simply would not exist. 

At least the brace languages mandate you _shall_ enclose blocks in braces. Of course they have then their own inconsistencies with if() and else() and such...
Having a non-mandated (but generally accepted as four) number of spaces is better, IMHO, than all the chaos that can arise from brace style: [http://en.wikipedia.org/wiki/Indentation_style](http://en.wikipedia.org/wiki/Indentation_style)

---

### Post by Reiger on 2009-09-20
That merely says that there the Python community hasn't had grown large enough for the Big Flame War of One True Indentation Style to occur... yet. :P

Seriously though the One True Brace Style and associated rubbish is as far as the language goes a non-issue. Style has no meaning in e.g. C, a fact commonly exploited in the Obfuscated C contest. In Python, the One True Indentation Style, however... See what I mean and meant?

---

### Post by fiddler616 on 2009-09-20
> **Reiger said:**
> That merely says that there the Python community hasn't had grown large enough for the Big Flame War of One True Indentation Style to occur... yet. :P

Seriously though the One True Brace Style and associated rubbish is as far as the language goes a non-issue. Style has no meaning in e.g. C, a fact commonly exploited in the Obfuscated C contest. In Python, the One True Indentation Style, however... See what I mean and meant?

I think that style is the *point* of Python--if you want non-stylish Python, use PHP, Ruby or Perl.

Don't make me start quoting the Zen of Python...

---

### Post by jpkotta on 2009-09-21
> **Reiger said:**
> Seriously though the One True Brace Style and associated rubbish is as far as the language goes a non-issue. Style has no meaning in e.g. C, a fact commonly exploited in the Obfuscated C contest. In Python, the One True Indentation Style, however... See what I mean and meant?

Style is far from a non-issue.  Programming languages aren't for computers, they're for humans.  Badly styled code is hard to read, just like English with no punctuation, run-on sentences, and no capitals.  Sometimes (rarely) I wish Python had braces or end keywords, but it will never have them.  

Any project of reasonable size in any language will have style conventions.  The maintainers will tell you fix your indentation, use spaces not tabs, etc. and resubmit your patch.  The project should specify the convention, not the language.

---

### Post by slavik on 2009-09-21
enough flamebait for one day

---

