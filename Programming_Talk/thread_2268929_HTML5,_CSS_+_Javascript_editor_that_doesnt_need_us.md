---
title: "HTML5, CSS + Javascript editor that doesnt need us to remove linux-generic"
date: 2015-03-12
forum: Programming Talk
---

### Post by Zendon on 2015-03-12
Yo whats the craic team?

Been Googling and Goolging. Trying to install software. Everything I try to install asks me to remove a few things like linux-generic. My computer keeps giving me errors when I try to remove this.

What is the simplest editor for HTML5, CSS and Javascript? 
Does not need at fancy visual tools. I will write the code myself.
Something to check syntax errors would be cool.

Even somethig like notepad plus for Ubuntu would be a start in the write direction.

Physically my computer is crap, and my LInux abilities arent good enough to make sure all the software is working. Longterm plan is to get new computer.

---

### Post by Zendon on 2015-03-12
I tried installing notepadplus but it doesnt work.
[http://sourcedigit.com/13031-install-notepadqq-notepad-text-editor-ubuntu-14-04-linux-mint-17/](http://sourcedigit.com/13031-install-notepadqq-notepad-text-editor-ubuntu-14-04-linux-mint-17/)

You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.13.0-46-generic : Depends: linux-image-3.13.0-46-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.13.0-46-generic but it is not going to be installed
 notepadqq : Depends: notepadqq-common (>= 0.45.1-0~trusty1) but it is not going to be installed
             Depends: notepadqq-common (< 0.45.1-0~trusty1.1~) but it is not going to be installed

---

### Post by Dimarchi on 2015-03-13
Any text editor is suitable. Gedit (under the guise of Text Editor or something like that)...Nano for terminal based text editors (or Vim, if Nano does not cut it). These come with Ubuntu, so you should not need to install them, iirc.

---

### Post by flaymond on 2015-03-14
[QUOTE=Dimarchi]Any text editor is suitable. Gedit (under the guise of Text Editor  or something like that)...Nano for terminal based text editors (or Vim,  if Nano does not cut it). These come with Ubuntu, so you should not need  to install them, iirc.[/QUOTE]

Like mentioned above, any text editor is find really. Gedit and Mousepad might be your choice for a simple graphical text editor. Otherwise, if you don't like these GUI text editor, you can try vim and nano. I prefer to use text editor if you are learning the markup/scripting languages. Anyway, if you working on a project and need to get the job done, fast, try IDE instead of text editor. I suggest you to try out **Geany** (I'm not gonna say it's an IDE, but's it's a bit like it and simple and also fast) and **Bluefish Editor** (This is the IDE if you want to solve the problem fast). 

Thanks

---

### Post by Holger_Gehrke on 2015-03-14
If any and all 'apt-get install' attempts throw messages like the one you quoted, then there's something wrong with your package database. You should really follow up on the advice the package manager gave you and correct the problem by running
```

sudo apt-get install -f

```

Do an update of the package list(s) and any pending package upgrades after that with
```

sudo apt-get update
sudo apt-get upgrade

```
and the try the installation again.

---

