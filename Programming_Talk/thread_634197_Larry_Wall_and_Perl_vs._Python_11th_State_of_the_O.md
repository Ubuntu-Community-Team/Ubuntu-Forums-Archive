---
title: "Larry Wall and Perl vs. Python? 11th State of the Onion..."
date: 2007-12-07
forum: Programming Talk
---

### Post by ThinkBuntu on 2007-12-07
Larry Wall's 11th State of The Onion, an annual report that deals with the Perl language, community, and other relevant things, was released today. Two paragraphs caught my attention:

[quote="Larry Wall"]
**Python**

After Tcl came Python, which in Guido's mind was inspired positively by ABC, but in the Python community's mind was inspired negatively by Perl. I'm not terribly qualified to talk about Python however. I don't really know much about Python. I only stole its object system for Perl 5. I have since repented.

**Ruby**

I'm much more qualified to talk about Ruby--that's because a great deal of Ruby's syntax is borrowed from Perl, layered over Smalltalk semantics. I've always viewed Ruby as a much closer competitor for Perls ecological niche, not just because of the borrowed ideas, **but because both Perl and Ruby take their functional programming support rather more seriously that Python does.** On the other hand, I think Ruby kind of screwed up on its declaration syntax, among other things.[/quote]

I know there are many Python supporters in this Forum, so I'm curious: What do you think about the statement I bolded in the second paragraph? Strong statements.

---

### Post by pmasiar on 2007-12-07
> **ThinkBuntu said:**
> What do you think about the statement I bolded in the second paragraph? Strong statements.

I am no way functional programming expert, but my understanding is: instead of esoteric functional-like map(), reduce() etc, Python uses easier to understand (IMHO) list comprehension (and drops some of them in Py3.0), and generic functions like all(), any(), some(). Also, lambda is limited (and narrowly escaped the axe for Py3.0).

Focus is not on functional purity, but on readability, as always.  :-)

---

### Post by ThinkBuntu on 2007-12-07
> **pmasiar said:**
> I am no way functional programming expert, but my understanding is: instead of esoteric functional-like map(), reduce() etc, Python uses easier to understand (IMHO) list comprehension (and drops some of them in Py3.0), and generic functions like all(), any(), some(). Also, lambda is limited (and narrowly escaped the axe for Py3.0).

Focus is not on functional purity, but on readability, as always.  :-)
I once read an argument about the relative power of languages, in this case championing Lisp for Macros. Would dropping lambda functions, for example, make Python less powerful?

---

### Post by CptPicard on 2007-12-07
> **ThinkBuntu said:**
> Would dropping lambda functions, for example, make Python less powerful?

Not in the theoretical sense of course, but I must admit I am really partial to languages that do have proper lambdas and closures. I find myself increasingly using them if they are available in a language. Without lambdas you end up hacking together some kind of ad hoc derivations of base classes with an execute() method or something like that (Java-style). It can get pretty ugly.

---

### Post by pmasiar on 2007-12-07
"Zen of Python" says: 
- Practicality beats purity
- Special cases are not special enough to break the rules.

Every feature in a language has mental price, even if you do not use it: 
- you need to learn about it (and ignore it)
- code needs to be maintained
- syntax has to handle it, with possible limits on further expansion.

This was one of the reasons why Python rejected TIMTOWDI of Perl, and has "There should be one obvious way to do it right" rule instead. List comprehension is **much** easier to read and understand, IMHO, with same results.

And Python still does have lambdas - just limited to expression, and not full block.

---

### Post by ThinkBuntu on 2007-12-07
To play devil's advocate, you lose development productivity and cause more mental strain when a developer needs to substitute a dumbed-down version for a missing feature. I can envision no CSS property that I would want banned from CSS for the sake of "mental price" so long as there's a use for it somewhere.

P.S. I'm sure this has been argued a million times over in a million places.

---

### Post by pmasiar on 2007-12-07
Of course, you **lose** some productivity and it **was** argued. :-)

**Some** developers might lose **some** of productivity by working around missing advanced feature, but many more developers gain productivity by not handling that at all (not paying any of the three prices). 

Language design is engineering task: it is about finding delicate compromise while ballancing competing requirements. 

I haven't noticed stampede of developers leaving Python because of limited lambda functionality (I don't care about lambda so far), so I guess it was good compromise.

---

### Post by Wybiral on 2007-12-07
I think Python is great for functional programming. Its lambdas are simple, but effective, and when they wont work closures will. Python also has a great host of functional tools like map/filter/reduce (not to mention it's powerful list comprehension). Googlers actually made a pretty cool functional module called "goopy" that extends them a bit. Very handy stuff. Being able to make objects callable also allows for some neat "functional" tricks that Python can do.

---

