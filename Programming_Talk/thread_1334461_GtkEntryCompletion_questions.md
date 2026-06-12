---
title: "GtkEntryCompletion questions"
date: 2009-11-22
forum: Programming Talk
---

### Post by houbysoft.xf.cz on 2009-11-22
Hi all, I have a few questions about GtkEntryCompletion
([http://library.gnome.org/devel/gtk/unstable/GtkEntryCompletion.html](http://library.gnome.org/devel/gtk/unstable/GtkEntryCompletion.html))

I already implemented it in my application, but I would need some further assistance since I need some features which I couldn't find on the page or on google.

1) How do I make the completion display something, but when one of the choices is accepted, insert something else? Ie how can I use one column in the GtkListStore I use for showing in the matches, but another column for inserting?
I need this because I'd like to create function-completion (the app is a calculator), and so for example if somebody types "fact" in the gtkentry, I'd like to show something like "factorial(x) - return the factorial of x", but when he selects this match, it would need to insert only "factorial(" so that the user can type his argument.

2) Is there a way to trigger the completion even in the middle of the GtkEntry?  I need this because it would be good to trigger auto-completion every time a character is entered. For example, if somebody types "2 + sq", it should tell him to try "sqrt(x) - return the square root of x" etc., but right now it only completes if the GtkEntry starts with "sq".


Thanks for your replies!

---

### Post by houbysoft.xf.cz on 2009-11-23
Well, bump.

---

### Post by houbysoft.xf.cz on 2009-11-25
Another one, nobody here knows?
I would really need this...

Please help.

---

