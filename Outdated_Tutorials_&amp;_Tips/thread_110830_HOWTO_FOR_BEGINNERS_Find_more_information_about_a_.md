---
title: "HOWTO FOR BEGINNERS: Find more information about a program or file."
date: 2005-12-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Refrozen on 2005-12-31
Hello,

I figured to get used to writing howto's I'd write one for the absolute beginner.

Ubuntu, and, Linux in general come with a program called `[man](http://manlib.com/man/501)`. Man searches your man paths, most notably /usr/local/man and /usr/share/man for man pages (see  /etc/manpath.config or just run [manpath](http://manlib.com/man/501) at the terminal).

Manpages are organized in to "sections", which are based on what they contain:

[quote=Output from man man]
       1   Executable programs or shell commands
       2   System calls (functions provided by the kernel)
       3   Library calls (functions within program libraries)
       4   Special files (usually found in /dev)
       5   File formats and conventions eg /etc/passwd
       6   Games
       7   Miscellaneous (including macro packages  and  conventions),
           e.g. man(7), [groff](http://manlib.com/man/500)(7)
       8   System administration commands (usually only for root)
       9   Kernel routines [Non standard]
[/quote]

To view a manpage, go to a terminal and type `man [entry name]` to search all sections, or `man [section] [entry name]` to search a specific section.

If you want to link to a man page, you can find it on [www.manlib.com](www.manlib.com) for the majority of the common ones, or just Google for `man [command]` and you'll find a web-resource.



Another way to find information, albeit, more simply, is apropos ([man apropos](http://manlib.com/man/356)). `Apropos [command]` lists any apropos entry which contains the string "command" and returns quick information on how to use it. On Ubuntu, apropos searches the man database, however, on many Linuxes, apropos searches the whatis database. 

whatis' database is created with the [makewhatis](http://manlib.com/man/974) command.

If the comamnd you're searching for is a program, you can try [command] --help or -h at the terminal to catch more information. --verbose or -v is sometimes helpful as well.

I hope you found this useful :) :KS :KS

---

