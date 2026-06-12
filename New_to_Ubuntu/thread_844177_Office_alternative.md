---
title: "Office alternative"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-06-29
Hy all

I have... kind of a problem with open-office.It doesn't display the word documents correctly.Here is a screen shot to see what I mean...
I don't know why it displays the black...things and why for each space it display a dot...
I heard about other office suites, like Applixware EIOffice KOffice StarOffice and  ThinkFree Office.Are this better then open-office?

---

### Post by lisati on 2008-06-29
> **Troll_the_Great said:**
> Hy all

I have... kind of a problem with open-office.It doesn't display the word documents correctly.Here is a screen shot to see what I mean...
I don't know why it displays the black...things and why for each space it display a dot...
I heard about other office suites, like Applixware EIOffice KOffice StarOffice and  ThinkFree Office.Are this better then open-office?
The black things are "end of paragraph" markers, and don't normally get printed. They can be turned off with one of the options. The first place to check is on Office's "View" menu, and seeing if "non-printing characters" is checked.

---

### Post by NikS on 2008-06-29
Ya,
those things dont get printed, they r just for us to get clear idea of the formatting, unnecessary spaces, pagebreaks, newlines etc!!!

U can turn them off thru otions!!

---

### Post by Troll_the_Great on 2008-06-29
Silly me...:) Thx for the answers.
And another thing.I use often MathType (in Windows) for creating formulas, but open-office doesn't seem to recognize them.When I click on them it says "General Error".Any ideas how can I fix it, and create formulas in open-office?

---

### Post by Troll_the_Great on 2008-06-29
Should I try to install MathType using wine?Will it work in open-office?

---

### Post by Chr0mis on 2008-06-29
You can use MathML: [http://www.w3.org/Math/Software/mathml_software_cat_editors.html](http://www.w3.org/Math/Software/mathml_software_cat_editors.html)

---

### Post by Troll_the_Great on 2008-06-29
I couldn't find what I need.Can someone give me a direct link to a debian package and tell me how to use the soft with open-office or abiword (or any other office suite)?
Thanks!

---

### Post by philinux on 2008-06-29
In open office writer, Insert>Object>Formula

---

### Post by soccerboy on 2008-06-29
> **philinux said:**
> In open office writer, Insert>Object>Formula

Same thing here.  I use open office writer.
Also, if you are not incredibly fond of doing formatting yourself, try LyX Document processor.  It runs on LaTeX and has excellent math formula support.  Multiplatform and outputs in pdf documents or postscript.

it's in the repos

```
apt-get install lyx
```

---

### Post by Victormd on 2008-06-29
> **Troll_the_Great said:**
> I couldn't find what I need.Can someone give me a direct link to a debian package and tell me how to use the soft with open-office or abiword (or any other office suite)?
Thanks!

Why not use Openoffice Formula?

---

### Post by kellemes on 2008-06-29
[GNOME_Office]("http://live.gnome.org/GnomeOffice")

---

### Post by Troll_the_Great on 2008-06-29
Lyx doesn't work...Here is what i get when I try to run it:

```
lyx
QPaintEngine::setSystemClip: Should not be changed while engine is active
QPaintEngine::setSystemClip: Should not be changed while engine is active
QWidgetPrivate::beginSharedPainter: Painter is already active

lyx: SIGSEGV signal caught
Sorry, you have found a bug in LyX. Please read the bug-reporting instructions in Help->Introduction and send us a bug report, if necessary. Thanks !
Bye.
Aborted
```

And with open-office formula, how can I create complicate formulas, like these in the screen shot?
I didn't see any functions (like in Mathtype):square roots, sums, fractions and so on.What can I do?

---

### Post by Troll_the_Great on 2008-06-30
Nobody? :(

---

### Post by Bloch on 2008-06-30
Insert > Object > Formula

and take a look through it.

If you click on the openoffice Help > openoffice help menu 
and at the top left tab choose
Openoffice.org Math
it will give you an intro and examples.

---

### Post by hardyn on 2008-06-30
install msttcorefonts for better compatibility with word... the windows base fonts, arial, times etc.

---

### Post by Troll_the_Great on 2008-06-30
Hy all.Thanks for your answers till now.
I found Kformula, and it resembles very much to MathType.The only problem is...I don't know how to use it!:(:(:( In Microsoft Word,I would start MathType, type a formula and then Ctrl+S and the formula would appear in the document.Here, when I try to save something, Kformula tries to save it as a file.How can I save formulas inside am open-office document?

---

### Post by hardyn on 2008-06-30
Insert > object > formula.

it opens a windows in the bottom of the screen, you then use the mouse and click away like you do in word... or learn the script language (mathml) and then key it all in which is WAAAAAAAY faster.  It is a very easy markup language to learn.  the mouse clicks simply print the function into the text window, so if you need a hint getting started it will help alot.

the formula will be placed at the cursor position.

---

### Post by Troll_the_Great on 2008-07-01
Thank allot hardyn for your tip, but how can I get open-office to recognize MathType formulas?I already checked that box in "Preferences", but when I try to open a formula it says "General Error" (see my previous posts).And I would also be happy it somebody would tell me about how to work with Kformula, it seems easier.
Cheers!

---

### Post by Mornedhel on 2008-07-01
KFormula is part of KOffice, so you would use that preferably from within KWord (also part of KOffice). But all these are KDE-oriented, and it's safe to assume you're using Gnome.

The OpenOffice formula editor tries its best to open and edit MathType formulas, but may sometimes choke (reverse-engineering is NOT easy). Does this happen on *every* formula you try it on ?

Finally, if you're looking for alternatives to OpenOffice, the two main contestants on Ubuntu are KOffice for KDE (already mentioned) and gnome-office (for Gnome...).

gnome-office only includes a document editor and a spreadsheet editor. It is really light and loads very fast.

KOffice is more complete as it also includes a scalable graphics program, a bitmap graphics program, and a slide editor (think PowerPoint). They all seem to be usable, but I haven't tried anything fancy with them.

Both are compatible with the 97-to-XP MS Office suite (as OOo is).

---

### Post by hardyn on 2008-07-01
unless the expressions are really complex, you can probably retype them in OOo faster than you can convert them... the mathml is really slick.

---

