---
title: "Python Gedit style editor"
date: 2008-09-26
forum: Programming Talk
---

### Post by lunisneko on 2008-09-26
I've been working on a gtksourceview2 style editor based on mike_g's C version here: [http://ubuntuforums.org/showthread.php?p=5790705](http://ubuntuforums.org/showthread.php?p=5790705)

By the way, Gedit uses gtksourceview2 to hilight it's code. This will create universal styles that can be used in Gedit and any others that use it as well.

I just finished 0.3 and would like to share it with anyone who wants it. It supports the main styles and diff: styles. The only gotcha is that it always saves using the File>Save menu and always saves to it's own dir as out.xml. This should be okay for now. Let me know what you think. Edit, View, and Help menus are there for looks right now. Only File>Save and File>Quit work. Try it and let me know.

P.S.
  You'll have to hand-edit the xml file after it's saved with your own author and title information, then copy it to ~/.gnome2/gedit/styles/ and rename it.

What else I want to do with it:
Be able to set all background colors at once.
Automatically install to ~/.gnome2/gedit/styles/
Be able to install universally with gksu
Save as... menu
Open... menu

Probably others :)

Update: Version 0.4
* Save and Save As work properly now.

---

### Post by lunisneko on 2009-08-15
Almost a year later, I've picked this back up. Hooray! Updated to 0.4.

---

### Post by trusktr on 2010-10-25
Almost a year later... This seems really cool! How do i install it?

---

### Post by lunisneko on 2010-11-14
You don't really. Just extract it all and run the main python file. In the future I'll come 'round to doing more to it and I'll add installers, etc.

---

### Post by junior562 on 2011-07-19
I really like what you have done.  I have been using the Gedit style editor for a short time.

I have two questions:

   -- How do you change the font for the sample text?

   -- What would one change to make the color outputs
        be only 6 digits instead of 12?

---

### Post by derekdreery on 2012-02-27
Hi. Would you consider putting it on github (or whatever) so ppl can improve it :). V useful btw

---

### Post by madame on 2012-02-29
Can this be used in other Linux distributions?

---

### Post by trusktr on 2012-12-25
It can be used with *any* Linux distribution provided you install the proper dependencies.

---

