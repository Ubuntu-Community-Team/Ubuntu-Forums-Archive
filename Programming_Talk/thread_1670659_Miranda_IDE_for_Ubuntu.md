---
title: "Miranda IDE for Ubuntu?"
date: 2011-01-19
forum: Programming Talk
---

### Post by litterbug_kid on 2011-01-19
I don't really know if this is the correct forum to be asking this, but I have to learn Miranda and was wondering if there was a nice IDE for it for Ubuntu?

---

### Post by Simian Man on 2011-01-19
> **litterbug_kid said:**
> I don't really know if this is the correct forum to be asking this, but I have to learn Miranda and was wondering if there was a nice IDE for it for Ubuntu?

It doesn't seem like it.  Googling "Miranda IDE" actually turns up this thread as the first result.  Usually if there is a good Linux IDE for a less-used language, it tends to be as an Eclipse plugin.  Googling for "Miranda Eclipse" doesn't turn up anything either.

Seems like it's text editor + terminal time :).

---

### Post by Reiger on 2011-01-19
Not that I know of, however Miranda is at the core rather similar to the more popular Haskell. For which there *is* some form of IDE support.

---

### Post by eeperson on 2011-01-19
There is a Miranda pugin for Emacs.  Due to the obscurity of Miranda, I'm guessing that is your best option for an IDE.

---

### Post by LemursDontExist on 2011-07-22
> **Reiger said:**
> Not that I know of, however Miranda is at the core rather similar to the more popular Haskell. For which there *is* some form of IDE support.

The reason you can't find IDE support is that no one would choose to program in Miranda over Haskell.  Except for a few minor function name differences, Miranda is a less capable subset of Haskell without the virtue of being open source. In fact many Miranda programs will compile under the Haskell compiler with little modification.  Unless you absolutely have to learn Miranda, Haskell is a better choice.

If for some reason you *do* need to use Miranda, a Haskell IDE will get you most of the way there, though you'll find some common functions are missed by the syntax highlighting (Haskell uses head instead of hd, tail instead of tl, etc.).

---

