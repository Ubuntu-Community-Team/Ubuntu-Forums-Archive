---
title: "What happens to the terminal session when you execute from a file browser?"
date: 2008-12-24
forum: Programming Talk
---

### Post by Jonas thomas on 2008-12-24
I've been working through some wxwidget tutorials and one of the applications sends messages via  std::cout to the terminal.
When I double clicked this GUI Application from the file browser to execute, you don't see a terminal session.  Is there a hidden terminal session running somewhere in the background?
That begs the question... Is it possible to make it display?

This is not a big deal, just curiosity.

---

### Post by nvteighen on 2008-12-24
I guess it just happens nothing. stdout is not defined, or maybe even defined to be /dev/null if no terminal device is open.

---

### Post by Paul Miller on 2008-12-27
As the previous poster mentioned, there is no terminal session.  To get one, you need to run the app with the "Run in terminal" option.

---

### Post by Jonas thomas on 2008-12-28
> **Paul Miller said:**
> As the previous poster mentioned, there is no terminal session.  To get one, you need to run the app with the "Run in terminal" option.
Conceptually, for some reason my brain is having some issues with this as far as what is going on in the background..  Some more things to study..
I guess I should mark this post as Solved.
Thanks nvteighen, Paul.

---

