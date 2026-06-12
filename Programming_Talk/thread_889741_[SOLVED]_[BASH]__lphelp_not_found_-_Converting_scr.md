---
title: "[SOLVED] [BASH]  lphelp not found - Converting script for Ubuntu"
date: 2008-08-14
forum: Programming Talk
---

### Post by mike_g on 2008-08-14
I'm trying to compile the drivers for a Star TSP100 printer in Ubuntu. When I run make it compiles the source ok, but I get an error when it tries to create the docs:
> #get ppd options via lphelp
lphelp ppd/sp512.ppd >> docs/sp512-options.txt
/bin/sh: lphelp: not found
make: *** [sp512-options.txt] Error 127
From what I can tell it seems that lphelp is a red hat thing (tho maybe I'm wrong). 

Anyway I opened the makefile and it does this:
```
docs: $(lphelpdocs)

$(lphelpdocs): %-options.txt: %.ppd
	@if [ ! -e docs ]; then echo "mkdir docs"; mkdir docs; fi
	#get ppd options via lphelp
	lphelp $< >> docs/$@
```
If possible I want to convert the lphelp bit to something that does the equivalent on Ubuntu. Anyone know how I can do this?

Cheers.

Edit: Actually I dont need to do this any more; found out that someone has been here before and converted the scripts for debian.

---

