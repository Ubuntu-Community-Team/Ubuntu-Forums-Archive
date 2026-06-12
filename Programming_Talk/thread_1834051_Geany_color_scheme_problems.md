---
title: "Geany color scheme problems"
date: 2011-08-27
forum: Programming Talk
---

### Post by memilanuk on 2011-08-27
Hello,

Hope I got this in the right place...

i've got Geany 0.20 installed on Ubuntu 11.04 desktop.  I downloaded some color scheme files and copied them into my ~/.config/geany/colorschemes/ directory... but when I restart Geany, I can't change the color scheme from the default (using View -> Editor -> Color Schemes)

The same thing inside a copy of WinXP inside Virtualbox works just fine... what am I doing wrong?

TIA,

Monte

---

### Post by memilanuk on 2011-08-27
BTT... I removed geany, deleted the directory ~/.config/geany/ and then reinstalled geany, and copied the color scheme .conf files back into ~/.config/geany/colorschemes/ and still cannot change the color scheme...

Can someone else with geany installed on 11.04 verify if this is working for them, or if this is a bug that needs filed?

---

### Post by c_wolf on 2011-09-18
Same problem here using Ubuntu 11.04!

Works fine in Debian, haven't tested in Ubuntu 11.10, but I will report if it actually works in the developing 11.10.

I have tried Geany 'schemes' from several different sources on the net, made sure all config files had proper access rights (both in /usr/share/geany and /home/user/.config/geany)

So far just can't get it to work :???: !

Great editor by the way! Using it from now on :D

---

### Post by memilanuk on 2011-09-18
Well, at least now I know its not just me losing my mind ;)

Seems odd that on the Launchpad page for 11.04/Geany there are no options other than the over view...?  The link to the source package shows a 'Bugs' option on that page that works...

---

### Post by c_wolf on 2011-09-18
Just found this page: [http://sourceforge.net/tracker/index.php?func=detail&aid=3193525&group_id=153444&atid=787791](http://sourceforge.net/tracker/index.php?func=detail&aid=3193525&group_id=153444&atid=787791)

That page 'inspired' me to open the file /home/user/.config/geany/geany.conf

Then to change

```
color_scheme=
```
to
```
color_scheme=oblivion2.conf
```

Guess what, this way it works!
Can't switch themes using the GUI, so have to manually edit the geany.conf pointing to  the theme file I'd like (to try).

Note: make sure you don't edit the geany.conf file with Geany itself, otherwise it overwrites any changes you made to when it closes itself ;)

This page has good themes [https://github.com/codebrainz/geany-themes](https://github.com/codebrainz/geany-themes)

:popcorn:

---

### Post by memilanuk on 2011-09-18
Sweet!

Works here too.  I had already downloaded that package of themes - kind of wish they'd just include it as part of the default install for geany - so I copied the files back over to the appropriate directories and went into edit the geany.conf file (using gedit, oh the irony ;) ) and voila, it works.

Now... from the bits and pieces I read in the Geany bug tracker, the cases with problems similar to this have one recurring common theme - Ubuntu or some flavor there of.  So does it make sense that somewhere along the lines the Ubuntu version of Geany is getting b0rked somehow?

Tried submitting a bug report for the Natty/Geany package but after submitting the brief description the page reloaded and came up blank - not sure if thats because I'm stuck at work today and my only internet access is via IE7 or if there is a larger issue with the bug report system...?

---

