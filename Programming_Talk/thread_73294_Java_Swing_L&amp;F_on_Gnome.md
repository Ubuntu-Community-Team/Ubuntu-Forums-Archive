---
title: "Java Swing L&amp;F on Gnome"
date: 2005-10-08
forum: Programming Talk
---

### Post by InfoRital on 2005-10-08
Hello,
I've installed Ubuntu Breezy and Java 1.5.
I've got two questions :
1)I've a big problem : Swing apps doesn't look like normal Swing apps (with the Ocean default look&feel) when i'm on Gnome. They get a GTK (not GTK++) like look&feel and that's quite horrible !
When I'm on KDE, they look like normal.

2)How can i desinstall GCJ/GIJ ? When i try to desinstall GIJ, Synaptic said me that openoffice2 and ubuntu-desktop !! must be removed...

Thanks for your answers and sorry for my english, i'm french.

---

### Post by fjleal on 2005-10-08
[QUOTE=InfoRital]Swing apps doesn't look like normal Swing apps (with the Ocean default look&feel) when i'm on Gnome. They get a GTK (not GTK++) like look&feel and that's quite horrible ![/QUOTE]
To user the default L&F:
```
UIManager.setLookAndFeel(UIManager.getCrossPlatformLookAndFeelClassName());
```
To use the system L&F:
```
UIManager.setLookAndFeel(UIManager.getSystemLookAndFeelClassName());
```

---

### Post by InfoRital on 2005-10-08
Thanks but i know that. The problem isn't in my applications (i don't develop Swing applications) but in applications that i haven't the source code and which are not mine.
For example, when i launch "javaws", it looks like that
[IMG]http://213.251.134.220/~linuxproje/javaws.jpg[/IMG]

---

### Post by fjleal on 2005-10-09
javaws is using the system default L&F, and Sun hasn't come up with a decent GTK look & feel yet, so it's using the "old" GTK widgets design. It's disgusting, you're right! And because the software isn't free, you can't change that behaviour. :(

But that's specific to that application. Other Swing apps. (hopefully) won't follow that regrettable design decision, and won't be bind to a particular L&F. Look for command-line options that may allow you to change the L&F - try executing "<app.> --help" on the CLI to see if there's such an option. On certaing Swing apps. (like the Netbeans IDE) you can pass a parameter to the application to choose the L&F.

;)

---

### Post by InfoRital on 2005-10-09
Thanks for your reply.

Yes some applications follow that design decision and some others don't.
I've found that you can set the defaut L&F for all Java applications. You must make a swing.properties file in the lib/ directory of your jre. And you can set the default l&f in this file.

---

