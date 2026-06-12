---
title: "Java GUI Q"
date: 2007-02-22
forum: Programming Talk
---

### Post by derby007 on 2007-02-22
Quick Q: hopefully a quicker answer will result....... i'm currently using Netbeans in Ubuntu for my little project. I dont understand why i get 2 different screen displays/look-n-feel when I:
 1) hit PREVIEW WINDOW in Netbeans, i get the Gnome settings/look-n-feel
 2) hit RUN the program, F6, and i get Java settings/look-n-feel 

Any ideas, i hope its something simple, maybe to do with 'javax.swing.UIManager' ??

---

### Post by MadMan2k on 2007-02-22
UIManager.setLookAndFeel(UIManager.getSystemLookAndFeelClassName());

---

### Post by derby007 on 2007-02-22
cheers, i was close to an answer so....

---

### Post by Fasga on 2007-02-22
There's also Java-Gnome ([http://java-gnome.sourceforge.net/)](http://java-gnome.sourceforge.net/)), however, I'm not sure if it has any benefits over MadMan stated.  Then, of course, there's SWT, which I've never really liked.

---

