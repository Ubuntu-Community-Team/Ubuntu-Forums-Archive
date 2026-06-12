---
title: "Command completion for CVS commands"
date: 2014-06-03
forum: Programming Talk
---

### Post by ofnuts on 2014-06-03
How does one enable command completion for the "cvs" command in a Bash prompt where it works for all other commands? Or is it just broken?

---

### Post by spjackson on 2014-06-03
It sounds like something's broken. It works on my Ubuntu 10.04 box and I didn't do anything in particular to enable it. I have just installed the cvs package on my 14.04 box and bash completion for cvs works there too.

---

### Post by ofnuts on 2014-06-03
Thanks. Renamed/disabled **[FONT=courier new]/usr/share/bash-completion/completions/cvs[/FONT]** and at least file name completion is back, but I of course prefer a more complete solution.

---

