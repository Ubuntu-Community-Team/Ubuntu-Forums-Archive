---
title: "l10n of numbers"
date: 2010-10-04
forum: Programming Talk
---

### Post by worksofcraft on 2010-10-04
I been exploring internationalization and localization... and well, I decide I don't really like having the numbers in my formats not being translated. So I made a new formatting facility that uses template strings that can be localized by gettext and thus render the numbers appropriately.

However not everybody can be bothered to create .po files and install .mo files and all that malarkey, so for those who just wanna see the potential I made this gui program that lets you specify the template set and test the number formatting.

I'll be uploading the new source code soon to [my code.google project]("http://code.google.com/p/speaknumber/downloads/list") althouogh there are lots of unresolved issues still like... should I allow negative indexes for rescaling floating point and I still have a few chapters to write for the HTML documentation. So here I'm attaching a 64 bit and a 32 bit ready compiled prototype for anyone who wants to see what I'm on about... oh and also a screen shot of what it should look like.

---

