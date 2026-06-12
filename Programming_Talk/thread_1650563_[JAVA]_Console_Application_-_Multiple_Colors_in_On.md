---
title: "[JAVA] Console Application - Multiple Colors in One Line"
date: 2010-12-21
forum: Programming Talk
---

### Post by AAndrew on 2010-12-21
Hey, I was just wondering how to use multiple colors in one line in Java. I know it's possible, but I've had no luck finding it on Google.

To be more specific, I want it to look something like this...

[SIZE="1"](I couldn't think of a better example, so I just used a screenshot from one of my favorite MUDs. ;))[/SIZE]
[img]http://i104.photobucket.com/albums/m178/hamsteroid/aardwolf.gif[/img]

Thanks,
-Andrew

---

### Post by myrtle1908 on 2010-12-22
Pretty sure there is no native support in Java.  For this requirement one gerenally uses ncurses via JNI.

Look here [http://sourceforge.net/projects/javacurses/](http://sourceforge.net/projects/javacurses/)
and here [http://roguebasin.roguelikedevelopment.org/index.php?title=Java_Curses_Implementation](http://roguebasin.roguelikedevelopment.org/index.php?title=Java_Curses_Implementation)

However, you could do it all in Swing and *fake* a terminal with a JFrame etc.

---

