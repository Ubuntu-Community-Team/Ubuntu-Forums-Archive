---
title: "leafpad  13.04"
date: 2013-07-01
forum: New to Ubuntu
---

### Post by ub9876 on 2013-07-01
why is it thought that a text editor is the better way to edit some terminal code???
why is it better than just typing in the terminal box and saving..???
does Leafpad have a edit feature that I am unaware of that makes it better to edit with  it???

---

### Post by grahammechanical on 2013-07-01
The terminal is just a shell for running commands. There are commands that will print or echo the contents of a file to the terminal. But to edit that file we need to run a command that loads an editor. Once upon a time all programs were loaded by commands in a terminal but it was only possible to run one program at a time. Linux had an advantage over Microsofts DOS. It had multiple terminals called consols or tty. So, a different program could be run by loading them into different consols.

So, in answer to your first two questions - because it is easier to do it that way with less of a risk of typing errors that would wreck the OS.

Regards.

---

### Post by vasa1 on 2013-07-01
> **ub9876 said:**
> why is it thought that a text editor is the better way to edit some terminal code???
why is it better than just typing in the terminal box and saving..???
does Leafpad have a edit feature that I am unaware of that makes it better to edit with  it???
What is your real question?

Leafpad is just like Notepad in Windows.

Lubuntu (if that is what you're using) also has nano by default if you prefer.

---

### Post by ub9876 on 2013-07-01
it sounds like you need an editor to change code. But I dont use it and have had no problems . And I dont see any dropdown selection that says use this to edit code. So I am asking why is it safer to type into an editor and then paste it in the code....as opposed to just typing it into the code in the terminal box..???

---

### Post by redmk2 on 2013-07-01
> **ub9876 said:**
> it sounds like you need an editor to change code. But I dont use it and have had no problems . And I dont see any dropdown selection that says use this to edit code. So I am asking why is it safer to type into an editor and then paste it in the code....as opposed to just typing it into the code in the terminal box..???

Yes you need a text editor to edit a file.  That editor does not need to be graphical.  The editors: ed, emacs, vim and nano are terminal based.  The editors: gedit, leafpad  and even Libre Office Writer are graphical editors.  Are you using a terminal based editor?  What command do you use to do what you are doing?

---

### Post by JKyleOKC on 2013-07-01
> **ub9876 said:**
> it sounds like you need an editor to change code. But I dont use it and have had no problems . And I dont see any dropdown selection that says use this to edit code. So I am asking **why is it safer to type into an editor and then paste it in the code**....as opposed to just typing it into the code in the terminal box..???If you are simply entering commands in the terminal, the only reason for doing it this way is to give you a chance to make sure that you have not made a typing error that could destroy your system by wiping the disk clean of all data. We could give examples of such an error -- but forum rules prohibit it because a few folk would try it and then complain about losing all their data.

However you can get the same advantage by simply taking the time to examine your typed command very carefully, before hitting the ENTER key. The machine will not do anything at all until you hit ENTER, so it's just as safe to do it this way.

The editor is needed only if you want to change an existing script.

---

### Post by dannyboy79 on 2013-07-01
> **ub9876 said:**
> why is it thought that a text editor is the better way to edit some terminal code???
why is it better than just typing in the terminal box and saving..???
does Leafpad have a edit feature that I am unaware of that makes it better to edit with  it???first, what do you consider "terminal code"?
first we maybe need to clarify your terminology. what do you consider the terminal box? how would you "save" in a terminal box and what would you "save" it as?

leafpad is a GUI text editor for linux (there's also Gedit (gnome) and Kate (KDE), just like notepad is a text editor for windows.

---

### Post by newb85 on 2013-07-01
Indeed.  A text editor is needed for editing text files (to be as profound as possible).  If you're changing configuration files, you need a text editor, whether it's graphical, curses, or simply command-line.  If you're entering terminal commands, you can simply type them in the terminal.  You could type them in a text editor, a word processor, or many other applications that allow typing and then copy and paste them to the terminal.  But I can see little benefit to that.

---

