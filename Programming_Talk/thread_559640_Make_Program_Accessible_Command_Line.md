---
title: "Make Program Accessible Command Line"
date: 2007-09-25
forum: Programming Talk
---

### Post by Black Mage on 2007-09-25
I noticed that some programs like wine and eclipse are accessible just by typing that in the terminal. How do I make other programs, like VMserver Server Console accesible in the same way?

---

### Post by Compyx on 2007-09-25
By typing the appropriate command in a terminal-emulator. You can look at the launcher in your menu and see what command is called with that launcher.

Reading the manual would also be quite helpful.

---

### Post by Black Mage on 2007-09-25
Where is the Launcher? I don't see it in Prefences or Administration.

---

### Post by Compyx on 2007-09-25
The launcher is the button / menu item you click when you start that program.

For example, suppose I'd like to see what command is issued to start 'Blackjack':

I'd right-click on the menu bar 'Applications' and select 'Edit Menus', then in the new screen that pops up I'd select 'Games' on the left and then right-click 'Blackjack'.

There you'll see the launcher properties of Blackjack, which tells us the blackjack binary (or a symlink) resides in /usr/bin and is called 'blackjack'. So in the terminal I would type blackjack.

---

### Post by Black Mage on 2007-09-25
Got it, thnx a lot.

---

### Post by Compyx on 2007-09-25
You're welcome, glad I could help.

---

