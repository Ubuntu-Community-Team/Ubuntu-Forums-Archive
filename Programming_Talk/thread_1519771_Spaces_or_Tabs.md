---
title: "Spaces or Tabs?"
date: 2010-06-28
forum: Programming Talk
---

### Post by Penguin Guy on 2010-06-28
Do you prefer to use spaces, or tabs to indent your code?

---

### Post by trent.josephsen on 2010-06-28
I used to set tabstops to 4 spaces and always use tabs.  Then I eschewed tabs altogether and used spaces for a while (my Python stage).  Nowadays I have 8 space tabs and let Vim indent my lines using a mixture of tabs and spaces.  It works.

---

### Post by GregBrannon on 2010-06-28
The behavior of spaces is more predictable as the code is viewed in various editors, though tabs require fewer key strokes and less thought to properly format the code to one's taste and style guides.  If one does use tabs while coding, using the editor's option to convert the tabs to spaces when saving restores the predictable behavior of spaces.

---

### Post by StephenF on 2010-06-28
[IMG]http://img248.imageshack.us/img248/8904/tabsspacesboth.png[/IMG]

---

### Post by aysiu on 2010-06-28
I voted *other* since I don't code.

---

### Post by -grubby on 2010-06-28
> **GregBrannon said:**
> though tabs require fewer key strokes

If you're using a decent editor, you can set tab to insert however many spaces you want.

I voted spaces.

---

### Post by wmcbrine on 2010-06-28
> **StephenF said:**
> [IMG]http://img248.imageshack.us/img248/8904/tabsspacesboth.png[/IMG]I'm with those guys. I'm a reformed space-and-tab mixer myself. Bad, bad, bad. Spaces only now. PEP 8 forever, even in my C code.

---

### Post by Simian Man on 2010-06-28
I indent with 2 spaces.

---

### Post by trent.josephsen on 2010-06-28
> **wmcbrine said:**
> I'm with those guys. I'm a reformed space-and-tab mixer myself. Bad, bad, bad. Spaces only now. PEP 8 forever, even in my C code.

Meh, whatever.  Consistency is more important than adhering to any particular set of guidelines.

---

### Post by wmcbrine on 2010-06-28
> **trent.josephsen said:**
> Consistency is more important than adhering to any particular set of guidelines....and consistency is impossible to achieve when mixing spaces and tabs.

---

### Post by BenAshton24 on 2010-06-28
Tabs. I hate spaces. They're fiddly and always end up getting in the way. I want a single character for each indentation!

---

### Post by jpkotta on 2010-06-28
For Python, PEP8 (4 spaces, no tabs).  For C and C-like languages, my default is to use tabs for indentation and spaces for alignment: [http://www.emacswiki.org/emacs/SmartTabs](http://www.emacswiki.org/emacs/SmartTabs).  See?  "Both" is actually the correct answer.

---

### Post by trent.josephsen on 2010-06-28
> **wmcbrine said:**
> ...and consistency is impossible to achieve when mixing spaces and tabs.
A line with an indentation level of N has floor(N/8) tabs followed by N (mod 8) spaces.  Vim does this for me; I don't count them out myself.  Nothing inconsistent about it.

---

### Post by schauerlich on 2010-06-29
I always use spaces. I prefer 4, but my CS classes usually want 2, so I do that for school work.

---

### Post by wmcbrine on 2010-06-29
> **trent.josephsen said:**
> A line with an indentation level of N has floor(N/8) tabs followed by N (mod 8) spaces.  Vim does this for me; I don't count them out myself.  Nothing inconsistent about it....until someone tries to look at the code in an editor (or other viewer) that handles tabs differently.

---

### Post by Zugzwang on 2010-06-29
> **wmcbrine said:**
> ...until someone tries to look at the code in an editor (or other viewer) that handles tabs differently.

May I ask what is the point about this "consistency"? Every piece of code should be well readable with any tab-setting, unless you have tabs in your comment ASCII-art or something like that.

---

### Post by trent.josephsen on 2010-06-29
> **wmcbrine said:**
> ...until someone tries to look at the code in an editor (or other viewer) that handles tabs differently.
Which is why setting tabstops to anything other than 8 spaces is a bad idea.

---

### Post by xsinsx on 2010-06-29
Use spaces preferably but all my editors are setup that a tab is equal to 4 spaces so i have the benefit of the one key for a set of spaces :D

---

### Post by Simian Man on 2010-06-29
> **trent.josephsen said:**
> A line with an indentation level of N has floor(N/8) tabs followed by N (mod 8) spaces.  Vim does this for me; I don't count them out myself.  Nothing inconsistent about it.

> **trent.josephsen said:**
> Which is why setting tabstops to anything other than 8 spaces is a bad idea.

I never want to work on a project with you :).


