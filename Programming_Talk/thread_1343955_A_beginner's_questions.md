---
title: "A beginner's questions"
date: 2009-12-02
forum: Programming Talk
---

### Post by sp0tz on 2009-12-02
I've got a couple questions about programming. Nothing real important, just stuff that makes code more readable and sharable.

0 - arrays always include a zeroth(?) element, so int whatever[3] will actually have 4 elements. Is it OK to use whatever[5] when you need five elements and ignore the zeroth, or is this considered bad practice? Personally it's more confusing to me to try to remember that whatever[3] has 4 elements, so the third one is... 2, but that may not be the way professional programmers think.

1 - I've always heard "lololol don't use tabs and spaces" but I don't really know what that means. Tabs seem pretty superior when it comes to indenting for a loop or something, so should I code stuff like
```
int(tab)variable(tab)=(tab)9001;
```
Or is the idea that *indentation* should be done with one or the other, but not both?

---

### Post by johnl on 2009-12-02
> 
0 - arrays always include a zeroth(?) element, so int whatever[3] will actually have 4 elements. Is it OK to use whatever[5] when you need five elements and ignore the zeroth, or is this considered bad practice? Personally it's more confusing to me to try to remember that whatever[3] has 4 elements, so the third one is... 2, but that may not be the way professional programmers think.


This depends on the language.  In some languages, arrays start at 1.  However, let's talk about C/C++.
When you say:

```

int myarray[3];

```
You declare an array with three elements:
myarray[0], myarray[1], and myarray[2].

Accessing any elements of the array other than those, for example, reading/writing to myarray[3], is _undefined behavior_. It may work as expected.  It may crash your program.  It may reboot your computer and cause it to burst into flames.  Don't do it.  


> 
1 - I've always heard "lololol don't use tabs and spaces" but I don't really know what that means. Tabs seem pretty superior when it comes to indenting for a loop or something, so should I code stuff like
```
int(tab)variable(tab)=(tab)9001;
```
Or is the idea that *indentation* should be done with one or the other, but not both?

The idea is that indentation should be done with one or the other, but not both.  Most people use spaces for 'internal space' between variables, operators, etc. This makes sharing code with other people cleaner, since their tab-width may be different than yours.

For example:

```

<tab><space><space><space><space>int x;
<tab><tab>x = 3;

```
will line up nicely when tab width is 4, but will look funny when the tab width is anything else.

---

### Post by lisati on 2009-12-02
> **sp0tz said:**
> 
0 - arrays always include a zeroth(?) element, so int whatever[3] will actually have 4 elements. Is it OK to use whatever[5] when you need five elements and ignore the zeroth, or is this considered bad practice? Personally it's more confusing to me to try to remember that whatever[3] has 4 elements, so the third one is... 2, but that may not be the way professional programmers think.

It can depend on the programming language. If you difine something as whatever[4], then some languages will set up the relevant memory as whatever[0] to whatever[3], others will set it up as whatever[1] to whatever[4]. Either way, it is risky to go to whatever[5] (even if the language allows it) because you could accidentally overwirte something completely unrelated to whatever.
> **sp0tz said:**
> 
1 - I've always heard "lololol don't use tabs and spaces" but I don't really know what that means. Tabs seem pretty superior when it comes to indenting for a loop or something, so should I code stuff like
```
int(tab)variable(tab)=(tab)9001;
```
Or is the idea that *indentation* should be done with one or the other, but not both?

It's often safer to use spaces than tabes with your formatting, because different programs interpret tabs as a different number of spaces, which could mess up the appearance of your code. 
Back when I started programming, it was safer to use spaces, because some compilers were sensitive to the number of spaces being in a line of source code - using a tab character would confuse the compiler. The way some of the older languages are (were?) defined includes the way the source code is formatted.
These days, the formatting is more for the benefit of the person reading the code.

Think back to an old-style manual typewriter. Many come equipped with a feature called "tab stops" - these correspond to a specific position on the page, and are good for formatting tables and other such stuff.

---

### Post by Simian Man on 2009-12-02
> **sp0tz said:**
> 0 - arrays always include a zeroth(?) element, so int whatever[3] will actually have 4 elements. Is it OK to use whatever[5] when you need five elements and ignore the zeroth, or is this considered bad practice? Personally it's more confusing to me to try to remember that whatever[3] has 4 elements, so the third one is... 2, but that may not be the way professional programmers think.
You're confused.  The following code:
```
int whatever[3];
```
Declares an array with **3** elements.  Not 4.  Those elements are named whatever[0], whatever[1] and whatever[2].  So when you declare an array, the subscript value is the *total number* but when you use it you count from 0 to (total - 1).

