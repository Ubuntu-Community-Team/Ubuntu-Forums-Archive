---
title: "what applications are available for C++ prog?"
date: 2008-08-12
forum: Programming Talk
---

### Post by ellankavi on 2008-08-12
Pls tell me what appl are avl for C++ prog. I tried codeblocks. but didn't find it easy. i'm looking at something like visual C++ or similar such easy GUI

---

### Post by dwhitney67 on 2008-08-12
You can pretty much use any document editor you want; and IDE is not essential for C++ development, and IMHO, not worth using.

If you want to immediately start developing C++ software, first install the compiler if you have not already done it.  Here's how:
```
$ sudo apt-get install build-essential

```
Then launch 'gedit', which is probably the easiest editor supplied with Ubuntu.  If you are using KDE, then I think it is called 'kedit'.

Insert this program:
[PHP]#include <iostream>

int main()
{
  std::cout << "My first program!" << std::endl;
  return 0;
}[/PHP]
Then save the file (program) as first.cpp.  Then in a terminal, run:
```
$ gcc first.cpp -o first
$ ./first
```
You should see the output of your program.

If you have a book/tutorial, I suggest you go through it to develop ever more complicated example programs so that your quest to learn C++ is satisfied.

Good luck with everything.

P.S.  Most die-hard *nix users use 'vim' for their editing of files/programs.  It is available even when there isn't a window manager running.  Those who can only use graphical editors are screwed if/when a window manager is not present.

---

### Post by pmasiar on 2008-08-12
If you are looking for C++ IDE, see sticky FAQ

---

### Post by finer recliner on 2008-08-12
eclipse

---

### Post by ggaaron on 2008-08-12
Eclipse, Netbeans, KDevelop - all are big IDE programs used by many people. You should choose one that suits you best.

---

### Post by happysmileman on 2008-08-12
> **dwhitney67 said:**
> 
Then launch 'gedit', which is probably the easiest editor supplied with Ubuntu.  If you are using KDE, then I think it is called 'kedit'.

There's "kate" or "kwrite", IMO Kate is better for programming, it has tabs, it's quicker to change the indentation and highlighting options and it can have a terminal open just below your text area, so you can compile and test programs there (assuming it's a terminal based app)

---

### Post by ggaaron on 2008-08-12
Original poster didn't ask for an editor, but for a complete GUI. Kate, GEdit, Vim aren't IDEs, just editors with some features for programmers.

---

### Post by neoguy2012 on 2008-08-12
I don't have much experience with GUI building on Linux, but I have dabbled with wxWidgets and Qt4.  For Qt4, QT 4 Designer was especially easy.  This, combined with QDevelop, provided an environment that matched the simplicity of Microsoft Visual Studio.  If you want to use wxWidgets, use wxGlade for the GUI design.  You can use whatever you'd like for the IDE (personally, I like Kdevelop).

---

