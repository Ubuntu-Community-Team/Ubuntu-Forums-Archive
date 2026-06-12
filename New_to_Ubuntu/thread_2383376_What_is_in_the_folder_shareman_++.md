---
title: "What is in the folder /share/man/ ++?"
date: 2018-01-24
forum: New to Ubuntu
---

### Post by mac187 on 2018-01-24
I had an older version of mongo db, have now installed the latest version of mongodb, my question is when i type 'whereis mongo db' command,
i get this output:

mudasar@Mudasar:~$ whereis mongo db
mongo: /usr/bin/mongo /usr/share/man/man1/mongo.1.gz
db: /usr/share/man/man3/db.3.gz


anyone can tell me what is in the man folders? 

Thanx :)

---

### Post by steeldriver on 2018-01-24
Files containing the on-line manual pages for the command (`man mongo`) - from `man whereis` :

```

DESCRIPTION
       whereis locates the binary, source **and manual files** for  the  specified
       command  names. 

```

See also [URL="https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard"]Filesystem Hierarchy Standard
[/URL]HTH

---

### Post by TheFu on 2018-01-24
man directories have the built-in help pages for every command on the system.  
If you use **man man**, how they are laid out is explained.
```

       The table below shows the section numbers of the manual followed by the
       types of pages they contain.

       1   Executable programs or shell commands
       2   System calls (functions provided by the kernel)
       3   Library calls (functions within program libraries)
       4   Special files (usually found in /dev)
       5   File formats and conventions eg /etc/passwd
       6   Games
       7   Miscellaneous  (including  macro  packages  and  conventions), e.g.
           man(7), groff(7)
       8   System administration commands (usually only for root)
       9   Kernel routines [Non standard]

       A manual page consists of several sections.
```
Above is from the man manpage. ;)

manpages have a specific layout. It takes a little time to understand, but it is brilliant. It shows the most commonly needed information at the top.  A few different tools will access specific parts for searching and summaries.  **apropos** is one.  You can learn more about that with 'man apropos'

If you use firefox, there is a manpage for it that shows the different command line options and has some tips.  It isn't very good.  The manpages for ssh and rsync are fantastic.  I learn something new every re-re-read.  Most config files have manpages too - **man ssh_config** is pretty good.  **man fstab** isn't great, but it does explain what each part of the file does.

manpages have been around 40+ yrs - well before google. ;)  Plus the manpage on your system is the correct version that matches the command version on there.  Options change, so website manpages don't always have the correct version for your system. 

Check out my profile image above ... manpages rock!

---

### Post by mac187 on 2018-01-24
Aha ok, but will this folder grow with time ? should it not be deleted when i delete mongodb, and the manual should be deleted with the program?

---

### Post by yancek on 2018-01-24
> but will this folder grow with time ?

No, it's a manual with instructions on use similar to a manual you would get with the purchase of pretty much any new appliance or mechanical device.  I'm not sure that man pages are deleted when you remove specific software.  You said you deleted an old version and installed a new version so I would expect the man pages to be for the current version .

---

### Post by mac187 on 2018-01-24
Ok, thanx for helping :)

---

### Post by TheFu on 2018-01-24
manpages are installed and removed as part of the package manifest.  If a program is removed, then the manpages are removed too.

But they are tiny, compressed.  On my desktop, all the manpages are 16MB.  That's nothing. Certainly cleaning up old kernels is 100x more important just on size alone.

---

