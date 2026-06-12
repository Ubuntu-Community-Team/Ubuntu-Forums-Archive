---
title: "[SOLVED] Inserting special characters by their code"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by natirips on 2008-09-13
How do I insert a special character if I know it's code but can't find/type it on the keyboard?

For example: if I broke my A key, but I know that it's 0100 0001 binary, 101 octal, 65 decimal, or 41 hexadecimal for capital; and 0110 0001 binary,... for non-capital.

So how do I insert it? In FreeDOS, for example, I can hold down ALT key and type decimal code at the num-pad. Also in console I can use $'\NNN', where NNN if octal for my desired character. But how do I do this in GNU/Linux in general (gedit, file save dialog, web browser,...)?

---

### Post by RomeReactor on 2008-09-13
Hi. You can press CTRL+SHIFT+U, then 41 for **a** or 61 for **A**.

---

### Post by natirips on 2008-09-13
> **RomeReactor said:**
> Hi. You can press CTRL+SHIFT+U, then 41 for **a** or 61 for **A**.

Opens a new tab with the same page as on active one in Galeon (my web browser). Besides, CTRL+SHIFT sounds like terminal. I need solution for the gui application. In my opinion inserting characters into openoffice/abiword and copy-pasting them into gedit is like cutting down a whole tree just to make a single toothpick out of it.

However it works fine with gedit, except you made a typo and confused the capital abd non-capital letter.

And just for future reference, CTRL+SHIFT+U, than hexadecimal code, and enter or spacebar.

---

