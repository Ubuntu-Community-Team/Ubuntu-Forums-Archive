---
title: "Text editor?"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by Susss on 2013-03-10
As m curently learning php and mysql and as i have instaled Xamp now i need a god text editor.....m curently using notepad++ but is ther any text edior made for ubuntu?and i cant get aces to my htdocs....

---

### Post by ViliX64 on 2013-03-10
Use 'Ubuntu software center'.. There is plenty of these stuff and it is easy to install..

---

### Post by MG&amp;TL on 2013-03-10
> **Susss said:**
> As m curently learning php and mysql and as i have instaled Xamp now i need a god text editor.....m curently using notepad++ but is ther any text edior made for ubuntu?and i cant get aces to my htdocs....
[URL="https://help.ubuntu.com/community/ApacheMySQLPHP"]
LAMP[/URL] may be a better choice for *buntu than Xamp, just for future reference.

Take your pick from probably hundreds of editors. Bluefish is specifically designed for web development, so that might be a good place to start.

There's also gedit (similiar to np++, slightly less functionality, comes with ubuntu by default), kate (similiar to gedit, comes with KDE), geany (extremely lightweight IDE), and various others, if you like GUI text editors.

If you're not afraid of the commandline and a steep learning curve, I would strongly recommend you learn to use one of the two main CLI editors: vim or emacs. Both have so many commands you'll be working more efficiently than ever after some practice. Emacs is probably more friendly to new users, but vim is less heavy and doesn't try to do 'everything' like emacs does. I do all my editing in vim.

.htdocs? Why can't you access them? BTW anything starting with a '.' character is a hidden file under unix-like operating systems, so you'll need to 'view hidden files' if you're using a file manager.

---

### Post by Susss on 2013-03-10
> **MG&TL said:**
> [URL="https://help.ubuntu.com/community/ApacheMySQLPHP"]
LAMP[/URL] may be a better choice for *buntu than Xamp, just for future reference.

Take your pick from probably hundreds of editors. Bluefish is specifically designed for web development, so that might be a good place to start.

There's also gedit (similiar to np++, slightly less functionality, comes with ubuntu by default), kate (similiar to gedit, comes with KDE), geany (extremely lightweight IDE), and various others, if you like GUI text editors.

If you're not afraid of the commandline and a steep learning curve, I would strongly recommend you learn to use one of the two main CLI editors: vim or emacs. Both have so many commands you'll be working more efficiently than ever after some practice. Emacs is probably more friendly to new users, but vim is less heavy and doesn't try to do 'everything' like emacs does. I do all my editing in vim.

.htdocs? Why can't you access them? BTW anything starting with a '.' character is a hidden file under unix-like operating systems, so you'll need to 'view hidden files' if you're using a file manager.
i cant aces my htdocs coz they need root previliges.i want a text editor that works jus like notepad++...anything u wud like to sugest?

---

### Post by MG&amp;TL on 2013-03-10
> i cant aces my htdocs coz they need root previliges.

Learn about Unix permissions, then use *sudo* to access them or modify the permissions. Why exactly do they have root ownership?

> i want a text editor that works jus like notepad++...anything u wud like to sugest?

Gedit is pretty good. Just type 'gedit' into the dash, or from the Alt-F2 run dialog. Although to be honest, the 'works jus like $SOFTWARE' attitude won't get you very far under Ubuntu, unless there's a linux version of the package you want.

---

### Post by BlinkinCat on 2013-03-10
> **Susss said:**
> i cant aces my htdocs coz they need root previliges.i want a text editor that works jus like notepad++...anything u wud like to sugest?

I would read up on the Info about Gedit in the software center if I was you.

Cheers - :)

---

### Post by bro on 2013-03-10
The htdocs question I answered in your other thread. People start wars over text editors so just go with your own experience. Vim is hard to learn and has many fans. I worked with gedit a long time it has nice collections of snippets too. I now use a none own editor called sublime text 2. It is very good and popular too.

---

### Post by vanadium on 2013-03-10
SciTE Text editor is available in the Software Center.

---

