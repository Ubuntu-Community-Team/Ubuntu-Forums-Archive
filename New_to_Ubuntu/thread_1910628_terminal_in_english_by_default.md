---
title: "terminal in english by default"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by Morpholinux on 2012-01-17
ok I work a lot with the terminal and the language for remembering commands, variables and everything is in english.
If I write something (g-mails, homeworks, etc) it will be in spanish
I have 3 keyboard layouts (enlish, spanish (default) and greek) and my keyboard is in spanish (Lam)
Problem is that every time that I open the terminal I have to change the keyboard layout from spanish to english(not very difficult, but -> mouse movement+click+mouse movement+click)
It would be very nice to open the terminal with keyboard layout in english by default
How I do that?

thanks in advance

---

### Post by BC59 on 2012-01-17
You can change the layout using keystrokes. I use the same languages... and I change them with SHIFT+ALT.

---

### Post by WasMeHere on 2012-01-17
```
setxkbmap us
``` if you want US English. You can put it into ~/.bashrc or have it as an alias for example
```
alias en='setxkbmap us'
``` also in ~/.bashrc to have en as an alias an a corresponding alias to go back to Spanish.

---

### Post by Morpholinux on 2012-01-18
I think I prefer the SHIFT+BLQMAYUS instead of the alias

Thanks

---

