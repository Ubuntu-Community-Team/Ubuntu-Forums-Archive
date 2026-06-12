---
title: "Programming standards and line length"
date: 2011-04-11
forum: Programming Talk
---

### Post by r-senior on 2011-04-11
This is just out of personal interest really, not an official poll or research, even though I've made it sound like one ;)

[LIST]
[*]Does you find people/places still adhere to the old 80-column rule?
[*]Does it depend on which language is in use?
[*]Have you adopted, or been asked to adopt, a different standard, e.g. 132?
[/LIST]

---

### Post by VernonA on 2011-04-11
At my company it's an informal rule, ie we try to keep lines below 80, and if a line needs to be broken we try to place the split so both results are under 80. However we don't insist on the rule, because some lines just don't split well. We like variable names which are self-documenting, so sometimes they get a bit long. If this forces a line to be say 90 or even 100 chars long so be it.

---

### Post by johnl on 2011-04-11
> **r-senior said:**
> This is just out of personal interest really, not an official poll or research, even though I've made it sound like one ;)

[LIST]
[*]Does you find people/places still adhere to the old 80-column rule?
[*]Does it depend on which language is in use?
[*]Have you adopted, or been asked to adopt, a different standard, e.g. 132?
[/LIST]

Everywhere I have worked has adhered (in various degrees of strictness) to the 80 column limit.  It seems to me that lines longer than 80 characters tend to get to be difficult to read anyway;  splitting them up cleanly can improve readability.

I have noticed that it is usually a lot easier to split lines in certain languages (e.g C) than in others (Python).  That's just my feeling, no hard research of experience.

---

### Post by slavik on 2011-04-11
when first programmers for actual computers appeared, they used punch cards. those punch cards had 80 columns. this later gave rise to terminals that displayed at most 80 characters on one screen.

---

### Post by Reiger on 2011-04-11
But the reason it is kept has to do with the fact that 80 columns is also a comfortable line length for Western scripts.

---

### Post by schauerlich on 2011-04-11
Try writing a Cocoa app with a 80 character line limit.

---

### Post by simeon87 on 2011-04-11
Although its origins can be traced back to technical limitations, I still prefer to keep my lines at 80 chars for readability. It helps to keep the code clean and readable.

---

### Post by Simian Man on 2011-04-11
I never break long lines into two lines like:
```

if((something really really long) && (something else really really long)) {
-----------------------------------------------------------------------
if((something really really long) &&
   (something else really really long)) {

```

Because I think that looks really hideous.  I do break things logically sometimes like:
```

cond1 = something really really long;
cond2 = something else really really long;
if(cond1 && cond2) {

```
But I just do this when things get too messy, not when I have surpassed some arbitrary limit.

---

### Post by 1clue on 2011-04-11
At work we use a "soft" limit of 140 characters.

Everyone who programs there has at least one 1920xsomething monitor, so this leaves plenty of room on the side for other IDE panels.

We find that code where the command wraps is more difficult to read, so we go extra wide.  The limit is "soft" because if some command is only a few characters longer, or if it's for some reason more difficult to read wrapped, then we can go with a longer line.

Most of the time lines are under 120, or in some cases the complexity of the line becomes more easily read in multiple lines.  For example, I often brake an if statement up:

