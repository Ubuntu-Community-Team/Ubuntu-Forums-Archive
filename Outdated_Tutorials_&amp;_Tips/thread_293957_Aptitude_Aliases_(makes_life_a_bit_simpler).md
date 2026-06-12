---
title: "Aptitude Aliases (makes life a bit simpler)"
date: 2006-11-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Koori23 on 2006-11-05
I get sick of typing "aptitude install foo" or "aptitude upgrade".. If you're in the same boat as me and don't do these things by the point a click method.. These aliases might help you. 

1. for Gnome type > sudo gedit ~/.bashrc
for KDE type > sudo kate ~/.bashrc

go to the end of the file and copy this text:

> 
# aptitude aliases
alias agi='sudo aptitude install'
alias agu='sudo aptitude update'
alias agd='sudo aptitude dist-upgrade'
alias agc='sudo aptitude clean'
alias agac='sudo aptitude autoclean'

Save it and exit the terminal.

now, whenever you want to install/update just type *agi foo* or *agu *enter* type in your password and away you go.

---

