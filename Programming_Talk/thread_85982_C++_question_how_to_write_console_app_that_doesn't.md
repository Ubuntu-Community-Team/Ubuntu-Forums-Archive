---
title: "C++ question: how to write console app that doesn't scroll?"
date: 2005-11-04
forum: Programming Talk
---

### Post by nrwilk on 2005-11-04
I've been writing this game for a while now and I finally realized that the reason it looks so crappy is that each time I want to output the paying field to the screen, I have to output the whole thing again, which just scrolls the last one up.  How can I get text output like one sees in games such as nethack, where only one character can move at once without having to redraw the whole field?  Is this very difficult?

Thanks for any help!

I really hope someone here knows how to do this.

---

### Post by ltmon on 2005-11-04
I don't know for sure, but you might have to use a specific library.

I would have a look at the "ncurses" library to see what is usable there.

L.

EDIT:  Possibly you could try buffering all your data before sending it to the console in one hit, if you are not already???  Maybe you are calculating your data as you display it... making the program run slightly slower and causing a visible lag in the display.

---

### Post by nrwilk on 2005-11-04
[QUOTE=ltmon]I don't know for sure, but you might have to use a specific library.

I would have a look at the "ncurses" library to see what is usable there.

L.

EDIT:  Possibly you could try buffering all your data before sending it to the console in one hit, if you are not already???  Maybe you are calculating your data as you display it... making the program run slightly slower and causing a visible lag in the display.[/QUOTE]

That's sort of what I'm doing already.  And with personal computers today, console apps run really quick.  It's hard to notice that the whole thing gets outputted every time something moves.

I'll take a look at ncurses.  I've heard of it before, what else is it used for?

EDIT:  This _IS_ what ncurses is used for. hehe.  thanks a lot!  I'm reading a tutorial now.

Any suggestions or advice, or links to good ncurses documentation or tutorials is, of course, still welcome!

---

