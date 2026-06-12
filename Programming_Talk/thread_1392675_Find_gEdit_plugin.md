---
title: "Find gEdit plugin"
date: 2010-01-28
forum: Programming Talk
---

### Post by Nonno Bassotto on 2010-01-28
I'm looking for a gEdit plugin, but I don't know how to search because I don't know the name of the feature I need.

It should allow to minimize paragraphs of code, and reopen them clicking on an arrow on the left side.

Detection of beginnning and end of the paragraph should be done either following indentation (for programming languages) or by opening and closing commands (for markup languages).

In particular I what interests me most is the possibility to collapse a single div onto a line, even if the file I am editing is mixed html and php (so it recognized as php as far as evidentation of code is concerned).

Do you know any suitable plugin, or at least the name of the feature? I'm sure it must be quite standard.

---

### Post by cubeist on 2010-01-28
> **Nonno Bassotto said:**
> I'm looking for a gEdit plugin, but I don't know how to search because I don't know the name of the feature I need.

It should allow to minimize paragraphs of code, and reopen them clicking on an arrow on the left side.

Detection of beginnning and end of the paragraph should be done either following indentation (for programming languages) or by opening and closing commands (for markup languages).

In particular I what interests me most is the possibility to collapse a single div onto a line, even if the file I am editing is mixed html and php (so it recognized as php as far as evidentation of code is concerned).

Do you know any suitable plugin, or at least the name of the feature? I'm sure it must be quite standard.

Have you searched through the available gedit plugins page?

[http://live.gnome.org/Gedit/Plugins](http://live.gnome.org/Gedit/Plugins)

If you can't find what you are looking for on that page, you might want to try a dedicated editor such as bluefish or geany.

---

### Post by hessiess on 2010-01-28
Its called code folding, don't know if there is a plug in for GEdit, Im a Vim guy;)

---

### Post by Nonno Bassotto on 2010-01-28
> **hessiess said:**
> Its called code folding, don't know if there is a plug in for GEdit, Im a Vim guy;)


Thank you, I found [Gedit folding]("http://code.google.com/p/gedit-folding/")

---

### Post by delfick on 2010-01-29
I don't believe there is that feature yet and gedit-folding doesn't seem to actually work.

However, hopefully in the future gtksourceview will have it (it's what gedit uses)

[https://bugzilla.gnome.org/show_bug.cgi?id=134610](https://bugzilla.gnome.org/show_bug.cgi?id=134610) :D

---

### Post by Nonno Bassotto on 2010-01-29
gEdit folding actually works for me, even if at the beginning it seemed to do nothing.

Be sure your code is indented. Then place the cursor on the first line of the block you want to fold and press alt+z

---

### Post by delfick on 2010-01-29
hmm, it does too.

how magical :D

---

### Post by physeetcosmo on 2010-02-11
All,

Where do i need to put this python file? i am typically putting third party plugins in:

/home/<usr>/.gnome/gedit 

and then i create a "plugins" folder. 

i can see "Simple Folder" listed in the "Preferences -> Plugins" tab, but when i click to activate it, it just "grays out".

Any ideas?

-Dustin

---

### Post by Nonno Bassotto on 2010-02-12
Try doing this after calling gedit from the terminal and see what the outpu is.

---

### Post by thecoshman on 2011-02-28
> **physeetcosmo said:**
> All,

Where do i need to put this python file? i am typically putting third party plugins in:

/home/<usr>/.gnome/gedit 

and then i create a "plugins" folder. 

i can see "Simple Folder" listed in the "Preferences -> Plugins" tab, but when i click to activate it, it just "grays out".

Any ideas?

-Dustin

You do need to have both the .gedit-plugin and .py file from that site, else like you say it greys it out.

I wouldn't mind something that shows a column down the side next to line numbers with and + or - for when a code block can be expanded or shrunk. And by the looks of this plugin does not save what sections have been shrunk.

I might have a look over it at some stage, see if I can't mod it to allow folded sections to save that they are folded. 

Maybe let it add a comment that on file load it can scan for reapply any folds. This might require a confg window to select what style of comment to use so that it can still work with all languages.

---

