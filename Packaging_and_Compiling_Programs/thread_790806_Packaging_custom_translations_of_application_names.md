---
title: "Packaging custom translations of application names separately - how?"
date: 2008-05-11
forum: Packaging and Compiling Programs
---

### Post by temcat on 2008-05-11
Hi all, 

not sure if this is the right forum for my question. If not, I will be glad to get any hints on where I should ask it.

I am going to make a private partial localization of Ubuntu for a customer. In addition to GUI strings in application, I will need to translate application names that are displayed in the menus. 

Application names are stored in .desktop files which reside in the main package for each application - unlike GUI strings, which are stored in common language support packages for a specific language. So it appears that to change the names, I would have to either: a) change them directly in the installed .desktop files which creates maintainability problems (an update will destroy my modifications) OR b) repackage all software which I of course would like to avoid. Is there any other way to have custom application name translations in a separate package - preferably involving as little programming a possible?

---