if(someFunction(this.that.theOther)
  || someOtherFunction(foo.bar())
  || ...) {

Sometimes the logic gets pretty complex, perhaps nesting logic within logic, and it gets hard to figure things out without breaking the line down.

The one overriding rule for us is ease of readability.  If the line is just some huge call with a bunch of options in it nobody will be interested in, we extend it out.  If the call can be broken up and be more readable, then we break it up.

---

### Post by cgroza on 2011-04-11
I really like them at 80, if they are longer, it starts being a problem on my monitor because my IDE is kind of bulky and takes up a lot of room.

---

### Post by aport on 2011-04-13
There is a quote, I'm going to butcher this, which is basically, "Programs are meant for reading, and only incidentally run on a computer."

Reading very long lines of code left to right can be a bit frustrating. Splitting these lines to fit within a set column limit (most commonly 80) improves the readability of code a good deal.

The Linux kernel style guidelines, which is my Bible in terms of programming style (at least in C), requires 80 columns maximum. Gedit has an option to show the margin at 80 columns default, and it's a good rule of thumb.

The Linux kernel style guidelines go one step further, and assert that if your code considerably overruns 80 columns, due to excessive levels of indentation from nesting or really long function and variable names, then you should perhaps re-think your programming strategy. I tend to agree with this. At least in C, there is really no good reason for your code to go past 80 columns. I've read tens of thousands of lines of code in C and have never seen a good justifiable reason for exceeding 80 columns. The programmer may think he has a good reason, but another programmer will be able to reduce the columns through better programming practices.

I can't comment on using wacky libraries like glib, where function names are ridiculously long due to the lack of real namespaces. That may be a good exception to the rule.

---

### Post by ssam on 2011-04-13
usually just let my editor soft wrap long lines. however if its wraps i take it as a hint that it is ugly code.

---

### Post by 1clue on 2011-04-13
I guess I have to agree with that, even though my company's width is almost double 80.

Our bible is readability, but our language is not c.  We write web applications, and sometimes we're pushing text out.  Sometimes it's just easier to read if the entire sentence or message is on the same line, especially since there is no handy IDE layout which uses all the rest of the space on our screens.

Most of the code I see is 80 columns or less.

---

### Post by llanitedave on 2011-04-14
I find myself most comfortable with 120 characters.  Using "natural" rather than cryptic variable names takes up a lot more space.

In Python, with its required indentation, the combination of nested indents and natural variable names makes the 80 character limit a bit tight.  In this case, limiting your lines to 80 characters actually reduces readability, IMO.

I also use blank lines to set off code blocks so that the code doesn't appear crowded in the vertical sense.

I've experimented with different styles in different editors with different fonts and character sizes, and the 120-character line seemed to me to fall out as the most comfortable arrangement.

---

### Post by r-senior on 2011-04-14
Interesting responses. =D>

I do stick to 80 columns with C, but Java (especially with Spring) and Objective-C are nigh on impossible with decent indentation. It was thinking about these that prompted the question.

---

### Post by 1clue on 2011-04-14
Ya, I'm doing java and grails with spring.  Same thing, and the reason why sometimes I think it's easier to read a longer line.

Self-documenting code and all that.  We rarely have comments in the code because the variable names are chosen to be most readable, which means they're not short unless it's a method-local or a standard across the app.

---

### Post by LoneWolfJack on 2011-04-14
> Everyone who programs there has at least one 1920xsomething monitor, so this leaves plenty of room on the side for other IDE panels.

same experience here. we just bought new monitors for all workstations in my company and they're all 1920x1080, so we cap lines at 220 characters.

---

### Post by nvteighen on 2011-04-15
I didn't know that the 80-characters "rule" had a technical reason behind. I stick to it just because it's like a default.

Anyway, the exact number of characters is irrelevant; what you really need are conventions that make your code predictable to the reader. This means: the reader should be able to concentrate in the code as soon as possible, by making some clear conventions that ease the project's learning curve.

---

### Post by Blackbug on 2011-04-15
well even at my workplace also, we adher to 80 character limit.
And, coding standards are almost generic now.
with emacs and vi, especially with emacs the indentations are easy to practice and quite generic.
 
my work is mostly in c++ so i can talk mostly about coding standards in c++.
certainly with C there are different practices, especially if we take into account opensource codebase (linux, wget, curl and etc etc..)

---

### Post by DarkHackerX on 2011-04-29
Does you find people/places still adhere to the old 80-column rule?
[COLOR=RoyalBlue]Yes, we do on my project to reduce alot side scrolling.[/COLOR]
Does it depend on which language is in use?
[COLOR=RoyalBlue]No, it changes from project to project.[/COLOR]
Have you adopted, or been asked to adopt, a different standard, e.g. 132?
[COLOR=RoyalBlue]No.[/COLOR]

---

### Post by worseisworser on 2011-04-29
132 here. That gives room for two columns (buffers) at a time on each screen. I don't see myself needing all that space coding e.g. C though, but Lisp nests well and that's nice at times and I end up way to the right then:

  [IMG]http://static.nostdal.org/~lnostdal/temp/Screenshot-emacs%40blackbox.png[/IMG]

---

