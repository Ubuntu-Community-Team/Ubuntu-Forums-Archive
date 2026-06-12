---
title: "Disable All Font Replacement"
date: 2013-10-20
forum: New to Ubuntu
---

### Post by Danny_Michel on 2013-10-20
I want to disable all font replacement such as Arial with something else, Helvetica with something else etc.

---

### Post by iloutzu on 2013-10-21
Do you have the core Microsoft fonts installed? They come when installing the ubuntu-restricted-extras package, or you can just add them using
```
sudo apt-get install ttf-mscorefonts
```
This installs the following fonts:
 [LIST]
[*]Andale Mono
[*]  Arial Black
[*]  Arial (Bold, Italic, Bold Italic)
[*]  Comic Sans MS (Bold)
[*]  Courier New (Bold, Italic, Bold Italic)
[*]  Georgia (Bold, Italic, Bold Italic)
[*]  Impact
[*]  Times New Roman (Bold, Italic, Bold Italic)
[*]  Trebuchet (Bold, Italic, Bold Italic)
[*]  Verdana (Bold, Italic, Bold Italic)
[*]  Webdings
[/LIST]

---

