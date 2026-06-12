---
title: "Notepad++"
date: 2009-03-09
forum: Programming Talk
---

### Post by Matuku on 2009-03-09
I've tried asking on the main Notepad++ forums but they seem very slow in responding so I thought I'd probe the mind of the extensive user base here.

How do you get Call Tips (i.e. Function Parameter hints on input) working in Notepad++? I'm trying to get it working specifically for programming in C but they just don't come up when I'm entering the functions.

Also, Auto-indent in version 5.2 seems to be non-existant for some reason; has anyone else encountered this?

---

### Post by cabalas on 2009-03-09
I don't know if you'll get a reply to that question here as notepad++ is a windows only tool.  

That being said have you tried e-mailing their mailing list or dropping into whatever IRC channel the notepad++ devs like to hang out in? That might give you a better shot of getting your question answered.

---

### Post by flannelbum on 2009-05-02
Easier than expected on stock Jaunty 9.04



[LIST=1]
[*]System > Administration >Synaptic Package Manager
[*]Supply password and Quick Search for "WINE" (no quotes)
[*]Mark WINE for installation and Apply
[*] (let the package manager install the dependencies it needs)
[*][Download Notepad++]("http://notepad-plus.sourceforge.net/uk/download.php") (Choose the .zip file once you get to SourceForge)
[*]Extract the zip file
[*]Create a custom application launcher with a custom command of:
[FONT=comic sans ms,sans-serif]wine <path-to-notepad++.exe>[/FONT]
[/LIST]
For instance, I downloaded the npp5.3.1.bin.zip file and it unzipped to the npp5.3.1.bin folder.  My custom application launcher command is:
[FONT=comic sans ms,sans-serif]wine /home/sean/Downloads/npp5.3.1.bin/ansi/notepad++.exe[/FONT][LEFT][COLOR=#000000]
[http://flannelbum.posterous.com/howto-notepad-on-ubuntu-jaunty-via-wine#ixzz0ENxV37Hu&A](http://flannelbum.posterous.com/howto-notepad-on-ubuntu-jaunty-via-wine#ixzz0ENxV37Hu&A)
[/COLOR][/LEFT]

---

