---
title: "AT&amp;T asm syntax highlighting?"
date: 2007-01-07
forum: Programming Talk
---

### Post by JRevell on 2007-01-07
Hey, this has been driving me mad. Are there any good text editors with syntax highlighting for the AT&T assembly syntax, or how could I configure one to do so ( please be in-depth, I'm a noob :-| )
Please note I do not want to have to spend 40+ hours relearning muscle-memory just do use a text editor, I would prefer something simple. Thank you.

---

### Post by JRevell on 2007-01-07
*bump*

---

### Post by Wybiral on 2007-01-07
While I personally feel it is best to learn without any help as this will develop a concrete understanding and memory of the syntax... And I will tell you that 9 out of 10 assembly programmers *probably* wont be using syntax highlighting (since there are so few commands).

However, for Gedit you can either write your own syntax file, or do this...

Take this file: [http://bugzilla.gnome.org/attachment.cgi?id=45158&action=view](http://bugzilla.gnome.org/attachment.cgi?id=45158&action=view)

Save that XML as something like "asm.lang" or "assembly.lang" or "gas.lang" and then move it to... "/usr/share/gtksourceview-1.0" (this may be different for you, first make sure that you have all of your other ".lang" files in there.

When you open up Gedit next, you should have the option of "Assembly" under "View->Highlight Mode->Sources"

---

### Post by DarkW0lf on 2007-05-28
I am trying to get syntax highlighting for HLA (high level assembler).
Would you know how to edit a lang file or who made this one ?

I think I can change keywords easy enough but the regex for the syntax is someting I don't understand.

I am going to have to browse around the lang folder that stores these.

---

### Post by Deepak Jindal on 2010-11-01
[http://www.asmcommunity.net/board/index.php?topic=29796.0](http://www.asmcommunity.net/board/index.php?topic=29796.0)

a good way of setting you gedit for assembly programming..

---

