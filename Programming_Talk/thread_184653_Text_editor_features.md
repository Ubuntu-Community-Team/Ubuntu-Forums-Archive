---
title: "Text editor features"
date: 2006-05-30
forum: Programming Talk
---

### Post by rplantz on 2006-05-30
There are always questions about what text editor is the "best" or has specific features. I ran across [http://en.wikipedia.org/wiki/Comparison_of_text_editors](http://en.wikipedia.org/wiki/Comparison_of_text_editors).

As has been pointed out in other threads, this comparison shows that emacs has the most features.

Edit: I did not mean to imply that emacs is the best here. I provided the link for those who are trying to decide which editor is best for them. There are good arguments for simplicity in many things in life, including text editors. "Features" often get in our way.

---

### Post by simplyw00x on 2006-05-30
It says that emacs has collaborative support and 'overlappable windows'. I seem to recall :sb in vim making paned "overlappable" windows and CVS being a collaboration tool, not the text editor, but whatever.

---

### Post by B0rsuk on 2006-05-30
Two things emacs doesn't have:

- hotkeys good for beginners... This means you initially spend a lot of time checking out most basic hotkeys. And basically each time you press a key combination by mistake, something weird happens and you don't know how to undo it.
- **convenient** code block folding. You can do it, but in my opinion it's not as simple to do as in Kate. My teacher, who is one of emacs contributors, agrees on this point.

Kate is enough for my needs; emacs does feel clunky for someone who doesn't remember all hotkeys.
I wrote short description here: [http://ubuntuforums.org/showthread.php?t=176482&page=5](http://ubuntuforums.org/showthread.php?t=176482&page=5)

Then again, emacs has mail, psychiatrist, speech synthesizer, and you can play nethack without closing emacs (I prefer Linley's Dungeon Crawl, but still)

---

### Post by IYY on 2006-05-30
No editor will ever beat good old vi. Not in the least bit intuitive, but once you get used to it, there's no going back.

---

### Post by thumper on 2006-05-31
[QUOTE=B0rsuk]Two things emacs doesn't have:

- hotkeys good for beginners... This means you initially spend a lot of time checking out most basic hotkeys. And basically each time you press a key combination by mistake, something weird happens and you don't know how to undo it.[/QUOTE]
Ctrl-Shift-_ of course :) Surely that's obvious...
I also map it to Ctrl-z which is much more useful to me than minimize.
[QUOTE=B0rsuk]- **convenient** code block folding. You can do it, but in my opinion it's not as simple to do as in Kate. My teacher, who is one of emacs contributors, agrees on this point.[/QUOTE]
I must admit, in my 20 years of programming I have never used block folding, nor do I really see the point of it.

If things are too complicated that you need to hide parts of the code to make sense of it, it is time to refactor it - break it up - make it more readable.

Hiding things is not the answer.

---

### Post by simplyw00x on 2006-05-31
I'm a die-hard vimmist and the code folding in that is intuitive (especially with the right plugins) and _damn_ useful. Sometimes there's no solution to a large chunk of code that makes navigating slow, and it's good to have a 'menu' of functions available at a glance.

---

### Post by Eric_T on 2006-05-31
[QUOTE=simplyw00x]I'm a die-hard vimmist and the code folding in that is intuitive (especially with the right plugins) and _damn_ useful. Sometimes there's no solution to a large chunk of code that makes navigating slow, and it's good to have a 'menu' of functions available at a glance.[/QUOTE]

To navigate past large chunks of code in emacs, you can either use tags or I-search.
I do agree that folding can be nice if you need to compare sections of code, but I just create separate buffers for that.

But just out of curiosity, how can you fold code in emacs?

---

### Post by rplantz on 2006-05-31
[QUOTE=thumper]
I must admit, in my 20 years of programming I have never used block folding, nor do I really see the point of it.

If things are too complicated that you need to hide parts of the code to make sense of it, it is time to refactor it - break it up - make it more readable.

Hiding things is not the answer.[/QUOTE]

The first "editor" I used was a card punch machine in 1961. I've used LOTS of editors since.

Like thumper, I never saw the need for block folding -- until I used it the other day on a book I've written using LaTeX. In that kind of writing, it's really nice to be able to temporarily hide, say, a chunk of code that I'm using as an example. (It's a book on assembly language.)

By the way, I installed kate a couple of days ago and am playing with it. With very little use so far, it looks really good to me.

I should mention that I was almost exclusively a Mac user for about 20 years. I used bbedit there. From that experience, the mouse is an integral part of my usage, even though I'm a pretty good touch typist.

---

### Post by Zed on 2006-05-31
I'm a big Emacs fan, but agree that the default keybindings are bad, and it's relatively hard to learn (but worth it.)

For one attempt to make the keybindings easier, check out [Easymacs](http://www.dur.ac.uk/p.j.heslin/Software/Emacs/Easymacs/).

---

