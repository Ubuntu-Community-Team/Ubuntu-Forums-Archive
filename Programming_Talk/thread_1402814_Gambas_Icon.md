---
title: "Gambas Icon"
date: 2010-02-09
forum: Programming Talk
---

### Post by Chamillionaire2 on 2010-02-09
What's Up?

OK, So small question, Is it possible to change the icon of a gambas made executable file?
[COLOR="White"]If you see this, Say bananas, And win a prize![/COLOR]

I tried via Projects>Properties and click on the icon their, But to no avail.

Anyone?

---

### Post by kalaharix on 2010-02-10
hi

Go into the project direcory in Nautilus (the file browser) and <ctrl>h to show hidden files. The icon is .icon.png

Or: right-click on the gambas executable in file browser, properties and click on the icon image.

rgds

---

### Post by Chamillionaire2 on 2010-02-10
When you change the icon via right clicking and properties, It will of course change when it's on someone else's computer, I also tried the .icon.png way, But when I make the executable file it back to its default ugly icon.

Not sure if you can embed a icon in a binary executable? Maybe wrong though.

---

### Post by kalaharix on 2010-02-11
Hi,

You need to make an installation package to automate that (the button is next to the 'make executable' one). I don't have much experience of that: my Gambas is for my own commercial use. From reading the forums, I know it is a bit of a minefield due to the nature of Linux.

Gambas is written is the spirit of Unix and relies heavily on external libraries. These libraries are themselves being updated with time and this can cause problems both within one distro's versions and particularly across different distros.

There was a problem with Ubuntu, for example, where Ubuntu libtool went from ver 1.5 to 2. For a time this caused a problem with with Gambas compilation, now fixed. Across distibutions, the problem is significant.

One serious Gambas user has even resorted to putting the application on a server and using FreeNX to run the clients (with the added advantage that he can run the application from Windows clients). 

If you are installing on a handful of other machines with differing distros, you might find it less frustrating to install Gambas and compile the application on each. Suck it and see.

rgds

---

### Post by raindog469 on 2010-02-11
Which icon are you talking about?  All the programs on my Karmic machine, in /usr/bin and elsewhere, have variations on the same icon when viewed in Nautilus, whether they're shell scripts, Perl scripts, executables or what have you.  If you're trying to change the icon used in Nautilus, can you give me an example of an executable that shows up in Nautilus with a different icon than all the rest?

If you want an icon associated with your program, you'll need to use the menu system, and the Gambas package generator creates a menu entry with your project's icon by default, at least for Ubuntu packages.

---

