---
title: "edit text with (very) long line"
date: 2007-06-18
forum: Programming Talk
---

### Post by lamborghiniwang on 2007-06-18
Hi there.
I'm writing a C++ code in which there are some very long (about 5-10K bytes each) single line mathematical expressions that I generated with Maple. I found that these long expressions make it very slow when I scroll up/down. (in either Anjuta or GEdit). I tried to turn on the "auto-wrap" option but it doesn't help.

I don't want to manually break them into shorter lines since it will makes the code hard to read. I'm wondering if there is any way (or any text editor) that can make the scrolling faster?:D

---

### Post by Arndt on 2007-06-18
> **lamborghiniwang said:**
> Hi there.
I'm writing a C++ code in which there are some very long (about 5-10K bytes each) single line mathematical expressions that I generated with Maple. I found that these long expressions make it very slow when I scroll up/down. (in either Anjuta or GEdit). I tried to turn on the "auto-wrap" option but it doesn't help.

I don't want to manually break them into shorter lines since it will makes the code hard to read. I'm wondering if there is any way (or any text editor) that can make the scrolling faster?:D

Emacs usually has no problem with very long lines, but I wonder: how can a single line of thousands of characters be easier to read than multiple shorter ones?

---

### Post by n00bWillingToLearn on 2007-06-18
I second the sugesstion of Emacs, but also consider vi and if you want an easy to use but still efficient and terminal based editor try nano.

---

### Post by lamborghiniwang on 2007-06-18
> **Arndt said:**
> Emacs usually has no problem with very long lines, but I wonder: how can a single line of thousands of characters be easier to read than multiple shorter ones?

Thanks for the suggestion, Emacs seems to work fine.:D

I said it's easier to read with a single line expression because otherwise it will cover so many lines and I have to page up/down for many times in order to read the next line of code (It's a 55KB file and 53KB of them are those expressions).

---

### Post by Arndt on 2007-06-19
> **lamborghiniwang said:**
> Thanks for the suggestion, Emacs seems to work fine.:D

I said it's easier to read with a single line expression because otherwise it will cover so many lines and I have to page up/down for many times in order to read the next line of code (It's a 55KB file and 53KB of them are those expressions).

I see now, you don't want to see the whole line, because it's only a sort of opaque garbage to the eye. Perhaps it's possible to put each of those lines in a .h file of its own, with a suitable #define statement, and #include them in the main file?

Another thing apart from readability that may become a problem is that C++ has a limit on how long lines are guaranteed to work. I don't remember the limit, and you apparently haven't encountered it yet, but one day the compiler may impose a need to actually split those long lines into shorter ones.

---

### Post by lamborghiniwang on 2007-06-22
> **Arndt said:**
> I see now, you don't want to see the whole line, because it's only a sort of opaque garbage to the eye. Perhaps it's possible to put each of those lines in a .h file of its own, with a suitable #define statement, and #include them in the main file?

Another thing apart from readability that may become a problem is that C++ has a limit on how long lines are guaranteed to work. I don't remember the limit, and you apparently haven't encountered it yet, but one day the compiler may impose a need to actually split those long lines into shorter ones.

Thanks for the suggestion Arndt. I'll keep the line length limit in my mind. I may have several even longer expressions that I need to add into my code. :D

---