> **xsinsx said:**
> Use spaces preferably but all my editors are setup that a tab is equal to 4 spaces so i have the benefit of the one key for a set of spaces :D

Most editors will insert some number of spaces when you hit the tab key - and most will indent for you in 90% of situations anyway, so it's not a big deal to use spaces.

---

### Post by MindSz on 2010-06-29
I use tab set to 4 spaces.

---

### Post by ELD on 2010-06-29
Tabs all the way, far, far less fiddely than spaces and everyone seems to use weird amounts with spaces....

---

### Post by trent.josephsen on 2010-06-29
> **Simian Man said:**
> I never want to work on a project with you :).
Hey, that convention was set long before I was born; I just follow it.  And I stick to the standards of the project I'm working on when such standards exist.

---

### Post by wmcbrine on 2010-06-29
> **Zugzwang said:**
> Every piece of code should be well readable with any tab-settingNot when tabs are mixed with spaces. That's what we're talking about here.

Not that I'm really fond of the idea of code looking different in different editors, even with pure tabs. I'm sad to see tabs winning the poll right now.

> **trent.josephsen said:**
> Which is why setting tabstops to anything other than 8 spaces is a bad idea.And yet, you yourself said that you used to set them to four. Anyway, it's not always an option. (I've even seen at least one semi-popular editor that doesn't handle tabs properly at all, treating them as fixed numbers of spaces rather than moving to the next tab stop.)

Like I said, I used to do what you're doing. And I saw my formatting messed up enough times to realize it was a bad idea.

---

### Post by wdaniels on 2010-11-19
> **wmcbrine said:**
> ...and consistency is impossible to achieve when mixing spaces and tabs.

I don't think that any perfect solution exists unfortunately. Ideally everyone would just use tabs and then indents can be consistently as big or small as each of us likes.

But invariably with collaborative development, sooner or later someone will mix it. So I think the best "rule" is not to have a rule and just try to remain consistent with what's used in each file as it comes.

For my own purposes, I find code easier to read in a terminal using indentation with 2 spaces, so that's my default setting. I would expect that to be unpopular but, frankly, I've never found any alternative strategy to work out either better or worse for promoting consistency in reality...somebody will screw it up whatever you do.

And if they don't screw up the indentation, they'll do something else you think is ugly with the layout of conditional blocks, curly braces, line lengths, naming etc.

This is just one of the things we have to learn to live with, especially in the FOSS world :D Difficult when most programmers are naturally pedantic about this stuff (myself included).

---

### Post by trent.josephsen on 2010-11-19
I revoke my former statements and reluctantly see the error of my ways.  Tabs FTW.

---

### Post by ziekfiguur on 2010-11-19
> **xsinsx said:**
> Use spaces preferably but all my editors are setup that a tab is equal to 4 spaces so i have the benefit of the one key for a set of spaces :D

That exactly, also:
```
sed -e 's/\t/    /g' -e 's/[[:blank:]]*$//' -e 'a\'
```

---

### Post by Vox754 on 2010-11-19
> **wdaniels said:**
> I don't think that any perfect solution exists unfortunately. Ideally everyone would just use tabs and then indents can be consistently as big or small as each of us likes.

But invariably with collaborative development, sooner or later someone will mix it. ...

Yes. The problem is mixing. The problem is also that most people don't make a distinction between "indentation" and "alignment" of code.

**Indentation** refers to the amount of white space at the beginning of a line, while **alignment** refers to any other white space in the line to accommodate the text with a previous line, this is where most horrors happen.

```

def f():
    This is indented
    Four-spaces indentation (assume it's a tab)
1234    1234    1234    1234    1234
    1234    1234    1234    1234
    |   |   |   |   |   |   |   |
    |   |   |   |   |   |   |   |
    int boo     =   56 ; /* There are two tabs */
    int bas     =   10 ; /* before the equals sign */
    char[] var  =   "There is one tab before the equals sign" ;
    /* There is one tab after each equals sign */

```