Definitely don't declare your arrays to have 1 extra element and ignore the first one.  That will confuse the hell out of whoever reads your code and will make it even harder to get used to counting from zero as you will inevitably have to if you want to program seriously.  Once you get used to it, it makes more sense than counting from 1.


> **sp0tz said:**
> 1 - I've always heard "lololol don't use tabs and spaces" but I don't really know what that means. Tabs seem pretty superior when it comes to indenting for a loop or something, so should I code stuff like
```
int(tab)variable(tab)=(tab)9001;
```
Or is the idea that *indentation* should be done with one or the other, but not both?
This is mostly just down to preference.  I never use tabs in my code, only spaces.  However when I hit the tab key in vim, it indents 2 spaces so you don't need to indent by hand with the space character to not use tabs.

---

### Post by MindSz on 2009-12-02
> **lisati said:**
> something completely unrelated to whatever.

haha :)

---

### Post by lisati on 2009-12-02
> **MindSz said:**
> haha :)

:) Well spotted. I accidentally illustrated the idea of unintended consequences, and was too lazy to fix it.

---

### Post by Arndt on 2009-12-02
> **sp0tz said:**
> I've got a couple questions about programming. Nothing real important, just stuff that makes code more readable and sharable.


1 - I've always heard "lololol don't use tabs and spaces" but I don't really know what that means. Tabs seem pretty superior when it comes to indenting for a loop or something, so should I code stuff like
```
int(tab)variable(tab)=(tab)9001;
```
Or is the idea that *indentation* should be done with one or the other, but not both?

If you use tabs, only use tab stops every 8 characters. That's the only setting that won't make you lots of enemies.

(What's the "lololol" meant to convey here? Not laughter, surely?)

---

### Post by sp0tz on 2009-12-02
Oh yeah, that's right. whatever[3] has only 3 elements. Yeah, guess I'd better learn to count from 0.

Also I'll continue using nothing but tabs for indentation and sometimes to make variable names/various operations line up for clarity.

Thanks, guys.

---

### Post by grayrainbow on 2009-12-02
The good things about tabs is that people could set them to what they like and code is always indented on persons preferences. That sad I'm evil and all IDEs/editors of mine convert tabs to spaces.

---

### Post by junapp on 2009-12-02
if you are talking about Python there is a little writeup at:
[http://wiki.python.org/moin/HowToEditPythonCode](http://wiki.python.org/moin/HowToEditPythonCode)

---

### Post by dwhitney67 on 2009-12-02
I'm a frequent user of the 'uncrustify' utility.  It takes the poorest formatted code and makes it look as if I wrote it myself.

---

### Post by The Cog on 2009-12-03
I just tried uncrustify. It refuses to do anything without a "config file", but I can't find any documentation as to what should be in that file. I don't have the time to try every possible combination of ascii characters up to maybe 1K long just to see what combinations do something useful. Is it documented anywhere?

---

### Post by johnl on 2009-12-03
I had trouble with this too a while ago; the following worked for me:

```

touch new.cfg && uncrustify -c new.cfg --update-config-with-doc > new.cfg

```

This will write a new config to 'new.cfg' along with documentation about each option.

---

### Post by The Cog on 2009-12-05
Thanks for the tip. 
Good grief, that list of options is huge! I'll have to take some time fiddling with it.

---

### Post by nvteighen on 2009-12-05
> **grayrainbow said:**
> The good things about tabs is that people could set them to what they like and code is always indented on persons preferences. That sad I'm evil and all IDEs/editors of mine convert tabs to spaces.

Except when one uses linebreaking when column 80 is reached... like me... :p

---

### Post by johnl on 2009-12-05
> **nvteighen said:**
> Except when one uses linebreaking when column 80 is reached... like me... :p

Lines longer than 80 characters makes me angry.

---

### Post by dwhitney67 on 2009-12-05
> **johnl said:**
> Lines longer than 80 characters makes me angry.

Then I guess I will refrain from attending the cinema on a Friday night.

---

### Post by Can+~ on 2009-12-05
> **dwhitney67 said:**
> I'm a frequent user of the 'uncrustify' utility.  It takes the poorest formatted code and makes it look as if I wrote it myself.

I use Eclipse's formatter for that (Ctrl+Shift+F), but thanks for that tool.

---

