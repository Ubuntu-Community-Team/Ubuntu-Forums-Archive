---
title: "Installing Prolog"
date: 2006-04-12
forum: Programming Talk
---

### Post by opticyclic on 2006-04-12
I tried to install the SWI-Prolog RPM from here [http://www.swi-prolog.org/dl-stable.html](http://www.swi-prolog.org/dl-stable.html) using alien to convert to a deb

However, I am having troubles running it.
I cant find it in the menus and when I type 'pl' in a terminal I get > pl: error while loading shared libraries: libgmp.so.3: cannot open shared object file: No such file or directory


Does anyone here use Prolog?
Anyone managed to install it?

Anyone fancy trying to install it on their system from the SWI site to help me out? ;)

---

### Post by toojays on 2006-04-13
SWI Prolog and GNU Prolog are both available in the universe repository. You should install them using synaptic or apt-get.

---

### Post by opticyclic on 2006-04-13
It was late and I was only looking for it using Gnome App Install (Add/Remove Programs).

Why does Synaptic have a greater list?
I thought they shared the same repository list. :confused:

Maybe it is just that the search is better using synaptic.  :-k

Anyway. I got it going. Thanks.

---

### Post by toojays on 2006-04-13
Add/Remove applications is a more newbie-friendly version of Synaptic. I don't think it shows command-line applications. It is a nice way for the average home user to install packages. The universe repository has over 15,000 packages in it, and it's difficult for a regular user to deal with so much choice, especially when they don't know what each program is for.

---

### Post by opticyclic on 2006-04-14
Thanks toojays.

In case anyone is interested in Prolog and like me doesn't like the widgets used to create XPCE (SWI IDE) there is a nicer solution.

If you install Anjuta you can run SWI in the integrated terminal and get a half decent Prolog IDE.

---

### Post by fre4k on 2006-09-09
I installed swi-prolog via synaptic, but how do i get the GUI running. I get the prompt when i type prolog in the shell.

---

### Post by opticyclic on 2006-09-10
Have you tried running it from inside Anjuta?
The other option is to install SWI and SWI Prolog Editor ([http://lernen.bildung.hessen.de/informatik/swiprolog/indexe.htm](http://lernen.bildung.hessen.de/informatik/swiprolog/indexe.htm)) under WINE.

---

### Post by HerliMenezes on 2009-04-14
HI, can I use Anjuta as an IDE for SWI-prolog?

---

### Post by HerliMenezes on 2009-04-19
I got a somewhat different problem. How can I run graphical tracer under ubuntu?
it's part of xpce package, but I cant  run it. any guess?

---

### Post by m42h31 on 2009-07-24
try running **apt-cache search prolog**
gpp - a general-purpose preprocessor with customizable syntax
gprolog - GNU Prolog compiler
gprolog-doc - documentation for the GNU Prolog compiler
highlighting-kate-doc - library documentation for highlighting-kate
libghc6-highlighting-kate-dev - syntax highlighting library based on Kate syntax descriptions
libghc6-highlighting-kate-prof - highlighting-kate library with profiling enabled
prolog-el - Emacs major mode for editing Prolog code
python-pyke - Prolog-inspired Python logic programming toolkit
python-pyke-doc - Prolog-inspired Python logic programming toolkit (documentation)
source-highlight - convert source code to syntax highlighted document
swi-prolog - ISO/Edinburgh-style Prolog interpreter
swi-prolog-clib - SWI-Prolog interface to system libraries
swi-prolog-doc - Documentation for SWI-Prolog interpreter and XPCE
swi-prolog-http - HTTP libraries for SWI-Prolog
swi-prolog-odbc - ODBC library for SWI-Prolog
swi-prolog-semweb - SWI-Prolog library for manipulating RDF triples
swi-prolog-sgml - SGML/XML/HTML parser for SWI-Prolog
swi-prolog-table - External table library for SWI-Prolog
swi-prolog-xpce - User interface library for SWI-Prolog
yap - The YAP Prolog System

**apt-get install gprolog swi-prolog **

---

### Post by opticyclic on 2009-07-24
Apparently another option now available is to use Netbeans
[http://platform.netbeans.org/tutorials/60/nbm-prolog.html](http://platform.netbeans.org/tutorials/60/nbm-prolog.html)

[http://hulles.supersized.org/pages/geewhiz.html](http://hulles.supersized.org/pages/geewhiz.html)

Haven't tried it myself as I am only programming Java now (using Netbeans also :))

---

