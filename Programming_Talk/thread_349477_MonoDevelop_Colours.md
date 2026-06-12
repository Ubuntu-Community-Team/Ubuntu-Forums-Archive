---
title: "MonoDevelop Colours?"
date: 2007-01-30
forum: Programming Talk
---

### Post by kian_ronan on 2007-01-30
I have a particular colour configuration that I use for all my editors, mostly consisting of green on a black background.  I've used this configuration for what feels like forever and a day between Emacs, then Eclipse and recently VS.NET 2003.

There's a very good reason for this kind of colour scheme.  I work mostly on a *tiny* laptop, with limited resolution and limited brightness.  I happily throw this thing into my bag and carry it everywhere since it weighs bugger all.  The negative colour scheme helps avoid problems such as light reflections, and I find it easier on my eyes over a longer period of time.



Now I appear to have something of a conundrum.  MonoDevleop, for which I have been impressed so far, only allows me to change the colour of the *text* in the editor.  This is fine and dandy, but nowhere can I find an option to change the background colour.  Am I missing something here, or is there some estoric setting hidden away in an XML file that I can tweak to switch the editor background to black?

Many Regards,


Kian Ryan

---

### Post by pkkid on 2008-04-29
Anyone ever figure this out?

---

### Post by TibetHiker on 2008-04-30
> **pkkid said:**
> Anyone ever figure this out?

nop, searched all setting itmes in [Preferences] found no solution...

---

### Post by pkkid on 2008-05-01
Thats too bad, I was really hoping to use this editor full time, and it seems like something one of the dev guys could fix in 5 minutes.  The best I could come up with was using CompizFusions inverse color option.  

For me its "Win + n"

---

### Post by lifusion on 2008-10-20
Have you looked at: [http://mjhutchinson.com/journal/2007/11/07/gtksourceview_2_monodevelop](http://mjhutchinson.com/journal/2007/11/07/gtksourceview_2_monodevelop) ?

---

### Post by pkkid on 2009-05-02
Yep, to finish off this thread, MonoDevelop2 in Ubuntu 9.04 fixes this issue using the same system for colors as the built in gedit. :)

---

### Post by zourtney on 2009-09-05
> **pkkid said:**
> ...MonoDevelop2 in Ubuntu 9.04 fixes this issue using the same system for colors as the built in gedit. :)

If this is the case, I must be doing something wrong. Editing gedit preferences made no difference. Do I need to explicitly define colors for a *.cs file?

I did get this to work by creating my own theme file. These are just simple XML files which can be imported via the MonoDevelop UI by going to Edit > Preferences > Text Editor > Syntax Highlighting. Several pre-existing themes are shown there.

I am not sure where those theme XML files are stored, but you easily find them on the MonoDevelop SVN, [here]("http://anonsvn.mono-project.com/viewvc/branches/monodevelop/main/2.0/src/addins/Mono.Texteditor/Styles/").

The files are pretty straight forward and can be imported via the UI dialog box. Only one word of caution: it seems that the filename MUST end in "Style.xml" Without "Style" appended, I never got it to read the file.

I did a quick write up on my site, [here]("http://randomland.net/tech/custom-monodev-theme").

*Edit 10-18-2009: Sorry, the link was broken. It is fixed now.*

---

### Post by nsk7even on 2011-04-22
Does no one have the problem of not being able to read the parameters of a method in the MonoDevelop tooltip?
Because they are printed dark blue (standard link color) and the tooltip background is black.

I solved this with the Gnome Color Chooser ... just if anyone else has this issue.

---

