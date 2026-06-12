---
title: "Anjuta and working glade plugin on Edgy?"
date: 2006-11-21
forum: Programming Talk
---

### Post by naxcz on 2006-11-21
Hi, I can't discover which combination of deb packages unlock for me support of Glade in Anjuta. I have installed and removed all versions of glade (and gnome-glade) in repositories, but still get only grayed checkbox in Anjuta plugin list for glade plugin. What do I do wrong?

Thanks a log

---

### Post by llonesmiz on 2006-11-21
That plugin isn't functional yet in anjuta. I think developers may have started implementing it in the cvs or svn but I'm not sure.

---

### Post by slavik on 2006-11-21
well, with 2.0.2 source, I got as far as ./configure and get everything except valgrind, but when I compile I get more trouble.

Valgrind 3.2.0 is the one included in edgy and there is no dev. When I try to build (compile) Valgrind 3.2.1 I get errors that are supposedly fixed with CFLAG of -gno-stack-protector, but somehow ./configure won't take it or I am doing something wrong (more likely), I also don't know what a -dev package exactly is nor how to make it.

for Glade, there is an error about a function not receiving enough parameters, the function is glade_app_paste_command(); which looks similar to all other functions in the plugin.c file for glade but I can't find the .h for glade to see what is wrong.

If these 2 problems get solved, I know that I can compile anjuta 2.0.2 with ALL plugins. :)

---

