---
title: "can we select whole words in nano?"
date: 2013-04-07
forum: New to Ubuntu
---

### Post by user201304 on 2013-04-07
In Windows Notepad you can do shift-ctrl+right to select whole words, or you can do shift-home/end to quickly select the whole line from where the cursor is. Are these possible in nano?

---

### Post by vasa1 on 2013-04-08
Here's some reading on nano: [https://help.ubuntu.com/community/Nano](https://help.ubuntu.com/community/Nano)
I'm not sure that comparing nano with Notepad is useful. If you want something like Notepad, consider GUI-based programs such as Gedit or Leafpad or Medit or Geany,

---

### Post by agent-squirrel on 2013-04-08
Nano is a Terminal Based Text editor and so is not likely to support the Windows GUI based equivalent&#8217;s features. 
As vasa1 said, a good alternative is Gedit on gnome or Kate on KDE.

---

### Post by alphacrucis2 on 2013-04-08
I don't know about nano but what the OP is requesting can easily be done using the VI or VIM cli editors. You would use the "yank" command. yw yanks from the current cursor position to the end of the current word. That would be to copy the word. If you wanted to delete it you would use dw. You can use dw for cut as well as the deleted text gets stored in a buffer you can paste from.

---

### Post by user201304 on 2013-04-08
Thanks guys for the suggestions.

> **alphacrucis2 said:**
> I don't know about nano but what the OP is requesting can easily be done using the VI or VIM cli editors. You would use the "yank" command. yw yanks from the current cursor position to the end of the current word. That would be to copy the word. If you wanted to delete it you would use dw. You can use dw for cut as well as the deleted text gets stored in a buffer you can paste from.

Thanks, learn something new every day... And apparently it's y$ to copy to the end of the line.

---

### Post by nothingspecial on 2013-04-08
> **user201304 said:**
> In Windows Notepad you can do shift-ctrl+right to select whole words, or you can do shift-home/end to quickly select the whole line from where the cursor is. Are these possible in nano?

Alt-A to set a mark then either Esc Esc Space to select the word or Esc Esc E to go to the end of the line.

To see nano's help page press Ctrl-G like it says at the bottom.

---

### Post by ronald577 on 2013-04-08
yeah it is possible to see Nano.

---

### Post by ronald577 on 2013-04-08
yeah it is possible Nano.

---

