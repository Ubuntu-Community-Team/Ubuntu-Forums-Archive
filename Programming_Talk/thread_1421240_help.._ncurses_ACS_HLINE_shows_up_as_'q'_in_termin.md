---
title: "help.. ncurses ACS_HLINE shows up as 'q' in terminal"
date: 2010-03-04
forum: Programming Talk
---

### Post by coldhandmurr on 2010-03-04
I'm using libncurses5-dev (via #include <curses.h>) to draw some boxes on the terminal screen.

The terminal screen I'm viewing in, is the one that shows up when you hit Ctrl+Alt+F1.  (If you want to see what I'm talking about, try it, and use Ctrl+Alt+F7 to get back to your graphical desktop.)

Problem is, when I try to draw a horizontal line using the character constant ACS_HLINE, it shows up as the 'q' character instead.

Ncurses faq says this is because I have the wrong terminal type set. It says "you simply have to find the correct terminfo description".
[http://invisible-island.net/ncurses/ncurses.faq.html#no_line_drawing](http://invisible-island.net/ncurses/ncurses.faq.html#no_line_drawing)

Which term type should I be exporting for these Ctrl+Alt+Fn terminals to show the correct ACS_HLINE and ACS_VLINE characters?

Should this be a feature request / bug fix or something?

Fwiw...
in the Ctrl-Alt-Fn terminals, $TERM is set to linux ... and it looks like 'linux' is an alias for 'xterm'

Thanks

---

### Post by coldhandmurr on 2010-03-04
If it helps any, using  [FONT=Fixedsys]border(0,0,0,0,0,0,0,0);[/FONT]  draws the ACS_HLINE AND ACS_VLINE characters correctly, as lines and no 'q' and 'x'.

---

### Post by coldhandmurr on 2010-03-04
Ok, this is happening when I pass ACS_HLINE to a function as a char arg. Digging through curses.h to figure it out...

..and also apparently talking to myself.

---

### Post by wmcbrine on 2010-03-04
"linux" is NOT an alias for "xterm", although they have a lot in common. The "linux" terminal type is correct.

If your goal is to draw horizontal lines, use hline() instead of ACS_HLINE. It should work if border() works.

ACS_HLINE is a chtype, rather than a character. If you strip off the A_ALTCHARSET attribute, then 'q' is what you'd get.

---

