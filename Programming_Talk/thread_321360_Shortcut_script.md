---
title: "Shortcut script"
date: 2006-12-18
forum: Programming Talk
---

### Post by jwest21 on 2006-12-18
I ran across a great tutorial a while back that helped me to install programs via wine.  One of the very helpful hints was about how to write a quick script that would allow you to quickly run a program from wine using a shortcut.  I know it involved a quick script and placing it in a specific folder (I think usr/bin) then just type "dreamweaver" at the command line instead of wine /.wine/c_drive/Program\ Files/Macromedia/Dreamweaver\ 8/Dreamweaver.exe

...or whatever it is.  Hopefully someone can help me out on this.

---

### Post by scxtt on 2006-12-18
an alias could do that ...

edit .bashrc and add:

[indent]alias dreamweaver='wine /.wine/c_drive/Program\ Files/Macromedia/Dreamweaver\ 8/Dreamweaver.exe'[/indent]

then run **source .bashrc** from the command line, you can then type **dreamweaver** from the CLI and have it startup ...

---

### Post by 23meg on 2006-12-18
Open a new document in any text editor, paste the line, save it, make it executable and place it in /usr/bin .

---