Now change it to 6-spaces tab.
```

def f():
      This is indented
      Six-spaces indentation (assume it's a tab)
123456      123456      123456      123456
      123456      123456      123456
      |     |     |     |     |     |
      |     |     |     |     |     |
      int boo           =     56 ; /* Still two tabs */
      int bas           =     10 ; /* before the equals sign */
      char[] var  =     "Still one tab, and it no longer aligns" ;

```
The indentation remains one tab, and it looks good. But the lines no longer align at the "=" character.

The alignment problem can be solved by always using spaces, without worrying about the amount of space used for indentation.

Again with six-spaces indentation, but using spaces for alignment:
```

def f():
      This is indented
      Six-spaces indentation (assume it's a tab)
123456      123456      123456      123456
      123456      123456      123456
      |     |     |     |     |     |
      |     |     |     |     |     |
      int boo     =     56 ; /* Five spaces before the sign */
      int bas     =     10 ; /* Five spaces before the sign */
      char[] var  =     "Two spaces before the sign"
      /* The space after the sign could be a tab */
      /* and it wouldn't affect the alignment */

```

Now with 9-spaces tabs.
```

def f():
         This is indented
         Crazy 9-spaces indentation (assume it's a tab)
123456789         123456789         123456789
         123456789         123456789
         |        |        |        |
         |        |        |        |
         int boo     =     56 ; /* Five spaces before the sign */
         int bas     =     10 ; /* Still aligns okay! */
         char[] var  =     "Two spaces before the sign"
         /* The space after the sign is a tab */
         /* and it doesn't affect the alignment */
         /* because the reference is the "=" sign, */
         /* which is correctly positioned with spaces */

```

I'm not sure if everybody gets my example.

In summary, understand the difference between indenting (at the beginning of a line), and aligning (everywhere else).

For indenting you can use tabs or spaces (be consistent!). For alignment you should only use spaces!

---

### Post by wdaniels on 2010-11-19
> **Vox754 said:**
> The problem is also that most people don't make a distinction between "indentation" and "alignment" of code.

Ah yes, a very good point. This is probably the worst of all actually now that I think about it...people using a small tab size then use tabs to align something about 30 spaces in from the block "indent", so then when someone else opens it with 4 or 8 tab size sometimes the "aligned" code is so far off to the right you don't even see it :D

Even if we were to invent a set of fancy language parsers for all the editors that would redo the layout of the entire source file according to the parse-tree structure, you would still never be able to sort out this problem with tabbed alignment, except to remove any alignment at all!

I've never been a fan of "significant white space" in languages, but perhaps it is the only way to enforce a solution to this perpetual aggravation. And when I think about it like that I always conclude that messed up formatting is the lesser of the two evils and I curse myself for being such a pedant.

---

### Post by Vox754 on 2010-11-19
> **wdaniels said:**
> Ah yes, a very good point. This is probably the worst of all actually now that I think about it...people using a small tab size then use tabs to align something about 30 spaces in from the block "indent", so then when someone else opens it with 4 or 8 tab size sometimes the "aligned" code is so far off to the right you don't even see it :D...

Happens in this same forum.

People use tabs to indent, and in their editor they (unknowingly) use 2 spaces expansion. Then they post code in this forum, which auto-expands to the classical 8 spaces.

So when people indent, in their own mind to 4 spaces, they actually use 2 tabs, or 16 spaces in this forum.

I've seen code like this here:
```

for (i = 0 ; i < 99 ; ++i) {
                for (i = 0 ; i < 99 ; ++i) {
                                if ( bla == 456)
                                                break ;
                }
}

```

And then they are like, "lol, I don't no what's wrong with the spacing, sorry guyz, Windows sucks, lol"

---

### Post by schauerlich on 2010-11-19
> **Vox754 said:**
> 
```

for (i = 0 ; i < 99 ; ++i) {
                for (i = 0 ; i < 99 ; ++i) {
                                if ( bla == 456)
                                                break ;
                }
}

```

And then they are like, "lol, I don't no what's wrong with the spacing, sorry guyz, Windows sucks, lol"

If you look at your example, there's bigger problems than just spacing. :)

---

### Post by worksofcraft on 2010-11-20
> **trent.josephsen said:**
> I revoke my former statements and reluctantly see the error of my ways.  Tabs FTW.

Awesome... someone with an open mind and prepared to changes his/her views based on reason :)

---

### Post by holiday on 2010-11-20
> **Simian Man said:**
> I indent with 2 spaces.

Me too. 

Scrolling horizontally to read the next condition? 

And if it takes more than a screen width, please think it over.

---

### Post by ssam on 2010-11-20
tabs.

tab is a single char that means indent. people can view my code with the width set to anything they want.

---

