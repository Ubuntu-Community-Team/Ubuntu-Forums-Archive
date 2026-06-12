---
title: "How exactly down btdownloadcurses work?"
date: 2007-06-02
forum: Programming Talk
---

### Post by Sp4cedOut on 2007-06-02
Where when you run it in the terminal it takes complete control of that terminal?  I'm using the gnome-terminal if that makes a difference.

---

### Post by blackened on 2007-06-02
I don't think I fully understand your question. If you're wanting to avoid letting it take complete control of the terminal window, then try using screen. This would allow you to start a screen session, then start btdownloadcurses, then detach the screen session leaving the process running with the ability to reattach to it later. I'm fairly sure that screen is included in the base Feisty install, but if not, then you can get it from the repos with sudo apt-get install screen. Check its manual entry for more info.

---

### Post by Sp4cedOut on 2007-06-02
Sorry, what I meant is, how would I write a program that takes control of the console window like btdownloadcurses does.

---

