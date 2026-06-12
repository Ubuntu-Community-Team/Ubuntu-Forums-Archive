---
title: "Glade Interface Translation Output Input"
date: 2006-09-21
forum: Programming Talk
---

### Post by Malac on 2006-09-21
I have a python application which extracts the "translatable" labels from a Glade file. 
Let's you enter translations.
Then rebuilds the Glade file with the translations inserted instead.
I thought I'd post it here as I don't know where else to put it.
It's written in Python and it's called [COLOR=Red]GITOI[/COLOR] - [COLOR=Red]G[/COLOR]lade [COLOR=Red]I[/COLOR]nterface [COLOR=Red]T[/COLOR]ranslation [COLOR=Red]O[/COLOR]utput [COLOR=Red]I[/COLOR]nput
Run the program, load [COLOR=Olive]<gladefilename>[/COLOR] hit the extract button, save gitoi file
It creates translation files with a .gitoi extension with the text in as follows:
```
#DO NOT REMOVE THESE LINES
#TRANSLATION TEXT TO BE PLACED AFTER THE |><| SYMBOLS
#DO NOT TRANSLATE [crlf] THESE ARE FOR MULTI-LINE LABELS
#
Original GLADE File|><|
Load Original GLADE file|><|
GITOI File|><|
Extract To GITOI|><|
Save GITOI File|><|
Load GITOI File|><|
Translate to GLADE|><|
Translated GLADE File|><|
Save Translated GLADE File|><|
```These can be sent off to translators or put with Glade projects for people to translate.
Just place the translations after the |><| symbol and save the file.
Then the file can be loaded and the translation inserted into a new file called [COLOR=Olive]<gladefilename>[/COLOR]_gitoi.glade.
The "_gitoi" part can then be changed to _fr, _de, etc. depending on the translation.

Here is a screenshot:
[ATTACH]16067[/ATTACH]
I hope this is the right place to put this and that it proves useful to someone.

---

### Post by Malac on 2006-09-27
New Version 1.0 uploaded 27th September 2006.

---

### Post by Malac on 2006-12-12
Added a .deb file, Tuesday, 12 December 2006.
Hopefully making it easier to install, remove or upgrade.

---

### Post by ivlivs on 2008-01-21
Would be interesting, but does nothing for me. Could you please post the dependencies?

---

### Post by ivlivs on 2008-01-22
Needs these three packages to run on Fluxbuntu:

[I]python-gconf
python-gnome2
python-gmenu[/I]

---

